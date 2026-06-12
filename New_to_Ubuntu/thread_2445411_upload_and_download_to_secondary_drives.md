---
title: "upload and download to secondary drives"
date: 2020-06-13
forum: New to Ubuntu
---

### Post by robhill19652 on 2020-06-13
I thought I already posted this but can't find it anywhere.

I'm having issues uploading and downloading to all my drives except my boot drive. I have two board mounted nvme drives. One is a dual boot with Kubuntu 20.04 and Windows 10. The other is storage. I have 3 other sata drives, (one ssd and two spinners).
I can access, read, and write to all of the drives, but if I'm trying to download or upload to or from the internet, my nvme drive does not show up in the left column of the window manager, and the other 3 sata drives won't let me download to them.I get an error popup (cannot read contents..., permission denied. I've tried with Chromium and Firefox both. Ideas?

---

### Post by CatKiller on 2020-06-13
You've not said how and where you've mounted those partitions.

Chromium is likely a snap, so it won't be able to access files outside your home folder regardless without setting its permissions.

---

### Post by robhill19652 on 2020-06-13
> **CatKiller said:**
> You've not said how and where you've mounted those partitions.

Chromium is likely a snap, so it won't be able to access files outside your home folder regardless without setting its permissions.


The 4 drives I'm having problems with are single partitions.
The boot drive has 5 partitions, MBR, Win 10, Win 10 Recovery, Kubuntu 20.04, and Linux swap.
I'm not sure what you're asking.

Chromium was installed with Synaptic, not snap, and Firefox was preinstalled. Both browser are doing the same thing.

FYI. I've been running dual boot linux/windows for years. I recently changed from Linux Mint and Windows 7. I had to upgrade to Win 10 due to no more support for Win 7. Mint 19.04, I was having issues with the windows manager freezing up on me, 

This is the first time I've had issues accessing other drives. It's not an issue if I'm just reading, writing, creating, deleting. It's only an issue when uploading or downloading.

---

### Post by TheFu on 2020-06-13
On Ubuntu 18.04 and later, all chromium installs are snaps.  snaps are constrained where they can read and write to the userid HOME.  The .deb file for chromium, forces the snap to be installed. They call it a "transitional package."

Check snap installs with **sudo snap list**

As for Firefox, i can only guess the issue is normal unix permissions for the Linux file systems.  The **ls -al** for the directory you want to access id needed to guess any more.  NTFS and FAT-whatever mounts set permissions only at mount time. The same ls -al for those directories is necessary, but the mount options used are also needed.

Fewer descriptions, more facts please.   Facts come from commands.

---

