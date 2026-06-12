---
title: "Puppy in Boot Menu"
date: 2008-10-24
forum: Other OS Talk
---

### Post by iampriteshdesai on 2008-10-24
I have installed Puppy (frugal install) by booting in with live cd. It copied files succesfully and when I restarted I couldn't get any option to boot in to Puppy Linux. I have Vista and Ubuntu in boot option.
I am a newbie.
Thanks!

---

### Post by alan34 on 2008-10-24
Hi I have just installed Puppy on my pc and at the end of the install it said to edit the Grub bootloader. 
So if you are using Grub to boot (it is all I know about)

In your Ubuntu install edit as sudo

/boot/grub/menu.lst

at the bottom add something like this

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda13.
title		Puppy 410, full install on /dev/sda13
root		(hd0,12)
kernel		/boot/vmlinuz root=/dev/sda13 pmedia=atadh nosmp
savedefault
boot

Now this is mine so you will have to edit /dev/sda13 and (hd0,12)
for your install.

sda is a sata drive
hda is a ide drive (I think!!)

and (hd0,XX) is the first hard drive (hd1,XX) if you have two etc.
Notice that the XX number is one less than the /dev/sda partition.

I am not sure about the pmedia=atadh nosmp at the end I would try without
first.

Hope this helps

Ps in a terminal

To backup
sudo cp boot/grub/menu.lst /boot/grub/menu.backup_24_10_08

To edit
gksudo gedit /boot/grub/menu.lst

---

### Post by iampriteshdesai on 2008-10-25
I tried to do as you said but I ran into few problems.
I have Ubuntu installed via Wubi. When I boot in my PC it shows  options
Vista
Ubuntu
now when I select Ubuntu I get a line on screen saying wait  seconds, press esc to see options.
I pressed esc and I got an option which had  options for Ubuntu, Vista, and Puppy Linux.
But when I select Puppy I get the following line
kernel /boot/vmlinuz root=/dev/sda13 pmedia=atadh nosmp
cannot find file.
Here are some extra details.
I have installed Puppy on my sd drive in a folder called Puppy_Linux
how to do it?
Is there any way I can get Puppy option in the main OS choosing step rather than in grub?
Thankyou

---

### Post by alan34 on 2008-10-25
I dont do vista but found this. *Please be careful I do not know if this is a solution to your problem.*

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Look here

[http://en.wikipedia.org/wiki/Windows_Boot_Manager](http://en.wikipedia.org/wiki/Windows_Boot_Manager)


Another better and **much** safer solution may be to put Puppy on a usb stick and then alter the boot order in the BIOS to boot from that first. Then with the stick in you get Puppy and with it not in you get Vista/Ubuntu.


Remember Puppy is designed to be run from the CD no real need to install it to your hard drive. I did it because I can :) 
The setup on my machine is much different to yours, I just like playing around with different OSs.


Please ignore my first post it does not apply to your setup at all. Just put your /boot/grub/menu.lst back to how it was.

Good luck Alan

---

### Post by iampriteshdesai on 2008-10-26
Hi Alan,
Thanks to you, I managed to get Puppy into the GRUB. 
After installation, Puppy Linux gave me the entire path to paste into Grub.
title Puppy 410, full install on /dev/sda13
root (hd0,12)
kernel /boot/vmlinuz root=/dev/sda13 pmedia=atadh nosmp
savedefault
boot I did that. Now I have Puppy working under the second boot loader.
However it doesn't work in Vista's bootloader. The program you suggested is simple, nut merely adds an entry into the boot loader. It doesn't even ask for the path where the file is. Also selecting the option it created while booting doesn't lead anywhere.
Do you have any idea how to get Puppy in Vista's boot loader?

---

