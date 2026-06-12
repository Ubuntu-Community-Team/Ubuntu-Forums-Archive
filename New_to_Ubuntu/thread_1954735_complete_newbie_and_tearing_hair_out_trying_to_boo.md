---
title: "complete newbie and tearing hair out trying to boot up system"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by jian91 on 2012-04-08
Hi,
I just got a new laptop (meenee MNW737- Dual Core N570) which only has ubuntu installed, no windows or mac. the laptop also doesn't have a CD drive

it's been working fine until now, when it didn't shut down properly because the battery ran out and when i've tried to turn it on again it simply won't start/ boot up


First menu it comes up with:
       GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-32-generic 
Ubuntu, with Linux 2.6.35-32-generic (recovery mode)
Ubuntu, with Linux 2.6.35-32-generic
Ubuntu, with Linux 2.6.35-32-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)


then if i click the first option:
[lots of numbers]
killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootary.


and then if i click the second option with recovery mode:
[numbers]
Killed
Begin: Running /scripts/local-bottom...done.
done.
Begin: Running /scripts/init-bottom...mount: mounting /dev on /root/dev failed: No such file or directory.
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on/root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootary


any ideas? i've tried rebooting ubuntu from a USB drive but it won't even let me past these screens to do so

---

### Post by Gone fishing on 2012-04-08
The errors are saying that the boot file system can't be found this is obviously not good.

I'd boot up on a live cd a check the file system using fsck

[http://ubuntuforums.org/showthread.php?t=1518426](http://ubuntuforums.org/showthread.php?t=1518426)

[http://linuxpoison.blogspot.co.uk/2009/04/how-to-checkrepair-fsck-filesystem.html](http://linuxpoison.blogspot.co.uk/2009/04/how-to-checkrepair-fsck-filesystem.html)

---

### Post by jian91 on 2012-04-08
hey,
thanks for getting back so quick, i've tried the fsck thing and it doesn't seem to have done anything. do you know if there is any way to boot up on a USB drive? i don't have a CD drive at all but i do have ubuntu ready on a USB, i just don't know how to boot it up because the bootup screen is just giving me the aforementioned text.

---

### Post by Dave_L on 2012-04-08
You probably have to change a BIOS setting to boot from a USB drive.

Do you know how to enter the BIOS during boot? Typically it involves pressing a key such as F1 or Del during boot, but it varies among different computers.

---

### Post by roelforg on 2012-04-08
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
The section "manual usb"

Maybe someone could write a script to automate this?

---

### Post by Gone fishing on 2012-04-09
Ubuntu comes with a utility called startup disk creator that will make usb start up disks.

Run the utility and follow the instructions, then make sure the computer's BIOS is set to boot from a usb disk.

---

### Post by Swagman on 2012-04-09
Is there anything on the hard drive you need to keep ?

If not... You could re-install (as a last resort). 

Whilst switched off insert the boot Usb stick.. Switch on and press del to go into Bios and change your boot priority.

Usually an F key will do this though so you don't have to go back into bios to change it back to hard drive.

I'd try the F key option first..  You need to press one (an F'key) immediately after switching on.

---

### Post by ravinfy on 2012-04-09
Just elaborating on "Gone Fishing"s plan: 

Step 1: Download the Ubuntu ISO file from [http://ftp-mirror.internap.com/pub/ubuntu-releases//precise/]("http://ftp-mirror.internap.com/pub/ubuntu-releases//precise/")

Step 2: Create a 'bootable' Pen drive using another functional Ubuntu or Windows machine. 
On Ubuntu, you will be able to use a program called "Startup disk creator"
On Windows, I found a utility called UNetbootin very helpful. Download it here: [unetbootin.sourceforge.net/]("unetbootin.sourceforge.net/")

Step 3: restart your machine and change your bootup sequence in BIOS. Hitting one of F1 thru F3 keys helped me do this. You want to boot with USB drive first. 

Step 4: The Ubuntu installation should initiate on its own when the system reboots. You will now be allowed to either do a clean install of Ubuntu or retain your documents and fix the broken parts of your OS. 

Hope this helps.

---

### Post by westcoast01 on 2012-04-09
ravinfy has some great advice, hope it works. Please let us know if you get your problem resolved. Best of luck.

---

### Post by Swagman on 2012-04-12
Did you solve this issue ?

---

