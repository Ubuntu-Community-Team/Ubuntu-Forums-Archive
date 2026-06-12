---
title: "HOWTO : LVM gui (Not EVMS)"
date: 2006-07-14
forum: Outdated Tutorials &amp; Tips
---

### Post by crazymonkey on 2006-07-14
This guide will show you how to install the Logical Volume Management gui from Fedora Core 8 rpm on your Ubuntu desktop. I prefer this gui over evmsgui because its alot more user friendly and gives you good information about your drives/volumes.

Before you begin here are some general note on LVM:
-For your system to work entirely on LVM you have to make a install using the **alternate** installation CD which will give you the option to install using LVM.

-If you have installed Ubuntu using LVM and you want to resize you root partition (or any system partition) you will have to boot using the Desktop live-cd and run the gui from there. You can grab both files attached to this post that contains everything needed to install and run system-config-lvm in a livecd session. Just extract the content, put it in the same folder as the .deb and run lvmgui-livecd-install.sh to get everything up and running.

[CENTER]
[COLOR="Red"][SIZE="4"]****WARNING****[/SIZE]
The GUI applies all settings instantly. Always be sure of what you do and double check before doing it. Its really easy to intialise the wrong drive and lose hours of work.](*,) [/COLOR][/CENTER]

First of all we want to get the alien package to convert the rpm package to a .deb :

```
sudo apt-get install alien
```

Then we need the system-config-lvm rpm package from Fedora :

```
 wget download.fedora.redhat.com/pub/fedora/linux/releases/8/Everything/i386/os/Packages/system-config-lvm-1.1.1-2.0.fc8.noarch.rpm
```

Next we will convert the .rpm package to .deb package (you will see alot of warning, you can ignore them) :

```
sudo alien system-config-lvm-1.1.1-2.0.fc8.noarch.rpm
``` 


Now we want to install our new deb package :
*For some reason alien changes the version number from 1.1.1-2 to 1.1.1-3 when creating the package
```
sudo dpkg -i system-config-lvm_1.1.1-3_all.deb
```


system-config-lvm needs the python interpreter and looks for it under the name /usr/bin/python2 but on Ubuntu 8.04 python is named /usr/bin/python2.5 so you need to create a link to python2.5 and name it python2

```
sudo ln -s /usr/bin/python2.5 /usr/bin/python2
```


Now if everything is alright you can start system-config-lvm (with sudo) and start managing your volumes.
```
sudo system-config-lvm &
```

On a final note here are the instruction to make the shortcut "Logical Volume Management" under System -> Administration work and lauch system-config-lvm properly.

1- Go to System -> Preference -> Main Menu
2- Find the "Logical Volume Management" and right click on it and open properties.
3- Change the command field to this: gksu system-config-lvm
4- Close everything and use your brand new shortcut!

[CENTER]
[COLOR="Red"][SIZE="4"]****WARNING****[/SIZE]
The GUI applies all settings instantly. Always be sure of what you do and double check before doing it. Its really easy to intialise the wrong drive and lose hours of work.](*,) [/COLOR][/CENTER]

I hope this guide will help you.

EDIT: Changed system-config-lvm version from 1.0.18-1.2.FC5 to 1.1.1-2.0.FC8 and updated the whole guide to reflect this change, I also removed/updated the parts for Dapper to Hardy. I also added instruction to make the menu shortcut work and general notes on LVM.

---

### Post by barret on 2006-07-15
I like this a lot more than the LVM GUI on freshmeat. Thanks for the useful howto!

---

### Post by mvanzante on 2006-07-23
Just a suggestion because I'm a noob, but couldn't you use a symbolic link instead of copying the python files over. I used the following command, which worked wonderfully:
```

ln -s /usr/bin/python2.4 /usr/bin/python2
```

---

### Post by zetman on 2006-08-06
I want reudce the size of my root partition.  Will I need to reduce the size of my file system first, or will the gui take care of that?

---

### Post by jaffamuffin on 2006-08-06
I want to know this too.  I Performed a default install with Ubuntu with LVM and I want to put mythtv on(which is better setup over mulitple partitions), but use LVM and different filesystems.

Can I just use this tool to change set the disk up, and sort the filesystems out?

---

### Post by crazymonkey on 2006-08-26
> **zetman said:**
> I want reudce the size of my root partition.  Will I need to reduce the size of my file system first, or will the gui take care of that?

First of all sorry for the late reply, i had problem with my internet the night i posted this HOWTO and tought it didnt make it to the forums...

If you installed ubuntu using the alternate install CD and chose to use LVM partition you can easily resize your root partition with this tool. Just select your Ubuntu volume group and select your root partition under the logical view and press the Edit Properties button.

This will open a new window (see screenshot) with your root partition properties. There you can change the size of your partition and free some space to assign to a new partition. On the screenshot it shows the size in extents but you can change it to KB,MB or GB too.

[IMG]http://ubuntuforums.org/gallery/data/500/Screenshot69.png[/IMG]

---

### Post by johnhedge on 2006-09-13
This was so much easier than EVMS which I just couldn't get to work! I now have a great partition spread over 3 hard drives.

Great 'Howto'.

One ? though. Where's the launch icon in the menu?

---

### Post by crazymonkey on 2006-09-20
> **johnhedge said:**
> This was so much easier than EVMS which I just couldn't get to work! I now have a great partition spread over 3 hard drives.

Great 'Howto'.

One ? though. Where's the launch icon in the menu?

The launch icon is added automatically in the others section. You will have to change the launcher to ```
gksu system-config-lvm
``` before using it.

---

