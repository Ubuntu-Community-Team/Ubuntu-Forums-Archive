---
title: "Only one kernel ever works for me on 8.04."
date: 2008-07-06
forum: New to Ubuntu
---

### Post by SpinDizzyMR on 2008-07-06
I think it was the very first kernal that came on the current 8.04 live cd.  I have since got 3 later kernals installed iirc, and none of them work, not even in recovery mode.

The "original" boots fine. 

The others don't, and I would like the bug fixes/etc... in the later kernels. 

All of them do the same thing. 

[B]ATA2 : Failed to Indentify.
ATA2 : Failed to recover some devices, retrying in 5 seconds. [/B]

which slows it right down, but eventually fails on.

[B]Check root - bootarg cat /proc

/cmdline

or missing modules, devices : cat proc/modules is /dev

failed to locate /dev/disk/by-uuid/"long serial number"[/B]

or something along those lines.

I only have one drive, its a SATA drive.  And you'll need to explain things to me a bit like talking to an idiot as I'm not too good at this ubuntu thing.

I've looked and looked for solutions. and one thing think I can try is checking the UUID in your /boot/grub/menu to the one on something else. 

But I found some of the stuff a bit difficult to take in, I have a headache and want it dumbing down a shade. 

Also there's probably some command lines to try to boot?  Like -irq poll? is that right? I would like it functioning without having to disable everything though if necessary only as a temp measure please.

Any help rly appreciated thx.

---

### Post by SpinDizzyMR on 2008-07-07
Noone? :confused:

Well maybe this might help.

1. 2.6.22-14 is the only 8.04 kernel I have working, I don't know what they changed in the versions after that one, but none of them work for me. 

2. It's nothing to do with xserver I'm sure, which is what I usually find in a google search.

3. I think maybe altering the boot path type might help, read somewhere that there are 3 or 4 ways to boot your kernel, whether by UUID, or something like SATA-2 /sda2 or something.  I saw a great post by someone on it yet I lost it and can't seem to find it again anywhere.

---

### Post by SpinDizzyMR on 2008-07-07
Ok I've been trying again tonight. 

And with the latest kernel I know of. 2-6-24-19(?)

With the addition of pci=msi to the command line.  It fixes both errors and boots fast like it should and even succeeds and goes straight to login screen.

I was chuffed for a few moments until I attempted to log in and it froze on a blank white screen.

2 more retries and it did exactly the same thing.

I've no idea what pci=msi does, just picked it up from other threads.  Don't know if it causes the white screen or anything.

Sorta hoping one of these updated kernals might fix a bug with my wireless network too.

I know I'm probably just talking to myself, but I just thought the more I narrow it down the more someone might be inclined to have an idea and post a suggestion? *shrug*

:Edit: 

Ah nvm, 2-6-24-16 works fine, and the problem appears to be the ATI driver compatibility with latest kernels since 2-6-24-17. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235262](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235262)

I'll see what I can, but just having 2-6-24-16 on has fixed my wireless network under ubuntu, just gotta find out what pci=nomsi does and go look how to permanently add to boot cmdline.  Thx for reading me babble. LOL. :p

---

