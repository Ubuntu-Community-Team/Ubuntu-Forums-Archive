---
title: "grub2, problem with Win7 hibernation"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by kunver400 on 2012-07-11
I am having win7 hibernation problem, with the grub boot loader

here is all about me and mine

2 hard disk

1st windows 7 160 gb

2nd grub ubuntu 40 gb


,when i go to system  setup and change the boot order  160gb HDD, and then 40 gb HDD

then window hibernates (works fine)
but ubuntu never boots!

can i use this to add ubuntu option in win7 boot loader!!

will it work as, i have ubuntu on anethor hdd!:(

---

### Post by kunver400 on 2012-07-11
IT didn't worked opening the GRUB option from windows 7 boot loader, returns nothing and brings me back to the same boot menu!! :(:(:confused:

any solutions please help!

---

### Post by wombathuffer on 2012-07-11
I dont know anything about the hypernation-problem you are talking about - i guess it might be a BIOS-ACPI-thing.

You cannot add the Ubuntu bootline to the Microsoft bootloader, but you can boot grub from the bootloader and then start Ubuntu from grub, as described.

---

### Post by oldos2er on 2012-07-11
Posts moved to their own thread.

---

### Post by kunver400 on 2012-07-11
> **wombathuffer said:**
> I dont know anything about the hypernation-problem you are talking about - i guess it might be a BIOS-ACPI-thing.

You cannot add the Ubuntu bootline to the Microsoft bootloader, but you can boot grub from the bootloader and then start Ubuntu from grub, as described.

yeah! buddy you are right!

yes i want to boot grub from the windows bootloader and then start Ubuntu from grub! :)

but my win7 and ubuntu are in different hard drives!

and the above method fails!
 

And the hibernation problem!:: IS THIS

when i hibernate windows 7 ,(booted from GRUB)
it returns back to the logon page!!
but everything works fine when i boot it with the microsoft bootloader !(i switch between bootloaders by changing the hardisk boot priority)!:guitar:

---