### Post by dernwine on 2006-10-09
Thanks for the awesome info - 
I've had system-config-lvm working fine with Gnome Ubuntu, however when I try the same steps with kde based kubuntu, I'm getting the following response. I did some searching and the best I can come up with is it has something to do with python (duh) but other than that, am at a loss... Any ideas?

@groucho:~$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 50, in ?
    from Volume_Tab_View import Volume_Tab_View
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 13, in ?
    from Properties_Renderer import Properties_Renderer
  File "/usr/share/system-config-lvm/Properties_Renderer.py", line 33, in ?
    import gnome
ImportError: No module named gnome

---

### Post by jdong on 2006-10-09
You probably need the gnome python bindings. Pull in gnome-app-install or alacarte or gdebi or some other gnome python app and that'll probably be your brain-dead simple way of getting any possible gnome dependencies... it's excessive but simple, just the way I like abusing modern-day hard drives and processors :)

---

### Post by dernwine on 2006-10-10
That did it. Thank you!

---

### Post by johnhedge on 2006-10-15
and it works on edgy as well.

---

### Post by Schammy on 2006-11-13
I'm having some trouble getting this to work.  I'm a noob at this and hopefully someone is still paying attention to this post.

I followed the instructions from my default terminal promopt and all seemed to go OK.  The problem starts when I try to launch the LVM manager.  I have a menu item in Application > Other > Logical Volume Management.  When I click on it, I get this error message:

[IMG]http://static.flickr.com/111/296930922_31c6d01855.jpg?v=0[/IMG]

As the message indicates, apparently I don't have the right file in the right directory.  How do I make sure it gets installed in the right directory?  Where did I go wrong? ](*,) 

Thanks in advance.

---

### Post by crazymonkey on 2006-11-14
The shortcut in the Others menu wont work because it does not use the gksu prefix to execute as root. You can change this in the menu editor (just add gksu before the command). gksu is the gnome equivalent of sudo. You can also try to run it from the terminal with the following command : sudo system-config-lvm

Let me know if it wont work from the terminal either.

---

### Post by Schammy on 2006-11-14
crazymonkey, you're pure genius!  I was able to run in gnome with "gksu system-config-lvm" and the terminal with "sudo system-config-lvm".  Then I found the Alacarte Menu Editor and modified the command that gnome uses to launch the program so I can now launch it from the Other menu.

I'm so happy to have this running.  I've always thought that easy LVM configuration was the biggest downfall of Ubuntu - now I have it.

Thanks again.

---

### Post by kalahari875 on 2006-11-21
Install python-gnome2. That seemed to do the trick.

---

### Post by vangos on 2006-12-05
I was successful installing Ubuntu Edgy (with Beryl !!!!) on a LVM spanning two physical disks. This has been very time consuming as it required multiple attempts for different reasons. Anyway because my setup is not exactly very secure, I installed the LVM gui and when I attempted to take a snapshot to save on a separate drive, I get this error message:
[COLOR="RoyalBlue"]
The dm-snapshot module is either not loaded in your kernel, or your kernel does not support the dm-snapshot target. If it is supported, try running "modprobe dm-snapshot". Otherwise, creation of snapshots is unavailable.
[/COLOR]
I tried to find help on the forum relative to that and even modprobe loaded the dm-snapshot module, but keep getting the same message. My kernel is 2.6.17-10-generic (i686).

Anybody has any idea if this is even possible to do. I would hate to have to go through the same ordeal...

Thank you

Evangelos

---

### Post by jdong on 2006-12-05
Can you create LVM snapshots from the command line using lvcreate? It might just be a GUI bug.

---

### Post by vangos on 2006-12-05
I will try it (although I am not experienced at all with LVM).


Evangelos

---

### Post by lime4x4 on 2006-12-05
heres the error i'm getting on edgy

john@john-edgy:/tmp$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 138, in ?
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 123, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 56, in __init__
    locking_type = self.model_factory.get_locking_type()
  File "/usr/share/system-config-lvm/lvm_model.py", line 998, in get_locking_type
    conf = open('/etc/lvm/lvm.conf')
IOError: [Errno 2] No such file or directory: '/etc/lvm/lvm.conf'
john@john-edgy:/tmp$ 


any ideas?

---

### Post by jdong on 2006-12-05
I have no idea if system-config-lvm will work with Edgy's LVM setup.

---

### Post by vangos on 2006-12-06
It is working for me. But I do have that problem with the snapshot. I think I read somewhere that it might be a problem with the LVM2. Who knows...

Evangelos

---

### Post by racmar on 2006-12-08
dude **crazymonkey**

"I love you man!"

This is something I've wanted to do ever since I first saw system-config-lvm on a centos machine.

-Thanks!

---

### Post by bodhi.zazen on 2006-12-13
Nice How-to

This thread has been added to the UDSF wiki.

