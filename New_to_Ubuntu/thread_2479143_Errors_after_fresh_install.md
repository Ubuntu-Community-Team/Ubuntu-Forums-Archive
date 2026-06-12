---
title: "Errors after fresh install"
date: 2022-09-15
forum: New to Ubuntu
---

### Post by diidii2 on 2022-09-15
Hello,

I'm a new to Unix and Ubuntu [COLOR=#333333][FONT=&amp]and not a geek, but a pensioner and sometimes a little slow on the uptake  [/FONT][/COLOR][IMG]https://forums.debian.net/images/smilies/icon_biggrin.gif[/IMG]

[COLOR=#333333][FONT=&amp]I actually started out with using Debian but I failed miserably trying to setup RAID1, but thanks to the following guide I managed it with bravour
[/FONT][/COLOR]
[https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices](https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices)

Now I get the following errors when I check the system log.
 
```
sudo journalctl -b -p 3
Sep 15 14:07:45 macmini kernel: DMAR-IR: [Firmware Bug]: ioapic 2 has no mapping iommu, interrupt remapping will be disabled
Sep 15 14:07:45 macmini kernel: ACPI Error: Needed type [Reference], found [Integer] 000000003b3df95e (20210730/exresop-66)
Sep 15 14:07:45 macmini kernel: ACPI Error: AE_AML_OPERAND_TYPE, While resolving operands for [Store] (20210730/dswexec-431)
Sep 15 14:07:45 macmini kernel: ACPI Error: Aborting method \_PR.CPU0._PDC due to previous error (AE_AML_OPERAND_TYPE) (20210730/psparse-529)
Sep 15 14:07:45 macmini kernel: mtd device must be supplied (device name is empty)
Sep 15 14:07:46 macmini kernel: mtd device must be supplied (device name is empty)
Sep 15 14:07:46 macmini kernel: mtd device must be supplied (device name is empty)
```

Unfortunately I'm unsure if I can modify GRUB (GRUB_CMDLINE_LINUX_DEFAULT="") on the RAID1 as I did on Debian 11 with a non raid configuration and simply edit **/etc/default/grub** and then do **update-grub**.

[COLOR=#333333][FONT=&amp]Many thanks in advance for any hint and all have a nice day :-)[/FONT][/COLOR]

---

### Post by ne29914 on 2022-09-15
The "mtd" errors are a bug in 22.04.
Annoying, but not catastrophic. Ignore it, hopefully an update will come out soon.

---

### Post by diidii2 on 2022-09-16
Thanks for that note about the bug!

I managed to get rid of the first error by adding the following to **[FONT=&amp]/etc/default/grub[/FONT]**

```
[COLOR=#000000][FONT=&amp]GRUB_CMDLINE_LINUX_DEFAULT="**intremap=off**"[/FONT][/COLOR]
```

Then I updated GRUB 3x as I don't know if the first command would update both drives in my RAID1

```
[B][FONT=&amp]update-grub
[/FONT][/B][B][FONT=&amp]update-grub /dev/sda
[/FONT][/B]**[FONT=&amp]update-grub /dev/sdb[/FONT]**
```

And successfully rebooted :-)

---

### Post by ajgreeny on 2022-09-16
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

