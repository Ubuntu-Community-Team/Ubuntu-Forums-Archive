---
title: "Problems with Grub"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by zeuso0 on 2011-10-07
EQUIPMENT: Acer AspireONE D257 * SYSTEM:win7 starter& ubuntu netbook remix 10.10 * PROBLEM: ran out of battery, then after plugin power supply and turn it back, in boot menu there appeared an additional OS name when asked for choosing operating system -Vista, however I never had that. Out of curiosity, I clicked on that then it got me in to deep grub rescue limbo!!
ERROR MESSAGE: error:no such partition.grub rescue>
CURRENT CONDITION: no cd/dvd rom, no floppy disk
WHAT WAS FOUND::( most important issue!: the laptop just could NOT get reboot from pen drive/flash drive !:( More detailed outputs with commands:  ls => (hd0),(hd0,msdos5),(hd0,msdos3),(hd0,msdos2),(hd0,msdos1) *  set => prefix=(hd0,msdos6)/boot/grub , root=hd0,msdos6 * 'ls' any one of these disks will give "error:unknown filesystem“ * set prefix and root to them was NO help * tried to reboot from usb (version10.10 and 11.04 both tried,failed,but verified on windows that they both worked, rebootable)I also verified that in BIOS usb boot sequence was set to number 1), reboot and again and again, it keeps going to the same grub-rescue-prompt! So I can't reboot from a thumb drive!!! what is going on, any god please help me!!!

---

### Post by amjjawad on 2011-10-07
> **zeuso0 said:**
> EQUIPMENT: Acer AspireONE D257 * SYSTEM:win7 starter& ubuntu netbook remix 10.10 * PROBLEM: ran out of battery, then after plugin power supply and turn it back, in boot menu there appeared an additional OS name when asked for choosing operating system -Vista, however I never had that. Out of curiosity, I clicked on that then it got me in to deep grub rescue limbo!!
ERROR MESSAGE: error:no such partition.grub rescue>
CURRENT CONDITION: no cd/dvd rom, no floppy disk
WHAT WAS FOUND::( most important issue!: the laptop just could NOT get reboot from pen drive/flash drive !:( More detailed outputs with commands:  ls => (hd0),(hd0,msdos5),(hd0,msdos3),(hd0,msdos2),(hd0,msdos1) *  set => prefix=(hd0,msdos6)/boot/grub , root=hd0,msdos6 * 'ls' any one of these disks will give "error:unknown filesystem“ * set prefix and root to them was NO help * tried to reboot from usb (version10.10 and 11.04 both tried,failed,but verified on windows that they both worked, rebootable)I also verified that in BIOS usb boot sequence was set to number 1), reboot and again and again, it keeps going to the same grub-rescue-prompt! So I can't reboot from a thumb drive!!! what is going on, any god please help me!!!

Hi,

I'm having HARD time reading your post ... would you please edit it and arrange it better so everyone can read it clearly? 

Thanks :)

---

### Post by zeuso0 on 2011-10-07
EQUIPMENT: Acer AspireONE D257 
SYSTEM:win7 starter& ubuntu netbook  remix 10.10 
PROBLEM: ran out of battery, then after plugin power  supply and turn it back, 'Vista' showed up in start menu ?!! while I never  had that installed!. Out of curiosity, I clicked on that then it got me in to deep  grub rescue limbo!!
ERROR MESSAGE: error:no such partition.grub rescue>
CURRENT CONDITION: no cd/dvd rom, no floppy disk
WHAT WAS FOUND::sad: most important issue!: the laptop just could NOT get reboot from pen drive/flash drive !:sad:
 More detailed outputs with commands:  ls =>  (hd0),(hd0,msdos5),(hd0,msdos3),(hd0,msdos2),(hd0,  msdos1) 
 set =>  prefix=(hd0,msdos6)/boot/grub , root=hd0,msdos6 .
 'ls' any one of these  disks will give "error:unknown filesystem&#8220; .
 set prefix and root to  them was NO help .
 tried to reboot from usb (version10.10 and 11.04 both  tried,failed,but verified on windows that they both worked,  rebootable)I also verified that in BIOS usb boot sequence was set to  number 1), reboot again and again, it keeps going to the same  grub-rescue-prompt! So I can't reboot from a thumb drive!!! so what is  going on, any god please help me!!!

---

### Post by zeuso0 on 2011-10-07
somehow my texts condensed into one block, sorry. hope you can read this now.

---

### Post by zeuso0 on 2011-10-07
EQUIPMENT: Acer AspireONE D257 * SYSTEM:win7 starter& ubuntu netbook remix 10.10 * PROBLEM: ran out of battery, then after plugin power supply and turn it back, in boot menu there appeared an additional OS name when asked for choosing operating system -Vista, however I never had that. Out of curiosity, I clicked on that then it got me in to deep grub rescue limbo!!
ERROR MESSAGE: error:no such partition.grub rescue>
CURRENT CONDITION: no cd/dvd rom, no floppy disk
WHAT WAS FOUND::( most important issue!: the laptop just could NOT get reboot from pen drive/flash drive !:( More detailed outputs with commands:  ls => (hd0),(hd0,msdos5),(hd0,msdos3),(hd0,msdos2),(hd0,msdos1) *  set => prefix=(hd0,msdos6)/boot/grub , root=hd0,msdos6 * 'ls' any one of these disks will give "error:unknown filesystem“ * set prefix and root to them was NO help * tried to reboot from usb (version10.10 and 11.04 both tried,failed,but verified on windows that they both worked, rebootable)I also verified that in BIOS usb boot sequence was set to number 1), reboot and again and again, it keeps going to the same grub-rescue-prompt! So I can't reboot from a thumb drive!!! what is going on, any god please help me!!!

---

### Post by amjjawad on 2011-10-07
Never mind :)

> **zeuso0 said:**
> 

EQUIPMENT: Acer AspireONE D257 

SYSTEM:win7 starter & ubuntu netbook  remix 10.10 

PROBLEM: ran out of battery, then after plugin power  supply and turn it back, 'Vista' showed up in start menu ?!! while I never  had that installed!. Out of curiosity, I clicked on that then it got me in to deep  grub rescue limbo!!

```
ERROR MESSAGE: error:no such partition.grub rescue>

```

CURRENT CONDITION: no cd/dvd rom, no floppy disk

WHAT WAS FOUND::sad: most important issue!: the laptop just could NOT get reboot from pen drive/flash drive !:sad:
 
More detailed outputs with commands:  

ls =>  (hd0),(hd0,msdos5),(hd0,msdos3),(hd0,msdos2),(hd0,  msdos1) 
 set =>  prefix=(hd0,msdos6)/boot/grub , root=hd0,msdos6 .
 
'ls' any one of these  disks will give "error:unknown filesystem“ .
 set prefix and root to  them was NO help .


 tried to reboot from usb (version10.10 and 11.04 both  tried,failed,but verified on windows that they both worked,  rebootable) I also verified that in BIOS usb boot sequence was set to  number 1), reboot again and again, it keeps going to the same  grub-rescue-prompt! So I can't reboot from a thumb drive!!! so what is  going on, any god please help me!!!

There are many solved threads to fix GRUB Rescue:
One of these: [http://ubuntuforums.org/showthread.php?t=1359802](http://ubuntuforums.org/showthread.php?t=1359802)
However, it might not be the same case with you.

If your machine can't boot from USB Drive, you need to double check your BIOS, try different USB Drive or plug that in different ports and most importantly, make sure to use the correct tool to create LiveUSB.

I recommend [UNetbootin]("http://unetbootin.sourceforge.net/").

I also assume you have checked MD5SUM before creating the LiveUSB ;)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by mörgæs on 2011-10-07
Changed the title to a less emotional one.

Also, please stop making more threads on the same subject.

---

