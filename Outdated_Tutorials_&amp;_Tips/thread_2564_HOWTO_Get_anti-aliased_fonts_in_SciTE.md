---
title: "HOWTO: Get anti-aliased fonts in SciTE"
date: 2004-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by .altan on 2004-10-29
I almost threw up when I started to write a little bit of code in SciTE. The fonts, by default, are quite ugly and jagged.

To fix this and use the smooth fonts we've come to love, 

```
sudo scite
``` OR ```
sudo chmod 777 /usr/share/scite/SciTEGlobal.properties
``` 

**Options > Open Global Options File**

Scroll down to **if PLAT_GTK** on **line 300** (there are many references to if PLAT_GTK, find the one on line 300 or if you've already edited your file [and maybe changed your line number] find the one where it refers to fonts.

Paste this in its place:

```
if PLAT_GTK

	font.base=font:!lucidatypewriter,size:12

	font.small=font:!lucidatypewriter,size:10

	font.comment=font:!new century schoolbook,size:12

	font.code.comment.box=$(font.comment)

	font.code.comment.line=$(font.comment)

	font.code.comment.doc=$(font.comment)

	font.text=font:!times,size:14

	font.text.comment=font:!lucidatypewriter,size:10

	font.embedded.base=font:!lucidatypewriter,size:12

	font.embedded.comment=font:!lucidatypewriter,size:12

	font.monospace=font:!courier,size:12

	font.vbs=font:!new century schoolbook,size:12
font.js=$(font.comment)
```

The anti-aliased fonts are enabled with the exclamation mark preceding each font name. Feel free to change the fonts, of course, if you don't like the default fonts. Just remember to put a ! before the name.

---

### Post by gunnzi on 2004-11-06
You can also just paste into the 'User Options' file. Works well for me, but then again if you have a multiuser computer the Global file is the best one to edit.

---

