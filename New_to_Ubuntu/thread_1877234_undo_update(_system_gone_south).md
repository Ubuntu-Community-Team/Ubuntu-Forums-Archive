---
title: "undo update?( system gone south)"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by pierreyy on 2011-11-07
hey guys, 
 last night i updated my ubuntu 11.10 and everything went south from there...

i am dual booting win7 and ubuntu 11.10 as i log into ubuntu this morning it says that ubuntu cannot automatically mount the file systems and that i should do it manually ( something about helper could not mount volume... error code 1 . i thought ill google it... which i did ( and with no avail) i understood that i need to manually mount the file systems everytime ( INCONVENIENT) i had my system in a way that when i log into ubuntu all partitions are mounted automatically, this is because i have ( well had) a launcher icon on the desktop that directs me to the contents of my windows desktop( i can no longer create this kind of icon for some reason) is there a way i can get it back?


 on another note the disk utility has detected 105 bad sectors on my laptops' HDD ( which is 5 months old) should there be such errors? can i repair this, if yes how and if no is there a workaround to stop this from expanding into an even bigger problem?


i have a toshiba satellite A665 core i5 4 gb ram and 500gb hard disk running a dual boot win7 64-bit and Ubuntu 11.10 32-bit 


thanks in advance you guys i really appreciate the help( and sry about the length of the post)

---

### Post by philinux on 2011-11-07
It looks like you might have a duff hard dri ve. If its under warranty I would contact the manufacturer or supplier.

---

### Post by pierreyy on 2011-11-07
thanks for the quick reply!, can you explain to me what exactly that is?( i know google exists i tried it but i didnt get a clear answer)

---

### Post by Mark Phelps on 2011-11-07
Having Windows filesystems, especially NTFS, automounted during login is what leads to this kind of problem -- especially if you're making the mistake of making changes to files or directories in the NTFS partitions from inside Ubuntu.

What you can do to get around that temporarily is boot into a command line and remove the /etc/fstab file.  That way, the partitions won't get mounted automatically, and once into the desktop, you can open a terminal and mount them manually -- seeing what error messages are being generated in the process.

---

### Post by pierreyy on 2011-11-07
i think i just killed my laptop 
i deleted a a 4 gb partition on the hdd, aparently that was the partition that contains the boot loader now it only boots into grub rescue.... i tried booting a knoppix live cd  but that also did not boot correctly and now is stuck 
and says"

line 546: /sbin/udevd: Input/output error 

what am i supposed to do now? please help me!

---

### Post by pierreyy on 2011-11-07
> **Mark Phelps said:**
> Having Windows filesystems, especially NTFS, automounted during login is what leads to this kind of problem -- especially if you're making the mistake of making changes to files or directories in the NTFS partitions from inside Ubuntu.

What you can do to get around that temporarily is boot into a command line and remove the /etc/fstab file.  That way, the partitions won't get mounted automatically, and once into the desktop, you can open a terminal and mount them manually -- seeing what error messages are being generated in the process.

i did not know that...now  i learned alot of things....including that regret is not a nice(nor useful) feeling... thank you though i really appreciate it.

---

### Post by utnubuuser on 2011-11-07
You might still be able to rescue your system with a liveCD and BootRepair.

There's a tutorial/how-to here:[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair](http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair)

You can also try to boot your OS manually, though if you've deleted your boot folder, that's going to be difficult.

UbuntuCommunityDocumentation has good help for booting from grub rescue prompt:
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting]("https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting")

And good help here for booting from grub> prompt if you can get to a normal grub> prompt from the grub-resue> prompt.  [http://sazeit.com/articles/boot-ubuntu-from-grub-prompt]("http://sazeit.com/articles/boot-ubuntu-from-grub-prompt")

Remember, you can use the ls command as well as TAB completion to help you find the information necessary to boot manually.

---

### Post by pierreyy on 2011-11-07
> **utnubuuser said:**
> You might still be able to rescue your system with a liveCD and BootRepair.

There's a tutorial/how-to here:[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair](http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair)

You can also try to boot your OS manually, though if you've deleted your boot folder, that's going to be difficult.

UbuntuCommunityDocumentation has good help for booting from grub rescue prompt:
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting]("https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting")

And good help here for booting from grub> prompt if you can get to a normal grub> prompt from the grub-resue> prompt.  [http://sazeit.com/articles/boot-ubuntu-from-grub-prompt]("http://sazeit.com/articles/boot-ubuntu-from-grub-prompt")

Remember, you can use the ls command as well as TAB completion to help you find the information necessary to boot manually.
 thank you very much!! the ls option replies with HD0 (hdo,msdos7) (hd0,msdos6) al the way to (hd0, msdos1)  but the tab button doesnot result in any activity... again thank you very very much!

---

### Post by pierreyy on 2011-11-07
im in desperate need of help guys please! i dunno what to do

---

### Post by wildmanne39 on 2011-11-07
Hi, I am sorry but this > Input/output error pretty much means that the drive has failed at least where those files are located and that is why it can not be read.
Thank you

---

### Post by pierreyy on 2011-11-07
ALREADY? the laptop is 5 months old! i guess im gunna get it replaced once i finish with the hassle im in now...  after the whole night(yes i havent slept) googling and such i gave up  took a linux cd i could find and installed Mageia( a mandriva fork and it was the cd that was in the best shape) i figured that the bootloader for that distro will read both windows and my ubuntu.... the good news is that my laptop boots now the bad new is that i cant access ubuntu ( bootloader error ironically enough) though i can still view my   files that are on ubuntu from mageia so i can recover them and i can go into windows.... so here comes my question:


can i convert the bootloader to run from ubuntu not magiea?
can i reinstall ubuntu  to replace my old ubuntu+mageia?
what is the best way to backup and preserve your settings and programs?
should i replace the hdd with an ssd?


 thanks in advance.

---

