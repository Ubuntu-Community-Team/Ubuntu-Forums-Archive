---
title: "Xfce 4.2 ?"
date: 2005-03-19
forum: Repositories &amp; Backports
---

### Post by Biffy on 2005-03-19
Hi. Xfce 4.0 is aviable in APT. But it is old, when will 4.2 be added? I know i can install it manually, but i like to keep my apps in .deb format so they all show in my package manager.

---

### Post by Nikola on 2005-03-19
Deb repository for latest and greatest Xfce4:

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

---

### Post by Biffy on 2005-03-20
[QUOTE=Nikola]Deb repository for latest and greatest Xfce4:

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main[/QUOTE]

Can i add them and install from thoose reposotories without risking that my system crashes down or something?

---

### Post by Biffy on 2005-03-20
Ok, so i added the first one. Seems to work fine, but i get this message:

```
W: GPG error: http://www.os-works.com testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CF455A0A8AC2C0A6
```

What's the point with deb-src btw?

---

### Post by Nikola on 2005-03-20
Don't pay attention to gpg error, AFAIK you have to import their public key or something like that, just ignore it.
And about src packages? Again, I realy don't know except you can choose to rebuild from source or something..if someone else can fill info about that, go on :-)

---

### Post by LongTooth on 2005-03-21
It wouldn't be a bad idea to comment out the deb repository afterwards. Those play hell with upgrades.

---

### Post by bored2k on 2005-03-21
[QUOTE=Biffy]Can i add them and install from thoose reposotories without risking that my system crashes down or something?[/QUOTE]
 Yes it is risk-free.

I used them to install XFCE , and It is mad awsome :D .

---

### Post by maqi on 2005-03-24
Check out post #4 in [this](http://ubuntuforums.org/showthread.php?t=21024) thread and follow the link. Take note of the info regarding your /etc/apt/preferences file - this is a good way to control how apt-get deals with different/multiple repositories. Glanz knows what he's talking about :)

maqi

p.s. for more info on the preferences file go [here](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin).

---

