# QA がバックログ作成をやってみた話

バックログというユーザの価値を決めるタスクを作成する

1. 情報のインプット
   1. ユーザの声を知る
   2. 会社の方針を把握する
      正しい情報をもとに考えることが大事
      → ユーザ、会社の双方に取ってのメリットを考えることが大事

※解決方法は 1 つではないので、コストを考える事が大切

解決方法を絞る過程で各職能メンバへの相談をしてブラッシュアップされる
→ リリースまでこぎつける

QA がバックログを作成して良かったこと

- QA の考え方はバックログ作成に生かせる
  - 製品機能に詳しい
  - 課題に対しての解決法を現状機能を把握しているので提案しやすい
  - 網羅的に列挙することが得意なので、影響範囲などの洗い出しもできる
- 試験への取り組み方がよくなった
  - インプットが増えたことで目的がはっきりした
  - ユーザ価値を意識して試験できるようになった
    - ユーザにとっての
- 製品理解が深まって楽しい
  - 会社の方向性や他の製品と Slash の関係性が理解できるようになった

品質向上にかかわることは職能にかかわらずに対応する

QA からバックログ作成に取り組みたいこと
→ QA から考えたいことあるかどうかを振られて返答する

情報収集で考えがまとまったら、職能メンバに報告をする
→ 情報を収集しやすいのもサイボウズの特色

開発している方よりも QA の方が詳しいこともあるので

# QA が In Production で活動に取り組み始めた話

背景

- Clara
  - Kintone の販売管理システム
  - 米国市場向け Kintone の AWS 移行ぷとジェクトの一巻
  - ユーザ
    - エンドユーザ
    - 社内セールスチーム
      - ライセンス管理やキャンペーン
- 開発プロセス
  - スクラム
  - リリースは週 2 回
  - 6 人中 3 人が QA
- 従来
  - サービス開発者と運用者が組織的に分かれている
- 今回
  - サービス開発者が運用まで行うことにチャレンジ
  - 本番環境のデータにアクセス可能
- QA の業務内容
  - リリースまでの PreProduction がメインだった
  - ここでは InProduction の領域にも広がった

取り組み

- リリース作業
  - バックログアイテムごとの試験が完了したらリリース
  - リリースは QA
  - GutHub→webhook→CI
- 本番環境で実行する自動テストの整備
  - デプロイパイプラインに本番環境での自動テストを含める
    - 切り戻し可能
- 定期的なエラーログの確認
  - 1 日 1 回抽出ログを目視で確認
  - 怪しいログは詳しく調査
  - ログ確認による効果
    - 開発環境では想定しづらい原因による不具合
    - 社内ユースケースに起因するエラー
- QA がログ確認するメリット
  - 実際にどう利用されているかが確認できる

気を付けたいこと

- InProduction だけに頼らない
  - あらゆる不具合をモニタリングや、本番環境のアラートで対応すれば良いのでは？
    - 自身の視野が InProduction のみに絞られてしまっていた
- 開発プロセス全体を俯瞰して確認する必要がある

質疑応答

本番環境でのログを確認することの知見、元々の QA での取り組みにどのようにフィードバックしているか
→ 本番環境だけで発生している操作等を、QA の指摘事項やテストケースとして指摘できるようにしている

データアナリティクスは PM が主に行う

In-Production とそれ以外の場所で、どんな種類のバグを見つけると良いか
→ 本番環境では発表の中にあったユースケースなどを検討する

ログ自体の品質については、開発段階からかかわることで改善をしている

# サイボウズ Data Center を支えるインフラ QA の挑戦

- SRE-QA
- インフラ QA
- 特殊な環境が故、必要な QA

  - 開発 → 運用までを自社でしているから必要になっている

- SRE-QA

  - SRE(24/365 でサービス稼働を支える → 開発スパンも短い)と連携する QA
  - データ管理・運用プログラムの QA
  - アーキテクチャの QA もしている
  - 開発・検証環境の管理等もしている
  - 求められる知識・スキル
    - Linux
    - Web アプリの基本
    - ミドルウェアの知識も必要

- Buddy 精度

  - SRE 数名と、QA1,2 名で Buddy を組んでチームとする
  - Buddy 制度で専門性を高めた際に、特定の人物のみに知識が集約されることはないか

- 工程を問わないやり取りが供される文化

  - PullRequest も QA 発信できる

- Whole チームでの品質への姿勢がある
  - SRE,QA 共に品質について自分事として対応している

twiter @tyamada248 へ DM すればカジュアル面談もできる？

質疑応答
buddy は SRE と SRE-QA 以外では対応されていないのか？
→ 他の開発環境では対応されていない

SRE,SRE-QA ですみ分ける必要はある？
→ 学ぶ領域が違ってくる QA だから持てる鋭い観点があるので、SRE だけでやるよりも品質保証に貢献できていると思う。

ロードバランサ
→ 試験は開発環境で行っているので、ロードバランサの全断試験もする
