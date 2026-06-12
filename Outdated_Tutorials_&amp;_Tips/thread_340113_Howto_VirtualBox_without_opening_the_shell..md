---
title: "Howto: VirtualBox without opening the shell."
date: 2007-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Ryan Marcus on 2007-01-16
[SIZE="5"]What will this guide do?[/SIZE]
This guide will take you through the steps of setting up VirtualBox, an application similar to Qemu and VMWare.

Unlike Qemu and VMWare, you can install VirtualBox without ever opening up the terminal, making it one of **the easiest pieces of software to install on Linux ever.**

Despite the ease, however, VirtualBox still merits a guide due to some "gotchas" when installing.

[SIZE="5"]Who can use VirtualBox?[/SIZE]
Anybody that is running Ubuntu Edgy Eft and wants to use VirtualBox for PERSONAL use.

[SIZE="5"]Alright already! Let's do it![/SIZE]
[SIZE="4"]1. Downloading[/SIZE]
The first step, of course, is to download VirtualBox. They've been nice enough to give us a **deb package**, so installation will be a snap.

You can go to the download page here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).

You will want to download "VirtualBox 1.3.2 for Linux Hosts." Choose the Edgy Eft Ubuntu link.

You will be asked (assuming you are using Firefox) if you would like to open the package with the default application or save it to disk. You want to **save to disk**.

[SIZE="4"]2. Installing[/SIZE]
This will be the easiest thing to install ever. Promised.

Go onto your desktop, or where you have Firefox set to download things, and right click on the .deb file. In the menu, go to Open With -> GDebi. Then, click the "install" button. What did I tell you? Easy. Almost like... a Mac or something... :-k 

[color=blue]EDIT (by bodhi.zazen): Virtualbox has been in fairly heavy development and there was a number of How-to's on the web, including this one, outlining how to install VirtualBox. Many have not been maintained.

_FYI_: Innotek now maintains a repo for VirtualBox and you might want to consider adding it. See this link for information :[/color]

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

[Color=blue]Another gotcha: During the installation you need to read and accept the license. To navigate this part of the install, use the <tab> key to select "OK" and the <enter> key to continue the install. If you abort the install you will break apt-get/synaptic.

The fix to this is to remove Virtualbox, from a terminal, with this command:[/color]

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

[[color=blue]**"noob friendly virtualbox install instructions"**[/color]](http://ubuntuforums.org/showpost.php?p=3496809&postcount=2) ~ *Thank you Dr Small*. 

[SIZE="4"]3. Configuring[/SIZE]
Ha! You thought you where done. However, it would not be Linux if you had to do something bizarre to get it to work.

The first thing you should do after the installation is logout and back in again. This might not be needed, but I did it.

When you installed VirtualBox, it created a group called vboxusers. For whatever reason, the installer was unable to automatically add you to the group, so you will have to do it yourself.

However, as promised, no shell.

Go to System -> Administration -> Users and Groups. On the right, you will see a button labeled "Manage Groups." Click on it. Scroll down the list to "vboxusers." The last item for me. Double click on it. You will see a list of users. Check your name, and press "OK." Then close "Groups settings." Then close "Users settings."

[SIZE="4"]Setup your first VM[/size]
Time for the good stuff. I've always been a little curios about Xubuntu, but never curios enough to actually download and try a live CD. VirtualBox presented the opportunity to try Xubuntu without burning an ISO.

First, download the Xubuntu CD ISO. You can do this from the download page on [xubuntu.com](xubuntu.com).

Once the ISO has finished downloading, open InnoTek VirtualBox from your Applications -> System Tools menu.

Next, click on the "New" button in the upper left corner of the window. A new window will appear. Click the "Next" button.

On the next screen, you will be asked for a name and an OS type. I entered "Xubuntu" and selected "Linux 2.6." Click "Next."

In this window, you will be allowed to choose the memory size for the OS. To be on the safe side, I set mine to 400 MB. Click "Next."

You will be asked to choose a "boot hard disk." Because this is the first time you've ran VirtualBox, you will have to click on the "New" button. 

In the window that appears, click on "Next."

This screen will allow you to choose to have a dynamically expanding image, or a fixed-size. A dynamic image will expand as you fill it, using the least amount of hard disk space possible. The fixed-size option will use all of the space, but will be faster. I went with dynamic.

Make your choice, and click "Next."

In this window, you will name and set the size of the image file. I named mine "Xubuntu" and set it's size to 3 GB.

Click "Next," and then "Finish."

Make sure your new hard drive is selected in the popup, and then click next. Then click "Finish."

Almost there! Next, select your new VM in the VM sidebar on the left side of the main window and click the settings button at the top. Go down to the "CD/DVD-ROM" section and check the "Mount CD/DVD Drive" checkbox.

Select the ISO image file option, and locate your Xubuntu image.

Press "OK."

So close! Go to File -> Global Settings in the main window, and click on "Input." Click inside of the host key field and press "F1."

Press "OK."

Select your new VM and press "Start." 

The VM will now boot from your Xubuntu live CD, which you can use to install Xubuntu.

If you click in the VM and want to get the mouse back, just press "F1."

I hope this guide helped, feel free to comment/flame.

[size=5]Troubleshooting[/size]
**1. You get a apt-get error the next time you try to get a package.**
You probably did not install the package correctly, or perhaps you have installed some strange packages. I don't claim to be an expert, but it seems some applications require an old version of the libcln4 package, and VirtualBox installs a new one. This causes some things to not install properly. Maybe VirtualBox requires the older version... I'm not sure. However, GDebi *should* handle this for you. However, for shell junkies who just *have* to break there machines in at least one way, you can solve the problem using these steps (once again, without using a shell):

1. Go to System -> Administration -> Synaptic Package Manager
2. Wait for the GUI to load (the toolbar items will become enabled.)
3. Click on the "Search" toolbar item.
4. Enter "virtualbox" and make sure the "Look in:" popup is set to "Name."
5. Click the search button.
6. You will see the single virtualbox package. Right click on it, and select "Mark for Complete Removal."
7. Click the "Apply" button in the toolbar, symbolized by a check mark.
8. Reboot your system.
9. Go back through this HowTo, and follow it exactly. If you open terminal, you are doing something wrong.

**2. When you open GDebi, you get a dependency (libc6-dev) error.**
1. Make sure the universe and multiverse are enabled. To do this, go to System -> Administration -> Software Sources, and make sure all the boxes except "Source Code" are checked.
2. Close Software Sources, if you opened it.
3. Open Synaptic Package Manager, from System -> Administration -> Synaptic Package Manager.
4. Click on the "search" button and type in "libc6-dev."
5. The package list will contain two entries, libc6-dev and libc6-dev-amd. Right click on the first one (the NON amd one) and mark it for installation.
6. Click "apply." Close Synaptic and try again.

If you don't see the "libc6-dev" package, you could try this alternative, which I was told works, but have not tested myself. Go back through the above 6 steps, but instead install the package "qemu". After the package installs, you can try installing VirtualBox again. If it works, you can uninstall Qemu. If it does not, you may also uninstall Qemu, unless you'd like to try it. 

One of the best ways to keep your Linux system in shape is by using the GUI tools provided by the Ubuntu team. They are designed not to break your system, and will provide a better overall experience then diving into the shell every 5 minutes. It has been proven that users who use GUIs when available are much more productive and effective then hard-core CLine users. The GUI is designed to serve and protect your work, as well as enable you to do it as effectively as possible.

---

### Post by spyke01 on 2007-01-17
wether i try to install the dapper package from shell or not i get an error with the vboxdrv where it doesnt create it, this is with root privleges, i also tried building from source and have the same issue

---

### Post by Ryan Marcus on 2007-01-17
I did not mean for this guide to be used by Dapper users. It is met for Edgy users, as stated in the guide.

---

### Post by gorilla_king on 2007-01-17
i had it installed and working two hours after they released it for free the other day. but hey thanks for posting this anyways

---

### Post by myname on 2007-01-21
Here is what I am getting when I install virtualbox:

~/download$ sudo dpkg --install VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb
Selecting previously deselected package virtualbox.
(Reading database ... 81420 files and directories currently installed.)
Unpacking virtualbox (from VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb) ...
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox

Any ideas what is wrong?  Do I not have the libraries installed?

--Kevin

---

### Post by ifross on 2007-01-21
You need to install dependencies: Go to System > Administration > Synaptic Package Manager and search for and install libxalan110 and libxerces27 then try it again.

---

### Post by george_apan on 2007-01-21
This looks interesting. How is the speed compared to vmware or qemu with the accelerator module?

And it's GPL now so I guess it won't be long until it reaches debian (and after that ubuntu) repositories...

---

### Post by Ryan Marcus on 2007-01-21
It runs about as fast (little faster) as Qemu with Kqemu. I've never tried VMWare.

Also, if you just double click on the debian package, it should install the needed packages by itself.

---

### Post by myname on 2007-01-22
Sweet, I got Vritualbox installed.  And following the steps to get Windows installed under it, I am having a permission problem.

When I click my XP Virtual Box, to launch it, and launch the setup CD, I get t windows with the following error:


VirtualBox kernel driver not accessible, permission problem.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1909 VERR_VM_DRIVER_NOT_ACCESSIBLE
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 ---------------------------------

I set the permissions per the above steps, then even went in to the official readme and tried those.  Nada.

Any help?

--Kevin

---

### Post by Stinger on 2007-01-22
> **myname said:**
> 
[COLOR="Red"]VirtualBox kernel driver not accessible, permission problem.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1909 VERR_VM_DRIVER_NOT_ACCESSIBLE
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}[/COLOR]


