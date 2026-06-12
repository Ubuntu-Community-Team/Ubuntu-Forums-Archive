---
title: "C++ or PHP RSS reading library"
date: 2010-04-09
forum: Programming Talk
---

### Post by imblack on 2010-04-09
Hello!

Can anyone please tell me a simple to use RSS reading library for C++ or PHP?
Like I just want to extract news/updates title and description thats it, all text.

I used TinyXml parser with C++ and Curl to make something, but it crashes on BBC.co.uk's RSS feed, only on that, digg.com etc work fine.

Please save me some time and if you want I can share my solution too.

Thanks!

---

### Post by cszikszoy on 2010-04-10
I've ussed LastRSS before, and it's very simple but pretty good.  It's PHP.  Give it a try: [http://lastrss.oslab.net/](http://lastrss.oslab.net/)

---

### Post by Reiger on 2010-04-10
I must be a bit annoying by now; but alternatively you can use a half decent XSL stylesheet to extract what you need, format it as you need and output.

Try something like:

script.php
[php]
<?php
/* 
 * left to the reader to implement, 
 * should return the path to the XSL sylesheet.
 */
function stylesheet();

/*
 * left to the reader to implement,
 * should return the URL of the RSS feed
 */
function getURL();

$contents = file_get_contents(getURL());
$rssDoc = new DOMDocument();
$rssDoc->loadXML($contents);

$xslDoc = new DOMDocument();
$xslDoc->loadXML(stylesheet());

$xslProc = new XSLTProcessor();
$xslProc->importStylesheet($xslDoc);

$result= $xslProc->transformToXML($rssDoc);
echo $result;
[/php]

And an XSL stylesheet like this:
```

<?xml version="1.0" encoding="utf-8"?>
<xsl:transform version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <!-- 
    - edit this to be suitable for your OS 
    - &#x0A is the linefeed (\n)
    - &#x0D is the carriage return (\r)
   -->
  <xsl:variable name="LINE_BREAK" select="'&#x0A;'"/>
  <xsl:template match="//*[local-name() = 'item']/*">
     <!-- output element name, e.g. 'description' -->
     <xsl:value-of select="concat(local-name(),':')"/>
     <xsl:value-of select="$LINE_BREAK"/>
     
     <!-- output text content -->
     <xsl:value-of select="text()"/>
     <xsl:value-of select="$LINE_BREAK"/>
  </xsl:template>
</xsl:transform>

```

---

### Post by imblack on 2010-04-10
Much appreciated mate. I'll try both of these and will get back, moreover if some one has other options tell me please.

---

### Post by imblack on 2010-04-10
> **cszikszoy said:**
> I've ussed LastRSS before, and it's very simple but pretty good.  It's PHP.  Give it a try: [http://lastrss.oslab.net/](http://lastrss.oslab.net/)

I must say I am loving this thing. So so straight forward and exactly what i wanted :)
and Thanks Reige, if something comes in way of using above solution ill try yours :)

And if you are curious, I have a free(as of yet) SMS based service that let you find people, make groups etc and I am adding RSS reader to it so the subscribed users get frequent update of feeds they have subscribed to through text messages.
Hope you like the idea.

---

### Post by ja660k on 2010-04-10
try this
[http://pear.php.net/package/XML_RSS](http://pear.php.net/package/XML_RSS)

if you have PEAR modules enabled in php that is.
and it comes with an example...

[PHP]
Fetching headlines from Slashdot
<?php
require_once "XML/RSS.php";

$rss =& new XML_RSS("http://rss.slashdot.org/Slashdot/slashdot");
$rss->parse();

echo "<h1>Headlines from <a href=\"http://slashdot.org\">Slashdot</a></h1>\n";
echo "<ul>\n";

foreach ($rss->getItems() as $item) {
    echo "<li><a href=\"" . $item['link'] . "\">" . $item['title'] . "</a></li>\n";
}

echo "</ul>\n";
?>

[/PHP]

---

### Post by imblack on 2010-04-10
I have heard bad things about PEAR, can you please give me a brief overview?
I know that it has been around long enough.

---

