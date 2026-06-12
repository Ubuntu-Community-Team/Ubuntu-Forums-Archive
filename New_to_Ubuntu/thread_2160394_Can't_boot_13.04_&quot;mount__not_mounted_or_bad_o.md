---
title: "Can't boot 13.04: &quot;mount: / not mounted or bad option&quot;"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by ryandekker on 2013-07-06
Hey there! I installed Ubuntu 13.04 on a 2007 Mac Mini to use XBMC with my TV, and it was working well for about a week. I was having some issues so I restarted (Ubuntu gave me a popup saying I should restart), except that now I can't get it to boot at all. :( I've made some progress (I think), but alas, I am unable to actually boot.

**What I've done:**
I was able to get it to boot from a CD with boot-repair which I guess gives me a sandboxed OS that is separate. I've tried running boot-repair, but it hasn't really helped. Initially I would get stuck at the grub2 menu and it wouldn't respond to any key presses. I got around that by configuring grub to wait only 10 seconds even when recordfail = 1. I also took out the "quiet" boot so I could see what the issues was.

That boot output basically was: 

```
[COLOR=#000000]mount: / not mounted or bad option[/COLOR]
```

The full output is here: [http://paste.ubuntu.com/5851374/](http://paste.ubuntu.com/5851374/)

**Where I'm at:**
Now that I have that output, I'm not really able to search for the issue because search engines strip the "/", so I'm hoping someone here can point me in the right direction.

If that's doesn't help as much as I was hoping, here's the (much longer) output that boot-repair gave me: [http://paste.ubuntu.com/5812764/](http://paste.ubuntu.com/5812764/)

I don't really see anything in there that helps me, but maybe to someone else... :)

I should note I installed openvpn recently (a few days before the issues, but the last thing I changed). I don't see how that could be causing this, but it has to be related to *something, *right? I suppose I could try to uninstall it, but apt-get seems to be running based on the clean install on the boot-repair disk, so it doesn't seem like I can just "sudo apt-get remove openvpn" or similar.

TIA for any help!

---

### Post by ryandekker on 2013-07-13
Well, I've looked into this a bit more, but I'm pretty stumped. Anyone have ideas of what I should be looking at?

Things I have tried:

[LIST]
[*]Auto repair
[*]Purge Grub before reinstalling it
[*]Repair file systems
[*]Reinstalling MBR
[/LIST]
I also tried to run fsck but the system is always mounted, and I can't seem to unmount it. The times I have run it from manual recovery it comes back "clean", but it also noted it was read only (forget the exact message).

Any attempts to implement the things I found searching seem to require a writeable file system (both Repair Disk and hard drive are readonly):

[LIST]
[*]Modify fstab config
[*]Install some tool to do various things
[*]Mount USB to backup files (bummer...)
[/LIST]
The best lead I have to go off of is a message that says:

```
coretemp: Errata AE18 not fixed, update BIOS or microcode of the CPU!
```

I'm not sure if this is the issue or just another problem. With the readonly files sytem, the fix I've found doesn't seem possible:

[http://ubuntuforums.org/showthread.php?t=1239544](http://ubuntuforums.org/showthread.php?t=1239544)

I'm at the point where I'm about ready to reinstall the OS, but I'd really like to at least pull some of my files off. If no one has ideas on how to fix the problem, can anyone tell me how to get a USB mounted to back up few things?

---

### Post by steeldriver on 2013-07-13
it may be nothing, but there seems to be a typo in your fstab (at least as reported in the boot-repair pastebin) for the root partition mount options

```
UUID=bf0decaf-2693-48d7-a193-bd3cd831b562 /               ext4 [COLOR=#ff0000]   error[/COLOR]=remount-ro 0       1
```

(should be plural [FONT=courier new]error**s**[/FONT] I think) - I don't know if that's significant or whether it would be enough to prevent the root filesystem from mounting, but you could try mounting the partition from the live CD/USB and correcting it

---

### Post by ryandekker on 2013-07-13
Unbelievable. That fixed it! Thank you SO much.

I don't even remember ever actually being able to edit that file, but apparently I did. Can't believe how long I spent on such a simple fix.

Thanks again!

---

### Post by steeldriver on 2013-07-13
Glad to help... sometimes it's the darnedest things

---

