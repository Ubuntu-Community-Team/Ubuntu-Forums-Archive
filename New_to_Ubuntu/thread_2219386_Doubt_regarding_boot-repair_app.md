---
title: "Doubt regarding boot-repair app"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by thomsebastin on 2014-04-23
I had Ubuntu 13.04 and then I installed windows 7 as it is required for me at my work place.As usual ,windows wrote over the MBR and now I've been trying to get back the boot screen by installing boot-repair from ppa on a live Ubuntu "12.04 LTS".now my question is that if it is okay for me to use 12.04 to recover the grub menu(failed)....or should I use the appropriate Ubuntu version .In that case I'll have to download Ubuntu 13.04 all over again as I don't have a bootable image.what say?

---

### Post by RadicaX on 2014-04-23
Have you already backed up on your important files using the liveCD? I would think that it should work fine. I doubt it changed much, if at all. So you are probably safe, but feel free to await another answer from someone who may have tried it.

---

### Post by thomsebastin on 2014-04-23
thank you for your time.Wen I log in to the live environment all I see is the windows partition and no traces of the old Ubuntu partitions.Is this normal or should I be seeing the Ubuntu partitions as well?.Anyway I'm low on bandwidth at the moment,so I prefer waiting for an answer by someone who had been through the same situation as mine.It's been a week or so that I've installed windows and only now I am trying to bring back the boot menu.Hope the time period is not a problem as long as everything s contained in the hard disk.

---

### Post by pfeiffep on 2014-04-23
> **thomsebastin said:**
> thank you for your time.Wen I log in to the live environment all I see is the windows partition and no traces of the old Ubuntu partitions.Is this normal or should I be seeing the Ubuntu partitions as well?.Anyway I'm low on bandwidth at the moment,so I prefer waiting for an answer by someone who had been through the same situation as mine.It's been a week or so that I've installed windows and only now I am trying to bring back the boot menu.Hope the time period is not a problem as long as everything s contained in the hard disk.

I won't comment on the ppa installed version...I had _total success_ using the downloaded version and making a live dvd from the iso which is the recommended method.

---

### Post by thomsebastin on 2014-04-24
> **pfeiffep said:**
> I won't comment on the ppa installed version...I had _total success_ using the downloaded version and making a live dvd from the iso which is the recommended method.Doesn't the downloable have any dependency criteria??..if it s a "no"..then it's high time I download it.by the way y isn't this app there by default on live CD's???It's pretty damn useful n would make all our lives easier.

---

### Post by oldfred on 2014-04-24
You will not see Linux partitions from Windows.

If your Ubuntu install was in a logical partition, Windows has been known to re-write partition table without the Linux partition. Most have recovered it with testdisk.

If partitions are there for Boot-Repair to find grub, it works for just about everyone. But you can use the manual mount partition and install grub procedure.

If not sure use Boot-Repair to run the BootInfo report and post the link it gives you so we can review report.
       
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by thomsebastin on 2014-04-24
> **oldfred said:**
> You will not see Linux partitions from Windows.If your Ubuntu install was in a logical partition, Windows has been known to re-write partition table without the Linux partition. Most have recovered it with testdisk.If partitions are there for Boot-Repair to find grub, it works for just about everyone. But you can use the manual mount partition and install grub procedure.If not sure use Boot-Repair to run the BootInfo report and post the link it gives you so we can review report.       Post the link to the Create BootInfo report. Is part of Boot-Repair:[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)sounds promising....I already know that windows don't read ext partitions....will I be able to mount them(old Ubuntu partitions) using a live CD??..I need few of my codes from /var/www/* ....if I get it back I shall just install a fresh trusty on top of it.Anyway I'll try with boot repair once again n get back with the reports.

---

### Post by thomsebastin on 2014-04-27
> **oldfred said:**
> You will not see Linux partitions from Windows.

** If your Ubuntu install was in a logical partition, Windows has been known to re-write partition table without the Linux partition. Most have recovered it with testdisk.**

If partitions are there for Boot-Repair to find grub, it works for just about everyone. But you can use the manual mount partition and install grub procedure.

If not sure use Boot-Repair to run the BootInfo report and post the link it gives you so we can review report.
       
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I tried again and here is the bootinfo url. 
[http://paste.ubuntu.com/7344656/](http://paste.ubuntu.com/7344656/) 

The bolded part of your reply sounds like my problem.But I've done this a ton times and this is the first time i got messed up. Never expected this shock.:rolleyes:](*,)

---

### Post by thomsebastin on 2014-04-27
the HDD is 500GB actualy though it shows 300 n something GB now:(.

---

### Post by oldfred on 2014-04-27
You are only showing three NTFS partitions, no Linux nor swap.
And you show all three NTFS partitions with data and they take up the entire hard drive.

Did you have wubi installed which would have been inside a Windows install?

You may be able to see old partitions with testdisk, but recovering any Linux partitions if you have any  would probably delete data in NTFS partitions.

Do not understand how drive could change from 500 to 300GB. If so then Linux partitions may be in space not shown.
What does BIOS show drive size as. If BIOS says it is 300GB then systems will only think it is 300GB.
What does Disks or Disk Utility and then Smart Status show on status of drive.

       [URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
This shows info on hard drive. 

sudo hdparm -I /dev/sda

Mine shows model number of my 160GB drive as MAXTOR STM3[COLOR=#ff0000]160[/COLOR]812AS 
And hidden in model number is the size.
Similarly for my 640GB drive.
WDC WD[COLOR=#ff0000]640[/COLOR]0AACS-00G8B1

---