[LVM_gui](http://doc.gwos.org/index.php/LVM_gui)

---

### Post by click4851 on 2007-01-30
first off thanks for the howto, it seems to have installed just fine. I say seems because all 3 of my drives show up but are uninitalized. My 80gig main drive in gparted shows:

/dev/hda1  73.44 gig  ext3           /boot
/dev/hda2   2.89 gig   extended    lba
/dev/hda5   2.89 gig   unknown

my 20gig winxp ntfs drive I assumed would be uninitialized.

and my 160 gig future main drive is currently just one big ext3 partition.

I've always assumed Ubuntu defaulted to lvm on install, but if I was currrently using lvm wouldn't my main drive be initialized already. I guess I am starting to question whether my drive appears setup for lvm or classic partition, but I don't see the classic partitions like swap, home, etc. If i'm using lvm, do I need to initialize the drive to have the system-config-gui see it and adjust/edit.

---

### Post by click4851 on 2007-01-30
I think I have my answer:

thomas@tihome2:~$ di
Filesystem         Mount               Megs     Used       Avail      %Used   fs Type
/dev/hda1          /                    74021.8  26955.6  43306.1  41%     ext3   
udev                 /dev                  10.0      0.2               9.8   2%      tmpfs  
devshm             /dev/shm           505.7      0.0         505.7   0%        tmpfs  
lrm                   /lib/modules/2.   505.7    17.7         488.0   4%        tmpfs  
procbususb       /proc/bus/usb     10.0     0.2               9.8   2%        usbfs  
varlock             /var/lock          505.7      0.0            505.7   0%        tmpfs  
varrun              /var/run           505.7      0.1            505.6   0%        tmpfs  
thomas@tihome2:~$ 

from what I've read, under file system type if any lvm volume were created they would be listed as such.

---

### Post by crazymonkey on 2007-02-06
The default installation doesnt use LVM, you have to use the alternate CD to use LVM and select format all drive using LVM when asked to partition.  Take note that you can still use LVM on new drives even if you didnt install ubuntu on LVM.

Also take note that i have noticed that sometime system-config-lvm can detect a drive that is actually using LVM as an unitialized entity so always double check in your volume groups before initializing a drive.

You lvm drives will always show up in /dev as /dev/nameofvolumegroup/nameoflogicalvolume
So if you installed using LVM your root logical volume would be /dev/Ubuntu/root
Ubuntu being the VG and root the LV

I hope this helps clear things up.

---

### Post by theorem_hunter on 2007-03-10
how can i create a snapshot of my root partition?

i get this error so, i take it i need to free up sum extents... (ill try use the gui...)

dimitri@OuZo:~$ sudo lvcreate -L592M -s -n rootBackup /dev/ursus250/lvRoot
  Incorrect metadata area header checksum
  Insufficient free extents (0) in volume group ursus250: 148 required

---

### Post by theorem_hunter on 2007-03-10
ok i freed up a gig & it worked...

dimitri@OuZo:~$ sudo lvcreate -L592M -s -n rootBackup /dev/ursus250/lvRoot
  Incorrect metadata area header checksum
  Logical volume "rootBackup" created

i restarted the gui & found the rootBackup... but how would i restore it?

thanks :) >>> this is a great how-to :)

---

### Post by theorem_hunter on 2007-03-10
i freed up 10G to use for snapshots

dimitri@OuZo:~$ sudo lvcreate -L10G -s -n rootBackup /dev/ursus250/lvRoot 
  Incorrect metadata area header checksum
  Logical volume "rootBackup" created

but is there a way to create the snapshot with out specifying the size, shot that it just determines what has changed in root & then makes a snapshot the size of the change?

---

### Post by gtr225 on 2007-03-28
Hey thanks for the guide, it really helped me out. But I'm still having trouble I hope someone can help me with. I currently have two 60GB hdd's setup as my root logical volume and I would like to add a 100GB hdd to the mix. I've successfully created a physical volume on the extra drive and added it to the volume group but the problem is when I try to extend the logical volume. No matter what I try I can't seem to umount "/", even when I try booting from a CD. Any help would be greatly appreciated.

---

### Post by crazymonkey on 2007-03-31
The problem is that you can't unmount / (root) because you are using it. One way to solve this is to boot from ubuntu livecd and follow the instructions to install and run system-config-lvm on the livecd session. From there you should be able to expand the root partition without problems. I have done this several times without any problems. 

If you plan on doing this often I suggest you to use [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") which is a nice tool that allow you to rebuild the ubuntu livecd and add custom packages.

---

### Post by gtr225 on 2007-03-31
I tried booting from the live cd earlier (before your reply) and my problem was the lack of LVM support on it. I'll try rebuilding the live cd with LVM support. I don't mind using the command line to fix my LVM it was just being able to do it with my root partition unmounted. Thanks for the help, this just may solve like a month of frustration I've been having.

---

### Post by gtr225 on 2007-03-31
I booted up from the Ubuntu 6.10 Desktop CD and followed the instructions and got the following error```
ubuntu@ubuntu:~$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 138, in ?
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 123, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 157, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 238, in prepare_tree
    self.model_factory.reload()
  File "/usr/share/system-config-lvm/lvm_model.py", line 156, in reload
    self.__PVs = self.__query_partitions()
  File "/usr/share/system-config-lvm/lvm_model.py", line 190, in __query_partitions
    multipath_data = multipath_obj.get_multipath_data()
  File "/usr/share/system-config-lvm/Multipath.py", line 30, in get_multipath_data
    raise CommandError('FATAL', COMMAND_FAILURE % ("dmsetup",cmdstr, e))
NameError: global name 'CommandError' is not defined

```

---

### Post by BrokenBrick on 2007-04-02
Well I get the message 

```
sudo: unable to execute /usr/sbin/system-config-lvm: No such file or directory
```

I thought this was a simple problem and that my binaries were just not in the right place for some reason, but upon investigation I found that /usr/bin/system-config-lvm is a broken link to /usr/bin/consolehelper, and that /usr/sbin/system-config-lvm is a link to a python script in /usr/share/system-config-lvm which does not work.

---

### Post by kanna1620 on 2007-04-02
> **crazymonkey said:**
> This guide will show you how to install the Logical Volume Management gui from Fedora Core 5 rpm on your Ubuntu desktop. I prefer this gui over evmsgui because its alot more user friendly and gives you good information about your drives/volumes.

EDIT: Works in dapper and edgy.

[CENTER]
[COLOR="Red"][SIZE="4"]****WARNING****[/SIZE]
The GUI applies all settings instantly. Always be sure of what you do and double check before doing it. Its really easy to intialise the wrong drive and lose hours of work.](*,) [/COLOR][/CENTER]

