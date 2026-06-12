---
title: "XML/XSLT: Reading in xml files"
date: 2008-12-18
forum: Programming Talk
---

### Post by munkyeetr on 2008-12-18
I am new to using xml/xslt and this is my situation:

I have an xml file (index.xml) which is rendered using the stylesheet index.xsl. This works great.

Now, from index.xsl I want to read in my footer information which is stored in the file footer.xml.

```

<!-- This is footer.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<footer>
	<line text="some footer text here"/>
	<line text="some more footer text here"/>
</footer>

```

I have tried a bunch of different ways to do this, none successful. Here's the last way I tried; this code is in index.xsl:
```

<xsl:for-each select="document('footer.xml')/line">
        <xsl:value-of select="@text" /><br />
</xsl:for-each>

```

and I get nothing. As I say, I've tried a bunch of stuff and nothing has worked so far. There has to be an easy way in XSLT to say:

[I]1) Use this file (footer.xml)
2) Read this/these nodes[/I]

Any help, code snippet, or a push in the right direction is appreciated.

---

### Post by Sportingfan on 2009-02-26
Are you referring to the xsl stylesheet in your footer.xml?
Read the tutorial on [w3schools]("http://www.w3schools.com/xsl").

---

### Post by hastur on 2009-02-26
hi,

your XPath is wrong, I tried with :

```

document('footer.xml')/footer/line

```
and with
```

document('footer.xml')//line

```

and it works fine

---

