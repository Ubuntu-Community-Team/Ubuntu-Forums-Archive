---
title: "XSLT help please"
date: 2011-07-26
forum: Programming Talk
---

### Post by mahy on 2011-07-26
Hi y'all,

it seems I can't overcome this peculiar problem: I need XSLT to produce this **literal text** in the output document (a DocBook section):

```
&some-bogus-name;
```

And the output MUST NOT be enclosed in comments: <!-- -->

I tried just about every combination of <xsl:text>, <xsl:comment>, CDATA and so on, but I just can't make it flush properly. I'm using xsltproc, and the parser either complains about an undefined entity, or encloses the problematic line in an HTML comment, or is the resulting xml file invalid and unable to be parsed by DocBook and DBLaTeX parsers... :(

Any help will be much appreciated, thanks in advance!

---

### Post by Arndt on 2011-07-26
> **mahy said:**
> Hi y'all,

it seems I can't overcome this peculiar problem: I need XSLT to produce this **literal text** in the output document (a DocBook section):

```
&some-bogus-name;
```

And the output MUST NOT be enclosed in comments: <!-- -->

I tried just about every combination of <xsl:text>, <xsl:comment>, CDATA and so on, but I just can't make it flush properly. I'm using xsltproc, and the parser either complains about an undefined entity, or encloses the problematic line in an HTML comment, or is the resulting xml file invalid and unable to be parsed by DocBook and DBLaTeX parsers... :(

Any help will be much appreciated, thanks in advance!

Is it acceptable if it produces

```
&amp;some-bogus-name;
```

instead? The result ought to be the same if the DocBook text is meant as XML input to something.

To get that, just write it exactly like that in the xslt stylesheet.

---

### Post by mahy on 2011-07-26
Unfortunately, that is not acceptable, the DocBook parser does not accept it.

I **partially** succeeded with this:

```
<xsl:text disable-output-escaping="yes">
&#xa;&#x26;some-bogus-name;&#xa;
</xsl:text>
```

But there's still one problem: the resulting XML file, instead of being neatly formatted (pretty-printed), is vomited onto 4 mile-long lines. That does not affect machine-readability, but it does affect human-readability. :(

---

### Post by Reiger on 2011-07-26
It seems highly unlikely an XML parser is unable to deal with &amp; which is defined by the XML spec AFAIK. However if you find your docbook tools are broken, maybe they will accept  instead? You could try outputing that, i.e:
```

<xsl:text>&amp;amp;some-bogus-name;</xsl:text>

```
becomes:
```

<xsl:text>&amp;#26;some-bogus-name;</xsl:text>
```

---

### Post by mahy on 2011-07-27
> **Reiger said:**
> It seems highly unlikely an XML parser is unable to deal with &amp; which is defined by the XML spec AFAIK. 

But can you use "&amp;" as a substitute for ampersand in an **entity name**? E.g. the copyright sign has the entity name "&copy;". Can you use "&amp;copy;" instead? Of course not. What I need is to produce an "entity" by XSLT, which in reality is a DocBook **include link** and is to be picked up by a DocBook parser.

As to that I already found a solution (written in my previous post), but the resulting XML is not pretty-printed, but garbled. That is the because of the **<xsl:text>** element which confuses the parser I use, xsltproc. (I already mailed libxslt developers about this issue.)

The solution you propose is not necessary. What would really help is a workaround without any <xsl:text> element. Unless the libxslt developers suggest a workaround or admit and fix a bug, I'm afraid I'll have to introduce that problematic line by sed... ](*,)

---

### Post by Arndt on 2011-07-27
> **mahy said:**
> But can you use "&amp;" as a substitute for ampersand in an **entity name**? E.g. the copyright sign has the entity name "&copy;". Can you use "&amp;copy;" instead? Of course not. What I need is to produce an "entity" by XSLT, which in reality is a DocBook **include link** and is to be picked up by a DocBook parser.

As to that I already found a solution (written in my previous post), but the resulting XML is not pretty-printed, but garbled. That is the because of the **<xsl:text>** element which confuses the parser I use, xsltproc. (I already mailed libxslt developers about this issue.)

The solution you propose is not necessary. What would really help is a workaround without any <xsl:text> element. Unless the libxslt developers suggest a workaround or admit and fix a bug, I'm afraid I'll have to introduce that problematic line by sed... ](*,)

What is it that makes DocBook accept &copy and not xsltproc? If it is some kind of entity declaration, you can perhaps include the same declaration in the style sheet.

You did write "bogus", so at least I thought you wanted that string as literal text for the end user to see.

---

### Post by mahy on 2011-07-27
> **Arndt said:**
> What is it that makes DocBook accept &copy and not xsltproc? If it is some kind of entity declaration, you can perhaps include the same declaration in the style sheet.

You did write "bogus", so at least I thought you wanted that string as literal text for the end user to see.

Yes, I want literal "&some-bogus-name;" to appear in the output XML (which in turn is an input for DocBook).