I get the exact same message , could it have anything to do with the Nvidia driver I'm using ???? :confused:

---

### Post by nfear24 on 2007-01-22
I installed VirtualBox just fine on my ubuntu Desktop.  But when I try to install on my ubuntu server I am having all kinds of problems with the vboxdrv.

---

### Post by Stinger on 2007-01-23
> **myname said:**
> 
VirtualBox kernel driver not accessible, permission problem.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1909 VERR_VM_DRIVER_NOT_ACCESSIBLE
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


This message is caused by launching the vbox kerneldriver with the wrong permissions.
Probably because you have tried to launch Vbox before you changed the user permissions , login out and in again only will only change the user permission but you'll have to launch the kerneldriver with the right permissions too , and because its already launched you can't do that.
A quick reboot solves this problem :grin: 
You can read all about it at the Vbox FAQ section
[[COLOR="Sienna"]http://www.virtualbox.org/wiki/User_FAQ[/COLOR]]("http://www.virtualbox.org/wiki/User_FAQ")

---

### Post by jimking1981 on 2007-01-23
I get this error when i try to start a virtual machine 
 

> VirtualBox kernel driver not installed.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

any body know how to fix this

---

### Post by Stinger on 2007-01-23
> **jimking1981 said:**
> I get this error when i try to start a virtual machine 
any body know how to fix this
Are you using Dapper ?? The howto is for [COLOR="Red"]Edgy only[/COLOR].

---

### Post by jimking1981 on 2007-01-23
got it to work reinstalled everything with 686 in it and that did the trick not the most elegant way but what ever works

---

### Post by webdr on 2007-01-23
> **jimking1981 said:**
> I get this error when i try to start a virtual machine 
 



any body know how to fix this

ditto... I have had this same problem on edgy and dapper
on three different machines so far, no love.
Spent a few hours reading this trying that... Glad to hear that others are not sharing in my misery, however, a little bummed that I can't seem to beat this error.

---

### Post by webdr on 2007-01-23
ok, I got past the 1908 error in edgy
1) attached is a quickie script for reseting the crashed install -- 
Download it , modify it to match your paths and run it or you can just follow the directions and do it line by line as instructed here... [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)[http://www.virtualbox.org/wiki/User_FAQ]("http://www.virtualbox.org/wiki/User_FAQ")

2) in a terminal window 'oops there goes the 'no' terminal thing ... sorry
run uname -a andtake note of the numerics
3) run synaptic, and make sure you have:
-linux-headers installed that match the numerics noted in previous step
-gcc
-libxalan110
-libxerces27
after making sure you have all that, you may now exit synaptic

4) Install Virtualbox again
5) You should now be good to go IF you have done the aforementioned (previos in this thread) usergroups instructions.
6) If you now get the 1909 error instead of the 1908 error, you can...

1) double check that u are in the user group and reboot and try again... should work fine
2) get impatient, don't reboot and instead start virtual box as super user.

I hope this helps and I'm sorry I did not have time to do more, perhaps someone will have time to take this and clean it up a bit.

ttyl  ):P 
racerx

---

### Post by Ryan Marcus on 2007-01-24
You terminal junkies. :D 

If you get a premission error, it is because you forgot to add yourself the the Vbox user group and then restart / logout.

---

### Post by Internet on 2007-01-24
missed a post

---

### Post by charakad on 2007-01-25
Hello,
I am running Edgy Eft on a 256 RAM computer. I am trying to install Windows XP with a base memory of 192MB which was the default.
When I try to start, i get this error. Appreciate some help.

Failed to start VM execution (VERR_NO_MEMORY).
Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Thank you
Charaka

---

### Post by ofek on 2007-01-26
Works Great~! great howto although i didnt quite follow it, wanted to compile myself lol.
I now have vista and xp on my linux system which means i dont ever need to reboot i can develop in visual c++ and play war3 =) the 2 most wanted options for me anyways).

---

### Post by balloons on 2007-01-26
> **charakad said:**
> Hello,
I am running Edgy Eft on a 256 RAM computer. I am trying to install Windows XP with a base memory of 192MB which was the default.
When I try to start, i get this error. Appreciate some help.

Failed to start VM execution (VERR_NO_MEMORY).
Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Thank you
Charaka

Try lowering your memory - you probably don't have 192 free. Try 64 mb (i know it'll be slow), and see if it works, you can up it later.

---

### Post by Fingerz91 on 2007-01-26
Hey All,

I saw this and thought, NICE, no more dual booting! However, I set up as per these instructions, and chose XP and my system (which is what I intended to install...) but I cannot get the program to read my XP cd to begin the install...

Any ideas?

---

### Post by nfear24 on 2007-01-27
> **Fingerz91 said:**
> Hey All,

I saw this and thought, NICE, no more dual booting! However, I set up as per these instructions, and chose XP and my system (which is what I intended to install...) but I cannot get the program to read my XP cd to begin the install...

Any ideas?

Make sure under the CD/DVD section in VirtualBox you have the mount device box checked.

Nick

---

### Post by NobodySpecial on 2007-01-27
Great How-To.  As mentioned above, it wouldn't hurt to do just ONE entry into the terminal to start:
```
sudo apt-get install linux-headers-`uname -r` gcc libxalan110 libxerces27
```
Also, I had to reboot, not just log out and in again, to get the permissions thing to work.

The program runs well on Ubuntu Edgy with Windows XP guest, although it didn't detect the Windows Key on my keyboard for some reason.  I wanted to experiment more without re-activating my copy (which I activated within VMWare), but the (legitimate) trick to copy the two wpa.* files didn't work.  ** sigh **

So does anybody know how to convert a VMWare machine into a VirtualBox machine?

---

### Post by xpod on 2007-01-29
I`d been keen to try the "virtual machine" thing for a while but kept putting it off until now.

Managed to install ok but i cant seem to get round the permission problem running VirtualBox normally.....checked in the users & groups and my username(real name) was already checked but still no joy, even after rebooting..

Ok, so run it as root and the permission problems is gone but even when i make sure the "mount cd/dvd drive" box is checked i cant seem to run any of the OS`s i`ve tried......XP,feisty & Pclos.

As soon as i hit start it goes past the INNOTEK splash but then i get a"FATAL:No bootable medium found !Sytem halted.
I`m not sure if it`s having trouble seeing my dvd drive because when i go and check the "mount cd drive" box it dont have my actual drive listed in the dropdown box next to it.It just turns blue if i click it.:confused: 

Will obviously keep reading for now but any ideas would be welcome
EDIT:The cd drive is still listed as "unmounted" on the right hand pane of the VB gui even after apparently mounting it.

---

### Post by nfear24 on 2007-01-29
> **xpod said:**
> I`d been keen to try the "virtual machine" thing for a while but kept putting it off until now.

Managed to install ok but i cant seem to get round the permission problem running VirtualBox normally.....checked in the users & groups and my username(real name) was already checked but still no joy, even after rebooting..

Ok, so run it as root and the permission problems is gone but even when i make sure the "mount cd/dvd drive" box is checked i cant seem to run any of the OS`s i`ve tried......XP,feisty & Pclos.

As soon as i hit start it goes past the INNOTEK splash but then i get a"FATAL:No bootable medium found !Sytem halted.
I`m not sure if it`s having trouble seeing my dvd drive because when i go and check the "mount cd drive" box it dont have my actual drive listed in the dropdown box next to it.It just turns blue if i click it.:confused: 

Will obviously keep reading for now but any ideas would be welcome
EDIT:The cd drive is still listed as "unmounted" on the right hand pane of the VB gui even after apparently mounting it.

Try unmounting the cd rom drive in your host system.  Then go and check that box in VirtualBox.  I found that solved a problem like that for me once..

Nick

---

### Post by charakad on 2007-01-29
> **guitara said:**
> Try lowering your memory - you probably don't have 192 free. Try 64 mb (i know it'll be slow), and see if it works, you can up it later.

Thank you for your reply. It worked.

---

### Post by xpod on 2007-01-29
> Try unmounting the cd rom drive in your host system. Then go and check that box in VirtualBox. I found that solved a problem like that for me once..

Good stuff m8
Seems to be working via a straight ISO ok so as soon as i`m finished with feisty here i`ll go back and give your idea a shot.

Still having to run it as root though so i`ll be at it for a while yet it seems:D 

Thanks a lot

---

### Post by xpod on 2007-01-29
Ok,all good with the cd-drive too.
Still a few niggles what with having to run as root and a couple of other minor annoyances with the feisty ISO but asides from that it`s all good:D 

