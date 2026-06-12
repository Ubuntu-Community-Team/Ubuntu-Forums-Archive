---
title: "3d acceleration without restricted drivers"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by thedrizz on 2008-04-26
Well, back in the day i tried to get wine to work. It didnt, so i never needed to use the restricted drivers. When i tried, it made me boot to a black screen.

But because Hardy is apparantly magic, wine is working. However, 3d acceleration is not. I uninstalled my old drivers, tried the restricted ones. I logged in, and got a pretty white screen. Strangely enough, when i ctrl=alt-backspaced, i saw my desktop for a second before it restarted.

Compiz is still working for some reason or another, even with the white screen (i can make the white screen do a 3d turn to another white screen). Well i did the xserver fix (i love that its automated now) and everything is back to normal. 

I'm using ATI's drivers, is there some xorg change that makes 3d acceleration work? Wine would be dandy.

Thanks in advance

Update: After turning off compiz i got halo usb version to show me some green triangles and play the first 5 seconds of the music over and over. Its a start

---

### Post by thedrizz on 2008-04-26
so is this a "no we cant help you" by the forum as a whole?

---

### Post by Can+~ on 2008-04-26
White screen? Maybe it's working at a wrong resolution or refresh rate and screwing everything up?

Most of my problems on the ATI card where solved after I followed the unnoficial guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Sorry I wasn't available when your post was on the first page, the forum gets a whole batch of posts in less than 1 hour, specially on new releases.

I remember, when I first installed ati drivers on gutsy, I had to jump to the shell (Ctrl+Alt+F1) and edit xorg.conf to add my own resolution, since, ati didn't filled that for me.

---

### Post by thedrizz on 2008-04-27
> **Can+~ said:**
> White screen? Maybe it's working at a wrong resolution or refresh rate and screwing everything up?

Most of my problems on the ATI card where solved after I followed the unnoficial guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Sorry I wasn't available when your post was on the first page, the forum gets a whole batch of posts in less than 1 hour, specially on new releases.

I remember, when I first installed ati drivers on gutsy, I had to jump to the shell (Ctrl+Alt+F1) and edit xorg.conf to add my own resolution, since, ati didn't filled that for me.

What on the unofficial guide do you want me to follow?

---

### Post by thedrizz on 2008-04-27
could you give me more detail on what in the xorg.conf i should edit? This is rather frustrating, but when i opened xorg with the white screen, its noticibly smaller than it is now.

---

