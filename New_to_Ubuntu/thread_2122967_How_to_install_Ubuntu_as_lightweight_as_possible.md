---
title: "How to install Ubuntu as lightweight as possible?"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by ArnsteinK on 2013-03-06
I want to install Ubuntu, but as lightweight as possible(so I can decide later what to install with it). How can I do this? Can I install it from command line when running from the CD?

---

### Post by mamamia88 on 2013-03-06
Well you could do a command line only install which will leave you with just a command prompt with the mini iso.   Then you can just apt-get install everything you need --no-install-recommends which should keep everything as light as possible.  I suggest lubuntu though for a shortcut.  [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by ArnsteinK on 2013-03-06
Thanks! Where can I find this mini iso? It was easier to find on earlier versions I think.

---

### Post by mamamia88 on 2013-03-06
on the page on the link above.

---

### Post by mörgæs on 2013-03-06
For 12.04:[URL="http://andyduffell.com/techblog/?p=689"]
http://andyduffell.com/techblog/?p=689[/URL]

---

### Post by ArnsteinK on 2013-03-06
Haha, didn't you edit the post? I must be blind! Thanks :)

---

### Post by ManamiVixen on 2013-03-06
Be aware though that the mini ISO usually cannot use wireless cards without a lot of work, you need a wired Ethernet connection install from them.

---

### Post by Sef on 2013-03-06
You could do a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD").

---

### Post by Merrattic on 2013-03-06
If using the mini.iso, be aware that after you select your apt mirror, the system will spend quite some time 10 - 20 minutes grabbing files from the mirror. You may think the installation has stalled, so be patient at this point, there is no feedback on screen to tell you what is happening.

---

### Post by tartalo on 2013-03-06
If the mini iso refuses to download things from any mirror you try (happened to me several times, don't know why) (*) download the alternate iso of any _buntu, press f4 in the first screen and choose "Install a command line".

EDIT: (*) Oh, probably what Merrattic explained above

---