Just what i`m going to do with a virtual XP i dont know but`s it`s good to know it works at least.
Cheers again

---

### Post by bodhi.zazen on 2007-02-01
Nice How-to

This thread has been added to the UDSF wiki.

[VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by nicnocquee on 2007-02-03
hi, i've installed virtual box on my edgy and it worked well. no errors or anything. but i have this one problem, i can not access my usb device from the guest OS, Windows XP. i have followed the instruction on the user manual but it's not working. the device is always accessed by edgy. i read that the user who run virtual box should have permission to write to usb filesystem. i run my virtual box as root, shouldn't root be able to do anything?...please help...

---

### Post by udanek on 2007-02-07
> **Stinger said:**
> I get the exact same message , could it have anything to do with the Nvidia driver I'm using ???? :confused:

No. Just type in console: 

sudo chmod 666 /dev/vboxdrv

---

### Post by mtalexan on 2007-02-09
Your directions don't work for a large number of people.  Try searching virtualbox and looking at how many people had apt or Synaptics stop working for them.  There's even a post on the VirtualBox website's FAQ about Debian distributions of Linux having this problem.  The only workable fix I found for it was here 
[http://ubuntuforums.org/showthread.php?t=350447&highlight=Virtualbox+install]("http://ubuntuforums.org/showthread.php?t=350447&highlight=Virtualbox+install")
I basically just had to "uninstall" it to get my computer working again.  The fix listed on the [VirtualBox website FAQ]("http://www.virtualbox.org/wiki/User_FAQ") involves manually changing error codes then following kernel compilation instructions that are meant to apply to people who want to help work on newer versions.

---

### Post by ghandi69_ on 2007-02-10
Great HowTo, I got it up and running during my all nighter last night.  I did have every error that I think was possible ....(1908, 1909)...... I also said it needed newer versions of some libraries, but I just did a force depends version with my dpkg -i and that got it running.  I have some issues though

1.)  When I double clicked no the .deb file.. there was no option to install, just opened up the folder and listed what was inside.

2.) I now have windows vista up and running, but something worse may have come out of it.  Whenever I try to install anything.... be it amarok, k3b, or whatever.. I get this..

> You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  pi: Depends: libcln4 but it is not going to be installed
  virtualbox: Depends: libqt3-mt (>= 3:3.3.7) but 3:3.3.6-3ubuntu3 is to be installed
              Depends: libssl0.9.8 (>= 0.9.8c-1) but 0.9.8b-2ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

However, when I go apr-get -f install... it removes the virtual box package!!!!

3.) Windows Vista is not able to get access to the internet.  Which is suprising, because it does in ubuntu.. I have tried every setting under network (except the one that works ;-)

Any help on any of these issues would be great.

---

### Post by Ryan Marcus on 2007-02-10
I apologize to all of the users that unintentionally screwed over there apt while using this guide, and, you may now look to the troubleshooting section of this guide to solve the problem.

Sorry for the inconvenience.

---

### Post by ghandi69_ on 2007-02-11
Hey man, any troubles I had along the way were more than worth it... I've had more success with this how to than most I read on this site.

---

### Post by ghandi69_ on 2007-02-11
wait a minute.. I just read the trouble shooting section... it involves removing my virtual box package!!!

lol thats not a trouble shoot.. thats giving up.. I already knew how to remove the package successfully, but I want to be able to install virtual box AND use app-get afterwords..

any way to do that?

---

### Post by zeroblitzt on 2007-02-11
I much preferred the thread that told me how to set up VMware, I just kept getting error after error with this.

---

### Post by Ryan Marcus on 2007-02-11
> **ghandi69_ said:**
> wait a minute.. I just read the trouble shooting section... it involves removing my virtual box package!!!

lol thats not a trouble shoot.. thats giving up.. I already knew how to remove the package successfully, but I want to be able to install virtual box AND use app-get afterwords..

any way to do that?

Sorry, I forgot the "try again" step. If you install everything via GDebi, it should work, otherwise, you are going to have to figure our what package is using a newer/older version of that library, which could take... A while.

---

### Post by ghandi69_ on 2007-02-11
grrr....

I have tried again.. and it always brings me back to the same place... either with virtual box and no apt or apt and no virtual box....

I follow the guide all the way up until it point where you click on the .deb file... when I do that, it just opens the file, there is no option to install when I click on the downloaded .deb file... I click on install with gdebi... and it gives an erros that it needs some dependencies that apparently don't exist.. as far as I can tell.

Any help though would be nice.

---

### Post by Ryan Marcus on 2007-02-12
> **ghandi69_ said:**
> grrr....

I have tried again.. and it always brings me back to the same place... either with virtual box and no apt or apt and no virtual box....

I follow the guide all the way up until it point where you click on the .deb file... when I do that, it just opens the file, there is no option to install when I click on the downloaded .deb file... I click on install with gdebi... and it gives an erros that it needs some dependencies that apparently don't exist.. as far as I can tell.

Any help though would be nice.

Have you enabled the universe/multiverse?

---

### Post by ghandi69_ on 2007-02-13
You betcha

---

### Post by Ryan Marcus on 2007-02-13
I'm sorry, but I really don't know enough about the inner workings of the Debian system to help you too much. It looks like you need to find all the packages on your system that relie on libcln4. I have no idea how to do that, but one of them is using an older version of the library, and is being pesky about an update. That's my best guess.

---

### Post by linuxfanatic1024 on 2007-02-13
I have a problem where it spontaneously reboots my computer right after clicking Start, no matter what the guest settings are. This didn't happen when I tried it in Fedora. I got the module permissions and such resolved though.

I also tried the generic package that worked in Fedora with the same results. Any ideas?

---

### Post by ghandi69_ on 2007-02-13
> **Ryan Marcus said:**
> I'm sorry, but I really don't know enough about the inner workings of the Debian system to help you too much. It looks like you need to find all the packages on your system that relie on libcln4. I have no idea how to do that, but one of them is using an older version of the library, and is being pesky about an update. That's my best guess.

Ok man, thanks for sticking with me though. I'll get back to ya if I find out the problem.

---

### Post by linuxfanatic1024 on 2007-02-13
OK, I fixed the spontaneous rebooting by *downgrading* to 1.3.2. VirtualBox 1.3.4 seems to have a serious bug in the kernel module.

Turns out I didn't realize they updated it, but I hope they fix it for the next release. It's a great program though. I used to use VMware Server until I found this. Now VMware Server is off my drive for good! It was great since it was full-featured, but I absolutely hated the reg-key thing. And VirtualBox is MUCH faster than VMware Server.

Anyway, if anyone else has spontaneous rebooting of your computer with the latest version, 
try downgrading to 1.3.2 (available on [the Old Builds page]("http://www.virtualbox.org/wiki/Download_Old_Builds")).

---

### Post by ghandi69_ on 2007-02-13
I wonder if downgrading will fix a bunch of other problems as well.. I'll try it.

---

### Post by ghandi69_ on 2007-02-13
Hey linux fanatic, thanks for the help!!  The old version runs as smooth as butter(without the commandline even.. just for you ryan ;-)

Although.. I'm still unable to get access to the internet within the virtual machine.. is that normal?

---

### Post by linuxfanatic1024 on 2007-02-14
You're welcome.

If you want to be able to access the Internet, select "NAT" as the network type, make sure the virtual cable is plugged in, and use DHCP in the VM. At least that's how I do it. :)

---

### Post by antharr on 2007-02-15
I am getting this error message. Has anyone else gotten this message or do you have any idea how to fix it?
VirtualBox kernel driver not installed.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by ghandi69_ on 2007-02-15
This thread is pretty much half devoted to that specific error.. I would read through the thread throughly, but basically you either need to get the old version of Virtual Box(what I did) or get some correct kernal header packages.

---

### Post by kiwidipstick on 2007-02-15
Thanks Ryan for this tutorial. I have the problem under your heading "Trouble Shooting". I followed through to remove using synaptic, but when I search in synaptic, I get the result Virtualbox in the left hand pane only. You cannot right click on it. I am stuck, as the icon for updating is still showing with the error message. Any other suggestions please.

---

### Post by bob-aptllc on 2007-02-22
Help needed! 

I tried to install virtualbox on Edgy and now my Synaptic won't display any packages. For error messages and description please refer to this thread: [http://ubuntuforums.org/showthread.php?t=367515](http://ubuntuforums.org/showthread.php?t=367515). 

Please help! Thanks!

---

### Post by John Jones on 2007-02-24
Hi there.

I tried your Howto, but the GDebi Package Installer comes up with "Error: Depency is not satisfiable: libc-dev".

I searched Synaptic Package Manager, which came up with several possiblities, none of which were called 'libc-dev'. The nearest was 'linux-libc-dev', which didn't make any difference.

Any thoughts, please?

John Jones

---

### Post by John Jones on 2007-02-24
> **John Jones said:**
> Hi there.

I tried your Howto, but the GDebi Package Installer comes up with "Error: Depency is not satisfiable: libc-dev".

I searched Synaptic Package Manager, which came up with several possiblities, none of which were called 'libc-dev'. The nearest was 'linux-libc-dev', which didn't make any difference.

Any thoughts, please?

John Jones

Hi again.

It occurred to me to Google libc-dev, and as a result, I ended up downloading 'libc6-dev' from the Debian website. When I tried to install this, I got a "dependency not satisfiable: libc6". So I downloaded 'libc6', also from the Debian website. When I tried to install this, I got a message telling me that a later version is already installed. :confused: 

I'm now way out of my depth, so I'm giving up pro-tem. I'd be delighted if some kind person could point me in the right direction, though.

Cheers again,

John Jones

---

### Post by John Jones on 2007-02-24
> **John Jones said:**
> Hi again.

It occurred to me to Google libc-dev, and as a result, I ended up downloading 'libc6-dev' from the Debian website. When I tried to install this, I got a "dependency not satisfiable: libc6". So I downloaded 'libc6', also from the Debian website. When I tried to install this, I got a message telling me that a later version is already installed. :confused: 

I'm now way out of my depth, so I'm giving up pro-tem. I'd be delighted if some kind person could point me in the right direction, though.

Cheers again,

John Jones

Hi again.

I've inadvertently solved the problem myself, by having a look at Qemu, which installed libc6-dev. Virtualbox has now installed without problems.

Thanks,

John Jones

---

### Post by cklinux on 2007-02-28
Hey, why say your guide isn't for Dapper? I have used it for dapper downloading the dapper package for virtualbox 1.3.6 and worked like a charm. Helped me a lot with the correct names of dependencies as in the site of virtualbox they had other names. Also noticed that you need to install a couple other things: linux-headers for your kernel and bridg-utils and uml-utilities. Also the Gdebi seems to take ages to install the package but it is because you have to expand the terminal and click on accept EULA. Now I am installing a windows 2000 box to use to convert my .pst and for other emergencies. BTW does anyone knows how to work multisync with Windows Mobile 2005 ? :offtopic: sorry I know but I haven't found anything helpfull. Thanx it is much simpler and smaller download than VMWare Server and itsn't a beta ;)

---

### Post by kodoku on 2007-03-03
Everyone,

Am I the only one getting random aborts with XP Pro in VirtualBox?  It seems whatever I do, whether surfing, watching videos or playing a game, VirtualBox would run incredibly smooth (much faster than VMWare), but then without warning whatsoever, it would abort.  This is incredibly annoying, as I have to restart the virtual machine almost all the time.  I installed VMWare server, and though it is much more sluggish, it is rock solid compared to VirtualBox, no crashes since installation....

---

### Post by kodoku on 2007-03-07
Nevermind, I uninstalled the premade deb and compiled the OSE version.  That one is rock solid

---

### Post by troymcdavis on 2007-03-11
First of all, fantastic how-to. Major props to the OP.

Forgive me if this has already been mentioned; I just skimmed the follow-ups. To do this in KDE without using the terminal, change the groups by going 

KMenu -> System Settings

That will open up the system settings window. Under the heading "Computer Administration" click "User Management". This opens up the user management in the same window. First, we need to be root to change anything, so click the "Administrator Mode..." button at the bottom right; it will prompt your for your password (as if you were using sudo). Click the "Groups" tab, then the group name vboxusers, then the "Modify..." just below it. On the left hand side, find your login, then click "Add ->". Click "Okay" then "Close" and follow the rest of the guide. You're good to go!

---

### Post by BirdZerk on 2007-03-13
I used the Howto and Virualbox installed with no errors.  I am now trying to install an OS from a cd and I keep getting the same error in the black background window,

> FATAL: No bootable medium found! System halted.

I tried both windows 2000 and xubuntu installation cd's and got the same message, any one know what is happening?

---

### Post by LookTJ on 2007-03-16
I have added myself to the vboxusers group.

Whenever I try to start a VM

I get:

> 
VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



---

### Post by OffHand on 2007-03-18
> **Taylor said:**
> I have added myself to the vboxusers group.

Whenever I try to start a VM

I get:

I get the same. The permission are lost after a reboot.
Any ideas?

---

### Post by tnreynolds on 2007-03-19
> **Taylor said:**
> I have added myself to the vboxusers group.

Whenever I try to start a VM

I get:

Ditto, adding myself to the vboxusers group seemed to have no effect.  I ended up just doing a 'sudo chmod a+rw /dev/vboxdrv' and it all worked out.

- Troy

---

### Post by OffHand on 2007-03-19
> **tnreynolds said:**
> Ditto, adding myself to the vboxusers group seemed to have no effect.  I ended up just doing a 'sudo chmod a+rw /dev/vboxdrv' and it all worked out.

- Troy

Me too. Weird issue. I get this error without setting permissions.

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by OffHand on 2007-03-19
> **tnreynolds said:**
> Ditto, adding myself to the vboxusers group seemed to have no effect.  I ended up just doing a 'sudo chmod a+rw /dev/vboxdrv' and it all worked out.

- Troy

Try this, it might work:

```
gksudo gedit /etc/udev/rules.d/60-vboxdrv.rules
```

And add:

KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", GROUP="vboxusers", MODE="0660"

---

### Post by scotttkd on 2007-03-19
got virtualbox working and running on my edgy laptop but need to print to networked printers that I have connected via samba.  I have not been able to find any info on how to do this.  any help would be greayly appreciated.

---

### Post by scotttkd on 2007-03-22
solved...vm needs to be bridged not NAT configuration.

---

### Post by .simon on 2007-03-23
Hi there,

Nice HowTo, I managed to get it on and working no problem by myself and I think it's quite good.

However, some help with USB and filesharing would be great!!

Because I've been trying to set-up USB and Fileshare for the last few days and it's starting to freak me out...

Cheers

Simon

---

### Post by Eldar11 on 2007-03-28
I followed the installation exactly, but when it is done, the program will not show up in the menu, is there any way to manually put it there? because I tried, but I could not find the program.

---

### Post by bodhi.zazen on 2007-03-28
To enable usb devices :

First you need to modify a configuration file :

use any editor you like (vim,nano, gedit)

I use vim ...

sudo vim (you can use gksudo gedit ...)

Edit (as root) **/etc/udev/rules.d/40-permissions.rules**

Change this line :

> SUBSYSTEM=="usb_device",              MODE="0664"

To :

> # Edited to enable USB devices with VirtualBox
# Original line commented out
# SUBSYSTEM=="usb_device",              MODE="0664"
SUBSYSTEM=="usb_device",              MODE="0666"

(the # comments out the first line in case you need to change the file back)

Now in virtual box, select your machine, select usb devices, enable, add usb devices.

Boot your virtual machine. On the bottom of the window is an icon to add usb devices to the virtual machine.

_Note_: The USB device can be used by either the virtual machine or the host, but not both at the same time. Your usb device will be unmounted when you boot the virtual machine by brute force, be prepared ...

---

### Post by mrmonday on 2007-04-05
Thankyou for your excellent howto, I now have edgy running nicely in virtualbox on edgy :p:D

You need to add an aditional reboot, after adding yourself to the virtualbox group.

---

### Post by Huet on 2007-04-06
Kind of a stupid question, but I'm stuck.

When I run the .deb package, it gets stuck at the Virtualbox Personal Use and Evaluation License (PUEL).  How do I get past this screen?  I've tried pressing enter, y, and mashing random buttons on my keyboard but nothing works.

---

### Post by Huet on 2007-04-06
Nevermind, some more keyboard mashing seemed to solve it.

---

### Post by vr6stress on 2007-04-08
i've got innotek installed and got xp up and running. but for this to really make it useful i need access to the drives in linux.

i've tried to follow the contents on section 5.4 about sharedfolders, but i can not get the hang of it...

this is the command i tried:
placido@placido-laptop:~$ VBoxManage sharedfolder add "winxp" -name /home/placido -hostpath "C:\placido"

that one gives me a:
VirtualBox Command Line Management Interface Version 1.3.8
(C) 2005-2007 InnoTek Systemberatung GmbH
All rights reserved.

[!] FAILED calling machine->CreateSharedFolder(Bstr(name), Bstr(hostpath)) at line 5533!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070057
[!] Text        = Shared folder path 'C:\placido' is not absolute
[!] Component   = SharedFolder, Interface: ISharedFolder, {8b0c5f70-9139-4f97-a421-64d5e9c335d5}
[!] Callee      = IMachine, {fd443ec1-0009-4f5b-9282-d72760a66916}

if i try it like this:
placido@placido-laptop:~$ VBoxManage sharedfolder add "winxp" -name /home/placido -hostpath "C:\placido_mnt\"

it doesn't stop, it just sits at >

so where am i going wrong? the documentation is a bit lite for a newb like me...

---

### Post by bodhi.zazen on 2007-04-09
Virtual Box

How to network :

[b]See here for details, including configuration at boot :

[http://doc.gwos.org/index.php/VirtualBox#Networking](http://doc.gwos.org/index.php/VirtualBox#Networking)[/b]

With the above how-to you will have network access, however you will not be able to make a connection between the host and virtual machine.

If you add a bridge (TAP) device, then each virtual machine will appear on your network as if it were hard wired. You can connect between host and virtual machines, but more important you can print and mount network shares.

OK, this involves some terminal stuff ....

Open a terminal and become root :

```
sudo -i
#Enter you log-in password
```

1. Install the necessary applications :

```
aptitude install uml-utilities bridge-utlis
```

2. kernel module : 

```
modprobe tun
```

3. Set permissions of tun device :
```
chomd 0666 /dev/net/tun
```

[color=red][size=4]**_NOTE_: During this step your network connection will go down. It will come back up as you finish, but you may want to print out these instructions[/size][/color]**

4.  Make a bridge and add you network interface to it :

**_Note_: In this example I use eth0, you will need to know you device and modify appropriately.**

To list your network interface(s), in a terminal type ```
ifconfig
```

OK, on to the bridge :

```
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
dhclient br0
```

5. Your internet connection should be back on line ....

6. Now add a tap device :

```
tunctl -t tap1 -u user_name
```

Change user_name to the user of the virtual machine.

7. configure tap device :

```
brctl addif br0 tap1

