---
title: "How to do this with XSLT?"
date: 2010-12-06
forum: Programming Talk
---

### Post by Sasabune on 2010-12-06
Hi!

How can I manage the following with XSLT: I have a piece of XML like this

```
<author>
  <firstname>Jody</firstname>
  <surname>Leason</surname>
  <firstname>Paul</firstname>
  <surname>Kennedy</surname>
  <affiliation>U of Wisconsin</affiliation>
</author>
```

and I want to output it like this

```
[[surname, firstname] | [affiliation]][; [surname, firstname] | [affiliation]][...]
```

For example

```
Leason, Jody; Kennedy, Paul; U of Wisconsin; ...
```

The DTD definition of the element 'author' is 

```
<!ELEMENT author ((firstname, surname) | affiliation)+ >
```

I know the structure is idiotic but it's given in the exercise so I can't change it..

---

### Post by Arndt on 2010-12-06
> **Sasabune said:**
> Hi!

How can I manage the following with XSLT: I have a piece of XML like this

```
<author>
  <firstname>Jody</firstname>
  <surname>Leason</surname>
  <firstname>Paul</firstname>
  <surname>Kennedy</surname>
  <affiliation>U of Wisconsin</affiliation>
</author>
```

and I want to output it like this

```
[[surname, firstname] | [affiliation]][; [surname, firstname] | [affiliation]][...]
```

For example

```
Leason, Jody; Kennedy, Paul; U of Wisconsin; ...
```

The DTD definition of the element 'author' is 

```
<!ELEMENT author ((firstname, surname) | affiliation)+ >
```

I know the structure is idiotic but it's given in the exercise so I can't change it..

Sounds like homework. Or is it an exercise in some book?

Anyway, what have you tried so far?

---

### Post by Sasabune on 2010-12-06
> **Arndt said:**
> Sounds like homework. Or is it an exercise in some book?

Anyway, what have you tried so far?

Homework. I've tried doing it with the for-each element, templates, pseudo-programming with callable templates, even string-mangling with xpath functions.. the main hurdle for me is outputting the first- and surnames in reverse order.. otherwise it'd be a piece of cake, say something like

```
<xsl:for-each select="author/*">
  <xsl:value-of select="."/>
  <xsl:if test="localname()='firstname'"><xsl:text> </xsl:text></xsl:if>
  <xsl:if test="localname()!='firstname'"><xsl:text>; </xsl:text></xsl:if>
</xsl:for-each>
```

---

### Post by Arndt on 2010-12-06
> **Sasabune said:**
> Homework. I've tried doing it with the for-each element, templates, pseudo-programming with callable templates, even string-mangling with xpath functions.. the main hurdle for me is outputting the first- and surnames in reverse order.. otherwise it'd be a piece of cake, say something like

```
<xsl:for-each select="author/*">
  <xsl:value-of select="."/>
  <xsl:if test="localname()='firstname'"><xsl:text> </xsl:text></xsl:if>
  <xsl:if test="localname()!='firstname'"><xsl:text>; </xsl:text></xsl:if>
</xsl:for-each>
```

I am reminded of how I could get nightmares from XML. I think this is beyond me.

If I _had_ to do it, never mind correctly with XML, I would of course use 'sed' or something.

---

### Post by Arndt on 2010-12-07
I see you marked the thread as solved. I'm just interested, how did you solve it?

---

### Post by Sasabune on 2010-12-07
> **Arndt said:**
> I see you marked the thread as solved. I'm just interested, how did you solve it?

It was very simple afterall, this

[HTML]following-sibling::*[position()=1][/HTML]

selects the next node, so it can be output before the current one.

---

