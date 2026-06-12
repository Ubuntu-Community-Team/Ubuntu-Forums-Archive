---
title: "[XQuery] Selecting everything before and after path, but without duplicated leafs"
date: 2008-02-10
forum: Programming Talk
---

### Post by SpaRood on 2008-02-10
Hi all,

I have an XML file (quite long) and I have a path to an element. I want to select (1) everything of that path and its descendants, at the same time I want to return everything (2) before that path, and everything (3) after that path. I was trying the XPath axes "preceding" and "following", but these axes are returning duplicate leafs, which is not what I want. I would like to reconstruct the original XML file, but with an extra tag for the XPath selection ($unit).

This is how my XQuery looks like.
```

 let $doc := doc("file.xml")

 let $precedingUnit := $doc/ead[1]/archdesc[1]/dsc[1]/c01[1]/preceding::node()
 let $unit := $doc/ead[1]/archdesc[1]/dsc[1]/c01[1]/self::node()
 let $followingUnit := $doc/ead[1]/archdesc[1]/dsc[1]/c01[1]/following::node()
 return
 <out>
 <before>
 {
    $precedingUnit
 }
 </before>
 <select>
 {
    $unit
 }
 </select>
 <after>
 {
    $followingUnit
 }
 </after>
 </out>

```

I am using XQuery with Saxon: ```
java -cp saxon9.jar net.sf.saxon.Query query.xq
```

Could you please help me?

Thank you very much, I am really desperate in getting this working.

---

### Post by SpaRood on 2008-02-10
I have also attached the XML file in this post.

---

### Post by Shin_Gouki2501 on 2008-02-10
first this helped me quite good:
[http://www.w3schools.com/xquery/default.asp](http://www.w3schools.com/xquery/default.asp)

2nd there are nice tools to test your querys with documents. I have to find that link again, then i post it

---

### Post by SpaRood on 2008-02-10
Thanks, but I know the basics of XQuery...

I only  fail to understand the problem that was stated above.

---

### Post by Shin_Gouki2501 on 2008-02-10
well if i understand you right you want navigate to an element and when you found it u want simply add some data.
as said i look after that programm i mentioned tray ur sample data and then try about the query.

---

### Post by Shin_Gouki2501 on 2008-02-11
here u go :
i know that tool imo its perfect to test somethigns regarding ur problem.

---

