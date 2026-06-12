---
title: "How to wrap everything between two tags in XSL ?"
date: 2009-10-19
forum: Programming Talk
---

### Post by josteinaj on 2009-10-19
I've got this XML-structure:

```
<level1>
  <h1>Title</h1>
  <p>text</p>
  <p>text</p>

  <h2>Section</h2>
  <p>text</p>
  <pagenum id="page2"/>
  <p>text</p>

  <h2>Section</h2>
  <p>text</p>
  <p>text</p>
</level1>
```

... and need to use XSL to wrap the subsections in like this:

```
<level1>
  <h1>Title</h1>
  <p>text</p>
  <p>text</p>

  <level2>
    <h2>Section</h2>
    <p>text</p>
    <pagenum id="page2"/>
    <p>text</p>
  </level2>

  <level2>
    <h2>Section</h2>
    <p>text</p>
    <p>text</p>
  </level2>
</level1>
```

So; everything between two <h2>-tags, or between a <h2>-tag and a </level1>-tag, shall be wrapped into a <level2>-tag.

(I need the same thing for h3, h4 etc. as well, but that'll probably be a copy/paste of the solution to this problem)

How can I achieve this?

---

### Post by Arndt on 2009-10-19
> **josteinaj said:**
> I've got this XML-structure:

```
<level1>
  <h1>Title</h1>
  <p>tekst</p>
  <p>tekst</p>

  <h2>Section</h2>
  <p>tekst</p>
  <pagenum id="page2"/>
  <p>tekst</p>

  <h2>Section</h2>
  <p>tekst</p>
  <p>tekst</p>
</level1>
```

... and need to use XSL to wrap the subsections in like this:

```
<level1>
  <h1>Title</h1>
  <p>text</p>
  <p>text</p>

  <level2>
    <h2>Section</h2>
    <p>text</p>
    <pagenum id="page2"/>
    <p>text</p>
  </level2>

  <level2>
    <h2>Section</h2>
    <p>text</p>
    <p>text</p>
  </level2>
</level1>
```

So; everything between two <h2>-tags, or between a <h2>-tag and a </level1>-tag, shall be wrapped into a <level2>-tag.

(I need the same thing for h3, h4 etc. as well, but that'll probably be a copy/paste of the solution to this problem)

How can I achieve this?

Something like this:
```

<xsl:stylesheet version="1.0"
		xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

  <xsl:output method="xml"/>

<xsl:template match="@*|node()">
  <xsl:copy>
    <xsl:apply-templates select="@*|node()"/>
  </xsl:copy>
</xsl:template>

<xsl:template match="h2">
  <xsl:element name="level2">
  <xsl:copy>
    <xsl:apply-templates select="@*|node()"/>
  </xsl:copy>
  </xsl:element>
</xsl:template>

</xsl:stylesheet>

```

---

### Post by josteinaj on 2009-10-19
Thanks. However that sheet results in this:

```
<?xml version="1.0" encoding="UTF-8"?>
<level1>
	<h1>Title</h1>
	<p>text</p>
	<p>text</p>
	<level2>
		<h2>Section</h2>
	</level2>
	<p>text</p>
	<pagenum id="page2"/>
	<p>text</p>
	<level2>
		<h2>Section</h2>
	</level2>
	<p>text</p>
	<p>text</p>
</level1>
```

From *[this site]("http://www.xml.com/pub/a/2003/11/05/tr.html")* I derived this XSL:

```
<xsl:stylesheet version="1.0"
		xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

  <xsl:output method="xml"/>

<xsl:template match="level1">
  <body>
    <xsl:for-each-group select="*" group-starting-with="h1">
      <chapter>
      <xsl:for-each select="current-group()">
        <xsl:copy>
          <xsl:apply-templates/>
        </xsl:copy>
      </xsl:for-each>
      </chapter>
    </xsl:for-each-group>
    <xsl:for-each-group select="*" group-starting-with="h2">
      <section>
      <xsl:for-each select="current-group()">
        <xsl:copy>
          <xsl:apply-templates/>
        </xsl:copy>
      </xsl:for-each>
      </section>
    </xsl:for-each-group>
  </body>
</xsl:template>

</xsl:stylesheet>
```

However, this was the result:

```
<?xml version="1.0" encoding="UTF-8"?>
<body>
	<chapter>
		<h1>Title</h1>
		<p>text</p>
		<p>text</p>
		<h2>Section</h2>
		<p>text</p>
		<pagenum/>
		<p>text</p>
		<h2>Section</h2>
		<p>text</p>
		<p>text</p>
	</chapter>
	<section>
		<h1>Title</h1>
		<p>text</p>
		<p>text</p>
	</section>
	<section>
		<h2>Section</h2>
		<p>text</p>
		<pagenum/>
		<p>text</p>
	</section>
	<section>
		<h2>Section</h2>
		<p>text</p>
		<p>text</p>
	</section>
</body>
```

Also, the example in the first post is a simplified version of my problem. To complicate things, the levels 1 and 2 are actually written as attributes instead of different tags:

```
<level1>
  <headline level="1">Title</headline>
  <p>text</p>
  <p>text</p>

  <headline level="2">Section</headline>
  <p>text</p>
  <pagenum id="page2"/>
  <p>text</p>

  <headline level="2">Section</headline>
  <p>text</p>
  <p>text</p>
</level1>
```

---

### Post by Arndt on 2009-10-19
> **josteinaj said:**
> Thanks. However that sheet results in this:

```
<?xml version="1.0" encoding="UTF-8"?>
<level1>
	<h1>Title</h1>
	<p>text</p>
	<p>text</p>
	<level2>
		<h2>Section</h2>
	</level2>
	<p>text</p>
	<pagenum id="page2"/>
	<p>text</p>
	<level2>
		<h2>Section</h2>
	</level2>
	<p>text</p>
	<p>text</p>
</level1>
```

From *[this site]("http://www.xml.com/pub/a/2003/11/05/tr.html")* I derived this XSL:

```
<xsl:stylesheet version="1.0"
		xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

  <xsl:output method="xml"/>

<xsl:template match="level1">
  <body>
    <xsl:for-each-group select="*" group-starting-with="h1">
      <chapter>
      <xsl:for-each select="current-group()">
        <xsl:copy>
          <xsl:apply-templates/>
        </xsl:copy>
      </xsl:for-each>
      </chapter>
    </xsl:for-each-group>
    <xsl:for-each-group select="*" group-starting-with="h2">
      <section>
      <xsl:for-each select="current-group()">
        <xsl:copy>
          <xsl:apply-templates/>
        </xsl:copy>
      </xsl:for-each>
      </section>
    </xsl:for-each-group>
  </body>
</xsl:template>

</xsl:stylesheet>
```

However, this was the result:

```
<?xml version="1.0" encoding="UTF-8"?>
<body>
	<chapter>
		<h1>Title</h1>
		<p>text</p>
		<p>text</p>
		<h2>Section</h2>
		<p>text</p>
		<pagenum/>
		<p>text</p>
		<h2>Section</h2>
		<p>text</p>
		<p>text</p>
	</chapter>
	<section>
		<h1>Title</h1>
		<p>text</p>
		<p>text</p>
	</section>
	<section>
		<h2>Section</h2>
		<p>text</p>
		<pagenum/>
		<p>text</p>
	</section>
	<section>
		<h2>Section</h2>
		<p>text</p>
		<p>text</p>
	</section>
</body>
```

Also, the example in the first post is a simplified version of my problem. To complicate things, the levels 1 and 2 are actually written as attributes instead of different tags:

```
<level1>
  <headline level="1">Title</headline>
  <p>text</p>
  <p>text</p>

  <headline level="2">Section</headline>
  <p>text</p>
  <pagenum id="page2"/>
  <p>text</p>

  <headline level="2">Section</headline>
  <p>text</p>
  <p>text</p>
</level1>
```

xsltproc which I'm using here doesn't support XSLT 2.0, so I don't have for-each-group. But from its description, it seems that it creates groups which start with what you say, *and* a first group beginning with the first element, even if it doesn't match. So maybe an 'if' of some kind solves the problem.

---

### Post by josteinaj on 2009-10-20
I've found a solution. This solution is from xsl-list at lists.mulberrytech.com :

```
<xsl:stylesheet
 xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
 version="2.0"
 xmlns:xs="http://www.w3.org/2001/XMLSchema"
 xmlns:mf="http://example.com/2009/mf"
 exclude-result-prefixes="xs mf">

 <xsl:output indent="yes"/>
 <xsl:strip-space elements="*"/>

 <xsl:function name="mf:group" as="node()*">
   <xsl:param name="nodes" as="node()*"/>
   <xsl:param name="level" as="xs:integer"/>
   <xsl:for-each-group select="$nodes" group-starting-with="headline[@level = $level]">
     <xsl:choose>
       <xsl:when test="self::headline[@level = $level]">
         <xsl:element name="level{$level}">
           <xsl:element name="h{$level}">
             <xsl:value-of select="."/>
           </xsl:element>
           <xsl:sequence select="mf:group(current-group() except ., $level + 1)"/>
         </xsl:element>
       </xsl:when>
       <xsl:otherwise>
         <xsl:copy-of select="current-group()"/>
       </xsl:otherwise>
     </xsl:choose>
   </xsl:for-each-group>
 </xsl:function>

 <xsl:template match="document">
   <xsl:variable name="v1">
     <headline level="1"><xsl:value-of select="metaData/title"/></headline>
     <xsl:copy-of select="contentSection/node()"/>
   </xsl:variable>
   <body>
     <xsl:sequence select="mf:group($v1/node(), 1)"/>
   </body>
 </xsl:template>

</xsl:stylesheet>
```

---

