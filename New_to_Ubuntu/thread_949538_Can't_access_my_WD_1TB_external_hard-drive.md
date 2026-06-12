---
title: "Can't access my WD 1TB external hard-drive"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Freidenker on 2008-10-16
Hi everyone. I'm completely new to Ubuntu and barely know how to operate it. I was drawn to it because I've heard it's stabler, faster, and more handy than Windows.

My first problem with adapting to Ubuntu is that I can't access my external hard-drive. Using vista, I simply accessed it using "Network". Since the external hard-drive connects to my laptop via an ethernet network cable, vista simply recognizes it and I can access the external HD from there.

In Ubuntu, although there is a "network" application, it just won't identify my external HD!

Can anyone help me?
Thanks all.

---

### Post by Paqman on 2008-10-16
Does it show up under Places > Network?

---

### Post by hyper_ch on 2008-10-16
open a terminal, run the following commands, post the output here and enclose each one in [noparse]```

```[/noparse] brackets:

```

lsusb

```

```

sudo fdisk -l

```
You will have to enter your user password here!

```

df -l

```

```

cat /etc/fstab

```

---

### Post by handydan918 on 2008-10-16
> **hyper_ch said:**
> open a terminal, run the following commands, post the output here and enclose each one in [noparse]```

```[/noparse] brackets:

```

lsusb

```



For an ethernet-attached device? Really?

---

### Post by hyper_ch on 2008-10-16
oh... it's a NAS :) I thought it's a USB one ;)

Ignore all the stuff I said ;) (except for the brackets)

---

### Post by LowSky on 2008-10-16
If its a network drive you might need Samba, especially if its formated for Windows' Networking

---

### Post by Freidenker on 2008-10-16
Samba? A-what-now? I DID mention I'm completely new to Ubuntu. What's Samba, how do I use it, and more pertinently, how can I use it to access my EHD?

---

### Post by Paqman on 2008-10-16
What model is this device? Is it a NAS or a Hard drive? Do you plug it into the router, or directly into the PC? Try searching this forum using the exact model number and see if someone has already set one up.

SAMBA is just a system for getting Linux machines to talk to a Windows network. Don't sweat it, it probably won't be at all hard to set up, and we can walk you through it.

---

### Post by Freidenker on 2008-10-16
Everyone, I was fiddling with Samba (I saw one of you mentioning it and I thought, what the hell) and for some reason, it worked. I can now access it pretty much the same way I accessed it in Vista. I have two more problems I wish to resolve and then I'm pretty much a-okay with using only Ubuntu as an OS. This is GREAT!

Hopefully, you're going to stick around for the other stuff I got to ask...

---

