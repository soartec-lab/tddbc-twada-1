# 収益認識

いま、ソフトウェア製品を扱う小さなECサイトを営んでいるとする。

（なお、本演習では顧客、消費税、税率、通貨、お釣り、在庫などの概念は扱わないものとする）


## 注意

本演習は TDD を体験することを主眼としていますので、 __プログラミングの速さを競っているのではない__ 点にご注意ください。
機能を粗く速く実装することよりも、テストを書いて動かすことによるフィードバックを受けながら、
リファクタリングを忘れずに着実に進めていくことが、本演習では重要です。


## 問題: 製品、契約、売上、収益認識

いま、以下の3つの種類（category）のソフトウェア製品（product）を扱っている。

- ワードプロセッサ
- スプレッドシート
- データベース

製品は名前（name）と価格（price）を持つ（今回は消費税を扱わないので、単純に価格と考えてください）。

例:

- ワードプロセッサ「MS Word」の価格は 18,800円
- ワードプロセッサ「一太郎」の価格は 20,000円
- スプレッドシート「MS Excel」の価格は 27,800円
- スプレッドシート「三四郎」の価格は 5,000円
- データベース「MS SQL Server」の価格は 919,000円
- データベース「Oracle Database」の価格は 2,100,000円

現時点では1回にどれか1つの製品を1つのみ購入する契約（contract）ができるものとする。契約が成立（sign）した場合、

- ワードプロセッサは契約日（signed_on または signedDate）に直ちに売上（revenue）全額を収益認識（revenue recognition）する
- スプレッドシートは契約日に売上の2/3、30日後に1/3を収益認識する
- データベースは契約日に売上の1/3、60日後に1/3、120日後にまた1/3を収益認識する

なお、収益認識の総和は売上とかならず __完全一致__ しなければならない。

- 本日「MS Word」が1つ売れる契約が成立したとき、いつにいくら収益認識されるだろうか
- 本日「MS Excel」が1つ売れる契約が成立したとき、いつにいくら収益認識されるだろうか
- 本日「MS SQL Server」が1つ売れる契約が成立したとき、いつにいくら収益認識されるだろうか
- （他の3製品に関してもテストしてください）


--

短縮 URL: https://bit.ly/3nkWwYq


![クリエイティブ・コモンズ 表示 - 継承 2.1 日本](http://i.creativecommons.org/l/by-sa/2.1/jp/88x31.png)
この演習問題は [クリエイティブ・コモンズ 表示 - 継承 2.1 日本 ライセンス](http://creativecommons.org/licenses/by-sa/2.1/jp/)の下に提供されています。

また、この演習問題は Martin Fowler の著作 『[Patterns of Enterprise Application Architecture](https://www.amazon.co.jp/dp/0321127420)』 から着想を得ています。