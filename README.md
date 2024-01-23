# 広島市立大学　プログラミングII　革新クラス　自主制作課題
## 概要
このレポジトリは2023年度広島市立大学情報科学部「プログラミングII」での自己制作課題プログラムを公開している（Python3, Jupiter Notebook形式）
コメントなどいただければ幸いだ．

### Work1
============

#### 説明と機能
Work1はユーザにそれぞれの都道府県名に対応する数字（0から46の整数）を求めることで，気象情報を出力するプログラムである．また，天気予報の音声を日本語と英語で出力してくれる．

これによって，日本人だけでなく，外国人も天気予報を聞くことができる．

#### 工夫した点
①ユーザーが「北海道」のようにテキストベースで入力することも考えたが，ユーザーは名称入力の手間がある．同様に，開発者としても，「おおさか」「大阪府」「大阪」などいろいろな入力パターンを想定しなければならないということで，数値入力でユーザの意図を理解させている．（非機能面）


②音声表示をする際にDisplay（Ipython())を用いた．これにより，複数（今回の場合は日英）の音声アナウンスを出力できる。Display()を用いないと最後の1つのmp3しか出力できない．（技術面）


③ユーザは日英のアナウンスを選択できるようになっている．テキスト翻訳と音声出力を別々のライブラリで処理している．（機能面）
#### 今後の展望

①都道府県の選択が0～46になっているので，1～47で表示し，処理できるようにしたい


②現在は県（府，都）庁所在地の天気情報を取得しているが，ユーザの希望に合わせて特定の市区町村で天気予報を表示できるようにもしていきたい

##### 参考資料
総務省統計局（2023年12月19日）：都道府県表示のために使用しているExcelファイルです

https://www.stat.go.jp/data/nihon/zuhyou/n230200200.xlsx


ぺんぎんのーと（2023年12月19日）：Web上からColab環境へファイルをダウンロードする方法（requests）について


https://ssrv.net/tech/python-requests-image/

Men of Letters（メン・オブ・レターズ） - 論理的思考/業務改善/プログラミング（2023年12月20日）：DataFrameのNaNの削除

https://laboratory.kazuuu.net/delete-rows-with-nan-values-in-the-dataframe-in-pandas/#toc2

研究人生（2023年12月19日）：天気予報の取得と表示のプログラムを参考にさせていただいた．

https://kenkyujinsei.com/2021/02/06/python-%E3%81%A7-%E5%A4%A9%E6%B0%97%E4%BA%88%E5%A0%B1api%E3%81%8B%E3%82%89%E3%81%8A%E5%A4%A9%E6%B0%97%E6%83%85%E5%A0%B1%E3%82%92%E5%8F%96%E5%BE%97%E3%81%97%E3%81%A6%E3%81%BF%E3%82%88%E3%81%86/


おとといからきたいも（2023年12月20日）：日本語（天気予報）を英語に翻訳する．

https://invisiblepotato.com/python11/

free journey（2023年12月20日）：音声読み上げ機能

https://fjjourney.com/artificial-intelligence/text-to-speech/


### Work2
============

#### 説明と機能
Work2はExcelファイルまたはCSVファイルを行列データとして読み込み，行列計算を行うプログラムである．


これによって，ユーザはExcel上で行列を容易にかつ視覚的に作成し，計算を行うことができる．

また，行列計算の計算結果をExcelファイルまたはCSVファイルで出力できる．

主に以下の機能を実装している

・2つの行列の和，差，積

・行列のスカラー倍，n乗

・逆行列の計算

・上記計算後に計算結果のExcel，CSV出力

・行列式の計算

・固有値の計算

・階数の計算

・トレースの計算

#### 具体的なターゲット
日本国内で線形代数を履修している理系大学１年生・２年生（学部）

PythonやNumPyに触れたことがない方向けに設計されている．（NumPyの難しい文法を意識する必要がない．）

行列計算の検算などに使用することをお勧めする．

免責事項：このプログラムは大学における課題提出・レポート作成においての不正やカンニングを促進・推奨するものではありません．

#### 工夫した点
①Colaboratoryのfilesライブラリを使用することで，ユーザがセルの中でExcelファイルをアップロードすることができる．これにより，Colaboratoryに精通していないユーザであっても，簡単にExcelの行列ファイルをアップロードすることができる（機能面）

