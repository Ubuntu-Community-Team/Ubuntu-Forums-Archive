---
title: "HowTo: Make a USB Recovery Drive"
date: 2008-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Belak on 2008-04-19
Hi, in this tutorial, I will show how to make a USB recovery drive with the following:

Super Grub Disk
gParted Live CD
Puppy Linux Live CD
Backtrack 3 Live USB

If you want tutorials on how to do other live CDs or Install CDs, just let me know and I'll try. I know DSL and DSL-N will be easy, along with knoppix... and I think I can do backtrack and an Ubuntu Live CD. I'll only try them if people want it though. I have little use for all of these...

You will need the following:
[LIST]
[*]At least a 1.5GB* Flash Drive (Empty-All data will be removed)
[*]A bios supporting USB booting (Note: You may be able to chainload into your USB drive. If you want to know how, just post, and I'll look into it.)
[*]gParted (Reccomended to be installed in a current Ubuntu install)
[*][Super Grub Disk Live USB](http://forjamari.linex.org/frs/?group_id=61&release_id=447)
[*][gParted Live CD - not USB - and be sure to download the ZIP file](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
[*][Puppy Linux Live CD (I got the puppy-3.01-seamonkey.iso file)]("http://distro.ibiblio.org/pub/linux/distributions/puppylinux/")
[*][BackTrack 3 (Be sure to get the Live USB - it has more features, and it's easier to extract :D)]("http://www.remote-exploit.org/backtrack_download.html")
[/LIST]

* Sizes Note:
[LIST]
[*]Any size above 4MB will work for SuperGrubDisk (SGD is for MBR repair, General boot repair, and it just works like grub, so you can use it to boot the OS's on the USB stick)
[*]About 64 MB is the minimum for gParted (And SGD)
[*]About 256 MB is the minimum for Puppy Linux (And gParted, and SGD)
[*]1.5 GB is for Backtrack, Puppy, gParted and SGD. (You could probably get away with 1 GB if you just wanted Backtrack)
[/LIST]

Steps:
Back up all important data on your USB drive.
If you don't have a USB Flash Drive, you'll need it for this. This WILL NOT WORK if you burn it to a cd!
Download the ISOs and extract them to separate folders.

Now, insert the USB drive and unmount it.

Step 1 - Partitioning
Open gParted and delete the partitions on it. Then make 2 new partitions
[LIST]
[*]256 MB: fat32 or ext2 (For SGD, gParted and Puppy Linux)
[*]1 GB: fat32 or ext2 (For Backtrack)
[*]The rest of the drive: fat32
[/LIST]
The first partition is for the bootloader and gParted and Super Grub Disk Files and the 2nd partition is extra data storage (not needed with smaller drives)

Now be sure to mount the USB partitions (Easiest from nautilus) and we will continue.

From this point on, I will refer to the 100 MB partition as /media/usb_boot
and the rest of the USB drive as /media/usb_data

Step 2 - Installing Super Grub Disk and Grub on your USB Flash Drive (Adapted from [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive) and [http://ubuntuforums.org/showthread.php?t=575406](http://ubuntuforums.org/showthread.php?t=575406).)
Before doing anything, we need to make sure that we (the user) can write to the usb drive.
Run the following commands in a terminal to accomplish this (Replace USER with your username):
```
sudo chown -R USER /media/usb_data
sudo chown -R USER /media/usb_boot
```

Next, run the following commands:
[COLOR="Red"]**CAUTION:**[/COLOR] Be careful when using the rm -r command! If used wrong, it can destroy your system if used wrong!
```
rm -r /media/usb_data/lost+found/
rm -r /media/usb_boot/lost+found/
```
This will remove the extra directories automatically made in the partitions. I'm not sure why they are made in the first place...

We now need to untar the SGD file.
Run the following commands in the directory where the tar file is (Be sure to replace the SGD tar file name with the right name):
```
tar xvfz sgd.tar.gz
```

Now we need to copy everything, so cd to the directory SGD just extracted to and run the following command:
```
cp -rv boot /media/usb_boot
```

If you plugged in your USB key after you booted up, you will have to restart the computer, making sure it is left plugged in.

Now, open up a grub shell with the following command:
```
sudo grub
```

You should now have a shell prompt like this:
> grub>_
Where the _ is your cursor.

Grub, along with the rest of the terminal, supports tab completion, so instead of typing in all of the commeand, just type the first few letters then hit TAB.
We need to figure out which HD that Grub sees is our USB one, so we use the geometry command to view the partition layout.
Type or paste in the following command then hit TAB to see the possible HDs:
```
geometry (
```

On my computer it displayed the following:
>  Possible disks are:  hd0 hd1

This tells us that 2 hard disks are noticed by grub.
Run the following command with each hard disk to view the partition layout (you should just have to replace x with a number each time):
```
geometry (hdx)
```

Example Output:
Yes, I know, pointless amount of partitions... that's what happens in a triple boot.
Output from geometry (hd0)
> drive 0x80: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type unknown, partition type 0x82
   
Output from geometry (hd1)
> drive 0x81: C/H/S = 243/255/63, The number of sectors = 3914751, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is fat, partition type 0xb
As you can see, from the partition layout, hd1 is the USB drive on my computer.


Run the following commands to install grub on your hard drive (Replace x with hd number of your USB drive):
```
root (hdx,0)
setup (hdx)
```

Example Output:
>  Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

Now, run the following command to exit the grub shell:
```
quit
```

I would reccomend this following command for convenience. It is not required. This will change the ownership of the grub folder to your username (Replace USER with your username):
```
sudo chown -R USER /media/usb_boot/boot/grub/
```

Congradulations. Super Grub Disk/Grub is now installed on your USB drive!

Step 3 - gParted
Now the bulk of the work is done. Yay.

First, we need to extract the zip file.

The following command will extract the gparted-live-0.3.6-7.zip file to a directory called g0.3.6-7
```
unzip gparted-live-0.3.6-7.zip -d g0.3.6-7
```

Next, fix permissions (be sure to replace the USER with your username and also to use the right directory name):
```
sudo chown USER -R g0.3.6-7/
```

Now we need to copy what we need.
```
cd g0.3.6-7/
cp -r live/ /media/usb_boot
```

Now, to create the grub entries. I used my guide ([which can be found here]("http://ubuntuforums.org/showthread.php?t=759890")) to get the correct entries.
[b]PLEASE NOTE:[b] You must use the usbshift grub command in order to get this working. You just add a line right after the title line in your entry that will say usbshift.

This is what my entries ended up being:
```
title gParted 0.3.6-7 (Live Boot)
usbshift
kernel $(grub_device)/live/vmlinuz1 boot=live  username=casper   noswap vga=788 ip=frommedia
initrd $(grub_device)/live/initrd1.img

title gParted 0.3.6-7 (Live Boot to RAM)
usbshift
kernel $(grub_device)/live/vmlinuz1 boot=live  username=casper   noswap vga=788 toram ip=frommedia
initrd $(grub_device)/live/initrd1.img

title gParted 0.3.6-7 (Live Boot - Without Framebuffer)
usbshift
kernel $(grub_device)/live/vmlinuz1 boot=live  boot=live  username=casper   noswap ip=frommedia vga=normal
initrd $(grub_device)/live/initrd1.img

title gParted 0.3.6-7 (Live Boot - Failsafe)
usbshift
kernel $(grub_device)/live/vmlinuz1 boot=live  username=casper   noswap acpi=off irqpoll noapic noapm nodma nomce nolapic nosmp ip=frommedia vga=normal
initrd $(grub_device)/live/initrd1.img
```

I like having this in a separate menu, so I made a file called gparted.lst in the /media/usb_boot/boot/grub folder then added the following to the menu.lst before the SGD entry:
```
title gParted 0.3.6-7
usbshift
configfile $(grub_device)/boot/grub/gparted.lst
```

Because I had a separate gparted.lst file, I added the following to the bottom (It'll take you back to the main menu):
```
title Go Back
usbshift
configfile $(grub_device)/boot/grub/menu.lst
```

gParted is now installed!

Step 4 - Puppy Linux

First we need to mount the iso (where puppy.iso is the name of your iso file)::
```
mkdir /tmp/isotemp
sudo mount -o loop puppy.iso /tmp/isotemp
```

Now we need to copy the files we need:
```
sudo cp /tmp/isotemp/pup_301.sfs /tmp/isotemp/zdrv_301.sfs /media/usb_boot/
sudo cp /tmp/isotemp/vmlinuz /tmp/isotemp/initrd.gz /media/usb_boot/boot/
```

Now that we don't need the CD any more, let's unmount it (Where puppy.iso is the same iso file as before)
```
sudo umount puppy.iso
```

Now we need to add an entry to the menu.lst file, so open it up (the file in /media/usb_boot/boot/grub/menu.lst)
Find your gParted entry and add the following below it
```
title Puppy Linux 3.0.1
usbshift
kernel $(grub_device)/boot/vmlinuz pmedia=usbflash
initrd $(grub_device)/boot/initrd.gz
```

Yay! Puppy Linux Should be Working!

Step 5 - Backtrack 3
Please note that using Backtrack for cracking your neighbor's wireless internet (Or any internet other than your own) is illegal and not promoted. I will not tell you how to crack any network here, so don't ask.

First, we need to get to the directory we downloaded backtrack into.
Now that we're there, we need to extract it with the following command (Replace backtrack3.rar with the rar file name)
```
unrar x backtrack3.rar
```

Now that we've extracted all the files, we need to convert the syslinux file into a grub menu file which we will save at /media/usb_boot/boot/grub/backtrack3.lst ([My guide can be found here]("http://ubuntuforums.org/showthread.php?t=759890")). Please note that you need the root command to get it to boot right.
I also added a Go Back entry just like before.
The syslinux file can be found at /BACKTRACK_EXTRACTED_DIR/boot/syslinux/syslinux.cfg
My grub file ended up being the following (For the BackTrack 3 Beta - 14-12-2007 release):
```
title BT3 Graphics mode (KDE)
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw chexpand=256 autoexec=xconf;kdm
initrd /boot/initrd.gz

title BT3 Graphics mode (Flux)
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw chexpand=256 autoexec=xconf;flux
initrd /boot/initrd.gz

title BT3 Graphics mode (Compiz) - Experimental
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw chexpand=256 load=cubez autoexec=xconf;cubez;startx
initrd /boot/initrd.gz

title BT3 Graphics mode (Compiz Nvidia) - Experimental
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw chexpand=256 load=cubez autoexec=xconf;cubez;startx
initrd /boot/initrd.gz

title BT3 Graphics mode with Persistent Changes
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw changes=/slax/slaxsave.dat autoexec=xconf;kdm
initrd /boot/initrd.gz

title BT3 KDE Copy To RAM
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw chexpand=256 copy2ram autoexec=xconf;kdm
initrd /boot/initrd.gz

title BT3 Graphics VESA mode (1024x768)
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw chexpand=256 autoexec=kdm
initrd /boot/initrd.gz

title BT3 Text mode FB
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw
initrd /boot/initrd.gz

title BT3 Text mode FB no DHCP
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw nodhcp
initrd /boot/initrd.gz

title BT3 PXE Server
root (hd1,1)
kernel /boot/vmlinuz vga=0x317 ramdisk_size=6666 root=/dev/ram0 rw load=pxe
initrd /boot/initrd.gz

title BT3 Text mode (Safe)
root (hd1,1)
kernel /boot/vmlinuz vga=normal ramdisk_size=6666 root=/dev/ram0 chexpand=256 rw
initrd /boot/initrd.gz

title Run Memtest utility
root (hd1,1)
kernel /boot/mt86p
quiet

title Go Back
usbshift
configfile $(grub_device)/boot/grub/menu.lst
```

Now cd into the directory that was just created from when you extracted the rar file.

Now run the following commands to copy what you need (This assumes that your backtrack partition is at /media/usb_bt. You should change this accordingly and also change USER to your username). You may not need the sudo and you may not need the 2nd command.
```
sudo cp -rv ./* /media/usb_bt
sudo chown -R USER /media/usb_bt
```

Now, to make sure that the main menu.lst has the right entry.
Open it up and add the following where you want the entry to show up.
```
title BackTrack 3 Beta
usbshift
configfile $(grub_device)/boot/grub/backtrack3.lst
```

Congrats. Backtrack 3 is now installed!

More to come soon (DSL-N, Ubuntu on a Stick)

Cheers,
Belak

---

### Post by reyhan on 2008-05-13
Thanks for the tutorial Its work successfully!!:):)

---

### Post by Belak on 2008-05-14
> **reyhan said:**
> Thanks for the tutorial Its work successfully!!:):)

Awesome.
I'm glad it helped.

Honestly, here are my personal opinions on all of the software on here.
SGD - Really Helpful if you do a lot with the MBR. This had saved my computer multiple times.
gParted - Always useful. Especially for installing Ubuntu. Especially since they changed how it's packaged. It's a lot easier to install now.
Puppy Linux - I don't like it. It's just a mini desktop install. If you have a large enough flash drive, try DSL-N. Or even a Persistent Ubuntu install
Backtrack - AWESOME. Sorry, I like the network tools. :D

---

### Post by reyhan on 2008-05-16
Thank you Very much!!! For this tutorial!!!
Maybe, can you Make A tutorial About Installing Damn Small linux On USB And about The network Tools on backtrack!!?:):)
now I can Use Linux Everywhere I Want it!!!:):)
Oh yeah and one more I like the network Tools but i am not Really smart to using it....

once Again Thanks:):):):)