ifconfig tap1 up
```

Almost done ...

For the last part we are back to the gui ;)

Fire up Virtual box ...
Select your virtual machine ...

Click "Network" on the Right

Under Adapter 0, in the "Attached to" pull down menu select "Host Interface"
Under interface name type "tap1" (without quotes)

Save and exit ...

Now start you machine and you should be good to go :p

---

### Post by robtotheb on 2007-04-10
Is there a new to increase a .VDI file size?  I stupidly made mine too small and don't want to have to reinstall everything on a new VDI image.

---

### Post by raja on 2007-04-15
> **vr6stress said:**
> i've got innotek installed and got xp up and running. but for this to really make it useful i need access to the drives in linux.


this is the command i tried:
placido@placido-laptop:~$ VBoxManage sharedfolder add "winxp" -name /home/placido -hostpath "C:\placido"

I see you had made this post a few days back, so maybe you have solved it by now. If you havent, the correct command would be like this ```
VBoxManage sharedfolder add "winxp" -name mysharedfolder -hostpath "/home/placido"
```

The point is that the hostpath refers to the path to the shared folder in the host. And name is just any arbitrary name you set for the shared folder. When you mount the folder from windows you will be referring to it by this name.

---

### Post by jocheem67 on 2007-04-22
Can you please be more specific regarding the shared folders..

I installed virtualbox with a XP guest without problems.
Next I mounted the addons iso and installed it from within xp, no problems there.
I succesfully added the My SharedFolder from within ubuntu....

But heck...how do I let it show up in xp????

Thanks in advance!

Never mind , found it...got my home folder now visible within the virtual xp

the command was ( in xp ): net use E: \\vboxsvr\MySharedFolder..

One thing though: xp says connection lost whereas I can read and write??
Well, xp says a lot of things that aren 't true, huh??

Cheers

---

### Post by marx2k on 2007-04-23
I would like to install the VirtualBox guest Additions but have no idea where to download these??

---

### Post by hjlane3 on 2007-04-23
> **bodhi.zazen said:**
> Virtual Box

How to network :

[b]See here for details, including configuration at boot :

[http://doc.gwos.org/index.php/VirtualBox#Networking](http://doc.gwos.org/index.php/VirtualBox#Networking)[/b]

With the above how-to you will have network access, however you will not be able to make a connection between the host and virtual machine.

If you add a bridge (TAP) device, then each virtual machine will appear on your network as if it were hard wired. You can connect between host and virtual machines, but more important you can print and mount network shares.

OK, this involves some terminal stuff ....

Open a terminal and become root :

```
sudo -i
#Enter you log-in password
```

1. Install the necessary applications :

```
aptitude install uml-utilities bridge-utlis
```

2. kernel module : 

```
modprobe tun
```

3. Set permissions of tun device :
```
chomd 0666 /dev/net/tun
```

[color=red][size=4]**_NOTE_: During this step your network connection will go down. It will come back up as you finish, but you may want to print out these instructions[/size][/color]**

4.  Make a bridge and add you network interface to it :

**_Note_: In this example I use eth0, you will need to know you device and modify appropriately.**

To list your network interface(s), in a terminal type ```
ifconfig
```

OK, on to the bridge :

```
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
dhclient br0
```

5. Your internet connection should be back on line ....

6. Now add a tap device :

```
tunctl -t tap1 -u user_name
```

Change user_name to the user of the virtual machine.

7. configure tap device :

```
brctl addif br0 tap1

