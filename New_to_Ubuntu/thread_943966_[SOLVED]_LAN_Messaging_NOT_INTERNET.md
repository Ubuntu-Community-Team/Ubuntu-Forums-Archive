---
title: "[SOLVED] LAN Messaging NOT INTERNET"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Kellemora on 2008-10-10
Hi Gang

Is there a program similar to RealPopUp for local LAN messaging in Ubuntu?

Someone mentioned Pigeon, but that appears to require an outside account to work.  I'm looking for totally in-house peer to peer messaging.

It needs to reside in the panel and pop-up or do something when a message is there.  Like in GET THEIR ATTENTION NOW, hi hi

Thanks

TTUL
Gary

---

### Post by dhtseany on 2008-10-10
Check this out:
[http://directory.fsf.org/project/ejabberd/](http://directory.fsf.org/project/ejabberd/)

Peace
Sean

---

### Post by dhtseany on 2008-10-10
Also:
[http://linux.softpedia.com/get/Communications/Chat/EZ-Intranet-Messenger-39524.shtml](http://linux.softpedia.com/get/Communications/Chat/EZ-Intranet-Messenger-39524.shtml)

FYI: I'm getting this from googling "ubuntu intranet instant messaging"

Peace
Sean

---

### Post by Kellemora on 2008-10-10
Thanks dhtseany!

The first one looked way over my head!
But the second may be just what I'm after.
I downloaded the zip file, but haven't tried it yet.
I see on their add they are using it on Ubuntu, that gives me hope, hi hi.....

TTUL
Gary

---

### Post by dhtseany on 2008-10-11
Hey no problem. I'm curious what your final solution will be so if you don't mind post back and let me know the details :)

Peace
Sean

---

### Post by Kellemora on 2008-10-11
Hi Sean

Turns out to be a no go!

It requires Java 1.6.0 to work!

Synaptic PKG MGR only has 1.0.2 available.

I tried loading from the Java web site jre-6u7-linux-i586.bin
but have not yet figured out how to get it to install properly.
I get more Error messages than Carters has pills.
They only have i586 and rpm versions to download.
I know rpm is Red Hat's version.
Everything else I download is i386 stuff, not sure what i586 means.

If'n I get it going, I'll post again to let you know!

TTUL
Gary

---

### Post by Kellemora on 2008-10-11
Hi Sean

I finally installed Java 1.6.7 successfully, but still have a zillion errors with the EZMessenger program.

I did find out from someone else that RealPop-Up will work in WINE though!
Don't know if I want to go that route or not.
Looking into something else, like running an in-house message server.

TTUL
Gary

---

### Post by cariboo on 2008-10-11
You can't always go by Ubuntu version numbers. If you install ubuntu-restricted-extras from the repositories you should get the correct java version.

Jim

---

### Post by handydan918 on 2008-10-11
fer Pete's sake, doesn't anybody here have gray hair?!
Check synaptic for talk/ktalk.

---

### Post by jerome1232 on 2008-10-11
Not to mention pidgin, the default IM client on Ubuntu has the Bonjour plugin. It's a LAN based IM protocol.

---

### Post by dhtseany on 2008-10-12
> **Kellemora said:**
> 
I did find out from someone else that RealPop-Up will work in WINE though!
Don't know if I want to go that route or not.
Looking into something else, like running an in-house message server.

That's a pretty cool idea. I've done a little googling regarding Bonjour but so far I'm only seeing help requests for it so I'm not sure how reliable it will be for you. I'll do some research and see if anyone has done something similar with the in-house IM server.

Peace
Sean

PS- Yes, UB version numbers are at times rather inaccurate.

---

### Post by dhtseany on 2008-10-12
Hey, I won't have a box to play with until I get to work tomorrow but try this out and see if you can get somewhere:

[http://ubuntuforums.org/showthread.php?t=330634](http://ubuntuforums.org/showthread.php?t=330634)
(Note post #6)

Peace
Sean

---