---

### Post by Belak on 2008-05-17
Yeah, I don't know if I'll do DSL or DSL-N.

DSL-N is evil. For whatever reason, the config file they use it in some weird encoding so I can't use it. I'm looking into other options though...

---

### Post by reyhan on 2008-05-17
Hey I want To install SLAX On the same Flash disk
but how do i do that?:(:(

---

### Post by love2learn on 2008-05-18
okay maybe this is where i get confused:

Now we need to copy what we need.
     Code:
     cd g0.3.6-7/
cp -r live/ /media/usb_boot 
Now, to create the grub entries. I used my guide ([which can be found here]("http://ubuntuforums.org/showthread.php?t=759890")) to get the correct entries.
[b]PLEASE NOTE:[b] You must use the usbshift grub command in order to get this working. You just add a line right after the title line in your entry that will say usbshift.

:::you say we need to convert the syslinux.cfg file but I took the above command to mean we are just copying over the live folder out of the g0.3.. folder. so only the live folder is in the usb drive. If i was to modify the syslinux.cfg that would still be in my ~./download/g0.3/syslinux/  folder that is still on my computer. so, how would modifying this help my usb drive?

---

### Post by Belak on 2008-05-18
You don't modify any syslinux files. You only change the grub menu.lst files.

The guide I mentioned helps you convert a syslinux file into a grub file so you can use it with super grub disk.

EDIT:
Ok, basicly, for the gparted part, you make the following file: /media/usb_boot/boot/grub/gparted.lst
That's where you put all the converted syslinux stuff.
Next you add the entry in the main menu.lst file on the usb drive in order tolink to the new one you just created.

Also, the reason we're only copying the live folder is because we only need the stuff in there. That's the folder that contains the kernel, and filesystem (If I'm remembering right). If we would have copied the whole thing, we would have gotten some extra syslinux crap which we don't need because we have SGD.

---

### Post by love2learn on 2008-05-18
okay, i think i am tracking now i just need to know which file i need to mod in the boot/grub/  because i dont see a gparted and this is probably not the best time to guess so here is my list::

l2l@Laptop:/media/disk-2/boot/grub$ ls
choose               
menu_super_grub_disk_backup.lst  
stage2
e2fs_stage1_5
menu_super_grub_disk.lst~        
stage2.c
fat_stage1_5         
message                          
stage2_eltorito
ffs_stage1_5        
 minix_stage1_5                  
 stage2_size.h
iso9660_stage1_5     
original_menu.lst                
start
jfs_stage1_5         
original_tirwal_menu2.lst        
start_eltorito
memdisk              
pre_stage2                       
ufs2_stage1_5
menu.lst             
pxeloader.S                      
ufs_stage1_5
menu.lst~            
reiserfs_stage1_5                
vstafs_stage1_5
menu_old.lst         
stage1                           
xfs_stage1_5
menu_only_cdrom.lst  
stage1_5.c
l2l@Laptop:/media/disk-2/boot/grub$



also I plan to modify the list with this::
title gParted 0.3.6-7 (Live Boot)
usbshift
kernel $(grub_device)/live/vmlinuz1 boot=live  username=casper   noswap vga=78$ 
initrd $(grub_device)/live/initrd1.img

title gParted 0.3.6-7 (Live Boot to RAM)
usbshift
kernel $(grub_device)/live/vmlinuz1 boot=live  username=casper   noswap vga=78$ toram 
initrd $(grub_device)/live/initrd1.img

title gParted 0.3.6-7 (Live Boot - Without Framebuffer)
usbshift
kernel $(grub_device)/live/vmlinuz1 boot=live  boot=live  username=casper   noswap  vga=normal
initrd $(grub_device)/live/initrd1.img

title gParted 0.3.6-7 (Live Boot - Failsafe)
usbshift
kernel $(grub_device)/live/vmlinuz1 boot=live  username=casper   noswap acpi=off irqpoll noapic noapm nodma nomce nolapic nosmp  vga=normal
initrd $(grub_device)/live/initrd1.img

based on my syslinux.cfg::

label GParted Live
  MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (Default settings)
  # MENU PASSWD
  kernel /live/vmlinuz1
  append initrd=/live/initrd1.img boot=live  username=casper   noswap vga=78$
  TEXT HELP
  * GParted live version: 0.3.6-7. Live version maintainer: Steven Shiau
  * Disclaimer: GParted live comes with ABSOLUTE NO WARRANTY
  ENDTEXT


am i in the ballpark now?

---

### Post by Belak on 2008-05-18
Yep, that would work.

Now, you can either copy that to the main menu.lst or create a sub menu like I did by placing that in a new file called gparted.lst and linking to it from the main menu.lst then adding a back button.

Sorry if I wasn't clear, but that file will probably not exist before you make it.

Yeah, that looks right, based on your file.
The vga=78$ looks a little weird though... It can't hurt to try it since that kernel option is only for the framebuffer.

Cheers

EDIT:
I think the vga=78$ should be vga=788

---

### Post by love2learn on 2008-05-19
Wow, 

3 days later, and thinking that the poster of this thread has no idea what he is talking about, and I find out that there is an issue with my sony vaio laptop ( specifically vgn-sz320p ) I was doing everything the thread said but I was getting an "error 25: disk write error" right after i selected anything in the grub menu. It was teasing me pretty hard because I could boot into grub on the thumbdrive. So, I knew it was not the usb stick or laptop ( so I thought ). But after 3 days of gparting the thumbdrive ( and my own laptop once ) over and over again I decided to test it on another computer.... it works perfectly fine. Everything mentioned in this thread works perfectly, just not on my laptop... Thank you very much for posting this. I guess I will just have to use it on any other computer but my own.

**edit** just to be thorough, i was using sandisk 4gb cruzer , gutsy 7.10 32 bit with vgn-sz320p sony vaio laptop and the above mentioned programs.

---

### Post by Belak on 2008-05-19
Well, I'm sorry to hear that it didn't work on your laptop, but I'm glad that I do kinda know what I'm talking about.

Next time, if you post your error code or what's going wrong, it would work better in us helping you with the problem.

---

### Post by yeahrite on 2008-10-28
Hi all (new member), I am a linux newbie learning fast:)
I have BT3 running off a pen/memory stick fine, but at boot I dont get the 'BT3 Graphics mode (Compiz) - Experimental' option? I get the others listed in your example, I'm on a eee pc 900 box on the original xandros distro (though waiting for the eeepc ubuntu to arrive;). Question is do I need it for BT? If so how?
many thanx for any advice
Regards
Jay

---

### Post by Belak on 2008-10-28
> **yeahrite said:**
> Hi all (new member), I am a linux newbie learning fast:)
I have BT3 running off a pen/memory stick fine, but at boot I dont get the 'BT3 Graphics mode (Compiz) - Experimental' option? I get the others listed in your example, I'm on a eee pc 900 box on the original xandros distro (though waiting for the eeepc ubuntu to arrive;). Question is do I need it for BT? If so how?
many thanx for any advice
Regards
Jay

Ok, the Compiz modes are just for eye candy and therefore you have no real need for them at all...

---

### Post by yeahrite on 2008-10-29
many thanx
Jay

---

### Post by blamc on 2009-07-06
This is a great idea,  went through your tutorial and it worked great.  Thanks a bunch.  I decided to try and add some more tools (ubcd) but have not had any success getting it to work properly.  Just wondering if you could help me get started.

---

