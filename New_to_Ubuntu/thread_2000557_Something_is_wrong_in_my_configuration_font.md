---
title: "Something is wrong in my configuration font"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by il_maniscalco on 2012-06-09
After months of satisfyingly use of my xubuntu, I discovered one disappointing issue, when compared to windows seven.

I just found that my screen seems a lot bigger and capable when using windows seven.

Consider I use Eclipse, and my impression is that my windows-7 version can contain twice the information instead of Ubuntu.

It seems my Ubuntu fonts are too large, but it's just for my windows, and the application, the browser (chromium and firefox) is not affected.

So I'm requesting you the easiest way to reduce this font-size, as I didn't find no options in the ubuntu control panel.

And, if possible, if there's a desktop environment/windows manager elegant and similar to windows 7, I'm not interested in graphic effects, want like just something minimal, nice-looking and fast.

thank you.

---

### Post by krustenBrot on 2012-06-09
Hey

had the same ... lets call it experience. Try installing "UbuntuTweak"  and change the Font size to 10 or 9 in general and the border font to 12.

This gives a better experience - **but** what i am personally missing is a dynamic adjustment to window size. For example opening a window and the website is adjusted to the window size as seen on Mac Os!

):P

---

### Post by il_maniscalco on 2012-06-09
can't find it... but I'm looking for it.
I also tried to find the preferences-font option (I found googling) but there's no one in my ubuntu 12.04

---

### Post by krustenBrot on 2012-06-10
**I do not know if this also works with xubuntu**...

go to: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) and download the previously mentioned tool.
Install it and start it for example via terminal by typing:

```
ubuntu-tweak
```

Goto the *Tweaks Tab* click on *Fonts* and adjust the Fonts ;)

---

### Post by Enigmapond on 2012-06-10
> **krustenBrot said:**
> **I do not know if this also works with xubuntu**...

go to: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) and download the previously mentioned tool.
Install it and start it for example via terminal by typing:

```
ubuntu-tweak
```

Goto the *Tweaks Tab* click on *Fonts* and adjust the Fonts ;)

This is fine except I wouldn't download it from the site as you will not get updates..get it this way:
```
sudo add-apt-repository ppa:tualatrix/ppa && sudo apt-get update && sudo apt-get install ubuntu-tweak
```

---

### Post by Rodney9 on 2012-06-10
In Xubuntu use the Settings Manager / Appearance / Fonts

See screen-shot

Rodney

---

### Post by il_maniscalco on 2012-06-11
I found the reason.
The fonts weren't the problem, the resolution was.
I setted it at 72 instead of 96, and now I'm satisfied.

---

