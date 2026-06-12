---
title: "Ant w/Headlight Screen Saver?"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Akacheebe on 2012-08-28
I've played around with Linux Mint and it had a built in screen saver that is an ant with what appears to be a head light that crawls around on the desktop.  I did a search in here to see how to install it in this clean install of Ubuntu 12.04 I have but got no help that I could understand?

So has anyone installed this screen saver and if so, can you explain to me how this is done?

Thanks

---

### Post by wojox on 2012-08-28
```
sudo apt-get update; sudo apt-get install xscreensaver
```
xscreensaver is the package it's in.

---

### Post by irv on 2012-08-28
> **wojox said:**
> ```
sudo apt-get update; sudo apt-get install xscreensaver
```
xscreensaver is the package it's in.
You also need to install xscreensaver-gl-extra, xscreensaver-data, xscreensaver-gl

---

### Post by irv on 2012-08-29
Akacheebe If this worked for you why don't you mark this thread solved.
[ATTACH]223350[/ATTACH]

---

### Post by Akacheebe on 2012-09-01
Sorry I haven't gotten back sooner.  Sometimes real life gets in the way.  

The screen saver does not work unless I enable it each time I boot up and I get the following message when I enable it.

> Warning

The XScreenSaver daemon doesn't seem to be running
on display ":0.0".  Launch it now?

So it's obviously not set to start up at boot?  So how do I fix that?

Thanks,

---

### Post by irv on 2012-09-01
I kept playing around with this and got it to work. Here is what I did:
 First Remove the gnome-screensaver
```
sudo apt-get remove gnome-screensaver
```
Then set xscreensaver to run at startup.
[ATTACH]223520[/ATTACH]
Then log out and back in again and it should work.

---

### Post by Akacheebe on 2012-09-06
Thanks Irv!!  That fixed it!  :mrgreen:

---

### Post by Akacheebe on 2012-09-25
This screensaver has been working fine until an update UNINSTALLED it the other day??  It quit working and just now I checked and the entire xscreensaver program wasn't there so I had to reinstall the whole thing all over again??

So can someone tell me why an update would uninstall xscreensaver without any input from me??

Thanks,

---

### Post by irv on 2012-09-26
I did a reinstall of my OS so I had to reinstall the screensaver. I'll watch and see if this happens to me and let you know. It may have updated the Gnome-screensaver which means it had to remove the xscreensaver because there don't work together. That would be my answer. But the question is, if it wasn't installed in the first place why would it update?

---

### Post by Akacheebe on 2012-09-26
Irv, thanks for your reply.  FYI I have two systems that run the exact same version and associated programs of Ubuntu and so far, the other one hasn't done this, BUT, I did just do an update on the other system that included a kernel update so I'll watch that one to see if anything happens to it.

Funny, an update fixing some things and breaking others reminds me of Windowz! ;)

---

### Post by Akacheebe on 2012-09-28
Hey Irv, I've got it working, kinda, but I got a question for ya.  I had to reinstall xscreensaver because it got uninstalled and even after I reinstalled it, gnome screensaver would still activate and would appear in preferences when I went in there.  

Tried to uninstall gnome again but it said it wasn't there??  So, I reinstalled it so I could uninstall it again and still I got the gnome screensaver even though it was uninstalled??
Interesting though that when I reinstalled gnome it only installed one file?  Same thing when I uninstalled it?  

So, I went into gnome in preferences and set it to 2 hours before activation and now xscreensaver comes up but over time it will come up a second time over top of the original??

What did you find when you did your install?

Thanks

---

### Post by irv on 2012-09-28
> **Akacheebe said:**
> Hey Irv, I've got it working, kinda, but I got a question for ya.  I had to reinstall xscreensaver because it got uninstalled and even after I reinstalled it, gnome screensaver would still activate and would appear in preferences when I went in there.  

Tried to uninstall gnome again but it said it wasn't there??  So, I reinstalled it so I could uninstall it again and still I got the gnome screensaver even though it was uninstalled??
Interesting though that when I reinstalled gnome it only installed one file?  Same thing when I uninstalled it?  

So, I went into gnome in preferences and set it to 2 hours before activation and now xscreensaver comes up but over time it will come up a second time over top of the original??

What did you find when you did your install?

Thanks
Xscreensaver is running OK. I have my laptop set to go into screensaver after 10 minutes and when I close the lid it go into suspend.
[ATTACH]224801[/ATTACH]

---

### Post by Akacheebe on 2012-09-28
Do you have screensaver listed twice in Preferences?:confused:

Thanks

---

### Post by irv on 2012-09-29
> **Akacheebe said:**
> Do you have screensaver listed twice in Preferences?:confused:

Thanks

If you mean startup preferences, I only have it once.
[ATTACH]224834[/ATTACH]

---

### Post by Akacheebe on 2012-09-30
No not startup.  I'm running Mate 1.4 so my Preferences may look different from yours if you're running unity.  In mine I have two Screensaver icons in the Preferences menu.  One lists the ant screensaver and the other doesn't.

---

