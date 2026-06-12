---
title: "Disk boot failure !"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by WILL_CHAN on 2008-10-27
- I'm using Ubuntu 8.04 LTS.
- Yesterday, everything was normal.
- Today, when I turn on my computer, it hung on the boot screen for about 10s and it showed me this message :
"DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER"
Then I tried to use my Ubuntu Disk to boot it but still, it showed error message that Disk boot failure...
I don't know what really happened ? Anyone could help me out ? Is that problem with my hard drive or something else ?

---

### Post by logos34 on 2008-10-27
check your hdd settings in the Bios (should be set for 'auto' detect).  To boot from the ubuntu cd make sure the cd/dvd drive is set first in the device boot order

---

### Post by perlluver on 2008-10-27
Does your computer have a floppy drive?  If so is there a floppy in there?

---

### Post by scorchgeek on 2008-10-27
It's possible that your hard drive could have become corrupted, but get booted from the disk first before trying to determine if something got messed up.

Did it hang on the GRUB menu or the Ubuntu boot screen?

---

### Post by P13808 on 2008-10-27
Set the BIOS to boot from CD first, then try booting from the CD.  If that fails, try putting the hard drive in a different computer.  Then see if it works.

---

### Post by WILL_CHAN on 2008-10-27
First, thanks all guys !
- If I don't insert the Ubuntu CD( version 6.10 ), it will hang on the XP screen boot srceen for a while( 10 sec ) then gave me the message 
"DISK BOOT FAILURE.....". Since I used Windows XP before.
- If I inserted the CD and let me automatic chose the option "Start or install Ubuntu from the menu" it gave me :
> 
BusyBox v1.1.3( Debian  1:1.1.3-3ubuntu3 ) Built-in shell( ash )
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off 
(initramfs)[   99.486576] ata1 : COMRESET failed( device not ready )
[ 104.956848] ata1 : COMRES....
[ 110.427157] ata1 : reset failed, giving up

then I hit the enter key and "reboot"
(initramsfs)reboot
It go back to the screen again.
- If I chose the option "Boot from disk hard disk"
It gave me :
> 
Booting from local disk....
isolinux : Disk error 01, AX = 0201, drive 80
Boot failed : press a key to retry...

---

### Post by WILL_CHAN on 2008-10-27
Hi P13808 :
> Set the BIOS to boot from CD first, then try booting from the CD. If that fails, try putting the hard drive in a different computer. Then see if it works.
I'm really newbie to Linux, and I don't really know how to set BIOS to boot from CD :( ? Could you show me step by step ? Thanks a lot ! Sorry for my stupid question !
Hi perlluver :
> Does your computer have a floppy drive? If so is there a floppy in there?
2 Hours Ago 07:14 PM
My computer doesn't have floppy disk :( !
Hi logos34 :
> check your hdd settings in the Bios (should be set for 'auto' detect). To boot from the ubuntu cd make sure the cd/dvd drive is set first in the device boot order
One more time, sorry for my stupid question guys, but I haven't done this stuff before so I have no idea how to do it :( ! Could you show me step by step ? Thanks a lot !
Hi Scorchgeek :
> It's possible that your hard drive could have become corrupted, but get booted from the disk first before trying to determine if something got messed up.

Did it hang on the GRUB menu or the Ubuntu boot screen? 
It hung from the XP Boot Screen( the blue one ) since I used XP before, and I just format all my hard drive and install Ubuntu. So my computer now is only Ubuntu. It didn't even go to the Ubuntu screen( the scroll-bar have a little bar run ).

-> In the worst case, if my hard drive is broken, what should I do ? I already have all my data saved in the external hard drive. So I don't mind about data, just wasting time to reinstall everything :( !

---

### Post by WILL_CHAN on 2008-10-28
Sorry guys, I'm a little rush since I have 2 project in C++ due next week ! Could anyone help me out ? Is it possible to fix it or in the worst case should I buy a new PC ? Could anyone give me an advice ?

---

### Post by WILL_CHAN on 2008-10-28
Just figure out how to set the priority for CD driver. But the problem is still the same ! I tried to boot from the Ubuntu CD.
It gave me :
> 
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh : can't access tty; job control turned off
(initramfs)[   99.766296] ata1 : COMRESET failed ( device not ready )
[ 105.236788] ata1 : COMRESET failed( device not ready )
[ 110.707281] ata1 : COMRESET failed( device not ready )
[ 110.707317] ata1 : reset failed, giving up


---

