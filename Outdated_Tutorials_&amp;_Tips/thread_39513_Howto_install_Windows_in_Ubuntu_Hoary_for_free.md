---
title: "Howto: install Windows in Ubuntu Hoary for free"
date: 2005-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Lunde on 2005-06-05
[SIZE=4]**Howto install Windows in Ubuntu Hoary for free**[/SIZE]

It's not totally free, because you need a Windows Install CD.

From the start, this was in my case: How to Make Photoshop and Dreamweaver work under Ubuntu ..but read on if you need other Windows applications or Even other OS's under Ubuntu.

There are several other solutions out there, it's just a bit difficult to chooce the right one.
In this little howto we will take a brief look at some of the solutions and guide you through how to set up the free emulator that I have tested with win2000 and win98. 



[SIZE=3]**Before we start:** [/SIZE]

**Guest** = Your Operating System installed in the emulator
**Host**  = In this case, Ubuntu Hoary 

Do this at your own risk, there are know problems with different graphic cards, refresh rate and color settings. 
If you notice any flickering on the screen when you change the screen resolution on the guest OS, try to shutdown first the guest, then completely reboot the host. if still it is flickering, there are probably something wrong with your graphic drivers or settings in the Xorg file.

I did this with a Fresh installation of Ubuntu Hoary Hedgehog 5.04 with 2.6.10-5 i386 kernel, Proper Nvidia drivers, Wireless Network and 768mb memory.

Please note that you preferably have some gigabites available while setting this up. I  recommend taking some backups of both the guest and the host while configuring this. 



**First** ...we will take a brief look at what I tried before I ended up with something that worked for me.

**Crossover Office** (Not Free)
Running Windows Programs under Linux, such as Office, Photoshop, Dreamweaver.. and lots more.

Note: Missing functions in Photoshop, unreadable menus.. supports a lot of Windows applications, but not the right for me.

**Win4LinPro** (Not Free)
Windows umulator for Windows2000 and WindowsXP (must be with sp2 or sp1)

Note: I tried this with WinXP, it was far from useable for my purpose, way to slow even with KQemu accelerator) 

**Win4Lin **(Not Free)
Windows umulator for Win95 and Win98, WinME

Note: Needs a custom kernel wich is quite difficult under ubuntu, I have still not tried this, but will soon give it a go.. 

**Qemu with KQemu** (Free)
Emulator for Win95 and Win98, WinME, Win2000, WinXP, Knoppix, lot's and lots of different OS's. 

Note: This is the ONE.. this is what we will go through here. I tried this with Win98, Win2000, Knoppix and will continue to try different OS's here. It is not as fast as VMware with Win2000, but it's a good free alternative.

**VMware Workstation** (Not Free)
Emulator for Windows all and lots of other OS's ...I had some problems with Win98.

Note: VMware is the best solution I have tried, I had a lot of trouble with crashes, screen flickering etc... but after I installed Qemu with KQemu it seems to work fine. I have no idea why and I don't think there are any relations. As long as I don't change screen resolution in the guest it's pretty stable now.



**OK.. Let's start...**

**[SIZE=3]Step 1. RUNNING QEMU WITH WIN98[/SIZE]**
If you are just installing Win98, with the current version (qemu-0.7.0) KQemu will not work anyway, so you don't need to install it. 

Win98 only, Just do: 
$ apt-get install qemu
...and jump to step 2

If you deside to install Qemu with the KQemu accelerator you just need to start win98 with the extra command -no-kqemu , we will get back to this later anyway.



**[SIZE=3]Step 1. RUNNING QEMU WITH KQEMU ACCELERATOR [/SIZE]**

Some of this information I ripped from: Nano Florestan at [http://oui.com.br/n/content.php?article.21](http://oui.com.br/n/content.php?article.21) a lot of the credits should go to him. 

First we need to remove any previously installed Qemu and compile it with Kqemu

**$ sudo apt-get remove qemu**

Go to: [http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html) 
...and download these 2 files:
1) QEMU source code (Not the binary for i386 which I took the first time, silly me)
2) QEMU Accelerator Module

0.7.0 is the current version.

**$ tar zxvf qemu-0.7.0.tar.gz **

The Kqemu shall be unpacked into a subdirectory of the new qemu-0.7.0 directory 

**$ cd qemu-0.7.0**
**$ tar zxvf /location of downloaded files/kqemu-0.6.2-1.tar.gz**

**NOTE: **Some people have reported permission errors during installation, the following command will correct the problem.

**$ sudo chmod -R 775 /path/to/qemu-0.7.0**

You now need to make sure you have some extra packets. First make sure you have the kernel headers installed by: 

**$  uname -r **
..this will output the kernel version

Open Synaptic package manager and search for packages called "linux-headers". Several packages start with this name. Install the one that corresponds to your processor and your kernel version.

Still in Synaptic, choose the package you have just installed, click Properties and go to the "Installed Files" tab. Write down the directory where the files were copied. In my case, they were copied to:  /usr/src/linux-headers-2.6.10-5-386/

**$ gedit configure**

change the: kernel_path="/usr/src/linux-headers-2.6.10-5-386" 

[B]$ sudo apt-get install libsdl1.2-dev
$ sudo apt-get install zlib1g-dev[/B]

Then check that everything is correct with:

**$ ./configure**

If everything is correct and you recieve no errors, proceed with:

**$ make**

Correct output to make will go on and on and output a lot of text...

If you did'nt get any errors you are now ready to install. If you get any errors or this does'nt work at all, make sure you have a gcc compiler in your system.

Now we are ready to install:

**Note:** Please check **AgenT's** suggestion of doing **checkinstall** instead of **make install**: [http://www.ubuntuforums.org/showthread.php?p=200873#post200873](http://www.ubuntuforums.org/showthread.php?p=200873#post200873) 

**$ sudo make install **

If everything went ok, you can now start the qemu with the command

**$ sudo modprobe kqemu**

Then we need to make this start when the computer boots

**$ sudo gedit /etc/init.d/bootmisc.sh**

Add these lines to the end just before "exit;"

[B]# Start Qemu with KQemu accelerator
/sbin/modprobe kqemu
mknod /dev/kqemu c 250 0  # Create the KQEMU device 
chmod 666 /dev/kqemu      # Make it accessible to all users[/B]

[SIZE=3][B]
Step 2. MAKING A VIRITUAL DISK WITH QEMU[/B][/SIZE]
First create a directory for the guest OS's. This should be done as the user you will use while running the guest OS

[B]$ cd /home/your username
$ mkdir Qemu 
$ cd Qemu[/B]

Then we will create the virtual hard drive, in my case for Win98 I used 2 gigabyte and 3,5 gigabyte for Win2000. We set the size with the (amount)M

**$ qemu-img create hd.img 3500M**


[SIZE=3]**Step 3. INSTALLING THE GUEST OS**[/SIZE]

So... we now have the disk and need to install something on it..

first lets hava a look at the options for booting with Qemu
-boot gives the parameter of which device to boot from. 

a = floppy 
d = cdrom 
c = hard drive


-fda /dev/fda 
will tell qemu where to find the floppy drive 
-fda /path/to/your/bootdisk.img
will tell qemu to boot from a bootdisk image. You can download images from [www.bootdisk.com](www.bootdisk.com)

PS: you can download an .exe bootdisk extractor and open it with Archive Manager and extract the bootdisk image


-cdrom /dev/cdrom 
will tell qemu where to find the cdrom drive. 
-cdrom /path/to/your/install_cd.iso
will tell qemu to use an iso instead of your cdrom drive.


-hda /path/to/your/new/viritual/hd.img
Will tell qemu which viritual harddrive to use. you can also use secondary drive with -hdb /path/to/your/new/viritual/secondary/hd.img


So here we go... If we have a bootable install cd and just want to use the cdrom drive, this is how it goes:
**$ qemu -boot d -cdrom /dev/cdrom  -hda hd.img**

If you need to start with different parameters, just modify and add to the end. If you install Win98, dont forget to add -no-kqemu at the end.


When the installation ask you to reboot, change the -boot d flag to -boot c for the virtual hard drive 



[SIZE=3]**Step 4. STARTING THE GUEST OS**[/SIZE]

Well.. we're sort of already there, again it's mostly just to change the -boot flag

**$ qemu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda hd.img -user-net -pci -m 256 -k en**


**Description of other flags used in this startup:**

-k en 
Keybord layout.. works with some languages

-user-net
Lets you connect to the net

-pci -m 256
Amount of memory provided the guest OS

Note: I will not go into details about networking here.. at least not yet. Internet should probably work from the guest without any modifications. To set up shared folders between the guest and the host, a tip is. Install samba, then share the folders with SMB and add the flag -smb /shared/folder to your startup command.



[SIZE=3]**Step 5. PERFORMANCE TWEAKING THE GUEST OS**[/SIZE]

Before you start tweaking the guest OS.. just copy the hd.img

**$ cp hd.img hd.img.backup**

Now find a good performance tweek site on the net for removing all unwanted processes for your OS
Win2000: [http://www.techspot.com/tweaks/win2k_services/print.shtml](http://www.techspot.com/tweaks/win2k_services/print.shtml) 

**EDIT:** Additional information from **sebdah**
For you guys who wants to tweak WinXP: Check [TweakXP.com](http://www.tweakxp.com), it should be everything you need!


[SIZE=3]**Step 6. CREATING A LAUNCER**[/SIZE]

Now finally you may want a launcher for your new OS.. 
Rightclick on the panel where you want to create the launcher and choose:

**Add to Panel > Custom Application Launcher >  **
**Name: **Win2000
**Command: **qemu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda /path/to/your/hd.img -user-net -pci -m 256 -k en
Choose an icon for you new OS

Note: modify the command starter after your needs.



[SIZE=3]**MISC**[/SIZE]

**CHANGING CD'S IN THE GUEST**
Some people have reported problems changing CD's while running the guest OS.
**rcerreto** has posted a solution here:
[http://ubuntuforums.org/showpost.php?p=282975&postcount=256](http://ubuntuforums.org/showpost.php?p=282975&postcount=256)



[SIZE=3]**LINKS TO USEFULL INFORMATION**[/SIZE]

[http://fabrice.bellard.free.fr/qemu/index.html](http://fabrice.bellard.free.fr/qemu/index.html)
[http://fabrice.bellard.free.fr/qemu/qemu-doc.html](http://fabrice.bellard.free.fr/qemu/qemu-doc.html) 
[http://www.debian-administration.org/?article=40](http://www.debian-administration.org/?article=40)
[http://oui.com.br/n/content.php?article.21](http://oui.com.br/n/content.php?article.21)  
[http://www.carlsonhome.net/computer_help_log.php](http://www.carlsonhome.net/computer_help_log.php) 

Free Operating System Zoo
[http://free.oszoo.org/](http://free.oszoo.org/)

Have fun...

 
Please correct me if something is wrong or can be done better.

---

### Post by kingzasz on 2005-06-05
How fast is it?  Would it be faster than using VNC to run windows programs?  Thanks.

---

### Post by Arthemys on 2005-06-05
[QUOTE=kingzasz]How fast is it?  Would it be faster than using VNC to run windows programs?  Thanks.[/QUOTE]
I haven't used this solution yet, but I'd have to assume it'd much faster than any VNC connection. I've run WinXPsp2 inside a VMware session full screen, you almost couldn't tell there was a host OS underneath.

---

### Post by lleberg on 2005-06-05
[QUOTE=Arthemys]I haven't used this solution yet, but I'd have to assume it'd much faster than any VNC connection. I've run WinXPsp2 inside a VMware session full screen, you almost couldn't tell there was a host OS underneath.[/QUOTE]
 One way to get a eindows-cd for free is to order a free 180 day trial CD from microsoft..
You'll never put up with windows for longer than that anyway! :D

---

### Post by 23meg on 2005-06-05
thanks for the detailed howto. i've been meaning to set up qemu for a while, this will perhaps get me going. 

is it possible to set things up so that one can boot into the same installation of windows both natively (with grub) and in a virtualization  / emulation environment such as vmware or qemu, kind of like how things work with wine? (i'm sure the short answer is "no" but.. maybe there's a "but" :) )

---

### Post by AgenT on 2005-06-05
One thing you may want to add. Instead of using "make install", you could use checkinstall (apt-get install checkinstall or use Synaptic). checkinstall is the best way to install compiled programs because it will make and install deb's instead of just installing the program! This means that you will have QEMU installed as if it were installed via apt-get or Synaptic! Neat stuff! To remove all you would have to do is apt-get remove qemu or removie via Synaptic. That is, everything would be done the same way as if you were to install a deb.

Quick rundown for any source code package using configure:
 ```
./configure
make
checkinstall
``` 
In other words, just replace the step "make install" with "checkinstall". That's it!

WARNING: make sure you are not running anything that touches your apt database. This means that you should not have Synaptic open or have apt-get running while using checkinstall. This will screw up checkinstall because it will be unable to install the deb files that it makes since the resources will be used by apt-get/Synaptic.

---

### Post by clarke.rainey on 2005-06-06
Could one use this to run games?.. I have been looking for a way to get away from Cedega without resorting to dual booting... I could live with running windows from ubuntu for when I want to play games...

---

### Post by bored2k on 2005-06-06
[QUOTE=clarke.rainey]Could one use this to run games?.. I have been looking for a way to get away from Cedega without resorting to dual booting... I could live with running windows from ubuntu for when I want to play games...[/QUOTE]
 3D Rendering is not good in emulation..

---

### Post by bored2k on 2005-06-06
[QUOTE=AgenT]One thing you may want to add. Instead of using "make install", you could use checkinstall (apt-get install checkinstall or use Synaptic). checkinstall is the best way to install compiled programs because it will make and install deb's instead of just installing the program! This means that you will have QEMU installed as if it were installed via apt-get or Synaptic! Neat stuff! To remove all you would have to do is apt-get remove qemu or removie via Synaptic. That is, everything would be done the same way as if you were to install a deb.

Quick rundown for any source code package using configure:
 ```
./configure
make
checkinstall
``` 
In other words, just replace the step "make install" with "checkinstall". That's it!

WARNING: make sure you are not running anything that touches your apt database. This means that you should not have Synaptic open or have apt-get running while using checkinstall. This will screw up checkinstall because it will be unable to install the deb files that it makes since the resources will be used by apt-get/Synaptic.[/QUOTE]
 Thanks for the tip ! I did not even know checkinstall existed. Loving it :D

---

### Post by mulino on 2005-06-06
What to prefer, if one has no glue which emulator to use? Why use qemu instead of wine?

---

### Post by benplaut on 2005-06-06
[QUOTE=mulino]What to prefer, if one has no glue which emulator to use? Why use qemu instead of wine?[/QUOTE]

if WINE doesn't support the programs you need to use

---

### Post by Lunde on 2005-06-06
[QUOTE=23meg]thanks for the detailed howto. i've been meaning to set up qemu for a while, this will perhaps get me going. 

is it possible to set things up so that one can boot into the same installation of windows both natively (with grub) and in a virtualization  / emulation environment such as vmware or qemu, kind of like how things work with wine? (i'm sure the short answer is "no" but.. maybe there's a "but" :) )[/QUOTE]

not with grub i think, but maybe if we can figure out how to mount a disk as a RW image, we can then boot up the native installation as -hda /path to image.

[QUOTE=AgenT]One thing you may want to add. Instead of using "make install", you could use checkinstall (apt-get install checkinstall or use Synaptic). checkinstall is the best way to install compiled programs because it will make and install deb's instead of just installing the program! This means that you will have QEMU installed as if it were installed via apt-get or Synaptic! Neat stuff! To remove all you would have to do is apt-get remove qemu or removie via Synaptic. That is, everything would be done the same way as if you were to install a deb.

Quick rundown for any source code package using configure:
 ```
./configure
make
checkinstall
``` 
In other words, just replace the step "make install" with "checkinstall". That's it!

WARNING: make sure you are not running anything that touches your apt database. This means that you should not have Synaptic open or have apt-get running while using checkinstall. This will screw up checkinstall because it will be unable to install the deb files that it makes since the resources will be used by apt-get/Synaptic.[/QUOTE]

Thanks! this looks like a better way of doing it..

[QUOTE=mulino]What to prefer, if one has no glue which emulator to use? Why use qemu instead of wine?[/QUOTE]

VMware is the best I think... Qemu is to me after all I tried, the second best, there is a big difference from a native installation, but as a tool for small applications it's good I did a Photoshop job in Qemu with no problems, it's a bit slow, but better then rebooting. There are other great benefits to Qemu, like the possibuility of running testing servers like a stripped down Slackware with Apache and Mysql or the Breezy Badger Development Release. When I have more time, I will look more into the possibuilities.

...but if you only want a coupple of programs, then WIne or Crossover Office may be your solution

---

### Post by mulino on 2005-06-06
[QUOTE=Lunde]

VMware is the best I think... Qemu is to me after all I tried, the second best, there is a big difference from a native installation, but as a tool for small applications it's good I did a Photoshop job in Qemu with no problems, it's a bit slow, but better then rebooting. There are other great benefits to Qemu, like the possibuility of running testing servers like a stripped down Slackware with Apache and Mysql or the Breezy Badger Development Release. When I have more time, I will look more into the possibuilities.

...but if you only want a coupple of programs, then WIne or Crossover Office may be your solution[/QUOTE]

Thanks for your feedback. I have wine installed and it runs quite fast. Maybe my solution! :mrgreen: I'll give it another try..;)

---

### Post by Lunde on 2005-06-06
[QUOTE=23meg]thanks for the detailed howto. i've been meaning to set up qemu for a while, this will perhaps get me going. 

is it possible to set things up so that one can boot into the same installation of windows both natively (with grub) and in a virtualization  / emulation environment such as vmware or qemu, kind of like how things work with wine? (i'm sure the short answer is "no" but.. maybe there's a "but" :) )[/QUOTE]

I tried something funny, I don't have a Windows native om my PC... But I have a secondary Ubuntu on another hard drive. What I tried was to trick Qemu to think that the drive was an image by: 

**ln -s /dev/hdb /path/to/qemu/ubuntu.img** 
then use the flag **-hda /path/to/qemu/ubuntu.img**

..and it looks like it's reading the disk, The message is:

ata0 master: Qemu HARDDISK ATA-2 Hard-Disk (19595 MBytes) 

Booting from Hard Disk...
Missing operating system_

OK I fully understand why it did'nt boot my ubuntu, the fstab would be wrong, the bootloader is somewhere on my hda, the partitions would probably have wrong names etc... but if it was a Windows on that disk, It may work. This is the closest I can get to testing this. If somebody esle tests this please leave a note here if it works.

**Note: **I dont know what this would do to the file system, I don't think it would do any damage, but just keep it in mind.

---

### Post by scrillamaan on 2005-06-06
Has anyone tried this with XP, its the only windows disk I have handy at the moment. The QEMU site says its experimental, but been tested on version 0.5.5. No word yet on 0.70 it seems. I've seen Qemu running XP on some fedora forums, but I was wondering if anyone has gotten XP running on Ubuntu?

---

### Post by 23meg on 2005-06-06
lunde, that's really inspiring! i'll see if i can take it any further when i have some free time to put into this. 

scrillamaan: i've heard people reporting success with running xp on debian via qemu, so it's highly probable that it's doable on ubuntu as well.

---

### Post by scrillamaan on 2005-06-06
23meg, thanks and I now have something to try tonight. I'll report on my success...or failure. I can't live without paint!  ;-)

---

### Post by abandoned_hussam on 2005-06-06
How can disable networking in qemu?
will it be disabled if I ommit -user-net or do I need to do something else?

---

### Post by crane on 2005-06-06
Just wondering. If for some reason one decodes not to use that OS (guest) can it just be deleted like a folder to remove?

I was also wondering. Would a guest windows system be able to access another partition? I have a windows partition on this computer but if I install like this then could it read the other?

---

### Post by spacemonkey on 2005-06-07
> Just wondering. If for some reason one decodes not to use that OS (guest) can it just be deleted like a folder to remove? 

I'm also wondering the same thing.

Also, checkinstall gave me an error when trying to install the debian package, but qemu seemed to install anyways, so all is well, just no deb package.  Also, would it be possible to mount another partition onto the Qemu dir and store the hd.img there, as I don't have tons of space on my Ubuntu install, but have space left on my hdd to test OSes, but now I can do it without rebooting.  And if I can do this, which I can't see any reason why I couldn't, would it cause any problems once I do it to just move my current hd.img to the new partition?

---

### Post by scrillamaan on 2005-06-07
Well I got XP installed and it was relatively painless. Kudos to you, Lunde! Great guide. I only had to change was ```
**sudo** modprobe kqemu
``` to start qemu.

Thanks again

---

### Post by spacemonkey on 2005-06-07
Any one have any clue how to use qemu to boot a windows install that's already on another hard disk?  Lunde, I tried your method, and it didn't boot.  It said it couldn't open the image.  This would be really great if we could figure out how to do this, because I've only got one windows license, and I'd love to be able to run windows on ubuntu when I need it for certain programs, but I still want to be able to boot into it of necessary.  I clean install is not a problem, it's just the licensing issue....

By the way....great how to, I've been messing with it all night.  I finally get to test out all those OSes I've wanted to try without to much commitment.  Thanks.

---

### Post by Lunde on 2005-06-07
[QUOTE=spacemonkey]Any one have any clue how to use qemu to boot a windows install that's already on another hard disk?  Lunde, I tried your method, and it didn't boot.  It said it couldn't open the image.  This would be really great if we could figure out how to do this, because I've only got one windows license, and I'd love to be able to run windows on ubuntu when I need it for certain programs, but I still want to be able to boot into it of necessary.  I clean install is not a problem, it's just the licensing issue....

By the way....great how to, I've been messing with it all night.  I finally get to test out all those OSes I've wanted to try without to much commitment.  Thanks.[/QUOTE]

Strange Qemu said that it could'nt open the image, because it worked fine for me, or  at least I had it reading the disk. I also had it reading different different partitions.

Did you make sure to give the **ln -s** the ending of **.img** 

Is your disk split into partitions? maybe then you have to symlink **hda1** instead of **hda** ..but still it should at least have read your disk

If it still won't work, I'm sure that even if you just have one license for Windows it's ok to install it twice on the same PC

---

### Post by Lunde on 2005-06-07
[QUOTE=scrillamaan]Has anyone tried this with XP, its the only windows disk I have handy at the moment. The QEMU site says its experimental, but been tested on version 0.5.5. No word yet on 0.70 it seems. I've seen Qemu running XP on some fedora forums, but I was wondering if anyone has gotten XP running on Ubuntu?[/QUOTE]

I tried win4linPro wich also use the KQemu accelerator... works but a bit slow for using it on daily bases. I'm not sure about Qemu, but it would'nt suprise me if it was a lot faster. My Win2000 went completly OK, but it's important to strip all the processes you don't need and get rid of fading menus, heavy background pictures, maybe run without the XP theme.

But.. instead of getting a new windows version, get an VMware Workstation license because that's a good option for running XP.

If you go for trying Qemu with xp, you have to increase the memory flag in the Qemu startup command. It might give you an error, but it will also give you a suggestion of the command to run to increase it.

---

### Post by pdk001 on 2005-06-07
its too long HOWTO to get it for me thoguh, i will follow you step by step

---

### Post by AgenT on 2005-06-07
[QUOTE=scrillamaan]Well I got XP installed and it was relatively painless.[/QUOTE]

Installation is the easy part, my question to you is this: does it run and boot into the desktop? The reason I ask is because mine will not boot to the desktop (the last time I tried at least) because of that stupid activation requirements. No matter what, it always says that the product is not activated properly. How about for you? Can you boot into the desktop fully activated? If so, how did you do it? Also, what kind of version of XP did you use? And was it pure XP or a special OEM version?

---

### Post by spacemonkey on 2005-06-07
lunde, my set it up is like this:

I've got two hard drives, the master has windows installed on one partition, grub installed on the MBR, and two other fat32 partitions just for holding data.  My slave disk has Ubuntu installed.  I tried the symbolic link to both hda1, and just hda, neither worked, and both had the .img on the end.  It just said it couldn't open the disk image.  Didn't even begin to read from the disk.

---

### Post by Lunde on 2005-06-07
[QUOTE=spacemonkey]lunde, my set it up is like this:

I've got two hard drives, the master has windows installed on one partition, grub installed on the MBR, and two other fat32 partitions just for holding data.  My slave disk has Ubuntu installed.  I tried the symbolic link to both hda1, and just hda, neither worked, and both had the .img on the end.  It just said it couldn't open the disk image.  Didn't even begin to read from the disk.[/QUOTE]

I've located your problem.. you have to **sudo qemu.....** Please keep me noticed, I'm very excited about if this works.

---

### Post by scrillamaan on 2005-06-07
[QUOTE=AgenT]Installation is the easy part, my question to you is this: does it run and boot into the desktop? The reason I ask is because mine will not boot to the desktop (the last time I tried at least) because of that stupid activation requirements. No matter what, it always says that the product is not activated properly. How about for you? Can you boot into the desktop fully activated? If so, how did you do it? Also, what kind of version of XP did you use? And was it pure XP or a special OEM version?[/QUOTE]

Yes I can boot to the desktop fine, but I'm using XP Pro Corporate so activation is not really an issue. I guess thats the difference.

---

### Post by Lunde on 2005-06-07
[QUOTE=spacemonkey]lunde, my set it up is like this:

I've got two hard drives, the master has windows installed on one partition, grub installed on the MBR, and two other fat32 partitions just for holding data.  My slave disk has Ubuntu installed.  I tried the symbolic link to both hda1, and just hda, neither worked, and both had the .img on the end.  It just said it couldn't open the disk image.  Didn't even begin to read from the disk.[/QUOTE]

[QUOTE=Lunde]I've located your problem.. you have to **sudo qemu.....** Please keep me noticed, I'm very excited about if this works.[/QUOTE]

I have to warn you that, if this works, you will get a lot of new hardware found because Qemu provide virtual devices. Make a backup of your system configuration before trying this. 

Maybe there is a soulution in your Windows to create different hardware profiles so that you can choose between qemu boot and native boot.

---

### Post by spacemonkey on 2005-06-07
I'll have to make the attempt... Although, I managed to get windows activated without any legal troubles (atleast not yet).  I don't have time right now to make the backups and try it, I'll let you know as soon as I try it though.

Also, I noticed something strange when moving the .img files to a different partition like I talked about earlier.  Originally, on the first ext3 partition they were on, I made a 3.5 gig image, but it didn't actually take up that amount of space on the disk, it only took up however much space was installed onto the image.  After moving them to another ext3 partition however, they actually take up the amount of space that is reserved for them.  So my 3.5 gig breezy .img actually takes up 3.5 gigs, when I'm not using near that much.  Does anyone know how to fix this without deleting the images and creating new ones on the new partition?

---

### Post by AgenT on 2005-06-07
[QUOTE=spacemonkey]I'll have to make the attempt... Although, I managed to get windows activated without any legal troubles (atleast not yet). [/QUOTE]

How did you get around the activation problem? How did you activate it?

---

### Post by spacemonkey on 2005-06-07
Well I thought it would give me troubles, since that license had already been installed, but I just went ahead and tried the online activation anyways, and it went through just fine.  I'm assuming that it checks the license to the computer, and since it's still installed on the same computer, it's ok to have multiple installations.

---

### Post by Lunde on 2005-06-07
[QUOTE=spacemonkey]
Also, I noticed something strange when moving the .img files to a different partition like I talked about earlier.  Originally, on the first ext3 partition they were on, I made a 3.5 gig image, but it didn't actually take up that amount of space on the disk, it only took up however much space was installed onto the image.  After moving them to another ext3 partition however, they actually take up the amount of space that is reserved for them.  So my 3.5 gig breezy .img actually takes up 3.5 gigs, when I'm not using near that much.  Does anyone know how to fix this without deleting the images and creating new ones on the new partition?[/QUOTE]

Only way I can think of is to create a new growable image boot from a liveCD or a third image with a good fdisk solution then do a disk copy. (-hda -hdb -cdrom or -hdc)  

There is for the future also another way to create images:

$ dd of=hd.img bs=1024 seek=2000000 count=0 
(Makes a 2gig disk... a bit less actually)

I've moved some of my images from ext3 to ext3 and they did'nt grow, but I think I created them with the above command

---

### Post by AgenT on 2005-06-07
[QUOTE=spacemonkey]Well I thought it would give me troubles, since that license had already been installed, but I just went ahead and tried the online activation anyways, and it went through just fine. I'm assuming that it checks the license to the computer, and since it's still installed on the same computer, it's ok to have multiple installations.[/QUOTE]

Mine will not even boot into the desktop so I cannot even "activate" it. It refuses to log in stating that it is not activated. And the activation does not work in safe mode for whatever strange reason. Ideas?

EDIT:
 Just read your previous posts and it seems that you are not actually installing XP from scratch in a QEMU img file, correct? Your XP was already installed on another partition and you are just using that in QEMU? That would of course explain it. :) 

From what I understand, XP will *not* see your original hardware, but instead QEMU emulation hardware. This means that the activation and the XP install, will think it is being run on a different machine.

---

### Post by Lunde on 2005-06-07
Something very intresting came up in all these replies above ..but it started to get a bit messy so I sum up here.

If **Qemu** is started as **root** or with **sudo**, it's possible to use a disk or a partition as a harddrive by tricking Qemu to belive that a symlink is an image. 

ln -s /dev/hdb /path/to/qemu/symlink.img
then use the flag -hdb /path/to/qemu/symlink.img

So in theory it's possibe to boot into the installed OS both nativly through grub and by booting it in Ubuntu with the **qemu** command.

I dont have the possibuility to try this, because I only have linux on both my drives and no spare primary partition, but if anybody try, please post here the result negative or positive.

There are some issues with doing this, I'll list the ones I can think of here:

1) Qemu emulates hardware so there will be difference in the hardware configuration

2) If you link up a linux partition in Windows with -hdb Windows diskmanager will want to format it to use it.

3) I think it can create problems if you should be able to boot your own system twise at the same time

4) there is probably more, so if you can think of anything, please post it here

I suggest to do backup before trying this!

---

### Post by spacemonkey on 2005-06-08
AgenT, no, I am running a clean install using Qemu, the discussion about using Qemu to run a previously installed version from hard disk is something I plan on trying, but have not yet done.  I have successfully installed, booted, and activated a copy if XP all with Qemu, so honestly I have no clue why yours doesn't work.  Maybe try reinstalling, perhaps something went wrong.  Also, I'm running XP pro, so I'm not sure if that would matter or not.

Lunde, thanks for the info, I plan on testing this as soon as I get the chance.  I need to back up everything and what not before I make the attempt.

---

### Post by bored2k on 2005-06-08
What's the speed of this emulation comparing to the one from VMWare ?

---

### Post by scrillamaan on 2005-06-08
Well, I just got sound working in XP. 

Qemu emulates a sound blaster 16 sound card and I manually installed this new device through the windows add hardware wizard. I followed [this guide](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=audio) to get multiple sounds working. Then I ran Qemu with this option ```
-enable-audio
``` Hope it helps.

[EDIT]
Qemu seems to continuously use the ALSA driver because while it is running, I cannot play any sounds in hoary due to the ALSA driver being in use.

...hopefully there is a solution
[/EDIT]

---

### Post by spacemonkey on 2005-06-08
I was just about to ask about getting sound to work, thanks.  Also, I'm running windows xp pro, and before I installed all the updates, it only took up about 2 gigs, now, after installing all the updates, including SP2, it takes up almost 4 gigs!!  I know I didn't download that much in updates.  Any tips for freeing up some space.

One more thing, anyone noticed that when the guest OS does anything that uses up more than slightly above idle amount of processing time, the processor readings on Ubuntu spike to 99% constantly, for instance, installing windows updates...which isn't to processor intensive.


EDIT:
About the CPU usage thing, I solved that by just booting with more ram, I didn't realize the defualt value was only 128.  Trying to run windows xp with only 128 mb of ram is no fun.

EDIT #2:
I I freed up lots of space by removing some installed components that are useless for a Qemu install suck as outlook express, media player, messenger...all that stuff, since I've got the same thing installed on ubuntu.  Check out [http://www.tweakxp.com/](http://www.tweakxp.com/) for some great tips to make everything run faster and save space.

---

### Post by Lunde on 2005-06-09
[QUOTE=scrillamaan]Well, I just got sound working in XP. 

Qemu emulates a sound blaster 16 sound card and I manually installed this new device through the windows add hardware wizard. I followed [this guide](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=audio) to get multiple sounds working. Then I ran Qemu with this option ```
-enable-audio
``` Hope it helps.

[EDIT]
Qemu seems to continuously use the ALSA driver because while it is running, I cannot play any sounds in hoary due to the ALSA driver being in use.

...hopefully there is a solution
[/EDIT][/QUOTE]

Personally I would'nt prefere sound in Qemu it slows it down a little. Anyway... Even i Ubuntu fresh install it is no possibuility to hear multiple sounds. So if you start xmms and Totem, only the first started program will hav access to sound. There is a workaround here: [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

### Post by Lunde on 2005-06-09
> 
EDIT:
About the CPU usage thing, I solved that by just booting with more ram, I didn't realize the defualt value was only 128.  Trying to run windows xp with only 128 mb of ram is no fun.

EDIT #2:
I I freed up lots of space by removing some installed components that are useless for a Qemu install suck as outlook express, media player, messenger...all that stuff, since I've got the same thing installed on ubuntu.  Check out [http://www.tweakxp.com/](http://www.tweakxp.com/) for some great tips to make everything run faster and save space.

> 
Step 4. STARTING THE GUEST OS

Well.. we're sort of already there, again it's mostly just to change the -boot flag

$ qemu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda hd.img -user-net -pci -m 256 -k en


You can also provide the geust more memory by remouting the virtual memory, how to do this is written in the terminal if you type ex: -pci -m 384

---

### Post by msgyrd on 2005-06-09
[QUOTE=Lunde]not with grub i think, but maybe if we can figure out how to mount a disk as a RW image, we can then boot up the native installation as -hda /path to image.
[/QUOTE]

Actually, this is quite possible, but from a different aproach.  I know you can install windows like to plan to dual boot, and then load the windows partition in vmware.

I don't remember any references to it anymore, but I had VMware running windows off it's own seperate hard drive in the Hoary prerelease a few months back, so it's doable.  Also, if you are willing to repartition, running the guest OS off a real disk instead of a disk image increases performance a bit.

Sorry I couldn't offer any helpful links.

---

### Post by Lunde on 2005-06-09
[QUOTE=msgyrd]Actually, this is quite possible, but from a different aproach.  I know you can install windows like to plan to dual boot, and then load the windows partition in vmware.

I don't remember any references to it anymore, but I had VMware running windows off it's own seperate hard drive in the Hoary prerelease a few months back, so it's doable.  Also, if you are willing to repartition, running the guest OS off a real disk instead of a disk image increases performance a bit.

Sorry I couldn't offer any helpful links.[/QUOTE]

I think this is the solution for Qemu: [http://www.ubuntuforums.org/showthread.php?p=203652#post203652](http://www.ubuntuforums.org/showthread.php?p=203652#post203652) 

By tricking Qemu to belive that a symlink is an image, must be done as root

Maybe this works in VMware too

---

### Post by RaymondQE on 2005-06-10
Great guide Lunde!

A note for the win98 installation (step 3):

If you plan on installing windows 98 SE from the cdrom, you first must boot up a win98se floppy bootdisk using qemu, run fdisk --> creating your partition on the hard disc image,  and then run the command 'format c: /s'.  After that, you can boot up the cdrom using qemu and run the windows installer off of the cdrom.  It installed fine for me, but I am still having problems getting the desktop to run more than 16 colors :-x 

Going to try to install the win9x nvidia drivers to see if that fixes it.

---

### Post by Lunde on 2005-06-10
[QUOTE=RaymondQE]Great guide Lunde!

A note for the win98 installation (step 3):

If you plan on installing windows 98 SE from the cdrom, you first must boot up a win98se floppy bootdisk using qemu, run fdisk --> creating your partition on the hard disc image,  and then run the command 'format c: /s'.  After that, you can boot up the cdrom using qemu and run the windows installer off of the cdrom.  It installed fine for me, but I am still having problems getting the desktop to run more than 16 colors :-x 

Going to try to install the win9x nvidia drivers to see if that fixes it.[/QUOTE]

Thanks!

Strange that you only can see 16 colors. I'm not sure if it will help installing the nvidia drivers, Qemu is simulating the hardware and it simulates a Cirrus Logic SVGA GD5446 Video card: [http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC27](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC27) 

Win98 should have a driver for this. I'm running win98 myself and I have no problems. Check if windows are using the right drivers for Cirrus. Are you running this on a PC?

---

### Post by RaymondQE on 2005-06-10
I checked in my system properties and the display adapter was indeed the cirrus 5446 PCI.  It is only when I change the display mode to 256 colors or higher do I get a screwed up screen.

screenshot:
[http://www.tc.umn.edu/~ouch0004/screenshots/Screenshot.png](http://www.tc.umn.edu/~ouch0004/screenshots/Screenshot.png)

I am running qemu on a pc, using a geforce4 mx.

The booting command that I use is:
"qemu -boot c -hda hd.img -pci -m 256"

---

### Post by Lunde on 2005-06-10
[QUOTE=RaymondQE]I checked in my system properties and the display adapter was indeed the cirrus 5446 PCI.  It is only when I change the display mode to 256 colors or higher do I get a screwed up screen.

screenshot:
[http://www.tc.umn.edu/~ouch0004/screenshots/Screenshot.png](http://www.tc.umn.edu/~ouch0004/screenshots/Screenshot.png)

I am running qemu on a pc, using a geforce4 mx.

The booting command that I use is:
"qemu -boot c -hda hd.img -pci -m 256"[/QUOTE]

OK I think your problem is not in Qemu, but in the linux drivers. It might be the change in the screen that triggers the error on your screen not the setting itself.  

You can try to work around this problem by setting the colordept in Ubuntu to 16bit.. It works fine for me in 24bit, but I have some problems changing the screen resolution in the guest OS, my screen then flickers and I have to do a hard reboot in linux. But when I start up again everything is fine.

Option 1: Try checking that your linux screendrivers are ok, temporarly change the colordept in ubuntu and if it works fine changing the resolution in the guest then set the ubuntu color dept back.

Option 2: is to accept the new settings in the guest even tho it might look wrong, then shutdown the guest, and do a full reboot in ubuntu. Do a backup first by simply making a copy of your hd.img

Also, did you install the KQemu? if so you need to turn that off in the startup options by -no-kqemu

Hope this helps

---

### Post by AgenT on 2005-06-10
[QUOTE=scrillamaan]Well, I just got sound working in XP. 

Qemu emulates a sound blaster 16 sound card and I manually installed this new device through the windows add hardware wizard. I followed [this guide]("http://www.ubuntuforums.org/showthread.php?t=32063&highlight=audio") to get multiple sounds working. Then I ran Qemu with this option ```
-enable-audio
``` Hope it helps.
[/QUOTE]

This does not seem to work for me. If I try to install SB 16 I get a message that the device is not working properly. Also, there seem to be sound devices already present, yet none of the sound options are available and the sound control panel widget says that no sound card is available. Anyone have any ideas?

Here are the *working* audio devices listed:
Audio Codecs
Legacy Audio Drivers
Media Control Devices (this maybe for video)
Video Codecs

Sound Blaster 16 or AWE32 or compatible (WDM) is listed but does not work.

---

### Post by Lunde on 2005-06-10
[QUOTE=AgenT]This does not seem to work for me. If I try to install SB 16 I get a message that the device is not working properly. Also, there seem to be sound devices already present, yet none of the sound options are available and the sound control panel widget says that no sound card is available. Anyone have any ideas?

Here are the *working* audio devices listed:
Audio Codecs
Legacy Audio Drivers
Media Control Devices (this maybe for video)
Video Codecs

Sound Blaster 16 or AWE32 or compatible (WDM) is listed but does not work.[/QUOTE]

Qemu emulates the SB16 card because windows recognices this device and install the correct drivers itself. Maybe there is a problem with some early win95 I don't know.

I think your problem is Ubuntu not supporting multiple sounds and therefor can not play sound in Windows.

I think the best thing to do is to delete the drivers you tried to install, then reboot and windows will install the correct drivers itself. 

Then configure Ubuntu to be able to play multiple soumds at the same time. Guide: [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

Hope this helps

---

### Post by AgenT on 2005-06-10
[QUOTE=Lunde]Qemu emulates the SB16 card because windows recognices this device and install the correct drivers itself. Maybe there is a problem with some early win95 I don't know.

I think your problem is Ubuntu not supporting multiple sounds and therefor can not play sound in Windows.

I think the best thing to do is to delete the drivers you tried to install, then reboot and windows will install the correct drivers itself. 

Then configure Ubuntu to be able to play multiple soumds at the same time. Guide: [http://www.ubuntuforums.org/showthread.php?t=32063]("http://www.ubuntuforums.org/showthread.php?t=32063")

Hope this helps[/QUOTE]

Sorry, I forgot to mention that I was using XP. Also, it is not a Ubuntu problem per-se because my problem is that Windows itself does not recognize the QEMU sound device (emulator). Rebooting and deleting the SB 16 does not help. Windows itself shows no sound card present in it's sound device widget (in control panel). Hardware detection says all current devices are installed. My problem is actually getting XP to ***recognize* **the SB 16.

---

### Post by Lunde on 2005-06-10
[QUOTE=AgenT]Sorry, I forgot to mention that I was using XP. Also, it is not a Ubuntu problem per-se because my problem is that Windows itself does not recognize the QEMU sound device (emulator). Rebooting and deleting the SB 16 does not help. Windows itself shows no sound card present in it's sound device widget (in control panel). Hardware detection says all current devices are installed. My problem is actually getting XP to ***recognize* **the SB 16.[/QUOTE]

I dont know if this has something to do with your problem, I'm just trying to see if anybody else had sound trouble in XP. Worth having a look even tho its for 0.6.2:
[http://lists.gnu.org/archive/html/qemu-devel/2005-02/msg00330.html](http://lists.gnu.org/archive/html/qemu-devel/2005-02/msg00330.html)

---

### Post by AgenT on 2005-06-10
I finally have XP recognizing the sound card. Solution? Sort of simple (but odd):
1. install SB 16 driver and if it is disabled due to "problems" go on to 2
2. shutdown XP and QEMU
3. start XP without -enable-sound
4. shutdown XP and QEMU
5. start XP with -enable-sound

That did it for me. Strange because installing and reinstalling SB 16 did nothing but -enable-sound and restarting did. Maybe XP was not smart enough to realize that the hardware was installed until after the drivers are loaded and the hardware is "restarted". Bah. 

Now all there is for me to do is actually getting sound to go from XP and into Ubuntu ;)

QUICK QEMU HINT: the -snapshot flag is your friend. This will delete all changes made to your img after you quit QEMU *unless* you specifically invoke "commit" in the QEMU console which saves your progress. Good for debuging and you do not have to worry about breaking your system :)

---

### Post by AgenT on 2005-06-10
**SOUND SOLUTION**
(not perfect however)

There are two routes in Ubuntu Hoary that one can take to get the sound working after the OS (in this case, XP) recognizes the sound card that QEMU provides.
[i]
METHOD 1[/i]
The first one is to kill esd when using QEMU. This can be done, for example, by using the command
 ```
killall esd
``` 
Then one must start QEMU with at least these "options":
 ```
QEMU_AUDIO_DRV="oss" qemu -enable-audio
``` 
Note that one may replace oss with sdl (on this setup, both work). This way of using QEMU will make it so that no other program from GNOME will be able to use the sound card. This may be a bad thing for some.

When done, type this to get your GNOME sound back:
 ```
esd -nobeeps &
``` 

*METHOD 2*
This one will not kill esd but will require a lot more CPU cycles. You will need esddsp by installing esound-clients like so:
 ```
apt-get install esound-clients
``` 
Now one must start QEMU with at least these "options":
 ```
QEMU_AUDIO_DRV="sdl" esddsp -m qemu -enable-audio
``` 
Again, sdl may be replaced with oss, but only sdl works on this machine. Note the -m option. This is required on this machine. -m enables sound mixer.

esddsp is a real resource hog so this option may not work for everyone.

Fun launcher script code for QEMU for method (1):
```
killall esd && <your qemu command with all options> && esd -nobeeps &
``` (replace <your qemu...> with your qemu string (duh!)

QUICK QEMU TIP: Use the savevm and loadvm options in QEMU if you do not want to boot/shutdown! Amazing time saver when you have to test something that requires QEMU to be shutdown and restarted over-and-over-and-over. savevm saves your current state, loadvm loads it. If you need to test some program (a sound file playing for example) just save right before you open up the file then you can always load up right to that spot! No booting or waiting!

---

### Post by Lunde on 2005-06-11
For those of you trying to dual boot Windows inside Qemu and navitivly through a bootloader, here is how it's done with VMware 4.5, I guess the issues are the same.

[http://www.vmware.com/support/ws45/doc/disks_dualboot_ws.html](http://www.vmware.com/support/ws45/doc/disks_dualboot_ws.html)


And here is how it's done with VMware in Gentoo:

[http://forums.gentoo.org/viewtopic-t-246371-highlight-ntfs%20vmware.html](http://forums.gentoo.org/viewtopic-t-246371-highlight-ntfs%20vmware.html)

These links also have a look at the windows configuration with multiple hardware profiles.

---

### Post by BerryB on 2005-06-11
I don't know if this question belongs here, but I was wondering: Is it faster to use QEMU or WINE. And can I use my already installed dual boot windows 2000, so that if I ever boot windows again, all things are the same (and I don't have to use my Linux space)

---

### Post by Lunde on 2005-06-11
[QUOTE=BerryB]I don't know if this question belongs here, but I was wondering: Is it faster to use QEMU or WINE. And can I use my already installed dual boot windows 2000, so that if I ever boot windows again, all things are the same (and I don't have to use my Linux space)[/QUOTE]

Wine is something different. I don't use wine myself because I need applications that are not supprted in Wine. 

As I wrote in some earlier posts in this tread, there are issues with using your native windows. Nobody here have tried it yet, I don't use windows other then in emulators and don't have the partition to try, but I belive it's possible.

In my last post here are links to descriptions and solutions for these issues in VMware and this should be read before trying this with Qemu. 

The reason for these issues are: the hardware emulated by Qemu are not the same as the hardware in your PC and therefor you need to set up different hardware profiles in Windows.

Somebody here was trying this, but we hav'nt heard from him for a while now and I'm getting a bit nervous that he crashed his whole system.. hope not

---

### Post by iammike on 2005-06-11
Ok, having some compiling problems here and don't know where to go.

Here are the results of a ./configure

```
iammike@IAMMIKE-01:~/Desktop/qemu/qemu-0.7.0$ ./configure
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/iammike/Desktop/qemu/qemu-0.7.0
C compiler        gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu
gprof enabled     no
static build      no
SDL support       yes
SDL static link   no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers-2.6.10-5-386
kbuild type       2.6

```

This is what happens when I try to run a make on it...

```
iammike@IAMMIKE-01:~/Desktop/qemu/qemu-0.7.0$ make
for d in i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu; do \
make -C $d all || exit 1 ; \
        done
make[1]: Entering directory `/home/iammike/Desktop/qemu/qemu-0.7.0/i386-user'
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/iammike/Desktop/qemu/qemu-0.7.0/target-i386 -I/home/iammike/Desktop/qemu/qemu-0.7.0 -I/home/iammike/Desktop/qemu/qemu-0.7.0/linux-user -I/home/iammike/Desktop/qemu/qemu-0.7.0/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/iammike/Desktop/qemu/qemu-0.7.0/fpu -I/home/iammike/Desktop/qemu/qemu-0.7.0/slirp -c -o translate-op.o /home/iammike/Desktop/qemu/qemu-0.7.0/translate-op.c
/home/iammike/Desktop/qemu/qemu-0.7.0/translate-op.c: In function `dyngen_code':/home/iammike/Desktop/qemu/qemu-0.7.0/translate-op.c:1358: error: syntax error at end of input
make[1]: *** [translate-op.o] Error 1
make[1]: Leaving directory `/home/iammike/Desktop/qemu/qemu-0.7.0/i386-user'
make: *** [all] Error 1
```

I'm lost and would love a pointer or 2 here...I don't compile much so I'm low on knowledge there.

---

### Post by Lunde on 2005-06-11
Can you open the **configure** file in a text editor and post the lines here that looks like this:

  if test '!' -d "$kernel_path/include" ; then  
      kernel_path="/usr/src/linux-headers-2.6.10-5-686" 
      if test '!' -d "$kernel_path/include" ; then  
          echo "Could not find kernel includes in /lib/modules or /usr/src/linux - cannot build the kqemu module" 
          kqemu="no" 
      fi 
  fi

And also, can you in terminal write

**$ uname -r**

and post the output here?

---

### Post by spacemonkey on 2005-06-11
Lunde, if you're referring to me about the person that was trying it, no worries, I haven't crashed anything....yet.  I still haven't gotten the chance to try it, as I've been busy with some other things, like classes and what not.  I'm going to give those two web pages you posted a quick read and see if I can't work up the courage to give it a shot.

EDIT:

Ok, I did the reading real quick, most of it is vmware specific, but I imagine the basic idea is the same.  Basically, I need to set up a new hardware profile on a host boot of windows, then create a symlink from the winxp drive to a .img file.  Then boot Qemu (with sudo this time).  I've never used hardware profiles in windows, so I don't know, but I assume I'll be asked at boot which profile I want to use, correct?  I really wish I could get my returned dvd burner back from newegg so I can make the appropriate back ups.  I suppose I could tar them and move them to my server.  I'll try this tonight and let everyone know how it went.

---

### Post by iammike on 2005-06-11
In the configure file...

```
# find the kernel path
if test -z "$kernel_path" ; then
kernel_version=`uname -r`
kernel_path="/lib/modules/$kernel_version/build"
if test '!' -d "$kernel_path/include" ; then
    kernel_path="/usr/src/linux"
    if test '!' -d "$kernel_path/include" ; then
        echo "Could not find kernel includes in /lib/modules or /usr/src/linux - cannot build the kqemu module"
        kqemu="no"
    fi
fi
```

Output from uname -r

```
iammike@IAMMIKE-01:~/Desktop/qemu/qemu-0.7.0$ uname -r
2.6.10-5-386
```

Does that help?

---

### Post by spacemonkey on 2005-06-11
I tried booting from an XP install on a harddisk, and here's what happened:

My drive set up is like this:
hda contains 3 partitions, hda1 = windows installation, hda2 and hda3, fat32 for storing data
hdb contains ubuntu and a few other partitions for data. 
Grub is installed on the MBR on hda

First I made the sym link to /dev/hda1, and nothing happened.  It said it was booting from harddisk like it always does when you boot Qemu, and just sat there.  Nothing happened.  So I made the sym link to /dev/hda, and it said:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21


Any suggestions on what to try from here?


UPDATE:

The Grub thing was a stupid error on my part.  The /boot dir is on hdb, so what I did was make another sym link to /dev/hdb, and boot qemu with -hda and -hdb, and I got to grub, then I booted windows, and it asked me which profile.  I selected the one I wanted to use.  Then it froze on the progress bar.

---

### Post by Lunde on 2005-06-12
[QUOTE=iammike]In the configure file...

```
# find the kernel path
if test -z "$kernel_path" ; then
kernel_version=`uname -r`
kernel_path="/lib/modules/$kernel_version/build"
if test '!' -d "$kernel_path/include" ; then
    kernel_path="/usr/src/linux"
    if test '!' -d "$kernel_path/include" ; then
        echo "Could not find kernel includes in /lib/modules or /usr/src/linux - cannot build the kqemu module"
        kqemu="no"
    fi
fi
```

Output from uname -r

```
iammike@IAMMIKE-01:~/Desktop/qemu/qemu-0.7.0$ uname -r
2.6.10-5-386
```

Does that help?[/QUOTE]
 OK..I've been twisting my head, it looks like you do everything correct, but you get a syntax error. this meens that there is a code error in the install files or in one of the modules needed.

Maybe there are something wrong with file permissions, or somthing went wrong unpacking the files. I suggest you unpack everything again. 

first check by opening **symnaptic** that there are no broken packages

[B]$ sudo apt-get install linux-headers-2.6.10-5-386
$ sudo apt-get install make
$ sudo apt-get install gcc
$ sudo apt-get install libsdl1.2-dev
$ sudo apt-get install zlib1g-dev[/B]

Note: Don't do the short version in one line, so you clearly see if there are any errors. Most likely it's just going to tell you that they are already installed, but just to make sure

Then change this line in the  configure section you sent me to: 

     kernel_path="/usr/src/linux-headers-2.6.10-5-386" 

and try agian.

..if this dont work.. I suggest you **sudo** the unpacking to **/tmp** and install as root with **sudo**. But if you do this I suggest you use the **checkinstall** described in: [http://www.ubuntuforums.org/showthread.php?p=200873#post200873](http://www.ubuntuforums.org/showthread.php?p=200873#post200873) so that you can uninstall through **symnaptic**, actually you should do this in both cases.

Hope this helps

---

### Post by Lunde on 2005-06-12
[QUOTE=spacemonkey]
The Grub thing was a stupid error on my part.  The /boot dir is on hdb, so what I did was make another sym link to /dev/hdb, and boot qemu with -hda and -hdb, and I got to grub, then I booted windows, and it asked me which profile.  I selected the one I wanted to use.  Then it froze on the progress bar.[/QUOTE]

Hmm.. well at least it tries to boot. Good news! 

Can you boot in Safemode?
Are you able to boot in command promt?

Maybe F8 works for boot options?

---

### Post by spacemonkey on 2005-06-12
already tried safe mode, same thing, only it shows what it's doing as it boots...the problem is it freezes when it's loading all the drivers, and not a specific one either.  I tried booting into my "guest" profile on the actual machine and disabling all the hardware, then booting from Qemu, but I still get the same thing.  "Safe Mode with Command Prompt" results in the same thing.

---

### Post by Lunde on 2005-06-12
[QUOTE=spacemonkey]already tried safe mode, same thing, only it shows what it's doing as it boots...the problem is it freezes when it's loading all the drivers, and not a specific one either.  I tried booting into my "guest" profile on the actual machine and disabling all the hardware, then booting from Qemu, but I still get the same thing.  "Safe Mode with Command Prompt" results in the same thing.[/QUOTE]
 What about -no-kqemu ?

---

### Post by spacemonkey on 2005-06-12
no change using -no-kqemu, any other suggestions?

---

### Post by tkiesel on 2005-06-12
This has been an absolutely amazing thread to read. it has my wife on the cusp of using Ubuntu. Photoshop is her deal-breaker app, and Wine has some serious issues with some fine-grained scheduling in the Photoshop UI that make her brushes all but useless.

She's got a useable install of Windows Xp through Qemu/Kqemu thanks to all of the fine people in this thread. The only isse we face now is getting a chunk of hard drive space that the guest OS (Windows Xp) and the host OS (Ubuntu) can write to.

We've tried symlinking to the FAT32 partition that she stores her images on, but Windows saw it as an unformatted drive. I'm hesitant to give formatting a go, because I don't know what would happen to her data. ;)

I've tried the "-smb <dir>" swtich for Qemu, which is supposed to give the guest OS access to <dir>.  The IP address that the manpage claimed would be available wasn't ping-able by Windows.  Odd.

Has anyone had luck with either the -smb switch or getting the guest OS and host OS to simultaneously access a drive/partition?

Amazing work, all. And an amazing program!

---

### Post by iammike on 2005-06-12
[QUOTE=Lunde]OK..I've been twisting my head, it looks like you do everything correct, but you get a syntax error. this meens that there is a code error in the install files or in one of the modules needed.

Maybe there are something wrong with file permissions, or somthing went wrong unpacking the files. I suggest you unpack everything again. 

first check by opening **symnaptic** that there are no broken packages

[B]$ sudo apt-get install linux-headers-2.6.10-5-386
$ sudo apt-get install make
$ sudo apt-get install gcc
$ sudo apt-get install libsdl1.2-dev
$ sudo apt-get install zlib1g-dev[/B]

Note: Don't do the short version in one line, so you clearly see if there are any errors. Most likely it's just going to tell you that they are already installed, but just to make sure

Then change this line in the  configure section you sent me to: 

     kernel_path="/usr/src/linux-headers-2.6.10-5-386" 

and try agian.

..if this dont work.. I suggest you **sudo** the unpacking to **/tmp** and install as root with **sudo**. But if you do this I suggest you use the **checkinstall** described in: [http://www.ubuntuforums.org/showthread.php?p=200873#post200873](http://www.ubuntuforums.org/showthread.php?p=200873#post200873) so that you can uninstall through **symnaptic**, actually you should do this in both cases.

Hope this helps[/QUOTE]
 Thanks, that seems to have been it.  I unpacked it and started over again and it's compiling as we speak.  I just hope it doesn't fail after I submit this post....that would be embarassing.  haha

EDIT:  Well, no error compiling but now an error trying to install the debian package.  I received the error while checkinstall tried to install the package and also when I did a sudo dpkg -i....here is the output.

```
iammike@IAMMIKE-01:~/Desktop/qemu-0.7.0$ sudo dpkg -i qemu-0.7.0_0.7.0-1_i386.deb
(Reading database ... 100486 files and directories currently installed.)
Unpacking qemu-0.7.0 (from qemu-0.7.0_0.7.0-1_i386.deb) ...
dpkg: error processing qemu-0.7.0_0.7.0-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.10-5-386/modules.alias', which is also in package linux-image-2.6.10-5-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 qemu-0.7.0_0.7.0-1_i386.deb
```

---

### Post by KLineD on 2005-06-12
[QUOTE=spacemonkey]I tried booting from an XP install on a harddisk, and here's what happened:

My drive set up is like this:
hda contains 3 partitions, hda1 = windows installation, hda2 and hda3, fat32 for storing data
hdb contains ubuntu and a few other partitions for data. 
Grub is installed on the MBR on hda

First I made the sym link to /dev/hda1, and nothing happened.  It said it was booting from harddisk like it always does when you boot Qemu, and just sat there.  Nothing happened.  So I made the sym link to /dev/hda, and it said:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21


Any suggestions on what to try from here?


UPDATE:

The Grub thing was a stupid error on my part.  The /boot dir is on hdb, so what I did was make another sym link to /dev/hdb, and boot qemu with -hda and -hdb, and I got to grub, then I booted windows, and it asked me which profile.  I selected the one I wanted to use.  Then it froze on the progress bar.[/QUOTE]

Weird, I'm trying exactly the same but I get different results.
I have Windows XP installed in /dev/hda1, so I made the link to /dev/hda because that's where grub is.

starting qemu with:
```
sudo qemu -boot c -hda /home/cesar/qemu/win.iso
```
gets me to the grub screen where I select Windows XP (already setup the hardware profiles) but when it tries to boot windows and grub says something about chainloader and stuff (just before the winxp logo and progressbar) qemu just spits some colorized garbage to the screen and nothing happens. I already tried with -no-kqemu also...

---

### Post by spacemonkey on 2005-06-12
So you don't even get to the hardware profile selection screen?

---

### Post by KLineD on 2005-06-12
Unfortunately not. But I really don't know why since the specs posted by you are pretty much the same as me.

---

### Post by Lunde on 2005-06-13
[QUOTE=tkiesel]
I've tried the "-smb <dir>" swtich for Qemu, which is supposed to give the guest OS access to <dir>.  The IP address that the manpage claimed would be available wasn't ping-able by Windows.  Odd.

Has anyone had luck with either the -smb switch or getting the guest OS and host OS to simultaneously access a drive/partition?

Amazing work, all. And an amazing program![/QUOTE]

Thanks!.. 
To get the -smb to work you only need to install samba for file sharing, then create a nework user. 

1. [http://www.ubuntuguide.org/#installsamba](http://www.ubuntuguide.org/#installsamba)
2. [http://www.ubuntuguide.org/#sharefolderstheeasyway](http://www.ubuntuguide.org/#sharefolderstheeasyway)

Hope this helps.

---

### Post by Lunde on 2005-06-13
I see that you use .iso instead of .img, maybe this makes a difference.

---

### Post by Lunde on 2005-06-13
[QUOTE=iammike]
```
iammike@IAMMIKE-01:~/Desktop/qemu-0.7.0$ sudo dpkg -i qemu-0.7.0_0.7.0-1_i386.deb
(Reading database ... 100486 files and directories currently installed.)
Unpacking qemu-0.7.0 (from qemu-0.7.0_0.7.0-1_i386.deb) ...
dpkg: error processing qemu-0.7.0_0.7.0-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.10-5-386/modules.alias', which is also in package linux-image-2.6.10-5-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 qemu-0.7.0_0.7.0-1_i386.deb
```[/QUOTE]

I never tried the checkinstall for this. I just installed it normal. do you have a backup? if not check this out: [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

First you should go into **Symnaptic** to fix any broken packages, it will notify you when you open it if there are broken packages.

Then I would consider doing the installation the normal way.

---

### Post by Lunde on 2005-06-13
Are you linking up both disks? 

I think it's best to link up the disk environment as it is originally. **-hda /link_to_hda.img**  **-hdb /link_to_hdb.img**. Then use **boot c **
all partitions under will be read as partitions. the bootloader starts in the first sectors of the primary disk, then it referes to exs: **hdb1/boot/** which is now in Qemu's disk reading also hdb1/boot. then it tries to start hda etc. 

Be carefull I don't know what happens if you end up starting your ubuntu becaues of timeout in the Grub menu. it might start overwriting your hardware configuration.

---

### Post by KLineD on 2005-06-13
[QUOTE=Lunde]Are you linking up both disks? 

I think it's best to link up the disk environment as it is originally. **-hda /link_to_hda.img**  **-hdb /link_to_hdb.img**. Then use **boot c **
all partitions under will be read as partitions. the bootloader starts in the first sectors of the primary disk, then it referes to exs: **hdb1/boot/** which is now in Qemu's disk reading also hdb1/boot. then it tries to start hda etc. 

Be carefull I don't know what happens if you end up starting your ubuntu becaues of timeout in the Grub menu. it might start overwriting your hardware configuration.[/QUOTE]

Oh I just linked the disk with Winxp. I'll try and do as you said.

And yes, I was thinking about what could happen if you boot ubuntu instead of winxp. It's worth the risk If I can boot xp this way!

---

### Post by tkiesel on 2005-06-13
[QUOTE=Lunde]Thanks!.. 
To get the -smb to work you only need to install samba for file sharing, then create a nework user. 

1. [http://www.ubuntuguide.org/#installsamba](http://www.ubuntuguide.org/#installsamba)
2. [http://www.ubuntuguide.org/#sharefolderstheeasyway](http://www.ubuntuguide.org/#sharefolderstheeasyway)

Hope this helps.[/QUOTE]

Samba was already installed. I got it working via the wonderful wikipage: [http://www.ubuntulinux.org/wiki/WindowsXPUnderQemuHowTo](http://www.ubuntulinux.org/wiki/WindowsXPUnderQemuHowTo)
Turns out, we were a victim of an unclearly worded manpage for qemu. When using the switch "-smb dir", it claims that the share is available at \\smbserver\qemu (implying that no matter what dir is used, it will be available to guest os as a share named qemu), when in fact you have to look at \\smbserver\dir (where dir is the string specified in the switch).

The wiki gave a perfectly formatted Howto. Very cool, and my wife's up and running with Photoshop. There are still a few performance issues she has with the program: brush strokes sometimes appear several second safter she makes them, rendering detail work cumbersome. It's not as unusable as Photoshop through Wine, but a nice bump in performance would be useful.

What I'm on the look out for now is performance improvements.
1. I'm now very much on the prowl for guest OS tweaks to lower footprint and/or boost performance.
2. Can you make a qemu disk image in /dev/shm or another RAM-based tempfs, and then have the guest OS use this image/drive for swap? I imagine that this would offer a non-zero improvement in the speed of the guest os.
3. I can imagine that aggressive optimizations in compiling qemu/kqemu would cause some issues, but is there any wiggle room there?

These are things I'm going to start experimenting with over the next few days. #2 in particular interests me. If anyone else is willing to try these out, our collective experimentation can provide more info for this awesome Howto and the Ubuntu wiki.

Take care, everyone,
-T

---

### Post by KLineD on 2005-06-13
Still getting the weird characters when trying to boot a native XP installation. I have SP2 installed in XP, maybe it has something to do ?

---

### Post by AgenT on 2005-06-13
[QUOTE=tkiesel]What I'm on the look out for now is performance improvements.
1. I'm now very much on the prowl for guest OS tweaks to lower footprint and/or boost performance.
2. Can you make a qemu disk image in /dev/shm or another RAM-based tempfs, and then have the guest OS use this image/drive for swap? I imagine that this would offer a non-zero improvement in the speed of the guest os.
3. I can imagine that aggressive optimizations in compiling qemu/kqemu would cause some issues, but is there any wiggle room there?

These are things I'm going to start experimenting with over the next few days. #2 in particular interests me. If anyone else is willing to try these out, our collective experimentation can provide more info for this awesome Howto and the Ubuntu wiki.

Take care, everyone,
-T[/QUOTE]

If you need better performance, why not change the guest OS? Win98 should run faster than XP (uses less memory, etc.). If it will run the applications you need, you may look into installing it. Can't hurt!

---

### Post by Lunde on 2005-06-13
[QUOTE=AgenT]If you need better performance, why not change the guest OS? Win98 should run faster than XP (uses less memory, etc.). If it will run the applications you need, you may look into installing it. Can't hurt![/QUOTE]

Win98 is not much faster, the Kqemu accelerator will not work. WIn95 is fastest, but there are lots of programs you can't run. Win2000 stripped down is the best option of all I tried.

Also note that win98 (before second edition) will not run latest Macromedia Dreamweaver, and probably a lot of other applications

---

### Post by spacemonkey on 2005-06-13
KlineD, I also have SP2 installed, but I don't think that would be the issue, because I've got SP2 installed on my virtual disk install of windows as well, and I don't see what the difference would be.  Strange that we have nearly identical disk setups, yet when trying to boot windows, we get different results....

---

### Post by Lunde on 2005-06-13
[QUOTE=tkiesel]Samba was already installed. I got it working via the wonderful wikipage: [http://www.ubuntulinux.org/wiki/WindowsXPUnderQemuHowTo](http://www.ubuntulinux.org/wiki/WindowsXPUnderQemuHowTo)
Turns out, we were a victim of an unclearly worded manpage for qemu. When using the switch "-smb dir", it claims that the share is available at \\smbserver\qemu (implying that no matter what dir is used, it will be available to guest os as a share named qemu), when in fact you have to look at \\smbserver\dir (where dir is the string specified in the switch).

The wiki gave a perfectly formatted Howto. Very cool, and my wife's up and running with Photoshop. There are still a few performance issues she has with the program: brush strokes sometimes appear several second safter she makes them, rendering detail work cumbersome. It's not as unusable as Photoshop through Wine, but a nice bump in performance would be useful.

What I'm on the look out for now is performance improvements.
1. I'm now very much on the prowl for guest OS tweaks to lower footprint and/or boost performance.
2. Can you make a qemu disk image in /dev/shm or another RAM-based tempfs, and then have the guest OS use this image/drive for swap? I imagine that this would offer a non-zero improvement in the speed of the guest os.
3. I can imagine that aggressive optimizations in compiling qemu/kqemu would cause some issues, but is there any wiggle room there?

These are things I'm going to start experimenting with over the next few days. #2 in particular interests me. If anyone else is willing to try these out, our collective experimentation can provide more info for this awesome Howto and the Ubuntu wiki.

Take care, everyone,
-T[/QUOTE]

1. Set as many processes you can to manual or disabled (Search Google for Xp tweak processes) Disable background image, disable all system sound, Antivirus and firewall takes a lot of resources. I use ClamAV to scan for viruses and keep all documents for windows in the linux shared folder. 
But for running XP... VMware the best solution I've tried

2. One option is to use the -m 512 or what ever you want to give the host as memory, Qemu will tell you that you have to raise the shm by:

$ sudo umount /dev/shm
$ sudo mount -t tmpfs -o size=528m none /dev/shm

If you want to do this permanent, set up the mount in /etc/fstab

3. WinXP without Kqemu I did in Win4LinPro, it was so slow before I compiled with Kqemu I'm not joking when I say it jumped to doubble speed, but still it was slow and I ripped it out fast.  

My solution now:
Because I'm also dependent on photoshop. Gimp is great, but I work so much faster in photoshop. I run a stripped down Win2000 in VMware for Photoshop, Illustrator, Dreamweaver, IE and Office and it's very fast, I almost can't notice that Ubuntu is running in the background. 

Cut and paste from Ubuntu to WIndows is great, feels like one big system. I surf the net with Firefox in 1 workspace, keep this forum up in another workspace, then I run windows in the third and switch with 3ddesktop (I love that app: [http://desk3d.sourceforge.net/](http://desk3d.sourceforge.net/) ). 

I use Qemu to run a webserver for testing. I can run both VMware and Qemu open at the same time and it works wonders. I am very happy with this solution and can recomend it to anyone developing web applications or similar. 

I'm now working on a "howto" for setting up and tweaking a development workstation with Ubuntu from scratch, but it will take a while before I'm done.

---

### Post by AgenT on 2005-06-13
[QUOTE=Lunde]
Because I'm also dependent on photoshop. Gimp is great, but I work so much faster in photoshop. I run a stripped down Win2000 in VMware for Photoshop, Illustrator, Dreamweaver, IE and Office and it's very fast, I almost can't notice that Ubuntu is running in the background. 
[/QUOTE]

While probably not suitable, have you tried [GIMPshop]("http://plasticbugs.com/index.php?p=241")? It is a fork of GiMP that tries to make it like Photoshop (shortcuts, single window, etc.).  Do note that I have never tried it because photoshop was never all that intuitive for me anyway ;-) But it may be worth a look.

---

### Post by tkiesel on 2005-06-14
Thanks for the tips Lunde. I don't think we have the financial means to buy a copy of Win 2k right now, though that's certainly an attractive prospect technically speaking.

We'll be upgrading our computers to 1 GB of RAM in another two weeks also, which might help. I'm going to forge ahead with trying to mount a RAMdisk to house a disk image for Windows swap and the Photoshop scratch disk. I won't have much time to experiment with this for the next week, but when I get some results, I wil post them here.

[QUOTE=AgenT]While probably not suitable, have you tried [GIMPshop]("http://plasticbugs.com/index.php?p=241")? It is a fork of GiMP that tries to make it like Photoshop (shortcuts, single window, etc.).  Do note that I have never tried it because photoshop was never all that intuitive for me anyway ;-) But it may be worth a look.[/QUOTE]

My reading up on GIMPshop had led me to believe that it didn't implement a single window UI.

Innnteresting. Perhaps I need to locate and compile it. (unless someone has made a Hoary i386 .deb for it.)

much love to all,
T

---

### Post by AgenT on 2005-06-14
[QUOTE=tkiesel]My reading up on GIMPshop had led me to believe that it didn't implement a single window UI.

Innnteresting. Perhaps I need to locate and compile it. (unless someone has made a Hoary i386 .deb for it.)

much love to all,
T[/QUOTE]

[GIMPshop downloads]("http://freshmeat.net/projects/gimpshop/?branch_id=57360&release_id=192296") (including rpm - look at mirror section)

Type this to create a deb from rpm:
 ```
 alien <your rpm file here>
``` 
That's it! Although this is not recommended and you should only use alien as a last resort (when no good deb's exist). Also, you may need to apt-get install alien if you do not have it.

QUICK EDIT: Debian file found here (no need for alien): [http://linux.suramya.com/tutorials/Install_GIMPShop/]("http://linux.suramya.com/tutorials/Install_GIMPShop/")

Also you could check the backports repositories.

---

### Post by Lunde on 2005-06-14
OK I tried to install Gimpshop, had to have a look. There's a toturial here: [http://ubuntuforums.org/showthread.php?postid=205361#poststop](http://ubuntuforums.org/showthread.php?postid=205361#poststop) 

I have to warn you that it's not easy there are a lot of errors that you might end up with. 

I used about 3 hours, could'nt figure out why it only changed the startup logo of gimp. Then I tried to remove it and install again and the same... Then I started it as root, wondering if there were some configuration from the old gimp under my home folder, and still the same. I frustrated started to do some drawing just to check that it worked like it did before... and actually there were some changes, The menu was more like Photoshop after I opened an image. 

Photoshop key shortcuts are excelent, but dont need the GimpShop for those. Can be downloaded here: [http://epierce.freeshell.org/gimp/gimp_ps.php](http://epierce.freeshell.org/gimp/gimp_ps.php)

Overall: better, but not much. Not worth the hours, I really liked gimp the way it was. What I really miss from Photoshop are: **Save for web** and **Actions**, saves me from a lot of work.

If there only were something like Dreamweaver for Linux, I would never start windows. I tried most out there to see if I could use it, but Dreamweaver is 10 steps ahead of everything else. Actually I mostly use gedit for scripts, but every time I start a project Dreamweaver is a must.

---

### Post by AgenT on 2005-06-14
[QUOTE=Lunde]If there only were something like Dreamweaver for Linux, I would never start windows. I tried most out there to see if I could use it, but Dreamweaver is 10 steps ahead of everything else. Actually I mostly use gedit for scripts, but every time I start a project Dreamweaver is a must.[/QUOTE]

My guess is that you have tried the newest version of NVU. If not, have a look. It is very early in its development however.

---

### Post by Lunde on 2005-06-15
[QUOTE=AgenT]My guess is that you have tried the newest version of NVU. If not, have a look. It is very early in its development however.[/QUOTE]

Yes I have. NVU is nice, probably the best I've tried for Linux but I guess I'm a bit picky. After using these programs for many years it's hard to convert to something else. 

Anyway, I guess the best option is to boot Windows inside Ubuntu, the best of both worlds. There are a lot of other programs I also need, like Illustrator, indesign, Flash, etc.

---

### Post by jakew1991 on 2005-06-15
I got this working before, but then I re-installed Ubuntu because I was going to try to emulate Ubuntu under Windows instead of Windows under Ubuntu, but it didn't work, so now I'm back on Ubuntu.

However, there are two errors that come up.  During the **./config** it comes up with the error "big/little check failed", and when I attempted to build it, the very first file came up with error "Command not found."

EDIT: If anyone has gotten this error, you can fix it by installing the newer version of GCC from the package manager.

 - jake

---

### Post by lonetree on 2005-06-15
Hey, seems that I have run into this problem too, below is my result,

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
big/little test failed
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/newuser/Desktop/qemu-0.7.0
C compiler        gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu
gprof enabled     no
static build      no
SDL support       no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers-2.6.10-5-386
kbuild type       2.6

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Already installed GCC the newest I suppose, however, did not remove the old ones.

So, could this be the problem why it still can't do the ./configure?

Anyone has got this problem? Please help

---

### Post by AgenT on 2005-06-15
[QUOTE=lonetree]Hey, seems that I have run into this problem too, below is my result,

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
big/little test failed
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/newuser/Desktop/qemu-0.7.0
C compiler        gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu
gprof enabled     no
static build      no
SDL support       no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers-2.6.10-5-386
kbuild type       2.6

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Already installed GCC the newest I suppose, however, did not remove the old ones.

So, could this be the problem why it still can't do the ./configure?

Anyone has got this problem? Please help[/QUOTE]

First, read the FAQ and Documentation (and search the QEMU forum) as it may help. [QEMU HOMEPAGE]("http://fabrice.bellard.free.fr/qemu/"). 

From the FAQ (may or may not help you):


 > **QEMU does not compile. Why ?**

  It is likely that you are using GCC 4.x: it is currently not supported by QEMU. You must use GCC 3.x.

---

### Post by BKonkle on 2005-06-26
Hi, I just wanted to comment that I got KQemu running with Windows XP Pro very easily, without a hitch.  The only thing that didn't work was using "checkinstall" instead of "make install".  I played around with it, and then decided to move on and just use "make install".

The speed is fine since I just intend to use it for Photoshop and Dreamweaver.

I'm very impressed.  Very very impressed.

Edit: Okay, here's another problem I'm working on.  I can't connect to the internet.  The status reports "Invalid IP Address". . . I'm figuring it must have something to do with my router.  I'm looking into it. . .

Edit: After pouring over endless documents and forums, I simply closed Qemu and opened it back up.  Go figure. . . networking is completely fine now.

---

### Post by Quest-Master on 2005-06-26
> FATAL: Error inserting kqemu (/lib/modules/2.6.10-4-686/misc/kqemu.ko): Invalid module format


When trying to modprobe kqemu with and without sudo.. :( I've almost lost all hope of QEMU and VMware.

---

### Post by Lunde on 2005-06-27
[QUOTE=BKonkle]Hi, I just wanted to comment that I got KQemu running with Windows XP Pro very easily, without a hitch.  The only thing that didn't work was using "checkinstall" instead of "make install".  I played around with it, and then decided to move on and just use "make install".

The speed is fine since I just intend to use it for Photoshop and Dreamweaver.

I'm very impressed.  Very very impressed.

Edit: Okay, here's another problem I'm working on.  I can't connect to the internet.  The status reports "Invalid IP Address". . . I'm figuring it must have something to do with my router.  I'm looking into it. . .

Edit: After pouring over endless documents and forums, I simply closed Qemu and opened it back up.  Go figure. . . networking is completely fine now.[/QUOTE]

Nice to hear that your're pleased and everything is fine.

---

### Post by Lunde on 2005-06-27
[QUOTE=Quest-Master]When trying to modprobe kqemu with and without sudo.. :( I've almost lost all hope of QEMU and VMware.[/QUOTE]

Did you get any errors during **./configure** or **make**?

Have you in the past upgraded your kernel? I can see your are on 2.6.10-**4**-686, maybe you have more then 1 kernel and compiled for the wrong one.

Can you do a:

$ uname -a

and post the output here?

You also have problems with VMware?

---

### Post by sebdah on 2005-06-27
Thanks for a very well written HOWTO, Lunde!

For you guys who wants to tweak WinXP: Check [TweakXP.com](http://www.tweakxp.com), it should be everything you need!

---

### Post by Lunde on 2005-06-27
[QUOTE=sebdah]Thanks for a very well written HOWTO, Lunde!

For you guys who wants to tweak WinXP: Check [TweakXP.com](http://www.tweakxp.com), it should be everything you need![/QUOTE]

Thanks, I've added this in the howto.

---

### Post by Lupine on 2005-06-27
First off, thanks for this very detailed HOWTO.....awesome work!

I was wondering if you or anyone else can give a step by step addition on how to get networking working to the point that the Guest OS (Win2k) can see the Ubuntu host and the rest of the internet.  I've read over all the searches on Ubuntu for "tun" "qemu" and a few others, but I just can't get this Guest on the net  :???: 

I've tried to go to the Qemu mailing list, but their server seems to be down (for a few days now).

This is what I've done so far:

Host Ubuntu networking info:
IP:  192.168.5.100
Gateway: 192.168.5.1
Has access to Internet and local 192.168.5.x network

1.) Followed this HOWTO and I have a working Winblows2k install
2.) On Ubuntu host laptop, I've ran the following:
[INDENT]
[B]tunctl -u myuser tun0
sudo ifconfig tun0 192.168.254.254 up
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
[/B]
[/INDENT]
3.) On the Win2k Guest I statically set IP info as:
IP:  192.168.254.100
Gateway: 192.168.254.254


That's about all the documentaton I could put together, but I still can't get Win2k Virtual PC (192.168.254.100) to ping Ubuntu Host PC (192.168.254.254).  Where did I go wrong?

TIA,
-Lup

---

### Post by Lunde on 2005-06-27
Do you use a software firewall like firestarter? if so, you must allow the guest IP to access the host and allow Ping.

I'm not sure if 192.168.5.100 is the IP the guest recognice as your host, try to set DHCP in guest and and see what IP you get, then the host IP is the same with 1 in the end, I think this also goes for you gateway. 

Internet should work out of the box, try to reboot the host, it's been suggested to help in some cases.

You do set the flag -user-net I assume

---

### Post by Quest-Master on 2005-06-27
[QUOTE=Lunde]Did you get any errors during **./configure** or **make**?

Have you in the past upgraded your kernel? I can see your are on 2.6.10-**4**-686, maybe you have more then 1 kernel and compiled for the wrong one.

Can you do a:

$ uname -a

and post the output here?

You also have problems with VMware?[/QUOTE]
 I didn't get any errors during ./configure or make.

This is the output of uname -a.

> Linux ubuntu 2.6.10-4-686 #1 Sat Mar 12 11:12:34 GMT 2005 i686 GNU/Linux


Also, in VMware, it can't find the sources to build a vmmon module.

---

### Post by Lunde on 2005-06-27
[QUOTE=Quest-Master]I didn't get any errors during ./configure or make.

This is the output of uname -a.



Also, in VMware, it can't find the sources to build a vmmon module.[/QUOTE]
 Some cut & paste that might help
 
This is about the 2.6.10-4 kernel:
If you want to compile vmmon under Ubuntu kernel you need to install kernel-headers for your kernel / achitecture.Didn't work. vmware-config.pl requires a compiled kernel tree containing some directories that are created during compilation (and that doesn't come with linux-headers). I couldn't recompile the original kernel using the headers either.

Do you have a reason for not updating your kernel? I think there are some fixes because I had no problem with the 2.6.10-5-686 kernel. Are you on Warty?

---

### Post by Quest-Master on 2005-06-27
[QUOTE=Lunde]Some cut & paste that might help
 
This is about the 2.6.10-4 kernel:
If you want to compile vmmon under Ubuntu kernel you need to install kernel-headers for your kernel / achitecture.Didn't work. vmware-config.pl requires a compiled kernel tree containing some directories that are created during compilation (and that doesn't come with linux-headers). I couldn't recompile the original kernel using the headers either.

Do you have a reason for not updating your kernel? I think there are some fixes because I had no problem with the 2.6.10-5-686 kernel. Are you on Warty?[/QUOTE]
 
Hmm.. I DO need to upgrade my kernel then. Thanks.

---

### Post by Lupine on 2005-06-27
DOH  ](*,) 


Nevermind!!!   ICMP is shut off by default.  I think I read that somewhere too....I'm an idiot!  For the rest of the world, don't waste your time like I've done....try and map a drive, surf the web, FTP....ANYTHING besides pinging your host, and tada....it works. :-x 


Thanks again for this great HOWTO!

---

### Post by Lunde on 2005-06-27
[QUOTE=Lupine]DOH  ](*,) 


Nevermind!!!   ICMP is shut off by default.  I think I read that somewhere too....I'm an idiot!  For the rest of the world, don't waste your time like I've done....try and map a drive, surf the web, FTP....ANYTHING besides pinging your host, and tada....it works. :-x 


Thanks again for this great HOWTO![/QUOTE]
 Glad to hear it's working, Have fun

---

### Post by Lunde on 2005-06-27
[QUOTE=Quest-Master]Hmm.. I DO need to upgrade my kernel then. Thanks.[/QUOTE]

it should go quite painless, make sure to check if you have something else compiled under your current kernel before upgrading, like Nvidia drivers and other special hardware drivers

---

### Post by Quest-Master on 2005-06-27
[QUOTE=Lunde]it should go quite painless, make sure to check if you have something else compiled under your current kernel before upgrading, like Nvidia drivers and other special hardware drivers[/QUOTE]
 My X is dead now, after that upgrade, hehe.. will have to sort that out before even trying to get QEmu working.

---

### Post by Lunde on 2005-06-27
[QUOTE=Quest-Master]My X is dead now, after that upgrade, hehe.. will have to sort that out before even trying to get QEmu working.[/QUOTE]
 Are you using the Nvidia drivers?

---

### Post by Quest-Master on 2005-06-27
[QUOTE=Lunde]Are you using the Nvidia drivers?[/QUOTE]
 Nope. Nothing special like that.

---

### Post by AgenT on 2005-06-27
[QUOTE=Quest-Master]My X is dead now, after that upgrade, hehe.. will have to sort that out before even trying to get QEmu working.[/QUOTE]

What does it say when it dies? Look at the log in /var/cache/log/.

More than likely you are now missing new video card modules. Did you install any video card modules (sometimes referred to as "drivers") yourself such ati, nvidia, etc.? If so, you may have to reinstall them.

---

### Post by Lunde on 2005-06-27
Can you post the "section device" output from /etc/X11/xorg.conf ? 
and if you have any old xorg.conf.backup or .bak or similuar in case you took a backup of it from when it first was changed.

---

### Post by Quest-Master on 2005-06-27
[QUOTE=Lunde]Can you post the "section device" output from /etc/X11/xorg.conf ? 
and if you have any old xorg.conf.backup or .bak or similuar in case you took a backup of it from when it first was changed.[/QUOTE]
 
> Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

And AgenT, the error is:

X: cannot stat /etc/X11/X (input/output error), aborting. 

I also get lots of errors about modprobe apm and /etc/rcS.d/someweirdmodulegoeshere.

---

### Post by AgenT on 2005-06-27
[QUOTE=Quest-Master]And AgenT, the error is:

X: cannot stat /etc/X11/X (input/output error), aborting. 

I also get lots of errors about modprobe apm and /etc/rcS.d/someweirdmodulegoeshere.[/QUOTE]

That is the first time that /etc/X11/X was ever mentioned to me. I never knew it existed. The other distro I used did not have this (then again, it may have had a different version of xorg). And why would a binary file be in /etc/? That is strange. You could try reinstalling xorg, although that will probably not help. Also, you are in Hoary, right?

Are you sure you have the right kernel for your system? Don't mix Hoary and Warty kernels.

Are you positive that you did not install any extra packages/programs that install extra modules? Whether that would be video card modules or others (your apm error is strange). Also, did you get any errors when installing these new sources?

A list of forum topics that may help:
[http://www.ubuntuforums.org/showthread.php?t=43271]("http://www.ubuntuforums.org/showthread.php?t=43271")
[http://www.ubuntuforums.org/showthread.php?t=44500]("http://www.ubuntuforums.org/showthread.php?t=44500")
[http://www.ubuntuforums.org/showthread.php?t=43835]("http://www.ubuntuforums.org/showthread.php?t=43835")
[http://www.ubuntuforums.org/showthread.php?t=43360]("http://www.ubuntuforums.org/showthread.php?t=43360")

But I have never upgraded a kernel that was not done by hand (compiled) so I may not be able to help you here.

Also, you should probably post your whole xorg config because that will give more hints (what module you used, etc.). But don't post the comments. Instead, do this (this should be mandatory for everyone posting configs) in the terminal:
 ```
cat /etc/X11/xorg.conf | sed -e '/^\(\t\| \)*#.*\|^\(\t\| \)*$/d' -e 's/\(.*\)#.*/\1/'
``` 
And paste the results.

For anyone interested, you can make this a program/script for easy usage by adding it into your /usr/local/bin/ directory:
 ```
#!/bin/bash

sed -e '/^\(\t\| \)*#.*\|^\(\t\| \)*$/d' -e 's/\(.*\)#.*/\1/' "$@"

```

---

### Post by Quest-Master on 2005-06-28
> Section "Files"
	FontPath	"unix/:7100"			# local font server

	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"

	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"MX70"
	HorizSync	30-70
	VertRefresh	47-120
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"MX70"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Also, I get the same error about stat'ing X when trying to remove, reinstall, or dpkg-reconfigure xserver-xorg.

---

### Post by Lunde on 2005-06-28
I don't know really, but this is just an idea...

Your driver is i810, the i810 has a unified memory architecture and uses system memory for video ram. By default 8 Megabytes of system memory are used for graphics. 

If something is wrong with this driver, it might give other errors too since it's reserving system memory.

So, do you know the name of your graphics card? Installing the correct driver may help.  

Since you said you did'nt install any special drivers, it is probably recogniced by the Ubuntu installer so I looked in synaptics and found the following
 
**Discription of the packet i810switch from synaptics**
-------------------------------------------------------------------------------------------------------------
Enables/disables video output to CRT/LCD on i810 video hardware
i810switch enables/disables the output to the CRT display and LCD,
depending on the i810 graphics controller hardware. Such hardware is found
on some laptops (eg, Sony Vaios, some Dell models, etc). Chipsets also
supported include i855, i830, i845.

This package includes the i810rotate script, which toggles the output
between three states: LCD only, LCD + CRT, and CRT only.
--------------------------------------------------------------------------------------------------------------- 

$ sudo apt-get remove i810switch
$ sudo apt-get install i810switch

Maybe this will help.

I also think we should move this problem to a seperate tread, It will be visible to more people there and it may be other that know more and can provide an easy solution to your problem. 

Just post the url to your tread here after and I will see if I can halp you more from there.

---

### Post by Quest-Master on 2005-06-28
[QUOTE=Lunde]I don't know really, but this is just an idea...

Your driver is i810, the i810 has a unified memory architecture and uses system memory for video ram. By default 8 Megabytes of system memory are used for graphics. 

If something is wrong with this driver, it might give other errors too since it's reserving system memory.

So, do you know the name of your graphics card? Installing the correct driver may help.  

Since you said you did'nt install any special drivers, it is probably recogniced by the Ubuntu installer so I looked in synaptics and found the following
 
**Discription of the packet i810switch from synaptics**
-------------------------------------------------------------------------------------------------------------
Enables/disables video output to CRT/LCD on i810 video hardware
i810switch enables/disables the output to the CRT display and LCD,
depending on the i810 graphics controller hardware. Such hardware is found
on some laptops (eg, Sony Vaios, some Dell models, etc). Chipsets also
supported include i855, i830, i845.

This package includes the i810rotate script, which toggles the output
between three states: LCD only, LCD + CRT, and CRT only.
--------------------------------------------------------------------------------------------------------------- 

$ sudo apt-get remove i810switch
$ sudo apt-get install i810switch

Maybe this will help.

I also think we should move this problem to a seperate tread, It will be visible to more people there and it may be other that know more and can provide an easy solution to your problem. 

Just post the url to your tread here after and I will see if I can halp you more from there.[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=44748](http://ubuntuforums.org/showthread.php?t=44748) :)

---

### Post by Dr Evolution on 2005-06-29
Lunde,

Many many thanks for the Howto installing vmware was starting to do my nut.  I can't say my installation of qemu has gone without problems though, at the moment my installation completes with no problem.  When i try and start qemu from my icon i get nothing.

I'm sure i've followed the howto to the letter, but i must be wrong.

---

### Post by Lunde on 2005-06-29
[QUOTE=Dr Evolution]Lunde,

Many many thanks for the Howto installing vmware was starting to do my nut.  I can't say my installation of qemu has gone without problems though, at the moment my installation completes with no problem.  When i try and start qemu from my icon i get nothing.

I'm sure i've followed the howto to the letter, but i must be wrong.[/QUOTE]
 What went wrong installing VMware?
Did you compile with KQemu?

What happens when you try to start Qemu from the command line?
**$ qemu -boot d -cdrom /dev/cdrom -hda hd.img** (Modefy after your choice of configuration)

Do you get any errors?

[B]What is the output from:
$ uname -a[/B]

---

### Post by Dr Evolution on 2005-06-29
[QUOTE=Lunde]What went wrong installing VMware?
Did you compile with KQemu?

What happens when you try to start Qemu from the command line?
**$ qemu -boot d -cdrom /dev/cdrom -hda hd.img** (Modefy after your choice of configuration)

Do you get any errors?

[B]What is the output from:
$ uname -a[/B][/QUOTE]

Lunde,

i manage to get a full installation of either win2k or xp complete.  I get no errors generated.  this issue seems to be when configuring the launcher, i've search various locations on my machine to find the hd.img and tried to point qemu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda /path/to/your/hd.img -user-net -pci -m 256 -k en to it, but it appears to launch then just doesn't do anything

---

### Post by Lunde on 2005-06-29
[QUOTE=Dr Evolution]Lunde,

i manage to get a full installation of either win2k or xp complete.  I get no errors generated.  this issue seems to be when configuring the launcher, i've search various locations on my machine to find the hd.img and tried to point qemu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda /path/to/your/hd.img -user-net -pci -m 256 -k en to it, but it appears to launch then just doesn't do anything[/QUOTE]

The launcer need the full path to your hd.img

Try the following:
$ sudo slocate -c
to create a search database of your drives

Then locate the hd.img with this command:
$ slocate hd.img

Copy the output path to your launcher -hda

---

### Post by Dr Evolution on 2005-06-29
[QUOTE=Lunde]What went wrong installing VMware?
Did you compile with KQemu?

What happens when you try to start Qemu from the command line?
**$ qemu -boot d -cdrom /dev/cdrom -hda hd.img** (Modefy after your choice of configuration)

Do you get any errors?


[B]What is the output from:
$ uname -a [/QUOTE]


when i run **$ qemu -boot d -cdrom /dev/cdrom -hda hd.img** from a prompt i get

could not open hard disk image '/dev/cdrom'

output from $ uname -a[/B

gives me linux@hostname 2.6.10-5-386 #1 Fri jun 24 16:53:01 UTC 2005 i686 GNU/Linux

as for vmware, it kept asking me questions i couldn't answer such as the locations of gcc, but i guess i've gotten past that to get this far with qemu

---

### Post by Lunde on 2005-06-29
[QUOTE=Dr Evolution]when i run **$ qemu -boot d -cdrom /dev/cdrom -hda hd.img** from a prompt i get

could not open hard disk image '/dev/cdrom'

output from $ uname -a[/B

gives me linux@hostname 2.6.10-5-386 #1 Fri jun 24 16:53:01 UTC 2005 i686 GNU/Linux

as for vmware, it kept asking me questions i couldn't answer such as the locations of gcc, but i guess i've gotten past that to get this far with qemu[/QUOTE]
 You need to set the full path to your hd.img as described in: 
[http://www.ubuntuforums.org/showthread.php?p=233682#post233682](http://www.ubuntuforums.org/showthread.php?p=233682#post233682)

For installing VMware:
sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install make
sudo apt-get install gcc
(the first package you probably have)

Then proceed as discribed in the VMware installation documentation

---

### Post by snoopgst on 2005-06-29
I can't find: linux-headersXXXX folder

Still in Synaptic, choose the package you have just installed, click Properties and go to the "Installed Files" tab. Write down the directory where the files were copied. In my case, they were copied to: /usr/src/linux-headers-2.6.10-5-386/

---

### Post by Lunde on 2005-06-29
[QUOTE=snoopgst]I can't find: linux-headersXXXX folder

Still in Synaptic, choose the package you have just installed, click Properties and go to the "Installed Files" tab. Write down the directory where the files were copied. In my case, they were copied to: /usr/src/linux-headers-2.6.10-5-386/[/QUOTE]
 type in the terminal:
$ uname -r

Then type:
$ sudo apt-get install linux-headers-2.6.10-5-386
in the above line, change the 2.6.10-5-386 with the output from "uname -r"

---

### Post by snoopgst on 2005-06-30
i'm stuck at: 
$ gedit configure

change the: kernel_path="/usr/src/linux-headers-2.6.10-5-386" 


is this refered to .config? thats all i see thats similar to configure.  but i dont see kernel_path

---

### Post by Lunde on 2005-06-30
[QUOTE=snoopgst]i'm stuck at: 
$ gedit configure

change the: kernel_path="/usr/src/linux-headers-2.6.10-5-386" 


is this refered to .config? thats all i see thats similar to configure.  but i dont see kernel_path[/QUOTE]
 configure is a file. I have a suspition that you may have downloaded the wrong packet from [http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html) you are **NOT** supposed to get the packet qemu-0.7.0-i386.tar.gz

**Here's a complete url to the latest correct packet:**
[http://fabrice.bellard.free.fr/qemu/qemu-0.7.0.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.7.0.tar.gz)

Inside this packet there is a file configure that we may need to change. 

**If you have the correct packet and are unsure of how to edit it**
Post the file **configure** as an attachment here and write the output of:
**$ uname -r**
..and I'll edit it for you

---

### Post by snoopgst on 2005-06-30
anybody willing to do this for me "remote desktop"

msn: [email]snoopyjh33@hotmail.com[/email]
aim: snoopyjh14
yahoo: snoopgst

---

### Post by neongtr on 2005-06-30
I use checkinstall then I hit an error when the package is FAILED to install

 here is the log:

(Reading database ... 83444 files and directories currently installed.)
Unpacking qemu-0.7.0 (from .../qemu-0.7.0_0.7.0-1_i386.deb) ...
dpkg: error processing /home/ching/qemu-0.7.0/qemu-0.7.0_0.7.0-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.10-5-386/modules.alias', which is also in package linux-image-2.6.10-5-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/ching/qemu-0.7.0/qemu-0.7.0_0.7.0-1_i386.deb

 where did I go wrong??

---

### Post by mohaham on 2005-07-01
Thanks for this excellent HOWTO

---

### Post by Lunde on 2005-07-01
[QUOTE=snoopgst]anybody willing to do this for me "remote desktop"

msn: [email]snoopyjh33@hotmail.com[/email]
aim: snoopyjh14
yahoo: snoopgst[/QUOTE]
 First thing you need ot do is to make a backup, there is a nice howto here:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

Now you are safe to try and fail, or hopefully success.. So go ahead and the worst thing that can happen to you is a 10-15min restore. I suggest to do a seperate backup for your /home/username, because you probably don't need to restore this if the installastin goes wrong.

I'll guide you through the installation if you want by msn: [email]do_not_send_to_this_email@hotmail.com[/email]

---

### Post by Lunde on 2005-07-01
[QUOTE=neongtr]I use checkinstall then I hit an error when the package is FAILED to install

 here is the log:

(Reading database ... 83444 files and directories currently installed.)
Unpacking qemu-0.7.0 (from .../qemu-0.7.0_0.7.0-1_i386.deb) ...
dpkg: error processing /home/ching/qemu-0.7.0/qemu-0.7.0_0.7.0-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.10-5-386/modules.alias', which is also in package linux-image-2.6.10-5-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/ching/qemu-0.7.0/qemu-0.7.0_0.7.0-1_i386.deb

 where did I go wrong??[/QUOTE]
 I suggest a 
**$ sudo make install **
if you have problems with checkinstall

Or you have to give write access to the /lib/modules/2.6.10-5-386/modules.alias, but I would'nt reccomend this

---

### Post by Karl S. on 2005-07-01
two quick suggestions to help those of us who don't know anything about computers:

a) I got lost briefly with the gedit configure until I realized I was meant to gedit configure from within the qemu-0.7.0 directory. Could you change the how-to to clear up that possible confusion?

b) at the bit where you have "if everything is correct," would it possible to give an example of what everything being correct should look like? I didn't have any errors listed, but I still wasn't sure I had everything done correctly.

--

Here are my troubles with trying to install XP from a CD:

After MAKE I got this at the end of my output:
> 
Warning: could not find /home/karl/qemu-0.7.0/kqemu/.kqemu-mod.o.cmd for /home/karl/qemu-0.7.0/kqemu/kqemu-mod.o
  CC      /home/karl/qemu-0.7.0/kqemu/kqemu.mod.o
  LD [M]  /home/karl/qemu-0.7.0/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/karl/qemu-0.7.0/kqemu'
root@ubuntu:/home/karl/qemu-0.7.0 #

Is this something I should be worried about?
--

This isn't working for me:
$ qemu -boot d -cdrom /dev/cdrom -hda hd.img

Here's how my system is set up:
hda3 linux-swap
hda1 ntfs (with Windows XP on it)
hda2 ext2 (with Ubuntu, and I planned on installing another copy of XP here)

I've tried various commands, without really knowing what I'm doing.

I tried $ qemu -boot d -cdrom /dev/cdrom -hda2 hd.img,
$ qemu -boot f -cdrom /dev/cdrom -hda hd.img (changed to 'f' because according to Windows my CD RW drive is at F, not D), and
$ qemu -boot d -cdrom /cdrom -hda hd.img (because according to File Browser, my cr drive isn't at /dev/cdrom but rather just at /cdrom). 

I've tried all combinations on these, and depending on what I've done I either get:

> qemu: invalid boot device 'f'
karl@ubuntu:~$ qemu -boot d -cdrom /dev/cdrom -hda hd.img
qemu: could not open hard disk image 'hd.img'
karl@ubuntu:~$ qemu -boot d -cdrom /dev/cdrom -hda hd.img
qemu: could not open hard disk image 'hd.img'
karl@ubuntu:~$ qemu -boot d -cdrom /dev/cdrom -hda2 hd.img
qemu: invalid option -- '-hda2'

And so forth.

Since the Computer's refusing to eject the CDROM right now (Unable to eject media. umount: /media/cdrom0: device is busy; umount: /media/cdrom0: device is busy; eject: unmount of `/dev/hdd' failed), and telling me, in the process, where it thinks the CD is, I tried these things:

> karl@ubuntu:~$ qemu -boot d -cdrom /media/cdrom0 -hda hd.img
qemu: could not open hard disk image 'hd.img'
karl@ubuntu:~$ qemu -boot d -cdrom /media/cdrom0 -hda2 hd.img
qemu: invalid option -- '-hda2'
Still doesn't work.

I also looked at this advice [here](http://www.ubuntuforums.org/showpost.php?p=233682&postcount=119) , but it didn't work.

Here's this:
> karl@ubuntu:~/Qemu$ uname -a
Linux ubuntu 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux

 
I did $ sudo slocate -c

and then 
> karl@ubuntu:~/Qemu$ sudo slocate hd.img
karl@ubuntu:~/Qemu$

But, as you see, it doesn't return any information. Or did it and I just don't know enough to recognize what I'm looking at?

Now, I did do 
$ qemu-img create hd.img 4500M

and if I 
karl@ubuntu:~/Qemu$ dir
hd.img

So it seems to be there.

....what can I do to fix this?
But maybe it didn't take?

---

### Post by Lunde on 2005-07-01
[QUOTE=Karl S.]two quick suggestions to help those of us who don't know anything about computers:

a) I got lost briefly with the gedit configure until I realized I was meant to gedit configure from within the qemu-0.7.0 directory. Could you change the how-to to clear up that possible confusion?

b) at the bit where you have "if everything is correct," would it possible to give an example of what everything being correct should look like? I didn't have any errors listed, but I still wasn't sure I had everything done correctly.
[/QUOTE]

OK, this is going to be a bit long so break this into several replies

a) If you follow the howto step by step, you are already inside the qemu-0.7.0 directory. I think this is where you went wrong. 

[B]$ cd qemu-0.7.0
$ tar zxvf /location of downloaded files/kqemu-0.6.2-1.tar.gz[/B]

b) Thanks for the input. I'm not going to install it again, but if someone post a correct output, I'll put it in the howto. I should maybe change it around to: If you don't get any error messages.

---

### Post by Lunde on 2005-07-01
[QUOTE=Karl S.]
 Warning: could not find /home/karl/qemu-0.7.0/kqemu/.kqemu-mod.o.cmd for /home/karl/qemu-0.7.0/kqemu/kqemu-mod.o
CC /home/karl/qemu-0.7.0/kqemu/kqemu.mod.o
LD [M] /home/karl/qemu-0.7.0/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/karl/qemu-0.7.0/kqemu'
root@ubuntu:/home/karl/qemu-0.7.0 #
[/QUOTE]

The errors here are showing that you have some problems with finding the Kqemu files. these should be exstracted into the folder qemu-0.7.0: 
[B]
$ cd qemu-0.7.0
$ tar zxvf /location of downloaded files/kqemu-0.6.2-1.tar.gz [/B]

I think something went wrong for you untar'ing the kqemu accelerator, so you should download it one more time and do that over again.

---

### Post by Lunde on 2005-07-01
> **Karl S.]
I tried $ qemu -boot d -cdrom /dev/cdrom -hda2 hd.img,
$ qemu -boot f -cdrom /dev/cdrom -hda hd.img (changed to 'f' because according to Windows my CD RW drive is at F, not D), and
$ qemu -boot d -cdrom /cdrom -hda hd.img (because according to File Browser, my cr drive isn't at /dev/cdrom but rather just at /cdrom).
[/QUOTE]

if you want to start it with just hd.img and not full path like /home/username/qemu/hd.img you have to start qemu from within the directory the hd.img is located.

When refering to the boot flag, there are no other options then these
a = floppy
d = cdrom
c = hard drive
Your cdrom is only F: in Windows 

As for your virtual hard drives, you have to use:
-hda (primary)
-hdb (secondary)

-hda0 -hda1 have no function on an unpartioned disk, you can partition your hd.img into several partitions if you like, but I still don't think you can boot with those options.  

[QUOTE=Karl S.]
Since the Computer's refusing to eject the CDROM right now (Unable to eject media. umount: /media/cdrom0: device is busy said:**
> 

This happens in Ubuntu sometimes, if somebody have an ansvere to that I'll be happy too. Anyway, I think it will he different when it has a disk to install to.

[QUOTE=Karl S.]
and if I
karl@ubuntu:~/Qemu$ dir
hd.img

So it seems to be there.


There you have it. Perfect: 
/home/karl/Qemu/hd.img

So your install command should be:
**$ qemu -boot d -cdrom /dev/cdrom -hda /home/karl/Qemu/hd.img -user-net -pci -m 256 -k en**

And your start command should be:
**$ qemu -boot c -cdrom /dev/cdrom -hda /home/karl/Qemu/hd.img -user-net -pci -m 256 -k en**

I hope this sorted you out. Good luck!
Don't forget to reinstall with kqemu like I explained in the previous post.

---

### Post by Karl S. on 2005-07-01
[QUOTE=Lunde]The errors here are showing that you have some problems with finding the Kqemu files. these should be exstracted into the folder qemu-0.7.0: 
[B]
$ cd qemu-0.7.0
$ tar zxvf /location of downloaded files/kqemu-0.6.2-1.tar.gz [/B]

I think something went wrong for you untar'ing the kqemu accelerator, so you should download it one more time and do that over again.[/QUOTE]

Thanks for your reply. Unfortunately, I'm getting the same error. I deleted the qemu-0.7.0 and Qemu folders, uninstalled libsdl1.2-dev and zlib1g-dev, redownloaded the QEMU Source Code and Accelerator Module, and started again.

I'm asking this question out of complete ignorance, but I just realized I untarred the kqemu while in root. Could that be causing a problem?

Here is the output of the Kqemu installation:
>  root@ubuntu:/home/karl/qemu-0.7.0 # tar zxvf /home/karl/kqemu-0.6.2-1.tar.gz kqemu/Makefile
kqemu/README
kqemu/LICENSE
kqemu/install.sh
kqemu/kmod.c
kqemu/kqemu.h
kqemu/kqemu-mod-i386.o
kqemu/kqemu-doc.texi
kqemu/kqemu-doc.html
root@ubuntu:/home/karl/qemu-0.7.0 #

After doing configure (and changing kernel_path="/usr/src/linux-headers-2.6.10-5-386" ...this is under the esac list, right?), I reinstalled libsdl1.2-dev and zlib1g-dev using Synaptic. The output for ./configure is:

> root@ubuntu:/home/karl/qemu-0.7.0 # ./configure
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/karl/qemu-0.7.0
C compiler        gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu
gprof enabled     no
static build      no
SDL support       yes
SDL static link   no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

And then after make outputs text for a while, I get this:

> Warning: could not find /home/karl/qemu-0.7.0/kqemu/.kqemu-mod.o.cmd for /home/karl/qemu-0.7.0/kqemu/kqemu-mod.o
  CC      /home/karl/qemu-0.7.0/kqemu/kqemu.mod.o
  LD [M]  /home/karl/qemu-0.7.0/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/karl/qemu-0.7.0/kqemu'

Okay, I'm going to try this again, but this time not do anything in root. Your answers strike me as very helpful, and I'm confident this is going to work. I only hope that my questions can help some other total newbie on this board. Thanks very much.

---

### Post by Lunde on 2005-07-01
I made this icon for the launcher. If any of you want to use it:

---

### Post by khai on 2005-07-01
Wow! I wish I'd have known about this sooner, I've got Windows XP working at similar speeds to when I was running it on my P4 at 256mb before I upgraded the ram to 512mb.

Make sure to install updates right away, I've had two installs screw up on me on the first boot before because my Windows doesn't come installed with any service packs and I ended up picking up a virus or trojan within a few minutes of being online.
Screenshot-
[http://img.photobucket.com/albums/v445/khai/Screenshot.png](http://img.photobucket.com/albums/v445/khai/Screenshot.png)

---

### Post by Lunde on 2005-07-01
[QUOTE=Karl S.]Thanks for your reply. Unfortunately, I'm getting the same error. I deleted the qemu-0.7.0 and Qemu folders, uninstalled libsdl1.2-dev and zlib1g-dev, redownloaded the QEMU Source Code and Accelerator Module, and started again.

I'm asking this question out of complete ignorance, but I just realized I untarred the kqemu while in root. Could that be causing a problem?

Here is the output of the Kqemu installation:


After doing configure (and changing kernel_path="/usr/src/linux-headers-2.6.10-5-386" ...this is under the esac list, right?), I reinstalled libsdl1.2-dev and zlib1g-dev using Synaptic. The output for ./configure is:



And then after make outputs text for a while, I get this:



Okay, I'm going to try this again, but this time not do anything in root. Your answers strike me as very helpful, and I'm confident this is going to work. I only hope that my questions can help some other total newbie on this board. Thanks very much.[/QUOTE]
 yes.. don't do anything as root before the installation. Also just to make sure, do a:
$ sudo chmod -R 775 /home/karl/qemu-0.7.0
after you have untar'ed the kqemu inside the qemu-0.7.0 directory

Hope it works this time

---

### Post by Lunde on 2005-07-01
[QUOTE=khai]Wow! I wish I'd have known about this sooner, I've got Windows XP working at similar speeds to when I was running it on my P4 at 256mb before I upgraded the ram to 512mb.

Make sure to install updates right away, I've had two installs screw up on me on the first boot before because my Windows doesn't come installed with any service packs and I ended up picking up a virus or trojan within a few minutes of being online.
Screenshot-
[http://img.photobucket.com/albums/v445/khai/Screenshot.png](http://img.photobucket.com/albums/v445/khai/Screenshot.png)[/QUOTE]
 You can set more memory if you like, ex: **-m 384**. you just have to to follow the instructions that comes with the error message after

---

### Post by Karl S. on 2005-07-01
[QUOTE=Lunde]yes.. don't do anything as root before the installation. Also just to make sure, do a:
$ sudo chmod -R 775 /home/karl/qemu-0.7.0
after you have untar'ed the kqemu inside the qemu-0.7.0 directory

Hope it works this time[/QUOTE]

Well. It's a mystery to me. I've tried this four times now and it still doesn't work. And I did the sudo chmod etc.

Here's some sample output:

> karl@ubuntu:~/qemu-0.7.0$ cd /home/karl
karl@ubuntu:~$ mkdir Qemu
karl@ubuntu:~$ cd Qemu
karl@ubuntu:~/Qemu$ qemu-img create hd.img 4500M
Formating 'hd.img', fmt=raw, size=4608000 kB
karl@ubuntu:~/Qemu$ qemu -boot d -cdrom /dev/cdrom -hda /home/karl/Qemu/hd.img -user-net -pci -k en
qemu: could not open hard disk image '/dev/cdrom'
karl@ubuntu:~/Qemu$

SInce the kqemu directory seems to be the one giving the trouble, here it is:

> karl@ubuntu:~/qemu-0.7.0/kqemu$ dir
install.sh  kqemu-doc.html  kqemu.ko          kqemu-mod.o  LICENSE
kmod.c      kqemu-doc.texi  kqemu.mod.c       kqemu.mod.o  Makefile
kmod.o      kqemu.h         kqemu-mod-i386.o  kqemu.o      README
karl@ubuntu:~/qemu-0.7.0/kqemu$ pwd
/home/karl/qemu-0.7.0/kqemu
Is that the way it should look? I don't know what "could not find /home/karl/qemu-0.7.0/kqemu/.kqemu-mod.o.cmd for /home/karl/qemu-0.7.0/kqemu/kqemu-mod.o" means, but if it's looking for a file .kqemu-mod.o.cmd, I can't find it either. But as you can see, the kqemu folder is where it's supposed to be, inside the qemu-0.7.0 folder, right?

If it's of any use to you, when I modprobe kqemu (or sudo modprobe kqemu), nothing seems to be happening.

I'm giving up on this for tonight, though. Thanks for your help so far.

---

### Post by khai on 2005-07-02
Is there anyway to resize the hd.img, 5 gigs ended up being a little too small for me. Also, while I'm at it, can this run in the console with no desktop enviroment or window manager loaded, if so, how? Thanks

---

### Post by Lunde on 2005-07-02
[QUOTE=khai]Is there anyway to resize the hd.img, 5 gigs ended up being a little too small for me. Also, while I'm at it, can this run in the console with no desktop enviroment or window manager loaded, if so, how? Thanks[/QUOTE]
 Yes, you have to create a new disk image of the size you want. then boot a liveCD in Qemu, I used Knoppix. Then use the fdisk to "disk copy" the hd.img into the new image. And last there's a tool called ntfsresize in Knoppix that will expand the partition to the full size of the new disk image.

No, Qemu needs a window manager. I have not tried this in anything else then Metacity /  Gnome.

---

### Post by Lunde on 2005-07-02
[QUOTE=Karl S.]Well. It's a mystery to me. I've tried this four times now and it still doesn't work. And I did the sudo chmod etc.

Here's some sample output:



SInce the kqemu directory seems to be the one giving the trouble, here it is:


Is that the way it should look? I don't know what "could not find /home/karl/qemu-0.7.0/kqemu/.kqemu-mod.o.cmd for /home/karl/qemu-0.7.0/kqemu/kqemu-mod.o" means, but if it's looking for a file .kqemu-mod.o.cmd, I can't find it either. But as you can see, the kqemu folder is where it's supposed to be, inside the qemu-0.7.0 folder, right?

If it's of any use to you, when I modprobe kqemu (or sudo modprobe kqemu), nothing seems to be happening.

I'm giving up on this for tonight, though. Thanks for your help so far.[/QUOTE]
 Can you post the kqemu directory listing with 
$ ls -al
So that I can see the permissions?

And also, your cdrom is that a combined RW? if so, it might be that it's /dev/hdd

---

### Post by jimcooncat on 2005-07-02
I do tech for a small business with users on Windows and am building an Ubuntu environment to host Linux programs. I'm trying a variety of technologies for sharing, like Cygwin, FreeNX, VNC, etc.

If the methods in this thread work well, I could have the users run Ubuntu with selected apps, using a common Win 2000 Pro installation. No hardware changes under Windows would be wonderful!

So if I get a chance I'll be experimenting with this soon, but a few answers ahead of time would be great:

1. Would Squid make an appropriate proxy for IE? I'd like the Windows installation only be able to access a short whitelist of URLs, like [http://windowsupdate.microsoft.com](http://windowsupdate.microsoft.com) and [http://quickbooks.com;](http://quickbooks.com;) and set this up before installing the Win 2000.

2. Once I have a Win 2000 image, can I just copy from one machine to another regardless of the actual hardware (assuming they can both do same screen resolution, etc.)?

3. Any specs or anecdotes on memory and filesystem with default install of Hoary, Qemu, kqemu, and Windows 2000?

4. Suggestions for stripping Windows 2000 of cruft?

---

### Post by Lunde on 2005-07-02
> **jimcooncat]I do tech for a small business with users on Windows and am building an Ubuntu environment to host Linux programs. I'm trying a variety of technologies for sharing, like Cygwin, FreeNX, VNC, etc.

If the methods in this thread work well, I could have the users run Ubuntu with selected apps, using a common Win 2000 Pro installation. No hardware changes under Windows would be wonderful!

So if I get a chance I'll be experimenting with this soon, but a few answers ahead of time would be great:
[/QUOTE]
VMware is what you are looking for, it's faster and more stabile. Tho Qemu also would do the trick. This sound like a fun network to set up. 

[QUOTE=jimcooncat]
1. Would Squid make an appropriate proxy for IE? I'd like the Windows installation only be able to access a short whitelist of URLs, like [http://windowsupdate.microsoft.com](http://windowsupdate.microsoft.com) and [url]http://quickbooks.com said:**
>  and set this up before installing the Win 2000.

I hav'nt tested squid myself, but as I understand it should'nt be a problem. Any firewall box with filtering would also do the trick. This can also be configured in the windows configuration in the template installation. I don't know how much you want your users to be able to configure their Windows, but if they all should have an identical windows image, then you only need to update the template and push it after work hours.

[QUOTE=jimcooncat]
2. Once I have a Win 2000 image, can I just copy from one machine to another regardless of the actual hardware (assuming they can both do same screen resolution, etc.)?
[/QUOTE]
Yes, Qemu & VMware are emulating the hardware, so there are no difference from machine to machine. If you change all "My Documents" folders so they are located on the mapped linux disk, then if your worker scew anything up you just push the template over the chrashed Windows image. 3min and they are back up again with all tools needed to do their work.

[QUOTE=jimcooncat]
3. Any specs or anecdotes on memory and filesystem with default install of Hoary, Qemu, kqemu, and Windows 2000?
[/QUOTE]
Depending on what sort of work you want to perform. But 512mb memory would do good. You can probably run with less too. 
As of filesystem, I would recommend Ext3 it's probably the safest.

[QUOTE=jimcooncat]
4. Suggestions for stripping Windows 2000 of cruft?[/QUOTE]
Use Antivirus on the mailserver, not on the clients, same for Firewall. Set up a Cronjob for backup of the windows "My Documents" located in the Linux disk.
Strip down the unneeded services, there is a link for this in the howto above.

---

### Post by Lunde on 2005-07-02
[QUOTE=jimcooncat]I do tech for a small business with users on Windows and am building an Ubuntu environment to host Linux programs. I'm trying a variety of technologies for sharing, like Cygwin, FreeNX, VNC, etc.
[/QUOTE]

There is also the weird and wonderful world of wake on LAN, PXE boot and tftp servers. Create a pushable windows image that has all hardware drivers from the PC's in your network available. A solution like this demands similar disk setup from PC to PC. 
Then you can remote push a bootdisk that gets loaded over the network and auto-perform a diskcopy from a ready configured image on the server. 

Linux apps.. you could configure a remote login for that. or run VMware inside Windows if you need a full insatallation inside the client.

There are so many different solutions for setting up a network environment, it's just finding the solution that fits best for the type of company you are serving.

---

### Post by Karl S. on 2005-07-02
> **Lunde]Can you post the kqemu directory listing with 
$ ls -al
So that I can see the permissions?

And also, your cdrom is that a combined RW? if so, it might be that it's /dev/hdd[/QUOTE]

> karl@ubuntu:~/qemu-0.7.0/kqemu$ ls -al
total 260
drwxrwxr-x   3 karl karl  4096 2005-07-01 19:26 .
drwxrwxr-x  24 karl karl  4096 2005-07-01 19:16 ..
-rwxrwxr-x   1 karl karl   435 2005-02-12 09:36 install.sh
-rwxrwxr-x   1 karl karl  7366 2005-02-10 17:09 kmod.c
-rw-r--r--   1 karl karl  4588 2005-07-01 19:26 kmod.o
-rw-r--r--   1 karl karl  9392 2005-07-01 19:26 .kmod.o.cmd
-rwxrwxr-x   1 karl karl  4942 2005-02-20 13:51 kqemu-doc.html
-rwxrwxr-x   1 karl karl  3979 2005-02-20 13:51 kqemu-doc.texi
-rwxrwxr-x   1 karl karl  3013 2005-02-12 09:37 kqemu.h
-rw-r--r--   1 karl karl 45701 2005-07-01 19:26 kqemu.ko
-rw-r--r--   1 karl karl   178 2005-07-01 19:26 .kqemu.ko.cmd
-rw-r--r--   1 karl karl  1461 2005-07-01 19:26 kqemu.mod.c
-rwxrwxr-x   1 karl karl 36666 2005-01-31 17:05 kqemu-mod-i386.o
-rwxr-xr-x   1 karl karl 36666 2005-07-01 19:26 kqemu-mod.o
-rw-r--r--   1 karl karl  3424 2005-07-01 19:26 kqemu.mod.o
-rw-r--r--   1 karl karl  7062 2005-07-01 19:26 .kqemu.mod.o.cmd
-rw-r--r--   1 karl karl 42875 2005-07-01 19:26 kqemu.o
-rw-r--r--   1 karl karl   176 2005-07-01 19:26 .kqemu.o.cmd
-rwxrwxr-x   1 karl karl   639 2005-02-12 09:35 LICENSE
-rwxrwxr-x   1 karl karl  1028 2005-02-20 13:52 Makefile
-rwxrwxr-x   1 karl karl   185 2005-02-12 09:34 README
drwxr-xr-x   2 karl karl  4096 2005-07-01 19:26 .tmp_versions
karl@ubuntu:~/qemu-0.7.0/kqemu$

Incidentally, I'm pretty sure I have gcc installed (I just checked synaptic and has these listed as installed said:**
> karl@ubuntu:~/qemu-0.7.0/kqemu$ cd ..
karl@ubuntu:~/qemu-0.7.0$ qemu -boot d -cdrom /dev/hdd -hda /home/karl/Qemu/hd.img -user-net -pci -k en
Could not read keymap file: '/usr/local/share/qemu/keymaps/en'
karl@ubuntu:~/qemu-0.7.0$

I wonder what would happen if I didn't install the English keyboard (that's what would happen if I just left off the '-k en' yes?)? I'd try it, but I was assurance that I'm not going to make anything unuseable.

---

### Post by Lunde on 2005-07-02
[QUOTE=Karl S.]
 karl@ubuntu:~/qemu-0.7.0/kqemu$ ls -al
total 260
drwxrwxr-x 3 karl karl 4096 2005-07-01 19:26 .
drwxrwxr-x 24 karl karl 4096 2005-07-01 19:16 ..
-rwxrwxr-x 1 karl karl 435 2005-02-12 09:36 install.sh
-rwxrwxr-x 1 karl karl 7366 2005-02-10 17:09 kmod.c
-rw-r--r-- 1 karl karl 4588 2005-07-01 19:26 kmod.o
-rw-r--r-- 1 karl karl 9392 2005-07-01 19:26 .kmod.o.cmd
-rwxrwxr-x 1 karl karl 4942 2005-02-20 13:51 kqemu-doc.html
-rwxrwxr-x 1 karl karl 3979 2005-02-20 13:51 kqemu-doc.texi
-rwxrwxr-x 1 karl karl 3013 2005-02-12 09:37 kqemu.h
-rw-r--r-- 1 karl karl 45701 2005-07-01 19:26 kqemu.ko
-rw-r--r-- 1 karl karl 178 2005-07-01 19:26 .kqemu.ko.cmd
-rw-r--r-- 1 karl karl 1461 2005-07-01 19:26 kqemu.mod.c
-rwxrwxr-x 1 karl karl 36666 2005-01-31 17:05 kqemu-mod-i386.o
-rwxr-xr-x 1 karl karl 36666 2005-07-01 19:26 kqemu-mod.o
-rw-r--r-- 1 karl karl 3424 2005-07-01 19:26 kqemu.mod.o
-rw-r--r-- 1 karl karl 7062 2005-07-01 19:26 .kqemu.mod.o.cmd
-rw-r--r-- 1 karl karl 42875 2005-07-01 19:26 kqemu.o
-rw-r--r-- 1 karl karl 176 2005-07-01 19:26 .kqemu.o.cmd
-rwxrwxr-x 1 karl karl 639 2005-02-12 09:35 LICENSE
-rwxrwxr-x 1 karl karl 1028 2005-02-20 13:52 Makefile
-rwxrwxr-x 1 karl karl 185 2005-02-12 09:34 README
drwxr-xr-x 2 karl karl 4096 2005-07-01 19:26 .tmp_versions
karl@ubuntu:~/qemu-0.7.0/kqemu$
[/QUOTE]

OK.. you see the **-rw-r--r--** file permissions. this meens read only for other then your user. We need to change this to** -rwxrwxr-x** (executable). do another:

**$ sudo chmod -R 775 /home/karl/qemu-0.7.0/kqemu**

And try an

**$ ls -al **

and se if they still have **-rw-r--r--**. If not, I think you are good to give it another try.

If it's a problem with your cdrom, we can create an .iso from the CD and boot from that. This will also make the installastion quicker. You do that with:

**$ sudo mkisofs -RJ -o /home/karl/Qemu/winXP.iso /dev/cdrom**

If it comes up with **mkisofs: command not found** do:

**$ sudo apt-get install mkisofs**

Assuming that Qemu is the directory you created the hd.img in, if not change the above to fit your location.

Then for installing use:

**$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci -m 256**

---

### Post by Lunde on 2005-07-02
[QUOTE=Lunde]
**$ sudo chmod -R 775 /home/karl/qemu/kqemu**
[/QUOTE]

Correction: 
**$ sudo chmod -R 775 /home/karl/qemu-0.7.0/kqemu**

Sorry!

---

### Post by Karl S. on 2005-07-02
[QUOTE=Lunde]Correction: 
**$ sudo chmod -R 775 /home/karl/qemu-0.7.0/kqemu**

Sorry![/QUOTE]

Thank you so much for your help so far! I hope this is of benefit to other people.

So, I ran the chmod command you suggested above, and it worked (it changed the permissions of everything in the kqemu folder to -rwxrwxr-x).

Then tried the qemu -boot d -cdrom /dev/cdrom -hda /home/karl/Qemu/hd.img -user-net -pci (note that I chopped off the -k en command), and it seemed to be working for the first time. It inspected my hardware configuration, loaded files (all seeming to do with hardware), then said it was starting Windows, the 'Processing Information File,' then Welcome to Setup. Press Enter for installing Windows. I hit enter, I get the license agreement, I press F8, then asks me to hit enter when the XP CD's in the drive. It's in the drive (which, by the way, works fine for Ubuntu updates, so I know the drive is fine, at least sometimes...). Says it's loading file dosnet.inf, and then goes back to it saying that there's nothing in the drive.

So I tried creating the disk image. > 
karl@ubuntu:~/qemu-0.7.0$  sudo mkisofs -RJ -o /home/karl/Qemu/winXP.iso /dev/cdrom
Password:
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
Total translation table size: 0
Total rockridge attributes bytes: 256
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
181 extents written (0 MB)
karl@ubuntu:~/qemu-0.7.0$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci

And this is the problem I came up with:

In the Terminal:
[screenshot here](http://www.columbia.edu/~kts15/hblog/KarlQEMU.png)

Here are the contents of the Qemu folder:
> karl@ubuntu:~/Qemu$ ls -al
total 380
drwxr-xr-x   2 karl karl       4096 2005-07-02 14:37 .
drwxr-xr-x  69 karl karl       4096 2005-07-02 10:05 ..
-rw-r--r--   1 karl karl 4718592000 2005-07-02 14:27 hd.img
-rw-r--r--   1 root root     370688 2005-07-02 14:37 winXP.iso
karl@ubuntu:~/Qemu$

---

### Post by Lunde on 2005-07-02
Try this one:
delete the old winXP.iso
$ sudo rm /home/karl/Qemu/winXP.iso

Then...
$ mkisofs -r -R -J -l -L -o /home/karl/Qemu/winXP.iso /mnt/cdrom
Hopefully this will work.

---

### Post by Karl S. on 2005-07-02
[QUOTE=Lunde]Try this one:
delete the old winXP.iso
$ sudo rm /home/karl/Qemu/winXP.iso

Then...
$ mkisofs -r -R -J -l -L -o /home/karl/Qemu/winXP.iso /mnt/cdrom
Hopefully this will work.[/QUOTE]

Nope!
> karl@ubuntu:~$ sudo rm /home/karl/Qemu/winXP.iso
Password:
karl@ubuntu:~$ mkisofs -r -R -J -l -L -o /home/karl/Qemu/winXP.iso /mnt/cdrom
mkisofs: The option '-L' is reserved by POSIX.1-2001.
mkisofs: The option '-L' means 'follow all symbolic links'.
mkisofs: Mkisofs-2.02 will introduce POSIX semantics for '-L'.
mkisofs: Use -allow-leading-dots in future to get old mkisofs behavior.
Warning: creating filesystem that does not conform to ISO-9660.
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node - /mnt/cdrom
Just for the hell of it, I tried replacing /mnt/cdrom with /dev/cdrom is the above command. This created the iso in the Qemu folder, but $ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci gets me the same problem as before (pictured in the screenshot).

I think I'll leave this alone until tomorrow....

---

### Post by Lunde on 2005-07-02
[QUOTE=Karl S.]Nope!

Just for the hell of it, I tried replacing /mnt/cdrom with /dev/cdrom is the above command. This created the iso in the Qemu folder, but $ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci gets me the same problem as before (pictured in the screenshot).

I think I'll leave this alone until tomorrow....[/QUOTE]
 Sorry, copied of the net, forgot to change that. change **/mnt/cdrom** to** /cdrom** not /dev/cdrom

---

### Post by Karl S. on 2005-07-02
[QUOTE=Lunde]Try this one:
delete the old winXP.iso
$ sudo rm /home/karl/Qemu/winXP.iso

Then...
$ mkisofs -r -R -J -l -L -o /home/karl/Qemu/winXP.iso /mnt/cdrom
Hopefully this will work.[/QUOTE]

Okay, I tried this again, but this time with 
**$ mkisofs -r -R -J -l -L -o /home/karl/Qemu/winXP.iso /cdrom**

Then 
**$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci**

I got the same error as in my screenshot previously (I compared the live Qemu screen to the screenshot: they were the same),

Here's my commands from my Terminal:
> karl@ubuntu:~$ sudo rm /home/karl/Qemu/winXP.iso
Password:
karl@ubuntu:~$ mkisofs -r -R -J -l -L -o /home/karl/Qemu/winXP.iso /cdrom
mkisofs: The option '-L' is reserved by POSIX.1-2001.
mkisofs: The option '-L' means 'follow all symbolic links'.
mkisofs: Mkisofs-2.02 will introduce POSIX semantics for '-L'.
mkisofs: Use -allow-leading-dots in future to get old mkisofs behavior.
Warning: creating filesystem that does not conform to ISO-9660.
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
Total translation table size: 0
Total rockridge attributes bytes: 265
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
181 extents written (0 MB)
karl@ubuntu:~$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci -m 256
You do not have enough space in '/dev/shm' for the 256 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=272m none /dev/shm
karl@ubuntu:~$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci
karl@ubuntu:~$

This is some mystery!

---

### Post by Lunde on 2005-07-03
[QUOTE=Karl S.]Okay, I tried this again, but this time with 
**$ mkisofs -r -R -J -l -L -o /home/karl/Qemu/winXP.iso /cdrom**

Then 
**$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci**

I got the same error as in my screenshot previously (I compared the live Qemu screen to the screenshot: they were the same),

Here's my commands from my Terminal:


This is some mystery![/QUOTE]
 I don't understand what's going wrong with your CD drive in the first place.

**Option 1**

Another way of doing the same
$ cd /home/karl/Qemu
$ rm winXP.iso
$ umount /media/cdrom0
$ dd if=/dev/hdc of=winXP.iso

Ref: How to create an iso of your Ubuntu CD and use it as repository
[http://ubuntuforums.org/showthread.php?t=35807](http://ubuntuforums.org/showthread.php?t=35807)

**Option 2**

The way I did this with my win2000 installation is:
Reinsert the XP cd again..
$ mkdir /home/karl/Qemu/winXP
$ copy -ax /cdrom/* /home/karl/Qemu/winXP
$ rm /home/karl/Qemu/winXP.iso
$ mkisofs -r -o /home/karl/Qemu/winXP.iso /home/karl/Qemu/winXP

if this worked, you can delete the winXP directory under /home/karl/Qemu

More info on iso creation and CD burning:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

Hope it works out this time

**Memory**

I can see that you need some more memory. How much do you have?
[QUOTE=Karl S.]
karl@ubuntu:~$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci -m 256
You do not have enough space in '/dev/shm' for the 256 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=272m none /dev/shm
[/QUOTE]
Try this during the installation: 
$ sudo umount /dev/shm
$ sudo mount -t tmpfs -o size=272m none /dev/shm

---

### Post by Karl S. on 2005-07-03
Okay. I think I'm getting somewhere. I removed the old winXP.iso. Option 1 didn't work. When I **dd if=/dev/hdc of=winXP.iso** I got **dd: opening `/dev/hdc': No medium found**. So I tried option 2. But when I [B]karl@ubuntu:~/Qemu$ copy -ax /cdrom/* /home/karl/Qemu/winXP
[/B] I got **bash: copy: command not found**. So I decided to be tricky. Since the terminal just wasn't cooperating, I just opened up the CDROM window on the Desktop and selected all and moved it to /home/karl/Qemu/winXP. Then, when I **mkisofs -r -o /home/karl/Qemu/winXP.iso /home/karl/Qemu/winXP**, for the first time, I got some output that seemed to mean something!

> karl@ubuntu:~/Qemu$ mkisofs -r -o /home/karl/Qemu/winXP.iso /home/karl/Qemu/winXP
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
Using SCANS000.EXE;1 for  /home/karl/Qemu/winXP/valueadd/msft/usmt/scanstate_a.exe (scanstate.exe)
  1.81% done, estimate finish Sun Jul  3 11:48:21 2005
  3.62% done, estimate finish Sun Jul  3 11:48:48 2005
  5.44% done, estimate finish Sun Jul  3 11:48:57 2005
  7.25% done, estimate finish Sun Jul  3 11:49:02 2005
  9.06% done, estimate finish Sun Jul  3 11:49:05 2005
 10.87% done, estimate finish Sun Jul  3 11:49:06 2005
 12.68% done, estimate finish Sun Jul  3 11:49:16 2005
 14.50% done, estimate finish Sun Jul  3 11:49:16 2005
 16.31% done, estimate finish Sun Jul  3 11:49:16 2005
 18.12% done, estimate finish Sun Jul  3 11:49:16 2005
 19.93% done, estimate finish Sun Jul  3 11:49:11 2005
 21.74% done, estimate finish Sun Jul  3 11:49:11 2005
 23.55% done, estimate finish Sun Jul  3 11:49:07 2005
 25.37% done, estimate finish Sun Jul  3 11:49:08 2005
 27.17% done, estimate finish Sun Jul  3 11:49:08 2005
 28.99% done, estimate finish Sun Jul  3 11:49:12 2005
 30.80% done, estimate finish Sun Jul  3 11:49:12 2005
 32.61% done, estimate finish Sun Jul  3 11:49:16 2005
 34.42% done, estimate finish Sun Jul  3 11:49:16 2005
 36.23% done, estimate finish Sun Jul  3 11:49:16 2005
 38.04% done, estimate finish Sun Jul  3 11:49:18 2005
 39.86% done, estimate finish Sun Jul  3 11:49:18 2005
 41.67% done, estimate finish Sun Jul  3 11:49:18 2005
 43.48% done, estimate finish Sun Jul  3 11:49:18 2005
 45.29% done, estimate finish Sun Jul  3 11:49:18 2005
 47.10% done, estimate finish Sun Jul  3 11:49:18 2005
 48.92% done, estimate finish Sun Jul  3 11:49:18 2005
 50.73% done, estimate finish Sun Jul  3 11:49:18 2005
 52.54% done, estimate finish Sun Jul  3 11:49:18 2005
 54.35% done, estimate finish Sun Jul  3 11:49:18 2005
 56.16% done, estimate finish Sun Jul  3 11:49:17 2005
 57.97% done, estimate finish Sun Jul  3 11:49:19 2005
 59.79% done, estimate finish Sun Jul  3 11:49:19 2005
 61.59% done, estimate finish Sun Jul  3 11:49:19 2005
 63.41% done, estimate finish Sun Jul  3 11:49:19 2005
 65.22% done, estimate finish Sun Jul  3 11:49:19 2005
 67.03% done, estimate finish Sun Jul  3 11:49:19 2005
 68.84% done, estimate finish Sun Jul  3 11:49:20 2005
 70.66% done, estimate finish Sun Jul  3 11:49:20 2005
 72.47% done, estimate finish Sun Jul  3 11:49:18 2005
 74.28% done, estimate finish Sun Jul  3 11:49:18 2005
 76.09% done, estimate finish Sun Jul  3 11:49:18 2005
 77.90% done, estimate finish Sun Jul  3 11:49:18 2005
 79.71% done, estimate finish Sun Jul  3 11:49:18 2005
 81.53% done, estimate finish Sun Jul  3 11:49:18 2005
 83.33% done, estimate finish Sun Jul  3 11:49:18 2005
 85.15% done, estimate finish Sun Jul  3 11:49:18 2005
 86.96% done, estimate finish Sun Jul  3 11:49:18 2005
 88.77% done, estimate finish Sun Jul  3 11:49:19 2005
 90.58% done, estimate finish Sun Jul  3 11:49:19 2005
 92.39% done, estimate finish Sun Jul  3 11:49:18 2005
 94.20% done, estimate finish Sun Jul  3 11:49:20 2005
 96.02% done, estimate finish Sun Jul  3 11:49:19 2005
 97.83% done, estimate finish Sun Jul  3 11:49:19 2005
 99.64% done, estimate finish Sun Jul  3 11:49:19 2005
Total translation table size: 0
Total rockridge attributes bytes: 581166
Total directory bytes: 1193984
Path table size(bytes): 2234
Max brk space used 47d000
276000 extents written (539 MB)
karl@ubuntu:~/Qemu$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci

But then when I tried that last command, I got the same error message that I've been getting [screenshot](http://www.columbia.edu/~kts15/hblog/KarlQEMU.png).

At any rate, it looks as though I have an WinXP ISO on my computer now:
> karl@ubuntu:~/Qemu$ ls -al
total 552560
drwxr-xr-x   3 karl karl       4096 2005-07-03 11:48 .
drwxr-xr-x  71 karl karl       4096 2005-07-03 11:04 ..
-rw-r--r--   1 karl karl 4718592000 2005-07-02 14:27 hd.img
drwxr-xr-x   7 karl karl       4096 2005-07-03 11:47 winXP
-rw-r--r--   1 karl karl  565248000 2005-07-03 11:49 winXP.iso
karl@ubuntu:~/Qemu$

The question is: how do I make qemu look at this ISO rather than trying to find the CDROM that, for some reason, works just fine for Ubuntu updates but not for this stuff?

Oh. Memory: well -- and this is evidence of how little I know -- I'm not entirely sure how to check, but the System Monitor says I have 503 MB. 

One more thing: when it comes time for me to delete the /Qemu/winXP folder, I've never quite figured out how to delete folders (I use the **rmdir** command, right?) that have items still in them. How can I delete this folder without having to go in and delete everything in it one-by-one first?

---

### Post by Lunde on 2005-07-03
**Copy**
Sorry! My mistake.. Not "copy".. but **cp -ax /cdrom/* /home/karl/Qemu/winXP** for future reference.

**Boot with with winXP.iso as cdrom**
$ sudo umount /dev/shm
$ sudo mount -t tmpfs -o size=272m none /dev/shm
$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci -m 256

**Delete the winXP folder**
just delete it in Nautilus

---

### Post by Karl S. on 2005-07-03
The continuing saga....

[QUOTE=Lunde]**Copy**
Sorry! My mistake.. Not "copy".. but **cp -ax /cdrom/* /home/karl/Qemu/winXP** for future reference.

**Boot with with winXP.iso as cdrom**
$ sudo umount /dev/shm
$ sudo mount -t tmpfs -o size=272m none /dev/shm
$ qemu -boot d -cdrom /home/karl/Qemu/winXP.iso -hda /home/karl/Qemu/hd.img -user-net -pci -m 256[/QUOTE]
....well. I deleted the winxp folder and deleted the iso I just made. The **cp** command worked just fine. And then I made a new iso. I went through those commands above, and I ended up with the same error screen as shown in the screenshot linked to above. Is it that qemu doesn't want to use the iso that's in the Qemu directory and keeps looking to a cdrom?

...although it seems that once we get this working, it'll be a lot faster to install from an iso on my hard drive than one from a cdrom...

---

### Post by Lunde on 2005-07-03
[QUOTE=Karl S.]The continuing saga....


....well. I deleted the winxp folder and deleted the iso I just made. The **cp** command worked just fine. And then I made a new iso. I went through those commands above, and I ended up with the same error screen as shown in the screenshot linked to above. Is it that qemu doesn't want to use the iso that's in the Qemu directory and keeps looking to a cdrom?

...although it seems that once we get this working, it'll be a lot faster to install from an iso on my hard drive than one from a cdrom...[/QUOTE]
 Is there a copy block or something on the XP cd? did'nt think so, but... If you use the 
Give it a coupple of more tries booting from the CDrom

Option1
$ qemu -boot d -cdrom /cdrom -hda /home/karl/Qemu/hd.img -user-net -pci -m 256

Option2
$ qemu -boot d -cdrom /media/cdrom0 -hda /home/karl/Qemu/hd.img -user-net -pci -m 256

Option3
$ sudo umount /media/cdrom0
$ qemu -boot d -cdrom /dev/hdc -hda /home/karl/Qemu/hd.img -user-net -pci -m 256

---

### Post by slava on 2005-07-03
hello,
has anyone succeded booting a native win xp through qemu? my local xp in is on hdc1 so here is what i did: 
ln -s /dev/hdc1 winxp.img
sudo qemu -boot c -hda winxp.img -pci -m 256
the qemu window starts, correctly finding the windows disk, goes just pass
Booting from hard disk...
and than gets stuck with cpu running at 100%. i waited for a long time and it does not move any further
thank you
slava

---

### Post by Lunde on 2005-07-04
[QUOTE=slava]hello,
has anyone succeded booting a native win xp through qemu? my local xp in is on hdc1 so here is what i did: 
ln -s /dev/hdc1 winxp.img
sudo qemu -boot c -hda winxp.img -pci -m 256
the qemu window starts, correctly finding the windows disk, goes just pass
Booting from hard disk...
and than gets stuck with cpu running at 100%. i waited for a long time and it does not move any further
thank you
slava[/QUOTE]
 I don't think any of us ever did. Someone got as far as the xp progressbar, but that's all I know. 
It's possible with VMware. If it's win9X you try doing this with there is a known bug about the 100% cpu and a fix for it.
[http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC28](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC28)

If you have any success, please post the result here

---

### Post by Karl S. on 2005-07-04
[QUOTE=Lunde]Is there a copy block or something on the XP cd? did'nt think so, but... If you use the 
Give it a coupple of more tries booting from the CDrom

Option1
$ qemu -boot d -cdrom /cdrom -hda /home/karl/Qemu/hd.img -user-net -pci -m 256

Option2
$ qemu -boot d -cdrom /media/cdrom0 -hda /home/karl/Qemu/hd.img -user-net -pci -m 256

Option3
$ sudo umount /media/cdrom0
$ qemu -boot d -cdrom /dev/hdc -hda /home/karl/Qemu/hd.img -user-net -pci -m 256[/QUOTE]
Sorry to say this, but:
> karl@ubuntu:~$ qemu -boot d -cdrom /cdrom -hda /home/karl/Qemu/hd.img -user-net -pci -m 256
You do not have enough space in '/dev/shm' for the 256 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=272m none /dev/shm
karl@ubuntu:~$ umount /dev/shm
umount: /dev/shm is not in the fstab (and you are not root)
karl@ubuntu:~$ sudo umount /dev/shm
Password:
karl@ubuntu:~$ mount -t tmpfs -o size=272m none /dev/shm
mount: only root can do that
karl@ubuntu:~$ sudo mount -t tmpfs -o size=272m none /dev/shm
karl@ubuntu:~$ qemu -boot d -cdrom /cdrom -hda /home/karl/Qemu/hd.img -user-net -pci -m 256
qemu: could not open hard disk image '/cdrom'
karl@ubuntu:~$ qemu -boot d -cdrom /media/cdrom0 -hda /home/karl/Qemu/hd.img -user-net -pci -m 256
qemu: could not open hard disk image '/media/cdrom0'
karl@ubuntu:~$ sudo umount /media/cdrom0
karl@ubuntu:~$ qemu -boot d -cdrom /dev/hdc -hda /home/karl/Qemu/hd.img -user-net -pci -m 256
qemu: could not open hard disk image '/dev/hdc'
karl@ubuntu:~$ cd Qemu
karl@ubuntu:~/Qemu$ ls -al
total 552556
drwxr-xr-x   2 karl karl       4096 2005-07-03 14:12 .
drwxr-xr-x  71 karl karl       4096 2005-07-04 10:03 ..
-rw-r--r--   1 karl karl 4718592000 2005-07-02 14:27 hd.img
-rw-r--r--   1 karl karl  565248000 2005-07-03 14:11 winXP.iso
I'm pretty befuddled. If the iso is on my computer, why shouldn't qemu be able to use it?

The winXP CD is an XP Professional Academic Edition with SP1 on it, which I purchased myself. I've installed this copy on both computers in the house, so I know it works...

---

### Post by Lunde on 2005-07-04
[QUOTE=Karl S.]Sorry to say this, but:

I'm pretty befuddled. If the iso is on my computer, why shouldn't qemu be able to use it?

The winXP CD is an XP Professional Academic Edition with SP1 on it, which I purchased myself. I've installed this copy on both computers in the house, so I know it works...[/QUOTE]
 The problem is to get the boot sector right in the .iso. There is an option to boot from a floppy, It's a long time since i did that with XP and I'm not sure how to do that in Qemu, but I'll see if I can find out.

It might be easier if I help you out over Gaim. My msn is: [email]do_not_send_to_this_email@hotmail.com[/email]

---

### Post by tepegoz on 2005-07-05
Hello to all,
First of all, I should mention that this tutorial is really great, and will be very usefull for many linux users.
My question is this: I succesfully compiled and installed qemu with kqemu support, there is no warning, no error, everything is good. However when I start qemu, it drains all the cpu power, waits there.  No window appears.  I tried many different methods to run qemu, but nothing has changed.  I found in one of the forums that this may be due to libsdl.  
Has anybody faced such a problem?

Helps will be appreciated.

---

### Post by Lunde on 2005-07-05
[QUOTE=tepegoz]Hello to all,
First of all, I should mention that this tutorial is really great, and will be very usefull for many linux users.
My question is this: I succesfully compiled and installed qemu with kqemu support, there is no warning, no error, everything is good. However when I start qemu, it drains all the cpu power, waits there.  No window appears.  I tried many different methods to run qemu, but nothing has changed.  I found in one of the forums that this may be due to libsdl.  
Has anybody faced such a problem?

Helps will be appreciated.[/QUOTE]
 Can you cut and paste the commands you use, and check the /var/log/syslog for errors related to this problem?

---

### Post by tepegoz on 2005-07-05
I used the commands in the tutorial.  That is: 
[COLOR=Blue]qemu -boot d -cdrom /dev/cdrom -hda hd.img[/COLOR]
I also tried commands like this:
[COLOR=Blue]qemu -boot d -cdrom /home/tepegoz/kubuntu-hoary-live-i386.iso -hda hd.img[/COLOR]

Nothing happens, no log, no window, nothing.  It seems that there is not any related information in syslog. Is there any other qemu log file?

Thanks in advance.

---

### Post by tepegoz on 2005-07-06
[QUOTE=tepegoz]I used the commands in the tutorial.  That is: 
[COLOR=Blue]qemu -boot d -cdrom /dev/cdrom -hda hd.img[/COLOR]
I also tried commands like this:
[COLOR=Blue]qemu -boot d -cdrom /home/tepegoz/kubuntu-hoary-live-i386.iso -hda hd.img[/COLOR]

Nothing happens, no log, no window, nothing.  It seems that there is not any related information in syslog. Is there any other qemu log file?

Thanks in advance.[/QUOTE]

The problem is solved by installing libsdl1.2debian-alsa insted of oss.  What is the difference between oss and alsa standards of libsdl, any idea?

---

### Post by Lunde on 2005-07-06
[QUOTE=tepegoz]The problem is solved by installing libsdl1.2debian-alsa insted of oss.  What is the difference between oss and alsa standards of libsdl, any idea?[/QUOTE]
 Glad you found the solution, somehow your previous post did'nt show up in my e-mail so I did'nt see it before now, sorry.

Howto: about sound in Hoary & Linux (I guess this answere your question)
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

---

### Post by tepegoz on 2005-07-06
This is really great to have dreamweaver and visio in linux. I don't need to reboot anymore :)
Thanks Lunde

---

### Post by Lunde on 2005-07-06
Thank you

---

### Post by lannick on 2005-07-06
Hi,

Thank you for this tutorial about the using of qemu.

Here is my problem.
I have winxp on hda1 (ntfs)
ubuntu on hda

I have linked hda to /home/lannick/windows/symlink.img

When I boot qemu I have the GRUB page and can select winxp but after I have this screen

'Booting Microsoft windows XP'

root (hd0,0)
Filesystem type unknow, partition type 0x7
Save default
Make active
Chainloader +1

Err. lecteur disque
Entrez CTRL+ALT+SUPPR pour redémarrer


If someone have an idea.

Thank you,
Lannick

---

### Post by Lunde on 2005-07-06
[QUOTE=lannick]Hi,

Thank you for this tutorial about the using of qemu.

Here is my problem.
I have winxp on hda1 (ntfs)
ubuntu on hda

I have linked hda to /home/lannick/windows/symlink.img

When I boot qemu I have the GRUB page and can select winxp but after I have this screen

'Booting Microsoft windows XP'

root (hd0,0)
Filesystem type unknow, partition type 0x7
Save default
Make active
Chainloader +1

Err. lecteur disque
Entrez CTRL+ALT+SUPPR pour redémarrer


If someone have an idea.

Thank you,
Lannick[/QUOTE]
 I assume you have read some of the post here in this tread and know some of the problems this may cause. I don't think any of us ever managed to boot a native Windows. I still belive it's possible, but I don't have the disks to try. VMware can do it.

Anyway, I'll try to help you as much as I can if you want to continue trying.

Have you tried to make a symlink to /dev/hda1? someone reported getting to the progressbar in XP.

Maybe, because of problems with the bootloader it's a solution to create an empty small -hda and install a bootloader to it. Then use the symlink as -hdb, this way is more safe.

How is your disk structure? Win on hda1, and the rest?

---

### Post by lannick on 2005-07-07
[QUOTE=Lunde]I assume you have read some of the post here in this tread and know some of the problems this may cause. I don't think any of us ever managed to boot a native Windows. I still belive it's possible, but I don't have the disks to try. VMware can do it.

Anyway, I'll try to help you as much as I can if you want to continue trying.

Have you tried to make a symlink to /dev/hda1? someone reported getting to the progressbar in XP.

Maybe, because of problems with the bootloader it's a solution to create an empty small -hda and install a bootloader to it. Then use the symlink as -hdb, this way is more safe.

How is your disk structure? Win on hda1, and the rest?[/QUOTE]

Hi Lunde,

Thank you for your answer.

Here are my partitions
hda1 - windows (ntfs)
hda2 - windows data (ntfs)
hda5 - linux (/)
hda6 - swap linux
hda7 - linux (/home)

I think I am going to test xp with a virtual installation on my home partition. I have started the install, it seem to work well but I have not enough disk space left.
I will reorganize my partitions and give you my results.

Best regards,
Lannick

---

### Post by Lunde on 2005-07-07
[QUOTE=lannick]Hi Lunde,

Thank you for your answer.

Here are my partitions
hda1 - windows (ntfs)
hda2 - windows data (ntfs)
hda5 - linux (/)
hda6 - swap linux
hda7 - linux (/home)

I think I am going to test xp with a virtual installation on my home partition. I have started the install, it seem to work well but I have not enough disk space left.
I will reorganize my partitions and give you my results.

Best regards,
Lannick[/QUOTE]
 WInXP is a bit slow on Qemu, alot faster on VMware. Win2000 is the best choice I think for Qemu if you have an old CD laying around.

---

### Post by Remix_88 on 2005-07-07
Thank you very much for posting this HOW TO. Until today I had never heard of Qemu, it is _perfect_ for my needs.

I now have it running WinXP SP2 from a hard disk image and I can now perform all my support functions at work without dual booting or having to explain to someone at work why they need to stump up the cash for a VMware license to support my Linux habbit :wink: 

I will install Breezy into another disk image later tonight and give that a whirl. I am so pleased I can test Breezy without having to risk trashing my (very) stable Hoary setup.

---

### Post by Lunde on 2005-07-07
[QUOTE=Remix_88]Thank you very much for posting this HOW TO. Until today I had never heard of Qemu, it is _perfect_ for my needs.

I now have it running WinXP SP2 from a hard disk image and I can now perform all my support functions at work without dual booting or having to explain to someone at work why they need to stump up the cash for a VMware license to support my Linux habbit :wink: 

I will install Breezy into another disk image later tonight and give that a whirl. I am so pleased I can test Breezy without having to risk trashing my (very) stable Hoary setup.[/QUOTE]
 Glad you're happy. Let me know how it goes with Breezy. It should'nt be any problems. I ran Knoppix and Ubuntu Server with success.

---

### Post by arnieboy on 2005-07-07
I have been running Windows XP service Pack 2 (it even supports hibernation wow!) without any problems on qemu but I have not been able to get my sound card working. Its an integrated VIA sound card on a PM800-M2 motherboard. -enable sound does not help. I will give it a try again tonight and see if I can make it work.
I have followed the tutorials on how to make duplex sounds work with Alsa..
Thanks for the detailed tutorial lunde.

---

### Post by Lunde on 2005-07-07
[QUOTE=arnieboy]I have been running Windows XP service Pack 2 (it even supports hibernation wow!) without any problems on qemu but I have not been able to get my sound card working. Its an integrated VIA sound card on a PM800-M2 motherboard. -enable sound does not help. I will give it a try again tonight and see if I can make it work.
I have followed the tutorials on how to make duplex sounds work with Alsa..
Thanks for the detailed tutorial lunde.[/QUOTE]
 The sound in Qemu has nothingto do with your soundcard, the linux sound driver is "transfering" the sound to your card, Qemu emulates a Soundblaster 16 card. Windows should recognize this card during the installation, but check in the Device Manager to be sure.

Does this help, As mentioned not a perfect solution, but it's a start to locate the problem (2 posts by Agent, check also the one below this post)
[http://ubuntuforums.org/showthread.php?p=207948&highlight=sound#post207948](http://ubuntuforums.org/showthread.php?p=207948&highlight=sound#post207948)

Here's another post, but I belive he did exactly the same as you did.
[http://ubuntuforums.org/showthread.php?p=205044&highlight=sound#post205044](http://ubuntuforums.org/showthread.php?p=205044&highlight=sound#post205044)

Did that temporarly fix the problem? if so, then we know what to look for..

---

### Post by arnieboy on 2005-07-07
Hey Lunde, Thanks A LOT! I was able to get sound working as well by emulating as SB16!  Thanks a Ton!
Now I have just one more question before am all set. I tried to set up samba by following ubuntuguide.org and the posts on this forum. Samba is up and running. I have shared a folder in my home folder and called it "share"
thus the path of it is: /home/myname/share.
Now i run qemu as follows:
sudo qemu -boot c -hda /home/myname/Qemu/hd.img -enable-audio -user-net -smb share -pci -m 256

Windows XP starts and when it boots up, I open a command prompt and type:
net use e: \\10.0.2.2\share
It asks for my username and password which I enter.
Then it throws up error "53" saying that it cannot find the network path.
Please help on this one. Thanks in advance.

---

### Post by Lunde on 2005-07-07
[QUOTE=arnieboy]Hey Lunde, Thanks A LOT! I was able to get sound working as well by emulating as SB16!  Thanks a Ton!
Now I have just one more question before am all set. I tried to set up samba by following ubuntuguide.org and the posts on this forum. Samba is up and running. I have shared a folder in my home folder and called it "share"
thus the path of it is: /home/myname/share.
Now i run qemu as follows:
sudo qemu -boot c -hda /home/myname/Qemu/hd.img -enable-audio -user-net -smb share -pci -m 256

Windows XP starts and when it boots up, I open a command prompt and type:
net use e: \\10.0.2.2\share
It asks for my username and password which I enter.
Then it throws up error "53" saying that it cannot find the network path.
Please help on this one. Thanks in advance.[/QUOTE]
 instead of **net use** just try to type in the address bar of IE or win.. explorer **\\10.0.2.2** that will bring up the shared folders in Ubuntu

..strange IP address, I don't remember completly the emulated network of Qemu, but check in the Command prompt:
**ipconfig**, then the IP of your host should be first in range.. xxx.xxx.xxx.1

---

### Post by arnieboy on 2005-07-07
hey thanks a lot again Lunde! Got the samba share up and working too. 
:)

---

### Post by Lunde on 2005-07-08
[QUOTE=arnieboy]hey thanks a lot again Lunde! Got the samba share up and working too. 
:)[/QUOTE]
 Just for the record, what was the complete path? I use VMware again for windows now, so I have no way to check?

---

### Post by arnieboy on 2005-07-08
[QUOTE=Lunde]Just for the record, what was the complete path? I use VMware again for windows now, so I have no way to check?[/QUOTE]

Sorry didnt get your question... complete path of what? my shared folder? that I have already mentioned in one of my posts.. but it must be something else u are asking about.

---

### Post by Lunde on 2005-07-08
[QUOTE=arnieboy]Sorry didnt get your question... complete path of what? my shared folder? that I have already mentioned in one of my posts.. but it must be something else u are asking about.[/QUOTE]
Sorry, I refrase my question: what was the solution to the network problem? I sort of just dropped out some ideas and what I remembered from when I did it earlier

---

### Post by arnieboy on 2005-07-08
[QUOTE=Lunde]Sorry, I refrase my question: what was the solution to the network problem? I sort of just dropped out some ideas and what I remembered from when I did it earlier[/QUOTE]
aah. ok. well the solution was quite easy. I just opened windows explorer and typed in \\10.0.2.2 and that opened up the shared folders.
Thanks for the hint again.

---

### Post by Lunde on 2005-07-08
[QUOTE=arnieboy]aah. ok. well the solution was quite easy. I just opened windows explorer and typed in \\10.0.2.2 and that opened up the shared folders.
Thanks for the hint again.[/QUOTE]
 Thanks! There's a lot of people asking questions here in this tread so I just try to memorize the solutions.

---

### Post by Tad030 on 2005-07-13
just curious, but would WindowsXP run faster from a disc image saved on the hard drive, compared to a cdrom, or does that matter?  

The install worked great for me, I'm now at the customization stage.  Thanks for this Howto. 


Tad

---

### Post by arnieboy on 2005-07-13
[QUOTE=Tad030]just curious, but would WindowsXP run faster from a disc image saved on the hard drive, compared to a cdrom, or does that matter?  

The install worked great for me, I'm now at the customization stage.  Thanks for this Howto. 


Tad[/QUOTE]
It cant work from a cdrom because the image would then become read only.

---

### Post by Lunde on 2005-07-13
[QUOTE=Tad030]just curious, but would WindowsXP run faster from a disc image saved on the hard drive, compared to a cdrom, or does that matter?  

The install worked great for me, I'm now at the customization stage.  Thanks for this Howto. 


Tad[/QUOTE]
 The XP installer will probably run a lot faster from an .iso image on your disk if that's what you meen. 

Glad you liked the Howto

---

### Post by Tad030 on 2005-07-13
[QUOTE=Lunde]The XP installer will probably run a lot faster from an .iso image on your disk if that's what you meen. 

Glad you liked the Howto[/QUOTE]

That is what I meant.  Thanks.

---

### Post by traherom on 2005-07-13
I'm wondering if anyone else has managed to do this from a "recovery" or "restore" CD, like the ones that often come with pre-built computers. I'm trying to use my laptop's recovery CD with this, but I get a little error...

Everything loads fine, the recovery agent (by PCAngel) pops up, does a few things, but suddenly tells me to "Please Insert System Restore DVD #1 now." Well... it is in. Any ideas?

It could be that this is the result of check to see if the computer it is being used on is the correct one (it may think it's not because the disk size appears much smaller), but I'd hope it would give a more informative message. :|

---

### Post by Lunde on 2005-07-14
[QUOTE=traherom]I'm wondering if anyone else has managed to do this from a "recovery" or "restore" CD, like the ones that often come with pre-built computers. I'm trying to use my laptop's recovery CD with this, but I get a little error...

Everything loads fine, the recovery agent (by PCAngel) pops up, does a few things, but suddenly tells me to "Please Insert System Restore DVD #1 now." Well... it is in. Any ideas?

It could be that this is the result of check to see if the computer it is being used on is the correct one (it may think it's not because the disk size appears much smaller), but I'd hope it would give a more informative message. :|[/QUOTE]
 I did it with a HP recovery CD form a Laptop, worked fine. But, the problem is that if your recovery CD expects to find spesific hardware. Qemu emulates the hardware so it's nothing like the original hardware even tho it's the same laptop. The disk is now an image in a folder, the screen card is an emulated Cirrus Logic, the Sound is an emulated SB16, Network is viritual etc.. 

I suggest, if you are able to boot Normal or in Safe mode, to remove PC angel and all the software that came with your recovery CD. If not, at which stange of the installation does it stop?

---

### Post by traherom on 2005-07-14
[quote=Lunde]I suggest, if you are able to boot Normal or in Safe mode, to remove PC angel and all the software that came with your recovery CD. If not, at which stange of the installation does it stop?[/QUOTE]It doesn't even begin to install files. It goes through the pre-recovery steps, but as soon as it gets to the step where it actually copies stuff, it tells me to insert the DVD...

---

### Post by Lunde on 2005-07-14
[QUOTE=traherom]It doesn't even begin to install files. It goes through the pre-recovery steps, but as soon as it gets to the step where it actually copies stuff, it tells me to insert the DVD...[/QUOTE]
 Thats a problem with the recovery CD's.. if you have enought disk space, there's an option that might work. Keep in mind that I've never done this and don't know the result.
[B]
Experimental[/B]
There's a possibuility that it might work to **dd** (image copy) the partition you already have installed XP to. The reason I think this might work is that you may just as well make a disk image with dd, then the qemu option used in this howto. 

**Hardware problem:**
If you try this, you most likely have to boot with safemode and delete drivers for your Screen card, sound card, etc.

**Disk space:**
with dd the image can be made so that it expands with the size of the disk, this meens that your result of the dd image copy may be smaller then the actual disk / partition you are copying from. At least it works like that when you create an empty image.

dd if=/dev/hda1 of=/home/username/location_of_diskimage.img

More detailed description of dd here:
[http://www.cpqlinux.com/ddbackup.html](http://www.cpqlinux.com/ddbackup.html)

---

### Post by traherom on 2005-07-14
Would it work to use someone else's XP install CD, but use the CD key on my laptop? It would be legal, because I do own it, I just can't get it to install. :D

Worth a try, anyway. I know someone who has their CD where I'll be tomorrow. :)

---

### Post by Lunde on 2005-07-14
[QUOTE=traherom]Would it work to use someone else's XP install CD, but use the CD key on my laptop? It would be legal, because I do own it, I just can't get it to install. :D

Worth a try, anyway. I know someone who has their CD where I'll be tomorrow. :)[/QUOTE]
 I afraid it might not work, different registration keys. Most recovery cd's have a seperate range of keys. And there also may be problems with the activation.

---

### Post by traherom on 2005-07-17
I got Windows installed by borrowing a friend's disk. Thanks!

---

### Post by Lunde on 2005-07-17
[QUOTE=traherom]I got Windows installed by borrowing a friend's disk. Thanks![/QUOTE]
 Glad it worked out for you

---

### Post by edemark on 2005-07-17
[QUOTE=Lunde]Glad it worked out for you[/QUOTE]
 Hi everybody just a quick question: 
How to remove an earlyer installation that was done with make install?

I have tried make uninstall but it did not work
I am just asking as i have to reinstall it.

Thanks

---

### Post by Lunde on 2005-07-18
[QUOTE=edemark]Hi everybody just a quick question: 
How to remove an earlyer installation that was done with make install?

I have tried make uninstall but it did not work
I am just asking as i have to reinstall it.

Thanks[/QUOTE]
 I suppose you used: 
$sudo make uninstall

I was pretty sure that would work, but I had the same problem after a kernel upgrade (Silly me), and I thought that was the reason it did'nt work.

I posted a question to the user forum of Qemu and will let you know as soon as i get an answere.

What's the reason for the reinstall? It may not be the best solution, but I thnk it's a possibuility to run another on top if it's not working.

---

### Post by edemark on 2005-07-18
[QUOTE=Lunde]I suppose you used: 
$sudo make uninstall

I was pretty sure that would work, but I had the same problem after a kernel upgrade (Silly me), and I thought that was the reason it did'nt work.

I posted a question to the user forum of Qemu and will let you know as soon as i get an answere.

What's the reason for the reinstall? It may not be the best solution, but I thnk it's a possibuility to run another on top if it's not working.[/QUOTE]
 My problem is that i started to make things before reading. So I have ended up with some warning message at the end of make (this issue was covered earlier in this thread ONE SHALL ALLWAYS READ FIRST) it is an issue related to permissions of kquemu. I did not have the right permissions while make and make install even though i did it so with sudo.
So I just would like to remove it, correct permissions, make again and make install again.

Pd would it be possible removing manually all parts (i know mayor part is in /usr/local)?

thanks

---

### Post by Lunde on 2005-07-18
Just overwrite on top, that should be OK.

As for removing, I'll have to get back to that.

---

### Post by deng on 2005-07-18
Im intrested with this topics but im begginer for all this... 

now i keep my eyes to all thats required installer... Not free .. freee.. not free...

brb...will tell u later...

---

### Post by Lunde on 2005-07-18
[QUOTE=deng]Im intrested with this topics but im begginer for all this... 

now i keep my eyes to all thats required installer... Not free .. freee.. not free...

brb...will tell u later...[/QUOTE]
 Qemu with Kqemu is free, but you are required to have a Windows install CD, preferably not a recovery CD delivered with new PC's, but also some of these works fine.

---

### Post by edemark on 2005-07-19
[QUOTE=Lunde]Just overwrite on top, that should be OK.

As for removing, I'll have to get back to that.[/QUOTE]
 Thanks Lunde it worked

I was able to reinstall qemu with kqemu and then i installed 2k.

---

### Post by Lunde on 2005-07-19
[QUOTE=edemark]Thanks Lunde it worked

I was able to reinstall qemu with kqemu and then i installed 2k.[/QUOTE]
 Great! Let me know if you have any other problems.
I'm still waiting for an answere on the uninstall

---

### Post by edemark on 2005-07-20
[QUOTE=Lunde]Great! Let me know if you have any other problems.
I'm still waiting for an answere on the uninstall[/QUOTE]
 If problem I have one think in mind. I just can not understand how to change cds while vvin is running. In other words the only cd it sees is the one that was inserted before starting up the guest os.

Is there any way to change cds or will i have to carry on with restarting the guest os to be able to change cds?

thanks

---

### Post by Lunde on 2005-07-20
Sounds very strange.. Even if you do a F5 (Refresh) in explorer? Qemu mounts the CDROM /dev/cdrom if you choose so in the startup command. So it should be just to eject and insert a new CD.. but maybe do a refresh in windows

---

### Post by edemark on 2005-07-20
[QUOTE=Lunde]Sounds very strange.. Even if you do a F5 (Refresh) in explorer? Qemu mounts the CDROM /dev/cdrom if you choose so in the startup command. So it should be just to eject and insert a new CD.. but maybe do a refresh in windows[/QUOTE]
 Ok so my story then a bit strange as qemu would not strt witn -cdrom /dev/cdrom if there is no cd in the drive it would just give an error message stating that it can not find a bootable image in the cdrom. I get this error even that i am booting hd.img. If I put a cd in the drive qemu boots perfectly the hd.img

any idea?

thanks

---

### Post by arnieboy on 2005-07-20
[QUOTE=edemark]Ok so my story then a bit strange as qemu would not strt witn -cdrom /dev/cdrom if there is no cd in the drive it would just give an error message stating that it can not find a bootable image in the cdrom. I get this error even that i am booting hd.img. If I put a cd in the drive qemu boots perfectly the hd.img

any idea?

thanks[/QUOTE]
it wont start with the cdrom option unless u have a cd entered in ur cdrom drive. if u dont need a cd u can start qemu without the -cdrom option... but if u do that u wont be able to access ur cdrom drive thru qemu once the emulator starts.

---

### Post by Lunde on 2005-07-21
I'm not running Qemu anymore so I can't try to reproduce that problem. It sounds very strange, I can't remember having any such problems.

Can you post the command you use to start Qemu?

---

### Post by edemark on 2005-07-21
[QUOTE=Lunde]I'm not running Qemu anymore so I can't try to reproduce that problem. It sounds very strange, I can't remember having any such problems.

Can you post the command you use to start Qemu?[/QUOTE]
 the command i use is the following
qemu -boot c -cdrom /dev/cdrom -hda hd.img -m 192 -pci -enable-audio

hope this helps
thanks

---

### Post by Lunde on 2005-07-21
[QUOTE=edemark]the command i use is the following
qemu -boot c -cdrom /dev/cdrom -hda hd.img -m 192 -pci -enable-audio

hope this helps
thanks[/QUOTE]
 is it still the same if you use 
**-cdrom /media/cdrom0** in the "end" of the command (No symlinks)

Also what you can try is:
If you start qemu from terminal, in the terminal window after qemu starts you can now type commands to qemu. Type:
**eject cdrom**
then:
**cdrom /dev/cdrom**

---

### Post by Kakalto on 2005-07-21
I could install WinXP onto Qemu, then use it to access my NTFS partitions from my real XP, right?

---

### Post by digiital on 2005-07-22
Maybe I missed something, but has anyone figured out how to get it to boot xp already on the HD? Trying to use the copy of xp I have already installed on this laptop. With somewhat limited HD space, I really can't afford to have another 2-3 gig image file.

Thanks.

---

### Post by Lunde on 2005-07-22
[QUOTE=Kakalto]I could install WinXP onto Qemu, then use it to access my NTFS partitions from my real XP, right?[/QUOTE]
 Not with SMB networking, because it's linux that shares the ntfs partition. I don't know about symlinks, might work:

**$ ln -s /dev/hdXX /home/username/Qemu/ntfs.img**
(Where XX is your ntfs partition and username is your username)
[B]
-hdb /home/username/Qemu/ntfs.img[/B]

---

### Post by Lunde on 2005-07-22
[QUOTE=digiital]Maybe I missed something, but has anyone figured out how to get it to boot xp already on the HD? Trying to use the copy of xp I have already installed on this laptop. With somewhat limited HD space, I really can't afford to have another 2-3 gig image file.

Thanks.[/QUOTE]
 Not that I know of, got close, but never worked completely. VMware can do that.

---

### Post by digiital on 2005-07-22
Ok thanks Lunde, just wanted to make sure I didn't miss something with the 22 pages of this thread.

[QUOTE=Lunde]Not that I know of, got close, but never worked completely. VMware can do that.[/QUOTE]

---

### Post by SuperMike on 2005-07-24
Lunde, do you have an idea how Qemu stacks up against Xen? Also, I've installed Wine pretty well, added in the MFC* DLLs from W2K into the System32 directory, and then got JASC Paintshop Pro 4 working fairly well. At my office, I use tsclient and rdesktop to connect to a regular Windows station. Saves the hassle.

On a side note, I've got a bad deal at my office. They either want me to install Novell Linux Desktop, or Windows XP. Since I only like Ubuntu, I'm thinking of installing Xen (if I can ever figure it out) and then get it to load up Novell Linux Desktop inside it in full screen mode. That should satisfy the nosy systems auditor who flies in from Calif. occasionally.

---

### Post by Lunde on 2005-07-25
[QUOTE=SuperMike]Lunde, do you have an idea how Qemu stacks up against Xen? Also, I've installed Wine pretty well, added in the MFC* DLLs from W2K into the System32 directory, and then got JASC Paintshop Pro 4 working fairly well. At my office, I use tsclient and rdesktop to connect to a regular Windows station. Saves the hassle.

On a side note, I've got a bad deal at my office. They either want me to install Novell Linux Desktop, or Windows XP. Since I only like Ubuntu, I'm thinking of installing Xen (if I can ever figure it out) and then get it to load up Novell Linux Desktop inside it in full screen mode. That should satisfy the nosy systems auditor who flies in from Calif. occasionally.[/QUOTE]
 I'm not to familiar with Xen, But VMware may be a good solution for you. VMware is definitly the fastes solution for proffesional use I have tried. 

[http://www.novell.com/coolsolutions/qna/1805.html](http://www.novell.com/coolsolutions/qna/1805.html)

---

### Post by Bramme on 2005-07-27
it's possible that this question is already asked,but i don't have the time for reading 22 pages, sorry :s

is the emulation much slower when the guest OS image is on another partition ? (on the same physical harddisk)

because this partition is full ... :(

---

### Post by Lunde on 2005-07-27
[QUOTE=Bramme]it's possible that this question is already asked,but i don't have the time for reading 22 pages, sorry :s

is the emulation much slower when the guest OS image is on another partition ? (on the same physical harddisk)

because this partition is full ... :([/QUOTE]
 I'm sure that's no difference, A lot of people (including me) use /home as a seperate partition and run it from  there.

---

### Post by geearf on 2005-07-29
Hello,

thanks for this how to, it was very usefull.

But maybe you should add something about the problem with x86 computers and the new 0.71, i had to do so : 

change the function kqemu_vmalloc in the file kqemu-linux.c like this:

void * CDECL kqemu_vmalloc(unsigned int size)
{
//return __vmalloc(size, GFP_KERNEL, PAGE_KERNEL_EXEC);
return __vmalloc(size, GFP_KERNEL, PAGE_KERNEL);
}

---

### Post by kLy on 2005-07-30
Hi

When trying to ./configure I get this:
```

kbuild type       2.6
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.

```

I did install libsdl1.2-dev :( What's wrong?

---

### Post by kLy on 2005-07-30
[QUOTE=kLy]Hi

When trying to ./configure I get this:
```

kbuild type       2.6
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.

```

I did install libsdl1.2-dev :( What's wrong?[/QUOTE]
 ok I got the above fixed somehow and it installed. But if I try to modprobe kqemu, I get this in dmesg:

kqemu: Unknown symbol __PAGE_KERNEL_EXEC

:(

What's up?

---

### Post by Lunde on 2005-07-30
[QUOTE=geearf]Hello,

thanks for this how to, it was very usefull.

But maybe you should add something about the problem with x86 computers and the new 0.71, i had to do so : 

change the function kqemu_vmalloc in the file kqemu-linux.c like this:

void * CDECL kqemu_vmalloc(unsigned int size)
{
//return __vmalloc(size, GFP_KERNEL, PAGE_KERNEL_EXEC);
return __vmalloc(size, GFP_KERNEL, PAGE_KERNEL);
}[/QUOTE]
 Thanx geearf

Just want to make sure I don't add anything without being sure. If I understand correctly, this is a problem that occures to all X86 PCs? Can you explain this a bit more?

---

### Post by Lunde on 2005-07-30
[QUOTE=kLy]ok I got the above fixed somehow and it installed. But if I try to modprobe kqemu, I get this in dmesg:

kqemu: Unknown symbol __PAGE_KERNEL_EXEC

:(

What's up?[/QUOTE]
 I guess this is a bug that's fixed in a new version

```

kqemu 0.7.1-1
From: Fabrice Bellard <fabrice <at> bellard.org>
Subject: kqemu 0.7.1-1
Newsgroups: gmane.comp.emulators.qemu
Date: 2005-07-28 22:31:24 GMT

A new version of kqemu is available.

version 0.7.1-1:

- FreeBSD compile fixes - added x86_64 support
- __PAGE_KERNEL_EXEC fix for Linux 2.6

Fabrice.

```

---

### Post by samjam on 2005-07-30
[QUOTE=Remix_88]Thank you very much for posting this HOW TO. Until today I had never heard of Qemu, it is _perfect_ for my needs.

I now have it running WinXP SP2 from a hard disk image and I can now perform all my support functions at work without dual booting or having to explain to someone at work why they need to stump up the cash for a VMware license to support my Linux habbit :wink: 

I will install Breezy into another disk image later tonight and give that a whirl. I am so pleased I can test Breezy without having to risk trashing my (very) stable Hoary setup.[/QUOTE]

So any tips?
I can't get XP SP1 to run.
In safe mode it gets stuck just afdter it loads Mup.sys whatever that is, or sometimes NDIS.sys
 
Sam

---

### Post by kLy on 2005-07-30
[QUOTE=Lunde]I guess this is a bug that's fixed in a new version

```

kqemu 0.7.1-1
From: Fabrice Bellard <fabrice <at> bellard.org>
Subject: kqemu 0.7.1-1
Newsgroups: gmane.comp.emulators.qemu
Date: 2005-07-28 22:31:24 GMT

A new version of kqemu is available.

version 0.7.1-1:

- FreeBSD compile fixes - added x86_64 support
- __PAGE_KERNEL_EXEC fix for Linux 2.6

Fabrice.

```[/QUOTE]
 oh ok. Where can I get this? It's not on the official site

---

### Post by kLy on 2005-07-30
ok sorry. it is. it's the KQemu module. thx

---

### Post by kLy on 2005-07-30
crap. there isn't a "make uninstall" ! arg!

Now there's a zillion files lying all over my system that I don't know where to find to get rid of :( This is why I hate non-distro installs :(

---

### Post by Lunde on 2005-07-30
[QUOTE=kLy]crap. there isn't a "make uninstall" ! arg!

Now there's a zillion files lying all over my system that I don't know where to find to get rid of :( This is why I hate non-distro installs :([/QUOTE]
 I posted a tread on the Qemu forum a coupple of weeks ago about that, no replies yet. I will check a bit more into that when I have time.

Is this because you want to remove it completly or because you want to upgrade?

---

### Post by kLy on 2005-07-30
no I upgraded now and hit the "make install". it just overwrote everything, which is ok. And now it works :) Thanks

But say I want to get rid of it... that'll get ugly. Most of the stuff's in /usr/local/bin or /usr/local/share, but then there's kernel modules and who know's what else floating around your system. Darn.

---

### Post by geearf on 2005-07-30
Hello,

if there is a new version out there, then no need to add nothing to the how to :)

---

### Post by Lunde on 2005-07-30
[QUOTE=geearf]Hello,

if there is a new version out there, then no need to add nothing to the how to :)[/QUOTE]
 Is there anything I need to change for the new version? Can I just update the version number?

---

### Post by geearf on 2005-07-30
Well it seems the bug was fixed (I'll be able to tell you that on Monday, i don't know why but my box at work does not answer to ssh right now).

But I guess just changing number is the right thing to do yes.

---

### Post by tombeharrell on 2005-07-30
An excellent how-to, many thanks. I have now got Qemu installed and into it I have installed Win XP Pro. It all seems to work fine, however the XP box's clock runs way too fast affecting things that are animated etc. Has anybody else experienced this?

When the machine is idling and drops to 600MHz a minute in the XP window takes about 19 seconds. With some load so the host runs at 1.5GHz, the minute takes about 10 seconds. Is there anyway of having it sync to the local clock properly? 

My machine is a Centrino-based Inspiron 6000.

Thanks
Tom.

---

### Post by Lunde on 2005-07-31
Hopefully the programs run that fast too :-) 

Does it help by setting the: **-localtime** in your startup command?

---

### Post by Lunde on 2005-07-31
Free Operating Systems ZOO is back up agian, Download free images for your Qemu emulator.

[http://free.oszoo.org/download.html](http://free.oszoo.org/download.html)

---

### Post by kLy on 2005-07-31
Instead of the hacky mods to bootmisc, might I suggest loading the module with:
modprobe kqemu major=0

This creates the /dev/kqemu device automatically. Then add "kqemu:root:root:0666" to the udev permissions in /etc/udev/permissions.d/

This is from the docs. I did this myself tho I haven't given it a reboot to see if that'll do it yet so give it a try.

---

### Post by Lunde on 2005-07-31
[QUOTE=kLy]Instead of the hacky mods to bootmisc, might I suggest loading the module with:
modprobe kqemu major=0

This creates the /dev/kqemu device automatically. Then add "kqemu:root:root:0666" to the udev permissions in /etc/udev/permissions.d/

This is from the docs. I did this myself tho I haven't given it a reboot to see if that'll do it yet so give it a try.[/QUOTE]
 Intresting kLy
Can you tell me how this works and if there are any benefits after the reboot? I would try myself, but I don't have Qemu installed right now. 

If this results in a performance boost or fix any problems, I would like to add this suggestion to the Howto.

---

### Post by kLy on 2005-07-31
not a performance boost. it just adds /dev/kqemu automatically without having to resort to the bootmisc hack, though I'm not too familiar with autoloading modules since all the ones I autoload don't need parameters: ie. can you specify module load parameters in /etc/modules?

eg. add the line "kqemu major=0" to it? If you can then this would be all you need I guess.

I'll test it myself as soon as I reboot.

---

### Post by Lunde on 2005-07-31
[QUOTE=kLy]not a performance boost. it just adds /dev/kqemu automatically without having to resort to the bootmisc hack, though I'm not too familiar with autoloading modules since all the ones I autoload don't need parameters: ie. can you specify module load parameters in /etc/modules?

eg. add the line "kqemu major=0" to it? If you can then this would be all you need I guess.

I'll test it myself as soon as I reboot.[/QUOTE]
 I guess this should'nt be a problem in /etc/init.d/bootmisc.sh at least..
/sbin/modprobe kqemu major=0

---

### Post by tombeharrell on 2005-07-31
[QUOTE=Lunde]Hopefully the programs run that fast too :-) 

Does it help by setting the: **-localtime** in your startup command?[/QUOTE]

Doesn't help unfortunately, though I think the time is synced when it starts to boot up. By the time the desktop loads it's already 10 minutes fast :roll: 

On another note I tried installing my work VPN (Sonicwall) but it doesn't see the network adapter. Although in Device Manager the card is listed (Realtek RTL8029) and it shows up as Ethernet adapter Local Area Connection with ipconfig /all, it doesn't show up in Control Panel/Network Connections. Has anyone found a way of having it show up here, as that might allow my VPN to see it properly?

Thanks, Tom.

---

### Post by Lunde on 2005-07-31
[QUOTE=tombeharrell]Doesn't help unfortunately, though I think the time is synced when it starts to boot up. By the time the desktop loads it's already 10 minutes fast :roll: 

On another note I tried installing my work VPN (Sonicwall) but it doesn't see the network adapter. Although in Device Manager the card is listed (Realtek RTL8029) and it shows up as Ethernet adapter Local Area Connection with ipconfig /all, it doesn't show up in Control Panel/Network Connections. Has anyone found a way of having it show up here, as that might allow my VPN to see it properly?

Thanks, Tom.[/QUOTE]
 Qemu is not comunicating directly with your network card, it's bridged if I remember correctly. The only thing you have to do to connect with the net is to use the **-user-net** then set the settings in Linux.
I know VMware let you communicate directly with the adapter, but I don't know if it's possible with Qemu.

---

### Post by geearf on 2005-08-01
Well I've just tried the new Kqemu, and it does not need any patch now, that's a good thing.

But I still cannot use checkinstall instead of make install, and that is a bad thing :(

(oh and I know why i could'nt access my computer Saturday, it was coz I forgot to take out the Ubuntu CD before rebooting the comp and going home :) )

---

### Post by geearf on 2005-08-01
It seems the network is not doing so well.

I am installing XP right now, and it seems to have trouble getting my network (it's been looking for it for about  10  minutes). But it seems to go further right now. The big thing is the network here is a bit complicated (you need to register the ip and the mac adress, you need to use the proxy ...).

Also to get numkeys in XP work, I have to unlock them in Ubuntu, a bit funny :)

I'll update this post as soon as I have something more to add to it :)

---

### Post by Lunde on 2005-08-01
[QUOTE=geearf]It seems the network is not doing so well.

I am installing XP right now, and it seems to have trouble getting my network (it's been looking for it for about  10  minutes). But it seems to go further right now. The big thing is the network here is a bit complicated (you need to register the ip and the mac adress, you need to use the proxy ...).

Also to get numkeys in XP work, I have to unlock them in Ubuntu, a bit funny :)

I'll update this post as soon as I have something more to add to it :)[/QUOTE]
 Is'nt it a possibuility to bridge the network adapter

---

### Post by Lunde on 2005-08-01
And for the numlock
[http://www.ubuntuguide.org/#numlockx](http://www.ubuntuguide.org/#numlockx)

---

### Post by geearf on 2005-08-01
Hello,

the installation is still not over, it says still one minute, but it's already been more so I guess not.

Also for the NIC, well it is still not installed so I cannot do much, and for the numlock, it's on within Ubuntu at start, but not within Windows, I think it just thinks that when it start Windows it should be off, then whatever it is under ubunto, when I start Windows => off.

But still, I am a bit frightened by the speed :(

edit : I've finally recompiled qemu and reinstalled Windows, it works fine, although it's a bit slow :(
Boot time is about 1 minute, which is great, but using it feel slow :(

edit again : I've got the network alrgith, but i can't figure how to use samba within it,if anyone has any idea on this I'll be glad :)

---

### Post by kLy on 2005-08-01
[QUOTE=Lunde]Qemu is not comunicating directly with your network card, it's bridged if I remember correctly. The only thing you have to do to connect with the net is to use the **-user-net** then set the settings in Linux.
I know VMware let you communicate directly with the adapter, but I don't know if it's possible with Qemu.[/QUOTE]

ok, this is as far as I understand it:

Two options:
1. Using -user-net:
This does not do ANY sort of true networking with anything outside the virtual machine. Hence it is completely user mode: user runnable and no need for root. It does not do any communication with any ports on your actual machine, everything is completely faked in user space:

qemu makes a fake dhcp server at 10.0.2.2 that assigns the client the IP of 10.0.2.1 or something.

You can use two extra options here:
-smb : runs a FAKE samba server in userspace (does not open any samba ports on your actual machine).

This server can be accessed from the client at 10.0.2.4. Check the man pages for details. I never got this working but then I never got any sort of windoze networking working in all my years of admin. It always breaks randomly or slows for no reason. It's crap slow on look up. It plain sucks! And did I mention it sucks?

-tftp : this runs a FAKE tftp server. you can get a free tftp client for windoze (98 that is since 2000 and XP come with it) here:
[http://www.tftp-server.com/tftp-download.html](http://www.tftp-server.com/tftp-download.html)

This could work but it was such a MISSION since there's no directory listings or anything in tftp. Tried it, it sucked and I don't recommend it.

By the way to temporarily get some files onto your client, the easiest way I found (after trying to mount and unmount virtual floppies and other annoyances) is simply just to dump stuff in "folder", then mkisofs -o bla.iso folder. then use that as the CD image. This can be useful for dumping small data, such as the tftp client onto the client machine.

2. OK, finally we arrive at option 2, the default option, the one I'm using now and the one I recommend: tun/tap

This does true network bridging and requires some root priviledges. This option is enabled as long as you don't do a -user-net.

What it does is create (using /dev/net/tun) firstly a virtual network card on your host machine for the virtual network between host and client. This is generally tun0 (you can see it with ifconfig). The default ip is something like 172.20.0.1, though you can change with ifconfig.

Then with the virtual network card on the client, it can talk on *this* network to your host. You can then ping 172.20.0.1 from client and it *actually* goes through to the REAL host machine. So, any ports you have open on your real host machine you can access from the internal network. I have an ftp server up on my host and with this I can access it from the client simply with "ftp 172.20.0.1". If you like samba and windoze networkin (may your soul be saved), just run a samba server on the host and connect to it from the client. etc. You get the idea. You can even let it access your cups server on 631 and print from the virtual machine :)

Now this is a LOT more versatile since you can run any server on the host and connect to it from the client.

It also allows for a REAL network bridge, something like this:

client (172.20.0.2) <--- internal net ---> (172.20.0.1) host / qemu / firewall (142.5.21.41 or whatever your real IP is)  <--- external net ---> Internet

This would require some esoteric firewalling / packet filtering, or what not (basically sets up a router I think), which I'm too lazy to investigate right now. But googling around should get you a decent guide. VMWare installs this by default so its easy peasy. QEmu does not. but you can get the functionality with a bit of work and have more control (and understanding) of it than you ever possibly could with vmware.

One caveat to this is that you need permissions on /dev/tun. What I did was mod the udev permissions so that anyone in the "admin" group can write to it. This might / might not be what you want. If it is, add:

net/tun:root:admin:660

to your udev permissions.

Phew! Hope this helps :)

---

### Post by Lunde on 2005-08-02
Nice. But what do you meen by:1. > Using -user-net:
This does not do ANY sort of true networking with anything outside the virtual machine. Hence it is completely user mode: user runnable and no need for root. It does not do any communication with any ports on your actual machine, everything is completely faked in user space:
This on a normal setup with a network card connection, lets you connect with the actual network. Worked for me on the first try.

---

### Post by geearf on 2005-08-02
Hello,

it's me again, back from the fight with qemu :)

Then here what's good or not for me : 

1- instead of samba, I use the 'connect a network drive option' as our drivers are in NFS under Ubuntu, that is not that bad I guess ..

2- AMD64 can't use ./configure, I had to use ./configure --target-list=x86_64-softmmu, and kqemu just crash qemu :(

3- I can't seem to understand how to make a simple copy / paste between Ubuntu and Windows (in fact I would need the ability to copy images too, just like in Virtual PC).

4- I can't put a CD in the drive to read it under Windows, if Windows was already started through qemu before.

In a few hours I may be able to tell you how fast it is on the amd64 comp, but for the moment still installing (and no more than 2Gb could be allocated too).

Thanks,

---

### Post by Lunde on 2005-08-02
There's no stabile version of KQemu on AMD64 yet I think, but there's supposed to be an alpha out there. 

..the performance will drop a bit without KQemu

As for the copy / paste, I don't remember if there is a fix for that. I'm on VMware and find it a better option for my type of work.

The CD problem we did a round on that a coupple of pages back, I think the solution is in the  terminal window (Monitor window) that started Qemu. where you can eject and insert disks and cd's.

I don't have Qemu operative anymore, but I'll try to help you as much as I can

---

### Post by geearf on 2005-08-02
Thanks for your help, I appreciate.

Just to explain it a bit more, my only goal here is to be able to use Office perfectly, people some folks here would like do their work under linux, do their report under Office, but without the need to swith computer or else :)

And the problem with VMWARE is that it costs a lot, and it's one license by proc I think, and some comp here have up to 4 proc, so it might get a bit expensive just for a little Word / Powerpoint.

---

### Post by rcerreto on 2005-08-02
[QUOTE=geearf]Hello,

...

4- I can't put a CD in the drive to read it under Windows, if Windows was already started through qemu before.

...

[/QUOTE]

1) Insert the CD/DVD 
2) type "Ctrl-Alt-2"  to open qemu console
3) type "change cdrom /dev/cdrom" or whatever your CD/DVD drive is
     (yes, "change" even if there was no CD to change)
4) "Ctrl-Alt-1" to get back into the guest windows
5) Your CD/DVD is now accessible

It works for me, hope it will for you too

---

### Post by geearf on 2005-08-02
Thanks for this tip :)

---

### Post by Lunde on 2005-08-02
[QUOTE=geearf]Thanks for your help, I appreciate.

Just to explain it a bit more, my only goal here is to be able to use Office perfectly, people some folks here would like do their work under linux, do their report under Office, but without the need to swith computer or else :)

And the problem with VMWARE is that it costs a lot, and it's one license by proc I think, and some comp here have up to 4 proc, so it might get a bit expensive just for a little Word / Powerpoint.[/QUOTE]
 Have you tried Wine or Crossover office

---

### Post by Lunde on 2005-08-02
[QUOTE=rcerreto]1) Insert the CD/DVD 
2) type "Ctrl-Alt-2"  to open qemu console
3) type "change cdrom /dev/cdrom" or whatever your CD/DVD drive is
     (yes, "change" even if there was no CD to change)
4) "Ctrl-Alt-1" to get back into the guest windows
5) Your CD/DVD is now accessible

It works for me, hope it will for you too[/QUOTE]
 Thanks I'll put this in the end of the howto

---

### Post by geearf on 2005-08-02
[QUOTE=Lunde]Have you tried Wine or Crossover office[/QUOTE]
Yes of course, and none of them did the job (and I tried a lot of versions of wine, and both the demo and the src of CrossOver)..

It seems they work with office XP but I only have 2003 licences here.

---

### Post by rcerreto on 2005-08-02
Thanks kLy, quite useful!!
Using tun/tap I can easily access the host samba and ftp servers.
Most important thing I can print now!

If you want to give the guest full access to the intranet/internet you just need to issue two commands in the host:

echo 1 > /proc/sys/net/ipv4/ip-forward   # to allow packet forwarding
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE # to enable NAT, change the net device accordingly

your choice where to put them but take into account the security issues. I placed them in a script together with some other iptables commands.

BTW, tun seems to disable dhcp services to the guest.
I had to assign addresses by hand: guest = 172.20.0.2, gateway = 172.20.0.1, DNS = my ISP dns (see /etc/resolv.conf)

**Thanks a lot to all people posting in this thread!!!!** 

Qemu is great, long live qemu and to the people which are working on it

---

### Post by geearf on 2005-08-02
Yes you cannot use DHCP within the guest OS (well at least with windows) :)

---

### Post by kLy on 2005-08-02
Yeah, if you run with -use-net, it sets up a fake virtual dhcp server that sets the client address to 10.0.something

You could I guess set up a REAL dhcp server on the host to do the job, but that's overkill. I just assigned the client IP manually. Make sure it's in the same subnet as the host IP tho!

> 
This on a normal setup with a network card connection, lets you connect with the actual network. Worked for me on the first try.


OK, let me correct myself :) This was very early in the morning when I tried it. lol. It seems that you CAN actually connect to the rest of the net using -user-net. Sorry!

It's just that it does a fake internal network (and with fake samba if you want it). You just can't do certain things like ping since it requires root priviledges. See here:
[http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC21](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC21)

---

### Post by kLy on 2005-08-02
hey. another tip.

Hope this wasn't mentioned before. The qcow image format is great! It lets you only use up as much space as needed for the actual files, not the empty space and it's fully windoze 98 compatible:

qemu-img create -f qcow bla.img

Now these things can grow and even if you delete data, it still stays that big. Why because data isn't actually deleted! It's only marked as deleted and so the sectors are still filled with 1's and 0's. Now what you need to do is a disk space zero. Now most of the packages out there do space WIPING. I couldn't find any for space zeroing. What they want to do is securely delete all their kiddy porn using DOD standards compliant writing of various patterns into "empty" space. This wont help us since what we want is make plain old 0's to reclaim space, not porn-destroying 1's and 0's. Fortunately, certain packages allow you to define your own pattern, ie: 000000000000000

One such (Free) one I found was: [http://www.heidi.ie/eraser/default.php](http://www.heidi.ie/eraser/default.php)

Now this can fill all empty space with 0's, and since we're writing to all this space, it'll make the image as big as the parition can be. ie. HUGE! It'll take up all the space.

BUT! Now that they're just plain old zero's, you can do a convert and qemu will nullify all the empty space:

qemu-img -convert -f qcow old.img -O qcow new.img

This reduced my 300MB image file to 100MB! A great space saver on the host! :)

Now next time, instead of deleting a file, WIPE it with zeroes. This will ensure that if you convert again, you reclaim the space. And you don't need to zero ALL free space ending up with a HUGE image file as an intermediate process.

Hope this helps! :)

---

### Post by kLy on 2005-08-02
To go with the above, you can also use the -c flag to do disk compression for an even smaller image. I don't think it would be a great performance hit since compression is read only, so you don't recompress data in realtime. ie. new sectors get written in uncompressed format, so you only need cycles to decompress sectors when running the emulator.

Happy Qemulating! :)

---

### Post by geearf on 2005-08-03
Hello,

I was told that this could help for the copy / past thing : 

[http://www.idata.sk/~robo/mpcb/](http://www.idata.sk/~robo/mpcb/)

It's a deamon for copy pasting over an tcp/ip network.

---

### Post by Talldave2002 on 2005-08-03
This has been extremely useful, I have managed to emulate both Win98 and WinXP in Qemu, Thanks so much for the info.

I have a slight problem though. I cannot figure out how to have a shared Folder Between my Win98 emulation and my Ununtu/Kubuntu Linux.

I only intend to use the Win98 for a few small progs that i cant find Linux alternatives for.

Can anyone help me?

---

### Post by kLy on 2005-08-04
[QUOTE=Talldave2002]This has been extremely useful, I have managed to emulate both Win98 and WinXP in Qemu, Thanks so much for the info.

I have a slight problem though. I cannot figure out how to have a shared Folder Between my Win98 emulation and my Ununtu/Kubuntu Linux.

I only intend to use the Win98 for a few small progs that i cant find Linux alternatives for.

Can anyone help me?[/QUOTE]
 check the posts about networking (I think on pg 26). You can either use -user-net -smb for fake samba or run a samba server on your host machine.

---

### Post by gangalee on 2005-08-04
How do I get it recognize the size of the hd.img I created?
When I run the Win98 setup, it scans the (virtual) system registry, then bombs with "Setup requires 734xxx bytes available on your C: drive" I copied and pasted the command straight from your instructions.

Also, how are the USB devices in qemu in general, and how's the Sony NetMD support in particular?

---

### Post by Trojan1313 on 2005-08-06
> Step 4. STARTING THE GUEST OS

Well.. we're sort of already there, again it's mostly just to change the -boot flag

$ qemu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda hd.img -user-net -pci -m 256 -k en


Description of other flags used in this startup:

-k en
Keybord layout.. works with some languages

-user-net
Lets you connect to the net

-pci -m 256
Amount of memory provided the guest OS

Note: I will not go into details about networking here.. at least not yet. Internet should probably work from the guest without any modifications. To set up shared folders between the guest and the host, a tip is. Install samba, then share the folders with SMB and add the flag -smb /shared/folder to your startup command.
I'm stuck, how do I install the guest OS from my WinXP Boot-CD to the hd-img?
Boot as in install-boot, not live. :)

---

### Post by Lunde on 2005-08-06
[QUOTE=Trojan1313]I'm stuck, how do I install the guest OS from my WinXP Boot-CD to the hd-img?
Boot as in install-boot, not live. :)[/QUOTE]
 $ qemu -boot d -cdrom /dev/cdrom -hda hd.img

Then install as a normal XP installation, let me know if you have any problems reading the CD drive

---

### Post by gangalee on 2005-08-06
I can read the CD fine, it just complains about installing to my hd.img
[FONT=Courier New]
ira@gator:~/Qemu$ ls -l
total 12
-rwxrwxrwx  1 ira ira 3145728000 2005-08-04 16:11 hd.img[/FONT]

Scanning system registry...
Windows Setup requires 7340032 bytes available on your C: drive

?????????????????????????/

---

### Post by Lunde on 2005-08-06
[QUOTE=gangalee]I can read the CD fine, it just complains about installing to my hd.img
[FONT=Courier New]
ira@gator:~/Qemu$ ls -l
total 12
-rwxrwxrwx  1 ira ira 3145728000 2005-08-04 16:11 hd.img[/FONT]

Scanning system registry...
Windows Setup requires 7340032 bytes available on your C: drive

?????????????????????????/[/QUOTE]
 First make sure your hd.img is created with the right size.
I had a similar problem with a win98 installation, I formated the hd.img first. Try and see if it helps. No point giving RWX to everybody, it'll do no difference.

---

### Post by Trojan1313 on 2005-08-06
[QUOTE=Lunde]$ qemu -boot d -cdrom /dev/cdrom -hda hd.img

Then install as a normal XP installation, let me know if you have any problems reading the CD drive[/QUOTE]
fourchan@Kaminix:~/Qemu$ qemu -boot d -cdrom /dev/cdrom -hda hd.img
warning: could not open /dev/net/tun: no virtual network emulation
qemu: could not open hard disk image '/dev/cdrom'

I have two optical devices, should I try the other one? (I would've done this directly if it wasn't for another question, I'm not that lazy)
What does the no virtual network emulation mean?

EDIT:
If this will works like I think it will, then I will love you forever. :)

---

### Post by geearf on 2005-08-06
you may need to try the other /dev for your cdrom yes :)

and about the warning, it says that the network between both os won't work if I'm not guessing wrong.

---

### Post by Trojan1313 on 2005-08-06
[QUOTE=geearf]you may need to try the other /dev for your cdrom yes :)

and about the warning, it says that the network between both os won't work if I'm not guessing wrong.[/QUOTE]
Meaning I won't be able to do something that's impossible anyway? (there's no network services that use network connection between two simultaniously runnings OSs, is there?)
Puh, lucky they warned me. :p

Going to try the other drive after I get some sleep. :)

---

### Post by geearf on 2005-08-06
Wrong there are, else you cannot get the net or anything interesting ;)

---

### Post by Lunde on 2005-08-07
[QUOTE=Trojan1313]fourchan@Kaminix:~/Qemu$ qemu -boot d -cdrom /dev/cdrom -hda hd.img
warning: could not open /dev/net/tun: no virtual network emulation
qemu: could not open hard disk image '/dev/cdrom'

I have two optical devices, should I try the other one? (I would've done this directly if it wasn't for another question, I'm not that lazy)
What does the no virtual network emulation mean?
[/QUOTE]

Since you have two optical devices, you may have to look into /dev/cdrom0, /dev/cdrom1 and /dev/hdc

Network between the Guest and Host is just like a normal bridged or shared network device. You have an option for virtuel Samba or you can use Samba to share folders from the host. this subject is mentioned a coupple of times in the previous pages of this tread (2-3 pages back I think).

---

### Post by Trojan1313 on 2005-08-07
[QUOTE=geearf]Wrong there are, else you cannot get the net or anything interesting ;)[/QUOTE]
Oh oh oh... I don't like that. How do I fix this? :p

How will the switch between the OS work? Will it be like I switch betwen Windows and Linux enviroment or will the installed Windows work like a driver for all Windows-programs in Linux?

---

### Post by Lunde on 2005-08-07
[QUOTE=Trojan1313]Oh oh oh... I don't like that. How do I fix this? :p

How will the switch between the OS work? Will it be like I switch betwen Windows and Linux enviroment or will the installed Windows work like a driver for all Windows-programs in Linux?[/QUOTE]
 What's there to not like? Can you describe your problem a bit more spesific

The network is bridged / routed from your network card, just like you would share your connectin between 2 adapters, just that one is virtual

Qemu is a complete emulator that shares / provide virtual hardware, memory and CPU to the windows / guest environment.

---

### Post by Trojan1313 on 2005-08-07
[QUOTE=Lunde]What's there to not like? Can you describe your problem a bit more spesific

The network is bridged / routed from your network card, just like you would share your connectin between 2 adapters, just that one is virtual

Qemu is a complete emulator that shares / provide virtual hardware, memory and CPU to the windows / guest environment.[/QUOTE]
Ah, I thought I wouldn't be able to use networking with Windows-thingies.
Then should I just ignore the error?

---

### Post by Lunde on 2005-08-08
[QUOTE=Trojan1313]Ah, I thought I wouldn't be able to use networking with Windows-thingies.
Then should I just ignore the error?[/QUOTE]
 So, what happens if you use the flag **-user-net** Do you use some kind of special network setup?

---

### Post by djmadkins on 2005-08-09
Anyone having problems getting the cdrom recognized?

I am trying to get winXP instaklled and have downloaded and created the 6 "boot" disk's from M$ so I can install XP. Problem is when I get to the final disk it then asks for the CD to be installed. 

I tried the following command lines (as well as remounting the CD, and converting the CD into an ISO even tho it is not a bootable cd):

qemu -boot c -fda /dev/fd0 -cdrom /dev/cdrom -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

qemu -boot c -fda /dev/fd0 -cdrom /dev/cdrom0 -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

qemu -boot c -fda /dev/fd0 -cdrom /dev/hdc -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

Anyone have any ideas?

Is there a link anywherre to an ISO of a "bootable" winXp CD? I could put in my own serial at the appropriate time.

---

### Post by Trojan1313 on 2005-08-09
[QUOTE=djmadkins]Anyone having problems getting the cdrom recognized?

I am trying to get winXP instaklled and have downloaded and created the 6 "boot" cd's from M$ so I can install XP. Problem is when I get to the final disk it then asks for the CD to be installed. 

I tried the following command lines (as well as remounting the CD, and converting the CD into an ISO even tho it is not a bootable cd):

qemu -boot c -fda /dev/fd0 -cdrom /dev/cdrom -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

qemu -boot c -fda /dev/fd0 -cdrom /dev/cdrom0 -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

qemu -boot c -fda /dev/fd0 -cdrom /dev/hdc -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

Anyone have any ideas?

Is there a link anywherre to an ISO of a "bootable" winXp CD? I could put in my own serial at the appropriate time.[/QUOTE]
...six boot CDs? :s

Sorry Lunde, forgot to write you back. I got it working now. :D
Thanks for your help. :)


btw, is there any way to send files between the virtual disk and the real disk? And is there a way to resize it?

---

### Post by Lunde on 2005-08-09
[QUOTE=djmadkins]Anyone having problems getting the cdrom recognized?

I am trying to get winXP instaklled and have downloaded and created the 6 "boot" disk's from M$ so I can install XP. Problem is when I get to the final disk it then asks for the CD to be installed. 

I tried the following command lines (as well as remounting the CD, and converting the CD into an ISO even tho it is not a bootable cd):

qemu -boot c -fda /dev/fd0 -cdrom /dev/cdrom -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

qemu -boot c -fda /dev/fd0 -cdrom /dev/cdrom0 -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

qemu -boot c -fda /dev/fd0 -cdrom /dev/hdc -hda /home/adkinsj/Qemu/hd.img -user-net -pci -m 512 -k en-us

Anyone have any ideas?

Is there a link anywherre to an ISO of a "bootable" winXp CD? I could put in my own serial at the appropriate time.[/QUOTE]
 Some other people have reported strange problems if you have more then 1 CD device. 
For the .iso you can use the following command (If this is not what you have already tried):
[B]
mkisofs -RJ -o file.iso /cdrom/
[/B]
Then link up the cdrom as **-cdrom file.iso**
Do you have more then 1 CD player (RW / R)?

---

### Post by Lunde on 2005-08-09
[QUOTE=Trojan1313]...six boot CDs? :s

Sorry Lunde, forgot to write you back. I got it working now. :D
Thanks for your help. :)


btw, is there any way to send files between the virtual disk and the real disk? And is there a way to resize it?[/QUOTE]
 Resize:
[http://www.carlsonhome.net/computer_help_log.php](http://www.carlsonhome.net/computer_help_log.php)

All the commands regarding fdisk is not written in this howto, but it shows the general procedure. You don't have to use Knoppix, any distro / livecd with ntfs resize and fdisk may do.

As for inserting files into the image, I've read somewhere that its possible, but can't remember how. I don't see the point, it's a better solution to set up networking and shared forlders.

---

### Post by Trojan1313 on 2005-08-09
[QUOTE=Lunde]Resize:
[http://www.carlsonhome.net/computer_help_log.php](http://www.carlsonhome.net/computer_help_log.php)

All the commands regarding fdisk is not written in this howto, but it shows the general procedure. You don't have to use Knoppix, any distro / livecd with ntfs resize and fdisk may do.

As for inserting files into the image, I've read somewhere that its possible, but can't remember how. I don't see the point, it's a better solution to set up networking and shared forlders.[/QUOTE]
Oh, right, I forgot I'm in network with my guest. :p

---

### Post by tmasboa on 2005-08-09
mine says it can't find qemu

---

### Post by Lunde on 2005-08-10
[QUOTE=tmasboa]mine says it can't find qemu[/QUOTE]
 How far did you get with the installation?

---

### Post by gangalee on 2005-08-10
[QUOTE=Lunde]First make sure your hd.img is created with the right size.
I had a similar problem with a win98 installation, I formated the hd.img first. Try and see if it helps. No point giving RWX to everybody, it'll do no difference.[/QUOTE]

It does seem to not be the proper size, since I tried formatting the hd.img with fdisk in the dos window and it bombed out after 32% saying no space left in the drive. What's wrong with my size?

---

### Post by Lunde on 2005-08-10
[QUOTE=gangalee]It does seem to not be the proper size, since I tried formatting the hd.img with fdisk in the dos window and it bombed out after 32% saying no space left in the drive. What's wrong with my size?[/QUOTE]
 Do you have enough space left on your drive? 

Try to create the image with dd instead:
**$ dd of=hd.img bs=1024 seek=2000000 count=0**
..will create an image almost 2gig

---

### Post by Trojan1313 on 2005-08-10
I was thinking 'bout something... I have some network problems in Linux wich I didn't have in Windows... will I have those if I emulate Windows like this?

---

### Post by fago on 2005-08-10
[QUOTE=Trojan1313]I was thinking 'bout something... I have some network problems in Linux wich I didn't have in Windows... will I have those if I emulate Windows like this?[/QUOTE]

yes, i think so

i'm currently installing winme, seems to work great.

i just wanted to note that another quick option to install the latest qemu without kqemu is to download the binary  tgz from qemu-site and convert it with alien to a deb.

---

### Post by c4pp4 on 2005-08-10
**so finally i got it!**
my first problem was that i didn't know where paste: kernel_path="[COLOR=Blue]/usr/src/linux-headers-2.6.10-5-386[/COLOR]"
because there are two places within the [COLOR=Blue]configure[/COLOR] file.
then came first error after command [COLOR=Blue]./configure[/COLOR]
[COLOR=Red]ERROR: QEMU requires SDL or Cocoa for graphical output  To build QEMU with graphical output configure with --disable-gfx-check  Note that this will disable all output from the virtual graphics card[/COLOR]
after i used [COLOR=Blue]./configure --disable-gfx-check[/COLOR] it was o.k.
then came next error after command [COLOR=Blue]make[/COLOR], something like:
[COLOR=Red]dyngen: ret or jmp expected at the end of op_divb_AL_T0 ...[/COLOR]
i found out that i didn't install [COLOR=Blue]gcc[/COLOR] (there was installed only gcc-3.3 in the synaptic)
i erased qemu dir and began again
after command [COLOR=Blue]checkinstall[/COLOR] next error
[COLOR=Red]dpkg-deb: subprocess paste killed by signal (Broken pipe)[/COLOR]
i erased qemu dir and began again
instead of [COLOR=Blue]checkinstall[/COLOR] i used [COLOR=Blue]sudo make install[/COLOR] and there was no problem finally
my cpu ran 100% all the time so it was very slow :(
when i fired up qemu command for 256MB of mem it didn't run and wanted me to use:
[COLOR=Blue]sudo umount /dev/shm
sudo mount -t tmpfs -o size=272m none /dev/shm[/COLOR]
so i did it and it works but i don't understand it (:o?)

**sequence of my steps to the end:**
i downloaded from [http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html) 
[COLOR=Blue]qemu-0.7.1.tar.gz[/COLOR] and [COLOR=Blue]kqemu-0.7.1-1.tar.gz[/COLOR] to my /home/user/temp 
fired up terminal
[COLOR=Blue]uname -r[/COLOR]
checked all packages:
[COLOR=Blue]sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install make
sudo apt-get install gcc
sudo apt-get install libsdl1.2-dev
sudo apt-get install zlib1g-dev[/COLOR]
cd temp
[COLOR=Blue]tar zxvf qemu-0.7.1.tar.gz
cd qemu-0.7.1
tar zxvf ../kqemu-0.7.1-1.tar.gz
sudo chmod -R 775 /home/user/temp/qemu-0.7.1[/COLOR]
i found out where synaptic installed files for *linux-headers*
[COLOR=Blue]sudo gedit configure[/COLOR]
i changed path right here:
```
# Linux specific kqemu configuration
if test $kqemu = "yes" -a $linux = "yes" ; then
# find the kernel path
if test -z "$kernel_path" ; then
kernel_version=`uname -r`
kernel_path="/lib/modules/$kernel_version/build"
if test '!' -d "$kernel_path/include" ; then 
    kernel_path="[COLOR=Blue]/usr/src/linux-headers-2.6.10-5-386[/COLOR]"
    if test '!' -d "$kernel_path/include" ; then 
        echo "Could not find kernel includes in /lib/modules or /usr/src/linux - cannot build the kqemu module"
        kqemu="no"
    fi
fi
fi

if test $kqemu = "yes" ; then
```
[COLOR=Blue]./configure
make
sudo make install
sudo modprobe kqemu
sudo gedit /etc/init.d/bootmisc.sh[/COLOR]
cd ..
cd ..
[COLOR=Blue]mkdir Qemu[/COLOR] ##/home/user/Qemu
[COLOR=Blue]cd Qemu
qemu-img create hd.img 5000M
qemu -boot d -cdrom /dev/cdrom -hda hd.img[/COLOR]
[COLOR=Navy]sudo umount /dev/shm
sudo mount -t tmpfs -o size=272m none /dev/shm[/COLOR]
[COLOR=Blue]qemu -boot c -hda /home/user/Qemu/hd.img -user-net -pci -m 256[/COLOR]

that's all and **many thanks to mr. Lunde** for my new experiences with Linux :D
btw: please what about uninstall info from Qemu forum?

---

### Post by Lunde on 2005-08-11
> 
when i fired up qemu command for 256MB of mem it didn't run and wanted me to use:
sudo umount /dev/shm
sudo mount -t tmpfs -o size=272m none /dev/shm
so i did it and it works but i don't understand it (?)

The /dev/shm is the mounted memory for Qemu to use, the command you ran is to increase the amount of memory. I found earlier the place to set the default amout, but can't remember where.  

**Uninstall:**
This is the only answere I got from the Qemu forum. I'll see if I can make an uninstaller shellscript that reads the tar directory and removes the files from the system, but I don't have time for a coupple of weeks, I'm moving and will not be on the net for a while.
> 
I faced the same problem months ago. Finally, I searched my harddisk for all the qemu files.
But I just found a new method: download qemu for linux-i386, and look what is inside the file with a software to uncompress files (like ark in kde). That is the list of all the files created by a compilation of qemu for linux on your harddisk.
There are other files, like /etc/qemu-ifup-sudo, or /dev/kqemu, but it is better not to delete them if you want to reinstall qemu. You would have to spend time creating them again.
You can delete the kqemu module in /lib/modules/kernel_version/misc

If you do this, don't forget to remove the:
```

# Start Qemu with KQemu accelerator
/sbin/modprobe kqemu
mknod /dev/kqemu c 250 0 # Create the KQEMU device
chmod 666 /dev/kqemu # Make it accessible to all users

```
from the **/etc/init.d/bootmisc.sh**

---

### Post by gangalee on 2005-08-11
[QUOTE=Lunde]Do you have enough space left on your drive? 

Try to create the image with dd instead:
**$ dd of=hd.img bs=1024 seek=2000000 count=0**
..will create an image almost 2gig[/QUOTE]
 I'm still having problems getting this to install Windows, now it just freezes. Could I use an existing hd.img? I remember seeing something about OSZoo. Is there a Win98 image I could download and use?

---

### Post by Lunde on 2005-08-11
[QUOTE=gangalee]I'm still having problems getting this to install Windows, now it just freezes. Could I use an existing hd.img? I remember seeing something about OSZoo. Is there a Win98 image I could download and use?[/QUOTE]
 Are you using a XP recovery cd that came with your comuter? That may cause problems, the hardware is completly different when Qemu emulates it.

---

### Post by gangalee on 2005-08-12
[QUOTE=Lunde]Are you using a XP recovery cd that came with your comuter? That may cause problems, the hardware is completly different when Qemu emulates it.[/QUOTE]
 It's a Win98SE install disk.
Here's my disk space:
ira@gator:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              26G   21G  4.1G  84% /
tmpfs                 249M     0  249M   0% /dev/shm
/dev                   26G   21G  4.1G  84% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
/dev/sda1             488M  216M  273M  45% /media/usbdisk
/dev/hdc              626M  626M     0 100% /media/cdrom0

---

### Post by Lunde on 2005-08-12
[QUOTE=gangalee]It's a Win98SE install disk.
Here's my disk space:
ira@gator:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              26G   21G  4.1G  84% /
tmpfs                 249M     0  249M   0% /dev/shm
/dev                   26G   21G  4.1G  84% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
/dev/sda1             488M  216M  273M  45% /media/usbdisk
/dev/hdc              626M  626M     0 100% /media/cdrom0[/QUOTE]
 win98 you need to start without KQemu if you have installed it... I think that's what causing the problem.

**-no-kqemu**
in the startup command

---

### Post by gangalee on 2005-08-12
[QUOTE=Lunde]win98 you need to start without KQemu if you have installed it... I think that's what causing the problem.

**-no-kqemu**
in the startup command[/QUOTE]
 I haven't installed KQemu (as far as I know).

Sorry, I really appreciate you trying to help me out- what's the exact syntax?

ira@gator:~/Qemu$ qemu -boot d -cdrom /dev/cdrom -hda hd.img -no-kqemu
qemu: invalid option -- '-no-kqemu'
ira@gator:~/Qemu$ qemu -boot-no-kqemu d -cdrom /dev/cdrom -hda hd.img
qemu: invalid option -- '-boot-no-kqemu'

---

### Post by Lunde on 2005-08-12
[QUOTE=gangalee]I haven't installed KQemu (as far as I know).

Sorry, I really appreciate you trying to help me out- what's the exact syntax?

ira@gator:~/Qemu$ qemu -boot d -cdrom /dev/cdrom -hda hd.img -no-kqemu
qemu: invalid option -- '-no-kqemu'
ira@gator:~/Qemu$ qemu -boot-no-kqemu d -cdrom /dev/cdrom -hda hd.img
qemu: invalid option -- '-boot-no-kqemu'[/QUOTE]
 Correct should be like this:
qemu -boot d -cdrom /dev/cdrom -hda hd.img -no-kqemu

So you compiled it without kqemu or did you just do atp-get install qemu?

---

### Post by gangalee on 2005-08-12
[QUOTE=Lunde]Correct should be like this:
qemu -boot d -cdrom /dev/cdrom -hda hd.img -no-kqemu

So you compiled it without kqemu or did you just do atp-get install qemu?[/QUOTE]
 I just apt-get install qemu

The syntax you just gave me is the same as the one I tried. Notice the error.
Is it a conspiracy to keep me from escaping booting into Windoze!!???

---

### Post by n1tro on 2005-08-16
Thanks for the great tutorial.  I had to redo the steps several times because I am a complete n00b at Linux but I managed to get XP sp2 installed onto my Asus laptop. :) But here something odd that happened and maybe the more experienced users can answer this one for me quickly.  When I first installed qemu and made the launcher for it, I had the option (-cdrom /dev/cdrom) for the cdrom to be emulated fine.  However, now when I press on my launcher, nothing happens.  But when I take out the option for the cdrom in the command line, qemu boots my XP fine.  What's up with that?  Does it have anything to do with me installing cd/dvd burning apps? Possibly the new apps took over control of the cdrom?  Any help is greatly appreciated.

---

### Post by Ozziej on 2005-08-16
I tried installing kqemu bu i get the following error:

```
Warning: could not find /home/ozzie/documents/download/qemu-0.7.1/kqemu/.kqemu-mod.o.cmd for /home/ozzie/documents/download/qemu-0.7.1/kqemu/kqemu-mod.o
```

i get this while doing make in de qemu dir. I followed every step in the howto, but i cant get past make, cause it keeps on giving this error.

does anyone know what to do about it?
i tried redownloading the files and extracting them but that doesnt help.

btw, both of the files named in the error message are in the specified diretory.

---

### Post by n1tro on 2005-08-17
Solved my own problem.  Apparently you have to put "sudo" in front of the command line for qemu for it to run with the cdrom option. otherwise it would just run the hard drive image.  :-? 


[QUOTE=n1tro]Thanks for the great tutorial.  I had to redo the steps several times because I am a complete n00b at Linux but I managed to get XP sp2 installed onto my Asus laptop. :) But here something odd that happened and maybe the more experienced users can answer this one for me quickly.  When I first installed qemu and made the launcher for it, I had the option (-cdrom /dev/cdrom) for the cdrom to be emulated fine.  However, now when I press on my launcher, nothing happens.  But when I take out the option for the cdrom in the command line, qemu boots my XP fine.  What's up with that?  Does it have anything to do with me installing cd/dvd burning apps? Possibly the new apps took over control of the cdrom?  Any help is greatly appreciated.[/QUOTE]

---

### Post by gangalee on 2005-08-17
If anyone gets a clean Win98SE image built, could you send it to me before you start customizing it?

Thanks,

---

### Post by rherman on 2005-08-17
I'm a complete noobie at this, but I am going to give it a try. I own a license for Windows 2000 and Windows 2000 Server. I only need to run  a few simple apps in emulation. How can I avoid the lengthy install and load a "skinnier" version if one exsists? Or do I just do a complete install and how do i trim off the fat? Thanks.

Rob

---

### Post by rherman on 2005-08-17
NEWBIE WARNING****

The install works as written step-by-step; HOWEVER, make your hd image size larger than 3500M for Win 2K Server. I just finished rebooting the hd.img after installing, and my 'c:' drive shows 132kb free! Is there a way to change the hd.img size available at this point? Please say yes.

Rob

---

### Post by edongski on 2005-08-17
Pardon me for my inability to comprehend.  I have this problem:

gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/root/qemu-0.7. 1/target-i386 -I/root/qemu-0.7.1 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFI LE_SOURCE -I/root/qemu-0.7.1/fpu -I/root/qemu-0.7.1/slirp -c -o translate-op.o / root/qemu-0.7.1/translate-op.c
In file included from /root/qemu-0.7.1/translate-op.c:36:
op.h: In function `dyngen_code':
op.h:12842: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[1]: *** [translate-op.o] Error 1
make[1]: Leaving directory `/root/qemu-0.7.1/x86_64-softmmu'
make: *** [all] Error 1
****  Installation failed. Aborting package creation.

Cleaning up...OK

I just followed the instructions but I get this. 

Thank you for your help.

EDIT:

I skipped the QEMU WITH KQEMU ACCELERATOR procedure.
I got the WinXP to install but when I enter: qemu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda hd.img -user-net -pci -m 256 it shows the attached image.

What did I do wrong? Please help.

---

### Post by ShagzModo on 2005-08-18
Thanks for the info!
I will try implementing this tonight, see if i can reverse engineer Active Directory / Exchange to get rid of microsoft licensing fees.... should all be done tomorrowmorning... ;-)

---

### Post by s_p_a_r_k_y on 2005-08-18
hi...I'm having a problem as my tun0 is 172.20.0.1 so I setup win98 to use 172.20.0.2

I can ping from windows the linux machine and the reverse as well. However I'm not sure how to setup the routing.... I cannot ping from the windows virtual machine my Router which is 192.168.0.1. I tried

```

iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE

```

to nat masquerade traffic from the tun0 device. Can someone help or should I just put tun0 into the 192.168.0.0/24 range and the win98 machine as well?

EDIT
I CAN ping the 192.168.0.8 address which is eth0 on the host computer. However it doesn't seem to be routing and letting the packets out.
```

sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

```

eth1      Link encap:Ethernet  HWaddr 00:90:4B:68:F2:A4
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe68:f2a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29359588 (27.9 MiB)  TX bytes:48261534 (46.0 MiB)
          Interrupt:19 Base address:0x8000

tun0      Link encap:Ethernet  HWaddr 00:FF:19:F1:D2:24
          inet addr:172.20.0.1  Bcast:172.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2ff:19ff:fef1:d224/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11970 (11.6 KiB)  TX bytes:8692 (8.4 KiB)

```

---

### Post by s_p_a_r_k_y on 2005-08-20
no one?

---

### Post by mulperi on 2005-08-21
Thanks Lunde for this howto. 

I tried the version (0.6.1) in Synaptic but win98 crashed with BSOD. It might be because I'm running K7 kernel version. 

However with your  compile instructions I was able to make a working copy. I also did not even know something as good as checkinstall existed  \\:D/ 

//mulperi

---

### Post by Lunde on 2005-08-26
Hi all!
I just moved to Sweden and have not been able access the internet. I'll be back online and can answere your questions in about a week from now.

---

### Post by mata_svada on 2005-08-27
[QUOTE=kLy]
What it does is create (using /dev/net/tun) firstly a virtual network card on your host machine for the virtual network between host and client. This is generally tun0 (you can see it with ifconfig). The default ip is something like 172.20.0.1, though you can change with ifconfig.[/QUOTE]
This just doesn't work on my PC: When I boot Windows with qemu and then go to ifconfig, it only shows my normal eth0.
I modified my udev and it didn't help.

Any idea what I'm doing wrong??

---

### Post by Trojan1313 on 2005-08-27
[QUOTE=Lunde]Hi all!
I just moved to Sweden and have not been able access the internet. I'll be back online and can answere your questions in about a week from now.[/QUOTE]
Welcome. ;)

---

### Post by domstyledesign on 2005-08-27
I have a dual boot system w/ one hd.  ubuntu on /dev/sda2 and windows on /dev/sda1.

if i use
```
qemu -hda /dev/sda1 -snapshot -user-net
```
qemu just hangs @ "Booting from hard disk..."

however, if i use
```
qemu -hda /dev/sda -snapshot -user-net
```
then GRUB loads and i can select windows.  however, after doing so, this is all i get:
```
  Booting 'Windows XP Pro SP2'

root (hd0,0)
 Filesystem type is fat, partition type 0xc
savedefault
makeactive
chainloader +1


Disk error
Press any key to restart
Boot from Hard Disk 0 failed
FATAL: Could not read the boot disk
```

is there any way i can make this work w/o making an image of my windows partition?

---

### Post by fig_jam_uk on 2005-08-27
[QUOTE=scrillamaan]Well, I just got sound working in XP. 

Qemu emulates a sound blaster 16 sound card and I manually installed this new device through the windows add hardware wizard. I followed [this guide](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=audio) to get multiple sounds working. Then I ran Qemu with this option ```
-enable-audio
``` Hope it helps.

[EDIT]
Qemu seems to continuously use the ALSA driver because while it is running, I cannot play any sounds in hoary due to the ALSA driver being in use.

...hopefully there is a solution
[/EDIT][/QUOTE]

thankyou very much now all i need to figure out is to get rid of the 169 IP im plagued by  ](*,)   ](*,)

---

### Post by flange on 2005-08-28
[QUOTE=kLy]Hi

When trying to ./configure I get this:
```

kbuild type       2.6
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.

```

I did install libsdl1.2-dev :( What's wrong?[/QUOTE]

Did anyone else encounter this problem and solve it?  I'm stuck on this now, and so far haven't found a fix.

---

### Post by fig_jam_uk on 2005-08-28
Hi Lunde thanx for a very helpfull how to...  :razz: 

I have tried win 98SE, win ME and XP all install and run fine :) the only problem is they wont go on the net, reading what other people have posted on this thread and others it looks like i need some sort of VPN/Tunneling connection, i have installed a few packages and i managed to get tun working with a 172IP after it asked for my password :) yay (much joy and rejoycing) but upon a second check with ifconfig i see that it has dissapeard again after about only 10 seconds (boo hoo  :-x  ) if anybody can give me any pointers it would be greatly appreciated....  ](*,)   ](*,)   ](*,)

---

### Post by mata_svada on 2005-08-30
> Hi Lunde thanx for a very helpfull how to...

I have tried win 98SE, win ME and XP all install and run fine the only problem is they wont go on the net, reading what other people have posted on this thread and others it looks like i need some sort of VPN/Tunneling connection, i have installed a few packages and i managed to get tun working with a 172IP after it asked for my password yay (much joy and rejoycing) but upon a second check with ifconfig i see that it has dissapeard again after about only 10 seconds (boo hoo ) if anybody can give me any pointers it would be greatly appreciated....  

ehhmm..., fig_jam_uk, did you get a connection between Ubuntu and the guest OS working. If yes, could you tell me what I did wrong (have a look at my post above)

thx a lot...

---

### Post by meastp on 2005-08-30
Hi!

This looks amazing! Now it will be easier, not having to reboot when transferring stuff to my minidisc (hopefully, anyway)!

However, there is one thing I have always wanted, and that is to play good, old Command & Conquer (Tiberian Dawn) and Red Alert (1) on LAN (Need win95 or 98 for that). Do you think that would be possible?

---
meastp

---

### Post by CHUCKYCHUCK on 2005-08-31
Hi ! ( my 1st post on the english-speaking ubuntu forum :)  )   I plan to use Qemu to install win xp, but i have a few question :
_ how much ram/hard drive space would you advise me to use ?? ( i think i'll juste use quicktime pro, flash mx, virtual dub, dvd shrink | not at the same time :D  ), and i have a P4 3Ghz, 512 Ram

_ how can we share files between the fake windows and ubuntu ?? : 
           _can we access the ubuntu partitions directly  ? or do we have to 1st write the files in the hd image and then copy them under ubuntu  ??

_ the emulated windows can access the cd-driver and burn cds/dvds can it ??

Thanks

---

### Post by domstyledesign on 2005-08-31
[QUOTE=CHUCKYCHUCK]how much ram/hard drive space would you advise me to use ?? ( i think i'll juste use quicktime pro, flash mx, virtual dub, dvd shrink | not at the same time :D  ), and i have a P4 3Ghz, 512 Ram
_ how can we share files between the fake windows and ubuntu ?? : 
_can we access the ubuntu partitions directly  ? or do we have to 1st write the files in the hd image and then copy them under ubuntu  ??

_ the emulated windows can access the cd-driver and burn cds/dvds can it ??[/QUOTE]

i'd recommend 256mb ram and 2gb hd space.  You can use smb to share files (check the man page).  The man page says that qemu will give windows CD-ROM support, but not CDR/RW or DVD support.

---

### Post by gangalee on 2005-08-31
[QUOTE=meastp]Hi!

This looks amazing! Now it will be easier, not having to reboot when transferring stuff to my minidisc (hopefully, anyway)!
---
meastp[/QUOTE]

This is pretty much all I use Windoze for, my Mini-disc. I haven't been able to install a hd.img yet however. Could you send me your Windows.img?

---

### Post by CHUCKYCHUCK on 2005-08-31
thx domstyledesign, well i think i'll use wine for dvd shrink ...

---

### Post by domstyledesign on 2005-08-31
no prob chuck.  now if i could only get help with my problem...

[QUOTE=domstyledesign]I have a dual boot system w/ one hd.  ubuntu on /dev/sda2 and windows on /dev/sda1.

if i use
```
qemu -hda /dev/sda1 -snapshot -user-net
```
qemu just hangs @ "Booting from hard disk..."

however, if i use
```
qemu -hda /dev/sda -snapshot -user-net
```
then GRUB loads and i can select windows.  however, after doing so, this is all i get:
```
  Booting 'Windows XP Pro SP2'

root (hd0,0)
 Filesystem type is fat, partition type 0xc
savedefault
makeactive
chainloader +1


Disk error
Press any key to restart
Boot from Hard Disk 0 failed
FATAL: Could not read the boot disk
```

is there any way i can make this work w/o making an image of my windows partition?[/QUOTE]

---

### Post by confused on 2005-09-01
cannot connect to fabrice.bellard website. No such site exists. Is there any other source to download the qemu source codes

---

### Post by CHUCKYCHUCK on 2005-09-01
Could you tell me exactly what to do to share files between WinXP and ubuntu with samba ??
( i'm a samba newbie )
i tried to do what's written in the " WinXP under Qemu  " wiki page, but i didn't succeed ...
thx

here's what i've already done :
installed samba via synaptics
_ shortcut=>connect server,     service type : windows share
                                                  server : mshome
                                                  share : qemushare
                                                  folder : #i left this blank
                                                   user name: qemushare
                                                 connection name : qemushare
then:
_ system=> administration=> shared folders
i shared my home folder : share with samba, name : home


 i start qemu sith the option -smb qemushare

in the emulated winxp, i can't access anything ...

could u help me ? thx ( P.S. i use win XP )

---

### Post by Beestar on 2005-09-01
Hi all!

I had a severe problem with sharing files in a Samba directory, I even posted this in the qemu forum:

> 
The problem is this: how to share files between the Linux host OS and the Windows guest OS. Preferably not using FTP, but by sharing a directory. This should be possible, according to QEMU's author's documentation, Fabrice. So far, I haven't succeeded. 
 
 I have Kubuntu 5.04 as host, Win2K as guest. I compiled qemu 0.7.0, without accellerator, from source and installed it, using the standard ./configure, make, sudo make install. Following this thread I conclude that the file sharing problem is not limited to the Kubuntu/Win2K combination, but dare I say to all Linux host / Windows guest combinations? 
 
 I start qemu as non root with: 
 $ qemu -user-net -smb /home/bee/qemuwinshare hd.img 
 
 In the guest Win2K I can ping 10.0.2.2 and 10.0.2.3 fine. However, 10.0.2.4 (the supposed Samba server) does not respond. 
 
 I put "10.0.2.4 smbserver" in /winnt/system32/drivers/etc/lmhosts (not in lmhosts.sam!). "\\smbserver\qemu" is not accessable in Windows Explorer. 
 
 My smbd is installed in the place qemu expects it: /usr/sbin/ 
 Samba is working correctly, other Windows machines can access my Samba share just fine. 
 
 When I start qemu with a non-existing directory, qemu doesn't complain and starts, with the same result as with an existing directory. 
 
 The Windows user name and password are the same as the one I use to log into Linux. 
 
 I chmod'ed the sharing directory to "ugo+rwx". 
 
 I can use Internet Explorer from the guest OS to surf the Internet fine. 
 
 I really have run out of things to try. I think qemu is an awesome piece of work, and I am dying to use it on a daily basis. However, the file sharing is a must for me. 
 

and thanks to this thread I found the answer.  I posted it back into the qemu forum:
> 
There appears to be two typo's in Qemu man page/website/documentation, which are crucial. ;)
 
 1. The IP address should NOT be 10.0.2.4, but 10.0.2.2. 
 2. The shared directory is NOT in \\10.0.2.2\qemu, but in \\10.0.2.2\<samba share name> 
 
 Hope this solution helps a lot of other people, too. To me it was quite frustrating, to say the least... :)
 
 Anyway, good-bye dual booting... :D


Since it took me a loooooooooong time and a lot of effort to find the solution, I hereby ask Lunde to PLEASE make your excellent HowTo even better by adding this information.

Many thanks in advance, and welcome in Sweden, Lunde!


Bee

---

### Post by CHUCKYCHUCK on 2005-09-01
the windows file which has to be modified, is it the same in xp and 2000 ??
i juste have to paste that line at the very end of the file ???
thx

when i try to access the shared file, i have to enter a user name and password ????? strange .... 
i have to add that line to the windows file:       smbserver 10.0.2.2       right ??
and then from windows         \\10.0.2.2\qemushare      ??
thx

---

### Post by domstyledesign on 2005-09-01
[QUOTE=CHUCKYCHUCK]the windows file which has to be modified, is it the same in xp and 2000 ??
i juste have to paste that line at the very end of the file ???
thx

when i try to access the shared file, i have to enter a user name and password ????? strange .... 
i have to add that line to the windows file:       smbserver 10.0.2.2       right ??
and then from windows         \\10.0.2.2\qemushare      ??
thx[/QUOTE]

your first question is a little unclear.  as for the second, i suspect the user name and password are probably in your samba config.

samba users are listed in the samba conf file.  try:```
sudo cat /etc/samba/smbpasswd
```
you can use the smbpasswd command to add users and change passwords.  check the man page for more info, and good luck.

---

### Post by rcerreto on 2005-09-05
[QUOTE=s_p_a_r_k_y]hi...I'm having a problem as my tun0 is 172.20.0.1 so I setup win98 to use 172.20.0.2

I can ping from windows the linux machine and the reverse as well. However I'm not sure how to setup the routing.... I cannot ping from the windows virtual machine my Router which is 192.168.0.1. I tried

```

iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE

```

to nat masquerade traffic from the tun0 device. Can someone help or should I just put tun0 into the 192.168.0.0/24 range and the win98 machine as well?

EDIT
I CAN ping the 192.168.0.8 address which is eth0 on the host computer. However it doesn't seem to be routing and letting the packets out.
```

sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

```

eth1      Link encap:Ethernet  HWaddr 00:90:4B:68:F2:A4
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe68:f2a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29359588 (27.9 MiB)  TX bytes:48261534 (46.0 MiB)
          Interrupt:19 Base address:0x8000

tun0      Link encap:Ethernet  HWaddr 00:FF:19:F1:D2:24
          inet addr:172.20.0.1  Bcast:172.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2ff:19ff:fef1:d224/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11970 (11.6 KiB)  TX bytes:8692 (8.4 KiB)

```[/QUOTE]

You need to forward packets through the host real NIC (not tun0):

sudo echo 1 > /proc/sys/net/ipv4/ip_forward # to allow forwarding
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE # change NIC accordingly

---

### Post by dante.hicks on 2005-09-07
Hello all,

thanks to this great howto - and especially c4pp4's post on his way to success, I was able to get qemu 0.7.1 and kqemu to run win xp as well as w2k on my XP2800+ with 1GB RAM and an ATI Radeon 9600 (running the recent fglrx drivers).

My aim is to be able to run a modeling software for which I only have a windows license without having to reboot into windows all the time. And here's the catch: the UI runs only at resolutions of 1280 by 1024 or higher...

Unfortunately Win XP is slow on my machine, even after stripping all the styles and background services. And I mean really slow. Except for the speed problem, it works, even at 1280 by 1024.

Win2k on the other hand runs at a reasonable pace which would allow for the anticipated use - but once I try to switch from 1024 by 768 to a higher resolution, the output is distorted, except for any pictures. To give you an idea of the phenomenon, I attached to screenshots: one at normal resolution, one at 1280 by 1024.

Since I'd like to make the switch away from Windoze as my primary OS to Ubuntu, I'd really appreciate any input on this!

---

### Post by Orunitia on 2005-09-09
Edit: Figured it out. Had to format with fdisk beforehand.

Edit 2: I got it installed, but when it goes to boot, it just freezes, and I have to kill Qemu. Any ideas what could be going wrong?

---

### Post by Bomper on 2005-09-10
New version:

     --- qemu-0.7.2

          [http://fabrice.bellard.free.fr/qemu/changelog.html](http://fabrice.bellard.free.fr/qemu/changelog.html)
    
     --- kqemu-0.7.2

          [http://fabrice.bellard.free.fr/qemu/kqemu-changelog.html](http://fabrice.bellard.free.fr/qemu/kqemu-changelog.html)

---

### Post by domstyledesign on 2005-09-10
can anyone explain to me how i can boot windows from my dual boot partition?

---

### Post by Orunitia on 2005-09-10
I got Windows 98 running, but now I can't get online with it. I followed the guide exactly, so I don't know what is wrong. Any help?

---

### Post by MikePB on 2005-09-14
I'm having trouble getting 98 to boot consistantly... plus, the video wn't go above 16 colors/ 640x480, or it'll crash

---

### Post by geearf on 2005-09-15
Hello, just to say that for the moment I am using BOCHS at my university and it works pretty well, I will soon install it on my ubuntu box at home, and test it against qemu I think and see therefore ..

---

### Post by sethmahoney on 2005-09-15
Has anyone gotten this working in Breezy yet?  I'd be surprised if the process was much different, but, you know, thought I'd ask before I stepped into it.

---

### Post by rcerreto on 2005-09-19
[QUOTE=sethmahoney]Has anyone gotten this working in Breezy yet?  I'd be surprised if the process was much different, but, you know, thought I'd ask before I stepped into it.[/QUOTE]

When compiling qemu/kqemu you have to use gcc-3.4 instead of gcc-4.0 (which is the default in breezy) otherwise you'll fail.
After that, I followed the same steps and everything looked OK but...
qemu seems to start and keeps running in the background but no output is produced.

Any suggestion?

---

### Post by Tao on 2005-09-20
[QUOTE=rcerreto]When compiling qemu/kqemu you have to use gcc-3.4 instead of gcc-4.0 (which is the default in breezy) otherwise you'll fail.
After that, I followed the same steps and everything looked OK but...
qemu seems to start and keeps running in the background but no output is produced.

Any suggestion?[/QUOTE]
 Qemu run with no problem on my Breezy (exept I have to force gcc3.4 to compile qemu as you said). Your problem (no output) seems to be not directly linked with Breezy.

---

### Post by jervine on 2005-09-20
ei guyz i finally got it running.. the problem is... i cant find other computers on my network... anybody got a solution about it??

---

### Post by fortytwo on 2005-09-21
I was just taking a look at QEMU and noticed that it has "Full system emulation. In this mode, QEMU emulates a full system (for example a PC), including a processor and various peripherials"...Does this mean I could get my non-linux supported printer to work if I ran windows through QEMU?

---

### Post by weijie90 on 2005-09-24
[SIZE=4]**IF USING BREEZY OR GCC-4.0:** [/SIZE]

run this to compile qemu:
```

cd /path/to/qemuSources
apt-get install gcc-3.4
./configure --cc=/usr/bin/gcc-3.4
make
make install
```

---

### Post by mthaddon on 2005-09-29
I have QEMU installed in binary mode and have two questions. I should note I'm still using Hoary at the moment.
1) What are the implications of allocating shared memory for emulated machines? Is there a limit to this, and is this the amount of my physical memory?
2) I'd like to install from source so I can install the accelerator as well. This is a little complicated by the fact that I'm running on AMD64 and so my binary install is actually in the 32bit chroot. I can't seem to get past the make script in AMD64. Here's what I get:

[abbreviated]
gcc -g -Wl,-T,/home/mthaddon/downloads/qemu-0.7.2/x86_64.ld -o qemu-i386 elfload.o main.o syscall.o mmap.o signal.o path.o osdep.o thunk.o vm86.o libqemu.a gdbstub.o   -lm
/usr/bin/ld:/home/mthaddon/downloads/qemu-0.7.2/x86_64.ld:62: parse error
collect2: ld returned 1 exit status
make[1]: *** [qemu-i386] Error 1
make[1]: Leaving directory `/home/mthaddon/downloads/qemu-0.7.2/i386-user'
make: *** [all] Error 1

Any ideas?
Thanks, Tom

---

### Post by mthaddon on 2005-09-29
Okay, I have it installed, thanks to this thread: [http://ubuntuforums.org/showthread.php?t=50203](http://ubuntuforums.org/showthread.php?t=50203)

Still wondering about the shared memory issue - can anyone help me out on that?

Thanks, Tom

---

### Post by sparhawk on 2005-09-29
Ok I have tried installing qemu about 20 times now but keep getting the same error when I run 'make'

Warning: could not find /home/mmartino/qemu-0.7.2/kqemu/.kqemu-mod.o.cmd for /home/mmartino/qemu-0.7.2/kqemu/kqemu-mod.o
  CC      /home/mmartino/qemu-0.7.2/kqemu/kqemu.mod.o
  LD [M]  /home/mmartino/qemu-0.7.2/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/mmartino/qemu-0.7.2/kqemu'

I have checked and I have gcc3.4 install so thats not the problems and the permissions are correct of the files.

mmartino@tomdickandharry:~/qemu-0.7.2/kqemu$ ls -al
total 420
drwxrwxr-x   3 mmartino mmartino  4096 2005-09-29 18:12 .
drwxr-xr-x  26 mmartino mmartino  4096 2005-09-29 18:08 ..
-rwxrwxr-x   1 mmartino mmartino   545 2005-09-04 09:46 Changelog
-rwxrwxr-x   1 mmartino mmartino   435 2005-02-12 09:36 install.sh
-rwxrwxr-x   1 mmartino mmartino  5863 2005-09-04 12:47 kqemu-doc.html
-rwxrwxr-x   1 mmartino mmartino  4714 2005-09-04 12:47 kqemu-doc.texi
-rwxrwxr-x   1 mmartino mmartino  7216 2005-08-14 12:34 kqemu-freebsd.c
-rwxrwxr-x   1 mmartino mmartino  4134 2005-08-15 09:30 kqemu.h
-rwxrwxr-x   1 mmartino mmartino  1552 2005-09-03 13:46 kqemu.inf
-rwxrwxr-x   1 mmartino mmartino  1374 2005-08-14 12:26 kqemu-kernel.h
-rwxrwxr-x   1 mmartino mmartino 39385 2005-09-29 18:12 kqemu.ko
-rwxrwxr-x   1 mmartino mmartino   194 2005-09-29 18:12 .kqemu.ko.cmd
-rwxrwxr-x   1 mmartino mmartino  8988 2005-09-03 12:39 kqemu-linux.c
-rwxrwxr-x   1 mmartino mmartino  5816 2005-09-29 18:12 kqemu-linux.o
-rwxrwxr-x   1 mmartino mmartino  9725 2005-09-29 18:12 .kqemu-linux.o.cmd
-rwxrwxr-x   1 mmartino mmartino  1625 2005-09-29 18:12 kqemu.mod.c
-rwxrwxr-x   1 mmartino mmartino 31857 2005-09-04 09:37 kqemu-mod-i386.o
-rwxrwxr-x   1 mmartino mmartino 32002 2005-09-04 12:44 kqemu-mod-i386-win32.o
-rwxrwxr-x   1 mmartino mmartino 31857 2005-09-29 18:12 kqemu-mod.o
-rwxrwxr-x   1 mmartino mmartino  3744 2005-09-29 18:12 kqemu.mod.o
-rwxrwxr-x   1 mmartino mmartino  7098 2005-09-29 18:12 .kqemu.mod.o.cmd
-rwxrwxr-x   1 mmartino mmartino 37032 2005-09-04 12:43 kqemu-mod-x86_64.o
-rwxrwxr-x   1 mmartino mmartino 36275 2005-09-29 18:12 kqemu.o
-rwxrwxr-x   1 mmartino mmartino   199 2005-09-29 18:12 .kqemu.o.cmd
-rwxrwxr-x   1 mmartino mmartino 54012 2005-09-04 12:44 kqemu.sys
-rwxrwxr-x   1 mmartino mmartino 10221 2005-09-03 13:45 kqemu-win32.c
-rwxrwxr-x   1 mmartino mmartino   778 2005-08-14 12:25 LICENSE
-rwxrwxr-x   1 mmartino mmartino  1232 2005-09-04 12:45 Makefile
-rwxrwxr-x   1 mmartino mmartino   184 2005-07-28 17:37 Makefile.freebsd
-rwxrwxr-x   1 mmartino mmartino   992 2005-04-17 12:36 Makefile.winnt
-rwxrwxr-x   1 mmartino mmartino   185 2005-02-12 09:34 README
drwxrwxr-x   2 mmartino mmartino  4096 2005-09-29 18:12 .tmp_versions

 The file its looking for... '.kqemu-mod.o.cmd' is in the path its looking for so I am at a loss. When I try to finish the install and load the module it says module not found. Any help in this would be welcome.

---

### Post by mthaddon on 2005-09-30
what does your ./configure look like?

---

### Post by sparhawk on 2005-09-30
Show me yours and I will show you mine... ah just kidding
Here it is

mmartino@tomdickandharry:~/qemu-0.7.2$ ./configure
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/mmartino/qemu-0.7.2
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu
gprof enabled     no
static build      no
SDL support       yes
SDL static link   no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /lib/modules/2.6.10-5-386/build
kbuild type       2.6

So any ideas????????

---

### Post by oddflux on 2005-09-30
Why would you want windows in linux o_0, I think we all agree that windows doesn't tickle our fancy.

---

### Post by sparhawk on 2005-10-01
I would love not to use windows but I work for an IT company and we use Radmin for remote desktop administration and you can not use it in linux if you need NT/Auth... so here I am. I am working on a way around the issue but for a couple of weeks I need Radmin to work... :( I guess that might mean staying with windows for a while.

---

### Post by neouser99 on 2005-10-04
[QUOTE=flange]Did anyone else encounter this problem and solve it?  I'm stuck on this now, and so far haven't found a fix.[/QUOTE]
Yes, I am also having the same troubles and was wondering how people got around this...it is early in the morning, and maybe I am just too lazy to figure it out...but if it has been figured out, that is easier then trying.

I apologize for the strange message, I thought that the quote would include the quote that flange had inside of it...

here is my error. i have run apt-get install libsdl1.2-dev

```

root@trinity:~/qemu-0.7.2 # ./configure
big/little test failed
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /root/qemu-0.7.2
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu
gprof enabled     no
static build      no
SDL support       no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers-2.6.10-5-686-smp
kbuild type       2.6
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.

```

---

### Post by neouser99 on 2005-10-04
[QUOTE=neouser99]Yes, I am also having the same troubles and was wondering how people got around this...it is early in the morning, and maybe I am just too lazy to figure it out...but if it has been figured out, that is easier then trying.

I apologize for the strange message, I thought that the quote would include the quote that flange had inside of it...

here is my error. i have run apt-get install libsdl1.2-dev

```

root@trinity:~/qemu-0.7.2 # ./configure
big/little test failed
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /root/qemu-0.7.2
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu
gprof enabled     no
static build      no
SDL support       no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers-2.6.10-5-686-smp
kbuild type       2.6
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.

```[/QUOTE]

I seemed to have fixed my problem...qemu's configure was looking for gcc, not gcc-3.3 which was the bin installed on my computer. all i had to do to fix things was softlink using this command
```
ln -sf /usr/bin/gcc-3.3 /usr/bin/gcc
```

Hope this helps someone else, if they are having issues.

---

### Post by refdoc on 2005-10-05
My laptop came with one of those stupid recovery disks. The installer stops when probing my qemu install whether it is the real thing.

Anyone any ideas?

Thanks!

---

### Post by Lunde on 2005-10-06
There are problems with some recovery CD's because the hardware that Qemu emulates is not similar the hardware of your computer.

---

### Post by Lunde on 2005-10-06
I'm back, just moved to Sweeden and have not been able to answere any questions the last weeks.

---

### Post by Lunde on 2005-10-06
/home/mmartino/qemu-0.7.2/kqemu/.kqemu**[COLOR="Red"]-[/COLOR]**mod.o.cmd (-)
-rwxrwxr-x   1 mmartino mmartino  7098 2005-09-29 18:12 .kqemu[COLOR="Red"]**.**[/COLOR]mod.o.cmd (.)

Hmm.. this looks like a typo in this release. I don't know if it's possible and if it would work, but I would try to rename the file.

[QUOTE=sparhawk]Ok I have tried installing qemu about 20 times now but keep getting the same error when I run 'make'
Warning: could not find /home/mmartino/qemu-0.7.2/kqemu/.kqemu-mod.o.cmd for /home/mmartino/qemu-0.7.2/kqemu/kqemu-mod.o
CC      /home/mmartino/qemu-0.7.2/kqemu/kqemu.mod.o
LD [M]  /home/mmartino/qemu-0.7.2/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/mmartino/qemu-0.7.2/kqemu'
I have checked and I have gcc3.4 install so thats not the problems and the permissions are correct of the files.
mmartino@tomdickandharry:~/qemu-0.7.2/kqemu$ ls -al
total 420
drwxrwxr-x   3 mmartino mmartino  4096 2005-09-29 18:12 .
drwxr-xr-x  26 mmartino mmartino  4096 2005-09-29 18:08 ..
-rwxrwxr-x   1 mmartino mmartino   545 2005-09-04 09:46 Changelog
-rwxrwxr-x   1 mmartino mmartino   435 2005-02-12 09:36 install.sh
-rwxrwxr-x   1 mmartino mmartino  5863 2005-09-04 12:47 kqemu-doc.html
-rwxrwxr-x   1 mmartino mmartino  4714 2005-09-04 12:47 kqemu-doc.texi
-rwxrwxr-x   1 mmartino mmartino  7216 2005-08-14 12:34 kqemu-freebsd.c
-rwxrwxr-x   1 mmartino mmartino  4134 2005-08-15 09:30 kqemu.h
-rwxrwxr-x   1 mmartino mmartino  1552 2005-09-03 13:46 kqemu.inf
-rwxrwxr-x   1 mmartino mmartino  1374 2005-08-14 12:26 kqemu-kernel.h
-rwxrwxr-x   1 mmartino mmartino 39385 2005-09-29 18:12 kqemu.ko
-rwxrwxr-x   1 mmartino mmartino   194 2005-09-29 18:12 .kqemu.ko.cmd
-rwxrwxr-x   1 mmartino mmartino  8988 2005-09-03 12:39 kqemu-linux.c
-rwxrwxr-x   1 mmartino mmartino  5816 2005-09-29 18:12 kqemu-linux.o
-rwxrwxr-x   1 mmartino mmartino  9725 2005-09-29 18:12 .kqemu-linux.o.cmd
-rwxrwxr-x   1 mmartino mmartino  1625 2005-09-29 18:12 kqemu.mod.c
-rwxrwxr-x   1 mmartino mmartino 31857 2005-09-04 09:37 kqemu-mod-i386.o
-rwxrwxr-x   1 mmartino mmartino 32002 2005-09-04 12:44 kqemu-mod-i386-win32.o
-rwxrwxr-x   1 mmartino mmartino 31857 2005-09-29 18:12 kqemu-mod.o
-rwxrwxr-x   1 mmartino mmartino  3744 2005-09-29 18:12 kqemu.mod.o
-rwxrwxr-x   1 mmartino mmartino  7098 2005-09-29 18:12 .kqemu.mod.o.cmd
-rwxrwxr-x   1 mmartino mmartino 37032 2005-09-04 12:43 kqemu-mod-x86_64.o
-rwxrwxr-x   1 mmartino mmartino 36275 2005-09-29 18:12 kqemu.o
-rwxrwxr-x   1 mmartino mmartino   199 2005-09-29 18:12 .kqemu.o.cmd
-rwxrwxr-x   1 mmartino mmartino 54012 2005-09-04 12:44 kqemu.sys
-rwxrwxr-x   1 mmartino mmartino 10221 2005-09-03 13:45 kqemu-win32.c
-rwxrwxr-x   1 mmartino mmartino   778 2005-08-14 12:25 LICENSE
-rwxrwxr-x   1 mmartino mmartino  1232 2005-09-04 12:45 Makefile
-rwxrwxr-x   1 mmartino mmartino   184 2005-07-28 17:37 Makefile.freebsd
-rwxrwxr-x   1 mmartino mmartino   992 2005-04-17 12:36 Makefile.winnt
-rwxrwxr-x   1 mmartino mmartino   185 2005-02-12 09:34 README
drwxrwxr-x   2 mmartino mmartino  4096 2005-09-29 18:12 .tmp_versions
The file its looking for... '.kqemu-mod.o.cmd' is in the path its looking for so I am at a loss. When I try to finish the install and load the module it says module not found. Any help in this would be welcome.[/QUOTE]

---

### Post by Lunde on 2005-10-06
There might be several reasons for this error. 
Your screencard does not handle the 2 screens in this resolution, check if you have the latest linux driver. 

Might be that it's the resolution change that causes it and not the resolution it self. try to shutdown windows with the new settings even if it's wrong, then restart X and boot up Qemu again

---

### Post by geearf on 2005-10-06
Hello,

I am writing a mini OS, and I use bochs a lot to try it, but I cannot run it on Qemu, it tells me there is no bootable media, where my image is one of a floppy that works fine on bochs and on real hardware.

I'd like to try it on Qemu, to see if it's faster.

Thanks.

---

### Post by Lunde on 2005-10-06
Not sure if it works, but I can't see why not. What command do you use to start it? and are all permissions set correct?

---

### Post by geearf on 2005-10-06
Hello,

I need to set permissions ?
Oh and I tried various commandes like "qemu -boot a -fda image"

---

### Post by Lunde on 2005-10-06
Permissions.. Only that the user you start Qemu with has permissions to use the image.

OK try this.. download a bootdisk image from bootdisk.com and extract the image from the .exe file with Archive Manager. Then see if your able to boot that image to check if the problem is with the image or with Qemu.

---

### Post by geearf on 2005-10-06
Hello,

good guess it works with another image, but not mine (which was made with tools provided by the theachers, that work with bochs and real computer, how strange).

Also about permissions, I only have one user, so no problem there.

Thanks,

---

### Post by barmaley on 2005-10-07
Hallo, guys!
1st of all thank you for this great guide.
2nd of all - HEEEEEEEEELP!
I failed to install win2k for a couple of days already and it drives me crazy. I really need windows on my comp to run OriginLab, Shadow ray tracing and sometimes for MS Word and IE.
The problem is that win2k installation goes smoothely up to a point where it says:

"The disk space on C: is insufficient for the components that are currently selected. You  will need to change your component selections".

From this point I don't know what to do. I created an image of 3.5G, should be enough. For installation I use:
qemu -hda win2k.img -cdrom /dev/cdrom -boot d -m 256
After reboot I type 'c' instead of 'd'.
Does anybody know what can be done?
Thank you in advance.

---

### Post by geearf on 2005-10-07
There is a parameter to give to qemu for that bug, I don't remember which but you'll find it in the man of qemu.

---

### Post by Zenbob96 on 2005-10-07
If your image area is only set at 3.5 GB for Windows 2000, plus some rather resource hungry applications and the Windows memory manager, you will likely need a larger partition area.  I have never tried running Windows on less than about 5.5 to 6.5 GB, as it is a real memory hog, and even when forced into smaller partition sizes (that install indicates will work) it does not work well.

Ubuntu can run very well in very small environments, but of course, it's not the resource zombie that MS Windows ends up being.

If your HDD allows for a bigger Windows environment, go ahead and allocate more space to it, rather than try to compress it all into the most "effecient" envelope possible.

Hard driv prices continue to drop, and if you need to install a new drive or second drive, that is also a reasonable option.

Good Luck!

---

### Post by barmaley on 2005-10-07
Thank you guys!
I'll try both geearf's and Zenbob96's advices. Though throughout the thread 3.5G was enough for everybody and noone came up with my problem.
geearf, if you could remember this option, plese post it here.
I'll try to find it by myself, bit one always wants to save time.
Thank you one more time! Ubuntu guys are great!

---

### Post by barmaley on 2005-10-07
geearf, is this the option you meant?
-win2k-hack
Use it when installing Windows 2000 to avoid a disk full bug. After Windows 2000 is installed, you no longer need this option (this option slows down the IDE transfers).
This is the only option I found in the qemu man to be somehow relevant to my problem, though I did not have full disk error, on the contrary disk was empty and had a capacity of 0 B.
I'll try it.  It is strange, I made same steps as everybody did and only I experience this problem. Is it because of my luck or because of win2k? :)

---

### Post by oxEz on 2005-10-07
When I first tried to compile it, I receive an error about 'GENERAL_REG', which can be found [here]("http://gcc.gnu.org/ml/gcc-bugs/2005-06/msg02034.html").

I fixed it by installing gcc-3.3 (3.4 could be fine), and editing the configure script as follows:
```

cc="gcc-3.3"
host_cc="gcc-3-3"

```

It suddently worked. Apparently it won't compile on GCC4. 

Thank you for the HOWTO, I have read it and it seems pretty accurate. Thanks!

---

### Post by oxEz on 2005-10-07
Okay, compilation is done, installation is completed. However when I run qemu I have this error:
```
qemu: could not open hard disk image 'hd.img'

```

The command I ran was:   qemu -boot d -cdrom /dev/cdrom -hda hd.img -user-net

Yes I created the disk image, and I'm in it's directory. I have to mention I'm installing QEMU on a free FAT32 partition newly created (it is totally empty).

Thanks!

[EDIT]

Okay, I figured out that FAT32 file system cannot handle large files.. and obviously 4 GB was a large file. That's why it didn't create the .img at first. I reformated the partition at ext2, and now it works.

---

### Post by barmaley on 2005-10-08
Hallo, guys.
I have at last win2k running with Qemu.
When installing windows 2000, the correct option is -win2k-hack.
It is mentioned in the qemu man.
Win2k runs a bit slower than I expected, but I like it even this way.
Thank you, Lunde for the guide, and geearf and Zenbob96 for your advices.
Great community. :D

---

### Post by dis-abled on 2005-10-08
[QUOTE=AgenT]One thing you may want to add. Instead of using "make install", you could use checkinstall (apt-get install checkinstall or use Synaptic). checkinstall is the best way to install compiled programs because it will make and install deb's instead of just installing the program! This means that you will have QEMU installed as if it were installed via apt-get or Synaptic! Neat stuff! To remove all you would have to do is apt-get remove qemu or removie via Synaptic. That is, everything would be done the same way as if you were to install a deb.

Quick rundown for any source code package using configure:
 ```
./configure
make
checkinstall
``` 
In other words, just replace the step "make install" with "checkinstall". That's it!

WARNING: make sure you are not running anything that touches your apt database. This means that you should not have Synaptic open or have apt-get running while using checkinstall. This will screw up checkinstall because it will be unable to install the deb files that it makes since the resources will be used by apt-get/Synaptic.[/QUOTE]


Awsome post, I am going to go try it!! Thanks!

---

### Post by Azrael on 2005-10-08
Kudos for a great howto!

Before I try installing Qemu myself I have some (probably silly) question to ask.

How much hardware can you access from within the guest OS (would be Windows 2000 in my case)? Can you for instance communicate with USB peripherals?

I have a Palm m505 PDA and I would be really nice if I could sync my PDA with my Palm Desktop manager (in Windows 2000 over Qemu over Ubuntu).

---

### Post by meastp on 2005-10-11
[QUOTE=Azrael]How much hardware can you access from within the guest OS (would be Windows 2000 in my case)? Can you for instance communicate with USB peripherals?[/QUOTE]

Could someone please answer? I want to use qemu->windows to transfer files to my netMD...

---

### Post by Brando569 on 2005-10-12
im using vmware 5 and ive set it up correctly according to the directions on their website, when i try to boot grub gives me error 17 anyone know how to fix this?

---

### Post by Azrael on 2005-10-16
[QUOTE=Azrael]Kudos for a great howto!

Before I try installing Qemu myself I have some (probably silly) question to ask.

How much hardware can you access from within the guest OS (would be Windows 2000 in my case)? Can you for instance communicate with USB peripherals?

I have a Palm m505 PDA and I would be really nice if I could sync my PDA with my Palm Desktop manager (in Windows 2000 over Qemu over Ubuntu).[/QUOTE]
I figured I'd answer my own inquiries in the unlikely case that anyone cares.

No, you can't use USB in a Qemu guest OS. Maybe in the future...

However, if you have a PDA with a network sync function like I have you can still flawlessly sync between your PDA and PDA desktop software in the Qemu guest OS.

After a day of investigating, I arranged it like this:

_On the Palm m505:_
1) In the main menu choose "HotSync" > "Options" > "LANSync Prefs" > "LANSync".
2) Open "HotSync" > "options" > "Primary PC Setup" and enter as "Primary PC Name" the same name you use in Windows on Qemu and enter as "Primary PC Address" 10.0.2.15 and enter as "Subnet Mask" 255.255.255.0.

_In Ubuntu_
1)sudo apt-get install pilot-link
2)gedit /path/to/where-ever/you/want/your/shell/script.sh
3)Enter this:
#!/bin/sh
sudo iptables -t nat -A OUTPUT -d 10.0.2.15 -j DNAT --to-destination 127.0.0.1
sleep 2s
sudo pi-nredir -p /dev/ttyUSB1
sleep 40s
sudo iptables -t nat -D OUTPUT -d 10.0.2.15 -j DNAT --to-destination 127.0.0.1
#iptables are being (ab)used because after every sync the Palm resets the IP address
#it uses to the IP of the of the OS in which Palm Desktop runs, which in this case is the
#Qemu guest OS, which more or less needs to have 10.0.2.15 as its IP address.
4)chmod 755 /path/to/where-ever/you/want/your/shell/script.sh
5)sudo gedit /etc/udev/udev.rules
6)Change the line:
BUS=="usb", KERNEL=="ttyUSB*", SYSFS{product}=="Palm Handheld*", \
					SYMLINK+="pilot"
To:
BUS=="usb", KERNEL=="ttyUSB1", SYSFS{product}=="Palm Handheld*", \
					SYMLINK+="pilot", RUN="/path/to/where-ever/you/want/your/shell/script.sh"
7)Run Qemu with the options "-user-net" and "-redir tcp:14238::14238".

_In Windows on Qemu:_
1)Open "Palm Desktop" and "HotSync Manager".
2)Right-click the HotSync Manager icon in the systray and check (only) "Network".
3)Right-click the HotSync Manager icon in the systray and click "Setup" and set the correct user if necessary and set "Subnet Mask" to 255.255.255.0.

Syncing with the Palm Desktop should now happen automagically whenever you press the HotSync button on the Palm cradle.

---

### Post by geearf on 2005-10-17
[QUOTE=geearf]Hello,

I am writing a mini OS, and I use bochs a lot to try it, but I cannot run it on Qemu, it tells me there is no bootable media, where my image is one of a floppy that works fine on bochs and on real hardware.

I'd like to try it on Qemu, to see if it's faster.

Thanks.[/QUOTE]

still wondering if anyone know anything about that :)

---

### Post by hamacker on 2005-10-18
if "make" show the follow error : "(...)/qemu-0.7.2/target-i386/ops_sse.h:574:
confused by earlier errors, bailing out" then probally you use a gcc4.
Please this form :
./configure --cc=gcc-3.4
make
(continue the article)

---

### Post by Oan on 2005-10-18
I'm trying to install Windows XP with Qemu, following step-by-step this HOW-TO. Qemu installed fine, but alas! - when I try to use the Windows' install cd I encouter the same problem as Karl [here]("http://www.ubuntuforums.org/showpost.php?p=238348&postcount=150") had:

[QUOTE=Karl S.]
And this is the problem I came up with:

In the Terminal:
[screenshot here](http://www.columbia.edu/~kts15/hblog/KarlQEMU.png)[/QUOTE]

I've tried to use both my cd-devices with different paths, make an iso-image of the cd and a pile of other "tricks" I've read over here..The result is always the Qemu-screen with "FATAL: Could not read the boot disk". 

Were the any solutions for this?

---

### Post by suRoot on 2005-10-30
Qemu is really cool - I've used it before & really like it.  However, as the OP stated, performance is second to VMWare.  That has been my experience, as well.

Luckily, as of a few days ago, VMWare has started to offer a new option (which happens to be free!!) - it's called VMWare Player.  It runs on Ubuntu, as I'm using it now.  You can read all about it at the VMWare site, but in a nutshell it only plays VM images - you can't create /edit new ones (although you can open the vmx file in vi or gedit and make some minor device related changes).

Here's what you do:

Download the VMWare Workstation eval at [http://www.vmware.com/download/ws/eval.html]("http://www.vmware.com/download/ws/eval.html")

Install it (there are several walkthroughs on the boards for doing this - I can help if you have a problem).  Once installed, setup as many virtual machines as you want.

After you create your virtual machines, you can get rid of VMWare workstation.  Just make sure you've stored the image files someplace else so you can use them again.

Download the VMWare Player at [http://www.vmware.com/download/player/]("http://www.vmware.com/download/player/")

Install it - the process is basically the same as installing VMWare workstation.  Once installed, fire it up & point it at your existing VM images.  Bingo - now you've got all the benefits of running VMWare --  **for free**!

I like Qemu - I suggest you try it out as it's a great learning experience.  It may run better than VMWare on your machine, anyway.  For me, though, VMWare is the better option.

---

### Post by trinaryouroboros on 2005-11-02
[QUOTE=Lunde]Correction: 
**$ sudo chmod -R 775 /home/karl/qemu-0.7.0/kqemu**

Sorry![/QUOTE]

Hey, excellent troubleshooting Lunde!

I'm getting a similar problem however, and I've followed and tracked just about every bit of posted advice I could about Ubuntu / Debian kqemu issues.

I still get the same problem listed previous. I tried even using alternate kernels even to see if maybe my linux-header files and kernel might have had some type of conflict with qemu installs.

To note, I am not using 0.7.0 - the latest I nabbed is 0.7.2, and I'm hoping I can still use this newer package the same as 0.7.0.

I have Ubuntu 5.04 / Hoary Hedgehog - 64-bit edition, running on an AMD64 3000+ processor, Lanparty nF4 Ultra-D mobo with 1GB (2x512) of Corsair RAM, video card temporarily is ATI All-in-Wonder Pro 128 PCI (rage128), hard drive is simple 30GB Western Digital IDE, two cd-roms - the main one I'm using for kqemu purpose is specified as "/dev/cdrw" on my box.

Windows XP Corporate Edition SP2 was installed with qemu by .iso image, successful but miserably slow install, and no operable drivers installed appropriately to surf the internet / exchange files / whatever I need to do - and OS is junkily slow as well during emu. I picked up litexppro, which I will happily use if I can get this thing operable enough, otherwise it's going on my returns list.

A brief idea of what I need XP for: Mainly development and graphic work. I need it primarily for a graphical wargame, of which I'll be happy to update any contributors on it's progress. Genre is Cyberpunk/Hacker orient, mild William Gibson implementation, GNU public license - freeware.

**uname -r ** returns: **2.6.10-5-amd64-xeon**

I'm using the appropriate specified linux-headers, and edited the configure file with: 

**kernel_path="/usr/src/linux-headers-2.6.10-5-amd64-xeon"**

I followed all instructions previous, and in order to properly configure, I have to do the following or make just does nothing:

**./configure --target-list=x86_64-softmmu**

then **make** is as follows at the kqemu portion:

> make[1]: Leaving directory `/home/ouroboros/qemu-0.7.2/x86_64-softmmu'
make -C kqemu
make[1]: Entering directory `/home/ouroboros/qemu-0.7.2/kqemu'
make -C /usr/src/linux-headers-2.6.10-5-amd64-xeon M=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'
  CC [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu-linux.o
cp /home/ouroboros/qemu-0.7.2/kqemu/kqemu-mod-x86_64.o /home/ouroboros/qemu-0.7.2/kqemu/kqemu-mod.o
  LD [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/ouroboros/qemu-0.7.2/kqemu/.kqemu-mod.o.cmd for /home/ouroboros/qemu-0.7.2/kqemu/kqemu-mod.o
  CC      /home/ouroboros/qemu-0.7.2/kqemu/kqemu.mod.o
  LD [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'
make[1]: Leaving directory `/home/ouroboros/qemu-0.7.2/kqemu'

My kqemu permissions are as follows :

> ouroboros@w0-rm-h0-l3:~/qemu-0.7.2$ ls -al kqemu
total 448
drwxrwxr-x   3 ouroboros root       4096 2005-11-02 11:45 .
drwxrwxr-x  26 ouroboros root       4096 2005-11-02 11:43 ..
-rwxrwxr-x   1 ouroboros ouroboros   545 2005-09-04 09:46 Changelog
-rwxrwxr-x   1 ouroboros ouroboros   435 2005-02-12 09:36 install.sh
-rwxrwxr-x   1 ouroboros ouroboros  5863 2005-09-04 12:47 kqemu-doc.html
-rwxrwxr-x   1 ouroboros ouroboros  4714 2005-09-04 12:47 kqemu-doc.texi
-rwxrwxr-x   1 ouroboros ouroboros  7216 2005-08-14 12:34 kqemu-freebsd.c
-rwxrwxr-x   1 ouroboros ouroboros  4134 2005-08-15 09:30 kqemu.h
-rwxrwxr-x   1 ouroboros ouroboros  1552 2005-09-03 13:46 kqemu.inf
-rwxrwxr-x   1 ouroboros ouroboros  1374 2005-08-14 12:26 kqemu-kernel.h
-rw-r--r--   1 ouroboros ouroboros 48600 2005-11-02 11:45 kqemu.ko
-rwxrwxr-x   1 ouroboros root        200 2005-11-02 11:45 .kqemu.ko.cmd
-rwxrwxr-x   1 ouroboros ouroboros  8988 2005-09-03 12:39 kqemu-linux.c
-rw-r--r--   1 ouroboros ouroboros  9136 2005-11-02 11:45 kqemu-linux.o
-rw-r--r--   1 ouroboros ouroboros  8131 2005-11-02 11:45 .kqemu-linux.o.cmd
-rw-r--r--   1 ouroboros ouroboros  1582 2005-11-02 11:45 kqemu.mod.c
-rwxrwxr-x   1 ouroboros ouroboros 31857 2005-09-04 09:37 kqemu-mod-i386.o
-rwxrwxr-x   1 ouroboros ouroboros 32002 2005-09-04 12:44 kqemu-mod-i386-win32.o
-rwxr-xr-x   1 ouroboros ouroboros 37032 2005-11-02 11:45 kqemu-mod.o
-rw-r--r--   1 ouroboros ouroboros  5136 2005-11-02 11:45 kqemu.mod.o
-rw-r--r--   1 ouroboros ouroboros  6384 2005-11-02 11:45 .kqemu.mod.o.cmd
-rwxrwxr-x   1 ouroboros ouroboros 37032 2005-09-04 12:43 kqemu-mod-x86_64.o
-rw-r--r--   1 ouroboros ouroboros 44382 2005-11-02 11:45 kqemu.o
-rwxrwxr-x   1 ouroboros root        205 2005-11-02 11:45 .kqemu.o.cmd
-rwxrwxr-x   1 ouroboros ouroboros 54012 2005-09-04 12:44 kqemu.sys
-rwxrwxr-x   1 ouroboros ouroboros 10221 2005-09-03 13:45 kqemu-win32.c
-rwxrwxr-x   1 ouroboros ouroboros   778 2005-08-14 12:25 LICENSE
-rwxrwxr-x   1 ouroboros ouroboros  1232 2005-09-04 12:45 Makefile
-rwxrwxr-x   1 ouroboros ouroboros   184 2005-07-28 17:37 Makefile.freebsd
-rwxrwxr-x   1 ouroboros ouroboros   992 2005-04-17 12:36 Makefile.winnt
-rwxrwxr-x   1 ouroboros ouroboros   185 2005-02-12 09:34 README
drwxrwxr-x   2 ouroboros root       4096 2005-11-01 21:05 .tmp_versions

The official qemu-0.7.2 directory is as follows : 

> ouroboros@w0-rm-h0-l3:~/qemu-0.7.2$ ls -al ../qemu-0.7.2
total 2628
drwxrwxr-x  26 ouroboros root        4096 2005-11-02 11:43 .
drwxr-xr-x  52 ouroboros ouroboros   4096 2005-11-01 21:05 ..
-rwxrwxr-x   1 ouroboros ouroboros  61233 2005-09-04 13:11 aes.c
-rwxrwxr-x   1 ouroboros ouroboros    717 2005-09-04 13:11 aes.h
-rwxrwxr-x   1 ouroboros ouroboros  82481 2005-09-04 13:11 alpha-dis.c
-rwxrwxr-x   1 ouroboros ouroboros   4098 2005-09-04 13:11 alpha.ld
-rwxrwxr-x   1 ouroboros ouroboros  14095 2005-09-04 13:11 a.out.h
-rwxrwxr-x   1 ouroboros ouroboros  56493 2005-09-04 13:11 arm-dis.c
drwxrwxr-x   4 ouroboros root        4096 2005-11-01 22:20 armeb-user
-rwxrwxr-x   1 ouroboros ouroboros   4107 2005-09-04 13:11 arm.ld
drwxrwxr-x   4 ouroboros root        4096 2005-11-01 22:20 arm-user
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 audio
-rwxrwxr-x   1 ouroboros ouroboros   6328 2005-09-04 13:11 block-bochs.c
-rwxrwxr-x   1 ouroboros ouroboros  16254 2005-09-04 13:11 block.c
-rwxrwxr-x   1 ouroboros ouroboros   4953 2005-09-04 13:11 block-cloop.c
-rwxrwxr-x   1 ouroboros ouroboros   8028 2005-09-04 13:11 block-cow.c
-rwxrwxr-x   1 ouroboros ouroboros   8293 2005-09-04 13:11 block-dmg.c
-rwxrwxr-x   1 ouroboros ouroboros   3105 2005-09-04 13:11 block_int.h
-rwxrwxr-x   1 ouroboros ouroboros  22466 2005-09-04 13:11 block-qcow.c
-rwxrwxr-x   1 ouroboros ouroboros  14234 2005-09-04 13:11 block-vmdk.c
-rwxrwxr-x   1 ouroboros ouroboros   6641 2005-09-04 13:11 block-vpc.c
-rwxrwxr-x   1 ouroboros ouroboros  54492 2005-09-04 13:11 block-vvfat.c
-rwxrwxr-x   1 ouroboros ouroboros   4454 2005-09-04 13:11 bswap.h
-rwxrwxr-x   1 ouroboros ouroboros  12044 2005-09-04 13:11 Changelog
-rwxrwxr-x   1 ouroboros ouroboros  17443 2005-09-04 13:11 cocoa.m
-rwxrwxr-x   1 ouroboros root         284 2005-11-02 11:43 config-host.h
-rwxrwxr-x   1 ouroboros root         539 2005-11-02 11:43 config-host.mak
-rwxrwxr-x   1 ouroboros ouroboros  20487 2005-11-01 22:19 configure
-rwxrwxr-x   1 ouroboros ouroboros  19553 2005-09-04 13:11 console.c
-rwxrwxr-x   1 ouroboros ouroboros  17976 2005-09-04 13:11 COPYING
-rwxrwxr-x   1 ouroboros ouroboros  26428 2005-09-04 13:11 COPYING.LIB
-rwxrwxr-x   1 ouroboros ouroboros  18961 2005-09-04 13:11 cpu-all.h
-rwxrwxr-x   1 ouroboros ouroboros   2964 2005-09-04 13:11 cpu-defs.h
-rwxrwxr-x   1 ouroboros ouroboros  42833 2005-09-04 13:11 cpu-exec.c
-rwxrwxr-x   1 ouroboros ouroboros    264 2005-09-04 13:11 .cvsignore
-rwxrwxr-x   1 ouroboros ouroboros   9888 2005-09-04 13:11 disas.c
-rwxrwxr-x   1 ouroboros ouroboros    673 2005-09-04 13:11 disas.h
-rwxrwxr-x   1 ouroboros ouroboros  17154 2005-09-04 13:11 dis-asm.h
-rwxr-xr-x   1 ouroboros ouroboros  39043 2005-11-02 11:43 dyngen
-rwxrwxr-x   1 ouroboros ouroboros  81199 2005-09-04 13:11 dyngen.c
-rwxrwxr-x   1 ouroboros ouroboros   6558 2005-09-04 13:11 dyngen-exec.h
-rwxrwxr-x   1 ouroboros ouroboros  12377 2005-09-04 13:11 dyngen.h
-rwxrwxr-x   1 ouroboros ouroboros    162 2005-09-04 13:11 dyngen-op.h
-rwxrwxr-x   1 ouroboros ouroboros  42647 2005-09-04 13:11 elf.h
-rwxrwxr-x   1 ouroboros ouroboros  17893 2005-09-04 13:11 exec-all.h
-rwxrwxr-x   1 ouroboros ouroboros  72984 2005-09-04 13:11 exec.c
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 fpu
-rwxrwxr-x   1 ouroboros ouroboros  20370 2005-09-04 13:11 gdbstub.c
-rwxrwxr-x   1 ouroboros ouroboros    206 2005-09-04 13:11 gdbstub.h
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 hw
-rwxrwxr-x   1 ouroboros ouroboros  99388 2005-09-04 13:11 i386-dis.c
-rwxrwxr-x   1 ouroboros ouroboros   4547 2005-09-04 13:11 i386.ld
drwxrwxr-x   4 ouroboros root        4096 2005-11-01 22:20 i386-softmmu
drwxrwxr-x   3 ouroboros root        4096 2005-11-01 22:20 i386-user
-rwxrwxr-x   1 ouroboros ouroboros   4455 2005-09-04 13:11 i386-vl.ld
-rwxrwxr-x   1 ouroboros ouroboros   8582 2005-09-04 13:11 ia64.ld
-rwxrwxr-x   1 ouroboros ouroboros    884 2005-09-04 13:11 ia64-syscall.S
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 keymaps
-rwxrwxr-x   1 ouroboros ouroboros   4285 2005-09-04 13:11 keymaps.c
drwxrwxr-x   3 ouroboros root        4096 2005-11-02 11:45 kqemu
-rwxrwxr-x   1 ouroboros ouroboros  21228 2005-09-04 13:11 kqemu.c
-rwxrwxr-x   1 ouroboros ouroboros    346 2005-09-04 13:11 LICENSE
-rwxrwxr-x   1 ouroboros ouroboros   2180 2005-09-04 13:11 linux-2.6.9-qemu-fast.patch
drwxrwxr-x   7 ouroboros root        4096 2005-09-04 13:11 linux-user
-rwxrwxr-x   1 ouroboros ouroboros   6090 2005-09-04 13:11 m68k.ld
-rwxrwxr-x   1 ouroboros ouroboros   3768 2005-09-04 13:11 Makefile
-rwxrwxr-x   1 ouroboros ouroboros  10087 2005-09-04 13:11 Makefile.target
-rwxrwxr-x   1 ouroboros ouroboros 161384 2005-09-04 13:11 mips-dis.c
drwxrwxr-x   4 ouroboros root        4096 2005-11-01 22:20 mips-softmmu
-rwxrwxr-x   1 ouroboros ouroboros  55126 2005-09-04 13:11 monitor.c
-rwxrwxr-x   1 ouroboros ouroboros  15040 2005-09-04 13:11 osdep.c
-rwxrwxr-x   1 ouroboros ouroboros   1438 2005-09-04 13:11 osdep.h
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 pc-bios
-rwxrwxr-x   1 ouroboros ouroboros 132561 2005-09-04 13:11 ppc-dis.c
-rwxrwxr-x   1 ouroboros ouroboros   4559 2005-09-04 13:11 ppc.ld
drwxrwxr-x   4 ouroboros root        4096 2005-11-01 22:20 ppc-softmmu
drwxrwxr-x   3 ouroboros root        4096 2005-11-01 22:20 ppc-user
-rwxrwxr-x   1 ouroboros ouroboros  15282 2005-09-04 13:11 qemu.1
-rwxrwxr-x   1 ouroboros ouroboros   1936 2005-09-04 13:11 qemu-binfmt-conf.sh
-rwxrwxr-x   1 ouroboros ouroboros  50911 2005-09-04 13:11 qemu-doc.html
-rwxrwxr-x   1 ouroboros ouroboros  37538 2005-09-04 13:11 qemu-doc.texi
-rwxr-xr-x   1 ouroboros ouroboros 218109 2005-11-02 11:43 qemu-img
-rwxrwxr-x   1 ouroboros ouroboros   8918 2005-09-04 13:11 qemu-img.1
-rwxrwxr-x   1 ouroboros ouroboros  17849 2005-09-04 13:11 qemu-img.c
-rwxrwxr-x   1 ouroboros ouroboros   4029 2005-09-04 13:11 qemu-img.texi
-rwxrwxr-x   1 ouroboros ouroboros  23957 2005-09-04 13:11 qemu-tech.html
-rwxrwxr-x   1 ouroboros ouroboros  18466 2005-09-04 13:11 qemu-tech.texi
-rwxrwxr-x   1 ouroboros ouroboros  11158 2005-09-04 13:11 readline.c
-rwxrwxr-x   1 ouroboros ouroboros     58 2005-09-04 13:11 README
-rwxrwxr-x   1 ouroboros ouroboros    525 2005-09-04 13:11 README.distrib
-rwxrwxr-x   1 ouroboros ouroboros   7195 2005-09-04 13:11 s390.ld
-rwxrwxr-x   1 ouroboros root        1094 2005-11-01 21:05 scr.sh
-rwxrwxr-x   1 ouroboros ouroboros  15862 2005-09-04 13:11 sdl.c
-rwxrwxr-x   1 ouroboros ouroboros   8772 2005-09-04 13:11 sdl_keysym.h
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 slirp
-rwxrwxr-x   1 ouroboros ouroboros  10165 2005-09-04 13:11 softmmu_header.h
-rwxrwxr-x   1 ouroboros ouroboros  10397 2005-09-04 13:11 softmmu_template.h
-rwxrwxr-x   1 ouroboros ouroboros 153195 2005-09-04 13:11 sparc-dis.c
-rwxrwxr-x   1 ouroboros ouroboros   4097 2005-09-04 13:11 sparc.ld
drwxrwxr-x   4 ouroboros root        4096 2005-11-01 22:20 sparc-softmmu
drwxrwxr-x   3 ouroboros root        4096 2005-11-01 22:20 sparc-user
drwxrwxr-x   3 ouroboros root        4096 2005-09-04 13:11 target-arm
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 target-i386
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 target-mips
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 target-ppc
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 target-sparc
drwxrwxr-x   2 ouroboros root        4096 2005-09-04 13:11 tests
-rwxrwxr-x   1 ouroboros ouroboros  11058 2005-09-04 13:11 texi2pod.pl
-rwxrwxr-x   1 ouroboros ouroboros   7061 2005-09-04 13:11 thunk.c
-rwxrwxr-x   1 ouroboros ouroboros   4108 2005-09-04 13:11 thunk.h
-rwxrwxr-x   1 ouroboros ouroboros   2230 2005-09-04 13:11 TODO
-rwxrwxr-x   1 ouroboros ouroboros   8367 2005-09-04 13:11 translate-all.c
-rwxrwxr-x   1 ouroboros ouroboros   1068 2005-09-04 13:11 translate-op.c
-rwxrwxr-x   1 ouroboros ouroboros      5 2005-09-04 13:11 VERSION
-rwxrwxr-x   1 ouroboros ouroboros  95581 2005-09-04 13:11 vgafont.h
-rwxrwxr-x   1 ouroboros ouroboros 102674 2005-09-04 13:11 vl.c
-rwxrwxr-x   1 ouroboros ouroboros  28184 2005-09-04 13:11 vl.h
-rwxrwxr-x   1 ouroboros ouroboros   6610 2005-09-04 13:11 x86_64.ld
drwxrwxr-x   4 ouroboros root        4096 2005-11-02 11:45 x86_64-softmmu

I'm at my wits end, I did so much already on this. Qemu works with WinXPcorpSP2 without a working kqemu, but it's miserably slow and I'd really like to get kqemu happy with it before going further on tweaking this emulation.

I'm in great hopes someone will help or inform me with this odd one. 

Thanks much in advance!

---

### Post by geearf on 2005-11-02
Last time I tried on an amd64 box it didn't work that well, but I cannot help you though :(

---

### Post by kakashi on 2005-11-02
[QUOTE=scrillamaan]Has anyone tried this with XP, its the only windows disk I have handy at the moment. The QEMU site says its experimental, but been tested on version 0.5.5. No word yet on 0.70 it seems. I've seen Qemu running XP on some fedora forums, but I was wondering if anyone has gotten XP running on Ubuntu?[/QUOTE]

i have winxp working.
i even once managed to start it in safe mode.
it is shit slow. i think your probably better of borrowing a win 95 or 98 cd from a freind who haas it. 
athough i have not yet installed win95 in qemu yet but since a only heard of qemu yesterday and al;ready have a working installation of winxp with kqemu i think i am doing quite well. :razz: 
don't you . **becomes embaressed at self parise

---

### Post by LinuxWiz83 on 2005-11-03
whats the -k en for from mu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda /path/to/your/hd.img -user-net -pci -m 256 -k en because i get this error message (Could not read keymap file: '/usr/share/qemu/keymaps/en') when i keep the -k en on it?

---

### Post by LinuxWiz83 on 2005-11-03
[QUOTE=kakashi]i have winxp working.
i even once managed to start it in safe mode.
it is shit slow. i think your probably better of borrowing a win 95 or 98 cd from a freind who haas it. 
athough i have not yet installed win95 in qemu yet but since a only heard of qemu yesterday and al;ready have a working installation of winxp with kqemu i think i am doing quite well. :razz: 
don't you . **becomes embaressed at self parise[/QUOTE]

Increase the memory size and it won't really be that bad but as of for win98 well that won't work for a lot of people because a lot of people use winxp software and even all the new media on web sites and such won't play on win98 because it uses old codecs.

---

### Post by kakashi on 2005-11-03
[QUOTE=LinuxWiz83]Increase the memory size and it won't really be that bad but as of for win98 well that won't work for a lot of people because a lot of people use winxp software and even all the new media on web sites and such won't play on win98 because it uses old codecs.[/QUOTE]

well i'm trying win 2000 now. 
let you know how fast that is. 
so far not too bad.
will most software work for win200.

as for codec i use mplayer in linux so no worries there.

---

### Post by kakashi on 2005-11-03
i have now installed win 2000 and its much faster than winxp but still sluggish. 
i have only given it 100 mb ram so i guess that what i'll get but still i think 
win98 will be almost perfect.

---

### Post by Lunde on 2005-11-03
100mb is a problem even for 98 if you start a coupple of programs. Why did you set the memory to 100?

---

### Post by Lunde on 2005-11-03
**Warning: could not find /home/ouroboros/qemu-0.7.2/kqemu/.kqemu_[COLOR="Red"]-[/COLOR]_mod.o.cmd **
This file does not exist, may be a typo in the script.
**/home/ouroboros/qemu-0.7.2/kqemu/.kqemu_[COLOR="red"].[/COLOR]_mod.o.cmd **

---

### Post by kakashi on 2005-11-03
[QUOTE=Lunde]100mb is a problem even for 98 if you start a coupple of programs. Why did you set the memory to 100?[/QUOTE]

i only have 256 mb ram and 1 gb swap
how much should i mem should ???

---

### Post by Lunde on 2005-11-03
[QUOTE=kakashi]i only have 256 mb ram and 1 gb swap
how much should i mem should ???[/QUOTE]

Try to start it with 192 and check the sytem monitor in Ubuntu how your system is reacting.

---

### Post by kakashi on 2005-11-03
[QUOTE=Lunde]Try to start it with 192 and check the sytem monitor in Ubuntu how your system is reacting.[/QUOTE]

can i make a seperate swap area ony for this

---

### Post by LinuxWiz83 on 2005-11-03
Well yea that's the problem Win2kPro/WinXP-Pro needs atleast 512 MB to run smoothly but with this emulator i would give it 1 GB of ram if you have it. As for win98 not running smoothly on 100 mb well no because beck in the days all i had was 32 mb and 64 mb and had no problems. Oh another way to speed up Win4Lin Pro is to increase the page file plus give Win4Lin Pro atleast 512MB of your memory.

---

### Post by trinaryouroboros on 2005-11-04
> **Lunde]**Warning: could not find /home/ouroboros/qemu-0.7.2/kqemu/.kqemu_[COLOR="Red"]-[/COLOR]_mod.o.cmd **
This file does not exist, may be a typo in the script.
**/home/ouroboros/qemu-0.7.2/kqemu/.kqemu_[COLOR="red"].[/COLOR]_mod.o.cmd **[/QUOTE]

Wow! Lunde, you are awesome. 

Sometimes it's the stupidest thing, my bad...I've gotten alot further than I did before, but I've had to use a specific method now. I tried to do this in user mode, but I got an error that looks permission orientated:

**Warning: could not open /home/ouroboros/qemu-0.7.2/kqemu/kqemu.mod.c: No such file or directory**

And sure enough the permissions were reset by something, so I tried a few ways with chmod 755 on all files in qemu and kqemu before and after .configure, but I always ended up with that same message...and it's there, the file does certainly exist and no typos this time.

By the way, I just cp'd that typo file with the correct format and it worked fine, passed that part.

Now I went to root, chmod 755'd qemu and kqemu dir's before and after ./configure ---blahblahx86 stuff, and during **make install** I get REAL further, but that message still appears midway during kqemu install this time :

[QUOTE]make[1]: Leaving directory `/home/ouroboros/qemu-0.7.2/x86_64-softmmu'
make -C kqemu
make[1]: Entering directory `/home/ouroboros/qemu-0.7.2/kqemu'
make -C /usr/src/linux-headers-2.6.10-5-amd64-xeon M=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'  CC [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu-linux.o
cp /home/ouroboros/qemu-0.7.2/kqemu/kqemu-mod-x86_64.o /home/ouroboros/qemu-0.7.2/kqemu/kqemu-mod.o
  LD [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu.o
  Building modules, stage 2.
  MODPOST
Warning: could not open /home/ouroboros/qemu-0.7.2/kqemu/kqemu.mod.c: No such file or directory
  CC      /home/ouroboros/qemu-0.7.2/kqemu/kqemu.mod.o
  LD [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'
make[1]: Leaving directory `/home/ouroboros/qemu-0.7.2/kqemu'
mkdir -p "/usr/local/bin"
install -m 755 -s qemu-img "/usr/local/bin"
mkdir -p "/usr/local/share/qemu"
install -m 644 pc-bios/bios.bin pc-bios/vgabios.bin \
                       pc-bios/vgabios-cirrus.bin \
                       pc-bios/ppc_rom.bin pc-bios/video.x \
                       pc-bios/proll.elf \
                       pc-bios/linux_boot.bin "/usr/local/share/qemu"
mkdir -p "/usr/local/share/doc/qemu"
install -m 644 qemu-doc.html  qemu-tech.html "/usr/local/share/doc/qemu"mkdir -p "/usr/local/share/man/man1"
install qemu.1 qemu-img.1 "/usr/local/share/man/man1"
mkdir -p "/usr/local/share/qemu/keymaps"
install -m 644 keymaps/da keymaps/en-gb keymaps/et keymaps/fr keymaps/fr-ch keymaps/is keymaps/lt keymaps/modifiers keymaps/no keymaps/pt-br keymaps/sv keymaps/ar keymaps/de keymaps/en-us keymaps/fi keymaps/fr-be keymaps/hr keymaps/it keymaps/lv keymaps/nl keymaps/pl keymaps/ru keymaps/th keymaps/common keymaps/de-ch keymaps/es keymaps/fo keymaps/fr-ca keymaps/hu keymaps/ja keymaps/mk keymaps/nl-be keymaps/pt keymaps/sl keymaps/tr "/usr/local/share/qemu/keymaps"
for d in x86_64-softmmu said:**
> : Entering directory `/home/ouroboros/qemu-0.7.2/x86_64-softmmu'
install -m 755 -s qemu-system-x86_64 "/usr/local/bin"
make[1]: Leaving directory `/home/ouroboros/qemu-0.7.2/x86_64-softmmu'
cd kqemu ; ./install.sh

There's got to be something simple now at this juncture...I'm in high hopes!

Any further assistance is greatly appreciated in advance!

Thanks,

---

### Post by Lunde on 2005-11-04
I can see that some of the files under your kqemu dir are in the root group, but this file is not. Try to chgrp and then do the chmod again on this specific file
[COLOR="Red"]-rw-r--r-- [/COLOR]1 ouroboros [COLOR="red"]ouroboros[/COLOR] 1582 2005-11-02 11:45 kqemu.mod.c

Strange if this helps, but stranger things has happend :-)


[QUOTE=trinaryouroboros]Wow! Lunde, you are awesome. 

Sometimes it's the stupidest thing, my bad...I've gotten alot further than I did before, but I've had to use a specific method now. I tried to do this in user mode, but I got an error that looks permission orientated:

**Warning: could not open /home/ouroboros/qemu-0.7.2/kqemu/kqemu.mod.c: No such file or directory**

And sure enough the permissions were reset by something, so I tried a few ways with chmod 755 on all files in qemu and kqemu before and after .configure, but I always ended up with that same message...and it's there, the file does certainly exist and no typos this time.

By the way, I just cp'd that typo file with the correct format and it worked fine, passed that part.

Now I went to root, chmod 755'd qemu and kqemu dir's before and after ./configure ---blahblahx86 stuff, and during **make install** I get REAL further, but that message still appears midway during kqemu install this time :



There's got to be something simple now at this juncture...I'm in high hopes!

Any further assistance is greatly appreciated in advance!

Thanks,[/QUOTE]

---

### Post by kakashi on 2005-11-04
does anyone know how i can configure smb shares for win 98. 
i managed to get smb for win 2000 but can't fint how to configure it for win 98

---

### Post by trinaryouroboros on 2005-11-05
[QUOTE=Lunde]I can see that some of the files under your kqemu dir are in the root group, but this file is not. Try to chgrp and then do the chmod again on this specific file
[COLOR="Red"]-rw-r--r-- [/COLOR]1 ouroboros [COLOR="red"]ouroboros[/COLOR] 1582 2005-11-02 11:45 kqemu.mod.c

Strange if this helps, but stranger things has happend :-)[/QUOTE]

   Ughck...it's a hanging deathtrap it is...my head is pounding, I'm going to sleep finally. I tried everything but reformatting and starting the whole silly OS from scratch.

started a brand new source directory, root only.

new commands used this round :

**./configure --target-list=x86_64-softmmu --enable-adlib --cc=gcc-3.4 --host-cc=gcc-3.4**

Now even with this beefcake, I still get the same weird "not found" message as mentioned previous.

Upon make clean from ./kqemu dir, I notice that the file in question gets rm'd ... soooo yeah. The thing gets rm'd, and make doesn't find the file...then somehow magically creates it after the fact it couldn't find the silly .c output module. Bah!

On a whim, I did **touch kqemu/kqemu.mod.c**, plus chgrp/chmod'd it up, and now instead of kqemu.mod.c being "not found" - **make** does : 

> make[1]: Leaving directory `/home/ouroboros/source/qemu-0.7.2/x86_64-softmmu'
make -C kqemu
make[1]: Entering directory `/home/ouroboros/source/qemu-0.7.2/kqemu'
make -C /lib/modules/2.6.10-5-amd64-xeon/build M=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'
  CC [M]  /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu-linux.o
cp /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu-mod-x86_64.o /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu-mod.o
  LD [M]  /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu.o
  Building modules, stage 2.
  MODPOST
Warning: could not open /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu.mod.c: Success
  CC      /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu.mod.o
  LD [M]  /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'
make[1]: Leaving directory `/home/ouroboros/source/qemu-0.7.2/kqemu'

***"Warning: could not open /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu.mod.c: Success"***

What in the nuggets of the backside is it saying "Success" for?!

**Foiled again!**

I tried at some points to force the linux-headers-2.6.10-5-amd64-xeon stuff to stick to gcc-3.4 only...boy was that useless.

I also tried from scratch using chgrp root, and chown 755, chown 777 on the file, etc...g'nite. 

:evil:

---

### Post by Lunde on 2005-11-05
[QUOTE=kakashi]does anyone know how i can configure smb shares for win 98. 
i managed to get smb for win 2000 but can't fint how to configure it for win 98[/QUOTE]

If this is for Qemu, Share the disk from linux, no point sharing anything from the guest OS

---

### Post by Lunde on 2005-11-05
[QUOTE=trinaryouroboros]Ughck...it's a hanging deathtrap it is...my head is pounding, I'm going to sleep finally. I tried everything but reformatting and starting the whole silly OS from scratch.

started a brand new source directory, root only.

new commands used this round :

**./configure --target-list=x86_64-softmmu --enable-adlib --cc=gcc-3.4 --host-cc=gcc-3.4**

Now even with this beefcake, I still get the same weird "not found" message as mentioned previous.

Upon make clean from ./kqemu dir, I notice that the file in question gets rm'd ... soooo yeah. The thing gets rm'd, and make doesn't find the file...then somehow magically creates it after the fact it couldn't find the silly .c output module. Bah!

On a whim, I did **touch kqemu/kqemu.mod.c**, plus chgrp/chmod'd it up, and now instead of kqemu.mod.c being "not found" - **make** does : 



***"Warning: could not open /home/ouroboros/source/qemu-0.7.2/kqemu/kqemu.mod.c: Success"***

What in the nuggets of the backside is it saying "Success" for?!

**Foiled again!**

I tried at some points to force the linux-headers-2.6.10-5-amd64-xeon stuff to stick to gcc-3.4 only...boy was that useless.

I also tried from scratch using chgrp root, and chown 755, chown 777 on the file, etc...g'nite. 

:evil:[/QUOTE]

What user are you running **make** from? Have you tried as root? Can it be that make clean mess up the files and that you need to unpack the files again

I have to add that I never had any such problems, but I never tried the 0.7.2.

---

### Post by LinuxWiz83 on 2005-11-05
[QUOTE=kakashi]does anyone know how i can configure smb shares for win 98. 
i managed to get smb for win 2000 but can't fint how to configure it for win 98[/QUOTE]

Well it is the same setup but the only difference i think is win98 does not support spaces in the shares names.

---

### Post by trinaryouroboros on 2005-11-05
[QUOTE=Lunde]What user are you running **make** from? Have you tried as root? Can it be that make clean mess up the files and that you need to unpack the files again

I have to add that I never had any such problems, but I never tried the 0.7.2.[/QUOTE]

I was running as root only. I've tried unpacking / starting from scratch several times with little success.

I think I'm dropping the project with 0.7.2 and trying just 0.7.0 instead, we'll see what happens - but, I can't seem to find the tars out there. Could someone possibly give me a link or send them via email to theallisone @ gmail.com ?

Much appreciated! :rolleyes:

---

### Post by kakashi on 2005-11-05
[QUOTE=trinaryouroboros]I was running as root only. I've tried unpacking / starting from scratch several times with little success.

I think I'm dropping the project with 0.7.2 and trying just 0.7.0 instead, we'll see what happens - but, I can't seem to find the tars out there. Could someone possibly give me a link or send them via email to theallisone @ gmail.com ?

Much appreciated! :rolleyes:[/QUOTE]
if you have some extra space why not install ubuntu in that space and try there. 
maybe something you have alreay done is effecting your install

---

### Post by trinaryouroboros on 2005-11-05
[QUOTE=kakashi]if you have some extra space why not install ubuntu in that space and try there. 
maybe something you have alreay done is effecting your install[/QUOTE]


Probably...my usual linux space tends to look very similar to my actual space - cluttered, unorganized, and deadly if left alone for too long...

:-k

---

### Post by Lunde on 2005-11-07
[QUOTE=trinaryouroboros]I was running as root only. I've tried unpacking / starting from scratch several times with little success.

I think I'm dropping the project with 0.7.2 and trying just 0.7.0 instead, we'll see what happens - but, I can't seem to find the tars out there. Could someone possibly give me a link or send them via email to theallisone @ gmail.com ?

Much appreciated! :rolleyes:[/QUOTE]
I may have them on one of my disks at home, I'll check this a bit later and upload them to my server if I can find them

---

### Post by trinaryouroboros on 2005-11-07
[QUOTE=Lunde]I may have them on one of my disks at home, I'll check this a bit later and upload them to my server if I can find them[/QUOTE]

That would be awesome. Else, I can give you an ftp account if you so desire.

---

### Post by kakashi on 2005-11-07
[QUOTE=barmaley]Hallo, guys!
1st of all thank you for this great guide.
2nd of all - HEEEEEEEEELP!
I failed to install win2k for a couple of days already and it drives me crazy. I really need windows on my comp to run OriginLab, Shadow ray tracing and sometimes for MS Word and IE.
The problem is that win2k installation goes smoothely up to a point where it says:

"The disk space on C: is insufficient for the components that are currently selected. You  will need to change your component selections".

From this point I don't know what to do. I created an image of 3.5G, should be enough. For installation I use:
qemu -hda win2k.img -cdrom /dev/cdrom -boot d -m 256
After reboot I type 'c' instead of 'd'.
Does anybody know what can be done?
Thank you in advance.[/QUOTE]
```

-win2k-hack 

```
this is the parameter to avoid the disk full error. 
i don;t know if this has been answered since i can't be bottheredto check 
just thougth i'd let you know.

---

### Post by Lunde on 2005-11-08
[QUOTE=trinaryouroboros]That would be awesome. Else, I can give you an ftp account if you so desire.[/QUOTE]
[http://fabrice.bellard.free.fr/qemu/qemu-0.7.0.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.7.0.tar.gz)

..It was just to change the version number at the end

---

### Post by Lunde on 2005-11-08
[QUOTE=kakashi]```

-win2k-hack 

```
this is the parameter to avoid the disk full error. 
i don;t know if this has been answered since i can't be bottheredto check 
just thougth i'd let you know.[/QUOTE]
above quote is is so true.. and in addition to the ansvere from kakashi, I worked around a similar issue by formatting the drive first and have the win installer change it to ntfs.

---

### Post by trinaryouroboros on 2005-11-08
[QUOTE=Lunde][http://fabrice.bellard.free.fr/qemu/qemu-0.7.0.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.7.0.tar.gz)

..It was just to change the version number at the end[/QUOTE]

This is true, but to get kqemu 0.7.0 - this same procedure does not work unfortunately. I was able to get qemu-0.7.0 just fine though, thank you!

Maybe I'll just play around with Win95 under regular qemu in the meantime.

---

### Post by Lunde on 2005-11-08
[QUOTE=trinaryouroboros]This is true, but to get kqemu 0.7.0 - this same procedure does not work unfortunately. I was able to get qemu-0.7.0 just fine though, thank you!

Maybe I'll just play around with Win95 under regular qemu in the meantime.[/QUOTE]
I'm not sure the version number you are trying to download exists. The one I used in this howto is here:
[http://fabrice.bellard.free.fr/qemu/kqemu-0.6.2-1.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-0.6.2-1.tar.gz)

There's also a more resent version, might work but I never tried it:
[http://fabrice.bellard.free.fr/qemu/kqemu-0.7.1-1.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-0.7.1-1.tar.gz)

Changelog:
[http://fabrice.bellard.free.fr/qemu/kqemu-changelog.html](http://fabrice.bellard.free.fr/qemu/kqemu-changelog.html)

---

### Post by trinaryouroboros on 2005-11-13
[QUOTE=Lunde]I'm not sure the version number you are trying to download exists. The one I used in this howto is here:
[http://fabrice.bellard.free.fr/qemu/kqemu-0.6.2-1.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-0.6.2-1.tar.gz)

There's also a more resent version, might work but I never tried it:
[http://fabrice.bellard.free.fr/qemu/kqemu-0.7.1-1.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-0.7.1-1.tar.gz)

Changelog:
[http://fabrice.bellard.free.fr/qemu/kqemu-changelog.html](http://fabrice.bellard.free.fr/qemu/kqemu-changelog.html)[/QUOTE]

Well, in update, I tried kqemu-0.7.1 with qemu-0.7.2, and when it came down to this bother:

>   LD [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu.o
  Building modules, stage 2.
  MODPOST
Warning: could not open /home/ouroboros/qemu-0.7.2/kqemu/kqemu.mod.c: No such file or directory
  CC      /home/ouroboros/qemu-0.7.2/kqemu/kqemu.mod.o
  LD [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'
root@w0-rm-h0-l3:/home/ouroboros/qemu-0.7.2/kqemu #

I decided to copy the kqemu.mod.c that WAS there, as kqemu.mod.c.2 - then make clean erased the kqemu.mod.c as usual...then I renamed kqemu.mod.c.2 to kqemu.mod.c - and make did the following :

> root@w0-rm-h0-l3:/home/ouroboros/qemu-0.7.2/kqemu # make
make -C /usr/src/linux-headers-2.6.10-5-amd64-xeon M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'
  CC [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu-linux.o
cp /home/ouroboros/qemu-0.7.2/kqemu/kqemu-mod-x86_64.o /home/ouroboros/qemu-0.7.2/kqemu/kqemu-mod.o
  LD [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu.o
  Building modules, stage 2.
  MODPOST
  CC      /home/ouroboros/qemu-0.7.2/kqemu/kqemu.mod.o
  LD [M]  /home/ouroboros/qemu-0.7.2/kqemu/kqemu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-xeon'
root@w0-rm-h0-l3:/home/ouroboros/qemu-0.7.2/kqemu #

But, of course, when doing:

> root@w0-rm-h0-l3:/home/ouroboros/qemu-0.7.2/kqemu # modprobe kqemu
FATAL: Error inserting kqemu (/lib/modules/2.6.12-9-amd64-generic/misc/kqemu.ko): Invalid module format

Oh well, you win some you lose some...I'll keep investigating. If I find a palpable solution I will certainly post it here for all to see, we can't live in the 32-bit ages forever you know.

---

### Post by .tommie on 2005-11-14
I've followed the howto, but ran in some trouble when compiling. This is my output when i do 'make':

Could someone point me out what's going wrong? I've tried and tried, but can't find a solution.

```
thomas@Chimay:~/Desktop/qemu-0.7.2$ make
gcc -Wall -O2 -g -fno-strict-aliasing  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o dyngen dyngen.c
dyngen.c: In functie ‘load_object’:
dyngen.c:508: let op: pointer targets in assignment differ in signedness
dyngen.c:544: let op: pointer targets in assignment differ in signedness
gcc -DQEMU_TOOL -Wall -O2 -g -fno-strict-aliasing  -g -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o qemu-img qemu-img.c block.c block-cow.c block-qcow.c aes.c block-vmdk.c block-cloop.c block-dmg.c block-bochs.c block-vpc.c block-vvfat.c -lz
block-cloop.c: In functie ‘cloop_read_block’:
block-cloop.c:116: let op: pointer targets in assignment differ in signedness
block-cloop.c:118: let op: pointer targets in assignment differ in signedness
block-dmg.c: In functie ‘dmg_read_chunk’:
block-dmg.c:231: let op: pointer targets in assignment differ in signedness
block-dmg.c:233: let op: pointer targets in assignment differ in signedness
block-vpc.c: In functie ‘vpc_probe’:
block-vpc.c:84: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
block-vpc.c:84: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
block-vpc.c:84: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
block-vpc.c:84: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
block-vpc.c:84: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
block-vpc.c:84: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
block-vpc.c:84: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
block-vpc.c:84: let op: pointer targets in passing argument 1 of ‘strncmp’ differ in signedness
block-vvfat.c: In functie ‘create_long_filename’:
block-vvfat.c:325: let op: pointer targets in passing argument 1 of ‘short2long_name’ differ in signedness
block-vvfat.c: In functie ‘fat_get’:
block-vvfat.c:393: let op: pointer targets in initialization differ in signedness
block-vvfat.c: In functie ‘long2unix_name’:
block-vvfat.c:446: let op: pointer targets in passing argument 1 of ‘__builtin_strncpy’ differ in signedness
block-vvfat.c:446: let op: pointer targets in passing argument 2 of ‘__builtin_strncpy’ differ in signedness
block-vvfat.c:453: let op: pointer targets in passing argument 1 of ‘__builtin_strncpy’ differ in signedness
block-vvfat.c:453: let op: pointer targets in passing argument 2 of ‘__builtin_strncpy’ differ in signedness
block-vvfat.c: In functie ‘create_short_filename’:
block-vvfat.c:492: let op: pointer targets in passing argument 1 of ‘__builtin_strncpy’ differ in signedness
block-vvfat.c: In functie ‘init_directory’:
block-vvfat.c:719: let op: pointer targets in passing argument 1 of ‘snprintf’ differ in signedness
block-vvfat.c: In functie ‘vvfat_write’:
block-vvfat.c:1620: let op: pointer targets in passing argument 1 of ‘long2unix_name’ differ in signedness
for d in i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu; do \
make -C $d all || exit 1 ; \
        done
make[1]: Entering directory `/home/thomas/Desktop/qemu-0.7.2/i386-user'
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o elfload.o /home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c: In functie ‘load_elf_binary’:
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:948: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:948: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:948: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:948: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:948: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:948: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:948: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:948: let op: pointer targets in passing argument 1 of ‘strncmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:1086: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:1086: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:1086: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:1086: let op: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:1086: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:1086: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:1086: let op: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/elfload.c:1086: let op: pointer targets in passing argument 1 of ‘strncmp’ differ in signedness
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o main.o /home/thomas/Desktop/qemu-0.7.2/linux-user/main.c
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o syscall.o /home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c: In functie ‘do_getsockopt’:
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:647: let op: pointer targets in passing argument 5 of ‘getsockopt’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:680: let op: pointer targets in passing argument 5 of ‘getsockopt’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c: In functie ‘do_syscall’:
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:1750: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:1784: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:1870: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:1871: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2301: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2302: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2303: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2304: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2305: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2306: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2307: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2308: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2309: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2310: let op: pointer targets in passing argument 1 of ‘tswap32s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2630: let op: pointer targets in passing argument 1 of ‘tswap64s’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2934: let op: pointer targets in passing argument 1 of ‘getresuid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2934: let op: pointer targets in passing argument 2 of ‘getresuid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2934: let op: pointer targets in passing argument 3 of ‘getresuid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2954: let op: pointer targets in passing argument 1 of ‘getresgid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2954: let op: pointer targets in passing argument 2 of ‘getresgid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:2954: let op: pointer targets in passing argument 3 of ‘getresgid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:3061: let op: pointer targets in passing argument 1 of ‘getresuid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:3061: let op: pointer targets in passing argument 2 of ‘getresuid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:3061: let op: pointer targets in passing argument 3 of ‘getresuid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:3079: let op: pointer targets in passing argument 1 of ‘getresgid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:3079: let op: pointer targets in passing argument 2 of ‘getresgid’ differ in signedness
/home/thomas/Desktop/qemu-0.7.2/linux-user/syscall.c:3079: let op: pointer targets in passing argument 3 of ‘getresgid’ differ in signedness
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o mmap.o /home/thomas/Desktop/qemu-0.7.2/linux-user/mmap.c
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o signal.o /home/thomas/Desktop/qemu-0.7.2/linux-user/signal.c
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o path.o /home/thomas/Desktop/qemu-0.7.2/linux-user/path.c
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o osdep.o /home/thomas/Desktop/qemu-0.7.2/osdep.c
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o thunk.o /home/thomas/Desktop/qemu-0.7.2/thunk.c
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o vm86.o /home/thomas/Desktop/qemu-0.7.2/linux-user/vm86.c
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o exec.o /home/thomas/Desktop/qemu-0.7.2/exec.c
/home/thomas/Desktop/qemu-0.7.2/exec.c: In functie ‘cpu_set_log’:
/home/thomas/Desktop/qemu-0.7.2/exec.c:1257: let op: pointer targets in passing argument 2 of ‘setvbuf’ differ in signedness
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o kqemu.o /home/thomas/Desktop/qemu-0.7.2/kqemu.c
gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -mpreferred-stack-boundary=2 -falign-functions=0 -fno-gcse -fno-reorder-blocks -fno-optimize-sibling-calls -I. -I/home/thomas/Desktop/qemu-0.7.2/target-i386 -I/home/thomas/Desktop/qemu-0.7.2 -I/home/thomas/Desktop/qemu-0.7.2/linux-user -I/home/thomas/Desktop/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/home/thomas/Desktop/qemu-0.7.2/fpu -I/home/thomas/Desktop/qemu-0.7.2/slirp -c -o op.o /home/thomas/Desktop/qemu-0.7.2/target-i386/op.c
/home/thomas/Desktop/qemu-0.7.2/target-i386/ops_sse.h: In functie ‘op_pshufw_mmx’:
/home/thomas/Desktop/qemu-0.7.2/target-i386/ops_sse.h:574: fout: unable to find a register to spill in class ‘GENERAL_REGS’
/home/thomas/Desktop/qemu-0.7.2/target-i386/ops_sse.h:574: fout: dit is de insn:
(insn:HI 18 17 19 0 /home/thomas/Desktop/qemu-0.7.2/target-i386/ops_sse.h:569 (set (strict_low_part (subreg:HI (reg/v:DI 63 [ r ]) 0))
        (mem/s/j:HI (plus:SI (mult:SI (reg:SI 64)
                    (const_int 2 [0x2]))
                (reg/v/f:SI 59 [ s ])) [0 <variable>._w S2 A16])) 52 {*movstricthi_1} (insn_list:REG_DEP_TRUE 16 (insn_list:REG_DEP_TRUE 12 (insn_list:REG_DEP_TRUE 53 (nil))))
    (expr_list:REG_DEAD (reg:SI 64)
        (nil)))
/home/thomas/Desktop/qemu-0.7.2/target-i386/ops_sse.h:574: in de war door de voorgaande fouten, ik stop ermee
make[1]: *** [op.o] Fout 1
make[1]: Leaving directory `/home/thomas/Desktop/qemu-0.7.2/i386-user'
make: *** [all] Fout 1

```

---

### Post by .tommie on 2005-11-14
Found a solution in another post. Check it out @ [http://www.ubuntuforums.org/showpost.php?p=432781&postcount=5]("http://www.ubuntuforums.org/showpost.php?p=432781&postcount=5")

---

### Post by hyg53 on 2005-11-15
Hum something strange in this method...

What is the point emulate windows like this when you have an install CD. Just insert the CD and install it I it's what you want.

What you only get with this method are problems and slow speed...

Am I wrong?

---

### Post by trinaryouroboros on 2005-11-25
[QUOTE=hyg53]Hum something strange in this method...

What is the point emulate windows like this when you have an install CD. Just insert the CD and install it I it's what you want.

What you only get with this method are problems and slow speed...

Am I wrong?[/QUOTE]

Well, in truth you could make Ubuntu Live, but some of us prefer to do the Permanent install. If everyone on the planet wanted to use Windows and Ubuntu simultaneously, and wanted Windows to own their system, there would only be Live CD's, and no permanent install cd's.

Also, for certain developers Linux is the way to be, and to emulate Windows is sometimes neccessary for software testing purposes...

:KS

---

### Post by Trojan1313 on 2005-11-25
I've been thinking a little. Would it be possible to use this to have webcam conversations with MSN? Or would I need a Linux-supported webcam for that?

I'm guessing the second, but it might atleast be worth a shot. :)

---

### Post by trinaryouroboros on 2005-11-25
[QUOTE=Trojan1313]I've been thinking a little. Would it be possible to use this to have webcam conversations with MSN? Or would I need a Linux-supported webcam for that?

I'm guessing the second, but it might atleast be worth a shot. :)[/QUOTE]

Have a looksie:

[http://amsn.sourceforge.net/]("http://amsn.sourceforge.net/")

They're still working on better webcam support, but it's worth a shot!

:KS 

Also check out this local How-to:
[HOWTO: aMSN 0.95 beta without compiling]("http://ubuntuforums.org/archive/index.php/t-87001.html")

And check this How-to out for general video capture in linux:
[http://www.faqs.org/docs/Linux-mini/BTTV.html]("http://www.faqs.org/docs/Linux-mini/BTTV.html")

---

### Post by trinaryouroboros on 2005-11-25
empty

---

### Post by Trojan1313 on 2005-11-25
[QUOTE=trinaryouroboros]Have a looksie:

[http://amsn.sourceforge.net/]("http://amsn.sourceforge.net/")

They're still working on better webcam support, but it's worth a shot!

:KS 

Also check out this local How-to:
[HOWTO: aMSN 0.95 beta without compiling]("http://ubuntuforums.org/archive/index.php/t-87001.html")

And check this How-to out for general video capture in linux:
[http://www.faqs.org/docs/Linux-mini/BTTV.html]("http://www.faqs.org/docs/Linux-mini/BTTV.html")[/QUOTE]
I've thought about that already, actully. :) Problem is, my cam is four versions to early for support in linux. :p (this is the first model, the fifth has support in Linux)

---

### Post by trinaryouroboros on 2005-11-26
[QUOTE=Trojan1313]I've thought about that already, actully. :) Problem is, my cam is four versions to early for support in linux. :p (this is the first model, the fifth has support in Linux)[/QUOTE]

Foiled! :eek:

---

### Post by Trojan1313 on 2005-11-26
[QUOTE=trinaryouroboros]Foiled! :eek:[/QUOTE]
I'm sorry, what?

---

### Post by trinaryouroboros on 2005-11-26
[QUOTE=Trojan1313]I'm sorry, what?[/QUOTE]

Foiled...as in, "My plans have been Foiled, again."

yeah... :???:

---

### Post by Trojan1313 on 2005-11-26
[QUOTE=trinaryouroboros]Foiled...as in, "My plans have been Foiled, again."

yeah... :???:[/QUOTE]
Ah, okay... I just didn't understand. :)

*rubs hands together and puts on his evil grin*

---

### Post by `GooZ´ on 2005-12-08
Thanks alot for this very clear howto! :-)

---

### Post by dgermann on 2005-12-15
Hi--

I'm stumped. Can you help me?

I have done apt-get install qemu, created the virtual disk, etc.

Now I want to install Win95. The problem seems to be that I have a Win95 CD which is not bootable, and a bootable floppy.

I have tried these things and cannot get Win95 to install:
```
 # qemu -boot a -fda /dev/fd0 -hda /home/doug/qemu/hd.img
 # qemu -boot d -cdrom /dev/hda -hda /home/doug/qemu/hd.img
 # qemu -boot a -fda /dev/fd0 d -cdrom /dev/cdrom0 -hda /home/doug/qemu/hd.img

```

...and half a dozen other things, including trying format c:/s from within the dos window that opens up and shows me all the files on the floppy.

I suspect it is something simple....

I have visited the various websites shown in the howto that starts this thread and there does not seem to be an answer there....

Thanks!

---

### Post by Lunde on 2005-12-16
Try to download a boot disk image from [www.bootdisk.com](www.bootdisk.com), extract the .img file from the .exe (self extracting zip file) with Archive Manager, then refer to this image in your Qemu boot path:

**$ qemu -boot a -fda /path/to/your/bootdisk.img - hda /home/doug/qemu/hd.img**

---

### Post by dgermann on 2005-12-16
Lunde--

Thanks for the quick reply!

[QUOTE=Lunde]Try to download a boot disk image from [www.bootdisk.com](www.bootdisk.com), extract the .img file from the .exe (self extracting zip file) with Archive Manager, then refer to this image in your Qemu boot path:

**$ qemu -boot a -fda /path/to/your/bootdisk.img - hda /home/doug/qemu/hd.img**[/QUOTE]

Archive manager would not open this file. So I executed it in Windows and created a boot disk. Then I did this:> # qemu -boot a -fda /dev/fd0 -hda /home/doug/qemu/hd.img

It got as far as to create an R:\ mapping, which is farther than before, but it then when I try to switch to drive R:\ says "Not ready reading drive R:." Drives C: and D: are invalid drive specs. Yes, the Win95 CD is in the drive.

I tried to pkunzip the image file, got winb95b.IMA which I renamed to winb95b.img, and then used your code on it--it gets to "booting from floppy" and then hangs.

In case it helps, here is the directory of the floppy:
> total 1.3M
drwxr-xr-x  2 root root 7.0K 1969-12-31 18:00 .
drwxr-xr-x  4 root root 4.0K 2005-10-05 20:33 ..
-rwxr-xr-x  1 root root  15K 1996-08-24 11:11 attrib.exe
-rwxr-xr-x  1 root root   45 1999-05-26 16:45 autoexec.bat
-rwxr-xr-x  1 root root  34K 1996-09-26 17:13 cd1.sys
-rwxr-xr-x  1 root root  17K 1996-11-21 01:54 cd2.sys
-rwxr-xr-x  1 root root  20K 1996-08-13 01:03 cd3.sys
-rwxr-xr-x  1 root root  41K 1998-05-11 20:01 cd4.sys
-rwxr-xr-x  1 root root  28K 1996-08-24 11:11 chkdsk.exe
-r-xr-xr-x  1 root root  92K 1996-08-24 11:11 command.com
-rwxr-xr-x  1 root root  377 1999-05-29 12:20 config.sys
-rwxr-xr-x  1 root root  21K 1996-08-24 11:11 debug.exe
-rwxr-xr-x  1 root root  19K 1996-08-24 11:11 deltree.exe
-r-xr-xr-x  1 root root  64K 1996-08-24 11:11 drvspace.bin
-rwxr-xr-x  1 root root  69K 1996-08-24 11:11 edit.com
-rwxr-xr-x  1 root root  46K 1996-08-24 11:11 extract.exe
-rwxr-xr-x  1 root root  62K 1996-08-24 11:11 fdisk.exe
-rwxr-xr-x  1 root root 6.6K 1996-08-24 11:11 find.exe
-rwxr-xr-x  1 root root  49K 1996-08-24 11:11 format.com
-rwxr-xr-x  1 root root  33K 1996-08-24 11:11 himem.sys
-r-xr-xr-x  1 root root 210K 1996-08-24 11:11 io.sys
-rwxr-xr-x  1 root root 9.2K 1996-08-24 11:11 label.exe
-rwxr-xr-x  1 root root  32K 1996-08-24 11:11 mem.exe
-rwxr-xr-x  1 root root  27K 1996-08-24 11:11 move.exe
-rwxr-xr-x  1 root root  25K 1996-08-24 11:11 mscdex.exe
-r-xr-xr-x  1 root root    6 1999-11-17 16:37 msdos.sys
-rwxr-xr-x  1 root root 104K 1996-08-24 11:11 regedit.exe
-rwxr-xr-x  1 root root 140K 1996-08-24 11:11 scandisk.exe
-rwxr-xr-x  1 root root 7.2K 1996-08-24 11:11 scandisk.ini
-rwxr-xr-x  1 root root  19K 1996-08-24 11:11 sys.com
-rwxr-xr-x  1 root root  75K 1996-08-24 11:11 uninstal.exe
-rwxr-xr-x  1 root root  41K 1996-08-24 11:11 xcopy32.exe
-rwxr-xr-x  1 root root 3.8K 1996-08-24 11:11 xcopy.exe


So what am I missing, O guru? <grin>

Thanks, Lunde!

---

### Post by Juzz on 2005-12-16
Did anyone find a resolution to the dependancy hell in Breezy?

```
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.
```

Then:
```
:~/src/qemu-0.7.2$ sudo apt-get install libsdl1.2-dev zlib1g-dev
Reading package lists... Done
Building dependency tree... Done
zlib1g-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages
```
If I then fire up synaptic and try to do some backtracing - it ends with a libgl package that is too new!
If I try to force the Hoary version then synaptic wants to uninstall Ubuntu Desktop and x-window-core :o 

Has anyone released a package for Breezy with kqemu inside?

---

### Post by isitututu on 2005-12-21
I have gone through this whole thread and all posts on the qemu forum and cant' find what I have done wrong. I am running Ubuntu 5, and have installed qemu without the accelerator and win98. All works fine exect that I can't get the samba share to work. I have the following share defined in samba:
[carlos]
	path = /home/carlos
	read only = No

I can access the web server using the url [http://10.0.2.2/](http://10.0.2.2/) and can also ping 10.0.2.2 and am  able to surf the net in win98. Unfortunately the samba share is not accessible.

I use the following command to start win98 with and without samba running:
sudo qemu -boot c -hda /home/carlos/Qemu/hd.img -pci -m 128 -user-net -smb carlos

have also tried with and without samba running:
sudo qemu -boot c -hda /home/carlos/Qemu/hd.img -pci -m 128 -user-net

In win98 I have tried \\10.0.2.2\carlos and \\10.0.2.4\carlos, neither of these work, I always get a cannot find file or item error.

Also I know that the samba share works because I have win2K running on an evaluation copy of vmware and am able to access the share through win2K.

Any help would be appreciated greatly. VMWare is a GREAT piece of software, but a little overkill for what I want, so I do not want to spend the money at this time. Win4lin 9x used to be really good but since they stopped creating win4lin kernels it is beyond my linux abilities to get it working. The pro version is also way to slow even with win2k and acceleration.

---

### Post by Straker on 2005-12-22
I am very interested in this concept as I have been using Win4Lin Home on Hoary but now want to upgrade to Breezy and would like to try this QEMU method.  However, the one issue I have is **can QEMU print from Windows thru to native Ubuntu printers?**

I ask this question, because there is essentially no documentation (web or otherwise) regarding how to print from within QEMU to native devices, and I have had no luck printing from a Linux QEMU session to native Windows printers.

Thanks in advance for any response.

---

### Post by Juzz on 2005-12-22
For those contemplating trying to get qemu or kqemu up and running - I can really recommend you try the vmware player, see this thread for more info:

[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

The vmware player runs extremely good and the speed is blistering compared to qemu :cool:

---

### Post by trinaryouroboros on 2005-12-23
[QUOTE=Juzz]For those contemplating trying to get qemu or kqemu up and running - I can really recommend you try the vmware player, see this thread for more info:

[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

The vmware player runs extremely good and the speed is blistering compared to qemu :cool:[/QUOTE]

Ole!!!

---

### Post by isitututu on 2005-12-31
I solved my problem. When the system is installed the windows image that is created in your home directory is owned by root. I changed ownership to my self. This seemed to have caused the problem. I had to change permissions on the directory so that others could write to the file. Now it all seems to work fine.

Just one comment. Even win98 is slow. I am considering using a litePC product, however the only emulator that I have no problems with so far is VMWare. Probably just worth spending the money. I would NOT recommend win4lin to anyone. I still have not been able to get either 9x or the pro version working properly. 9x is GREAT on a system that has the kernel. My spouse is running Linspire with 9x.

---

### Post by drfalkor on 2006-01-01
[QUOTE=scrillamaan]I can't live without paint!  ;-)[/QUOTE]

Don't worry, take 2 pills, and try out gimp .

---

### Post by valnar on 2006-01-01
[QUOTE=isitututu]I would NOT recommend win4lin to anyone. I still have not been able to get either 9x or the pro version working properly.[/QUOTE]

Sadly, I agree.  Has anyone made Win4lin 9x work on Breezy?

Robert

---

### Post by isitututu on 2006-01-01
[QUOTE=drfalkor]Don't worry, take 2 pills, and try out gimp .[/QUOTE]

I was a paint junkie too. Photoshop and the Gimp are waaay to complex for me. Try Kolorpaint. It is a KDE app but I am running it on Gnome just fine.

---

### Post by sup on 2006-01-07
thanks for the guide. 
I encountered a small problem with compilation. Upon
```
tom@tom:~/Desktop/qemu-0.8.0$ ./configure
```
I got following
```
big/little test failed
ERROR: "gcc" looks like gcc 4.x
QEMU is known to have problems when compiled with gcc 4.x
It is recommended that you use gcc 3.x to build QEMU
To use this compiler anyway, configure with --disable-gcc-check
```
I have got gcc 3.4 installed as well as 4.0,  so it wasnt an issue of installing new packages, but I was kind of at a loss as to how to tell QEMU to use 3.4 version, because 
```
tom@tom:~/Desktop/qemu-0.8.0$ ./configure --help
```
gave me exactly the same result as shown above. It took me some time to figure out only thing I needed was 
```
tom@tom:~/Desktop/qemu-0.8.0$ ./configure --disable-gcc-check --help
``` which started help and I found out that only this simple command is needed: ```
tom@tom:~/Desktop/qemu-0.8.0$ ./configure --cc=gcc-3.4
``` Maybe the first post could be upgraded since this can be a little confusing(at least it was for me)?

---

### Post by Ramses on 2006-01-11
[QUOTE=Straker]I am very interested in this concept as I have been using Win4Lin Home on Hoary but now want to upgrade to Breezy and would like to try this QEMU method.  However, the one issue I have is **can QEMU print from Windows thru to native Ubuntu printers?**

I ask this question, because there is essentially no documentation (web or otherwise) regarding how to print from within QEMU to native devices, and I have had no luck printing from a Linux QEMU session to native Windows printers.

Thanks in advance for any response.[/QUOTE]

I Don't know if it's any help but I managed to get my linux printer to work from qemu running winxp. I am running Qemu 0.72 + KQemu 0.72.
First you need working samba and cups. If you have Samba and cups working, printer will show up when you browse samba share from explorer (in my case \\10.0.2.2. Printer installation did not work stright from printer icon.

You need to go in Windows: start --> settings --> printers and faxes --> add printer --> next --> local printer --next --> create new port --> local port (you should put here the samba printer share (example \\10.0.2.2\lp)) 
It took some time when it was looking for printer. Then it asks you to install drivers for printer. 

This is all written from memory so there may be some flaws.

---

### Post by kenquad on 2006-01-11
Hi all:

I'm running Breezy but still decided to try out the qemu howto listed here, since I have 3 Windows programs I have to run for work.  BTW - and this is probably "news" like the discovery of America in 1492 :cool:  - Nando Florestan has written a shell script for installing qemu with kqemu support, available at the same location: [http://oui.com.br/n/content.php?article.21]("http://oui.com.br/n/content.php?article.21").  I was ready to bite the bullet and type in all the code in the howto, but this script totally bypassed it!  

On to my main point.  Win2000 is running slow.  Atrociously slow.  As in five seconds to open the right-click menu on the desktop.  Will this much slowness be fixable by just tweaking the OS?  And boot parameters I can change?

Also, I can't get on my LAN or net access, which is a must.

I'd appreciate any ideas.

Thanks.

---

### Post by oswald-p on 2006-01-12
This is very interesting indeed...
But I am not a Samba specialist so could you explain how you configure it?
Actually, I can ping 10.0.2.2 but I cannot connect through explorer...
thanks.

O-p

---

### Post by galgoz on 2006-01-12
when I run the command 

```

qemu -boot c -cdrom /dev/cdrom -hda /path/to/your/hd.img -user-net -pci -m 256 -k en

```

I get the following error.

```

qemu: invalid option -- '-user-net'

```

---

### Post by sup on 2006-01-12
galgoz:I got the same mistake, so I just  did not use that option, I think that this howto works well enough (if you of course want to run windows) (scroll down to Sharing Files With XP and Networking) [https://wiki.ubuntu.com/WindowsXPUnderQemuHowTo?highlight=%28qemu%29]("https://wiki.ubuntu.com/WindowsXPUnderQemuHowTo?highlight=%28qemu%29")

oswald-p:oswald:I am not sure, have you got file ssharing in windows enabled (including workgroup), but howto mentioned above should work as well.

kenquad:what is you hardware configuration? Are you sure you are using kqemu?

---

### Post by sup on 2006-01-12
galgoz:I got the same mistake, so I just  did not use that option, I think that this howto works well enough (if you of course want to run windows) (scroll down to Sharing Files With XP and Networking) [https://wiki.ubuntu.com/WindowsXPUnderQemuHowTo?highlight=%28qemu%29]("https://wiki.ubuntu.com/WindowsXPUnderQemuHowTo?highlight=%28qemu%29")

oswald-p:oswald:I am not sure, have you got file ssharing in windows enabled (including workgroup), but howto mentioned above should work as well.

kenquad:what is you hardware configuration? Are you sure you are using kqemu? As to the LAN part, see the howto mentioned above as well, it worked for me.

---

### Post by sup on 2006-01-12
oops

---

### Post by galgoz on 2006-01-12
[QUOTE=Lunde]
2. One option is to use the -m 512 or what ever you want to give the host as memory, Qemu will tell you that you have to raise the shm by:

$ sudo umount /dev/shm
$ sudo mount -t tmpfs -o size=528m none /dev/shm

If you want to do this permanent, set up the mount in /etc/fstab
[/QUOTE]

What do you mean by the last part?  Do you mean change the second line to read... 

$ sudo mount -t tmpfs -o size=528m none /etc/fstab

Then do I need to change the command line or the lines for the bootmisc.sh as well?

---

### Post by DavidGX on 2006-01-15
Hey guys. I want to use windows xp to stream music (via windows media connect) to an xbox 360 I have connect to the network. I installed windows xp into Qemu, network was running, wmc installed on it but the xbox 360 can't see it. This is my setup..

```
                             *internet*
                                 |
                                 |
                            Cable Modem
                                 |
                                 |
                              Router
                            /        \
                           /          \
                          /            \
                        PC           Xbox 360
                         |
                       Linux
                         |
                    Windows xp
```
 

Is there any way to configure networking so that the windows xp installed into qemu will see the 360?

---

### Post by kakashi on 2006-01-15
theres a tutorial around here concerning qemu and bridge networking. use that.

---

### Post by galgoz on 2006-01-16
When I am running Windows and it crashes (imagine that) my mouse will not work in Ubuntu.  I assume because I didn't get to hit alt-ctrl before it crashed to release the Grab.  Is there a way to get my mouse back without rebooting?

---

### Post by oswald-p on 2006-01-17
Thanks Sup, I installed qemu 7.2 + Kqemu 7.2 as described above... it seems to work well except for file sharing / printing...
My distro is Ubuntu 5.10

I can browse web, ping 10.0.2.2 but I can't share files (user-net option activated).

I shared a directory with samba and it seems to work as I can connect to it via external computer on our network. I used "-smb" option to run qemu that run win98SE where I gave the same user/password as my ubuntu box (juste to be sure....)

Does anybody have any idea?

thanks 

O-p

---

### Post by galgoz on 2006-01-17
[QUOTE=Lunde]Originally Posted by Lunde
2. One option is to use the -m 512 or what ever you want to give the host as memory, Qemu will tell you that you have to raise the shm by:

$ sudo umount /dev/shm
$ sudo mount -t tmpfs -o size=528m none /dev/shm

If you want to do this permanent, set up the mount in /etc/fstab
[/QUOTE]

[QUOTE=galgoz]
What do you mean by the last part?  Do you mean change the second line to read... 

$ sudo mount -t tmpfs -o size=528m none /etc/fstab

Then do I need to change the command line or the lines for the bootmisc.sh as well?[/QUOTE]

Still looking for an answer as to how to do this permanently.   Anyone know?

---

### Post by galgoz on 2006-01-24
[QUOTE=c4pp4]
after command [COLOR=Blue]checkinstall[/COLOR] next error
[COLOR=Red]dpkg-deb: subprocess paste killed by signal (Broken pipe)[/COLOR]
[/QUOTE]

I get this same error.  Is there a solution to this as I would like to be able to install qemu if I want later

---

### Post by trinaryouroboros on 2006-01-26
Sorry, I sort of gave up since I couldnt' get kqemu working properly.

I do recall the error once however, I think it had something to do with the version of the compiler. Go back in history and ensure you have the older version.

---

### Post by galgoz on 2006-01-26
I actually won't be using Qemu anymore.  I now have my Dreamweaver 8 and Flash 8 working in Cedega!  Yea, Windowz is gone.

---

### Post by trinaryouroboros on 2006-01-27
[QUOTE=galgoz]I actually won't be using Qemu anymore.  I now have my Dreamweaver 8 and Flash 8 working in Cedega!  Yea, Windowz is gone.[/QUOTE]

Get outta here, you got a working link to a guide or something on that?

---

### Post by galgoz on 2006-01-27
I am actually now an Advocate on Cedaga for Dreamweaver 8 and will be writing something up for the site as long as they approve the method that is required.  If you want to IM me I can give you the quick quick version.

---

### Post by yetanothersteve on 2006-01-29
Ridiculously easy way to to set up Qemu and KQemu on Hoary.

[http://oui.com.br/n/content.php?article.23]("http://oui.com.br/n/content.php?article.23")

I made a change to the script because I wanted Qemu 0.8.0.

KQemu turns it from a dog into something reasonable on my Athlon 3000 with 1Gb RAM.

---

### Post by xurizaemon on 2006-02-27
kQemu really does make a difference, yes.

Tonight i decided i was bored of having no gTalk client on my linux box, and needed to get my audio working in either of the qEmu windozes i had set up.

To get it going in the win98, tried adding the option "-soundhw sb16", which detected the card when ran the add new hardware wiz, but then bluescreened on boot. So restarted qemu with "-soundhw es1370" instead and that worked a treat (had to d/l drivers though as i didn't have the correct 98 cd handy, haven't seen it since doing the install, whoops!)

The XP (home) install just needed me to start it with "-soundhw es1370". I didn't try -audio-hw sb16 because 1370 worked better on win98. Once it booted it detected a new audio device and went straight to work.

Amazingly, in 98 the sound started straight away - as i installed the drivers i heard the speakers pop into life. and let me check ... Yep. I can get sound from Amarok in Linux, AND from Win98 (in qEmu) AND from XP all at once. (XP just went 'ding' in the background to tell me it's finished d/l gTalk).

Wow. I wouldn't expect this of Windows normally! Haha, running XP and 98 on an Athlon XP 2800. Typing this in FFOx on the 98 'machine'. Crazy stuff.

Thanks Ubuntu! Thanks qEmu! And ... heh ... thanks Microsoft too!

:mrgreen:

Now on to test how well it copes with gTalk yakker ... hehe

---

### Post by clackey on 2006-03-09
I'm having problems installing Qemu with KQemu in Dapper...
Everything works fine up until I needed to install. First, I tried using 

**sudo checkinstall**

which generated a package called  qemu_0.8.0-1_i386.deb.
Then, I did

**sudo dpkg -i qemu_0.8.0-1_i386.deb**

...which gave me this:

```
~/qemu-0.8.0$ sudo dpkg -i qemu_0.8.0-1_i386.deb
(Reading database ... 160124 files and directories currently installed.)
Unpacking qemu (from qemu_0.8.0-1_i386.deb) ...
dpkg: error processing qemu_0.8.0-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.15-17-386/modules.alias', which is also in package linux-image-2.6.15-17-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 qemu_0.8.0-1_i386.deb
```

So then I tried 

**sudo make install**

...that seemed to work fine; no errors. On to the next step:

**sudo modprobe kqemu**

...oops:

```
~/qemu-0.8.0$ sudo modprobe kqemu
FATAL: Error inserting kqemu (/lib/modules/2.6.15-17-386/misc/kqemu.ko): Invalid module format
```

I couldn't figure out what was wrong, so I tried to go ahead with the rest of the HOWTO... it worked, except I noticed that Qemu was unable to run KQemu (said something about /dev/kqemu in the terminal while Qemu was running; I forget exactly what, though).

Although Qemu itself runs fine, I'm trying to run XP under it; and without KQemu, it's painfully slow. I'm willing to bet this has something to do with the fact that I'm using Dapper, or the kernel version i'm using (uname -r gives me 2.6.15-17-386), or both. Can anyone help?

Thanks,
Clackey

---

### Post by trinaryouroboros on 2006-03-10
[QUOTE=clackey]I'm having problems installing Qemu with KQemu in Dapper...
Everything works fine up until I needed to install. First, I tried using 

**sudo checkinstall**

which generated a package called  qemu_0.8.0-1_i386.deb.
Then, I did

**sudo dpkg -i qemu_0.8.0-1_i386.deb**

...which gave me this:

```
~/qemu-0.8.0$ sudo dpkg -i qemu_0.8.0-1_i386.deb
(Reading database ... 160124 files and directories currently installed.)
Unpacking qemu (from qemu_0.8.0-1_i386.deb) ...
dpkg: error processing qemu_0.8.0-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.15-17-386/modules.alias', which is also in package linux-image-2.6.15-17-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 qemu_0.8.0-1_i386.deb
```

So then I tried 

**sudo make install**

...that seemed to work fine; no errors. On to the next step:

**sudo modprobe kqemu**

...oops:

```
~/qemu-0.8.0$ sudo modprobe kqemu
FATAL: Error inserting kqemu (/lib/modules/2.6.15-17-386/misc/kqemu.ko): Invalid module format
```

I couldn't figure out what was wrong, so I tried to go ahead with the rest of the HOWTO... it worked, except I noticed that Qemu was unable to run KQemu (said something about /dev/kqemu in the terminal while Qemu was running; I forget exactly what, though).

Although Qemu itself runs fine, I'm trying to run XP under it; and without KQemu, it's painfully slow. I'm willing to bet this has something to do with the fact that I'm using Dapper, or the kernel version i'm using (uname -r gives me 2.6.15-17-386), or both. Can anyone help?

Thanks,
Clackey[/QUOTE]

Please rewind, I had the same exact problem w/ no workaround to date.

It's a very intriguing problem. Fair warning, however, don't lose too much hair like I did with this one.

I thought it might have something to do with my 64-bit processor, at least I'm glad to know it's not the family of the cpu that matters in regards to this trouble. If you do discover a fix, please let us know, I've been fighting with that kqemu for a long time now.

---

### Post by clackey on 2006-03-10
Hmm... I read over the Nando Florestan article, and it said this:

> So the last step is to load the kqemu kernel module:

  modprobe kqemu


What if this command does not work, saying this?

  FATAL: Error inserting kqemu (/lib/modules/2.6.10-2-386/misc/kqemu.ko): Invalid module format


This means you did something wrong when compiling. For instance, the headers used during compilation are for a different kernel than the one you are actually using. You can run a "make clean" to wipe the compiled files and restart from the "./configure" step, doing something different this time.

...Now, I know I used the right headers for my kernel, however, I did read on a thread somewhere someone mentioning that in order for it to work, you have to have compiled your kernel with the same gcc version as qemu (or it could have been some other program that had the same module error). I'll try to find that thread and post it here.

Also, check this out: [http://www.mepis.org/node/9277]("http://www.mepis.org/node/9277")

It's a post by someone using Mepis who had the same problem; with a reply by someone with an apparent workaround. I might try it out.

Clackey

---

### Post by clackey on 2006-03-10
The solution in the Mepis post seems to work!

> Found the solution.

Steps I Took That Worked
Make sure to have the following line in /etc/apt/sources.list:
deb [http://apt.mepis.org/3.4/](http://apt.mepis.org/3.4/) etch main
Then, as root:
# apt-get update
# apt-get install linux-headers-2.6.15-1-586tsc
# ln -sf /usr/src/linux-headers-2.6.15-1-586tsc /usr/src/linux
# apt-get install gcc-3.3 g++-3.3 libsdl1.2debian libsdl1.2debian-all build-essential libsdl1.2-dev zlib1g-dev
# ln -sf /usr/bin/gcc-3.3 /usr/bin/gcc
# wget -nv [http://fabrice.bellard.free.fr/qemu/qemu-0.8.0.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.0.tar.gz)
# tar zxvf qemu-*.tar.gz
# cd qemu-*
# wget -nv [http://fabrice.bellard.free.fr/qemu/kqemu-0.7.2.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-0.7.2.tar.gz)
# tar zxvf kqemu-*.tar.gz
# export CPP=g++-3.3
# export CC=gcc-3.3
# sh ./configure --prefix=/usr --cc=gcc-3.3 --host-cc=gcc-3.3 --kernel-path=/usr/src/linux
# rm /usr/bin/gcc
# ln -sf /usr/bin/gcc-3.3 /usr/bin/gcc
# make
# rm /usr/bin/gcc
# ln -sf /usr/bin/gcc-4.0 /usr/bin/gcc
# cd kqemu
# make clean
# make
# cd ..
# make install

...I just changed the kernel version to my own, skipped this

**# ln -sf /usr/src/linux-headers-2.6.15-1-586tsc /usr/src/linux**

changed **--kernel-path=/usr/src/linux** to **--kernel-path=/usr/src/linux-headers-2.6.15-17-386**

and that was that!

The reason why it wasn't working was exactly like I had mentioned; kqemu was compiled along with qemu using gcc-3.3, while the kernel was compiled with gcc-4.0, causing a conflict... using this fix recompiles kqemu after qemu using gcc-4.0 so it can work with the kernel.

However, I still wasn't able to use checkinstall without a "modules.alias" error, so I just used make install; which worked just fine.

Hope this can fix it for you too trinaryouroboros!

Clackey

---

### Post by trinaryouroboros on 2006-03-11
[QUOTE=clackey]The solution in the Mepis post seems to work!



...I just changed the kernel version to my own, skipped this

**# ln -sf /usr/src/linux-headers-2.6.15-1-586tsc /usr/src/linux**

changed **--kernel-path=/usr/src/linux** to **--kernel-path=/usr/src/linux-headers-2.6.15-17-386**

and that was that!

The reason why it wasn't working was exactly like I had mentioned; kqemu was compiled along with qemu using gcc-3.3, while the kernel was compiled with gcc-4.0, causing a conflict... using this fix recompiles kqemu after qemu using gcc-4.0 so it can work with the kernel.

However, I still wasn't able to use checkinstall without a "modules.alias" error, so I just used make install; which worked just fine.

Hope this can fix it for you too trinaryouroboros!

Clackey[/QUOTE]

Jesus! I'm freaking excited! I can't believe it's true, finally there's a real solution out there that works?!

My weekend already rocks, holy freakin cow! :mrgreen: 

I'm trying this as soon as I get home! I had almost lost all hope on this!


\\:D/    WOOHOOOO!

---

### Post by ruscook on 2006-03-16
I've tried Nando's script and get the following output from my attempt on my Dapper install. Anyone know why make is failing with a segementation error ?


InsQEMU - version 0.1 (2005-12-15)
======= by Nando Florestan -- [http://oui.com.br/n](http://oui.com.br/n)
This script downloads and installs QEMU 0.8.0,
with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger.
Based on:
[http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation](http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation)

If this script succeeds, you will see a message at the end saying:
"InsQEMU SUCCEEDED!"
...else you have some problem.

If you have any difficulties, you can edit the script yourself.
It is heavily commented so as to help.
Please send any bug corrections to [email]nandoflorestan@gmail.com[/email]

First of all, we install the dependencies.
Reading package lists...
Building dependency tree...
gcc-3.4 is already the newest version.
g++-3.4 is already the newest version.
libsdl1.2debian is already the newest version.
libsdl1.2debian-all is already the newest version.
build-essential is already the newest version.
libsdl1.2-dev is already the newest version.
zlib1g-dev is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Finding out whether your kernel is i386 or i686.
Downloading Linux headers for K7...
Reading package lists...
Building dependency tree...
linux-headers-k7 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


Directory already exists: /root/qemu-src/qemu-0.8.0
I will use its files instead of downloading them from the internet.
BEGINNING CONFIGURE !
Install prefix    /usr
BIOS directory    /usr/share/qemu
binary directory  /usr/bin
Manual directory  /usr/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /root/qemu-src/qemu-0.8.0
C compiler        gcc-3.4
Host C compiler   gcc-3.4
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user mips-user mipsel-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu arm-softmmu
gprof enabled     no
static build      no
SDL support       yes
SDL static link   no
mingw32 support   no
Adlib support     no
CoreAudio support no
ALSA support      no
DSound support    no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers-2.6.15-8-k7/
kbuild type       2.6


BUILDING QEMU !
for d in i386-user arm-user armeb-user sparc-user ppc-user mips-user mipsel-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu arm-softmmu; do \
	make -C $d all || exit 1 ; \
        done
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/i386-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/i386-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/arm-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/arm-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/armeb-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/armeb-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/sparc-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/sparc-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/ppc-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/ppc-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/mips-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/mips-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/mipsel-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/mipsel-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/i386-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/i386-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/ppc-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/ppc-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/sparc-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/sparc-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/x86_64-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/x86_64-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/mips-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/mips-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/arm-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/arm-softmmu'
make -C kqemu
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/kqemu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/kqemu'

Now let us remove Qemu if it is installed...
Reading package lists...
Building dependency tree...
Package qemu is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



Installing with "make install"...

========================= Installation results ===========================
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.

Copying documentation directory...
/var/tmp/dfJLDOUimkZmjrDqKiaM/installscript.sh: line 13: 21034 Segmentation fault      mkdir -p "/usr/share/doc/qemu"
for d in i386-user arm-user armeb-user sparc-user ppc-user mips-user mipsel-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu arm-softmmu; do \
	make -C $d all || exit 1 ; \
        done
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/i386-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/i386-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/arm-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/arm-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/armeb-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/armeb-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/sparc-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/sparc-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/ppc-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/ppc-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/mips-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/mips-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/mipsel-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/mipsel-user'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/i386-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/i386-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/ppc-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/ppc-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/sparc-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/sparc-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/x86_64-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/x86_64-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/mips-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/mips-softmmu'
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/arm-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/arm-softmmu'
make -C kqemu
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/kqemu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/kqemu'
mkdir -p "/usr/bin"
make: *** [install] Segmentation fault

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

---

### Post by mrjohnston on 2006-03-18
I have fixed the insQEMU script so it works with dapper.  I did make a couple other changes like making it recognize k7 headers and I fixed the gcc issues.  Let me know if you have any problems.

Maybe later if I get adventurous I'll try to make a cvs script for qemu as well.

Just untar and run the script below as you normally would to get working qemu + kqemu patch.

---

### Post by trinaryouroboros on 2006-03-20
[QUOTE=mrjohnston]I have fixed the insQEMU script so it works with dapper.  I did make a couple other changes like making it recognize k7 headers and I fixed the gcc issues.  Let me know if you have any problems.

Maybe later if I get adventurous I'll try to make a cvs script for qemu as well.

Just untar and run the script below as you normally would to get working qemu + kqemu patch.[/QUOTE]

Dude, you rock!

:mrgreen:

---

### Post by Schrollini on 2006-03-28
Thanks to everyone who has posted in this thread, I can now run Win98 inside of qemu, which is very handy for tax software.

I did have trouble with Samba, so I thought I would share how I got it (mostly) working.  I found [this thread]("http://qemu.dad-answers.com/viewtopic.php?p=1934&sid=4785304a4f9888063c11763f5acdecf2") (which was referenced, but not linked to, from here) rather enlightening.

There seem to be two methods to get Samba working. The first is to note that the client OS sees the host OS running at 10.0.2.2 . Thus, if you already have Samba up and running, you should be able to access it at this address. I was unable to get this working under Windows 98, but this was my first time playing with Samba, so I may have screwed something up server-side.

The other method is to pass the -smb <directory> switch to qemu. This starts up a "fake" Samba server that client can access at 10.0.2.4 . After much confusion and frustration, here's what I finally got to work:[LIST=1]
[*]Install the "samba" package.
[*]Turn off the "Folder sharing service (samba)" via System | Adminstration | Services. This isn't necessary, but I didn't need it running.
[*]Start qemu with ```
sudo qemu <options> -smb /full/path/to/shared/directory
``` I could only get it to work if I used an absolute path to the shared directory.
[*]After Windows boots, add the line ```
10.0.2.4 smbserver
``` to the file C:\Windows\Lmhosts (at least in Win98. The qemu man page suggests that this should work for Win95 and ME as well, while the NT / 2000 branch should do this in C:\WINNT\SYSTEM32\DRIVERS\ETC\LMHOSTS) **Important:** Make sure you are acutally editting Lmhosts. My install had a file named Lmhosts.sam, which with hidden file extensions appeared in Explorer as Lmhosts. I spent the better part of an hour editting it, to no avail.
[*]You might have to reboot Windows at this point.  I don't remember if it was necessary for me or not.
[*]Now, you should be able to access the shared directory by entering "\\smbserver\qemu" into the location bar of Explorer.
[*] (Optional) Right click "Network Neighborhood" and select "Map Network Drive". Accept the drive letter and enter "\\smbserver\qemu" as the path. Click the box to "Reconnect at login". Now, the shared folder is accessible through a network drive, which will automatically be set up each time you log in. (Maybe. It is Windows.)[/LIST]
Outstanding issues:[LIST]
[*]I can't use IP addresses to access the share in Windows; \\10.0.2.4\qemu doesn't work. I suspect this is a limitation in Windows.
[*]I have to start qemu with sudo, otherwise Windows complains that it can't connect to the host. This doesn't seem necessary, but I haven't found a way around it.
[*]If you want to write to the shared directory from Windows, it must have 777 permissions. This has security implications, I'm sure.
[*]Along the same lines, files created in Windows in the share are owned by "nobody/nogroup". There ought to be a way to have them owned by the user who launched qemu, but I have no clue where to start looking to fix this.[/LIST]
I hope this saves somebody a bit of work!

---

### Post by Schrollini on 2006-03-28
[quote=tombeharrell]An excellent how-to, many thanks. I have now got Qemu installed and into it I have installed Win XP Pro. It all seems to work fine, however the XP box's clock runs way too fast affecting things that are animated etc. Has anybody else experienced this?

When the machine is idling and drops to 600MHz a minute in the XP window takes about 19 seconds. With some load so the host runs at 1.5GHz, the minute takes about 10 seconds. Is there anyway of having it sync to the local clock properly? 
[/quote] 
I've seen the same problem on my setup (Athlon 3500, Ubuntu 5.10, Windows 98 ). When the computer is idling, the clock speed seems right, but it rushes by whenever the CPU throttles up. I haven't found a fix.

A note to other Win9x users: These systems don't idle properly, and continue to use CPU cycles all of the time, as noted in the [qemu user documentation]("http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC34").  Installing the patch linked to on that page seems to work.  (Now the clock only races occasionally....)

---

### Post by bernardfrancois on 2006-04-06
Wow, this is a very long thread :) I didn't read everything yet (but I searched on the topics I'm asking questions about).

I tried to compile it with the accelerator, but it didn't work. The modprobe command returned something like 'kqemu not found'. I will try it again later, and I'll read the instructions that came with the source.

[edit]
I managed to make it work now. Probably there's something unclear in the howto.
What I did to compile/install qemu 0.8.0 + qemu accelerator 1.3.0pre5:

```

#get the path of the linux headers, for example /usr/src/linux-headers-2.6.12-10-amd64-generic (explained in the howto)

#edit quemu-0.8.0/configure; kernel_path="" -> kernel_path="/usr/src/linux-headers-2.6.12-10-amd64-generic"

ber@linber:qemu-0.8.0$ ./configure --cc=gcc-3.4

ber@linber:qemu-0.8.0$ make

ber@linber:qemu-0.8.0$ sudo checkinstall

	#don't do the following step if you have an i386 architecture

	Enter a number to change any of them or press ENTER to continue: 7
	Enter the architecture type: 
	>> amd64

#edit kqemu-1.3.0pre5/configure; kernel_path="" -> kernel_path="/usr/src/linux-headers-2.6.12-10-amd64-generic

ber@linber:kqemu-1.3.0pre5$ ./configure

ber@linber:kqemu-1.3.0pre5$ make

ber@linber:kqemu-1.3.0pre5$ sudo checkinstall
	#failed

ber@linber:kqemu-1.3.0pre5$ sudo make install

```

Note that the installation of the accelerator using checkinstall failed.
[/edit]

[QUOTE=sup]
I found out that only this simple command is needed: ```
tom@tom:~/Desktop/qemu-0.8.0$ ./configure --cc=gcc-3.4
``` Maybe the first post could be upgraded since this can be a little confusing(at least it was for me)?[/QUOTE]

I also suggest the above to be added to the howto. This was also necessary here.

For now, I tried the version from synaptic (without native execution of machine instructions). It took a long time to install windows XP.
Now I can't log on. If I try to log on, I get a warning (translated): '*Due to a problem, Windows can't accurately translate the license for this computer. Error code: 0x800703e6*'. After clicking the OK-button, I get logged of and I see the screen where you can pick a user again (I attached a screenshot).

It is a legal version of Windows XP Professional. The key was accepted during the installation. It's the first time I install it (my school has a contract with M$, every student in the course I'm taking can download a legal version of windows and get a legal key).

---

### Post by bernardfrancois on 2006-04-06
About the command to boot an image as suggested in the howto:
[list]
[*]The **-k** option is obsolete if you use Linux and if you want to use the keyboard layout you use in Linux.
[*]the **-user net** option is obsolete (this is the default setting).
[*]the **-kernel-kqemu** option should be added (this works if the accelerator works) to make it 2-5x faster.
[/list]
I found this information in the manual pages of qemu version 0.8.0 

A **problem**:
The QEMU Accelerator needs QEMU >= 0.8.1 . 
However, the current version of QEMU is 0.8.0 (downloadable [here](http://fabrice.bellard.free.fr/qemu/download.html)). I want to download version 0.8.1 or newer from CVS, but I can't find more information on the site on how to do this.

Can anyone help me with this?

---

### Post by Burgresso on 2006-04-06
Stupid question, but...

Will/does work on 6.04 Breezy? Anyone tried it?

---

### Post by bernardfrancois on 2006-04-06
[QUOTE=Burgresso]Stupid question, but...
Will/does work on 6.04 Breezy? Anyone tried it?[/QUOTE]

6.04 = dapper
breezy = 5.10

There's a script (few posts higher) to install it on Ubuntu 6.04 

It works on any linux kernel 2.4.18 or higher.

These are the requirements:

```

host      gcc      binutils      glibc    linux   
-----------------------------------------------------
x86       3.2      2.13.2        2.1.3    2.4.18

```

---

### Post by Burgresso on 2006-04-06
thanks!

---

### Post by bernardfrancois on 2006-04-10
[QUOTE=bernardfrancois]
Now I can't log on. If I try to log on, I get a warning (translated): '*Due to a problem, Windows can't accurately translate the license for this computer. Error code: 0x800703e6*'. After clicking the OK-button, I get logged of and I see the screen where you can pick a user again (I attached a screenshot).[/QUOTE]

I think I had this error because I changed the amount of ram (passed with the command line) after the installation of windows. I also changed the version of qemu I was using.
I think windows won't work anymore after the hardware settings changed... If this is true, this is something to be added to the howto as well.

---

### Post by jalyst on 2006-04-11
[QUOTE=mrjohnston]I have fixed the insQEMU script so it works with dapper.  I did make a couple other changes like making it recognize k7 headers and I fixed the gcc issues.  Let me know if you have any problems.

Maybe later if I get adventurous I'll try to make a cvs script for qemu as well.

Just untar and run the script below as you normally would to get working qemu + kqemu patch.[/QUOTE]

Dont spose you could write it to grab the latest CVS, and while you're at it, compile for A64?

Wishful thinking??!!? :D 

-jedL.

---

### Post by wwitthoff1 on 2006-04-11
question for you.  I am trying to install win 98 and it uses a floppy to boot the cd.  the floppy works fine but it says that it can't find the cd.  Any ideas?

---

### Post by jalyst on 2006-04-11
no idea sorry  :-(

---

### Post by wwitthoff1 on 2006-04-12
i found how to boot but now cannot install as i get the error "cannot create temp directory"  any ideas?

---

### Post by bernardfrancois on 2006-04-12
maybe it thinks the disk is full...

you could try the following option:
```
-win2k-hack     use it when installing Windows 2000 to avoid a disk full bug
```

---

### Post by wwitthoff1 on 2006-04-12
would that work for 98 as well?     and where does it go in the command.   I am using the command:

$qemu -boot d -cdrom /home/bassclarinetl2/New_Compilation.iso -hda /home/bassclarinetl2/Qemu/hd.img

---

### Post by wwitthoff1 on 2006-04-12
found answer to previous post.  tried win2k hack but no dice.  same error:

"Cannot create a temporary directory.  This may be caused by too many files in the root directory"

any ideas?

BTW   The actuall "Pressed" install CD is not bootable and came with a floppy disk.  I created a bootable CD with the contents of the Pressed cd on it.

---

### Post by monicams on 2006-04-27
.

---

### Post by Doctor DEA on 2006-09-15
Im really new to Linux/Ubuntu...  Every single tutorial I come across in reguards to Linux, you people start gloating in knowledge and failing to break things down, and explaining things to make them more simple for us noobs....  LINUX TUTORIALS ARE PUTTING A BAD TASTE IN MY MOUTH....  In other words, you need tutorials for your tutorials.

Tried to run a simple resize for formatting to dual boot the Hard Drive with Win. and Ubuntu.  
Its always nice when your thinkpad freezes during this.

I really want to sway from the big overtaker, but finding it to be very difficult to learn your O.S.  Ive had to restrain myself from launching my computer through the wall in the past with UBUNTU....

---

### Post by xurizaemon on 2006-09-15
Don't put all nerds in the same basket, DEA. Some of us do know how to talk human tongues. And the ones who talk gibberish, they might sound holier-than-thou (as a rule of thumb, the more evangelical and holier they sound, the more recent the convert) but they probably really do want to help you*.

And, if you've ever had to debug an error message like this one from Outlook: 
> 51 messages couldn’t be retrieved from the server. This usually happens when the connection to the server is lost due to network problems. Contact your administrator. Download error 0×80040403.
which translates from MCSESpeke into:
> 51 messages couldn't be downloaded because of a filesystem limitation in FAT32 (dude, you have a 2GB mailbox). But ... saying so would be bad marketing, so here's a red herring and a secret hexidecimal clue to spend your day chasing.
you'll know that while O.S.S geeks sometimes talk nonsense with the best of intentions, the commercial geeks sometimes get paid to write stuff that is flat-out deliberately confusing ;)

[http://glo.dyndns.org/glob/2006/08/30/0x80040403-argh/](http://glo.dyndns.org/glob/2006/08/30/0x80040403-argh/)

So ... you say your ThinkPad freezes during Ubuntu install?

[http://www.ubuntuforums.org/archive/index.php/t-222077.html](http://www.ubuntuforums.org/archive/index.php/t-222077.html)

This thread seems to suggest that the gPartEd Live CD does the trick (resizing an XP - NTFS partition) when the Ubuntu Live CD doesn't.

If this works for you, you might want to a bug to LaunchPad saying "Live CD doesn't correctly resize NTFS but gPartEd does" and give the full details of what did and didn't work, including your laptop specs - that might help someone fix the bug that's tripping you up.

Good luck!

* (OK, Some users from all camps are just idiots. No OS can protect against its users being fools. Can't be helped.)

---

### Post by Doctor DEA on 2006-09-15
Ok,

I was pretty aggrevated when I wrote that.  Thank you for responding in kindness.  O:) 

IBM ThinkPad R51 Model 1836:  Intel(R)Pentium(R)M
                              Processor 1.70GHz 1.70Ghz,
                              768MB of RAM HardDrive 55.89GB
                              81% free space.
  

Goal Has Changed To:   To get Suse 10.1 with gnome + XGL to run along with current OS.  Or Ubuntu 5.10 with XGL.
Why:  So I can utilize the tools I know to help further my knowledge into linux without the hassel of dual booting.  And because it's cool as hell!  
:rolleyes:

Current Status:  VMware Workstation installed on current OS with 20GB allocated for SUSE.

Question:  Am I going about this the correct way, or should it be vise versa with my base OS.  In other words, should I make Linux my core OS to run VMware Workstation on? And then install "The Others" OS onto VMware? I would have no problem with doing this, but fear that alot of drivers for my thinkpad will be lost.  

Thanks for your help, this is what ill be doing for the remainder of my night until the morning... :biggrin:    ](*,)

---

### Post by jmfv on 2007-05-06
A very good free and opensource alternative to using qemu is VirtualBox.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I've tried it and now I'm running WinXP flawlessly inside linux, with native emulation speed. 
Cheers.

---

### Post by roimam on 2007-06-18
[FONT="Verdana"][COLOR="DarkGreen"]Ok this is my goal... I already have Ubuntu installed but I need to install windows XP too, then I don't want to delete my Ubuntu.  I want to have both Ubuntu and windows.  Can anybody tell me how to do it?

Thanks everybody.[/COLOR][/FONT]

---

### Post by s_p_a_r_k_y on 2007-06-24
hey, the easiest way to achieve this is by formatting the computer to have an NTFS partition and install windows there first, then install ubuntu onto another empty partition and have its bootloader allow you to boot to both OSes

---

### Post by ares623 on 2007-12-24
hello.
i'm having trouble with this step
**$ gedit configure**
where is this **configure** file located? I tried editing the configure file in the extracted qemu directory, but it has no line that says "kernel_path=..."

---

