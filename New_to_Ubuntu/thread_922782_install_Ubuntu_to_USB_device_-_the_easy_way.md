---
title: "install Ubuntu to USB device - the easy way"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-09-17
Ubuntu can be installed on almost any USB device with 2 GB of memory or more.
USB HDD, Thumb Drive, Digital camera, Cell phone or MP3 player.
There are many reasons to own a portable operating system.
You can take your desktop anywhere, to a friend,s house to play your latest game or to foreign country. 
You can walk into the closest internet cafe open Google Earth with all your places and routes or open any of your other essential applications. (handy if your laptop gets lost).
I use mine to securely run Linux on the office computer, to play movies on the media center, to service the other computers in the house, and to try experiments with Ubuntu that I would not otherwise try.

There are many links to extremely complex methods of installing Ubuntu to Thumb Drive.* 
You can even download extremely complex looking programs to help simplify the process.
Many of these just copy the Live CD which does not save changes on reboot.

Setting up Ubuntu on a USB device is no different than setting it up on a hard disk.

Installation:
Simple Method
Unplug your HDD power cables or disable your HDD's in bios. (optional).
Boot the Live CD..
Plug in the USB device.
Run Install.

When you get to partitioning you can use:
Guided, use entire disk
This seems to work best on low quality devices.
or if you want to be able to plug into a computer running windows and upload files, use:
Guided, resize ...and use remaining space.
Then drag the bar right to show how much FAT you want to keep
Complete the setup, when it is done you will have Ubuntu on USB.

I find Xubuntu more suited to slower thumbdrives, setup is the same for this and other members of the Ubuntu family.

Booting:
Not all computer BIOS will support USB boot.
Some will support booting from USB HDD but not pendrive.
If the computer supports USB booting, the BIOS must be set to boot the USB device before or as the first HDD.
Some computers will not boot from USB, on these the Flash drive can be booted from CD.
See [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Partitioning:
You can adjust or create partitions on your device using gparted.
I have not found a way to add a partition recognized in Windows after setup.
If you want to use the chip for it's original purpose, such as taking photos or storing music on a m3 player leave a little of the original partition at setup.

Home folder:
You can copy the Home folder from your HDD to the USB drive.
Use gksu nautilus, (or gksu thunar if you are using Xubuntu).
Merge but do not overwrite any files in the new home folder.
You will need to enable permissions, see info on chown elsewhere, use -R
You might also want to create a different home folder for your office computer than for your game machine, setting different permissions and wallpaper or perhaps create a smaller desktop for your eee. Home folders can be added in Users and Groups.

Security:
If you are walking around with a copy of your home folder on an easy to misplace micro SD, it is wise to encrypt it.
There are simple methods.

Restricted Drivers:
Switchconf may be used to enable various xorg.conf options at boot.
You can select your main computer with dual monitors or your media center with 50" HDTV, both using the latest Restricted drivers, or your laptop with ATI, a generic computer, even an EEEPC. I have not found a way to keep both Nvidia and ATI drivers co-existing on the same installation and could use some advice.

Grub Boot Options:
It is simple to modify grub menu for an option to select the host computer's HDD or other devices at boot.
add
title* Windows
root** (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
at the end of /boot/grub/menu.lst. It will allow you to boot to the first hard disk in bios at grub. 
(If you leave your hard drive plugged in durring installation, grub will provide options to boot from any of the bootbable drives on the computer).
*
Optional Desktops:
You can install multiple desktops, (Ubuntu, Kubuntu, Xbuntu, Edbuntu, Ubuntu-studio) depending on which you want to boot from what computer.
I normally use xubuntu-desktop on my office computer but prefer ubuntu-desktop for the entertainment center.
Synaptic has many desktop options and is simpler and safer than command line for installing them.

Other Uses:
System management. The USB drive can be used to run gparted, anti-virus programs, etc on other computer systems. Much handier than the live CD. You can install and run any system tool on USB that you can on HDD.
Secure web browsing. No trace is left on the host computer and you don't loose your cookies or bookmarks.
Game stick, install only what is required to optimize the game and have nothing else running in the background.
Espionage, loaded on a micro sd chip it a great tool for a spy on a low budget. 
Expendable test system, Use to test risky stuff before attempting it on your main system,* Copying the Ubuntu partition to un-formatted usb space on the drive, as a backup, makes re-installs much faster than from Live CD.

Speed Issues:
USB drives are getting faster but are no where near the speed of SATA.
It will take longer to install Ubuntu to a USB device than to HDD, expect 1/2 hour or more.
If there is lots of ram in the host computer there should not be an issue when running normal tasks.
USB write speed is still faster than most internet connections can download, movies play great and you don't worry about DRM eating your hard drive.
* 
I love my dongle and wish to share the experience.
I've placed this in Beginner Talk because bootable USB is great for the beginner or the un-committed, as long as they don't have to work through pages of command line hieroglyphics to install it.
If there is any interest, make a comment, and I will try to expand or clarify the above and add some links.

---

