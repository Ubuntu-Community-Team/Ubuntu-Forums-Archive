---
title: "Ubuntu Quick-Guide (for n00bs) [moved?]"
date: 2007-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by xthund3rh3adx on 2007-06-09
[CENTER]**MetallicaMaster3's guide to installing Ubuntu!**[/CENTER]
PS, i am Metallicamaster3 on SD...

This is my guide on how to install ubuntu on a partioned Hard Drive or another Hard Drive.

First, you will need the ubuntu LiveCD, available here>> 
[Download Ubuntu | Ubuntu](http://www.ubuntu.com/getubuntu/download)

get the version that best fits your computer and your needs. 

Here we will emphasize on Ubuntu 7.04 Feisty Fawn 

Once you download the ubuntu LiveCD (it will take a while, even with a fast Internet Connection), You need to write it to a CD.
You will need a peice of software that can write ISOs, such as Nero or ISO Recorder. Simply copying it to a Disk through Windows is a no go, since the ISO will only be a file on the Disk. The ISO needs to be uncompressed and layed out onto the disk using a ISO recorder. This creates a bootable LiveCD. 

Once the CD is made, you need to restart your computer.
When the BIOS splash screen appears, you need to go into a Boot Menu, or edit the sequence that the Computer boots from.
If you have a Boot Menu, simply select to boot from your optical drive. 
Or, if you do not, you need to go into your BIOS and change the boot sequence. Find where this is, every BIOS is probably different. 
Change it accordingly in this order-

1.) (your optical drive)
2.) Hard Drive
3.) Network boot
4.) (whatever is left)

Then, exit and save changes. The computer will reboot.

When the computer restarts, then The CD will automatically Boot.

Give it 5 minutes, and you will be up and running. On the desktop, you will see an installation shortcut. Double Click, and wait about 30 seconds to a minute until you get to a select option in the Window. Choice one of these choices

Use free disk space (has a slider to edit percentage)
Manually edit partion table.

Manually Edit Parion Table


if you choose this ( you probably should ), you could do the following:
If you are partioning your hard drive, or if you are completely reformatting your drive for Ubuntu, then you will do the following-

If you want to delete everything on the disk and use it for ubuntu, then you will need to delete the entire drive (WARNING, YOU WILL LOSE EVERYTHING!), and then select "New", and reformat it to ext3.

If you want to create a new partion, then select the drive you want to install it on, and click "new". Then, create the amount of space you want the partion to be. 

Then, click next. Make sure you have it set so that whatever you want to install Ubuntu on is selected to do so.



The installation of GRUB and Ubuntu will now begin. 
This shouldnt take too long.

Once the installation process is done, then shut down your computer, and eject the LiveCD. 
-------------------------------------------



Start up your computer.
You will see a new Menu caled "GRUB". It lists 3 Ubuntu entrys, and then any other OSs you might have. 

The default selection is Ubuntu, and the default time is 30 seconds. 
You can change this easily. 

Boot into Ubuntu, and log in.

[CENTER]
CHANGE DEFAULT SELECTED OS in GRUB[/CENTER]

open up terminal, and enter this:

```

sudo gedit /boot/grub/menu.lst

```
Find this line 

```

default     0

```

Replace with the following line 

```

default     (number of entry)

```


***replace "(number of entry)" with the number of the OS you want to be the default. Count downwards.....be aware that "Other Operating systems" counts as an OS entry.

0 is the first entry. 1 is the second entry, and so on. REMEMBER THIS!

Save the edited file 

If you want to change the amount of time there is before the default OS is loaded, then find the 

```

 timeout 10line and replace "10" with the amount of seconds you want.

```

When your done screwing around with GRUB, then reboot, and you should see your changes take effect.

Of course, you can always skip this step if you dont mind the defualt settings (recommended for beginners)

As a side note, I think it&#8217;s important to mention that, if you do manage to completely mess up your grub.conf [or menu.ls] file to the point that your machine won&#8217;t boot, you can fix it by booting into a livecd (like the Ubuntu livecd or Knoppix or DSL or something), and then copying your backup grub.conf [or menu.ls] over while in there. In fact, this method is great whenever you do something to your system that makes it temporarily unusable.

Microsoft Virtual PC is not compatible with ubuntu.


[CENTER]removing Ubuntu[/CENTER]

if you ever want to get rid of ubuntu, its quite easy.
First, you will need a windows xp installation CD. 
Boot into that. 
Go to "repair" by pressing the key when told to do so.
Type 

```

 C:\FIXMBR

```

this repairs the master boot record, and removes GRUB. Windows will automatically boot now when you start the computer. 

Be prepared to see a Disk Consistancy check. do not be alarmed, Windows is actually doing something right . 

Just because GRUB is gone, doesnt mean you got rid of ubuntu either. you need to empty the partion/hard drive. 

