---
title: "png screenshot - prefer jpg"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-11-15
Pressing "prt sc" in Lubuntu takes a screenshot in png format. 

The png file is large. 

Is there a way to force it to save the screenshot as a jpg file and therefore not take up so much space?

---

### Post by stinkeye on 2013-11-16
This page shows how to use imagemagick to take screenshots.
[http://wiki.lxde.org/en/How_to_take_screenshots](http://wiki.lxde.org/en/How_to_take_screenshots)

You could follow that guide and instead of using their **screenshot.sh** script,
use something like this....
```
#!/bin/bash
DATE=`date +%Y-%m-%d-%H:%M:%S`
scrot "$HOME/Desktop/$DATE.[COLOR="#FF0000"]jpeg[/COLOR]"
```

Look at **man scrot** if you want other options like delay.
There is also a quality option(-q) to reduce filesize.

Don't use Lubuntu so can't confirm if this works.
On that same wiki page is a link to [**_[COLOR="#B22222"]lxscreenshot[/COLOR]_**]("http://lubuntublog.blogspot.be/2012/02/lxscreenshot.html") which may suit your purpose

---

### Post by SeijiSensei on 2013-11-16
Or you can install imagemagick and run
```
convert image.png image.jpg
```
after you've taken the screenshot.

---

### Post by Kevin McCready on 2013-11-17
thanks both
I'll give it a bash

---

### Post by SeijiSensei on 2013-11-17
> **urmbmjpb said:**
> Umm. Change the extension using gimp?

Imagemagick convert is much easier and faster than using GIMP.

---

### Post by heir4c on 2013-11-18
You can use screencloud (install via UbuntuSoftwareCenter)
[http://screencloud.net/](http://screencloud.net/)
In the 'Preferences' you can change PNG to JPG.
There are also 3 Hotkeys to take a screenshot.

[IMG]http://i.imgur.com/05xeJSOl.png[/IMG]


[IMG]http://i.imgur.com/ea8JiTcl.png[/IMG]

Here I must use the 'normal' 1/2/3 on the keyboard and not the numpad-keys.

---

### Post by vasa1 on 2013-11-18
```
[06:06 PM] ~ $ scrot '%Y-%m-%d_$wx$h.jpeg'
[06:18 PM] ~ $ file 2013-11-18_1366x768.jpeg 
2013-11-18_1366x768.jpeg: JPEG image data, JFIF standard 1.01
[06:19 PM] ~ $ 

```

Stolen from [How to change screenshot file type from png to jpg when doing a Print Screen on Lubuntu?]("http://askubuntu.com/a/197331/25656")

And possibly useful information is here: [http://stackoverflow.com/q/419584/1771119](http://stackoverflow.com/q/419584/1771119)

---

### Post by philinux on 2013-11-18
> **Kevin McCready said:**
> Pressing "prt sc" in Lubuntu takes a screenshot in png format. 

The png file is large. 

Is there a way to force it to save the screenshot as a jpg file and therefore not take up so much space?

Can you install gnome-screenshot there aren't too many dependencies. Once you've taken the screenshot you can change the png extension to jpeg before it saves it.

---

### Post by vasa1 on 2013-11-18
I just ran
**scrot '%Y-%m-%d_$wx$h.jpeg'**
and
**scrot '%Y-%m-%d_$wx$h.png'**
on virtually the same image
```
[06:39 PM] ~ $ ll 2013*
-rw-r--r-- 1 vasa1 vasa1  88234 Nov 18 18:39 2013-11-18_1366x768.jpeg
-rw-r--r-- 1 vasa1 vasa1 147228 Nov 18 18:39 2013-11-18_1366x768.png
[06:39 PM] ~ $ 

```
So there is a decent difference in size but not a significant difference in quality for ordinary purposes! Thanks to your question I've changed from .png to .jpeg :)

---

