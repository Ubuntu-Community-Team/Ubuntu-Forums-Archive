---
title: "php and xml *sigh*"
date: 2009-03-01
forum: Programming Talk
---

### Post by cyclobs on 2009-03-01
EDIT:

hey guys, i'm out of ideas but basically i wanna know how to do an efficent way of doing this:
```

<?php
$xml = simplexml_load_file("latest.xml");
$date1 = $xml->news_item1->date." ";
$title1 = $xml->news_item1->title." ";
$text1 = $xml->news_item1->text." ";

$date2 = $xml->news_item2->date." ";
$title2 = $xml->news_item2->title." ";
$text2 = $xml->news_item2->text." ";

$find = array("/n");
$replace = "<br />";
$news_item1 = str_replace($find, $replace, $text1);
$news_item2 = str_replace($find, $replace, $text2);

echo $date1 . "<br />";
echo $title1 . "<br />";
echo "<br />";
echo $news_item1;
echo "<br /><br />";
echo $date2 . "<br />";
echo $title2 . "<br />";
echo "<br />";
echo $news_item2;
?> 
```

can anyone help?

---

### Post by cyclobs on 2009-03-01
this was sort of how i wanted it to be layed to fit onto my site.
```

<?php
$xml = simplexml_load_file("latest.xml");
$date = $xml->news_item->date." ";
$title = $xml->news_item->title." ";
$text = $xml->news_item->text." ";
$find = array("/n");
$replace = "<br />";
$news_item = str_replace($find, $replace, $text);

// Write the xml data into the site
echo "<div class=\"news_section\">";
echo "<p class=\"news_title\">".$title."</p>";
echo "<p class=\"date\">".$date."</p>";
echo "<hr class=\"news\" />";
echo "<p class=\"news_dec\">";
echo "$news_item;
echo "</p>";
echo "<hr class=\"news\" />";
echo "</div>";
?>

```

XML file contains:
```

<?xml version="1.0" encoding="UTF-16" ?>
<!--		News xml file		-->

<news>
	<news_item>
		<title>Melville Got Banned</title>
		<date>27/2/09 2:00pm</date>
		<text>
		Melville got banned from the school network!/n
		Sucked in sucker.
		</text>
	</news_item>
	
	<news_item>
		<title>New Website</title>
		<date>22/2/09</date>
		<text>
		Hey guys,/n/n
		Finially got our website built and up. not much to it just yet we need to do a fair bit of work to it. But it's here for you guys and as we get some songs recorded and some upcoming events we'll let you guys know on here./n/n
		Bang your heads!
		</text>
	</news_item>
</news>

```

---

### Post by hastur on 2009-03-01
hi,

not sure if this will help in your case, because this solution is not "simple"...
I do the same kind of things on my website : 
- I load the xml file using the DOM extension (by default in php), 
- then I load an xsl stylesheet with the DOM, 
- and finally I transform the xml in the desired html string using the XSL extension (XSLT processor, included by default but must be enabled by --with-xsl).

note : you can also serve the page as an xml file "including" the xsl stylesheet, the browser will do the transformation for you. I didn't like this way of doing things, since not all browsers will understand xml+xsl, but if you're fine with serving only for recent browsers...

---

### Post by cyclobs on 2009-03-02
doesn't really help me.

i'm trying to learn how to do it but all of the tutorials i've looked at so far just make me really confused

---

### Post by hastur on 2009-03-02
> **cyclobs said:**
> 
i'm trying to learn how to do it


if you are refering to xsl stylesheets, you can try the tutorial at w3schools : short, easy to understand, shows good practice.
[http://www.w3schools.com/Xsl/default.asp]("http://www.w3schools.com/Xsl/default.asp")

I also wrote a simple stylesheet as an exemple (just copy the two files in a directory, then open the xml file with a xsl-aware browser like firefox):

news.xml
```
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="news.xsl"?>
<news>
	<news_item>
		<title>Melville Got Banned</title>
		<date>27/2/09 2:00pm</date>
		<text>
		Melville got banned from the school network!
		Sucked in sucker.
		</text>
	</news_item>
	<news_item>
		<title>New Website</title>
		<date>22/2/09</date>
		<text>
		Hey guys,
		Finally got our website built and up. not much to it just yet we need to do a fair bit of work to it. But it's here for you guys and as we get some songs recorded and some upcoming events we'll let you guys know on here.
		Bang your heads!
		</text>
	</news_item>
</news>

```

news.xsl
```

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
<html>
	<body>
		<xsl:apply-templates select="//news_item" />
	</body>
</html>
</xsl:template>

<xsl:template match="//news_item">
	<div>
		<h3><xsl:value-of select="title" /></h3>
		<p><xsl:value-of select="date" /></p>
		<hr />
		<p><xsl:value-of select="text" /></p>
		<hr />
	</div>
</xsl:template>

</xsl:stylesheet>

```

once you've learned about xsl stylesheet and practiced a little with statics files, you can try your first php transformations :
- first learn to load xml file with DOM. I learned by reading the php manual page about the extension :
[http://fr2.php.net/dom]("http://fr2.php.net/dom")
- then learn how to do the transformation :
[http://fr.php.net/xsl]("http://fr.php.net/xsl")

---

### Post by cyclobs on 2009-03-02
i got it :D

after about 2 hours of reading and coding i've worked out how to do it :D

---