Boot up the Ubuntu LiveCD. go into a terminal and enter 

```

 sudo gparted

```

FInd the partion with ubuntu on it, and delete it. Reformat it to NTFS or FAT32 if it was on a seperate drive. Then hit Next. Ubuntu will be gone and you will be back to your old XP setup once more  





[CENTER]Installing Google Earth[/CENTER]
How to install Google Earth



```

wget -c http://dl.google.com/earth/GE4/GoogleEarthLinux.bin

```
```

sudo sh GoogleEarthLinux.bin

```
* Leave /usr/local/google-earth as the installation path
* After installation click Exit. If you instead chose to run the application, read the Note below. 


```

 sudo cp /opt/google-earth/googleearth.desktop /usr/share/applications/

```
* Applications -> Internet -> Google Earth 

* Note: If you run Google Earth for the first time from the installer, it will require root privileges to run the next time. To fix that: 


```

sudo chmod 777 -R ~/.googleearth

```

[CENTER]Widescreen Monitors[/CENTER]

[B]I do not recommend to use a modeline which is not made for your screen so if you want to use a modeline create your own, a wrong modeline might in some case damage your screen.
Here are some modeline generators you can use to create your own modeline :
[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)
[http://sh.nu/nvidia/gtf.php](http://sh.nu/nvidia/gtf.php)
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
[http://koala.ilog.fr/cgi-bin/nph-colas-modelines](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)
[/B]

* 24/23" widescreen monitors have issues running 1920x1200 resolution
to fix this, open terminal and enter:

```

sudo gedit /etc/X11/xorg.conf
[code]
* Add the following line to the appropriate "Monitor" section 


[code]
Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235

```
configure your resolution now and you should see a 1920x1200 option.

[CENTER]Mounting NTFS[/CENTER]
Open up terminal, and enter this:


```

sudo apt-get install ntfs-3g

```
* Create the local mount folder and edit the fstab file to mount the disks to this folder. 

(Assumong /dev/hda1 is the location of Windows partition [NTFS] )
Local mount folder: /media/windows 
then, enter this in terminal:

```

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```
Add the following line at the end of file. 


```

/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0

```
* You can adjust your locale. Execute 'locale -a' in a terminal to know which one are supported by your system. 

* Save the edited file. 

* If you reboot now, the disk will be writable to every user. If you want the changes to take effect immediately without rebooting, execute the following command, ignoring the errors about "/" and others not being unmounted. 


```

sudo umount -a && sudo mount -a

```
[CENTER]Bluetooth[/CENTER]

to get bluetooth support, enter this in Terminal.

```

sudo aptitude install bluez-utils gnome-bluetooth

```
* Open Applications -> Accessories -> Bluetooth file sharing
* You're now able to receive files from other Bluetooth-devices
* To send a file: find a file to send, right click and choose "Send to", wait until the other device is detected, and click "send". 

To see if your Bluetooth-device is supported check here 


If you dont like the GRUB Menu...

if your like some people, not only you uses the computer. This can be a hassle with GRUB with people saying "what the hell is this?!" and cause a panic in your household (especially if they arent computer savvy like you ). So, if you want to hide the GRUB Menu, look below. Be aware that you cannot make a selection other than the default since you cannot see it 

anyway, here it is:


In terminal:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

```
Find this line 

```

#hiddenmenu

```
Replace with the following: 


```

hiddenmenu

```
Save the new edited file

---

### Post by frodon on 2007-06-11
Nice guide.

I have a quick note to add, i do not recommend to use a modeline which is not made for your screen so if you want to use a modeline create your own, a wrong modeline might in some case damage your screen. 
Here are some modeline generators you can use to create your own modeline :
[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)
[http://sh.nu/nvidia/gtf.php](http://sh.nu/nvidia/gtf.php)
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
[http://koala.ilog.fr/cgi-bin/nph-colas-modelines](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)

---

### Post by xthund3rh3adx on 2007-06-11
Thank you, frodon, its great to know my work is appreciated! ^_^

I have heard the modeline problem before, i think i might edit in a disclaimier. Thank you!

---

### Post by xthund3rh3adx on 2007-06-12
For what its worth, head on over to [http://mysillypc.com/ubuntu](http://mysillypc.com/ubuntu) or [http://ubuntu.mysillypc.com](http://ubuntu.mysillypc.com).

I just opened it up with servers from a site that i am a staff member of. Its like UbuntuForums, but strictly for help, support, and Linux related discussions....well so is this.......but you get my point

---

### Post by durand on 2007-06-15
Thanks, very noob friendly, lol

---

### Post by ziaziu on 2007-12-10
Unfortunately the links are dead :(

---

### Post by spai on 2007-12-10
> **ziaziu said:**
> Unfortunately the links are dead :(

Really?
All links work for me except [http://koala.ilog.fr/cgi-bin/nph-colas-modelines](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)

---