However, such entity is never explicitly declared in DocBook. If it were, I'd just copy the declaration to my XSL stylesheet. DocBook simply tries to find a file with matching name and then includes its content. That's why I wrote it's an "include link".

But I already solved this part and now I'm facing a well-formed but garbled XML output.

---

### Post by Reiger on 2011-07-27
What are we looking at?

If you want to XSLT *produce* "&copy;" you output "&amp;copy;". Doesn't have to be done through <xsl:text>, could be part of anything which emits PCDATA or attribute values.

If you want a generic XML parser to *read* &copy; for use with XSLT this is not going to work because copy is an entity name not defined in the XML spec. You'd have to grab the Unicode code point, or just copy-paste ©. (Type: Alt-Gr + C on a keyboard using US Intl with Alt-Gr dead keys layout.)

---

### Post by mahy on 2011-07-28
> **Reiger said:**
> What are we looking at?

If you want to XSLT *produce* "&copy;" you output "&amp;copy;". Doesn't have to be done through <xsl:text>, could be part of anything which emits PCDATA or attribute values.


Can you perhaps give an example? I tried it myself, and when I put
```

&amp;some-bogus-name;
```

it stays like that after XSLT, which is not what I want...

---

### Post by Reiger on 2011-07-28
If this is text.xsl:
```

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
                version="1.0">
  <xsl:template match="/">
    <root><xsl:text>This is the HTML entity for the © symbol: &amp;copy;</xsl:text></root>
  </xsl:template>
</xsl:stylesheet>

```

And this is test.xml:
```

<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="test.xsl"?>
<root/>

```

Then the XSLT processor should output:
```

<root>
This is the HTML entity for the © symbol: &copy;
</root>

```

Change output method to "text" and the <root> tags are removed, but the text stays the same.

That works for any entity you care to enter because the &amp; is converted to & in the output. Now the only thing to worry about is whether or not the parser which reads the output of the XSLT understands &copy;. If not, then use the Unicode code point because any conforming XML parser is required to handle that.

---

### Post by Arndt on 2011-07-28
> **Reiger said:**
> If this is text.xsl:
```

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
                version="1.0">
  <xsl:template match="/">
    <root><xsl:text>This is the HTML entity for the © symbol: &amp;copy;</xsl:text></root>
  </xsl:template>
</xsl:stylesheet>

```

And this is test.xml:
```

<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="test.xsl"?>
<root/>

```

Then the XSLT processor should output:
```

<root>
This is the HTML entity for the © symbol: &copy;
</root>

```

Change output method to "text" and the <root> tags are removed, but the text stays the same.

That works for any entity you care to enter because the &amp; is converted to & in the output. Now the only thing to worry about is whether or not the parser which reads the output of the XSLT understands &copy;. If not, then use the Unicode code point because any conforming XML parser is required to handle that.

I'm not qualified to say whether you or xsltproc or neither is wrong, but what I get is this:

```
<?xml version="1.0"?>
<root>This is the HTML entity for the © symbol: &amp;copy;</root>

```

---

### Post by Reiger on 2011-07-28
Well obviously, xsltproc is wrong. ;) No, seriously, it is wrong. The content of <xsl:text> is PCDATA as per the [XSLT spec]("http://www.w3.org/TR/xslt#section-Creating-Text"), so &amp; is & therefore, &amp;copy; is &copy;.

But you can work around this. You said the XML output was not very pretty once you added output-escaping to the mix, however if I change the template to this:
```

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
                version="1.0">
  <xsl:output method="xml" indent="yes"/>
  <xsl:template match="/">
    <root>
      <foo><xsl:text disable-output-escaping="yes">This is the HTML entity for the © symbol: &amp;copy;</xsl:text></foo>
    </root>
  </xsl:template>
</xsl:stylesheet>

```
And run xsltproc on it:
```
$ xsltproc test.xsl test.xml
<?xml version="1.0"?>
<root>
  <foo>This is the HTML entity for the © symbol: &copy;</foo>
</root>

```
... then maybe just file a bug report against xsltproc?

---

### Post by mahy on 2011-07-29
Guys, many thanks for your replies. I'm considering filing a bug, probably through Launchpad.

Anyway, even if that bug was fixed, it **wouldn't** solve my problem, since the <xsl:text> element breaks up indentation and I can't wrap it in a meaningless element, like Reiger did (<foo>), to restrict that indentation breakup. There is simply no such acceptable element in DocBook.

I sort of gave up and instead of my desired inclusion link, I have XSLT produce a meaningless element <span class="replacement"/>, and then I have "sed" run through the file and replace that element with "&inclusion-link;".

Guaranteed to work like a charm on every Linux/Unix and gives me valid and neatly-formatted XML DocBook file. :popcorn:

---

### Post by Reiger on 2011-07-29
You don't need the <foo> element. I added it to see if it would produce the problem you described earlier, but it didn't -- looks like xsltproc can be made to behave with the indent="yes" option in the <xsl:output> element.

---

