---
title: "html, object tag, class id attribute -&gt; browser hangs"
date: 2010-07-26
forum: Programming Talk
---

### Post by koenn on 2010-07-26
Hi there, 

Could someone explain in a few words whatthe html 'object' tag is for, and what its classid attribute is supposed to refer to ? 

eg in this code:
```

<object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" 
 codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,29,0" width="700" height="630">

  <param name="movie" value="20080414.swf?frame=3">
  <param name="quality" value="high">

   <embed src="http://www.bibliotheeknetwerk.be/20080414.swf?frame=3" quality="high" pluginspage="http://www.macromedia.com/go/getflashplayer" type="application/x-shockwave-flash" width="700" height="630">

</object>


```

This works in Firefox, but makes IE8 hang. If I remove the classID aattribute from object tag, or even the 'clsid:' from the value, it works in both browsers.
so this works:
```
<object  codebase="http://download.macromedia. ...   

```
and so does this:
```
<object classid="D27CDB6E-AE6D-11cf-96B8-444553540000" 
 codebase="http:/  ....  >

```


So I'm trying to understand what this attribute is for, what it is supposed to do, why the web developer would put it there while it appears unnecessary, and what, if anything, I can tweak to make this work in IE8. 
(it's not my code, I'm on the client side)

---

### Post by koenn on 2010-07-27
bump

---

### Post by koenn on 2010-07-31
bump?

---

