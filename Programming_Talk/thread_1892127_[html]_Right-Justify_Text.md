---
title: "[html] Right-Justify Text"
date: 2011-12-07
forum: Programming Talk
---

### Post by dodle on 2011-12-07
I recently built a site with multi-language support. I'm trying to switch the layout of the page for right-to-left languages and the text that I have justified I would like to keep so. CSS doesn't have an option to right-justify text. Does anyone know how I can achieve this?

[php]<?php
$lang = GetLanguage(); // Function to get the browsers' preferred language
$rtol_langs = array(1 => 'ar', 'he');
$rtol = array_search($lang, $rtol_langs);

$align = 'left';
$justify = 'justify';
if ($rtol)
{
    $align = 'right';
    $justify = (something to right-justify here);
}

print("<html lang=$lang>
<head>
<title>Direction Test</title>

<style type=text/css>
  .normal {text-align: $align}
  .justify {text-align: $justify}
</style>

<body>
<h3 class=normal>This is some normal text</h3>
<br>
<h3 class=justify>This is some justified text</h3>
</body>
</html>"
?>[/php]

Is there a better way to do this using PHP or JavaScript? I think I might also run into problems with centered text.

---

### Post by CoffeeRain on 2011-12-07
The code for aligning right is <p align="right">text</p>. You could try to fit that in where it needs to be.

---

### Post by dodle on 2011-12-07
That aligns it "right", but it does not "justify" it. Anyway, I found a very simple answer: Just include "dir=rtl" in the html tag and let the browser do all the aligning of the elements and text.

[php]<?php
$lang = GetLanguage(); // Function to get the browsers' preferred language
$rtol_langs = array(1 => 'ar', 'he');
$rtol = array_search($lang, $rtol_langs);

if ($rtol)
    $pagedir = ' dir=rtl';

print("<html lang=$lang$pagedir>
<head>
<title>Direction Test</title>

<body>
<h3>This is some normal text</h3>
<br>
<h3 style=text-align:justify>This is some justified text</h3>
</body>
</html>"
?>[/php]

[php]<html lang=ar dir=ltr>
<head>
<title>Direction Test</title>

<body>
<h3>This is some normal text</h3>
<br>
<h3 style=text-align:justify>This is some justified text</h3>
</body>
</html>[/php]

---

