---
title: "XSL cross reference attribute names"
date: 2009-02-26
forum: Programming Talk
---

### Post by Sportingfan on 2009-02-26
Hi,

for the sake of simplicity, I'll start with an example xml:

```
<games>
	<game>
		<gameevent gameid="1" eventname="soccer" />
		<gameevent gametid="2" eventname="basketball" />
	</game>
	<results>
		<result gameid="1" team1="Liverpool" team2="Manchester" gamescore="1-0" />
		<result gameid="2" team1="LA" team2="Dallas" gamescore="85-73" />
		<result gameid="1" team1="Madrid" team2="Barcelona" gamescore="0-0" />
	</results>
/games>
```

I want to list all the results sorted by the eventnames:

```
soccer
Liverpool - Manchester 1-0
Madrid - Barcelona 0-0

basketball
LA - Dallas 85-73
```

How can this be done? 
For each gameevent I want to get the matching results.

---

### Post by hastur on 2009-02-26
hi,

maybe you can try with <xsl:key> :

```

<xsl:stylesheet>

<xsl:key name="gameid" match="//result" use="@gameid"/>

<xsl:template match="//gamevent">
  <!-- print the title of the event here -->
  <xsl:apply-templates select="key('gameid',@gameid)" />
</xsl:template>

<xsl:template match="//result">
  <!-- print the result here -->
</xsl:template>

</xsl:stylesheet>

```

if it's not clear or doesn't work out of the box :
[http://www.w3schools.com/xsl/el_key.asp]("http://www.w3schools.com/xsl/el_key.asp")

---

### Post by pp. on 2009-02-28
Produce a sorted list of all event names. For each event name produce a list of results with the appropriate gameid.

---

### Post by Sportingfan on 2009-03-21
I think I'll have to wait until xslt 2.0 to use for-each-group and current-grouping-key(), which probably solve the problem.

Unless anybody else has another idea?!

---

### Post by Sportingfan on 2009-03-21
I found the solution! 
See below!

```
<?xml version="1.0" encoding="ISO-8859-1"?>

<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

	<xsl:template match="/">
		 <html>
  			<body>
    				<table border="1">
    					<tr bgcolor="#9acd32">
					      	<th align="left">Team 1</th>
					      	<th align="left">Team 2</th>
						<th align="left">Score</th>
    					</tr>
					<xsl:apply-templates select="//gameevent"/>
    				</table>
  			</body>
  		</html>
	</xsl:template>

	<xsl:template match="//gameevent">
		<xsl:variable name="id" select="@gameid"/>

		<xsl:for-each select="//result[@gameid=$id]">
			<tr>
			      	<td><xsl:value-of select="@team1"/></td>
				<td><xsl:value-of select="@team2"/></td>
			      	<td><xsl:value-of select="@gamescore"/></td>
			</tr>
		</xsl:for-each>

	</xsl:template>

</xsl:stylesheet>
```

---

