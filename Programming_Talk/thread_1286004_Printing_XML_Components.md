---
title: "Printing XML Components"
date: 2009-10-08
forum: Programming Talk
---

### Post by mastermindg on 2009-10-08
I'd like to execute a command in shell that would take this:

<row>
  <Category>Pop</Category>
  <Name>SIRIUS XM Hits 1</Name>
  <Number>2</Number>
  <Description>Top 40 Hits</Description>
</row>
<row>
  <Category>Pop</Category>
  <Name>40s on 4</Name>
  <Number>4</Number>
  <Description>Forties Pop Hits/Big Band</Description>
</row>

and convert it to this:

Group	Name			Number	Description
Pop	Sirius XM Hits 1	2	Top 40 Hits
Pop	40s on 4		4	Forties Pop Hits/Big Band

---

### Post by mastermindg on 2009-10-08
I'm using the following stylesheet:

```
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
<xsl:output method="text" />

<xsl:template match="/rows/row">
<xsl:value-of select="Group"/>
<xsl:value-of select="Name"/>
<xsl:value-of select="Number"/>
<xsl:value-of select="Description"/>
</xsl:template>

</xsl:stylesheet>
```

to work with:
```

<rows>
<row>
  <Group>Pop</Group>
  <Name>SIRIUS XM Hits 1</Name>
  <Number>2</Number>
  <Description>Top 40 Hits</Description>
</row>
<row>
  <Group>Pop</Group>
  <Name>40s on 4</Name>
  <Number>4</Number>
  <Description>Forties Pop Hits/Big Band</Description>
</row>
</rows>
```

How can I add a column header to the top of the output?

---

### Post by mastermindg on 2009-10-08
Figured out how to get a header. My problem is now that the spacing is off because different fields are different widths. How can I align the rows?

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
     version="1.0">
<xsl:output method="text" indent="yes" />

<xsl:strip-space elements="*"/>

<xsl:template match="rows">
Group&#9;&#9;Name&#9;&#9;&#9;Number&#9;Description
-----&#9;&#9;-----&#9;&#9;&#9;------&#9;----------
<xsl:apply-templates/>
</xsl:template>

<xsl:template match="row">
  <xsl:apply-templates select="Group"/>
  <xsl:text>&#9;&#9;</xsl:text>
  <xsl:apply-templates select="Name"/>
  <xsl:text>&#9;&#9;</xsl:text>
  <xsl:apply-templates select="Number"/>
  <xsl:text>&#9;</xsl:text>
  <xsl:apply-templates select="Description"/><xsl:text>
</xsl:text>
</xsl:template>

</xsl:stylesheet>
```

---

### Post by myrtle1908 on 2009-10-08
So are you wanting to print the formatted output to the shell/console or display in a web browser?  I assume the latter as you are using XSLT.  If so, then use a HTML table.

If you want to dump the output to the shell or a text file then I would use an XML parser (dom4j is my fav for Java), a fixed width font and a bit of right-padding (printf/sprintf/rightPad etc.) depending on your language of choice.

---

