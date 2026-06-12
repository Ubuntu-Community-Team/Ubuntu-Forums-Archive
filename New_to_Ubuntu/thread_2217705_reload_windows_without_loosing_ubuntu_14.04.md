---
title: "reload windows without loosing ubuntu 14.04"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by rollo2 on 2014-04-18
Hi
Some how my windows 7 OS has lost a drive and won't load . I now have windows 8 how can I install this with out losing my ubuntu 14.04 OS or messing up the grub
I am not a very experenced user so please dont get to technical.
Thnaks
[email]rollo@ravenscroft.za.net[/email]

---

### Post by Double.J on 2014-04-18
Hi there,

A very warm welcome to the forums!

as far as I know there is still no way to install windows without a bootloader from their installer. The good news is that windows can't see your ubuntu partition, so as long as you do not format the whole disk, it's just a case of install windows, then boot an ubuntu live cd and run [boot repair]("https://help.ubuntu.com/community/Boot-Repair").

Just make sure you back up first. I also like to use gparted to organise my disk first. Remember thst windows has to be the first OS on the drive, and that you would not want to give it less than 60GB. I usually leave this as free space, so i can just tell windows to format the free space (more often than not if you format as ntfs in gparted, windows will want to reformat it anyway)

best of luck, and one last time, please back up ;)

Jj

---

