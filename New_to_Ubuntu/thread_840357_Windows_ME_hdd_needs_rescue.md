---
title: "Windows ME hdd needs rescue"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by querent on 2008-06-25
Hi.  My mom had an old compaq with windows me.  It crashed recently, such that it now boots into the desktop, reboots immediately, ad infinitum.  She has some un-backed up financial data on there.  I pulled the hdd out and put it in an external casing, hoping I could mount it like an external hdd.  (I run heron.)  I saw it once under "Computer", but it said it couldn't mount, and now I see it no more.  I tried booting from it (there's a "USB Memory" option when you use f12 to enter the boot menu at startup), but it doesn't even seem to try.  goes straight to GRUB and ubuntu.  

I'm a noob.  Be gentle.  Oh...and she's thinking of switching over (she just got a laptop with vista and i've been preaching the word).  if the community can help, it might win a convert.

Thanks all!
q

---

### Post by Kevbert on 2008-06-25
Hi.  You can get a boot disk for Me from [here]("http://www.bootdisk.com/"). 
Once you've made a disk, boot from it and you should be able to see the files on the hard disk.  You may need to set up the boot option in bios, in order to do this.
If it doesn't work with the Me disk try an XP boot disk (at the same URL).
Good luck.

---

### Post by fiddledd on 2008-06-25
You could try booting the ME machine in Safe Mode (press F8 as it boots) then run msconfig and check "Diagnostic Startup" then load your drivers until you find the one that causes the restart loop and disable it from Safe Mode again.

---

### Post by prshah on 2008-06-25
> **querent said:**
> 
  (I run heron.)  I saw it once under "Computer", but it said it couldn't mount, and now I see it no more.  


Unplug it, wait 15 seconds; then replug it in and wait 15 seconds; then open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

dmesg | tail
fdisk -l
lsusb

```

---

### Post by querent on 2008-06-25
> **Kevbert said:**
> Hi.  You can get a boot disk for Me from [here]("http://www.bootdisk.com/"). 
Once you've made a disk, boot from it and you should be able to see the files on the hard disk.  You may need to set up the boot option in bios, in order to do this.
If it doesn't work with the Me disk try an XP boot disk (at the same URL).
Good luck.

Ok...no one here has a floppy drive.  three laptops in this house are all that function.  If this isn't a problem, let me know.

Working on the other suggestions.  Thanks to all.
q

---

### Post by querent on 2008-06-25
here's the output:

william@ubuntu:~$ dmesg | tail
[  758.743144] scsi 5:0:0:0: Direct-Access     WDC WD15 0AA-60BAA0       10.0 PQ: 0 ANSI: 0
[  758.746221] sd 5:0:0:0: [sdb] 29336831 512-byte hardware sectors (15020 MB)
[  758.747215] sd 5:0:0:0: [sdb] Write Protect is off
[  758.747222] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  758.747227] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  758.748702] sd 5:0:0:0: [sdb] 29336831 512-byte hardware sectors (15020 MB)
[  758.750126] sd 5:0:0:0: [sdb] Write Protect is off
[  758.750135] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  758.750139] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  758.750146]  sdb:
william@ubuntu:~$ fdisk -l
william@ubuntu:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 010: ID 067b:2507 Prolific Technology, Inc. PL2507 Hi-speed USB to IDE bridge controller
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
william@ubuntu:~$

---

### Post by bumanie on 2008-06-25
Do you think the problem is with the drive or the filesystem/boot sector/partition table of the drive? If it is the latter, I would plug the drive in and get the [testdisk live cd]("http://www.cgsecurity.org/wiki/TestDisk") and see if it recognizes the hard drive. Testdisk can repair partition tables and rewrite 'windows-like' boot sectors (as well as recover data from unwanted filesystem deletion). If you think the drive has developed a problem, have a look at using dd commands to copy the data to another drive, before your drive dies completely. Before trying any of these, if you decide to, read all documentaion very carefully, or else you might inadvertantly destroy the information that is on the drive by using these tools incorrectly.

---

### Post by querent on 2008-06-25
ok...here's some voodoo...i ran the diagnostics that i posted, rebooted, and the drive was recognized.  it's an icon on the desktop, like any external hdd.  I got the stuff off!  no idea what's happened here.  did i mount it somehow in the commands i gave (that are posted)?

thanks to all for whatever has happened!

q

---