First of all we want to get the alien package to convert the rpm package to a .deb :

```
sudo apt-get install alien

```

Then we need the system-config-lvm rpm package from Fedora :

```
wget http://download.fedora.redhat.com/pub/fedora/linux/core/updates/5/i386/system-config-lvm-1.0.18-1.2.FC5.noarch.rpm

```

Next we will convert the .rpm package to .deb package (you will see alot of warning, you can ignore them) :

```
sudo alien system-config-lvm-1.0.18-1.2.FC5.noarch.rpm

``` 
*change version number if necessary

Now we want to install our new deb package :

```
sudo dpkg -i system-config-lvm_1.0.18-2.2_all.deb

```

system-config-lvm needs the python interpreter and looks for it under the name /usr/bin/python2 but on ubuntu python is named /usr/bin/python2.4 so you need to create a link to python2.4 and name it python2

```
sudo ln -s /usr/bin/python2.4 /usr/bin/python2

```

Now if everything is alright you can start system-config-lvm (with sudo) and start managing your volumes.
[CENTER]
[COLOR="Red"][SIZE="4"]****WARNING****[/SIZE]
The GUI applies all settings instantly. Always be sure of what you do and double check before doing it. Its really easy to intialise the wrong drive and lose hours of work.](*,) [/COLOR][/CENTER]

I hope this guide will help you. Please let me know if there is some improvement to do or things I need to change, this is my first guide so be kind. :D

Good Howto. I feel so happy if you post the same Howto for a Ubuntu 6.06 user. I am not a Fedora user. Thank you.

---

### Post by morequarky on 2007-04-03
That is the howto for Ubuntu.

---

### Post by morequarky on 2007-04-03
Quick question?  I want to re-install my 64bit machine with Fisty with LVM.  Will this work on 64bit kernal?

---

### Post by crazymonkey on 2007-04-04
> **morequarky said:**
> Quick question?  I want to re-install my 64bit machine with Fisty with LVM.  Will this work on 64bit kernal?

I never tried it on 64bit. Let us now if it works, i'll add it to the Works with part of the howto

---

### Post by djseto on 2007-04-10
> **lime4x4 said:**
> heres the error i'm getting on edgy

john@john-edgy:/tmp$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 138, in ?
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 123, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 56, in __init__
    locking_type = self.model_factory.get_locking_type()
  File "/usr/share/system-config-lvm/lvm_model.py", line 998, in get_locking_type
    conf = open('/etc/lvm/lvm.conf')
IOError: [Errno 2] No such file or directory: '/etc/lvm/lvm.conf'
john@john-edgy:/tmp$ 


any ideas?

I am having this same problem. How do you fix it?

---

### Post by djseto on 2007-04-10
Nevermind. I didnt have LVM2 installed. Doh!

---

### Post by groggyboy on 2007-05-04
has anyone tried this with feisty?

i can't get it to run - i followed the howto but nothing happens when i try to run the program:
```
groggyboy@ono-sendai:~$ gksu /usr/bin/system-config-lvm
groggyboy@ono-sendai:~$ 

```