②エラー処理に多くの時間を費やした．フールプルーフの考え方で，行列に文字列が含まれている場合や，異なったファイル形式がアップロードされた場合などを想定することで開発者が予期していないエラーが発生することを最大限防止している．（非機能面＆技術面）

③欠損値（空白セル）は0に置換している．これにより，開発者側は処理が簡略化できた．また，行列の0の要素を入力しないユーザがいることが想定されるので，あらかじめ0に置換する仕様にした．（非機能面＆技術面）

④読み込んだ行列はpandasにてDataFrameの形で出力している．これはユーザにとって視覚的でわかりやすい行列表現を追求した結果である（機能面）

⑤NumPyライブラリの内部処理はＣ言語で実装されているため，行列計算の段階でオーバーフローしてしまうと，計算処理が上手く反映されないという課題があった．そこで，オーバーフローしやすい行列のn乗の計算に関しては，datatypeをPythonの標準のobject型に変換して行列計算を行っている．これによって，オーバーフローを考える必要がなくなる．（技術面）

#### 今後の展望
①ColabratoryのfilesライブラリでExcelファイルをアップロードする仕様であるが，Colabがアップロードを待っている段階でキャンセルボタンを押すと，処理が中断し，エラーとなってしまう．このエラーを回避する方法（アップロードされたかされていないかを検知する方法）を探したのだが，そのような機能は搭載されていないとのことだった．本当に検知する方法がないのかや他の環境では実装できないか等を熟考していきたいと考える．

②工夫した点の５項で記述したが，n乗計算の際にdatatypeをobjectに変換している．これはオーバーフローを回避する解決策なのだが，NumPyの高速な計算処理を犠牲にしている．NumPyの高速な計算処理とオーバーフローの回避を両立できる方法がないかを調査していきたいと考える．

#### 参考文献
広島市立大学　プログラミングII　講義資料　第５週　NumPyの基礎　第６週　NumPyの応用：NumPyと行列計算について復習

広島市立大学　線形代数学I，II　講義資料：行列について復習

https://www.delftstack.com/ja/howto/python-pandas/how-to-convert-pandas-dataframe-to-numpy-array/

DelftStack，Pandas DataFrame の列ですべての NaN 値をゼロに置き換える方法（2024年1月11日）：空白セルを0に置換

https://www.delftstack.com/ja/howto/python-pandas/how-to-replace-all-the-nan-values-with-zeros-in-a-column-of-a-pandas-dataframe/

いかたこのたこつぼ，Numpyのオーバーフロー回避（2024年1月11日）：NumPyのオーバーフロー回避

https://ikatakos.com/pot/programming_algorithm/python_tips/avoid_overflow

ITCブログ，Pythonで行列を扱う方法｜numpyの使い方を実例付きで徹底解説（2024年1月11日）：コードととともにmatrixの使い方が幅広く解説されていた．

https://itc.tokyo/python/python-matrix/

note.nkmk.me，pandas.DataFrame, SeriesとNumPy配列ndarrayを相互に変換（2024年1月11日）：DataFrameを行列に変換する方法

https://note.nkmk.me/python-pandas-numpy-conversion/#pandasdataframe-seriesnumpyndarray

### Work3
============

#### 説明と機能
work3は名刺データをアップロードし，読み取った情報を読み込み，連絡先登録を支援するシステムだ．読み込んだ情報はvcf形式で出力されるため，Windowsの連絡先ファイルとして機能する．

work3では，名刺の次の項目を読み取り，vcfファイルに反映させる

・名前

・勤務先

・メールアドレス

・電話番号

#### 使い方
①Google Colaboratory上で上から順番にプログラムを実行し，PDFファイルをアップロードする．

<img width="760" alt="image" src="https://github.com/taiyang2525/Prog2kakushin/assets/145079223/0b83977c-f54a-4e12-bcbc-d56c9b32f427">

②自動で名刺情報を読み込む．情報を読み込む際，誤ることもあるため，ユーザは読み込んだ情報を確認し，誤りがあれば変更できる．
<img width="890" alt="image" src="https://github.com/taiyang2525/Prog2kakushin/assets/145079223/bb9bee59-828c-4120-be46-a34164a3ce1d">

③もう一つ下のセルを実行する．すると，読み込んだ名刺の情報をvcfファイルで出力する．
<img width="848" alt="image" src="https://github.com/taiyang2525/Prog2kakushin/assets/145079223/0c0f173a-169f-45f2-b304-7a8ba77844f4">

