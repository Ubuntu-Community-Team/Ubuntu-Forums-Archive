---
title: "Qemu with KQemu accelerator and Win4LinPro in Hoary"
date: 2005-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Lunde on 2005-05-31
[SIZE=4]**Qemu with KQemu accelerator and Win4LinPro in Hoary**[/SIZE]

..I have made a complete howto for running Windows on Qemu with KQemu. If you are not specifically intrested in trying Win4LinPro, I suggest you try this first. Unlike Win4LinPro, the Qemu and KQemu accelerator is completly free, and from my experience it's even a better solution.

You can find this Howto here: [http://www.ubuntuforums.org/showthread.php?p=200357#post200357](http://www.ubuntuforums.org/showthread.php?p=200357#post200357) 


READ THIS!!! Before you start installing Win4LinPro[/B]
I don't know if I did something wrong, I hope I did.. because.. this is bad!!! 

*The performance is so horrible that I don't understand how they have the gutz to charge for it.

*The installation support and documentation from Win4LinPro is very poor, I spent 1 hour on the net trying to find out how to start it in full screen and did'nt find out. It's not the same as in earlier WIn4Lin

*Be sure (If you're not a guru in hacking) that you need a bootable CD of win2000 or XP sp1 or sp2. WIn98 /95/ millenium / home edition will not work in Win4LinPro.

OK.. Let's start...


[SIZE=3]**step 1. RUNNING QEMU WITH KQEMU ACCELERATOR To boost performence of win4lin** [/SIZE]
(It helps, insted of taking 20sec to open a window, it's down to 10sec).

This information is mostly ripped from: Nano Florestan (which should have most of the credit) at [http://oui.com.br/n/content.php?article.21](http://oui.com.br/n/content.php?article.21) 

I will mostly just write the commands here:


First we need to remove Qemu and compile it with Kqemu

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

You now need to make sure you have some extra packets. First make sure you have the kernel headers installed by: 

**$  uname -a **
..this will output the kernal version

Open Synaptic package manager and search for packages called "linux-headers". Several packages start with this name. Install the one that corresponds to your processor and your kernel version.

Still in Synaptic, choose the package you have just installed, click Properties and go to the "Installed Files" tab. Write down the directory where the files were copied. In my case, they were copied to:  /usr/src/linux-headers-2.6.10-5-386/

**$ gedit configure**

change the: kernel_path="/usr/src/linux-headers-2.6.10-5-386" 

**$ sudo apt-get install libsdl1.2-dev**
**$ sudo apt-get install zlib1g-dev**

Then check that everything is correct with:

**$ ./configure**

If everything is correct, proceed with:

**$ make**

Correct output to make will go on and on and output a lot of text...

If you did'nt get any errors you are now ready to install. If you get any errors or this does'nt work at all, make sure you have a gcc compiler in your system.

Now we are ready to install:

**$ sudo make install **

If everything went ok, you can now start the qemu with the command

**$ modprobe kqemu**

Then we need to make this start when the computer boots

**$ sudo gedit /etc/init.d/bootmisc.sh**

Add these lines to the end just before "exit;"

[B]# Start Qemu with KQemu accelerator
/sbin/modprobe kqemu
mknod /dev/kqemu c 250 0  # Create the KQEMU device 
chmod 666 /dev/kqemu      # Make it accessible to all users[/B]


[SIZE=3]**Step 2. INSTALLING WIN4LINPRO**[/SIZE]

Go to: [http://www.win4lin.com/index.php?option=com_remository&Itemid=76&func=fileinfo&parent=category&filecatid=2](http://www.win4lin.com/index.php?option=com_remository&Itemid=76&func=fileinfo&parent=category&filecatid=2) 

Download the .deb packet and install with:

**$sudo dpkg -i win4linpro_6.1.1-03_i386.deb**

There we go, now you are ready to install win2000 or XP... this you do with the command:

**$ loadwinproCD**

This will load the installation cd into your disk before installation. Do this as your user, not root or sudo. If you want to use a .iso you specify this with:    

**loadwinproCD -r /location/of/your/file.iso**

After the CD or .iso is loaded into your drive you start the installation process by:

**$ installwinpro**

Still as your user.. not root or sudo

For more configuration go to the User-guide at: [http://www.netraverse.com/support/docs/pro6_guide.html](http://www.netraverse.com/support/docs/pro6_guide.html) 


Congratulations.. or more like good luck! I really wish that you can figure out why it's stilll so slow and can reply here how you did it.

---

### Post by bhima on 2005-05-31
I have installed Windows XP SP 2 home edition on Win4LinPro.
Despite kqemu enabled, the guest sessions are slow.
I have an unsolved issue with my keyboard which goes on default "English -US" . I have a french keyboard.
Adding MRGPRO_KB_LANG="fr" in Edit/etc/default/mergepro does not solve my problem.
119 $ or euros for Win4LinPro is quite expensive : 
Installation of programs are sometimes hasardous, the windows session just disappears.
For the moment, i prefer a dual boot till things get a bit better ...

---

### Post by Lunde on 2005-05-31
They say they have a fix for keybord layout in the latest release. 

I stopped it before i even tested my keyboard. Clicked on the start button and started internet explorer, 2-3 hours installation and that's it. I have been trying to find out if it's possible to configure it so it goes faster, but hav'nt found anything yet, They should'nt sell anything that is not good enough for even beta testing, or at least warn people about it. 

VMware workstation is much better for heavy OS's like winXP, I am / was runnung win2000 pro in vmware and it's kinda OK, but... fullscreen has a refresh rate at 65 htz (Horrible to look at) and semi fullscreen runs slower. 
For some reason after I moved my system to another disk it's crashing with my Nvidia drivers I think. Screen is locking and I have to hard reboot my PC.
 
...anyway VMware are much better then Win4LinPro, almost fast enough. lack of grafic-performance, but good for Office, Dreamwaver and I used some Photoshop.

---

### Post by kakashi on 2005-11-02
installing winxp in qemu is not a very good idea. it seems.
i hav installed xp already and its sooooooooooooooo slowwwwwwwwwwwwwwwwww
with kqemu 
i like most everyother old windwos user have a copy of windows 98 lying aorund or with a freind. is it faster if so then i'll give that a go. 
thanks

---

### Post by Lunde on 2005-11-03
[QUOTE=kakashi]installing winxp in qemu is not a very good idea. it seems.
i hav installed xp already and its sooooooooooooooo slowwwwwwwwwwwwwwwwww
with kqemu 
i like most everyother old windwos user have a copy of windows 98 lying aorund or with a freind. is it faster if so then i'll give that a go. 
thanks[/QUOTE]

There is a problem with 98 and kqemu, it simply crashes so you have to turn  kqemu off. Win2000 is a good choice (May be a 98 fix now, don't know) 

[http://www.ubuntuforums.org/showthre...357#post200357](http://www.ubuntuforums.org/showthre...357#post200357)

---

