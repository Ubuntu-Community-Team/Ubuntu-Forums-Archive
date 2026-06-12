---
title: "stuck on installation"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by mr. awsome on 2008-12-01
i am using wubi to install ubuntu 8.10, i have all the files downloaded but when i select ubuntu for one of the boot choices it goes to the screen t would usually go to boot up but it loads a little bit of it then stops forever.

windows xp media center edition
 toshiba satellite a100
ATI RADEON EXPRESS 200M SERIES
1406 mb of ram

---

### Post by Kellemora on 2008-12-02
Hi Mr A

Sorry to see none of the guru's have picked up on your message here!

I've been stuck with the XP-MCE edition myself, more problems than Carters has pills.  Major hardware vendors like HP don't even support this platform for their products!

I don't know what Wubi is, so will be of no help here, just making a reply to cause your question to be bumped back to the top of the list so it might be responded to by someone in the know!

Good Luck

TTUL
Gary

---

### Post by mapes12 on 2008-12-02
This may help: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by mr. awsome on 2008-12-04
sorry but this doesn't really help because i cant even do anything after i choose ubuntu on the boot choices it just gets stuck on loading

---

### Post by nakama85 on 2008-12-04
> **mr. awsome said:**
> sorry but this doesn't really help because i cant even do anything after i choose ubuntu on the boot choices it just gets stuck on loading

As much as it hurts me to tell you this, this may be a graphics card problem that as of yet has not been unsolved.

I had this same issue with a card I had. Once I switched graphics cards everything worked fine.

My recommendation is to search for you g card in the forums and see if that is the problem.
Or even better if you have access to another card try that and see if it works.
On the bright side if it is your Graphics card then you have it narrowed down.

Sorry I could not be more help

---

### Post by falcon61102 on 2008-12-04
The next time you boot up and get to the GRUB, select the Recovery mode, it should be the second item on the list.  This should let you get into Ubuntu so that you can attempt to work around this issue.

Once you get into Ubuntu, check to see if you need any restricted drivers by going to System>Administration>Hardware Drivers.  That will scan your hardware and allow you to enable any restricted hardware.  Also, you may want to update Ubuntu at this point as well.  There have been quite a few updates and that may resolve the issue.

---

### Post by mapes12 on 2008-12-04
> As much as it hurts me to tell you this, this may be a graphics card problem that as of yet has not been unsolved.Have you tried booting from a Ubuntu Live CD? If the Live CD works you will know that your hardware can run Ubuntu. Therefore, your problem will be an issue with how wubi has been set up within windoze. If you can't get a wubi installation to work you can look at a dual boot installation. Here's a HowTo: [http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

Also, If you experience problems installing from a Live CD (one of my machines hates the Live CD) then try an alternate CD from here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

