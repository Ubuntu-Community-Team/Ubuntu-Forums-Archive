---
title: "Problem with installation"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by tallpaul66 on 2008-09-03
My computer runs XP. I have 2 IDE hard drives, 1 RAID hard drive, and one external USB hard drive. I used Partition Magic to create a Linux partition on my C: drive so I could install Ubuntu into it. Now I am unable to boot into Windows. When I run the Ubuntu installation from the CD I get to the point where it says Prepare disk space. The Guided option is selected and there are two bars, one which says /dev/sdd1/25%(175.7 GB) and it is orange. The other bar says Ubuntu 8.04.1 75% (523.0 GB) and it is gray. I believe my C: drive is only 500 GB so those numbers don't look right to me. When I click on forward I get a pop up that asks about writing disk information and I click on continue then get another pop up that says Too small size. I do not want Ubuntu to use my entire disk so I tried the manual option but when I click on forward it just comes back to the partition menu after a few seconds. Is there something I missed or what?

---

### Post by oilchangeguy on 2008-09-03
> **tallpaul66 said:**
> My computer runs XP. I have 2 IDE hard drives, 1 RAID hard drive, and one external USB hard drive. I used Partition Magic to create a Linux partition on my C: drive so I could install Ubuntu into it. Now I am unable to boot into Windows. When I run the Ubuntu installation from the CD I get to the point where it says Prepare disk space. The Guided option is selected and there are two bars, one which says /dev/sdd1/25%(175.7 GB) and it is orange. The other bar says Ubuntu 8.04.1 75% (523.0 GB) and it is gray. I believe my C: drive is only 500 GB so those numbers don't look right to me. When I click on forward I get a pop up that asks about writing disk information and I click on continue then get another pop up that says Too small size. I do not want Ubuntu to use my entire disk so I tried the manual option but when I click on forward it just comes back to the partition menu after a few seconds. Is there something I missed or what?

i hope you backed up your data before you did this. and you don't need to use something like partition magic. ubuntu does a fine job of creating it's own partitions. you'll probably end up having to take the c: drive out of this computer, install it as a slave in another computer, and see if your data can be recovered. reinstall windows, then do some reading on how to properly set up a dual boot computer.

---

### Post by Mike.B on 2008-09-03
I just installed kubuntu, and also used Paragon. I'm assuming that both installs are the same.
I had pre prepared 2 partitions on my drive 1 @ 5gb ext3 and 1 @ 1gb swap,
When I installed using install without making changes to your computer, it installed, but would not let me boot, and went thru to XP.
I then installed again using the option underneath (sorry cannot remember what it was). This took no notice of the pre formatted partitions but allowed me to pick which partitions to install to.
Voila it's working well.

---

