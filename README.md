# Roundcube Plugin: Cloud View

[![GitHub Workflow Status (branch)](https://img.shields.io/github/workflow/status/jfcherng-roundcube/plugin-cloudview/main/master?style=flat-square)](https://github.com/jfcherng-roundcube/plugin-cloudview/actions)
[![Packagist](https://img.shields.io/packagist/dt/jfcherng-roundcube/cloudview?style=flat-square)](https://packagist.org/packages/jfcherng-roundcube/cloudview)
[![Packagist Version](https://img.shields.io/packagist/v/jfcherng-roundcube/cloudview?style=flat-square)](https://packagist.org/packages/jfcherng-roundcube/cloudview)
[![Project license](https://img.shields.io/github/license/jfcherng-roundcube/plugin-cloudview?style=flat-square)](https://github.com/jfcherng-roundcube/plugin-cloudview/blob/master/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/jfcherng-roundcube/plugin-cloudview?style=flat-square&logo=github)](https://github.com/jfcherng-roundcube/plugin-cloudview/stargazers)
[![Donate to this project using Paypal](https://img.shields.io/badge/paypal-donate-blue.svg?style=flat-square&logo=paypal)](https://www.paypal.me/jfcherng/5usd)

A Roundcube plugin which lets you directly view mail attachments in the browser
with cloud viewers like Google Docs or Microsoft Office Web.

![cover](https://raw.githubusercontent.com/jfcherng-roundcube/plugin-cloudview/master/docs/screenshot/cover.png)

<details>
  <summary>Click me to see the user settings page</summary>
  <img src="https://raw.githubusercontent.com/jfcherng-roundcube/plugin-cloudview/master/docs/screenshot/settings.png">
</details>

## Viewers & Supported Formats

### 3rd-party Viewers

<table>
  <thead>
    <tr>
      <th>Viewer</th>
      <th>Supported Formats</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Google Docs</td>
      <td>
        doc, docx, xls, xlsx, ppt, pptx
      </td>
    </tr>
    <tr>
      <td>Microsoft Office Web</td>
      <td>
        doc, docx, xls, xlsx, ppt, pptx,
        odt, ott, ods, ots, odp, otp
      </td>
    </tr>
    <tr>
      <td><a href="https://stackedit.io/">StackEdit</a></td>
      <td>md</td>
    </tr>
  </tbody>
</table>

### Self-hosting Viewers

<table>
  <thead>
    <tr>
      <th>Viewer</th>
      <th>Supported Formats</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>HTML JS</td>
      <td>htm, html</td>
    </tr>
    <tr>
      <td><a href="https://github.com/chaitin/strapdown-zeta">Markdown JS</a></td>
      <td>md</td>
    </tr>
    <tr>
      <td><a href="https://github.com/mozilla/pdf.js">PDF JS</a></td>
      <td>pdf</td>
    </tr>
    <tr>
      <td><a href="https://github.com/meltingice/psd.js">PSD JS</a></td>
      <td>psd</td>
    </tr>
  </tbody>
</table>

## Requirements

This plugin is tested in the following environment.

- Roundcube: `1.4`
- PHP: `7.1` (min requirement), `7.4`
- Skin: `Classic`, `Larry`, `Elastic`

Different environments may work as well without guarantee.

## How to install this plugin in Roundcube

### Install via Composer (Recommended)

This plugin has been published on [Packagist](https://packagist.org) by the name of [jfcherng-roundcube/cloudview](https://packagist.org/packages/jfcherng-roundcube/cloudview).

1. Go to your `ROUNDCUBE_HOME` (i.e., the root directory of your Roundcube).
2. Run `composer require jfcherng-roundcube/cloudview`.
3. Copy `config.inc.php.dist` to `config.inc.php` and edit `config.inc.php` if you want.

### Install manually

1. Create folder `cloudview` in `ROUNDCUBE_HOME/plugins` if it does not exist.
2. Copy all plugin files there.
3. Copy `config.inc.php.dist` to `config.inc.php` and edit `config.inc.php` if you want.
4. Edit `ROUNDCUBE_HOME/conf/config.inc.php` locate `$config['plugins']` and add `'cloudview',` there:

```php
<?php

// some other codes...

$config['plugins'] = array(
    // some other plugins...
    'cloudview', // <-- add this
);
```

## Temporary Files

This plugin will extract attachments from messages into `plugins/cloudview/temp/`
so that remote cloud viewers can publicly access them. But those files will not
be deleted automatically. You will need to setup a cron job to periodically
delete them.

For example, execute `crontab -e` and add the following job

```text
# delete temporary files on 03:00 AM every day
0 3 * * * rm -rf PATH_TO_ROUNDCUBE/plugins/cloudview/temp/*/
```

## Acknowledgement

- The basic idea comes from https://github.com/brestows/cloudview-roundcube
- This plugin is initially sponsored by [@Galandrix](https://github.com/Galandrix).
