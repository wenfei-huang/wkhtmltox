# wkhtmltox

This repository contains the version 0.12.6 of wkhtmltopdf and wkhtmltoimage from the [wkhtmltopdf project](https://github.com/wkhtmltopdf/wkhtmltopdf), check for latest (https://github.com/wkhtmltopdf/wkhtmltopdf/releases/latest).

The binaries are built for Ubuntu 20.04 focal, amd64 only AMD64 architectures are included.

## Why
h4cc/wkhtmltopdf-amd64 and h4cc/wkhtmltoimage-amd64 package is outdated and gives errors on php 8.0

When it's not possible to install the latest version via .deb package with apt
```bash
wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.focal_amd64.deb
sudo apt install ./wkhtmltox_0.12.6-1.focal_amd64.deb
```

Or sometimes you just want a quick solution for your dev environment ;)

## Installation

This package is published on [Packagist](https://packagist.org/packages/wenfei-huang/wkhtmltox) and should be installed with [Composer](https://getcomposer.org/download/).

The version of the binary is equal to the git tag.
Composer will install the latest version by default.
```bash
$ composer require-dev wenfei-huang/wkhtmltox
```

Composer will install the package in your project path into the _vendor/wenfei-huang/wkhtmltox/_ directory.

The binaries are located in the _vendor/wenfei-huang/wkhtmltox/bin/_ directory.

Composer will symlink them to the _vendor/bin/_ directory.

_Optional:_ You can also symlink them to the _/usr/local/bin/_ directory, as apt would install normally there.

```bash
$ ln -s /absolute/path/to/your/project/vendor/wenfei-huang/wkhtmltox/bin/wkhtmltopdf_0.12.6_linux_ubuntu_focal_amd64 /usr/local/bin/wkhtmltopdf
$ ln -s /absolute/path/to/your/project/vendor/wenfei-huang/wkhtmltox/bin/wkhtmltoimage_0.12.6_linux_ubuntu_focal_amd64 /usr/local/bin/wkhtmltoimage
```

Check the Version:
```bash
$ wkhtmltopdf -V
wkhtmltopdf 0.12.6 (with patched qt)
```

### Usage
If using with [Laravel Snappy PDF](https://github.com/barryvdh/laravel-snappy) package, you can change in the snappy config file:
``` php
    'pdf' => array(
        ...
        'binary'  => base_path('vendor/wenfei-huang/wkhtmltox/bin/wkhtmltopdf-amd64'),
        ...

    ),
    'image' => array(
        ...
        'binary'  => base_path('vendor/wenfei-huang/wkhtmltox/bin/wkhtmltoimage_0.12.6_linux_ubuntu_focal_amd64'),
        ...
    ),

```


With the [KNP-Snappy](https://github.com/KnpLabs/snappy) package, you can now use the binaries to create PDFs or Images from HTML.

You can use the path constants from this project to easily locate the binary paths (with PSR 4 Autoloader):

``` php
<?php
use Knp\Snappy\Pdf;
use Knp\Snappy\Image;
use Wkhtmltox\Wkhtmltopdf;
use Wkhtmltox\Wkhtmltoimage;

$snappyPdf = new Pdf(Wkhtmltopdf::wkhtmltopdfx64);
$snappyImage = new Image(Wkhtmltoimage::wkhtmltoimagex64)
``` 

_OR_ If you symlinked the binaries to _/usr/local/bin_:

``` php
<?php
use Knp\Snappy\Pdf;
use Knp\Snappy\Image;

$snappyPdf = new Pdf('/usr/local/bin/wkhtmltopdf');
$snappyImage = new Image('/usr/local/bin/wkhtmltoimage');
```

### License

This package is published under the same GNU General Public License v3.0 [LICENSE](https://github.com/wenfei-huang/wkhtmltox/blob/master/LICENSE) as the [wkhtmltopdf project](https://github.com/wkhtmltopdf/wkhtmltopdf).
