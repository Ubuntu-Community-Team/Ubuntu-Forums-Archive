---
title: "extract data from html to xml with Python"
date: 2009-05-11
forum: Programming Talk
---

### Post by Krijk on 2009-05-11
I'm learning python and I'm having problems with extracting data from some files. 
I want to learn how to select chunks of data from large files  and extract these to create other files (preferably in xml)

I want to select from a larger file the part between 
<p class ..> to </p> 
the parts between 
<span class ...> to </span> 
are seperate elements and all these have to be converted to:
[LIST=1]
1. as XML in a single file
2. as XML in multiple files (so other data can be inserted on item-level)
[/LIST]

I'm strugling with htmllib and sgmllib, but no success up to now. Can anybody give me some pointers how to do this? 

```

<p class="itemheader">
<span class="date">20090511 15:40</span>
<span class="hyperlink"><a href="http://www.justalink.com/8347647.html">Just a link to somewhere</a></span>
<span class="content">Just some content that is needed</span>
</p>

<p class="itemheader">
<span class="date">20090511 16:40</span>
<span class="hyperlink"><a href="http://www.justalink2.com/8347647.html">link 2 to somewhere</a></span>
<span class="content">Just some other content 2 that is needed</span>
</p>
```

---

### Post by Reiger on 2009-05-11
Doesn't Python have a DOMDocument library with XPath support ? Then we just use XPath:
[list="1"]
[*]Select all p elements with a class attribute //p[@class]
[*]Select all span elements with a class attribute //span[@class]
[/list]

Since PHP's DOMDocument library is based on libxml (the Gnome XML library) and since that one can be used to read/write HTML as well as XML...

---

