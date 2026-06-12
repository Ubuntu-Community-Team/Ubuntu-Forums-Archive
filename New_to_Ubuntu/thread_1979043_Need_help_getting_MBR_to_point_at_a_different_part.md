---
title: "Need help getting MBR to point at a different partitions boot folder"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by diablo75 on 2012-05-12
I have a friend who did some experimenting with having two different copies of Ubuntu installed on his system where they shared a home partition.  The idea was to have one as a backup in case he screwed up the other.

He's had some problems upgrading to 12.04 recently (his video card needs an upgrade and he's going to order a card) but in the mean time his latest attempt to reinstall 12.04 over the one he gummed up has resulted in the MBR pointing to a copy of grub that was a part of the other older Ubuntu install on a separate secondary root partition.  So basically he gets an old school black and white grub menu coming up with a linux kernel versions that aren't actually present where it thinks they are.

My bet is the install itself (besides grub) of 12.04 went fine, it's just accessing the wrong copy of grub from the wrong partition.  Right now he's only able to use the system by booting a live CD so I need to know how to fix this using a Live CD.  Thanks for the help!

---

### Post by oldfred on 2012-05-12
Often with multiple installs or multiple drives it is best to run boot info script to see exactly what is where.  Boot-Repair also runs the script and can often fix minor issues.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Another repairCD that can often boot directly into a broken install.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Or manually reinstall grub from the liveCD or USB.
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct if more than one you have to know which is which - see boot script above:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

