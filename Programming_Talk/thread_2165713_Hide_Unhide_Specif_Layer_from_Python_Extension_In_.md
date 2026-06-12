---
title: "Hide Unhide Specif Layer from Python Extension In Inkscape"
date: 2013-08-06
forum: Programming Talk
---

### Post by shababhsiddique on 2013-08-06
Hi

I am new to scripting inkscape extension. I have so far covered the basics and created a working hello world example. I cant find a good resource/documentation where i can find full list of available functions that i can use from python in extensions. So i am posting here for your help. If you guys can point me to such resource it would be great as well.

I am trying to build an extension to hide/unhide specific layers(layers have specific names) from my extension. I have no clue about how to proceed. Are there any function like-

```
# Get access to main SVG document element and get its dimensions.
svg = self.document.getroot() 

#get layer by name and hide it ??
svg.getLayerByName("Name_of_layer").hide() <<< ???? 
```


Thanks in advance. I really appreciate your time to read this out.

---

### Post by ofnuts on 2013-08-06
Set its "visibility" attribute to "hidden" or "collapse".

---

### Post by shababhsiddique on 2013-08-07
How exactly am I going to do that? I cant find a way to select that specific layer. and thus far away from changing attribute?

---

### Post by ofnuts on 2013-08-07
> **shababhsiddique said:**
> How exactly am I going to do that? I cant find a way to select that specific layer. and thus far away from changing attribute?
Well it's just a matter of editing the XML document to set the attribute. The Inkscape extension use the popular [lxml library](http://lxml.de/api/lxml.etree-module.html).

---

