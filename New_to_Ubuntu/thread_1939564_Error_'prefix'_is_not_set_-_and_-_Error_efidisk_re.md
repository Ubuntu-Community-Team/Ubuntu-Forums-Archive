---
title: "Error 'prefix' is not set - and - Error: efidisk read error"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by ClientAlive on 2012-03-11
Hi,

I just installed Ubuntu 11.10 on a UEFI system. I recall that when I booted the installation cd there was an error that flashed across the screen "Error 'prefix' is not set"

I was pretty sure this message was coming from my firmware and figured it was something that would get ironed out after the install completed. Perhaps it did because I don't see that one now, after the install is complete.

What I do see now comes up when I boot the new system. When the firmware first begins to boot the o/s I get: "Error: efidisk read error". I mention both because I think they may be related or the first might at least be a clue to the second.

I also noticed that only 1 MB is used in my efi system partition (output of df -m). This corresponds more to a BIOS install of grub I think. What's confusing is I recall seeing the name "grub-efi" going by in the install messages durring installation.

Can anyone help me sort this out?

Thanks in advance...
Jake

---

### Post by Azyx on 2012-04-11
bump

---

### Post by ClientAlive on 2012-05-08
I ended up installing 12.04 server as a BIOS install (not EFI, which, to be perfectly honest, makes me feel sick). The install works, for the most part. I get some grub error I don't know how to deal with (fd0 read error and fd1 read error) but it doesn't seem to have an adverse effect on the system (except for being annoying and delaying my boot time).

---

