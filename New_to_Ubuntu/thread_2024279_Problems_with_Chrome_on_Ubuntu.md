---
title: "Problems with Chrome on Ubuntu?"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2012-07-13
I never had any Problems with Ubuntu and Chrome. But since a few days everything is ****** up..


Viewing Youtube Videos - Vids play sometimes at double speed (or even faster)

Animated scrollbars (like on youtube for playlists and similar things) - cant use them properly

Viewing Animated Gifs - only a very small area (about 1/4 of the image) is animated rest is static

Input Text - Sometimes i cant write in these text fields. Example: Login Informations on various sites or using search bar for youtube.

And LOTS more problems. I did not change ANYTHING on my computer the last days. I have this Problem ONLY with Chrome, not with Firefox or any other Browser. I have the same Problems on my 2 Notebooks and my personal Computer at Home.

Any Ideas ?

EDIT: Its too WAY slower than Firefox
EDIT: I am using the newest Stable Ubuntu Release 12.04

---

### Post by Laiquendi on 2012-07-13
Try using the linux version of chrome -> chromium.

---

### Post by xedi on 2012-07-13
> **Laiquendi said:**
> Try using the linux version of chrome -> chromium.

Chromium is not the Linux version of Chrome. Both Chrome and Chromium have Linux versions (which I assume krabby is running). Chomium is the open source basis of Chrome.

That said, I also got the double speed bug the last days, it has never done it before. It's not too much help but rebooting fixes it.

---

### Post by rend on 2012-07-13
Krabby, I have actually had the same problems with Youtube and Hulu not displaying right and I get the double speed thing and audio and video not syncing right. 
Just started last week, running v20.0.1132.57 on Precise.
Not sure if v20 is the prob or what.
Been using firefox for streaming but I prefer chrome.

---

### Post by deadflowr on 2012-07-13
Disable the pepperflash plugin which is built into chrome.
In the address bar:
```
chrome://plugins
```

Click the details to expand and the top entry should be shockwave flash ver 11.3-something,something. Disable that, but only if you've installed flash on your Ubuntu install, as to, if you look to the plugin below the pepperflash plugin, you'll see the shockwave flash version which is installed on your system.

I've found this works, and that the pepperflash has been pretty problematic.

Here's chrome's how-to for filing bug reports(For what it's worth)

[http://productforums.google.com/forum/#!topic/chrome/W6n9Oeah3so]("http://productforums.google.com/forum/#!topic/chrome/W6n9Oeah3so")

---

### Post by followkim on 2012-09-30
Removing PepperFlash worked great for me!  I was having all sorts of problems with text input fields and "complex" websites (that have lots of side ads, etc) and now Chrome works perfectly for me!

---

