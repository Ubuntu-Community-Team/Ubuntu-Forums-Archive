---
title: "Problems with grub loader v1.5 - error codes 17 and 21"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by DannyJigg on 2008-05-28
Hi,
i have recently started using ubuntu alongside windows, but on separate drives and have encountered a few issues.

I installed ubuntu on my secondary hdd where it made a partition of 250gb on a 300 drive. I was not too pleased with this as i use this drive for backing up my main hdd. 

I attempted to uninstall it, but after about 5 minutes of doing nothing and no disk activity my pc powered off.
I tried a reboot and selected to load windows xp. It ran a scandisk and said there were errors on my secondary disk and had fixed them. I proceeded to check the folders were ok, but found that there was only 1.5gb of space remaining and my backup was originally about 10gb so found that unusual.

I copied all of the files i could and formatted the drive suspecting a major issue, and rebooted again. bios was ok, but after the 'verifying dmi' step of the boot i got the message grub loader error 17, after which the system just hangs. I rebooted again and gt to the same point and got error message 21. I disconnected my secondary hdd, and rebooted, but it then didnt hit bios.

I reset cmos via the jumper and reconnected the hdd, i got error 17 again. I tried a boot from the live cd and a fresh install to the secondary hdd using it all. Now it is not detecting any hdd i connect and subsequently not able to run any os that isnt a live disk. 

Any ideas?
thanks in advance

---

### Post by rraj.be on 2008-06-01
The best way to remove a complete OS from a  partition completely is to formate it.
now i think you have'nt removed your ubuntu completly and thats the cause for your problem at first.

Now after formating the problem is due to your GRUB.

When you install ubuntu it will replace your ntldr of windows with GRUB.

now you want to make your windows bootable.

Try to connect each of your hard disk to a perfect clean windows and run chkdsk..

this will solve your problem.

If further not just get into recovery mode and replace your ntldr and boot.ini.

just i think this will help yu to know about GRUB

```
http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17
```

if you want to know abt it.

Super grub may also help.

just read more abt that there

---

### Post by bumanie on 2008-06-01
As long as xp is still in tact you should be able to fix its boot sector with the xp install disk. We can worry about getting ubuntu running again once xp is going.

---

### Post by meierfra. on 2008-06-01
Check out [hermanzone]("http://www.users.bigpond.net.au/hermanzone/p18.htm") It explains  various ways  how to fix your MBR.

---

### Post by DannyJigg on 2008-06-01
Thanks guys (or girls) going to try all of the above and hiren that a friend of mine recommended. Will let you know how it goes

---

### Post by rraj.be on 2008-06-01
I cant get you


Is hiren your friend ?
 or you are telling bout the boot Cd.

I have a boot Cd called hiren consisting of all PC troubleshooting ,cleaning, Backup tools , pasword recovery tools etc.

you can find more info here

[www.hiren.info/pages/bootcd]("www.hiren.info/pages/bootcd")

and you can download it here

[soft.softoogle.com/ap/ hiren-s-bootcd-download-6916.shtml]("soft.softoogle.com/ap/ hiren-s-bootcd-download-6916.shtml")

---

