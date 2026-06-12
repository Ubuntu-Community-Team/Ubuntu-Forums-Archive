---
title: "Flashing BIOS without floppys or bootdisks for Dell Computers"
date: 2007-12-24
forum: Outdated Tutorials &amp; Tips
---

### Post by ziploc67 on 2007-12-24
ok, here is how you flash your BIOS for Dell Computers, without having to go through the trouble of creating floppy disks or downloading boot disks.

Please note that I take no responsibility as to what you do with this information. Please know that incorrectly flashing (upgrading) your BIOS can result in corrupting your BIOS, making it impossible to boot your computer, because the BIOS is the first thing that starts up. if this does occur, your computer becomes a functional paperweight, albeit an expensive one.
[B]
Step 1: Identify your model computer[/B]
go to dell.com, you will see to the lower right quadron of your screen a blue button that says "help & support" under it. put your cursor over it, and select "drivers & downloads." click the green button saying select model. navigate to what system you have. when that is completed, hit the confirm button. you will be brought to a screen where there are options listed for downloads. hit the plus sign to the left of Bios, and click "Download Now" on the box that pops up. save the .exe file to your desktop. rename it to something easy to remember, as continually typing the file name will eventually irritate you.;)

Step 2: Get Biosdisk, and untar
go to  and download [http://linux.dell.com/biosdisk/]("http://linux.dell.com/biosdisk/") and download "biosdisk-0.75-2.tar.gz." untar it by extracting it into a folder. rename the folder to something easy to remember, like biosdisk.

Step 3: Install necessary tools
this is an easy step, open your terminal, and type "sudo /bin/bash" (without quotes). this will give you root capabilities. type your password, and then type "apt-get install sysutils syslinux" (no quotes). thats all thats needed in this step.

Step 4: Installing Biosisk
open a terminal, and type "cd /home/yourname/Desktop/filename" and then type "./install.sh

Step 5: Create image file
in that same terminal used above, type "biosdisk mkimage /home/yourname/Desktop/downloadedbiosfile.exe" then type "mv /tmp/downloadedbiosfile.img /boot/"

Step 6: Prepare grub:
in same terminal used above, type "cp /usr/lib/syslinux/memdisk /boot/", hit enter, and then reboot your machine.

Step 7: Installing BIOS
heres what you have been waiting for. as the computer boots, you will come to a message where it says "hit esc for menu". using the arrow keys, go to the top most option, and hit "E" to edit. WARNING: DO NOT EDIT THE PREEXISTING LINES. using the details given, add two new lines, and edit them. in the first line, edit it and type "kernel /boot/memdisk" and in the second, type "initrd /boot/downloadedbiosfile.img". hit esc and boot from that kernel. the bios setup will begin, and hit any key to commence it. once it is finished, hit any key to finish the process, and there you go! you have just flashed your BIOS!


*note: i did this personally, and this also helped fix the freezing of my usb mouse.

---

### Post by claytronic on 2008-01-17
Thanks for the HOWTO.  I found it very helpful for flashing the BIOS of my D400 laptop.  Bringing it up to A08 seems to have improved the hibernation problems I was having with the Gutsy 7.10 install.

---

### Post by uxinn on 2009-03-03
Was worried for a second I might need to install *Beeeeep* to be able to flash the bios 

Thanks, just updated my Dell M65 to bios version A10
(so far so good)


Uxinn

---

