# 超初心者がmoNa2を導入する（途中まで）

## 目次
  - [1. この記事は](#1-この記事は)
  - [2. moNa2購入前の準備](#2-moNa2購入前の準備)
    - [2-1. 参考記事](#2-1-参考記事)
    - [2-2. 事前に買ったもの](#2-2-事前に買ったもの)
  - [3. キーマップ編集環境の構築](#3-キーマップ編集環境の構築)
    - [3-1. GitHubにログイン](#3-1-GitHubにログイン)
    - [3-2. ファームウェアを入手](#3-2-ファームウェアを入手)
    - [3-3. KeymapEditorと連携](#3-3-KeymapEditorと連携)
  - [4. キーマップ編集](#4-キーマップ編集)


## 1. この記事は
<br>

自作キーボードとGitHubの両方とも初めての著者が分割キーボードmoNa2を導入するまでの記録です。  
<br>

> [!CAUTION]
> 記載内容は商品購入前に書かれたものであり、実機が手元になく全て未検証です。  
> 誤りが多数含まれていることが見込まれます。ご利用は自己責任でお願いします。

購入後に判明した誤記は適宜修正していく予定です。  
使用者からのご指摘もお待ちしております。検証のうえ修正します。  
<br>
<br>

## 2. moNa2購入前の準備

### 2-1. 参考記事

数多くの素敵なmoNa紹介記事があります。  
全てを紹介したいところですが、ここではmoNaを使用するにあたり必ず読むべきと思うものを挙げました。  
他の記事もぜひ時間の許す限り目を通してみてください。  
<br>

- #### [分割キーボードmoNaの利用1ヶ月レビュー【自作キーボード】（電電猫猫さん）](https://note.com/electrical_cat/n/n4fbec3582384)
著者がmoNaを知るきっかけとなった記事。  
詳細なレポートのおかげで使用感などが具体的にイメージできました。  
<br>

- #### [moNa2詳細説明（pooh_poloさん）](https://github.com/sayu-hub/zmk-config-moNa2)
続いて熟読したのが製作者による商品詳細。  
商品の組み立て方や後述するファームウェアの操作法などが詳述されており、ここを読めば使えるようになります。  
製作者お二方のX（[pooh_poloさん](https://x.com/Pooh_pol0)、[shakupanさん](https://x.com/shakupan_/)）や[moNa2のdiscordサーバー](https://discord.gg/kJjDBDHGer)にも有益な情報がちりばめられています。  
<br>

- #### [moNa2 のオンボーディング（ぶらきよさん）](https://github.com/sayu-hub/zmk-config-moNa2/blob/main/docs/on-boarding.md)
商品到着からキーマップ変更までの流れが細かく記述されています。ここを読めば設定が完了します。必ず読んでください。  
ぶらきよさんの記事で理解できる方は本記事を読む必要はありません。  

以下に記載する内容はmoNa2詳細説明とぶらきよさんの二番煎じのようなものです。  
<br>
<br>

### 2-2. 事前に買ったもの

キースイッチを別途用意する必要があります。  
<br>

キースイッチとはキーキャップ（QWERTYなどと印字がある一つ一つのパーツのことです）と基盤の間にある文字通りスイッチです。  
様々な製品があるようで、何を買えばよいのか最初はわかりませんでした。  

公式では[lofree ghost](https://lofree.co.jp/products/ghost-low-profile-pom-switches)が推奨されています。  

著者はリニア＆軽いキータッチが好みなので、お薦めされているlofree製のうち[lofree Hades](https://lofree.co.jp/products/hades-low-profile-pom-switches)を選びました。  
moNa2は42キーなので、予備1つ合わせ43個のHadesスイッチを[lofree公式サイト](https://lofree.co.jp/collections/switch)で約1万円で購入しました。  
<br>

あとはPCと接続するUSB-Cケーブルと、M2ネジを締めるための精密ドライバを準備すればOKです。  
<br>

そのほかに利用に必須ではありませんが準備すると快適になるものが[moNa2詳細説明](https://github.com/sayu-hub/zmk-config-moNa2)などに挙げられています。  
興味があれば購入を検討してみてください。  
<br>
<br>

## 3. キーマップ編集環境の構築
42キーしかないmoNaでは、レイヤー機能を使って一つのキーに複数の文字種を割り当てる必要があります。  
この割り当て表がキーマップです。  
キーマップを自分好みに編集する環境を構築するための手順を記載していきます。  
<br>

### 3-1. GitHubにログイン
GitHubのアカウントを持っていなければ[新規作成（sign up）](https://github.com/)します。  
<br>

### 3-2. ファームウェアを入手
次いでmoNa2(右手トラボ版)のファームウェアのリポジトリをフォークします。なんていわれても最初はわけがわかりませんでした。  
> - ファームウェア :「ハードウェアを動かすためのソフト（プログラム）」のこと  
> - リポジトリ :「保管場所」  
> - フォーク :「つながりを保ちつつコピペ」  

つまり公開されているデータを自分のGithubアカウント上にコピーしてカスタマイズする、といった意味合いになります。  
<br>

- #### [moNa2(右手トラボ版)のファームウェア](https://github.com/sayu-hub/zmk-config-moNa2)

上記にアクセスし、画面右上にある「fork」ボタンを押し、Ownerが自身のアカウントになっていることを確認して「Create fork」を押せば入手できます。  
<br>

### 3-3. KeymapEditorと連携
[Keymap Editorのサイト](https://nickcoutsos.github.io/keymap-editor/)へアクセスし、GitHubボタンを押してLoginします。  
「Authorize Keymap Editor」ボタンを押し、「Add Repository」ボタンを押します。  
「Only select repositories」を選び、select repositoriesから先ほどフォークしたMoNa2のファームウェアzmk-config-moNa2を選択してInstall。  

以上で準備作業は終了です。  
インストール後は[Keymap Editorのサイト](https://nickcoutsos.github.io/keymap-editor/)へ再びアクセスすればKeymap Editorが起動します。  
<br>
<br>

## 4. キーマップ編集
ここから先は実機が届いたら追記していく予定です。自身が使いやすいと思う配置を解説していきたいと考えています。  

なお、電電猫猫さんのキーマップが[Noteに公開](https://note.com/electrical_cat/n/n4fbec3582384)されています。
[moNa2のdiscordサーバー](https://discord.gg/kJjDBDHGer)にもkeymapチャンネルが開設されています。