④名前.vcfでColablatoryのファイルにvcfファイルが出力されている．Colabratoryのファイルタブから確認できる．また，vcfファイルをローカルの環境にダウンロードすると連絡先として活用できる．
<img width="1082" alt="image" src="https://github.com/taiyang2525/Prog2kakushin/assets/145079223/7d63ee11-827f-4c6e-a2d7-40afda6d5234">

vcfファイルを読み込んだ状態（Windows11 英語環境）
<img width="1127" alt="image" src="https://github.com/taiyang2525/Prog2kakushin/assets/145079223/6fdcb242-c1d1-4a1e-b9f9-8baee8bf5c8d">





#### 工夫した点
①OCRの精度を上げるため，カラー，グレースケール，２値化の３つの画像にてそれぞれOCR処理を行い，自動的にテキストをマージしている．これにより，高い精度でのOCRが期待できる．（技術面）

②開発の段階で，名刺の名前（性＋名）の特定は特に難航した．日本人の名前の性は４文字以下かつ全角文字であり，性と名の間にスペースがあるという仮定をすることで，高い精度で名前を抽出することが可能となった．（技術面）

③電話番号の処理の際，市外局番に括弧が含まれていたり，ハイフンで区切られている可能性がある．そこで，今回は簡単のために，括弧，ハイフン等はすべて省略する処理を加えた．（技術面）

④OCRが失敗することもあるため，Inputで読み取り値（名前，メールアドレスなど）を修正できる．その際，名刺画像が上に表示されているので，ユーザは名刺をスクリーン上で見ながら，正誤を確認することができる．（機能面）

#### 応用例
このプログラムは以下の状況で約に立つかもしれない

・オフィスビルにおける外来者訪問の受付の効率化

・名刺管理システムの一部

#### 今後の展望
①OCRの精度の向上に努めていきたい．また，現状の氏名特定のプロセスは氏名が５文字の人では機能しない．また，役職名等を抽出する可能性があるなど脆弱性もある．そのため，これらを改善する最適なアルゴリズムを探していきたい．

②今回は機械学習を使わなかったが，機械学習を用いたものも作ってみたい．

#### 参考文献
某エンジニアのお仕事以外のメモ（分冊）　Pythonで文字を全角か半角か判別する（2024年1月19日）：全角文字の抽出

https://water2litter.net/rum/post/python_unicodedata_east_asian_width/

株式会社 asken（あすけん） Google ColabでTesseractOCRを使う方法（2024年1月19日）：名刺からのOCR

https://qiita.com/shoku-pan/items/7a67f484a10430da6678

自作で機械学習モデル・AIの使い方を学ぶ　[Python]電話番号をエスケープ !正規表現で便利なテクニック解説（2024年1月19日）：電話番号の抽出

https://machine-learning-skill-up.com/knowledge/python%E9%9B%BB%E8%A9%B1%E7%95%AA%E5%8F%B7%E3%82%92%E3%82%A8%E3%82%B9%E3%82%B1%E3%83%BC%E3%83%97-%E6%AD%A3%E8%A6%8F%E8%A1%A8%E7%8F%BE%E3%81%A7%E4%BE%BF%E5%88%A9%E3%81%AA%E3%83%86%E3%82%AF%E3%83%8B

novonovo　Python 文字列からURLやメールアドレスを抽出（2024年1月19日）：メールアドレスの抽出

https://blog.novonovo.jp/python/python-%E6%96%87%E5%AD%97%E5%88%97%E3%81%8B%E3%82%89url%E3%82%84%E3%83%A1%E3%83%BC%E3%83%AB%E3%82%A2%E3%83%89%E3%83%AC%E3%82%B9%E3%82%92%E6%8A%BD%E5%87%BA/

note.nkmk.me　（2024年1月19日）：OpenCVのRGB変換

https://note.nkmk.me/python-opencv-bgr-rgb-cvtcolor/

@derodero24(derodero)　【Python】Pillow ↔ OpenCV 変換（2024年1月19日）：OCRの際にPillowに変換

https://qiita.com/derodero24/items/f22c22b22451609908ee

ecoAGI PyPDF2：PDFの操作のための究極のPythonライブラリ（2024年1月19日）：PDFの分割（１ページのみ抽出）

https://ecoagi.ai/ja/topics/Python/pypdf2-python-pdf
