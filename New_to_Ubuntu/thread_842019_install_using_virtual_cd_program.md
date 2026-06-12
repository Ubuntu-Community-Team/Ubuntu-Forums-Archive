---
title: "install using virtual cd program ?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Shoujoboy on 2008-06-27
Hi I'm wondering if I can install Ubuntu using a virtual CD program ? 
anyways I've tried already and I've gotten to the point wher when you turn on the computer you'll see Ubuntu and the other operating system and I'm wondering what do I do once I've gotten to the point after you choose ubuntu.....

---

### Post by bodhi.zazen on 2008-06-27
What kind of virtual CD are you talking about ?

You can install Ubuntu into VMWare or VirtualBox.

You can install Ubuntu with wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

You might be able to use VMWare or Virtualbox to install to a partition.

The "Standard" method is to boot the Ubutnu CD.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Shoujoboy on 2008-06-27
oh thanks for showing those programs I'll try these but I'm using windows 98 with like 128 megs of ram anyways the question I have is can Ubuntu run windows xp games mainly the ones from MSN....yeah I'm a total noob to this. Also if I can't install it from the Iso will it just run if i put it on a cd ?

---

### Post by mcduck on 2008-06-27
With only 128MB of memory you won't be able to boot the live-CD at all. Also all vitualisation options are pretty much out of the question.

You _can_ install Ubuntu using the Alternate-CD, but with as little memory as your machine has you should probably consider Fluxbuntu, Xubuntu or some other more lightweight option.. While Gnome works with that little memory, it's going to need quite slow.

---

### Post by Shoujoboy on 2008-06-28
oh thanks for helping me out there !! I was wondering why it would not open up well my mother decided it wasn't a good idea to install it on my grandmother's computer to test it out so I had to uninstall it. Now I'm wondering how to uninstall it I went to remove programs in windows 98 and I uninstalled it....but I still see the option to open it when I start the computer up...anyone know how to fix this problem? it'd be great if I could get some more of your awesome help

---

### Post by cariboo on 2008-06-28
If you have a dos boot disk, boot from the boot disk and at the c:\ prompt type:

```
fdisk /mbr
```

That should fix your problem.

Jim

---

### Post by Shoujoboy on 2008-06-28
thank you I will try that out

---

### Post by Shoujoboy on 2008-06-28
ok yeah I don't think my grandmother has the dos boot up disk so is there another way ?(i just want to remove ubuntu from the boot loader menu)<--- at leat thats what I think the menu is called

---

