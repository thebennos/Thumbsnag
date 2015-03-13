# Thumbsnag [![Build Status](https://travis-ci.org/gstjohn/Thumbsnag.svg?branch=master)](https://travis-ci.org/gstjohn/Thumbsnag)

Thumbsnag crawls a webpage and makes a best effort at finding imagery that represents the given page.

## Example

```php
use Thumbsnag\FastImageAnalyzer;
use Thumbsnag\Thumbsnag;
use Thumbsnag\UrlDocument;

$url = 'http://simplegifts.co';
$html = file_get_contents($url);

$document = new DOMDocument();
$document->loadHTML($html);

$analyzer = new FastImageAnalyzer(new FastImage());

$thumbsnag = Thumbsnag::load(new UrlDocument($doc, $url), $analyzer);
$images = $thumbsnag->process();
```

After inspection, `$images` will return something like:

```bash
array(2) {
  [0]=>
  string(31) "http://simplegifts.co/image1.jpg"
  [1]=>
  string(31) "http://simplegifts.co/image2.png"
}
```

## Configuration

## Usage

### Step 1: Install

Pull the package in through Composer.

```js
"require": {
  "gstjohn/thumbsnag": "~1.0"
}
```

### Step 2: Configure (as necessary)

Thumbsnag::load() takes an array as its third parameter which overrides the default config. Available configuration options are:

+ #####min_area (default: 5000)#####

  This option represents the minimum pixel area (width x height) of the images that is required in order to be included in the result set.
  
+ #####ratio_threshold (default: 3.0)#####
  This option represent the maximum ratio of width-to-height allowed in order to be included in the result set.
  
+ #####filename_filters (default: "sprite", "blank", and "spacer")#####
  This option represent an array of words that must not be in the image file name in order to be included in the result set.

## Credits

+ [How to Find the Image That Best Represents a Web Page](https://tech.shareaholic.com/2012/11/02/how-to-find-the-image-that-best-respresents-a-web-page/)
+ [Crawlsane](https://github.com/michaelmcmillan/Crawlsane)

# License

Thumbsnag is open-sourced software licensed under the [MIT license](https://raw.githubusercontent.com/gstjohn/Thumbsnag/master/LICENSE).