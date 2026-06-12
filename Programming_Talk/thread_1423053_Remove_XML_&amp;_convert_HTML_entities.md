---
title: "Remove XML &amp; convert HTML entities"
date: 2010-03-06
forum: Programming Talk
---

### Post by Paddy Landau on 2010-03-06
I wonder if this is possible in Bash.

I want to take an XML file and remove all XML codes, and convert HTML entities back to their original characters, also changing all whitespace to a single space.

For example, suppose I have a file with the following (it's a nonsense example just for illustration):
[html]<?xml version="1.0" encoding="UTF-8"?>
<dc:date>2010-03-06T11:02:17</dc:date>
<meta:initial-creator>Chris    &amp;    Sandy</meta:initial-creator>
<text:span text:syle-name="XY">&lt;&lt;Here this!&gt;&gt;</text:span>[/html]I'd like to remove all the XML codes and convert the [FONT=Courier New]&amp;[/FONT], [FONT=Courier New]&lt;[/FONT] and [FONT=Courier New]&gt;[/FONT] to [FONT=Courier New]&[/FONT], [FONT=Courier New]<[/FONT] and [FONT=Courier New]>[/FONT], and convert all whitespace into a single space. Thus:
```
2010-03-06T11:02:17 Chris & Sandy <<Hear this!>>
```I've been wracking my brains but haven't found a simple solution.

(I could make a complex program for this, but I was wondering whether there was a way to use some type of regex like egrep, which of course would be far more efficient than a complex Bash program! If I knew C++ I could use that, but I don't.)

Question: Do you know of a simple way to achieve what I need? Even just the names of the commands would be great; I could look up the options and syntax.

---

### Post by howlingmadhowie on 2010-03-06
this could get you started:

```

cat file.xml | sed -e 's/<[^>]*>//g' -e 's/&lt;/</g' -e 's/&gt;/>/g' -e 's/&amp;/\&/g' -e 's/ \{1,\}/ /g' | tr -d '\n'

```

let's see what the forum software makes of the html entities.

unfortunately i don't know what the record separator in your xml file looks like.

---

### Post by Reiger on 2010-03-06
Hmm... let's see: I think this XSLT ought to do the trick:

```

<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
<xsl:template match="text()">
  <xsl:copy-of select="normalize-space(.)"/>
</xsl:template>
</xsl:styelsheet>

```

*Note: it dumps everything to a single line like the example output you posted.

Alternatively; you can use something like SAX since its parsing model (callbacks when certain bits of document are found) fits your intended output nicely.

---

### Post by Hellkeepa on 2010-03-06
HELLo!

If you have PHP-cli installed, this is all you need:
[php]#!/usr/bin/php
<?php
$String = html_entity_decode (strip_tags (file_get_contents ($argv[1])), ENT_QUOTES, 'utf-8')."\n";
echo preg_replace ("/\s+/u", " ", $String);
?>[/php]
Made this UTF-8 compatible, but it can be expanded with a test to detect other charsets if there is a possibility of other charsets being used.

Happy codin'!

---

### Post by Paddy Landau on 2010-03-06
> **howlingmadhowie said:**
> ... sed ...
sed looks perfect for my needs, thank you. I shall read the manual to understand what you've been doing.

> **Reiger said:**
> ... XSLT ...
Ha! I learn something every day. I had not heard of XSL, and now I find out not only that what I displayed was not XML but XSL, but also that there is something called XSLT.

Thanks for the idea.

I'm looking at XSLT on Google now. How does one 'run' XSLT against a file?

> **Hellkeepa said:**
> ... PHP-cli ...
Thanks for the idea, but the computers that will run it cannot be guaranteed to have PHP.

---

### Post by Paddy Landau on 2010-03-06
I'm struggling a little with sed. I wanted to add the following expression to remove linefeeds:
[FONT=Courier New][COLOR=Navy]-e 's/\n/ /'[/COLOR][/FONT]
but of course that doesn't work. So, I used the following:
[FONT=Courier New][COLOR=Navy]-e 'N'[/COLOR][/FONT]
which is supposed to add the next line onto the current line, but that didn't work either. So, I had to use [FONT=Courier New][COLOR=Navy]tr[/COLOR][/FONT] instead. (I did see an example of [using 'N' in sed to merge lines]("http://www.zytrax.com/tech/web/regex.htm#sed") -- scroll down to #15 *Strip HTML tags* -- but I can't understand why my version doesn't work. Maybe you can tell me what I did wrong?)

Anyway, I've ended up with this:
```
tr '\n' ' ' <file.xml | sed -re 's/<[^>]*>/ /g;s/\s+/ /g'
```
[LIST]
[*][FONT=Courier New][COLOR=Navy]tr '\n' ' '[/COLOR][/FONT] converts linefeeds to a single space
[*][FONT=Courier New][COLOR=Navy]s/<[^>]*>/ /g[/COLOR][/FONT] removes the XML statements
[*][FONT=Courier New][COLOR=Navy]s/\s+/ /g[/COLOR][/FONT] converts all whitespace to a single space
[/LIST]
Apart from the HTML entities, that works perfectly!

My question now is HTML entities, if anyone knows. There are many HTML entities, and I'm wondering whether some program has knowledge of them (like PHP's [FONT=Courier New][COLOR=Navy]html_entity_decode[/COLOR][/FONT]), otherwise I'll have to laboriously list them all out from the [HTML character specifications]("http://www.w3.org/TR/html4/sgml/entities.html").

---

### Post by Paddy Landau on 2010-03-06
> **Paddy Landau said:**
> My question now is HTML entities, if anyone knows.
Well, I have discovered that the [sgml-data]("apt:sgml-data") package (installed by default, it seems) provides a list of all the entities. Files:
[FONT=Courier New] /usr/share/xml/entities/xml-iso-entities-8879.1986/*.ent[/FONT]

However, I'm quite clueless as to how to make use of the information in these files!

I'm crossing my fingers that some command already exists to convert from (say) [FONT=Courier New][COLOR=Navy]&gt;[/COLOR][/FONT] to [FONT=Courier New][COLOR=Navy]>[/COLOR][/FONT].

---

### Post by howlingmadhowie on 2010-03-06
provided you only expect entities like &amp; or &uuml; (in other words, entities of the form &<some letters>; ) you can probably grep for these in the files of /usr/share/xml/entities/* and then replace them in the output text.  something like this:
```

ENTITIY='&uml;'
ENT_TMP=`echo $ENTITY | sed -e 's/&\([^;]\{1,\}\);/\1/'`
UNICODENUMBER=`grep $ENT_TMP /usr/share/entities/xml-iso-entities-8879.1986/*.ent | sed -e 's/.*&#x\([^;]\{1,\}\).*/\1/'`
echo -e '\u'$UNICODENUMBER

```

but it ain't pretty.

---edit---

forgot to add, i'm using zsh at the moment. echo -e '\uXXXX' doesn't work under bash.

---

### Post by Reiger on 2010-03-06
> **Paddy Landau said:**
> I'm looking at XSLT on Google now. How does one 'run' XSLT against a file?

Depends on how you want to display output. If you want to display the results in, say, a webbrowser or similar &#8220;agent&#8221; then it is probably easiest to inject an XML processor instruction:

```

<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="path/to/xsl/file.xsl"?>
<!-- document content below -->

```

If not, then there are various commandline XSLT processors; e.g. xsltproc; as well as bindings (libraries) to a host of other programming languages. Aforementioned PHP has library functions for XSLT in the form of bindings to libxml (the GNOME XML library); and so do Python, Perl etc. etc.

*Note: my original example had a flaw in case true plain text output was desired: this example is better:
```

<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
<!-- previous example forgot to include this output line
  -  it could have resulted in errors depending on how the XSLT file was used
 -->
<xsl:output method="text"/>
<xsl:template match="text()">
  <xsl:copy-of select="normalize-space(.)"/>
</xsl:template>
<!-- previous example had a typo: order of l and e was wrong in stylesheet -->
</xsl:stylesheet>

```

---

### Post by Paddy Landau on 2010-03-08
> **Reiger said:**
> ... xsltproc ... this example is better ...
Wow, this is an incredible piece of simplicity! Thank you. I had no idea of the power of this XSL.

I've used the following command. [FONT=Courier New]sh.xsl[/FONT] contains the code that you gave me (I assumed the extension [FONT=Courier New].xsl[/FONT]; what is the usual default?). [FONT=Courier New]my.xml[/FONT] contains my XML data.
```
xsltproc sh.xsl my.xml
```There is one frustrating problem, though; it eliminates spaces between sections. Is there any way to maintain a space between two different parts?

I'll give you an example. An extract from my test XML file:
[html]an <text:span text:style-name="T1">eye</text:span>[/html]After running through xmlproc, this results in "aneye" instead of "an eye"; it has eliminated the space between them. How can I retain the spaces?

---

### Post by Reiger on 2010-03-08
Well, normalize-space(.) does that: it removes ingorable whitespace (leading and trailing whitespace as well as substituting multiple whitespace characters for a single one.

If you want everything on a line, this alternative should work well enough:
```

<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:text="com.test.www">
<xsl:output method="text"/>
<xsl:preserve-space elements="* xml:* text:*"/>
  <xsl:template match="/">
    <xsl:value-of select="normalize-space(//*)"/>
  </xsl:template>
</xsl:stylesheet>

```

Tested it with the built in XSLT processor of the Opera web browser on a sample document created from your original post:
```

<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="test.xsl"?>
<text:root xmlns:text="com.test.www">
<text:date>2010-03-06T11:02:17</text:date>
<text:initial-creator>Chris    &amp;    Sandy</text:initial-creator>
<text:span text:syle-name="XY">&lt;&lt;Here this!&gt;&gt;</text:span>
<text:span>I got an <text:span text:style-name="T1">eye</text:span></text:span>
</text:root>

```

The output I got was:
```

2010-03-06T11:02:17 Chris & Sandy <<Here this!>> I got an eye

```

EDI: If you don't understand what the code is doing you may want to spend some time reading the excellent introduction over at W3C schools:
[http://www.w3schools.com/Xsl/default.asp](http://www.w3schools.com/Xsl/default.asp) (this explains the XSLT language)
[http://www.w3schools.com/Xsl/xsl_functions.asp](http://www.w3schools.com/Xsl/xsl_functions.asp) (this lists the functions library)

---

### Post by Paddy Landau on 2010-03-08
> **Reiger said:**
> If you don't understand what the code is doing...
Thank you for the links and the revised code. I found that your code, simplified as follows, still works:
```
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:text="com.test.www">
<xsl:output method="text"/>
<xsl:preserve-space elements="* xml:* text:*"/>
</xsl:stylesheet>
```I don't know why, but it doesn't matter, because it works!

If I explain what I'm doing, perhaps you'll understand where I'm coming from.

There is currently no facility to search OpenOffice documents (.odt files) for content, something that I sometimes need (e.g. find all documents that refer to "hypnosis research").

OpenOffice contents are stored in XML files. If I can extract the content from an XML file -- which I can do now, thanks to you! -- then I can write a very simple script to do this.

Thanks to all who contributed to the thread. I shall mark this as 'solved.'

---

### Post by Paddy Landau on 2010-03-08
Hmm, even this seems to do the job:
```
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:text="com.test.www">
<xsl:output method="text"/>
</xsl:stylesheet>
```Interesting.

---

### Post by Reiger on 2010-03-08
! I think that would be because there are certain &#8220;default&#8221; rules in XSLT that you can override. I expect that by default text is copied over to output.

---

