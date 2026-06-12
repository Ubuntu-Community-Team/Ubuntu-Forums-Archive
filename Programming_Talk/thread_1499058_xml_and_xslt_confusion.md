---
title: "xml and xslt confusion"
date: 2010-06-01
forum: Programming Talk
---

### Post by denarced on 2010-06-01
I'm currently receiving data in an xml format and I usually convert it to a website using xsl-stylesheets. Everything was all fine until they started using namespaces in theirs xml. Now I'm pretty much clueless. I just don't understand how to write an xsl stylesheet when playing with namespaces.
Could you please tell me what's wrong with the following xsl-stylesheet when used with the xml file also included.
xml:
```

<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet href="style.xsl" type="text/xsl" ?>
<root xmlns:tr="http://www.mozilla.org/projects">
<tr:collection>
    <tr:item>
        <tr:name value="Joe" />
        <tr:age value="34" />
    </tr:item>
    <tr:item>
        <tr:name value="Joanna" />
        <tr:age value="21" />
    </tr:item>
    <tr:item>
        <tr:name value="Derek" />
        <tr:age value="99" />
    </tr:item>
    <tr:item>
        <tr:name value="Dorothy" />
        <tr:age value="41" />
    </tr:item>
</tr:collection>
</root>

```
xsl:
```

<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
xmlns:tr="http://www.mozilla.org/projects">
<xsl:output method="html" omit-xml-declaration="yes" />
    <xsl:template match="/">
        <html><head><title></title></head><body>
            <table>
                <xsl:for-each select="item">
                    <xsl:value-of select="name"></xsl:value-of>
                    <tr:value-of select="name"></tr:value-of>
                </xsl:for-each>
            </table>
        </body></html>
    </xsl:template>
</xsl:stylesheet>

```

---

### Post by denarced on 2010-06-01
Ok, I'm making progress. Same deal but a little better xml and xsl definitions. Here goes:
data.xml:
```

<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet href="style.xsl" type="text/xsl" ?>
<root xmlns:tr="http://www.mozilla.org/projects">
<tr:collection>
	<tr:item>
		<tr:name type="given">Joe</tr:name>
		<tr:age>34</tr:age>
	</tr:item>
	<tr:item>
		<tr:name type="given">Joanna</tr:name>
		<tr:age>21</tr:age>
	</tr:item>
	<tr:item>
		<tr:name type="given">Derek</tr:name>
		<tr:age>99</tr:age>
	</tr:item>
	<tr:item>
		<tr:name type="given">Dorothy</tr:name>
		<tr:age>41</tr:age>
	</tr:item>
</tr:collection>
</root>

```
style.xsl:
```

<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
xmlns:tr="http://www.mozilla.org/projects">
<!--<xsl:output method="html" omit-xml-declaration="yes" />-->
	<xsl:template match="/">
		<html><head><title></title></head><body>
			<table border="1">
				<xsl:for-each select="//tr:item">
					<tr>
						<td><xsl:value-of select="//tr:name" /></td>
						<td><xsl:value-of select="//tr:age" /></td>
					</tr>
				</xsl:for-each>
			</table>
		</body></html>
	</xsl:template>
</xsl:stylesheet>

```
My problem at the moment is that the browser prints the following:
Joe	34
Joe	34
Joe	34
Joe	34
Can't figure out why it's doing it
???

---

### Post by trent.josephsen on 2010-06-01
I'm not familiar with the // notation, but this seems to work:

```
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
xmlns:tr="http://www.mozilla.org/projects">
<!--<xsl:output method="html" omit-xml-declaration="yes" />-->
  <xsl:template match="/">
    <html><head><title></title></head><body>
      <table border="1">
        <xsl:for-each select="//tr:item">
          <tr>
            <td><xsl:value-of select="tr:name" /></td>
            <td><xsl:value-of select="tr:age" /></td>
          </tr>
        </xsl:for-each>
      </table>
    </body></html>
  </xsl:template>
</xsl:stylesheet>
```

---

### Post by denarced on 2010-06-01
> **trent.josephsen said:**
> I'm not familiar with the // notation, but this seems to work:

```
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
xmlns:tr="http://www.mozilla.org/projects">
<!--<xsl:output method="html" omit-xml-declaration="yes" />-->
  <xsl:template match="/">
    <html><head><title></title></head><body>
      <table border="1">
        <xsl:for-each select="//tr:item">
          <tr>
            <td><xsl:value-of select="tr:name" /></td>
            <td><xsl:value-of select="tr:age" /></td>
          </tr>
        </xsl:for-each>
      </table>
    </body></html>
  </xsl:template>
</xsl:stylesheet>
```

Yes, it does .. hmm
I just copied the //-notation from somewhere while looking for a quick solution. One can look for one but often enough you just have to understand what you're doing.

Much thanks :)

---

