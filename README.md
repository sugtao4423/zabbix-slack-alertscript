# zabbix slack alertscript
Send notification to Slack.

# Zabbix Configure

## メディアタイプ
`管理` -> `メディアタイプ`

* 名前: `Slack`
* タイプ: `スクリプト`
* スクリプト名: `slack.sh`
* スクリプトパラメータ:
  - `{ALERT.SENDTO}`
  - `{ALERT.SUBJECT}`
  - `{ALERT.MESSAGE}`

## ユーザー
通知したいユーザーのメディアにSlackを登録

`管理` -> `ユーザー` -> `メディア`タブ

* タイプ: `Slack`
* 送信先: `#zabbix` // Slackのチャンネル
* 有効な時間帯: `1-7,00:00-24:00`
* 分類は必要なものをチェック
* 有効

## アクション
`設定` -> `アクション`

* 名前: `Report problems to slack`

`実行内容`タブ

* デフォルトのアクション実行ステップの間隔: `1h`

* 実行内容
  - 次のメディアのみ使用: `Slack`
  - 件名: `** PROBLEM alert - {HOST.NAME}: {EVENT.NAME}`
  - メッセージ:
```
HOST: {HOST.NAME}
TRIGGER_NAME: {TRIGGER.NAME}
TRIGGER_STATUS: {TRIGGER.STATUS}
TRIGGER_SEVERITY: {TRIGGER.SEVERITY}
DATETIME: {DATE} / {TIME}
ITEM_ID: {ITEM.ID1}
ITEM_NAME: {ITEM.NAME1}
ITEM_KEY: {ITEM.KEY1}
ITEM_VALUE: {ITEM.VALUE1}
EVENT_ID: {EVENT.ID}
TRIGGER_URL: {TRIGGER.URL}
```

* 復旧時の実行内容
  - 次のメディアのみ使用: `Slack`
  - 件名: `** RECOVERY alert - {HOST.NAME}: {EVENT.NAME}`
  - メッセージ:
```
HOST: {HOST.NAME}
TRIGGER_NAME: {TRIGGER.NAME}
TRIGGER_STATUS: {TRIGGER.STATUS}
TRIGGER_SEVERITY: {TRIGGER.SEVERITY}
DATETIME: {DATE} / {TIME}
ITEM_ID: {ITEM.ID1}
ITEM_NAME: {ITEM.NAME1}
ITEM_KEY: {ITEM.KEY1}
ITEM_VALUE: {ITEM.VALUE1}
EVENT_ID: {EVENT.ID}
TRIGGER_URL: {TRIGGER.URL}
```