it's installed, however:```
groggyboy@ono-sendai:~$ locate system-config-lvm
/home/groggyboy/Desktop/system-config-lvm-1.0.18-1.2.FC5.noarch.rpm
/home/groggyboy/Desktop/system-config-lvm_1.0.18-2.2_all.deb
/home/groggyboy/.local/share/applications/system-config-lvm.desktop
/var/lib/dpkg/info/system-config-lvm.conffiles
/var/lib/dpkg/info/system-config-lvm.md5sums
/var/lib/dpkg/info/system-config-lvm.list
/etc/pam.d/system-config-lvm
/etc/security/console.apps/system-config-lvm
/usr/bin/system-config-lvm
/usr/sbin/system-config-lvm
/usr/share/doc/system-config-lvm
/usr/share/doc/system-config-lvm/copyright
/usr/share/doc/system-config-lvm/changelog.Debian.gz
/usr/share/doc/system-config-lvm-1.0.18
/usr/share/doc/system-config-lvm-1.0.18/COPYING.gz
/usr/share/applications/system-config-lvm.desktop
/usr/share/system-config-lvm
/usr/share/system-config-lvm/Segment.py
/usr/share/system-config-lvm/Volume.pyc
/usr/share/system-config-lvm/renderer.pyc
/usr/share/system-config-lvm/Multipath.pyc
/usr/share/system-config-lvm/Volume_Tab_View.pyc
/usr/share/system-config-lvm/CommandError.pyo
/usr/share/system-config-lvm/lvui.glade
/usr/share/system-config-lvm/VolumeGroup.pyc
/usr/share/system-config-lvm/Filesystem.glade
/usr/share/system-config-lvm/Filesystem.pyc
/usr/share/system-config-lvm/CommandError.pyc
/usr/share/system-config-lvm/Segment.pyo
/usr/share/system-config-lvm/lvm_model.pyo
/usr/share/system-config-lvm/Fstab.py
/usr/share/system-config-lvm/execute.pyc
/usr/share/system-config-lvm/LogicalVolume.py
/usr/share/system-config-lvm/parted_wrapper.pyc
/usr/share/system-config-lvm/Volume.py
/usr/share/system-config-lvm/parted_wrapper.py
/usr/share/system-config-lvm/Fstab.pyo
/usr/share/system-config-lvm/LogicalVolume.pyo
/usr/share/system-config-lvm/Partition.pyo
/usr/share/system-config-lvm/PhysicalVolume.py
/usr/share/system-config-lvm/system-config-lvm.py
/usr/share/system-config-lvm/VolumeGroup.py
/usr/share/system-config-lvm/CommandError.py
/usr/share/system-config-lvm/Partition.pyc
/usr/share/system-config-lvm/fdisk_wrapper.pyo
/usr/share/system-config-lvm/migrate_extents.glade
/usr/share/system-config-lvm/Volume.pyo
/usr/share/system-config-lvm/BlockDeviceModel.pyo
/usr/share/system-config-lvm/execute.pyo
/usr/share/system-config-lvm/LogicalVolume.pyc
/usr/share/system-config-lvm/BlockDeviceModel.pyc
/usr/share/system-config-lvm/Partition.py
/usr/share/system-config-lvm/lvm_model.py
/usr/share/system-config-lvm/InputController.pyo
/usr/share/system-config-lvm/BlockDeviceModel.py
/usr/share/system-config-lvm/CommandHandler.py
/usr/share/system-config-lvm/Filesystem.py
/usr/share/system-config-lvm/utilities.py
/usr/share/system-config-lvm/WaitMsg.pyc
/usr/share/system-config-lvm/renderer.pyo
/usr/share/system-config-lvm/pixmaps
/usr/share/system-config-lvm/pixmaps/grad3.xpm
/usr/share/system-config-lvm/pixmaps/lv_icon.png
/usr/share/system-config-lvm/pixmaps/PV.xpm
/usr/share/system-config-lvm/pixmaps/LV.xpm
/usr/share/system-config-lvm/pixmaps/VG.xpm
/usr/share/system-config-lvm/pixmaps/UV.xpm
/usr/share/system-config-lvm/ExtentBlock.pyc
/usr/share/system-config-lvm/cylinder_items.pyc
/usr/share/system-config-lvm/PhysicalVolume.pyo
/usr/share/system-config-lvm/Multipath.pyo
/usr/share/system-config-lvm/ExtentBlock.pyo
/usr/share/system-config-lvm/InputController.py
/usr/share/system-config-lvm/InputController.pyc
/usr/share/system-config-lvm/execute.py
/usr/share/system-config-lvm/lvm_model.pyc
/usr/share/system-config-lvm/Properties_Renderer.pyo
/usr/share/system-config-lvm/Segment.pyc
/usr/share/system-config-lvm/utilities.pyo
/usr/share/system-config-lvm/lv_edit_props.glade
/usr/share/system-config-lvm/Multipath.py
/usr/share/system-config-lvm/lvmui_constants.pyc
/usr/share/system-config-lvm/Filesystem.pyo
/usr/share/system-config-lvm/Properties_Renderer.pyc
/usr/share/system-config-lvm/lvmui_constants.py
/usr/share/system-config-lvm/cylinder_items.py
/usr/share/system-config-lvm/fdisk_wrapper.pyc
/usr/share/system-config-lvm/Volume_Tab_View.pyo
/usr/share/system-config-lvm/PhysicalVolume.pyc
/usr/share/system-config-lvm/system-config-lvm.pyc
/usr/share/system-config-lvm/parted_wrapper.pyo
/usr/share/system-config-lvm/BlockDevice.py
/usr/share/system-config-lvm/Properties_Renderer.py
/usr/share/system-config-lvm/utilities.pyc
/usr/share/system-config-lvm/WaitMsg.py
/usr/share/system-config-lvm/BlockDevice.pyc
/usr/share/system-config-lvm/BlockDevice.pyo
/usr/share/system-config-lvm/system-config-lvm.pyo
/usr/share/system-config-lvm/cylinder_items.pyo
/usr/share/system-config-lvm/Fstab.pyc
/usr/share/system-config-lvm/renderer.py
/usr/share/system-config-lvm/VolumeGroup.pyo
/usr/share/system-config-lvm/Volume_Tab_View.py
/usr/share/system-config-lvm/CommandHandler.pyo
/usr/share/system-config-lvm/WaitMsg.pyo
/usr/share/system-config-lvm/lvmui_constants.pyo
/usr/share/system-config-lvm/fdisk_wrapper.py
/usr/share/system-config-lvm/ExtentBlock.py
/usr/share/system-config-lvm/CommandHandler.pyc

