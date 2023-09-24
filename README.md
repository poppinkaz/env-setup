# プログラミング環境構築の手順

以下のいずれかにしたがって環境構築を行う。

- [【Windows 簡略版】プログラミング環境構築の手順](./【Windows簡略版】プログラミング環境構築の手順.md)
- [【Mac 簡略版】プログラミング環境構築の手順](./【Mac簡略版】プログラミング環境構築の手順.md)

## この環境構築の手順がサポートするもの

- Linux ベースの開発環境
- Oh My Zsh によるリッチなシェル
- Anaconda による Python 環境
- Git エイリアスによる迅速な開発体験

## 対象 OS

- Windows 10 バージョン 2004 以上 または Windows 11
- macOS Catalina 以降

## なぜ開発者は Linux を使うのか？

このセクションは佐々木の自論である。

### より高機能な Bash/Zsh シェルが使えるから

Windows に WSL1 が入った経緯はこれにあたるのではないだろうか(WSL とは Windows Subsystem for Linux の略で、Windows 上で Linux を使えるようにする機能のこと)。

WSL2 の前バージョンにあたる WSL1 は、本物の Linux カーネルを使用しないなど、いわば"なんちゃって Linux"だった。その"なんちゃって Linux"を Windows に導入する最も大きなメリットは、 Linux のシェル(コマンドを打つときにターミナルに表示されているプログラムのこと)が使えることだろう。

Linux のシェルである Bash/Zsh は Windows の Powershell に比べて機能が段違いに多い。例えば、ファイル内の文字列置換は Powershell では`(Get-Content ファイル名) | foreach { $_ -replace "置換前","置換後" } | Set-Content ファイル名`と書かなければならない(処理としては `ファイルの内容取得 -> forループを使った置換処理 -> 元ファイルに上書き`を 3 つのコマンドで行っている)。しかし、Linux では`sed -i 's/置換前文字列/置換後文字列/' ファイル名`と、`sed`コマンド一つを使うだけでよい。

このような、抽象的な操作を行うコマンドが Linux には非常に多い。これにより、シェル操作が簡単になるほか、比較的高機能なアプリを作る際もわざわざプログラミング言語でプログラムしなくても、シェルスクリプト(一連のシェルコマンドを纏めたファイル)を作るだけで済ませることができるようになる。Linux では、アプリのインストーラがよくシェルスクリプトで出来ていることが多い。

とはいえ、これらのコマンドがプログラミングにどう役立つんだと思うかもしれないが、大量のファイルを扱うことになるプログラミングでは、例えばコンパイル一つを行うにも一苦労することがある。そんなときは、「コンパイルを自動化する」という、"プログラミングのプログラミング"をする場面が出てくる。その際に、高機能なコマンドはとても役に立つ。他にも、例を挙げるのは難しいが、Linux の高機能なコマンドは快適な開発体験に必要不可欠なのである。

### 世界中の開発者が Linux "を" 開発するから

WSL2 は、本物の Linux カーネルを仮想マシン上で動作させるなど、WSL1 と全く異なる仕組みで作られている。WSL1 だけでは物足りなくなって、結局ほぼ本物の Linux を搭載するよう大幅な改変が行われたのは、この理由によるところが大きいのではないだろうか。

まずは、[Wikipedia の Linux についての説明](https://ja.wikipedia.org/wiki/Linux)を引用しよう。

> Linux の開発は、フリーかつオープンソースなソフトウェアの共同開発として最も傑出した例のひとつである。
>
> Linux カーネルのソースコードは無償で入手でき、GNU 一般公衆利用許諾書のもとにおいて、非営利・営利に関わらず誰でも自由に使用・修正・頒布できる。Linux は、世界中の開発者の知識を取り入れるという方法によって、あらゆる方面に利用できる幅広い機能と柔軟性を獲得し、数多くのユーザの協力によって問題を修正していくことで高い信頼性を獲得した。

つまり、Linux は開発者が開発者のために作った OS と言える。開発者は、自身、または開発者コミュニティのために Linux を改変する。このようにして現在も進化を続ける Linux が開発に向いているというのは、前出の文字列置換の例を見ても納得するところではないだろうか。

また、このように多くの人が使うということは、文献が豊富に出来ることにもつながる。「プログラミングはエラーと戦うのが 8 割」とよく言うが、先人が見つけた対処法があるだけでデバッギングの状況は大きく変わってくる。実際、Linux ではエラー内容で Google 検索すればたいていは対処法がすぐに出るため、私はエラー処理を苦に感じたことはない。
