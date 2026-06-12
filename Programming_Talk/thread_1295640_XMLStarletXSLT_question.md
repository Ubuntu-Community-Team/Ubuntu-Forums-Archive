---
title: "XMLStarlet/XSLT question"
date: 2009-10-19
forum: Programming Talk
---

### Post by wesg on 2009-10-19
I'm trying to extract data from an XML file to use in a bash script. After toying with sed/awk/grep, I've moved on to XMLStarlet, with better results. My problem now is getting the data I really need. 

I want to get one tag, based on the value of another tag on the same level. 

For example, I want to search through an XML file where the tag <tag1>45</tag1> exists, then collect the data from <tag2> that is in the same child. This XML file is from TVRage, as I'm processing TV titles. 

My current code,
```
xmlstarlet sel -t -v "/Show/Episodelist/Season[@no='$season']/episode"
```
can't seem to compare tag values with what I want.

Any suggestions?

---

### Post by Reiger on 2009-10-19
Are you sure it is not some silly escape character foul-up? Single-quotes, double quotes, dollar-expansion and who-knows how many other bash features that may interfere?

---

### Post by Arndt on 2009-10-20
> **Reiger said:**
> Are you sure it is not some silly escape character foul-up? Single-quotes, double quotes, dollar-expansion and who-knows how many other bash features that may interfere?

Or namespaces.

---

