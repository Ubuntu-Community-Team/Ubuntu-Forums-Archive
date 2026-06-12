---
title: "[SOLVED] PHP Get ALL Links in a page"
date: 2008-07-04
forum: Programming Talk
---

### Post by LinuxRocks713 on 2008-07-04
Hi:

How do I get all links in a page? For example ,if I have a page:

<html>
<head></head>
<body>
<a href="/link1">Link1</a>
<a href="http://aaa.com/>Link2</a>
<h3><small><a href="a/b/c.php">Link Text</small></h3>
<a href="ftp://server.net/">Link...</a>
</body>
</html>

and it returns an array:

Array[0] = "/link1"
Array[1] = "http://aaa.com/"
Array[2] = "a/b/c.php"
Array[3] = "ftp://server.net/"

How do you do this

---

### Post by LaRoza on 2008-07-04
[http://www.php.net/dom](http://www.php.net/dom)

You can use the DOM to get all such elements. getElementsByTagName()

---

### Post by slavik on 2008-07-04
regex solution in Perl:

```

...
$html; #assume this var has the HTML code
@links = $html =~ /href=\"(.*?)\"/gis;
...

```

---

### Post by LinuxRocks713 on 2008-07-04
> **LaRoza said:**
> [http://www.php.net/dom](http://www.php.net/dom)

You can use the DOM to get all such elements. getElementsByTagName()

How do you return it in an array? It's return type is a DOMNodeList object.

---

### Post by henchman on 2008-07-04
hi :)

just stick to the php.net documentation, it always has good examples :)

[http://us2.php.net/domnodelist](http://us2.php.net/domnodelist)

```
foreach ($nodeList as $node) {
  echo $node->nodeValue;
}
```

---

### Post by LinuxRocks713 on 2008-07-04
> **henchman said:**
> hi :)

just stick to the php.net documentation, it always has good examples :)

[http://us2.php.net/domnodelist](http://us2.php.net/domnodelist)

```
foreach ($nodeList as $node) {
  echo $node->nodeValue;
}
```

Though it returns this:

```

Link1
Link2
Link Text
Link...

```

Here is test.php:
[php]
<?php

$doc = new DOMDocument;
$doc->load('file.htm');

$items = $doc->getElementsByTagName('a');

foreach($items as $value) {
        echo $value->nodeValue . "\n";
};

?>
[/php]

and here is file.htm:

```

<html>
<head>
<title>Title Page</title>
</head>
<body>
<a href="/link1" target="_blank">Link1</a>
<a href="http://aaa.com/">Link2</a>
<h3><small><a href="a/b/c.php">Link Text</a></small></h3>
<a href="ftp://server.net/">Link...</a>
</body>
</html>

```

---

### Post by LaRoza on 2008-07-04
> **slavik said:**
> regex solution in Perl:


In PHP in case the title didn't work ;)

---

### Post by henchman on 2008-07-05
well, the PHP-documentation also has a site on the topic XMLNode located here:

[http://usphp.com/manual/en/class.domnode.php#domnode.props.attributes](http://usphp.com/manual/en/class.domnode.php#domnode.props.attributes)

object of this class have an attribute called "attributes" *grml* which is an instance of the class "DOMNamedNodeMap". Documentation for that class is here:

[http://usphp.com/manual/en/class.domnamednodemap.php](http://usphp.com/manual/en/class.domnamednodemap.php)

It again has several methods. You may try to retrieve the href attribute that way :)

---

### Post by LinuxRocks713 on 2008-07-05
> **henchman said:**
> well, the PHP-documentation also has a site on the topic XMLNode located here:

[http://usphp.com/manual/en/class.domnode.php#domnode.props.attributes](http://usphp.com/manual/en/class.domnode.php#domnode.props.attributes)

object of this class have an attribute called "attributes" *grml* which is an instance of the class "DOMNamedNodeMap". Documentation for that class is here:

[http://usphp.com/manual/en/class.domnamednodemap.php](http://usphp.com/manual/en/class.domnamednodemap.php)

It again has several methods. You may try to retrieve the href attribute that way :)

Thanks! It worked.

If anyone wants the test.php file:

[php]
<?php


$doc = new DOMDocument;
$doc->load('file.htm');

$items = $doc->getElementsByTagName('a');

foreach($items as $value) {
	echo $value->nodeValue . "\n";
	$attrs = $value->attributes;
	echo $attrs->getNamedItem('href')->nodeValue . "\n";
};

?>

[/php]

---

