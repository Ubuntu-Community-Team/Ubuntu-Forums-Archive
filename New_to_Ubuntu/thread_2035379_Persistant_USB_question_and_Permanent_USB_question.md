---
title: "Persistant USB question and Permanent USB question"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by TheSpaceBetween2 on 2012-07-30
Hi I really am not at the level of even this forum but we all have to start somewhere. 

My issue is this I installed ubunut 10.0.4.3  using pendrive app to make it a persistent drive, searched around the internet about how to update firefox, and it said move to ~/opt/ so managed to do that and finally get it working. For chrome I think I just downloaded it and clicked it much like I would in windows, both remained after rebooting however avast which I had Downloaded to Downloads folder was no longer present, I had installed it with dpkg -iavast* as I was told, when looking about for it found a reference to it in " tmp" tried reinstalling but got told it was already installed, even though I could not find it's icon any where removed it, reinstalled it but when running all I get is a message "the engine failed to initialize due to invalid argument".  If I format the drive and use pendrive again should I move avast to /opt/ before installing it to make it persistent? as I guess "tmp" is temporary folder. 

I also have a question about installing to a different pen drive, a guide says make sure you select /dev/sdc1 NOT /sdc, which is the default as that will write grub to your primary hard drive and make it fail to boot but my question is if you had more partitons on your sdc drive would you still just select the first for boot loader to load to, or a different partion or ALL partions, in order to avoid the main hard disk GRUB being tampered with? 

Finally how do you post those boxes with output in this forum and insert screen shots into a post as I see other people using these tools to assist the clarity of their posts?

---

### Post by oldfred on 2012-07-30
Welcome to the forums.

How large is flash drive? If 8GB or more you can do a full install that is then fully updateable. Otherwise you use persistance.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Lubuntu may fit on a smaller drive and work a bit better from USB flash as applicatons are smaller:
Installs to 4GB flash, newer of Ubuntu versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

I have a full install of Ubuntu in a 8GB partition on my 16GB flash with the other 8GB just for data. Not speedy but functional.

You do not need a separate /boot for a pen drive nor most desktop installs. You should always install the grub2 boot loader to the drive like sdc not a partition like sdc1 or sdc2. Partitions have numbers after the drive. 

The edit panel above a full message (not quick reply) had a paperclip to attach a screenshot or other data. Also you can paste code or long bits of formated text. Then highlight like copying again and click the # in the edit panel to auto add code tags. Preserves formating and makes it easier to review.
Hover over each icon do get its name.

---

### Post by C.S.Cameron on 2012-07-30
If you are doing a full install to pendrive sdc, grub should be installed on sdc not sdc1.
For a beginner I would suggest unplugging your internal drive before proceeding.

Use the # sign above the message window to wrap code tags around output.

Use the icon with the mountains to insert an image.

Play around with the various icons, (or hover above them), to see what they do.

Welcome to the forums.

---

### Post by TheSpaceBetween2 on 2012-07-30
Hi just bumping so this thread is not forgotten about.  And because I have another issue that is usb drives randomly become unmountable either by gui or trying sudo mount /dev/sdc  /media/. I am not sure of the unmount command but I thought it was sudo unmount /dev/sdc  /media but when the drive becomes mountable the unmount command doesn't work and their is no option on the GUI to unmount flash drives.

---

### Post by TheSpaceBetween2 on 2012-07-30
> **C.S.Cameron said:**
> If you are doing a full install to pendrive sdc, grub should be installed on sdc not sdc1.
For a beginner I would suggest unplugging your internal drive before proceeding.

Use the # sign above the message window to wrap code tags around output.

Use the icon with the mountains to insert an image.

Play around with the various icons, (or hover above them), to see what they do.

Welcome to the forums.


Thanks my drive is 8GB.  I tried persitance but that did not work correctly with avast, but [did with google and firefox updates. I was wondering if that was due to me not moving it to /opt/  or should persitance just work with the default downloads folder used for the install?

Secondly you both say to install it to /sdc not the partition but this link [https://wiki.ubuntu.com/LiveUsbPendrivePersistent/](https://wiki.ubuntu.com/LiveUsbPendrivePersistent/)

[FONT=Arial]Says " Choose to install GRUB to the first USB partition (i.e. /dev/sdb1, rather than simply /dev/sdb).  [/FONT][I][FONT=Arial]Failure  to do this will cause the GRUB on your hard disk to be changed and  render the system unbootable from the hard disk, requiring you to boot  from a CD and reinstall GRUB to the hard disk (possibly requiring a  chroot to the hard disk filesystem first)." 
[/FONT][FONT=Arial][I]
THIS is confusing as its the opposite of what your tellling me. Also I don't know how to remove a hard drive and surely telling the installer to write grub to sdc means it wont touch sda? [/I][/FONT]
[/I]
Is the link incorrect? I was just wondering about mutiple partions if you need to install the boot loader to them all or to the first one or to a specfic one?  Now I don't know whether to install it to sdc or sdc1 as your advice differs from the article psoted.

---

### Post by oldfred on 2012-07-30
Because that set of instructions also discusses 8.04 which used grub legacy. You could install grub legacy to a partition and use the Windows or any of the Windows like boot loaders in the MBR to boot. Windows type boot loaders just find the boot flagged partition and jump to that partition. Normally Windows has additional code in the partition boot sector. Old grub legacy installs to a partition ok, but grub2 does not work well from a partition. 

Best just to install grub2 to the MBR of the flash drive. You cannot use any of the auto install procedures as then grub2's boot loader auto installs to the MBR of sda which usually is the internal drive. If you use Manual install or Something else then you get the option to choose where to install grub2's boot loader. But you have to select which partition is / (root) and what format.

---

### Post by C.S.Cameron on 2012-07-31
Following is what worked for me with 10.04:
Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

