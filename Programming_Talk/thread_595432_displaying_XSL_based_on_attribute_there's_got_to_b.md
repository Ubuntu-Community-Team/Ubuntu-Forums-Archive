---
title: "displaying XSL based on attribute: there's got to be a better way"
date: 2007-10-28
forum: Programming Talk
---

### Post by DouglasAWh on 2007-10-28
Ok, I've got an XSL where I want to show only items from a certain element with a certain attribute.

The following works
```

<xsl:for-each select="//table_data[2]/row">
      <tr>
        <td><xsl:value-of select="field[2]"/></td>
        <td><xsl:value-of select="field[1]"/></td>
	    <td><xsl:value-of select="field[3]"/></td>
      </tr>
      </xsl:for-each>

```

However, it requires counting the elements, which for the 2nd isn't so bad, but for the 9350308th that would suck.  How do I go about doing this based on the name attribute of the table_data element?

---

### Post by DouglasAWh on 2007-10-28
Figured it out:

```

      <xsl:for-each select="//table_data[@name='student']/row">

```

---

