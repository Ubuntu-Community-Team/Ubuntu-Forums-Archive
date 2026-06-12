---
title: "PHP Simple html dom:Get Any Thing From Any Html Page"
date: 2009-12-24
forum: Programming Talk
---

### Post by astkboy2008 on 2009-12-24
(Simple html dom 1.11) is A simple PHP HTML DOM parser written in PHP5+, supports invalid HTML, and provides a very easy way to handle HTML elements.
[COLOR=Olive]**And it**[/COLOR]


[LIST]
[*]Supports invalid HTML.
[*]Find tags on an HTML page with selectors just like jQuery.
[*]Extract contents from HTML in a single line.
[/LIST]


**Quick Start**

 [B]How to get HTML elements?
[/B][php]// Create DOM from URL or file
$html = file_get_html('http://www.jooria.com/');

// Find all images
foreach($html->find('img') as $element)
       echo $element->src . '<br>';

// Find all links
foreach($html->find('a') as $element)
       echo $element->href . '<br>'; 
[/php]**How to modify HTML elements?** 
[php]// Create DOM from string
$html = str_get_html('<div id="hello">Hello</div><div id="world">World</div>');

$html->find('div', 1)->class = 'bar';

$html->find('div[id=hello]', 0)->innertext = 'foo';

echo $html; // Output: <div id="hello">foo</div><div id="world" class="bar">World</div>
[/php] [B]
Extract contents from HTML[/B] 
[php]// Dump contents (without tags) from HTML
echo file_get_html('http://www.jooria.com/')->plaintext;
 [/php]
[SIZE=3] [/SIZE]</div>[CENTER][LEFT][CENTER][[FONT=Arial][SIZE=3]script Home[/SIZE][/FONT]]("http://www.jooria.com/scripts/HTML-CSS-133/Simple-html-dom-937/index.html")[SIZE=3][ page]("http://www.jooria.com/scripts/HTML-CSS-133/Simple-html-dom-937/index.html")[/SIZE]
[/CENTER]
[SIZE=3] [/SIZE][CENTER][SIZE=3]_download_[/SIZE]
[/CENTER]
[SIZE=3] [/SIZE][CENTER][SIZE=3][simplehtmldom_1_11.zip [26.58 KB]]("http://www.jooria.com/downloads/454/simplehtmldom_1_11.zip")[/SIZE]
[/CENTER]


And see the source of eamples

[LIST]
[*][example/example_advanced_selector.php *[1.49 KB]*]("http://www.jooria.com/view/file/454/13")
[*][example/example_basic_selector.php *[976 B]*]("http://www.jooria.com/view/file/454/14")
[*][example/example_callback.php *[604 B]*]("http://www.jooria.com/view/file/454/15")
[*][example/example_extract_html.php *[110 B]*]("http://www.jooria.com/view/file/454/16")
[*][example/example_modify_contents.php *[378 B]*]("http://www.jooria.com/view/file/454/17")
[/LIST]

[/LEFT]
[/CENTER]

---

### Post by Reiger on 2009-12-24
But... 

.. Why not use the built-ins?
[PHP]
/**
 * Load HTML from source
 * @param source the source to load; either a file name/URL or a HTML string
 * @param isFile whether or not to treat source as file or as source HTML, defaults to file treatment.
 * @return a DOMDocument object initialized from the given source
 */
function loadHTML($source, $isFile = true) {
  $doc = new DOMDocument();
  $doc->recover=true; /* tell libxml to try and parse broken documents to the best it can */
  
  return $isFile ? $doc->loadHTMLFile($source) : $doc->loadHTML($source);
}

function test() {
  $doc1 = loadHTML('http://www.jooria.com/');
  $xpath = new DOMXpath($doc1);
  $nodeListResult = $xpath->query('div');
  // do stuff with $nodeListResult here?
}
[/PHP]

---

### Post by astkboy2008 on 2009-12-24
> **Reiger said:**
> But... 

.. Why not use the built-ins?
[php]
/**
 * Load HTML from source
 * @param source the source to load; either a file name/URL or a HTML string
 * @param isFile whether or not to treat source as file or as source HTML, defaults to file treatment.
 * @return a DOMDocument object initialized from the given source
 */
function loadHTML($source, $isFile = true) {
  $doc = new DOMDocument();
  $doc->recover=true; /* tell libxml to try and parse broken documents to the best it can */
  
  return $isFile ? $doc->loadHTMLFile($source) : $doc->loadHTML($source);
}

function test() {
  $doc1 = loadHTML('http://www.jooria.com/');
  $xpath = new DOMXpath($doc1);
  $nodeListResult = $xpath->query('div');
  // do stuff with $nodeListResult here?
}
[/php]

thats is very great
but i think the class is more advanced

---

### Post by astkboy2008 on 2009-12-24
is [COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]DOMDocument is built in php
or what[/COLOR][COLOR=#007700][/COLOR][/COLOR]

---

### Post by Reiger on 2009-12-24
When using the DOM API PHP 5 offers you use PHP's bindings to [libxml]("http://xmlsoft.org/") (which is written in C). The PHP functions are essentially an API: Document Object Model is in fact a W3C standard (API) and the exact same method names should work in a Python environment that supports DOM just as well as under PHP. There are various levels of DOM (versions of the API) but that is another matter, and mostly only relevant in e.g. a JavaScript project since the main changes involve additional event models.

DOMDocument is part of a default PHP installation; although its XSL support must be installed as separate package on Ubuntu (php5-xsl) -- and IIRC must then manually be enabled by editing/adding the appropriate php.ini directive (extension=xsl.so).

For an overview of what PHP offers w.r.t. XML: [http://www.php.net/manual/en/refs.xml.php](http://www.php.net/manual/en/refs.xml.php)

---

### Post by astkboy2008 on 2009-12-25
> **Reiger said:**
> When using the DOM API PHP 5 offers you use PHP's bindings to [libxml]("http://xmlsoft.org/") (which is written in C). The PHP functions are essentially an API: Document Object Model is in fact a W3C standard (API) and the exact same method names should work in a Python environment that supports DOM just as well as under PHP. There are various levels of DOM (versions of the API) but that is another matter, and mostly only relevant in e.g. a JavaScript project since the main changes involve additional event models.

DOMDocument is part of a default PHP installation; although its XSL support must be installed as separate package on Ubuntu (php5-xsl) -- and IIRC must then manually be enabled by editing/adding the appropriate php.ini directive (extension=xsl.so).

For an overview of what PHP offers w.r.t. XML: [http://www.php.net/manual/en/refs.xml.php](http://www.php.net/manual/en/refs.xml.php)
nice information
thanks
this mean there is no one will use this class :popcorn:

---