```

any idea what's going on?

---

### Post by groggyboy on 2007-05-05
anyone?

---

### Post by Cheiron on 2007-05-07
for some reason that command doesn't work, but running the .py file directly does.

> $ sudo python /usr/share/system-config-lvm/ system-config-lvm.py

However, I'm having an issue of my own...

It seems to be running into an error and then having trouble finding its error-handling class.

When I modify the section of code to dump the error to the terminal, the command its trying to run is :

> 
dmsetup /sbin/dmsetup table


and the error message it returns is:

> /proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
/proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.08 (2006-07-17)(compat) and kernel driver 
Command failed


It's over my head, and could use any help offered.

Thanks

---

### Post by groggyboy on 2007-05-08
as to being unable to run it:

i borked my install by accident this week while attempting to set up a multi-boot situation.  i just followed this howto on my (fairly) fresh install, and for whatever reason running "sudo system-config-lvm" works fine.  bizarre, but i won't argue!

---

### Post by FerGeCo on 2007-05-13
Hi,

Just wanted to point out that there is a newer version available of system-config-lvm:

[ftp://fr2.rpmfind.net/linux/fedora/core/development/x86_64/os/Fedora/system-config-lvm-1.1.1-1.0.fc7.noarch.rpm](ftp://fr2.rpmfind.net/linux/fedora/core/development/x86_64/os/Fedora/system-config-lvm-1.1.1-1.0.fc7.noarch.rpm)

Changelog:

[http://rpmfind.net/linux/RPM/fedora/devel/x86_64/system-config-lvm-1.1.1-1.0.fc7.noarch.html](http://rpmfind.net/linux/RPM/fedora/devel/x86_64/system-config-lvm-1.1.1-1.0.fc7.noarch.html)

---

### Post by Raquen on 2007-05-14
So I'm running Feisty Fawn and trying to get this going and here is what I am getting:

matthew@Carceri:~$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 173, in <module>
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 158, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    locking_type = lvm_conf_get_locking_type()
  File "/usr/share/system-config-lvm/lvm_model.py", line 1025, in lvm_conf_get_locking_type
    conf = open('/etc/lvm/lvm.conf')
IOError: [Errno 2] No such file or directory: '/etc/lvm/lvm.conf'


I have confirmed that all the files are there, is there something I might be missing?

help....

---

### Post by SBFC on 2007-05-15
Thanks for the Howto. Followed it with Feisty and everything works peachy. 

Now to see if I can hose my system messing around with it. :P

---

### Post by SBFC on 2007-05-15
Um...so I set up my LVM layout wrong?

While using the GUI I chose to view the properties of my /home partition...and it says it's not resizable...none of them claim to be resizable...just trying to shrink my /home partition to make room for a new OS.

---

### Post by corvid on 2007-05-20
very helpful HOWTO thanks...
just needed to change the python link to reference python2.5 rather than 2.4 on Feisty - works perfectly.

---

### Post by Schwyl on 2007-05-26
OK so i followed this guide all the way through but when i run the last command it looks like it starts to open up but then closes and give me this.

server@Server:~$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 138, in ?
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 123, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 56, in __init__
    locking_type = self.model_factory.get_locking_type()
  File "/usr/share/system-config-lvm/lvm_model.py", line 998, in get_locking_type
    conf = open('/etc/lvm/lvm.conf')
IOError: [Errno 2] No such file or directory: '/etc/lvm/lvm.conf'



OK  so after that didnt work. I played around in Synaptic Package manager and i manually grabbed the LVm files. Now when i try again this is what it gives me

server@Server:~$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 138, in ?
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 123, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 157, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 238, in prepare_tree
    self.model_factory.reload()
  File "/usr/share/system-config-lvm/lvm_model.py", line 156, in reload
    self.__PVs = self.__query_partitions()
  File "/usr/share/system-config-lvm/lvm_model.py", line 190, in __query_partitions
    multipath_data = multipath_obj.get_multipath_data()
  File "/usr/share/system-config-lvm/Multipath.py", line 30, in get_multipath_data
    raise CommandError('FATAL', COMMAND_FAILURE % ("dmsetup",cmdstr, e))
NameError: global name 'CommandError' is not defined
server@Server:~$

---

### Post by rdeman on 2007-05-26
I am on Fiesty and I pointed the symlink to Python2.5 and now Im getting this:

[PHP]/usr/share/system-config-lvm/system-config-lvm.py
Traceback (most recent call last):
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 17, in <module>
    from lvmui_constants import PROGNAME, INSTALLDIR
ImportError: Bad magic number in /usr/share/system-config-lvm/lvmui_constants.pyc
[/PHP]

---

### Post by rdeman on 2007-05-28
> **rdeman said:**
> I am on Fiesty and I pointed the symlink to Python2.5 and now Im getting this:

[PHP]/usr/share/system-config-lvm/system-config-lvm.py
Traceback (most recent call last):
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 17, in <module>
    from lvmui_constants import PROGNAME, INSTALLDIR
ImportError: Bad magic number in /usr/share/system-config-lvm/lvmui_constants.pyc
[/PHP]

ok posting an answer to my own problem:

the 'Bad Magic Numbers' have something to do with the system-config-lvm utility being compiled with an older Python version. Ubuntu 7.04 Feisty uses Python 2.5
So I downloaded the latest development version of the system-config-lvm .rpm package for Fedora Core 7 ([http://rpmfind.net/linux/rpm2html/search.php?query=system-config-lvm&submit=Search+](http://rpmfind.net/linux/rpm2html/search.php?query=system-config-lvm&submit=Search+)...) and did generated a .deb package for Ubuntu out of the .rpm using alien as described in the 1st post of this thread. Then I made the soft linbk (not to Python2.4 but to Python 2.5 ofcourse) and et voila it works now.
:)

---

### Post by crumpet on 2007-06-10
Using Feisty and followed this guide - except to change python 2.4 to python 2.5 ...  system-config-lvm works just fine -  many thanks

---

### Post by esj on 2007-06-24
does this error make any sense?  running on 7.04

esj@lydia:~$ sudo system-config-lvm 
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 138, in ?
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 123, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 157, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 238, in prepare_tree
    self.model_factory.reload()
  File "/usr/share/system-config-lvm/lvm_model.py", line 156, in reload
    self.__PVs = self.__query_partitions()
  File "/usr/share/system-config-lvm/lvm_model.py", line 190, in __query_partitions
    multipath_data = multipath_obj.get_multipath_data()
  File "/usr/share/system-config-lvm/Multipath.py", line 30, in get_multipath_data
    raise CommandError('FATAL', COMMAND_FAILURE % ("dmsetup",cmdstr, e))
NameError: global name 'CommandError' is not defined
esj@lydia:~$

---

### Post by Canarygsr on 2007-08-15
OK 2 things

1; I have to use the terminal and Sudo (Cant use the link in the taskbar)

2; I have mounted my old fedora LVM, but my bigger problem is I cant change the read/write settings only root can ( I'm a newb to ubuntu, in fedora I would have just browsed in "super user mode" (su) and changed it). I would like mythtv to be able to write its files to this LVM can anyone help

Thanks

---

### Post by codexile on 2007-10-13
For all of you having the error:

NameError: global name 'CommandError' is not defined

a simple 'apt-get install dmraid' will fix it.

---

### Post by morequarky on 2007-10-21
refuses to start

python the latest
seemed to install fine

failed to execute child process "/usr/bin/system-config-lvm" (No such file or directory)

I downloaded f7 for 64 same result

---

### Post by StratosL on 2007-10-21
> **morequarky said:**
> refuses to start

python the latest
seemed to install fine

failed to execute child process "/usr/bin/system-config-lvm" (No such file or directory)

I downloaded f7 for 64 same result

Same here. Running gutsy 64 bit

---

### Post by hgbekker on 2007-10-27
On Gutsy the link to the python binary should be to python2.5 not python2.4
```
sudo ln -s /usr/bin/python2.5 /usr/bin/python2
```
Chera

---

### Post by hgbekker on 2007-10-27
I'm looking for an easy way to resize my root logical volume. Is there a Ubuntu or perhaps Fedora live CD with LVM support? Must be a CD cause the server has no DVD (old machine).

Chera

---

### Post by hgbekker on 2007-10-29
I found a good way to resize my root logical volume with the Knoppix 5.1.1 live CD. Just boot from knoppix. Start a terminal and
```
su
/etc/init.d/lvm start
lvdisplay
```
And you should have all your logical volumes available. Then you can use lvextend to increase the root logical volume and resize2fs to grow the ext2/ext3 root file system to fill up the increased logical volume. 
Hope this is of use to someone.

Chera

---

### Post by IanW on 2007-11-03
> **morequarky said:**
> refuses to start

python the latest
seemed to install fine

failed to execute child process "/usr/bin/system-config-lvm" (No such file or directory)

I downloaded f7 for 64 same result

The launcher symlink seems to be broken.This worked for me on Gutsy 64:-

```
sudo rm /usr/share/system-config-lvm
sudo ln -s /usr/share/system-config-lvm/system-config-lvm.py /usr/bin/system-config-lvm