ifconfig tap1 up
```

Almost done ...

For the last part we are back to the gui ;)

Fire up Virtual box ...
Select your virtual machine ...

Click "Network" on the Right

Under Adapter 0, in the "Attached to" pull down menu select "Host Interface"
Under interface name type "tap1" (without quotes)

Save and exit ...

Now start you machine and you should be good to go :p


I've followed these instruction as well as every other instructions I could find to setup a bridge network with a tap device. And while things look good after doing so, and virtualbox starts up without complaint, my Windows XP guest always fails to get an IP from my network. =\

Any ideas about this?

---

### Post by bodhi.zazen on 2007-04-24
> **hjlane3 said:**
> I've followed these instruction as well as every other instructions I could find to setup a bridge network with a tap device. And while things look good after doing so, and virtualbox starts up without complaint, my Windows XP guest always fails to get an IP from my network. =\

Any ideas about this?

Heh, this could be complex to trouble shoot. Problem could be with your bridge, virtual box, windows, or your router.

So ...

1. Starting with the bridge, is it working ? type ```
ifconfig
``` In a terminal and you should see the bridge listed.

2. In Virtual Box, Select your virtual machine ...

Click "Network" on the Right

Under Adapter 0, in the "Attached to" pull down menu select "Host Interface"
Under interface name type "tap1" (without quotes)

Save and exit ...

Now start you machine and you see what you get.

3. If that fails you could try a Linux guest, like say DSL . If you get an IP with DSL then the problem is with windows.

4. I am not so good at windows networking, check the network settings on your windows guest against a working windows install ? Sorry, lame I know.

5. I would doubt a router problem, but could be. This would depend on the router of course...

---

### Post by hjlane3 on 2007-04-24
1) As far as I can tell the bridge is intact and working. I see the br0 device with the ip and use brctl to see that eth device and the tap device are bridged in br0.

2) Yup have the host interface setup just like that in virtualbox network config, as far as I can tel it's not a problem with my configurations.

3) Will try using a Linux guest once I get home.

4) Windows networking is setup right. I've tried with DHCP (in which case it sets a bogus IP at boot because it can't find one, then when I try to get it to ask for an IP again it sits there for a few mins then fails to update the IP. And I've tried setting up a static IP, with the correct IP and information for my 

5) I don't think there's anything wrong with my router setup, it's pretty basic. But i'll look into it.

Btw, here's something interesting: [http://bbs.archlinux.org/viewtopic.php?pid=227203#p227203](http://bbs.archlinux.org/viewtopic.php?pid=227203#p227203)

NetworkManager causing issues with bridge hosting?

---

### Post by hjlane3 on 2007-04-29
So yeah, I've tried with  a linux guest as well, no go.as well. I also tried disabling networkmanager and it's service too, and still no go.

It's like everything on host side looks completely correct, while guest side just can't get an IP, and even when I manually set an IP it still  wn't see a connections right.

---

### Post by bodhi.zazen on 2007-05-05
> **marx2k said:**
> I would like to install the VirtualBox guest Additions but have no idea where to download these??

:lolflag:

Marx2k: This was a real pain for me to solve ...

[http://doc.gwos.org/index.php/VirtualBox#Additions_.iso](http://doc.gwos.org/index.php/VirtualBox#Additions_.iso)

---

### Post by nyxynyx on 2007-05-07
wat keys did u bash to get past the screen in gdeb? im stuck there too lol help!

---

### Post by bodhi.zazen on 2007-05-07
> **nyxynyx said:**
> wat keys did u bash to get past the screen in gdeb? im stuck there too lol help!

Hmm ... not sure where you are getting stuck. I fall back to the CLI when the GUI fails.

Close gdeb/synatpic 

Open a terminal, cd into the directory where you keep the virtualbox .deb you downloaded (I suggest ~/src/VirtualBox):

```
sudo apt-get update
sudo apt-get install libxalan110 libxerces27
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_Edgy_x86.deb
```

* substitute the feisty package if you are on feisty ...

If you get error messages about unmet dependencies (and you likely will) :

```
sudo apt-get -f install
```

If that fails, post any error messages.

---

### Post by Jeff59 on 2007-05-12
You may want to add a note about getting USB devices to work running XP as guest.  I spent a few hours trying to get my External hard drive to show up in My Computer in XP.  Did not realize that not only do you need to have the USB device selected but you also need to have the "Mass Storage Device" selected.  Being somewhat of a newbie this was not intuitive.  Great How to.  Thanks

---

### Post by bodhi.zazen on 2007-06-06
VirtualBox 1.4 released today :

[Release annonucement](http://forums.virtualbox.org/viewtopic.php?t=323)

[Donwload](http://www.virtualbox.org/wiki/Downloads)

Keep in mind, in the update process it is advised to remove previous versions and then install the new version.

[http://doc.gwos.org/index.php/VirtualBox#Upgrading_VirtualBox](http://doc.gwos.org/index.php/VirtualBox#Upgrading_VirtualBox)

Innotek has added a repository for installing VirtualBox so installation should now be even easier (I have not worked through this yet, but I am working on updating the wiki).

New features include support for 64 bit processing.

> Jun 5, 2007. innotek today released VirtualBox 1.4.0 for Windows and Linux.

This new version brings hundreds of improvements, more than any update since the first official release in January 2007. Among the new features are full support for 64-bit Linux hosts, RDP session shadowing, clipboard synchronization and easier Linux host interface networking. In the storage department, VirtualBox now supports VMware disk images (VMDK) natively and can give virtual machines access to physical disks and partitions ("raw disk support"). The graphical user interface has received more polish and has now been translated into 12 languages (German, Spanish, French, Italian, Polish, Portuguese, Romanian, Arabic, Russian, Japanese, Traditional Chinese and Chinese). Red Hat Enterprise Linux 5 (RHEL5) and Xandros Desktop 4.1 are now officially supported; support for FreeBSD and OpenBSD guests has been improved.

---

### Post by mrazster on 2007-06-08
Just want to report back that 1.4.0 works like a charm...used this howto and it it's all fine. No glitches or problems what so ever.

Onlything left is to have 3D working so you can install a game and play... :p

---

### Post by michaeljt on 2007-06-12
Just some information for the maintainers of this howto: host interface networking has been revisited somewhat in VirtualBox 1.4.0, and the manual now contains Debian/Ubuntu-specific setup instructions which may save people some pain.
Regards, Michael

---

### Post by bodhi.zazen on 2007-06-12
> **michaeljt said:**
> Just some information for the maintainers of this howto: host interface networking has been revisited somewhat in VirtualBox 1.4.0, and the manual now contains Debian/Ubuntu-specific setup instructions which may save people some pain.
Regards, Michael

he he he ...

Well I am the only one maintaining documentation of VirtualBox. The original poster, Ryan Marcus, has not been active on Ubuntu and has not responded to my PM.

I am maintaining documentation here : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

I am trying to update the how to with the new release. The Network section is a mess right now, but the rest is in good shape.

I think I am going to revise the Networking section to include a basic bridge and links to external references.

The Networking section in the VirtualBox pdf is OK. It is fairly generic and for example I can not get the scripts to run as advertised.

I have received some help from a few others and any help anyone would like to offer is appreciated.

I could use some input from windows users. Is usb working on Windows(it was broken in 1.3.8) ? Is there anything special windows users must do to boot/run/install Ubuntu guests ? Networking tips/links.

Any feedback here is also appreciated.

~ Windows is my weak link and Virtual Box does not work on a Virtual Windows machine. I am willing to help, but draw the line at installing Windows ...

Thanks.

---

### Post by michaeljt on 2007-06-12
USB was certainly working on Windows, host and guest, in 1.3.x and in 1.4.0 (I know that doesn't really help those who are having trouble).  Booting Ubuntu guests can be a fiddly process - due to known bugs, Dapper Server, Edgy (Both) and Feisty Server do not boot reliably.  The Dapper and Edgy bugs have been fixed in the distributions (upgrade to the latest available kernels), but the fixes didn't make it onto the installation CDs unfortunately.  We are working on a workaround for the Feisty Server bug.

---

### Post by bodhi.zazen on 2007-06-12
> **michaeljt said:**
> USB was certainly working on Windows, host and guest, in 1.3.x and in 1.4.0 (I know that doesn't really help those who are having trouble).  Booting Ubuntu guests can be a fiddly process - due to known bugs, Dapper Server, Edgy (Both) and Feisty Server do not boot reliably.  The Dapper and Edgy bugs have been fixed in the distributions (upgrade to the latest available kernels), but the fixes didn't make it onto the installation CDs unfortunately.  We are working on a workaround for the Feisty Server bug.

LOL

The "problem" I had with virtualbox on 1.3.8 was through a friend. He installed the usb support during the installation of 1.3.8 and this interfered with his usb mouse/keyboard. When he rebooted he could not log into his box :(

He got a hold of some ps2 components, and removed VirtualBox.

---

### Post by Das Goat on 2007-06-12
Hey, I am sorry i am such an idiot, but I can not get Virtual Box to install because I can not accept the license agreement. Whether I do it GUI or through the terminal I come back to the same place. A 8bit like screen pops up wanting me to accept the license agreement, but I can't click <ok>

Surely I should be hitting something on the keyboard to say yes, but village idiot that I am i can't figure it out.

Please help your local village idiot. :(

---

### Post by bodhi.zazen on 2007-06-12
> **Das Goat said:**
> Hey, I am sorry i am such an idiot, but I can not get Virtual Box to install because I can not accept the license agreement. Whether I do it GUI or through the terminal I come back to the same place. A 8bit like screen pops up wanting me to accept the license agreement, but I can't click <ok>

Surely I should be hitting something on the keyboard to say yes, but village idiot that I am i can't figure it out.

Please help your local village idiot. :(

LOL

At that screen use the <Tab> key

Once OK is highlighted hit the <Enter> key 

:)

---

### Post by Das Goat on 2007-06-14
Ack! (like Bill the Cat)

ok, synaptics can not continue because Virtual Box did not finish.

Please tell the Village Idiot how to make it stop so I can start again.

---

### Post by Das Goat on 2007-06-14
Clairification:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it

this is what i can not get around.

---

### Post by bodhi.zazen on 2007-06-15
> **Das Goat said:**
> Ack! (like Bill the Cat)

ok, synaptics can not continue because Virtual Box did not finish.

Please tell the Village Idiot how to make it stop so I can start again.

LOL

I have seen this eror message appear typically after the installation process for virtualbox is aborted.

The only way I know of to clear this problem is to finish the installation of virtualbox.

So either use dpkg or synaptic and install virtualbox. You can then remove virtualbox if you like.

If you need further assistance, please what/how did you try to install virtualbox and what went wrong ?

---

### Post by myname on 2007-06-15
From one village idiot to another... When I could no longer get into Adept after trying to install virtual box, I had to reboot,

I then opened a terminal and entered in:

sudo dpkg --configure -a

This seemed to clear up the not being able to open adept.  Once I ran the above line, I kept the terminal opened, and typed:

sudo apt-get install virtualbox  from a console.  I was then able to answer the license agreement.

let me know if this helps.

--kevin

---

### Post by Das Goat on 2007-06-15
Thanks for the help. 

i did:  sudo dpkg --configure -a

No errors so I assume that worked. But I could not just click on the package and have it install. The Package manager said it thought the file was corrupted. I downloaded a new copy, but got the same message.

So.... i went back to the terminal, changed to the desktop directory and did:
sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb

The last thing the installer said:

Preparing to replace virtualbox 1.4.0-21864_Ubuntu_feisty (using virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb) ...
Unpacking replacement virtualbox ...
Setting up virtualbox (1.4.0-21864_Ubuntu_feisty) ...
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 

so i guess it is ok, right?

so, now what can i do with this thing? maybe run Quicken finally?

---

### Post by Das Goat on 2007-06-15
Well Wheeeee! Or I guess a more modern spelling would be Wii.........

So I made my first VM. I picked something easy (and something I sill had in my archive) and selected WinME.

Everything seems set up right, and i mounted the installation CD, but when I try to start the VM, I get this error message:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

ok, that makes sense. But I downloaded the manual, read half of it a skimmed the rest, but i don't see where I go to set this.

Could some kind citizen please point me in the right direction?

---

### Post by Das Goat on 2007-06-15
Ok, as a kludge (i hope I am using the term right) I tried launching as; sudo VirtualBox.

This time it let me launch the WinME VM, but there is no OS installed (obviously) 

the manual sore of seems to skip this step. I'm sure it is an over sight because the authors figure you know this part (Kind of like me and training new employees. "What do you mean you don't know how to do X?" I bet we would get along, only this time I am on the short end of the stick)

So i am staring at the black FATAL: no bootable medium found! System Halted.

I figure i need to tell the VM to boot to the CD, but how? the VM boot order is Floppy, CD ROM, Hard Disk

---

### Post by Das Goat on 2007-06-15
One last thing. I did see the F12 select boot device, but when I chose the CD-ROM, nothing happened except the FATAL error again.

---

### Post by bodhi.zazen on 2007-06-16
Nice ...

I agree regarding the virtualbox manual :)

Take a peek here : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

The networking section is a mess, but most of the rest is in good shape ;)

---

### Post by Das Goat on 2007-06-16
ok, perhaps i should title my posts "Tales from the Village Idiot"

When in doubt, do two things:

1) Re-Read the instructions, especially the instructions from the START of the post you are in (doh!) about adding yourself to the right group (Yes, all of those restarts really ARE required) and then the problem is solved.

2) Blame Microsoft! (hell, if you weren't before, why are you on Linux anyway?)

So, as my Lil' Village Idiot self, I thought about it, "Didn't I have a hell of a time before loading Win ME back when it was new because it had the nasty habit of only booting to itself on a clean install where it had control of everything?" so i think to my Idiot self, "I think you are right. Why don't you load something else?"

You can guess. I loaded Win 98 and Sha Zam! It works! Not that there wasn't errors (this is Windows after all) where I had to reset the VM like it says not to do (pull the plug out) but hey! What is a few reboots in a Win "bottle" after all?

So, bottom line my compatriots is that I got it to work. I can't do anything yet because I I have to figure out how to let the "bottle" talk to my wireless (good grief). But other wise it functions. On a plus note, i get to spend time remembering how windows 98 works. That should be worth something in the current job market....

Heh heh heh! Makes you pine away for XP doesn't it? Lordy, Lord!

Anyway, XP is next on my hit list. Unless I can figure out how to make the wireless work on Win98 (seems like a waste of time) I am one GREAT step forward in getting rid of WIN. Thank You all for the support. I couldn't have got this far with out your dedication to this project.

Das Goat

---

### Post by bodhi.zazen on 2007-06-16
> **Das Goat said:**
> ok, perhaps i should title my posts "Tales from the Village Idiot"

When in doubt, do two things:

1) Re-Read the instructions, especially the instructions from the START of the post you are in (doh!) about adding yourself to the right group (Yes, all of those restarts really ARE required) and then the problem is solved.

2) Blame Microsoft! (hell, if you weren't before, why are you on Linux anyway?)

LMAO !!!

Now time to clear my nose and clean the coffee off the monitor.

---

### Post by Das Goat on 2007-06-17
> **bodhi.zazen said:**
> LMAO !!!

Now time to clear my nose and clean the coffee off the monitor.

:-) Glad I could bring some humor to the thread. Hell, if you can't laugh at your errors sometimes, you are taking all of this too seriously.

:popcorn:

---

### Post by Das Goat on 2007-06-17
Ok, I have this little project (one of many).

What I have done, by trial and error, not by design, is to have TWO instances of Ubuntu installed on my laptop.
I needed to do this to get my wireless working correctly and I got tired of re-installing Ubuntu just so I could go back and say "nope that didn't work". So I hit on the "Two State Solution". (sounds like middle east policy, doesn't it?)

The first instance, I keep like a virgin with a chaperone. Nothing installed unless it has been vetted by the second instance. Here I keep all of the down load files and instructions 

The second instance is where I do all of the "here, try this, it is the answer to all of your problems". usually, but not always, that means re-installing Ubuntu.

So, what I would like to know is this: Now that I have successfully Virtual Box, and I have got an instance of Win98 loaded, should I stick with Win98 and go through the trouble of making the wireless work (probably a daunting task) or should I make an XP bottle? Since I only have so much room on my laptop drive, I will probably have to abandon my "Two State Solution".

So, for the record, what have other people had GOOD success at? I have seen in the documentation that someone claims to have gotten VISTA working in Virtual Box. They are truely brave. i would be happy with XP. Should I do it? Do I defile my "virgin" and make a second instance of XP in a bottle? Is there a way to grab my XP partition and "bottle" it with out killing my drive?

---

### Post by Weav on 2007-06-19
Is this tutorial still valid for Fiesty Fawn?

---

### Post by Das Goat on 2007-06-19
It was for me. 

I run Feisty Fawn 64 bit.

I was able to install an instance of Win98

I was NOT able to install an instance of WinME (blame microsoft)

I have not yet installed an instance of XP, but that is because i think i am out of room and I am waiting on some advice.

---

### Post by bodhi.zazen on 2007-06-20
> **Weav said:**
> Is this tutorial still valid for Fiesty Fawn?

NO

Innotec has added a repository for VirtualBox and this tutorial was written for vbox 1.3.8

Go here for more up to date information :

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

*Sorry the networking section is such a mess, but I am trying to clean it up a little. Other then tat the wiki is a decent source of information.

---

### Post by Das Goat on 2007-06-21
Huh? I don't understand.  Do you mean there is a new Virtual box?

---

### Post by Das Goat on 2007-06-21
Sorry, let me clairify:

I accidently nuked my Ubuntu (actually my whole system and all my back ups, but that is another story)

So, on re-install, I installed the virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb file I had downloaded before and used the instructions at the begining of this thread to set it up and it seems to have worked good.

So was the question "is this thread still valid?" or was it "is the instruction manual updated" or was it "Is there a new Virtual Box?"

---

### Post by bodhi.zazen on 2007-06-21
> **Das Goat said:**
> Sorry, let me clairify:

I accidently nuked my Ubuntu (actually my whole system and all my back ups, but that is another story)

So, on re-install, I installed the virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb file I had downloaded before and used the instructions at the begining of this thread to set it up and it seems to have worked good.

So was the question "is this thread still valid?" or was it "is the instruction manual updated" or was it "Is there a new Virtual Box?"

LOL, good question.

1. There is a new virtualbox. 1.4.0 is the most current version (unless you svn, but that is for another thread).

2. As is typical for Linux, there are multiple ways of installing. You can download the .deb from virtualbox and install, your can use automatix, or you can add the innotek repo to /etc/apt/sources.list.

3. No single was is "better". IMO adding the unnotek repo is easiest and this method will update virtualbox when a new version is available. Automatix of a single app seem over kill, but that is me. Automatix will also updte when a new version of virtualbox is available (or so I assume). If you want automatix support, please refer to thier forums. If you download the .deb you will have no automatic update.

Thus, IMO, this how to is depreciated in favor of adding innotek to your repositories. You are free to do maintain your system any way you like.

I am not the author of this thread. I have tried to contact the author with no response.

So I try to maintain : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

Anyone who would like to contribute to the wiki is welcome. If you would like, PM me with any updates or errors.

*I am not an employee of innotek nor an expert in vbox, networking, or even virtualization :twisted:

---

### Post by Das Goat on 2007-06-21
Weeeeee!

Ok, I am a Noob to Ubuntu. So often I don't do things right, some times I even blow up my whole system because "a little bit of knowledge is a very dangerous thing" and I am proof positive of that!

I added the resposititories (at least I think I did) by looking at the help file, but i installed Virtual Box by following the instructions on this page.

And it works! (tears in my eyes) It really works!

After totally blowing my system up by my own ignorance, I was able to install my favorite distro of WinXP (don't worry you MS police, I really do own several licenses, even if I load a composite version on XP that some one compiled that has ALL of your "fixes" bundled into one DVD so I don't have to spend hours rebuilding my PC just because you will not send me a one disk up date EVEN though I PAID for your fricking software) and it works in the Virtual Box program.

I want to cry I am so happy! It really is as easy as people say. Networking even works even though I am wireless with my laptop.

So I am going to work my Virtual XP distro as hard as I can, with the goal of giving up Windows all together.

Thank You Thank You Thank you! Everyone who has contributed to this thread. This has been the light at the end of the tunnel I have been praying for.

Lord help me if it is a train :-)

---

### Post by Das Goat on 2007-06-22
I read you manual on page [http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices](http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices)

my first question is: If I am reading this right, what I need to do is plug in my USB, then right click "Eject" the device, then start my VM?

the second question is, Why do i have to set the permissions in either method one or two? what am I doing and why weren't these set during installation? Does this apply to version 1.4?

Third question: The next section refers to sharing your home dir with your guest WinXP VM.  I followed your instructions, and I got no errors in the terminal adding the share to vbox, but WinXP couldn't find it. Is there a way to list vbox shares so I can a)verify it was created and b) make sure I am spelling it correctly?

---

### Post by Das Goat on 2007-06-22
Doh!

Again, try reading the instructions from the start..........

I still have those questions, but I believe I should be loading the VirturalBox Additions.iso first.

Ok, where is it? I can't find it in /etc/vbox/ and I can't find it on the Downloads page from innotek

---

### Post by bodhi.zazen on 2007-06-22
LOL Das Goat :twisted:

KEEP READING ;)

OK, one thing at a time ...

1. For shared folders you need to use the additions.iso. Check out the additions section.

The additions iso is at : /opt/VirtualBox-1.4.0/additions/VBoxGuestAdditions.iso

2. After add the additions, reboot your guest, and use "net use ..."


==============

The USB is a little buggy. If you share the USB, do not Eject  it first. HOWEVER ... when you boot your guest OS it will yank the USB from your host and give it to the guest. When you close the guest it will return it to the host. So both can not access the USB at the same time ...

In terms of the permissions, you are changing who has permissions to access the raw device (thus allowing virtualbox to access the device). This is a (potential) minor security hole so it is not the default configuration at installation.

HTH

---

### Post by Das Goat on 2007-06-23
Wheee! Wheee! Wheee!

I kiss you in most European Way!

Why doesn't Unbuntu come this way set up?

Mien Got! I think I will wet my self! I am truely so excited. You have done more for me this past week than anyone has done for me in 9 months of trying to convert to Ubuntu.

Don't get me wrong. The journey has been worth every step so that i have a clue what the hell I am doing, but the five posts you have given me have done more for my productivity than the last 9 months wandering in the wilderness combined. (excluding CompWiz's wireless manual, which I couldn't even start if i didn't have, stupid broadcom hardware)

Thank You, Thank You, Thank You!

:popcorn:

---

### Post by Spccowboy on 2007-06-23
Anybody know how to make virtualbox run of an exsting windows partition?

---

### Post by bodhi.zazen on 2007-06-23
> **Spccowboy said:**
> Anybody know how to make virtualbox run of an exsting windows partition?

At this time no. Probably not in the near future as the emulated hardware is different from your actual hardware ...

BUT you can convert your windows install into a virtual machine that will run on VBox :

[http://doc.gwos.org/index.php/VirtualBox#Convert_.28Migrate.29_your_Windows_Insallation](http://doc.gwos.org/index.php/VirtualBox#Convert_.28Migrate.29_your_Windows_Insallation)

---

### Post by Spccowboy on 2007-06-24
> **bodhi.zazen said:**
> At this time no. Probably not in the near future as the emulated hardware is different from your actual hardware ...

BUT you can convert your windows install into a virtual machine that will run on VBox :

[http://doc.gwos.org/index.php/VirtualBox#Convert_.28Migrate.29_your_Windows_Insallation](http://doc.gwos.org/index.php/VirtualBox#Convert_.28Migrate.29_your_Windows_Insallation)


Thanks, I'm out of town, but I'll give that a try when i get back.

---

### Post by Das Goat on 2007-06-24
So far, I am so happy. 

One thing if you could, can you explain what I am doing when I follow the instructions for enabling a UBS device? I am a little spooked when it says that you can delete the whole UBS device if you do it wrong.

Will both device have control over the stick (what I am most concerned about)? Is this what I have to be careful of?  Will the device be "seen" by both Ubunut and Windows?  If so, do i need to eject it from both OS before I remove it? The instructions are not clear.

Thanks!

---

### Post by bodhi.zazen on 2007-06-25
> **Das Goat said:**
> So far, I am so happy. 

One thing if you could, can you explain what I am doing when I follow the instructions for enabling a UBS device? I am a little spooked when it says that you can delete the whole UBS device if you do it wrong.

Will both device have control over the stick (what I am most concerned about)? Is this what I have to be careful of?  Will the device be "seen" by both Ubunut and Windows?  If so, do i need to eject it from both OS before I remove it? The instructions are not clear.

Thanks!

Hmmm ...

To use usb devices ...

Leave them mounted on the host.

When the guest is booted, any shared usb device will be removed from control by the host, forced unmount if you will. Unsaved data will be lost (Normally, Linux saves data when you unmount or eject a usb device ; this is the part that does not happen when the device is turned over to the guest).

The device will the be available to the guest OS.

A usb device can not be used by both guest and host at the same time.

When you close the guest, the usb device will be available to the host again.

HTH

---

### Post by SpiritIsReality on 2007-09-07
howdy

thanks all, for the howto and thread

trails

---

### Post by theboomboomcars on 2007-09-26
Thanks for all the info, i was able to install a linux VM, but when I try to install WinXP it BSODs.  Which is an improvement from not trying to boot the cd at all.

---

### Post by antisocialist on 2007-10-09
> **Ryan Marcus said:**
> I did not mean for this guide to be used by Dapper users. It is met for Edgy users, as stated in the guide.

it works just fine for fiesty

---

### Post by jodoj80 on 2007-10-10
I want to know if this HOWTO works for the feisty distribution. In my case, when I press right click and select Open with "GDebi Package Installer" the installation crash. The error that appears is 

[IMG]http://mail.google.com/mail/?ui=1&realattid=file0&attid=0.1&disp=thd&view=att&th=11589b1c2d5e0aa3[/IMG]
If you want to see the picture, please made a SAVE AS to get the high resolution. I'll appreciate you help

---

### Post by bodhi.zazen on 2007-10-10
IMO most of the How-to's on Virtualbox are somewhat outdated.

Virtualbox has been in heave development and there was an initial burst of how-to's on the web, including this one.

Innotek maintains a repo for VirtualBox and the best way to install is to add the repo and then use synpatic or apt-get.

See here : [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by gunksta on 2008-02-12
Thanks for all the info. I am looking to instal virtualbox on a Kubuntu install so I can run a few needed (DANG!) Windows applications.

All I have are the reinstall CD's that came with the laptop. It's not the world's newest laptop (Dell Latitude D600) with 512 MB of RAM. I have accepted the fact that it will probably run a little slow when I virtualize things.

That's OK. I'll live with it.

I want to know if I can use the reinstall CD from Dell to install XP Professional onto Virtualbox. This is a work computer so I'd like to be fairly certain of success before committing to the Kubuntu installation.

The driver CD is separate and I don't think I'll need it to use the virtualized hardware but I don't know if Virtualbox can handle the Dell reinstall CD or if I need to use a standard Windows install CD. I have a legal copy of what appears to be Windows Server 2000 which is no longer in use so I could use that, but I'd rather use XP so I can more easily upgrade certain MS Office components.

Thanks!

---

### Post by theboomboomcars on 2008-02-13
You probably will not be able to use the CD that came with your computer, it checks to make sure the computer is a Dell before it will install, instead of asking for a product code, the information it is looking for is programmed on a chip on the Motherboard.  Since the Hardware in a VM is virtualized it won't find what it is looking for.  

Have you tried wine to run your programs?

---

### Post by gunksta on 2008-02-14
Yeah, Access 2003 doesn't like Wine very much. According to this page on [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9717&iTestingId=17323"), Access 2003 has a bad tendency to crash when you do menial things like . . . create a new database. It installs. It "runs" but I don't think it's at a useable level yet.

I decided to go ahead and partition my hard drive and reboot into XP if I need to use Access, etc. Otherwise, For 90% of my work, I'll be able to use Kubuntu. When someone sends me a file that I have to use Office 2003 to open, I'm one quick reset away.

Maybe I'll be able to get virtualization up and running when the company buys me a new machine.

---

### Post by theboomboomcars on 2008-02-14
If it's a work machine they might have a regular WinXP disc that you could use.

---

### Post by startling on 2008-03-28
> **bodhi.zazen said:**
> 

Innotek maintains a repo for VirtualBox and the best way to install is to add the repo and then use synpatic or apt-get.

See here : [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

I tried adding the repo but kept getting the error:
W: GPG error: [http://www.virtualbox.org](http://www.virtualbox.org) feisty Release: The following signatures couldn't be verified because the public key is not available

I'm sorry, but I have no idea what that means nor how to solve the error.

---

### Post by Browser_ice on 2008-04-16
What if I want to set it up to use a fixed amount of diskspace and that diskspace is a partition I create to be used by my VM O/S ?

Would choosing fixed size allow me to point to that partition and use it ?

Or do I have to do something else ?

---

### Post by michaeljt on 2008-04-16
> **Browser_ice said:**
> What if I want to set it up to use a fixed amount of diskspace and that diskspace is a partition I create to be used by my VM O/S ?

Would choosing fixed size allow me to point to that partition and use it ?

Or do I have to do something else ?

You can set up VirtualBox to run off a partition (see the user manual at [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)), but it is not really recommended for "normal use", as it is easy to get it wrong and dammage your host system.

---

### Post by 73ckn797 on 2008-10-19
> **bodhi.zazen said:**
> IMO most of the How-to's on Virtualbox are somewhat outdated.

Virtualbox has been in heave development and there was an initial burst of how-to's on the web, including this one.

Innotek maintains a repo for VirtualBox and the best way to install is to add the repo and then use synpatic or apt-get.

See here : [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

I am wanting to install Virtual Box in Hardy. I have followed the info to download:
[http://ubuntuforums.org/showthread.php?t=582729](http://ubuntuforums.org/showthread.php?t=582729) and read your post and followed your link to their site.

I noticed on their web site that they have several options for download.
These were downloaded:
Installed the following packages:
libqt4-core (4.3.4-0ubuntu3)
libqt4-gui (4.3.4-0ubuntu3)
linux-image-2.6.24-19-virtual (2.6.24-19.41)
virtualbox-2.0 (2.0.2-36488_Ubuntu_hardy)
virtualbox-ose-guest-modules-2.6.24-19-generic (24.0.4)

Does this appear correct or will any of it mess me up? The system wants to reboot but I am concerned that the kernel has been changed. If so, will that be anything that will allow VB to work properly or Hardy to not work?

---

### Post by bodhi.zazen on 2008-10-19
> **73ckn797 said:**
> I am wanting to install Virtual Box in Hardy. I have followed the info to download:
[http://ubuntuforums.org/showthread.php?t=582729](http://ubuntuforums.org/showthread.php?t=582729) and read your post and followed your link to their site.

I noticed on their web site that they have several options for download.
These were downloaded:
Installed the following packages:
libqt4-core (4.3.4-0ubuntu3)
libqt4-gui (4.3.4-0ubuntu3)
linux-image-2.6.24-19-virtual (2.6.24-19.41)
virtualbox-2.0 (2.0.2-36488_Ubuntu_hardy)
virtualbox-ose-guest-modules-2.6.24-19-generic (24.0.4)

Does this appear correct or will any of it mess me up? The system wants to reboot but I am concerned that the kernel has been changed. If so, will that be anything that will allow VB to work properly or Hardy to not work?

I have not installed VirtualBox in a while, I use OpenVZ and KVM nowadays.

I do not see anything overtly wrong with the information you posted.

---

### Post by 73ckn797 on 2008-10-19
> **bodhi.zazen said:**
> I have not installed VirtualBox in a while, I use OpenVZ and KVM nowadays.

I do not see anything overtly wrong with the information you posted.

Installation went flawlessly.

There are only 2 programs that I really need XP for since they would not work in WINE.

Thanks for the input.

---

