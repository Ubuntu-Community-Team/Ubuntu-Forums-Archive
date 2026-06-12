---
title: "Remove previous installed OS"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Alexbit on 2008-06-30
Hi all!
As you can appreciate if you my previous post I'm a really beginner with *buntu.

Some days ago I've decide to switch my personal laptop from Windows to *buntu.

That's the story:
Windows was on the laptop
First time I've installed Ubuntu in a separated partition.
Second time I've installed Kubuntu in a separated partition.
NOW I plan (and hope) to remain with Kubuntu and I want to remove Ubuntu to get back some space.
In a later time I always want to delete Windows too.
The partition schema is the one you can see in the attachment.

Can you post a safe method to remove ubuntu and preserve the possibility to boot Kubuntu or windows xp home sp2?

If you need more detail of my configuration don't hesitate to ask.

Thank you in advance,
Ale

---

### Post by novatotal on 2008-06-30
put the live cd of kubuntu and restart, now start parted and edit your partitions, asigning the free space as you see fit; next reinstall grub, exit and restart

---

### Post by sayakb on 2008-06-30
Since Kubuntu was installed in the end, you might not lose Grub when you wipe off your Ubuntu partition. Also, whatever may be the case, grub will not be affected if you clear up your Windows partition. Download and burn the Supergrub disc and Gparted LiveCD. Boot into the Gparted LiveCD and remove the Ubuntu partition. Reboot and check. If you lose Grub, just put in the Supergrub Disk and reconfigure/reinstall grub again.

---

### Post by Alexbit on 2009-01-02
Sorry for the very betrayed answer.
I really forgot to reply!
Today for the past i say thank you for the reply.
Today I'm *only* with ubuntu.
Simply I've backup all my data, I've re-parted the hard disk to fit my new assets and, finally, I've intsalled a fresh copy of ubuntu.

Have a nice day!
Ale

---

### Post by bryncoles on 2009-01-02
just for reference, if you install ubuntu and then decide you want to try another flavour, such as xubuntu or kubuntu, you can just open synaptic package manager and search for 

```
kubuntu-desktop
```

this will install kubutu alongside ubuntu without the need for a separate partition. if you want to use kubuntu instead of ubuntu, click 'sessions' at the login screen and select the appropriate one from there!

---

