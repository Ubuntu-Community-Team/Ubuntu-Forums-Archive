---
title: "Can you have a usb flash drive that is recognized by windows 10 (host) and ubuntu (vm"
date: 2020-02-06
forum: New to Ubuntu
---

### Post by justindwalker87 on 2020-02-06
Can you have a usb flash drive that is recognized by windows 10 (host) and ubuntu (virtual box)?I got two identical usb 2.0 flash drives, and one I put a wallpaper photo on via windows 10, and this one can't be accessed on ubuntu. The other one comes up in ubuntu but then when I try to access it from windows it doesn't show up. Anyone know what to do? Thanks, clearly I'm new

---

### Post by thehipho on 2020-02-06
Hi, are they using the FAT file system?

To find file system type from Linux:

```
df -Th
```

---

### Post by TheFu on 2020-02-06
They need to use either FAT32 or exFAT file systems and Windows needs to properly close the file system before it is removed. Basically, press the "eject" button.
If going through virtualbox, then the USB port needs to be exclusive to the running VM when in use.  Similar to Windows, you'll need to eject and/or umount the storage before removing it from the USB port.

---

### Post by CelticWarrior on 2020-02-07
And actually answering the implicit question...

At the same time? No. Any USB mass storage device passed to the VM will be unavailable in the host.

But considering this is likely a X-Y problem, @[**[COLOR=#000000]justindwalker87[/COLOR]**]("https://ubuntuforums.org/member.php?u=2139832"), you should be using "shared folders" instead. Please consult the manual or online documentation of the hypervisor you're using.

---

### Post by TheFu on 2020-02-07
There are two sorts of sharing.
[LIST=1]
[*]Normal, default, network sharing (samba/cifs)
[*]Hypervisor hostOS disk access
[/LIST]

Network sharing between systems, hypervisor or not, works just like any other network file sharing, with the same risks and mitigations. Between Windows, the normal protocol used is CIFS.  Between Unix systems, use NFS.  There is an NFS for Windows, but it is a pain, so almost everyone uses samba, including me.

Hypervisor hostOS disk shares work from a client to storage on the hostOS.  The safety of this has proven to be less than network shares and file locking has proven to be flawed in a few implementations. I've been burned by the vboxsf driver, for example. Linux kernel devs just rejected that driver: [https://www.phoronix.com/scan.php?page=news_item&px=VirtualBox-Shared-Folder-5.6](https://www.phoronix.com/scan.php?page=news_item&px=VirtualBox-Shared-Folder-5.6)

Using network sharing means both systems have access to the storage concurrently.  I wouldn't do any sort of sharing with portable USB storage. Too easy to forget to shutdown the sharing services before removal.  That could be very bad and cause data corruption.

There are probably other considerations that elude me now. Hopefully, someone else can expand.

Back on the original exFAT option - with Linux, the exfat driver package must be installed.  I don't recall the exact name. Sorry. Something like *exfat-utils* would be expected.

---

### Post by justindwalker87 on 2020-02-07
Thank you all so much, helped a lot!

---

### Post by oldrocker99 on 2020-02-07
ANY computer, camera, phone can read FAT. exFAT is readable by both OSes, and is a better filesystem than FAT is.

---

