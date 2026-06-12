---
title: "Something like puppy, but hd-install?"
date: 2007-12-14
forum: Other OS Talk
---

### Post by Anaphylaxis on 2007-12-14
Hi, Folks. I have a couple of old PCs with 128 and 256 megs of RAM respectively. They are both using wireless connections to the internet, D-link usb and D-link pci, both with ralink drivers. Ubuntu is too demanding for these old timers, and xubuntu/fluxbuntu seems to have a hard time getting me online, I have to play around with the GUI as if it was a slot machine, sometimes you win, sometimes you don't. The only OS consistently getting my n00b a$$ online seems to be puppy. Oh, and Mandriva, but it is too slow, and I don't know my way around with KDE. Zenwalk leaves me with ndiswrapper, now what the f. is that? And it doesn't even work. :(

Could somebody give a n00b like me some advice on how to get an OS onto my wireless computers that both has the puppy support to get me online, lightweight applications for browsing and watching films, and a lightweight DE or WM suitable for 128MB RAM? 

I suppose I could get the machines wired and do a server install of a 'buntu, what would I have to download in addition to get me such an OS, and what would I have to configure myself/learn to configure? Menu entries? 

Give me some starting help so I can play a little over the holidays. :D

---

### Post by stalker145 on 2007-12-14
> **Anaphylaxis said:**
> ... wireless computers that both has the puppy support to get me online, lightweight applications for browsing and watching films, and a lightweight DE or WM suitable for 128MB RAM? 

Why not just install [Puppy]("http://www.puppylinux.org/user/viewpage.php?page_id=1") on them since it seems to work? There *is* an option to install to disk.

---

### Post by mips on 2007-12-15
I think what he means is he is looking for a installable CD that will give him wireless net access from a live/fresh install environment similair to what puppy offers but he does not actually want to install puppy on the HD.

So he is looking for a distro where his wireless will work out of the box and it will need a lightweight WM like Fluxbox etc.

Anaphylaxis, is this what you mean?

---

### Post by Anaphylaxis on 2007-12-15
Yep, you got it. I would have used fluxbuntu, but for some reason, the GUI in puppy gets me online, but not the one in fluxbuntu. Kinda strange that a tiny OS like puppy so far has the best hardware recognition. Is it possible to install the wireless recognition programs that puppy uses and put it on a 'buntu?

---

### Post by HermanAB on 2007-12-16
You can try Xubuntu or install Mandriva and select IceWM as the desktop (IceWM is even faster than Xfce).

However, if you already tried Puppy and it works, then why change?  Puppy is fun really and you can install a lot more schtuff if you want, it doesn't have to be minimalist.

Cheers,

Herman

---

### Post by tommcd on 2007-12-18
> **Anaphylaxis said:**
> Hi, Folks. I have a couple of old PCs with 128 and 256 megs of RAM respectively. They are both using wireless connections to the internet, D-link usb and D-link pci, both with ralink drivers. ........Zenwalk leaves me with ndiswrapper, now what the f. is that? And it doesn't even work. :(
:D

If your wireless card uses Ralink drivers there is no need to use ndiswrapper in Zenwalk. My wireless card uses the rt61 driver. Just use the latest CVS tarball from here:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)
It works fine for me.
Just extract, then make, then make install, then modprobe driver_name.
Then add your wireless settings to /etc/rc.d/rc.inet1.conf as per here:
[http://wiki.zenwalk.org/index.php?title=Broadcom_bcm43xx_ndiswrapper](http://wiki.zenwalk.org/index.php?title=Broadcom_bcm43xx_ndiswrapper)
Just change driver name to the name of your driver. A computer with your specs should run fine in Zenwalk. Write back if you need more help with this.

---

### Post by init1 on 2007-12-18
Antix has fluxbox, and the best hardware detection for my laptop (because of it's Mepis base). The older version (6.5) is better IMHO, even though the packages are ancient. 
[http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page)

---

