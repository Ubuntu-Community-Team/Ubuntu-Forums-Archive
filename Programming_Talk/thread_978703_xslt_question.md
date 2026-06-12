---
title: "xslt question"
date: 2008-11-11
forum: Programming Talk
---

### Post by badperson on 2008-11-11
Hi,

If I have a bunch of tags in an xml file like: 
```
<prefix:group1-element1/>
<prefix:group1-element2/>
<prefix:group1-element3/>
<prefix:group1-element4/>
<prefix:group1-element5/>
<prefix:group1-element6/>



```

and I want to write a stylesheet to change those tags to this:

```
<prefix:group2-element1/>
<prefix:group2-element2/>
<prefix:group2-element3/>
<prefix:group2-element4/>
<prefix:group2-element5/>
<prefix:group2-element6/>



```

do I need to write a template for each tag, element1 thru element6? Or can I write one template that will cover all of them? 

(right now I'm thinking perl may be better for this)
bp

---

### Post by badperson on 2008-11-12
pretty sure the answer to this is no.
bp

---

### Post by achelis on 2008-11-12
Well I can't think of a way to do it using xslt. But if it's the only transformation you need sed could do it fairly easily for you.

---

### Post by badperson on 2008-11-14
It would also be easy in perl...I'm on the fence a lot in terms of deciding what to do in perl and what to do in xslt.

---

### Post by rjack on 2008-11-14
This should work:```
<xsl:template match="//prefix:*[starts-with(local-name(), 'group1-')]">
    <xsl:element name="prefix:group2-{substring-after (local-name(), '-')}">
        <xsl:apply-templates/>
    </xsl:element>
</xsl:template>
```

---

