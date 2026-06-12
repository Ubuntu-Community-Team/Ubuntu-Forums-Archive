---
title: "Can't boot up my computer"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by LxGalaxy18 on 2011-10-26
I have (had) Ubuntu and Windows 7 installed on my laptop (which is a 2 year old ASUS). Last night I wanted to remove the Ubuntu partition on my computer. I deleted (what i thought was the partitions I made) but now when i turn my computer on i get this...

error: no such partition.
grub rescue>

I followed another this [thread]("http://ubuntuforums.org/showthread.php?t=1359802") that seemed like someone had the exact problem as me but when i tried the solutions that everyone gave it never worked for me. I don't have a  live CD or usb for Ubuntu and I only have the Windows vista recovery that came with my laptop. 

My problem is that when i run this code:
grub> set root=(hd0,0) grub> makeactive grub> chainloader +1 grub> boot
it tells me "makeactive" is not a valid command. I also have a lot of school documents that I don't want to lose. Anyone have suggestions?

---

### Post by collisionystm on 2011-10-26
> **LxGalaxy18 said:**
> I have (had) Ubuntu and Windows 7 installed on my laptop (which is a 2 year old ASUS). Last night I wanted to remove the Ubuntu partition on my computer. I deleted (what i thought was the partitions I made) but now when i turn my computer on i get this...

error: no such partition.
grub rescue>

I followed another this [thread]("http://ubuntuforums.org/showthread.php?t=1359802") that seemed like someone had the exact problem as me but when i tried the solutions that everyone gave it never worked for me. I don't have a  live CD or usb for Ubuntu and I only have the Windows vista recovery that came with my laptop. 

My problem is that when i run this code:
grub> set root=(hd0,0) grub> makeactive grub> chainloader +1 grub> boot
it tells me "makeactive" is not a valid command. I also have a lot of school documents that I don't want to lose. Anyone have suggestions?

You need to grab your Windows 7 DVD and repair the MBR

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

[http://technet.microsoft.com/en-us/magazine/ee851681.aspx](http://technet.microsoft.com/en-us/magazine/ee851681.aspx)

Just google, Windows 7 remove grub repair MBR

---

### Post by LxGalaxy18 on 2011-10-26
> **collisionystm said:**
> You need to grab your Windows 7 DVD and repair the MBR

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

[http://technet.microsoft.com/en-us/magazine/ee851681.aspx](http://technet.microsoft.com/en-us/magazine/ee851681.aspx)

Just google, Windows 7 remove grub repair MBR

My Windows 7 CD is this though: Windows 7 Home Premium Upgrade Media.

I turned my computer on with the CD in the drive and it still brought me to the...
error: no such partition.
grub rescue>

Any suggestions?

---

### Post by collisionystm on 2011-10-26
> **LxGalaxy18 said:**
> My Windows 7 CD is this though: Windows 7 Home Premium Upgrade Media.

I turned my computer on with the CD in the drive and it still brought me to the...
error: no such partition.
grub rescue>

Any suggestions?

Shoot. You upgraded to 7?

Do you have access to another computer and a cd burner?

---

### Post by LxGalaxy18 on 2011-10-26
> **collisionystm said:**
> Shoot. You upgraded to 7?

Do you have access to another computer and a cd burner?

Ya I got my laptop the year that 7 came out.... I do have access to another computer but not a burner. I'm pretty sure i can download a free one off the internet thought right?

---

### Post by collisionystm on 2011-10-26
> **LxGalaxy18 said:**
> Ya I got my laptop the year that 7 came out.... I do have access to another computer but not a burner. I'm pretty sure i can download a free one off the internet thought right?

You can download the files you need to fix it, but you need a blank cd to put the files on.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You want that but it needs to go on a cd or thumb drive

---

### Post by LxGalaxy18 on 2011-10-26
> **collisionystm said:**
> You can download the files you need to fix it, but you need a blank cd to put the files on.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You want that but it needs to go on a cd or thumb drive

I have blank CD's laying around the house and some empty USB's too. Do i just need to leave them in when I boot my computer up?

---

### Post by collisionystm on 2011-10-26
> **LxGalaxy18 said:**
> I have blank CD's laying around the house and some empty USB's too. Do i just need to leave them in when I boot my computer up?

I assume your other computer is Windows?

Grab a usb key with at least 512 mb of space.

Download this

[http://download.berlios.de/rescatux/rescatux_cdrom_usb_hybrid_i386_486-amd64_0.29.iso](http://download.berlios.de/rescatux/rescatux_cdrom_usb_hybrid_i386_486-amd64_0.29.iso)

Download this

[http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)

Install the LinuxLiveUsb program

Plug in your USB drive

Run the Linux Live Usb program

Choose your USB drive at the top of the program

Below that, click on ISO/IMG/ZIP

Browse to the cd you downloaded ( first thing you downloaded ) it was the rescatux file that ended in .iso

Choose the file.

Leave your persistence set to 0mb

Check  the box to format the usb key

Uncheck other boxes

Click the lightning bolt to put the image on it


When finished, plug the usb into your laptop

Reboot your computer and keep tapping the ESC key on your keyboard

Choose to boot from the USB device

Follow instructions

Use this video for reference

[http://www.youtube.com/watch?v=SPpPgnfTdE0](http://www.youtube.com/watch?v=SPpPgnfTdE0)

---

### Post by LxGalaxy18 on 2011-10-26
> **collisionystm said:**
> I assume your other computer is Windows?

Grab a usb key with at least 512 mb of space.

Download this

[http://download.berlios.de/rescatux/rescatux_cdrom_usb_hybrid_i386_486-amd64_0.29.iso](http://download.berlios.de/rescatux/rescatux_cdrom_usb_hybrid_i386_486-amd64_0.29.iso)

Download this

[http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)

Install the LinuxLiveUsb program

Plug in your USB drive

Run the Linux Live Usb program

Choose your USB drive at the top of the program

Below that, click on ISO/IMG/ZIP

Browse to the cd you downloaded ( first thing you downloaded ) it was the rescatux file that ended in .iso

Choose the file.

Leave your persistence set to 0mb

Check  the box to format the usb key

Uncheck other boxes

Click the lightning bolt to put the image on it


When finished, plug the usb into your laptop

Reboot your computer and keep tapping the ESC key on your keyboard

Choose to boot from the USB device

Follow instructions

Use this video for reference

[http://www.youtube.com/watch?v=SPpPgnfTdE0](http://www.youtube.com/watch?v=SPpPgnfTdE0)

Thanks so much! I can finally get through that stage :) but now i have another problem.... Windows fails to start and it asks for me to insert my Windows installation disc and restart my computer. Well I have put my Windows vista CD in but it doesn't read it. Any idea how?

---

### Post by collisionystm on 2011-10-27
> **LxGalaxy18 said:**
> Thanks so much! I can finally get through that stage :) but now i have another problem.... Windows fails to start and it asks for me to insert my Windows installation disc and restart my computer. Well I have put my Windows vista CD in but it doesn't read it. Any idea how?

Yes put in the CD

reboot your computer

keep tapping the ESC key

choose to boot from CD

---

