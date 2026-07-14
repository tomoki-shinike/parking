駐車料金計算ツール（Parking Fee Calculator）

契約駐車場の料金体系（時間帯別単価・上限料金・休日料金など）をあらかじめ登録しておき、入庫時刻を選ぶだけで「現在時刻＋15分」時点の駐車料金と、精算に必要な100円チケットの枚数を自動計算するツールです。

A tool for staff who issue paid parking tickets at contracted parking lots. Once each lot's pricing rules (time-based rates, daily/period fee caps, holiday rates, etc.) are registered, staff only need to select the lot and the entry time — the tool automatically calculates the parking fee as of "now + 15 minutes" and the number of 100-yen tickets required.


主な機能 / Key Features


駐車場ごとの料金設定：フラット料金、または時間帯ごとの単価（○分ごとに○円）を登録可能
Per-lot pricing: flat rate, or time-of-day based unit pricing (e.g. ¥100 per 20 minutes)
上限（最大）料金の設定：時間帯ごとの上限、および「暦日ごと」「入庫から24時間ごと」「滞在全体で1回」の上限ルールに対応
Fee caps: per time-band caps, plus caps that reset daily, every 24 hours from entry, or once per stay
休日料金：土日および任意の日付（祝日・年末年始など）を休日として設定可能
Holiday pricing: weekends and any custom dates can be flagged as holiday rate days
ワンタップ計算：駐車場と入庫時刻を選ぶだけで、現在時刻＋15分時点の料金・必要チケット枚数を自動算出
One-tap calculation: select the lot and entry time, and the fee / ticket count as of now+15 minutes is calculated automatically
計算履歴：その端末で行った計算を記録し、「本日の合計金額・枚数」を確認可能
Calculation history: keeps a log on the device, with a running total for the current day
料金設定の共有管理：料金体系は parking-data.json という1つのファイルに集約。GitHub等にHTMLファイルと並べて置いておけば、ファイルを更新するだけで全利用者に新料金が反映される
Shared pricing data: all lot/holiday settings live in a single parking-data.json file. Hosting it alongside the HTML (e.g. on GitHub Pages) means updating that one file instantly reflects new pricing for everyone



ファイル構成 / Files

ファイル名役割駐車料金計算ツール.htmlツール本体（これを開いて使用）parking-data.json駐車場ごとの料金設定・休日リスト（マスターデータ）

FileRole駐車料金計算ツール.htmlThe tool itself — open this in a browserparking-data.jsonMaster data: per-lot pricing rules and holiday list


使い方 / Setup


駐車料金計算ツール.html と parking-data.json を同じフォルダにアップロードします（GitHub Pagesなど https で配信できる場所である必要があります）。
管理者が「駐車場管理」「祝日設定」タブで料金を登録・編集します。
「データ管理」タブの「現在の設定を parking-data.json として書き出す」でファイルを書き出し、GitHub上の parking-data.json を置き換えます。
職員はHTMLを開いて「駐車場」「入庫時刻」を選ぶだけで計算できます。開くたびに最新の parking-data.json を自動で読み込みます。
Upload 駐車料金計算ツール.html and parking-data.json to the same folder (must be served over https, e.g. GitHub Pages — opening the HTML directly from local disk will not load the JSON).
An administrator registers/edits pricing in the "駐車場管理" (Lot Management) and "祝日設定" (Holiday Settings) tabs.
From the "データ管理" (Data Management) tab, export the current settings as parking-data.json and replace the file in the repository.
Staff simply open the HTML file and pick a lot and entry time — the tool always loads the latest parking-data.json on open.



補足 / Notes


計算履歴はブラウザ内（localStorage）に保存されるため、端末ごとに別々の記録になります。
料金設定・休日は parking-data.json を書き換えることで全利用者に反映されます。
parking-data.json が読み込めない場合は、その端末に前回保存されていた設定（キャッシュ）を使用し、画面上に警告が表示されます。
Calculation history is stored per-device (browser localStorage) and is not shared between devices.
Pricing/holiday changes take effect for everyone once parking-data.json is updated.
If parking-data.json fails to load, the tool falls back to the last cached settings on that device and shows a warning banner.
