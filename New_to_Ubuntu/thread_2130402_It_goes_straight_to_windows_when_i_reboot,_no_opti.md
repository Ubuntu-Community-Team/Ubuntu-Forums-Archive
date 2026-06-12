---
title: "It goes straight to windows when i reboot, no option to choose ubunto."
date: 2013-03-29
forum: New to Ubuntu
---

### Post by Baluba on 2013-03-29
Hey!

I'm a long time windows user, but a complete newbie to linux.

Now, for the question at hand.

I have two hdds, one wd 160gb and one samsung 250gb.

I've installed windows 7 on the wd 160gb (some time ago)

and I've installed ubuntu 12.10 on a 25gb partition on the samsung hdd (just recently)

I put the boot loader on the samsung hdd (not in a partition, but the hdd itself)

the installation process in itself went smoothly.

Now the problem is that i get no option to choose to load ubuntu instead of windows, it simply just goes straight to loading windows.

I think that i should have put the boot loader on the same hdd as windows is installed on( the wd hdd), then i would have gotten an option to choose wich os to load, but thats the problem, i actually dont know.

Am i right, or is it something else i havent done that i should have done?

Patiently waiting (but hopefully not for too long) Baluba.

---

### Post by JLeon85 on 2013-03-29
Have you gone into your BIOS settings and made sure it's booting from the Samsung HD first?

---

### Post by Mark Phelps on 2013-03-29
My own preference, when you have two physical drives with a different OS on each is to install GRUB on the Ubuntu drive.  That avoids the risk of corrupting anything on the Windows drive.

Change your BIOS to boot from the Ubuntu drive.

If you don't see a GRUB menu offering a choice of Ubuntu or Windows, then open a terminal and enter "sudo update-grub".  That will generate a new GRUB config file and should add an entry for Windows.

When you reboot, you should see a GRUB menu list which contains both Ubuntu entries and a Window loader entry.

---

### Post by Baluba on 2013-03-30
Thanks to the boths of you, just had to change boot priority on my two hdds :)

Thanks for the help :)

---

