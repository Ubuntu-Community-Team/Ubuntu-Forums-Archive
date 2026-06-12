---
title: "Rights on a USB stick"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by thebender on 2008-07-29
Hi! 

I followed this tutorial to install ubuntu from a usb stick: [http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)

if i now boot from usb it just says "missing operation system" ... 

i checked the rights of the files on the usb stick and just i have right to read or write on the stick. 

i am the owner of the files but the group is set to "root". is that normal??

i tried to change the rights with chmod and the owner with chown.. doesnt work. the terminal gives me an error that i dont have a permission and if i try it in ubuntus gui the right-field just popps back to "---".


I am pretty new to linux and this doesnt make sense to me. 

Shouldnt everybody has access to the files and folders on the usb stick? :(


please help. Its urgent!
Thanks a lot!!

---

### Post by Pro-reason on 2008-07-29
I'm not familiar with what you are trying to do, but I can comment on changing permissions.

If *chmod* fails due to you not having permission to alter the files, most of the time it is because you need to do *sudo chmod*.  Similarly, to use the GUI to work with files for which you do not have permissions, you need to start the GUI with root privileges.  You can do this with commands such as *gksudo nautilus*, *gksudo thunar*, *kdesudo dolphin* or *kdesudo konqueror*, depending on your desktop environment.

---

### Post by hansdown on 2008-07-29
Hi thebender. Your tutorial says...  On the root directory of your USB device, create a folder “install”
Copy the installer kernel and the initramdisk into this folder (Download source below.You need the files “vmlinux” and “initrd.gz”).

Download source for the installer kernel and initramdisk

For AMD64 Download from here
For i386 Download from here

You need to download the files “vmlinux” and “initrd.gz

---

### Post by thebender on 2008-07-30
Hi!

At first thanks for the replies!

After spending 2 hours trying to get the usb stick working with the tutorial i followed a hint of "Bob" who commented on the tutorial and i used UNetbootin. ( [http://sourceforge.net/project/showfiles.php?group_id=222386](http://sourceforge.net/project/showfiles.php?group_id=222386) ) 

It was so much easier. And the most important thing: it worked!

To the permissions: 

yeah... I tried to chmod or chown the files and folders as root in the command line. didn't work either. 

I've checked the files which UNetbootin put on my stick. They have the very same permissions like the files i put on. So i think i mad a mistake when i followed the tutorial ... but i really dont know where. 


Nevermind. I was able to set up the Laptop with Ubuntu ... 

Thanks for your help!
Dennis

---

