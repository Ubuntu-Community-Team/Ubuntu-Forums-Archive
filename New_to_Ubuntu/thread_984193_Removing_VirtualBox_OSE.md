---
title: "Removing VirtualBox OSE"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-11-16
When I try to remove VirtualBox OSE, why in the world does aptitude try to uninstall all my kernel modules:

```
$ sudo apt-get remove virtualbox-ose virtualbox-ose-modules 2.6.24-19-generic virtualbox-ose-source

The following packages will be REMOVED:
  dkms{u} fakeroot{u} linux-backports-modules-2.6.27-7-generic{u} linux-headers-2.6.24-17{u} linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} virtualbox-ose
  virtualbox-ose-modules-2.6.24-19-generic virtualbox-ose-source
0 packages upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 142MB will be freed.
```

The kernel I am running:

```

brad@brad-laptop-ubuntu:~$ uname -r
2.6.27-7-generic

```

---

### Post by Rplus9 on 2008-11-16
I cam looking for the same answer! If I figure anything out I'll be back.

---

### Post by gjoellee on 2008-11-16
You should uninstall Virtual Boc from synaptic, that is safe...

---

### Post by yousellstuff on 2008-11-16
if you ever need a clone script of a big website like facebook or you tube, just go to [www.clonedscripts.info](www.clonedscripts.info)

---

### Post by linkmaster03 on 2008-11-17
Thanks, very surprisingly, I could remove them under Synaptic.

---

### Post by kernelhaxor on 2008-11-17
In your apt-get remove command, why do you have "2.6.24-19-generic" that? .. That should not be present .. That explains it

---

### Post by Silverspell on 2008-11-18
Hey, all. I have recently removed Vitualbox OSE because i wanted to put Vbox 2.04. Eventually i could not install it (i am getting a weird message, which i can post if needed when i get back from work). My main problem is that now, although i uninstalled Vbox from Synaptic, when i reinstalled it and reinstalled the virtualbox-ose-modules-generic it still cannot find them (I am getting a message saying it cannot load the kernel modules). I removed it again through terminal, reinstalled...the same.

Any ideas?

I am running Ubuntu 8.04 by the way.

---

### Post by Rplus9 on 2008-11-19
yeah i'm having issues getting the virtualbox-ose-modules-generic-2.6.27 at all.

that's for 8.10 though.

---

### Post by statto1977 on 2008-11-19
I removed Virtualbox via the add/remove programs box. I assumed I'd have more hard drive space afterwards (I can't remember how much I assigned it upon install) but that doesn't seem to be the case. Has anyone got any ideas why?

---

### Post by shifty_powers on 2008-11-19
have you checked if it has removed the .virtualbox folder in your home partition? this is where it stores you virtual harddrive images....

---

### Post by dusted on 2008-11-19
Agreed, removing Virtualbox does not remove the virtual hard drives it created, be default it will save them to ~/.virtualbox unless you specified to save it somewhere else.  Just a quick hint, buy a 4GB or 8GB flashdrive or SD card or some removable storage and save your virtual disk on there, then you don't have to worry about losing physical hard drive space.

---

### Post by shifty_powers on 2008-11-19
but you do have to worry about the loss of performance....

---

### Post by statto1977 on 2008-11-19
> **shifty_powers said:**
> have you checked if it has removed the .virtualbox folder in your home partition? this is where it stores you virtual harddrive images....

Ahh, thanks for that, that was it. :)

---

### Post by shifty_powers on 2008-11-19
np's, my pleasure :D

---

