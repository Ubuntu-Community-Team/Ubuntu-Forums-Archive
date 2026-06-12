---
title: "making firefox the default browser"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by techno-mole on 2008-07-14
hello.
ive been playing around with kubuntu for a couple of days or so (i plan to install it on my new 500gb hard drive, when it arrives) ive been using ubuntu for a while and thought id try kubuntu to see what kde is like (i know i could have just installed kde) but i frequently mess things like that up, so i thought downloading one of the kubuntu version was a better choice.

anyway back to the point, konqueror, how do i stop it being the default for the internt ? i dont mind using it for file browsing, but i would rather have firefox open a link if i click one, for example i have some study guides for my web apps course that have links in them, but clicking on them opens konq, so how do i change it to fire fox ?

i did try removing konq, but had to put it back on as i must have removed too much, and couldnt browse any files in the home directory.
cheers

---

### Post by adamogardner on 2008-07-14
hi  I'm just wondering if the rule for making firefox default is the same rule to make anything else default.  I want to do this w/ amarok (as posted in a thread yesturday).  I'm guessing this is very hard to do because even after a bump; no comment.

---

### Post by philinux on 2008-07-14
[http://jatshergill.com/blog/2006/05/16/how-to-setup-the-default-web-browser-in-kubuntu/](http://jatshergill.com/blog/2006/05/16/how-to-setup-the-default-web-browser-in-kubuntu/)

---

### Post by techno-mole on 2008-07-15
thanks for the tip, done it now.
i dont mind konq, but  do prefer firefox for web browsing.

---

### Post by zipperback on 2008-07-15
Install Firefox on your system using your package manager.

Now open a terminal window, and type the following:
**sudo update-alternatives --config x-www-browser**

You should then see a listing of the browsers available to you on your system.

Select Firefox from the list and then press enter.

Firefox should now your default browser.

- zipperback
:popcorn:

---

### Post by piemonkey on 2008-07-27
> **zipperback said:**
> 
You should then see a listing of the browsers available to you on your system.

I tried this, and Konsole gave me:

There is only 1 program which provides x-www-browser
(/usr/bin/firefox-3.0). Nothing to configure.

but it still opens urls in Konqueror... This may be because I'm using kde4, which seems to have problems with things like default programs... at least my install does...

---

