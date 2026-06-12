---
title: "'Times' font ugly. How can I map it to another font?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by powerpleb on 2008-11-01
Sometimes I've visited certain web pages and been struck by how horrible the font looks. On closer examination I've found that this happens when webpages are using the fonts 'Times' and 'Helvetica'.

I think this is why:
```
~$ fc-match Times; fc-match Helvetica
timR12.pcf.gz: "Times" "Regular"
helvR12.pcf.gz: "Helvetica" "Regular"

```
It's using ugly old non true-type fonts.

So my question is, can I map 'Times' to be replaced by, say 'Liberation Serif' (or something similar) and 'Helvetica' to be replaced by 'Liberation Sans'.

I've tried playing with the ~/.fonts.conf thus:
```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
[COLOR="DarkRed"] <alias>
   <family>Times</family>
   <prefer><family>Liberation Serif</family></prefer>
 </alias>[/COLOR]
</fontconfig>
```
But it doesn't work.

Any ideas?

---

### Post by Mazza558 on 2008-11-01
Try enabling Firefox's text smoothing settings.

Put this in the firefox address bar:

> about:config

then narrow the options down by typing "gfx".

then for the "gfx.use_text_smoothing_setting" value, double-click to change it to "true", then restart firefox.

Alternatively, you could always force all web pages to use the same font in options > content in firefox

---

### Post by powerpleb on 2008-11-01
Thanks for your response.

> **Mazza558 said:**
> 
then for the "gfx.use_text_smoothing_setting" value, double-click to change it to "true", then restart firefox.
This didn't work.

> **Mazza558 said:**
> 
Alternatively, you could always force all web pages to use the same font in options > content in firefox
This does work. But now everything is in the same font, which isn't ideal.

---

