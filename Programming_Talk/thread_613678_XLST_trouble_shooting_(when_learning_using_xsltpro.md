---
title: "XLST trouble shooting (when learning using xsltproc from libxslt)"
date: 2007-11-15
forum: Programming Talk
---

### Post by kentl on 2007-11-15
I'm using xsltproc from libxslt to transform some XML into text. I mostly do it for learning purposes.

**input.xml**:
```

<?xml version="1.0" encoding="utf-8" ?>
<root>
	<list type="unordered">
		<item>Leonardo</item>
		<item>Donatello</item>
		<item>Rafael</item>
		<item>Shredder</item>
		<item>Mr Myagi</item>
	</list>
	<list type="bob">
		<item>Horse</item>
		<item>Cat</item>
		<item>Pig</item>
		<item>Wolf</item>
		<item>Dog</item>
	</list>
</root>

```

**latex.xsl**:
```

<?xml version="1.0" encoding="utf-8" ?>
<xsl:stylesheet version ="1.0" xmlns:xsl = "http://www.w3.org/1999/XSL/Transform">
<xsl:output method="text" encoding="utf-8"/>
<xsl:template match="list[@type='unordered']">
\begin{enumerate}<xsl:for-each select="item">
\item <xsl:value-of select="."/>
</xsl:for-each>
\end{enumerate}

</xsl:template>
</xsl:stylesheet>

```

**output.txt generated from 'xsltproc -o output.txt latex.xsl input.xml'**:
```

\begin{enumerate}
\item Leonardo
\item Donatello
\item Rafael
\item Shredder
\item Mr Myagi
\end{enumerate}



                Horse
                Cat
                Pig
                Wolf
                Dog

```

[INDENT][B]My question:
[/B]Why are the animals printed? They are in a list of type='bob' and I thought I matched only lists of type='unordered'.

It seems like everything not matched is printed as-is. And if that's the case, how do I turn it off? :-)
[/INDENT]

---

