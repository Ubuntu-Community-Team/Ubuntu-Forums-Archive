---
title: "Bash: know the active color used by GTK?"
date: 2011-08-05
forum: Programming Talk
---

### Post by honeybear on 2011-08-05
Hi,

gtk+ 2.0 change theme allows to change your gtk theme. OK. I would need to know the most important color used by gtk so that firefox looks black, braun, ... and other apps. 

How to know it with bash in realtime? 

Cheers

---

### Post by JupiterV2 on 2011-08-06
man gconftool-2

---

### Post by DependencyHell on 2011-08-06
I hope i understood correctly your question: you want to find the most abundant color in icons used by your apps? I believe there is more elegant solution to this, but i gave it a try and made this simple script
> 
#!/bin/sh
#a simple script to extract the most used colors
i=0
for file in $1/*
do
pngtopnm $file >/tmp/buff.pnm
pnmcolormap 2 /tmp/buff.pnm>/tmp/buff2.pnm
pnmtopng /tmp/buff2.pnm>~/map_result$i.png
rm -f /tmp/buff.pnm
rm -f /tmp/buff2.pnm
i=$(($i+1))
done
What is produced are small (2px large!) pngs with two colors. from man pages for pnmcolormap i understand that those two are mean colors appearing in the picture, from two disjunct sets being identified. For example, here is the output of my empty-trash icon (result.png). If i use pnmcolormap **-meanpixel** 2 /tmp/buff.pnm>/tmp/buff2.pnm, the result is better, because mean color is now weighted by the amounts of pixels! 
result2 shows this output, and i believe is more realistic...the drawback of this "method" is that you have to check the colors by eye. And you have to enlarge the 2px pictures. :confused: perhaps there is something faster.

---

### Post by honeybear on 2011-08-07
> **DependencyHell said:**
> I hope i understood correctly your question: you want to find the most abundant color in icons used by your apps? I believe there is more elegant solution to this, but i gave it a try and made this simple script
What is produced are small (2px large!) pngs with two colors. from man pages for pnmcolormap i understand that those two are mean colors appearing in the picture, from two disjunct sets being identified. For example, here is the output of my empty-trash icon (result.png). If i use pnmcolormap **-meanpixel** 2 /tmp/buff.pnm>/tmp/buff2.pnm, the result is better, because mean color is now weighted by the amounts of pixels! 
result2 shows this output, and i believe is more realistic...the drawback of this "method" is that you have to check the colors by eye. And you have to enlarge the 2px pictures. :confused: perhaps there is something faster.

it is a cool bull or cow, man. Is it coming from minecraft? 

I meant that how to know the current GTK color tht is currently used.

---

### Post by DependencyHell on 2011-08-07
[QUOTE=honeybear]Is it coming from minecraft? [/QUOTE]
Nope, from zootetragonoides icon set :)
No for your question...i don't know if this helps but here is what i would suggest:
first enter the directory /usr/share/themes/<your theme name>
if you don't want to look which theme you currently have just type in
```
 cd /usr/share/themes/`grep gtk-theme-name ~/.gtkrc-2.0 | sed 's/"/ /g' | awk '{print $2}'`
```Then look for the colors appearing in your .rc files:
```
grep  '#[[:alnum:]][ff,FF]' `find . -name *.rc`
```for example here is my output for the theme "Radiance" i use:
```

./gtk-2.0/apps/gnome-terminal.rc:    text[NORMAL] = "#ffffff"
./gtk-2.0/apps/chromium.rc:  ChromeGtkFrame::frame-color = "#dfd7cf"
./gtk-2.0/apps/chromium.rc:  ChromeGtkFrame::inactive-frame-color = "#dfd7cf"
./gtk-2.0/apps/chromium.rc:  ChromeGtkFrame::incognito-frame-color = "#dfd7cf"
./gtk-2.0/apps/chromium.rc:  ChromeGtkFrame::incognito-inactive-frame-color = "#dfd7cf"

```the last "*" (e.g. #dfd7cf) contains the encoding for color used within my theme.

Cheers!

---

### Post by honeybear on 2011-08-07
> **DependencyHell said:**
> Nope, from zootetragonoides icon set :)
No for your question...i don't know if this helps but here is what i would suggest:
first enter the directory /usr/share/themes/<your theme name>
if you don't want to look which theme you currently have just type in
```
 cd /usr/share/themes/`grep gtk-theme-name ~/.gtkrc-2.0 | sed 's/"/ /g' | awk '{print $2}'`
```Then look for the colors appearing in your .rc files:
```
grep  '#[[:alnum:]][ff,FF]' `find . -name *.rc`
```for example here is my output for the theme "Radiance" i use:
```

./gtk-2.0/apps/gnome-terminal.rc:    text[NORMAL] = "#ffffff"
./gtk-2.0/apps/chromium.rc:  ChromeGtkFrame::frame-color = "#dfd7cf"
./gtk-2.0/apps/chromium.rc:  ChromeGtkFrame::inactive-frame-color = "#dfd7cf"
./gtk-2.0/apps/chromium.rc:  ChromeGtkFrame::incognito-frame-color = "#dfd7cf"
./gtk-2.0/apps/chromium.rc:  ChromeGtkFrame::incognito-inactive-frame-color = "#dfd7cf"

```the last "*" (e.g. #dfd7cf) contains the encoding for color used within my theme.

Cheers!

thank you. That's very great reply. Thanks. 

However to know the current one (without looking into /usr/share/theme) but into $HOME ?

Best regards

---

### Post by DependencyHell on 2011-08-07
Hmm..I think that color settings you use with apps are tightly connected to the themes. For example, when i wanted make some difference how my apps look, i had to modify the Radiance theme. I am actually not sure if there is some other way to access current color  settings besides looking at the current theme settings.  I am sorry i couldn't help you more than this. But if there is a way, i would be glad to learn it. I looked over the entries of gconf-editor, but couldn't find anything besides reference to the whole theme, in my case Radiance :confused:

---

