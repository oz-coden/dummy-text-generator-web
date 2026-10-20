# Dummy Text Generator

日本語の説明は[目次](#目次)から読めます。

## Table of Contents

1. [Summary](#summary)
2. [Background of Development](#background-of-development)
3. [Features](#features)
4. [Requirements, Dependencies](#requirements-dependencies)
5. [Installation](#installation)
6. [LICENSE](#license)
7. [CREDIT](#credit)

## Summary

A browser-based tool that generates placeholder text from preset passages or a custom string. Specify an output length or repetition count, then copy the result.

[Playground Is Here!](https://tools.oz-coden.com/dummy-text-generator/)

## Background of Development

The aim is to prepare placeholder text for page layouts, input fields and prototypes without manually copying and trimming passages.

## Features

- Preset passages and custom text  
  Choose from three Japanese literary excerpts, Lorem ipsum, or your own string.
- Two generation modes  
  Repeat and trim the source to a specified length, or repeat it a specified number of times.
- Unicode-aware character counts  
  Count Unicode code points, so a supplementary character such as `😀` counts as one. Combining marks and multi-code-point emoji are counted separately.
- Copy the result  
  Copy generated text to the clipboard. If copying is unavailable, select and copy the text manually.
- Shared navigation and themes  
  Use the common tool header and light or dark theme.

## Requirements, Dependencies

- A current web browser with JavaScript enabled.
- Automatic clipboard access may require a secure context, such as HTTPS or localhost. Manual copying is also available.

The user interface is in Japanese. Shared UI assets are included in this repository. Python 3 is only needed for the example local server command below; an equivalent static HTTP server can also be used.

## Installation

1. Clone or download this repository, keeping the directory structure intact.
2. Start a static HTTP server from the repository root. For example, with Python 3:

   ```sh
   python -m http.server 8000
   ```

3. Open `http://localhost:8000/` in your browser.

The application files are at the repository root. Running the application requires only static HTML, CSS and JavaScript; no Node.js runtime, API server or build step is required.

Text generation runs entirely in the browser. The application does not upload the source text or generated output, and does not save them for restoration after reloading.

### Usage

1. Select a preset under **使用する文字列**, or select **カスタム文字列** and enter your own text.
2. Choose **指定した文字数まで出力** or **指定した回数繰り返す** under **出力の条件**.
3. Enter a positive integer and click **テキストを生成する**.
4. Click **クリップボードにコピー** to copy the result.

The numeric input is limited to 1,000,000, and the output is limited to 1,000,000 code points. In repetition mode, the total output must also fit within this limit. If the custom string is empty, the first preset is used.

### Development and publication

Application-specific behavior and layout are in `script.js` and `style.css`. Shared styles, navigation and themes are bundled in `vendor/ui/` from [oz-coden.com-ui-web](https://github.com/oz-coden/oz-coden.com-ui-web). The source commit and file hashes are recorded in `shared-ui.json`, so the application does not fetch the shared UI repository at runtime.

To update the bundled UI, clone the shared UI repository alongside this repository. From this application's root, run `node ../oz-coden.com-ui-web/scripts/sync-ui.mjs . COMMIT_SHA`, replacing `COMMIT_SHA` with the full 40-character commit SHA to use. Commit the updated `vendor/ui/` files and `shared-ui.json`. This maintenance command requires Node.js 22 or later and an internet connection.

This repository checks JavaScript syntax on push and pull requests. With Node.js 22 or later, run the same checks locally:

```sh
node --check script.js
node --check vendor/ui/ui.js
```

The hosted application is assembled and published through [tools.oz-coden.com](https://github.com/oz-coden/tools.oz-coden.com). Its publication workflow applies the shared UI to all tools and runs browser integration checks. See that repository for deployment instructions.

## LICENSE

This project is released under the [MIT License](LICENSE).

## CREDIT

Shared styles, navigation and themes: [oz-coden.com-ui-web](https://github.com/oz-coden/oz-coden.com-ui-web).

Preset excerpts:

- 宮沢賢治『ポラーノの広場』
- 太宰治『走れメロス』
- 夏目漱石『吾輩は猫である』

---

# ダミーテキストジェネレーター

## 目次

1. [概要](#概要)
2. [開発背景](#開発背景)
3. [機能](#機能)
4. [前提・依存](#前提依存)
5. [導入方法](#導入方法)
6. [ライセンス](#ライセンス)
7. [クレジット](#クレジット)

## 概要

プリセットの文章や任意の文字列から、ダミーテキストを生成するブラウザ用ツールです。文字数または繰り返し回数を指定し、生成結果をコピーできます。

[Playgroundはこちら！](https://tools.oz-coden.com/dummy-text-generator/)

## 開発背景

ページのレイアウトや入力欄、プロトタイプに使う仮の文章を、手作業でコピーしたり切り詰めたりせずに用意できることを目的としています。

## 機能

- プリセットとカスタム文字列  
  日本語の文学作品3種類の冒頭、Lorem ipsum、任意の文字列を選べます。
- 2つの生成モード  
  元の文字列を繰り返して指定文字数で切り詰めるか、指定回数だけ繰り返します。
- Unicodeに対応した文字数  
  Unicodeコードポイント単位で数えるため、`😀`のような補助文字も1文字として扱います。結合文字や複数コードポイントで構成される絵文字は、それぞれのコードポイントを数えます。
- 結果のコピー  
  生成結果をクリップボードにコピーできます。コピーできない場合は、結果を選択して手動でコピーできます。
- 共通ナビゲーションとテーマ  
  共通ヘッダーとライト・ダークテーマを利用できます。

## 前提・依存

- JavaScriptが有効な最新のWebブラウザ。
- クリップボードへの自動コピーには、環境によってHTTPSやlocalhostなどの安全なコンテキストが必要です。手動でのコピーも利用できます。

画面の言語は日本語です。共通UIのファイルはこのリポジトリに同梱しています。Python 3は下記のローカルサーバーのコマンドを使う場合に必要で、同等の静的HTTPサーバーでも実行できます。

## 導入方法

1. このリポジトリをクローンまたはダウンロードし、フォルダ構成を保ちます。
2. リポジトリのルートで静的HTTPサーバーを起動します。Python 3を利用する場合は、次のコマンドを実行します。

   ```sh
   python -m http.server 8000
   ```

3. ブラウザで`http://localhost:8000/`を開きます。

アプリ本体はリポジトリのルートにあります。実行には静的なHTML・CSS・JavaScriptだけを使い、Node.jsの実行環境・APIサーバー・ビルド工程は不要です。

テキストの生成はブラウザ内で行います。元の文字列や生成結果をアップロードする処理はなく、再読み込み後に復元するための保存も行いません。

### 使い方

1. **使用する文字列**からプリセットを選ぶか、**カスタム文字列**を選んで任意の文字列を入力します。
2. **出力の条件**で、**指定した文字数まで出力**または**指定した回数繰り返す**を選びます。
3. 正の整数を入力し、**テキストを生成する**を押します。
4. **クリップボードにコピー**で結果をコピーします。

数値欄の上限は100万、生成結果の上限は100万コードポイントです。繰り返しモードでも、結果をこの上限以内に収める必要があります。カスタム文字列が空の場合は、最初のプリセットを使用します。

### 開発と公開

アプリ固有の処理は`script.js`、レイアウトは`style.css`で管理します。共通のスタイル・ナビゲーション・テーマ切り替えは、[oz-coden.com-ui-web](https://github.com/oz-coden/oz-coden.com-ui-web)から`vendor/ui/`へ同梱しています。取得元のコミットとファイルハッシュは`shared-ui.json`に記録しており、実行時に共通UIリポジトリへアクセスする必要はありません。

同梱の共通UIを更新するには、このリポジトリと同じ親フォルダに共通UIリポジトリをクローンします。このアプリのルートで`node ../oz-coden.com-ui-web/scripts/sync-ui.mjs . COMMIT_SHA`を実行し、`COMMIT_SHA`を取り込む版の40桁のコミットSHAに置き換えてください。更新された`vendor/ui/`のファイルと`shared-ui.json`をコミットします。この保守用コマンドには、Node.js 22以降とインターネット接続が必要です。

このリポジトリでは、pushとプルリクエスト時にJavaScriptの構文を検査します。Node.js 22以降を利用すると、同じ検査をローカルでも実行できます。

```sh
node --check script.js
node --check vendor/ui/ui.js
```

公開用のアプリは、[tools.oz-coden.com](https://github.com/oz-coden/tools.oz-coden.com)で組み立てて配信します。公開処理では、全ツールに共通UIを適用し、ブラウザでの統合検査を行います。公開手順は同リポジトリを参照してください。

## ライセンス

This project is released under the [MIT License](LICENSE).

## クレジット

共通のスタイル・ナビゲーション・テーマ：[oz-coden.com-ui-web](https://github.com/oz-coden/oz-coden.com-ui-web)。

プリセットには、次の作品の冒頭を使用しています。

- 宮沢賢治『ポラーノの広場』
- 太宰治『走れメロス』
- 夏目漱石『吾輩は猫である』
