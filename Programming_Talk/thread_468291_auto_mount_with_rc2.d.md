---
title: "auto mount with rc2.d"
date: 2007-06-08
forum: Programming Talk
---

### Post by etechship on 2007-06-08
I am trying to make one of my USB devices mounted ever time the computer turns on. I think that runlevel is 2, but I'm not even sure about that. I make a file named S99mount with the below content and but copied it to rc3.d, rc4.d and rc5.d (from rc2.d). I have already made the folder red5 in /usr/lib. I can run that same command one I log in, so the command works.

Content:
mount /dev/sda1 /usr/lib/red5

thanks
dave

---

### Post by yabbadabbadont on 2007-06-08
Use sudo or gksudo to edit your /etc/fstab and add an appropriate entry for your USB drive.  Then it will be mounted for you at boot automatically.

---

### Post by steve.horsley on 2007-06-08
I confirm that rc2.d is the right place for the script. You may well need to specify **/bin/mount** instead of just **mount**.

But /etc/fstab is the right place to configure which filesystems should be mounted at boot. **man fstab** will help. My only concern is that I'm not sure if it will work for USB disks - depends if USB services get started before fstab is processed, and I'm not sure.

---

### Post by yabbadabbadont on 2007-06-08
Modules are loaded prior to non-root filesystems being mounted as those modules may be needed in order to mount them.  e.g. samba, nfs, vfat, ntfs, ...  The modules needed for the root filesystem to be mounted are loaded by the initrd.

---

### Post by etechship on 2007-06-09
so if I just edit /etc/fstab I should be okay? I don't have to do the rc2.d thing then?

Can you please explain what <dump> and <pass> are?

I think I figured out everything else. I will copy what my file looks like here.

Content:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/ida/c0d0p1 /               ext3    defaults,errors=remount-ro 0       1
/dev/ida/c0d0p5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /usr/lib/red5   ext3    rw              0       1

```

thanks
dave

---

### Post by yabbadabbadont on 2007-06-09
The fstab man page can explain "dump" better than can I.  :D

The "pass" option just determines the order in which the file system will be checked during boot.  Root should always be '1' and generally the others should be '2'.  i.e. root is checked on the first pass and the rest are checked afterwards.

---

### Post by etechship on 2007-06-09
ok, the dump and pass are okay, but what did I do wrong to not make the USB device not bootable?

---

### Post by yabbadabbadont on 2007-06-10
> **etechship said:**
> ok, the dump and pass are okay, but what did I do wrong to not make the USB device not bootable?
What do you mean "bootable"?  You never mentioned that before.  /etc/fstab is only used when you boot linux.  If you are trying to boot from your USB drive, then you will have to configure your system BIOS to boot from USB (assuming that your BIOS even supports that option).

---

### Post by etechship on 2007-06-10
I didn't mean as in I'm running Linux from it. I meant that It still doesn't auto mount on start-up. I think it needs to load the USB drivers for it first. Anyway yo do that?

---