```

Then edit the launcher to make it run with root priveleges:-

```
Open System/Preferences/Main Menu/Other
Right-click on "Logical Volume Manager" & select Properties
Ensure the existing "Command" begins with gksu

```

---

### Post by MattiJ on 2007-11-03
I'm on Gutsy amd64 and got this working fine, but have to activate  the lv manually after reboot.

```
 sudo vgchange -ay vg
```

if I have  

```
/dev/vg/lv1		/media/lv1		ext3	defaults	1 2
```

in fstab boot stops shoving this error

```
fsck.ext3: No such file or directory while trying to open /dev/vg/lv1
/dev/vg/lv1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8
```

so how can I get it to auto activate before mount?

Edit:
Found this [http://www.faqs.org/docs/Linux-HOWTO/LVM-HOWTO.html#AEN338]("http://www.faqs.org/docs/Linux-HOWTO/LVM-HOWTO.html#AEN338")
and it solved it. But shouldn't this have been set up by the install?

---

### Post by kronocyber on 2007-11-26
I ran around google and message boards all day with a crazy headache after failing to install from the how to
 :confused: "/usr/bin/system-config-lvm" (No such file or directory.
so I after chasing this "Header V3 DSA signature: NOKEY, key ID 4f2a6fd2" **distraction** all over 
I came back and actually **read** not skimmed the thread and found this.
> **hgbekker said:**
> On Gutsy the link to the python binary should be to python2.5 not python2.4
```
sudo ln -s /usr/bin/python2.5 /usr/bin/python2
```
Chera I uninstalled the deb via synaptitic,and deleted the alien  generated deb made the working symbolic link to python2.[COLOR="Red"]**[SIZE="5"]5[/SIZE]**[/COLOR] this time 
Then installed dmraid via synaptic made a new deb with alien and installed it.
:guitar:and now it works!!!:guitar: thank you so much

P.S. todays daily affirmation:
I will take more time to read the symbolic links I create in the future
and less time screaming and throwing things! :)

---

### Post by JimGvo on 2008-01-10
> **StratosL said:**
> Same here. Running gutsy 64 bit

It appears to be in /usr/sbin on my system, not /usr/bin.

---

### Post by daveatub on 2008-01-17
> **gtr225 said:**
> I booted up from the Ubuntu 6.10 Desktop CD and followed the instructions and got the following error```
ubuntu@ubuntu:~$ sudo system-config-lvm
Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 138, in ?
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 123, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 73, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 157, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 238, in prepare_tree
    self.model_factory.reload()
  File "/usr/share/system-config-lvm/lvm_model.py", line 156, in reload
    self.__PVs = self.__query_partitions()
  File "/usr/share/system-config-lvm/lvm_model.py", line 190, in __query_partitions
    multipath_data = multipath_obj.get_multipath_data()
  File "/usr/share/system-config-lvm/Multipath.py", line 30, in get_multipath_data
    raise CommandError('FATAL', COMMAND_FAILURE % ("dmsetup",cmdstr, e))
NameError: global name 'CommandError' is not defined

