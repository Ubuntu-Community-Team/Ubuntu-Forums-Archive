---
title: "HOWTO: Improve fonts rendering"
date: 2008-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by luca_linux on 2008-05-13
Sometimes fonts rendering on Linux (especially on some distros) can be a real issue.
As I managed to find a configuration that works great for me, I thought I should share this.
This HowTo is based on my current distro which is Ubuntu with Gnome. However, the proper settings can be applied to other Desktop Environments (such as KDE) and other distros too; you'll just have to find the right GUI in which to set up these things.
Anyway, the idea is to play with the "Smoothing" and "Hinting" font parameters.

[LIST]
[*]First of all, go to "System --> Preferences --> Appearance" menu
[/LIST]

The following window should open and then go to the "Fonts" tab:

[IMG]http://img153.imageshack.us/img153/7094/screenshotappearanceprebe6.png[/IMG]


[LIST]
[*]Now in the "Rendering" section pick the "Subpixel smoothing (LCDs)" option
[*]Then click on the "Details" button
[/LIST]

A new window will open, as follow:

[IMG]http://img208.imageshack.us/img208/355/screenshotfontrenderingwi5.png[/IMG]


[LIST]
[*]In the "Smoothing" section pick the "Subpixel (LCDs)" option
[*]In the "Hinting" section pick the "Slight" option
[/LIST]
You'll immediately notice a better font rendering in this same window. As a quick preview, take a close look to the difference between the fonts in the two images I used in this HowTo.

[LIST]
[*]Now just close the the windows by clicking on the "Close" buttons
[*]Enjoy the better rendering
[/LIST]

I hope that'll help. :)



P.S: please note that this HowTo especially helps on LCD screens. On CRT monitors the result might not be great.

---

### Post by wieman01 on 2008-05-14
Nice one! I will try it out!

---

### Post by Ferio on 2008-05-14
Well, I suppose it's just a choice dependant on likings; I like it better when choosing *Full* instead of *Slight*.

---

### Post by luca_linux on 2008-05-15
> **Ferio said:**
> Well, I suppose it's just a choice dependant on likings; I like it better when choosing *Full* instead of *Slight*.
It might be. :)
Anyway, on higher resolution (which are more and more common nowadays) in which everything is smaller, I think the "Slight" hinting performs better, because it makes the regular font style appear bolder.

---

### Post by Holy Cheater on 2008-05-17
That makes small fonts look more clear, but spoils the appearance of small bold fonts. And there is a problem that gnome ignores all the fontconfig settings, so I can't just modify it to make small fonts render with slight hinting and normal-sized and bold render with full-hinting :(

---

### Post by zerwas on 2008-05-18
> **Holy Cheater said:**
> so I can't just modify it to make small fonts render with slight hinting and normal-sized and bold render with full-hinting :(

```
sudo dpkg-reconfigure fontconfig-config
```
Here, choose "ALWAYS" (you can leave the rest or play around with it)
```
sudo dpkg-reconfigure fontconfig
```
Restart X.

-- zerwas

---

### Post by the8thstar on 2008-05-18
Note that this is not a one-size-fits-all solution. I personally use Futura Bk size 9, with slight hinting on my laptop, which looks fabulous.

However, the same setting looks like crap on the CRT monitor of my desktop computer.

Nice how-to though: it can help people just starting with Ubuntu. :)

---

### Post by saratchandra on 2008-05-19
Excellent tutorial. Thanks

---

### Post by luca_linux on 2008-05-20
> **the8thstar said:**
> Note that this is not a one-size-fits-all solution. I personally use Futura Bk size 9, with slight hinting on my laptop, which looks fabulous.

However, the same setting looks like crap on the CRT monitor of my desktop computer.

Nice how-to though: it can help people just starting with Ubuntu. :)
Yeah, you're right.
This HowTo suits LCD screens better. :)
That's also suggested by the Gnome GUI itself ("SubPixel (**LCDs**)").

---

