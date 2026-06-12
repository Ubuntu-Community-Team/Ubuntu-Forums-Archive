---
title: "Triple booting... 2x Ubuntu 1x Windows"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by mrfraser89 on 2008-08-18
My setup at the moment is booting Ubuntu, rarely use Windows these days (feels great :D).

I want to however, now install Ubuntu Studio AS WELL.

How will I go about partitioning the hard drive. I have a 120gb spare partition for files etc, which I will just split for studio.

Curious however, how will I go about setting it all up? Should studio just install into a partition formatted as ext3 and mount point / ?

Give it it's own swap as well, or can it just use the existing Ubuntu's swap partition?

---

### Post by nicedude on 2008-08-18
It can use the same SWAP as Ubuntu I believe and you can just format ETX3 with mount of / but remember as you install it will redo your Grub and install it on the studio drive. No big deal but if you ever delete the studio partition it would wipe out grub and therefore you booting Windows or Ubuntu. Still not big deal as you could just reinstall Grub with a Grub boot disk, I would get a grub boot disk .iso and burn it before messing around too much in case you ever end up needing it ( it is an essential for your linux toolkit anyway )


hope that helps

---

### Post by Elfy on 2008-08-18
afaik any distro you install will use the swap so you only need 1. Do you want to keep studio seperate from your ubuntu - you could install it in ubuntu and choose which to run at login.

+1 for a copy of supergrub and I'd add partedmagic

---

### Post by mrfraser89 on 2008-08-18
Thanks for the post mate :)

Yeah already have a GRUB disk and Gparted lying around somewhere too :P

The UltimatebootCD is something I'd never be without either!

Well I'll go ahead and do it now I guess, see how she goes.

---

### Post by mrfraser89 on 2008-08-18
> **forestpixie said:**
> afaik any distro you install will use the swap so you only need 1. Do you want to keep studio seperate from your ubuntu - you could install it in ubuntu and choose which to run at login.

+1 for a copy of supergrub and I'd add partedmagic

Choosing to run it from Login might be something to consider, wasn't even aware that was an option...

How would I go about that :)?

---

### Post by Elfy on 2008-08-18
```
sudo aptitude install ubuntustudio-desktop
```

---

### Post by kansasnoob on 2008-08-18
> **mrfraser89 said:**
> Choosing to run it from Login might be something to consider, wasn't even aware that was an option...

How would I go about that :)?

Read the "Playing Around" section here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

While they're dealing with Gnome, KDE, and XFCE the same basic principles apply.

If you should decide to triple boot, I'm doing it right now with XP, Hardy, and Mint. No problem, GRUB always installs to the last Ubuntu derivative installed, but if I were to remove Mint (which was my last install) I could restore GRUB to Hardy with either the Hardy Live CD or the Hardy Alternate CD:

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

Sharing a SWAP partition is also fine, I'm doing it right now, but I only recently learned that sharing SWAP, or for that matter resizing/moving partitions, can result in SWAP not staying "on". It's easy to fix though, thanks to Mcduck:

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

---

### Post by gorgon on 2008-08-18
Hi,

Out of curiosity - why do you want two versions of ubuntu? is there anything you feel that you cannot do in ubuntu when you've installed the studio package?

---

### Post by mrfraser89 on 2008-08-18
> **gorgon said:**
> Hi,

Out of curiosity - why do you want two versions of ubuntu? is there anything you feel that you cannot do in ubuntu when you've installed the studio package?

I use ubuntu for a lot of Uni stuff at the moment, as well as playing around.

I feel if I had an OS 'just' for my photography stuff, I'd be able to focus better :)

Ideally I should have one 'just' for my uni work, but you know, fun before work :P

---

### Post by Elfy on 2008-08-18
> Out of curiosity - why do you want two versions of ubuntu?When i first got ubuntu it wasn't long before I had xubuntu and kubuntu as well - just to see what they were like lol

---