```

Make sure you have lvm2 installed
$sudo apt-get install lvm2

---

### Post by jtsop on 2008-04-02
for Hardy use:
ln -s /usr/bin/python2.5 /usr/bin/python2

---

### Post by crazymonkey on 2008-04-02
> **jtsop said:**
> for Hardy use:
ln -s /usr/bin/python2.5 /usr/bin/python2

Updated the first post.
Thanks for the update!

---

### Post by MartinHansell on 2008-05-05
This has been a really great help - thanks!  Of course, I have a question also...  your post says that if you installed using the (textual) liveCD installer and using the LVM default guided setup you could not alter the root without rebooting with the liveCD.  But later in your comment responses you said that if you can just edit the properties of the "root" LV from within the GUI.

I tried to alter the size of the root LV by editing properties, but I had to agree to demount the fs in order to resize.  Thankfully the GUI told me I that /bin was in use, and that I could not demount the fs in order to make the changes to the size of the LV..  I guess this saved me from having to reinstall the whole system again ??

This is a brand new install hence my willingness to try crazy things like un-mounting the root system (I also don't have a clue what I'm doing, really).  But I am trying to get myself setup before I migrate everything over from my WindowsXP files...  so do I have to use the LiveCD approach (which to be honest I would rather not do coz of other issues like hardware glitches)?  What am I missing

Cheers
Martin  :)

---

### Post by globalenigma on 2008-05-16
Quick Note to people using XFCE (such as my mythbox):

Make sure you install package python-gnome2 or you will get a gnome error.  Yes I know it is a given for most people but I was stumped for five mins until I actually read the error message word for word.  

Just a quick tip for those not using gnome! :)

sudo apt-get install python-gnome2

---

### Post by MartinHansell on 2008-05-28
Hi CrazyMonkey...

I am in solid agreement with all the accolades - this post has been a real help to me....  I have been experimenting with Linux/Ubuntu and have reinstalled and rejigged my system several times along the way.  Each time I have followed your instructions, and got the result I was after...... but this time around I seem to have generated an error, and not sure what I have done wrong. Wondered if you could take a look?  The system starts to load and then bombs out.

Many thanks
Martin

ps - take the compliments, ignore the help request... i read backwards and found the answer on your page 6.  Cheers!!

**********************************

martin@Mangostine:~$ sudo system-config-lvm &
[2] 798
martin@Mangostine:~$ Traceback (most recent call last):
  File "/usr/sbin/system-config-lvm", line 173, in <module>
    runFullGUI()
  File "/usr/sbin/system-config-lvm", line 158, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/sbin/system-config-lvm", line 108, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 135, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 216, in prepare_tree
    self.model_factory.reload()
  File "/usr/share/system-config-lvm/lvm_model.py", line 164, in reload
    self.__PVs = self.__query_partitions()
  File "/usr/share/system-config-lvm/lvm_model.py", line 198, in __query_partitions
    multipath_data = multipath_obj.get_multipath_data()
  File "/usr/share/system-config-lvm/Multipath.py", line 30, in get_multipath_data
    raise CommandError('FATAL', COMMAND_FAILURE % ("dmsetup",cmdstr, e))
NameError: global name 'CommandError' is not defined
martin@Mangostine:~$

---

### Post by jtsop on 2008-06-20
sudo apt-get install python-gnome2

when not using gnome e.g. kubuntu

---

### Post by jtsop on 2008-07-15
this is a script to install command for system-config-lvm (with ALL dependencies in [k]ubuntu) from latest version of fedora 9:

url="http://download.fedora.redhat.com/pub/fedora/linux/releases/9/Everything/i386/os/Packages/system-config-lvm-1.1.4-1.0.fc9.noarch.rpm"	
file="system-config-lvm.rpm"
wget url -O /tmp/$file && sudo alien -i /tmp/$file && sudo ln -s /usr/bin/python2.5 /usr/bin/python2 && sudo apt-get install python-gnome2 lvm2

ps: please update first page

---

### Post by haydentech on 2008-07-31
If you don't want to deal with alien and Fedora packages, you can just use the package from Intrepid.  Thankfully, it requires no new dependencies over what's already in Hardy.

[http://packages.ubuntu.com/intrepid/all/system-config-lvm/download](http://packages.ubuntu.com/intrepid/all/system-config-lvm/download)

The whole thing was downloaded and installed in under a minute, and just feels a lot cleaner than the other method.

---

### Post by Chinthor on 2008-09-27
> **codexile said:**
> For all of you having the error:

NameError: global name 'CommandError' is not defined

a simple 'apt-get install dmraid' will fix it.
Thanks! Was searching through and only found more like me with the same problem. Solved!

---

### Post by davidmaxwaterman on 2008-10-28
> **Chinthor said:**
> Thanks! Was searching through and only found more like me with the same problem. Solved!

This fixed my problem too.

---

### Post by bellesmanieres on 2008-11-14
> If you don't want to deal with alien and Fedora packages, you can just use the package from Intrepid. Thankfully, it requires no new dependencies over what's already in Hardy.

[http://packages.ubuntu.com/intrepid/...g-lvm/download](http://packages.ubuntu.com/intrepid/...g-lvm/download)

Or use the debian package. It worked like a charm for me (on Hardy with Kde)
[http://packages.debian.org/search?keywords=system-config-lvm]("http://packages.debian.org/search?keywords=system-config-lvm")

---

### Post by Caysho on 2008-12-20
mythbuntu 8.10, fresh install with all updates.

I think the [LVM service is not running]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=507751#10").

The python symlink and the dmraid install didn't change anything (I don't know if they have any effect on the lvm service or not)
I did a reboot and the gui is now up.

---

