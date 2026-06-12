---
title: "How can I format my external harddisk?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by eHobayyeb on 2008-07-11
Hi,

I have a WD external Harddisk with 160GB NTFS filesystem and want to format it and set it to ext3 filesystem.

I used GParted but every button and menu item is disabled except for some items which they just show you information or close the software.

How can I enable these buttons and menu items?

thanks

---

### Post by bumanie on 2008-07-11
Use gparted as you are doing, but **unmount** the external drive first. Gparted will not do anything to a mounted drive other than allow you to view it.

---

### Post by tenjin1 on 2008-07-11
You can also format from command line by using fdisk.

Plug in your USB hard Drive, after it is mounted, Open the terminal and type:
```
sudo fdisk -l
```

This will list all hard drive and partitions on your system. Also this will give you the name of the location of your USB hard drive. (example /dev/sda)

First you will use the fdisk command to erase any old partitions on the drive and create a new one. Any changes you make using fdisk are only made permanent if you then issue the “w” command before quitting. If at any time you find yourself stuck, you can quit the program without saving changes by holding the "Ctrl" key and pressing "c."

At the command prompt, type:
```
fdisk /dev/sda
```
replacing the "sda" with the letters for your drive from above.

Upon opening, fdisk may give you a couple of warnings, all of which can be ignored. It then gives you a prompt that looks like this: 
```
Command (m for help):
```

Enter “p” to see the partition table of the drive. The first line of output from the “p” command will also tell you size of the drive. This is a good way to double check that you are working with the correct drive.

If there are any partitions already on the drive they will be listed as the last lines of the “p” command. 

To delete any existing partitions, press “d” then enter. It will ask you which partition number you wish to delete. The number of the partition is the number that follows sda. If there are multiple partitions repeat the “d” command for each one. You can always view the partition table again with the “p” command.

Once you have deleted all existing partitions on the drive you are ready to make a new one. Type “n” and hit enter. Then press “p” to create a primary partition. It asks you for a partition number, enter “1." Now you are asked which cylinder the partition should start at, the beginning of the drive is the default, so just hit Enter. Then you are asked for the last cylinder, the end of the drive is default so you can just press Enter again.

Now you are back at fdisk's command prompt. Use the “p” command to check the partition table. You should now see your new partition at the bottom of the output. In the example it lists “/dev/sda1.”

You now need to set the filesystem type for your new partition with the “t” command. You are asked for the Hex code of the filesystem you wish to use. We wll use the standard Linux ext3 filesystem which is “83." If you are doing something special and know of a particular filesystem that you need to use, you can press “L” to see all the codes, which are one or two characters made up of the numbers 0-9 and the letters a-f.

Now just issue the “w” command to write your new partition table and exit fdisk.

Now you need to create the filesystem on the drive. This is done with the “mkfs” command.

At the command prompt, enter:
```
mkfs -t ext2 /dev/sda1
```
while remembering to change the sda1 to whatever the letters are for the partition you just created.

If you are using a different filesystem than ext3, you will have to specify that where "ext3" is in the above command.

All that is left is to run a check on the drive and enter it into your fstab so that the drive mounts each time you start your computer. This can be done with a single fsck command.

At the command prompt, type: 
```
fsck -f -y /dev/sda1
``` 
again replacing sda1 with the letters and number for your partition.

After fsck runs, your new drive is formatted. Restart your system before using it.

If you reformatted your system drive, you will now need to boot off an installation disk to install an Operating system.

---

### Post by Inxsible on 2008-07-11
GParted is much simpler. The options are all locked because the drive is probably mounted.

You may also want to take backups of the data on the external drive - if you have any.

---

