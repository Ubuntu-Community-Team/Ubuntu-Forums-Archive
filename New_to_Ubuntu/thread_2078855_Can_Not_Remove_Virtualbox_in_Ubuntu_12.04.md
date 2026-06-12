---
title: "Can Not Remove Virtualbox in Ubuntu 12.04"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Jeffreytooker on 2012-10-31
I have been searching all day trying to get Virtualbox running in 12.04.  I am needing to remove Virtualbox 4.2.4.2 for Windows (I know stupid mistake) from 12.04.  I will then install the proper Virtualbox package for 12.04.  These packages are from the Oracle site for Virtualbox downloads.  I have removed all Virtualbox applications with both Ubuntu Software and Synaptic.  Synaptic says no Virtualbox packages installed.  An Icon for Virtualbox still exists in Dash/installed programs.  This icon opens 4.2 and it does not work because it is a Win package.  I can do a bit of command line cut and paste with proper code.  How do I uninstall Virtualbox which is still installed, when Synaptic says it is not installed?

Jeffrey

---

### Post by newb85 on 2012-10-31
How did you manage to install VirtualBox for Windows on Ubuntu?

---

### Post by Jeffreytooker on 2012-11-01
As I said above stupid mistake.  I was thinking it was for my Win computer, not the Ubuntu software.  At 70 some things do not  work as well as they use to.  In thinking about it the Virtualbox must be downloaded where synaptic can not find it.  I guess there should be a path, but I do not know how to find it.  I may look more tomorrow.

Jeffrey

---

### Post by newb85 on 2012-11-01
My last post was an actual question, not an expression of wonder meant to belittle you.  It's not possible to install VirtualBox for Windows on Linux without also using an abstraction layer or an emulator.  That's what I was getting at.

---

### Post by cyb0rgb0rg on 2012-11-01
Could it be that it was handled by wine? In that case, could it be an uninstaller present? I'm not familiar with VirtualBox, so this is just on the top of my head.

---

### Post by Isamu715 on 2012-11-01
If it was handled by Wine(and if it's the Windows version it probably was) you should be able to remove it using the Wine application uninstaller. Search for "wine" in the dash and there should be an entry called "Uninstall Wine Applications". There's a chance your  Virtualbox install is present there.

---

### Post by NikTh on 2012-11-01
Hi , 

please open a terminal (CTRL+ATL+T) and give the results of bellow commands. 
You can copy-paste the commands from here to terminal and vice-versa (for the results).

```
dpkg -l | grep -i virtualbox
dpkg -l | grep -i wine
lsb_release -rcd ; uname -r
```Above results will give us informations about what packages are installed in your system relating to virtualbox - wine and also give us the informations of your system's version and kernel. 

Put the results between these brackets **[noparse]```
here
```[/noparse]** in order to be easier to read.

Thanks

---

### Post by Jeffreytooker on 2012-11-01
> **NikTh said:**
> Hi , 

please open a terminal (CTRL+ATL+T) and give the results of bellow commands. 
You can copy-paste the commands from here to terminal and vice-versa (for the results).

```
dpkg -l | grep -i virtualbox
dpkg -l | grep -i wine
lsb_release -rcd ; uname -r
```Above results will give us informations about what packages are installed in your system relating to virtualbox - wine and also give us the informations of your system's version and kernel. 

Put the results between these brackets **[noparse][      **jeffrey@jeffrey-desktop:~$ dpkg -l | grep -i virtualbox 
 rc  virtualbox-ose                                4.1.12-dfsg-2ubuntu0.1                          transitional package for virtualbox 
 rc  virtualbox-qt                                 4.1.12-dfsg-2ubuntu0.1                          x86 virtualization solution - Qt based user interface 
 jeffrey@jeffrey-desktop:~$  
 

 

 

 jeffrey@jeffrey-desktop:~$ dpkg -l | grep -i wine 
 ii  gnome-exe-thumbnailer                         0.9-0ubuntu1                                    Wine .exe and other executable thumbnailer for Gnome 
 ii  wine                                          1.4-0ubuntu4.1                                  Microsoft Windows Compatibility Layer (meta-package) 
 ii  wine-gecko1.4                                 1.4.0-0ubuntu2                                  Microsoft Windows compatibility layer (embedded web browser) 
 rc  wine1.2                                       1.4-0ubuntu4.1                                  Microsoft Windows Compatibility Layer (transitional package) 
 ii  wine1.4                                       1.4-0ubuntu4.1                                  Microsoft Windows Compatibility Layer (Binary Emulator and Library) 
 ii  wine1.4-common                                1.4-0ubuntu4.1                                  Microsoft Windows Compatibility Layer (transitional package) 
 ii  wine1.4-i386                                  1.4-0ubuntu4.1                                  Microsoft Windows Compatibility Layer (32-bit support) 
 ii  winetricks                                    0.0+20120308                                    Microsoft Windows Compatibility Layer (winetricks) 
 jeffrey@jeffrey-desktop:~$  
  
 

 

 jeffrey@jeffrey-desktop:~$ lsb_release -rcd ; uname -r 
 Description:    Ubuntu 12.04.1 LTS 
 Release:    12.04 
 Codename:    precise 
 3.2.0-32-generic-pae 
 jeffrey@jeffrey-desktop:~$  
  **    ]here[/code][/noparse]** in order to be easier to read.

Thanks

Results posted above.  All references in code above refer to Virtualbox 4.1.  The Virtualbox that keeps coming up is 4.2.  I checked this in the "About Virtualbox"  when program comes up.  It is still doing it this morning.  I have the proper Virtualbox 4.2 sitting in downloads.  My idea is to remove all old Virtualbox data in system then load the proper one.  In my research yesterday the first problem seems to be getting all old Virtualbox data removed.  I found several posts on this issue.  I would like to be able to remove all Virtualbox data be it 4.1 or 4.2.  In Synaptic PM I find only one entry for 4.2.  When I go to Synaptic/status/not installed, all of th 4.1 and the 4.2 files show up.

Jeffrey

---

### Post by NikTh on 2012-11-01
If I understood correctly , you have wine and you want to install virtualbox through wine ? If yes, then this is the wrong way. 

If I understood wrong and you want to install VB 4.2.4 (the latest version) then you have to purge first the old VB with this command

```
sudo apt-get purge virtualbox*
``` 
and then goto Oracle's website and download the latest version 
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

and install it through synaptic or Ubuntu Software Center. 

Thanks

---

### Post by CharlesA on 2012-11-01
virtualbox.org has better instructions, but it looks like it is down atm, so you can use the link in the previous post to install 4.2.4.

---

### Post by NikTh on 2012-11-01
> **CharlesA said:**
> virtualbox.org has better instructions, but it looks like it is down atm, so you can use the link in the previous post to install 4.2.4.

Yes CharlesA , I noticed that. I don't know why but is down for now , so I gave the alternate link. :)

---

### Post by CharlesA on 2012-11-01
> **NikTh said:**
> Yes CharlesA , I noticed that. I don't know why but is down for now , so I gave the alternate link. :)
I know it's happened before, but it looks like only the website is down, because download.virtualbox.org works fine.

They'll probably get it fixed shortly. :)

---

### Post by rburkartjo on 2012-11-01
jef if you havent gotten your problem fixed. try this open a terminal and type the following in order
[http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html](http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html)

the problem might be that virtual box likes to start up automatically and therefore hard to remove. you can reinstall wine later.

---

### Post by Jeffreytooker on 2012-11-01
In reading about removal of programs, mostly Synaptic and Ubuntu Software, it seems there are some terminology problems.  To me "add or remove programs", means adding or removing programs to the library of the installed operating system.  In this case the Operating System is Ubuntu 12.04, and the  "library" is the "all software" in Ubuntu Software.  The installed software is on the "installed" list in Ubuntu Software.  It is installed in 12.04.

I presently have a lot of Virtualbox 12.1 software on the "All Software" list in "Ubuntu Software" that I want to completely remove from "Ubuntu Software"  When I go to the "Remove" instructions in "Ubuntu Software"  They want me to choose an item from the "Installed" list to remove.  In removing from the "Installed" list, I am actually "Uninstalling" the program, from the Operating System, and NOT removing it from the "All Software" list of "Ubuntu Software".  

This is important to Virtualbox, because in the instructions for installing Virtualbox 4.2 it says to "remove" not "uninstall" all previous Virtualbox software.  It seems that there is a conflict between the old and the new.  This is why all of the old has to be completely removed, not just uninstalled.  I have read the instructions in both Synaptic and Ubuntu Software, and I am unable to fully remove the Virtualbox software from the Ubuntu 12.04 operating system.  How do I fully remove the 4.1 software from Ubuntu 12.04?

I am beginning to believe that with all 4.1 software fully removed from the O/S the proper 4.2 package will operate correctly.

Jeffrey

---

### Post by NM5TF on 2012-11-01
I think that NickTH gave you the command you need on page #1...

did you try that yet???:rolleyes:

here is the command again

```
sudo apt-get purge virtualbox*
```

FWIW.....I have been using VBox for a couple of months now & love it...:P

running Win XP Pro under Ubuntu 12.04 because my employer requires that
I take on-line H & S training that ONLY works under IE 8....

I have noticed that Win XP loads & runs faster/better than it ever did
stand-alone......:biggrin:

after you purge the old VB, go to Oracle's site & download the CORRECT
version for your hardware...and then be certain to download the add-ons
that will allow you to use any USB devices you might need...like a printer
for instance...be sure to download the correct addon version for the version of VB that you are using...

the info is on Oracle's site...when it comes back up....go here:

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

good luck,

Tommy

---

### Post by Jeffreytooker on 2012-11-01
> **NM5TF said:**
> I think that NickTH gave you the command you need on page #1...

did you try that yet???:rolleyes:


that will allow you to use any USB devices you might need...like a printer
for instance...be sure to download the correct addon version for the version of VB that you are using...

the info is on Oracle's site...when it comes back up....go here:

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

good luck,

Tommy
   

NikTH and Tommy:  

NikTH:  Not loading through Wine.  Latest VB correct.

I was writing reply when power went out, computer died, XXXXXXX!!!!  So here we go again.


jeffrey@jeffrey-desktop:~$ sudo apt-get purge virtualbox*
[sudo] password for jeffrey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'virtualbox-dbg' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-x11' for regex 'virtualbox*'
Note, selecting 'virtualbox' for regex 'virtualbox*'
Note, selecting 'virtualbox-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-x11' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.2' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.2' for regex 'virtualbox*'
Note, selecting 'virtualbox-4.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-4.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-4.2' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-utils' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-additions-iso' for regex 'virtualbox*'
Note, selecting 'virtualbox-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-additions' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-qt' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-dbg' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-fuse' for regex 'virtualbox*'
Note, selecting 'virtualbox-qt' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-fuse' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-utils' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-dkms' for regex 'virtualbox*'
Package virtualbox-guest-additions is not installed, so not removed
Package virtualbox-guest-additions-iso is not installed, so not removed
Package virtualbox is not installed, so not removed
Package virtualbox-dbg is not installed, so not removed
Package virtualbox-dkms is not installed, so not removed
Package virtualbox-fuse is not installed, so not removed
Package virtualbox-guest-dkms is not installed, so not removed
Package virtualbox-guest-source is not installed, so not removed
Package virtualbox-guest-utils is not installed, so not removed
Package virtualbox-guest-x11 is not installed, so not removed
Package virtualbox-ose is not installed, so not removed
Package virtualbox-ose-dbg is not installed, so not removed
Package virtualbox-ose-dkms is not installed, so not removed
Package virtualbox-ose-fuse is not installed, so not removed
Package virtualbox-ose-guest-dkms is not installed, so not removed
Package virtualbox-ose-guest-source is not installed, so not removed
Package virtualbox-ose-guest-utils is not installed, so not removed
Package virtualbox-ose-guest-x11 is not installed, so not removed
Package virtualbox-ose-qt is not installed, so not removed
Package virtualbox-ose-source is not installed, so not removed
Package virtualbox-qt is not installed, so not removed
Package virtualbox-source is not installed, so not removed
Package virtualbox-4.1 is not installed, so not removed
Package virtualbox-4.2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgsoap1 update-manager-kde
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeffrey@jeffrey-desktop:~$ 


The problem seems to be that Purge will not remove VB if it is not installed.  VB 4.2 instructions say to totally remove from O/S (Ubuntu 12.04) all previous VB data.  We know it is there.  How do we get it out?

Tommy:
I will load the USB also as the point of this whole thing is to get an XP VB so I can run my HP all in one to full capacity, which I can not do in 12.04.  I also have a few Win Specific programs I need to run.

Jeffrey

---

### Post by NM5TF on 2012-11-01
open your Home folder & go to "View" at the top bar....
select "view hidden files"

you should see a Folder named VirtualBoxvms...this folder contains
the "guest OS" in a .vdi file format

you will also see a folder named .VirtualBox...this folder contains
the VB files needed to run it....

from another thread they say this works....try it and let us know

```
sudo apt-get remove virtualbox* --purge
```

that should remove the entire VB kernel & all files....

then reinstall the "new" VB & the guest additions from the Oracle site
to be able to use your HP printer within the VB....the page I directed
you to will explain how to set up the USB filter....

as an aside....I also have a HP F4180 all in one that works flawlessly under Ubuntu 12.04 as well as under the VB.....what problems are you having
trying it under 12.04???


Tommy

---

### Post by newb85 on 2012-11-01
> **Jeffreytooker said:**
> In reading about removal of programs, mostly Synaptic and Ubuntu Software, it seems there are some terminology problems.  To me "add or remove programs", means adding or removing programs to the library of the installed operating system.  In this case the Operating System is Ubuntu 12.04, and the  "library" is the "all software" in Ubuntu Software.  The installed software is on the "installed" list in Ubuntu Software.  It is installed in 12.04.

I presently have a lot of Virtualbox 12.1 software on the "All Software" list in "Ubuntu Software" that I want to completely remove from "Ubuntu Software"  When I go to the "Remove" instructions in "Ubuntu Software"  They want me to choose an item from the "Installed" list to remove.  In removing from the "Installed" list, I am actually "Uninstalling" the program, from the Operating System, and NOT removing it from the "All Software" list of "Ubuntu Software".  


The software shown in "All Software" in the Software Center is all the software available to you in the repositories you have set up and enabled on your machine.  If you add another repository, it will make more/newer software available, but it will not "add/remove" or install software.  Installing involves downloading the software from the repository and then running dpkg to set the software up (all done automatically by apt-get when you choose to install something).

When someone tells you to "remove" software like VB from your system, it does [i]not[/] mean you have to remove it from the list of available software.

---

### Post by Jeffreytooker on 2012-11-01
> **NM5TF said:**
> open your Home folder & go to "View" at the top bar....
select "view hidden files"


then reinstall the "new" VB & the guest additions from the Oracle site
to be able to use your HP printer within the VB....the page I directed
you to will explain how to set up the USB filter....

as an aside....I also have a HP F4180 all in one that works flawlessly under Ubuntu 12.04 as well as under the VB.....what problems are you having
trying it under 12.04???


Tommy

Tommy: 

Tried your command.  Results same as before:

jeffrey@jeffrey-desktop:~$ sudo apt-get remove virtualbox* --purge
[sudo] password for jeffrey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'virtualbox-dbg' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-x11' for regex 'virtualbox*'
Note, selecting 'virtualbox' for regex 'virtualbox*'
Note, selecting 'virtualbox-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-x11' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.2' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.2' for regex 'virtualbox*'
Note, selecting 'virtualbox-4.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-4.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-4.2' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-utils' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-additions-iso' for regex 'virtualbox*'
Note, selecting 'virtualbox-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-additions' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-qt' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-dbg' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-fuse' for regex 'virtualbox*'
Note, selecting 'virtualbox-qt' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-fuse' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-utils' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-dkms' for regex 'virtualbox*'
Package virtualbox-guest-additions is not installed, so not removed
Package virtualbox-guest-additions-iso is not installed, so not removed
Package virtualbox is not installed, so not removed
Package virtualbox-dbg is not installed, so not removed
Package virtualbox-dkms is not installed, so not removed
Package virtualbox-fuse is not installed, so not removed
Package virtualbox-guest-dkms is not installed, so not removed
Package virtualbox-guest-source is not installed, so not removed
Package virtualbox-guest-utils is not installed, so not removed
Package virtualbox-guest-x11 is not installed, so not removed
Package virtualbox-ose is not installed, so not removed
Package virtualbox-ose-dbg is not installed, so not removed
Package virtualbox-ose-dkms is not installed, so not removed
Package virtualbox-ose-fuse is not installed, so not removed
Package virtualbox-ose-guest-dkms is not installed, so not removed
Package virtualbox-ose-guest-source is not installed, so not removed
Package virtualbox-ose-guest-utils is not installed, so not removed
Package virtualbox-ose-guest-x11 is not installed, so not removed
Package virtualbox-ose-qt is not installed, so not removed
Package virtualbox-ose-source is not installed, so not removed
Package virtualbox-qt is not installed, so not removed
Package virtualbox-source is not installed, so not removed
Package virtualbox-4.1 is not installed, so not removed
Package virtualbox-4.2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgsoap1 update-manager-kde
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeffrey@jeffrey-desktop:~$ 

In addition to the problem of removing packages because we need to, we cant remove them and we should be able to.  That in itself is a problem.



Newb85:

I would tend to agree, however after a lot of searching yesterday the crux of th issue seems to be that just "uninstalling" still leaves some kind of conflict.  So the advice seems to completely remove.  Keeping VB 4.1 on board serves no purpose.  It should be able to be removed.  So how?  You are not being ignored.  In most cases I would say you are correct.

Thank you.

Jeffrey

---

### Post by NM5TF on 2012-11-01
hmmmmmmmmmmmmmm....interesting...

do you still have the VB folders in your Home directory???

if so, then try removing them....use shift + delete to do it

weird that the apt-get remove cmd  says they are not installed,
but you say they are still there....how do you know this???

I searched for "virtual box" both in Synaptic & Ubuntu software 
center but it came up with no choices....I installed my version 
directly from the Oracle download site...

here are the results of some codes I ran....

tommy2@tommy-Inspiron-531s:~$ dpkg -l | grep -i virtualbox
ii  virtualbox-4.1                         4.1.22-80657~Ubuntu~precise             Oracle VM VirtualBox
tommy2@tommy-Inspiron-531s:~$ lsb_release -rcd ; uname -r
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
3.2.0-32-generic

your version of VB seems to be different.....is your hardware 32 bit or 64bit???

---

### Post by Jeffreytooker on 2012-11-01
> **NM5TF said:**
> hmmmmmmmmmmmmmm....interesting...

do you still have the VB folders in your Home directory???

if so, then try removing them....use shift + delete to do it

weird that the apt-get remove cmd  says they are not installed,
but you say they are still there....how do you know this???

I searched for "virtual box" both in Synaptic & Ubuntu software 
center but it came up with no choices....I installed my version 
directly from the Oracle download site...

here are the results of some codes I ran....

tommy2@tommy-Inspiron-531s:~$ dpkg -l | grep -i virtualbox


ii  virtualbox-4.1                         4.1.22-80657~Ubuntu~precise             Oracle VM VirtualBox
tommy2@tommy-Inspiron-531s:~$ lsb_release -rcd ; uname -r
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
3.2.0-32-generic

your version of VB seems to be different.....is your hardware 32 bit or 64bit???


Files above removed as directed.  Also removed VB in C Prog files as a flag said Ubuntu was picking up a file in C/users/Jeffrey of my Windows HDD.  Two seperate HDD's, boot Ubuntu in second HDD from BIOS.  Ubuntu has access to Win HDD C.  Still nothing changed.  Finally found four VB files in: Home Folder/file system/etc/init.d/vbox.  Tried to remove the four files with shift delete.  No joy.  How does one do it.  These files were found under VB 4.2.  Under VB 4.1 I found none.

Jeffrey

---

### Post by Jeffreytooker on 2012-11-01
> **Jeffreytooker said:**
> Files above removed as directed.  Also removed VB in C Prog files as a flag said Ubuntu was picking up a file in C/users/Jeffrey of my Windows HDD.  Two seperate HDD's, boot Ubuntu in second HDD from BIOS.  Ubuntu has access to Win HDD C.  Still nothing changed.  Finally found four VB files in: Home Folder/file system/etc/init.d/vbox.  Tried to remove the four files with shift delete.  No joy.  How does one do it.  These files were found under VB 4.2.  Under VB 4.1 I found none.

Jeffrey


My guess is that the Virtualbox purge does not find the four files mentioned above as they are titled Vbox not virtualbox.

I would guess temp fix is to modify the purge command.  A correction to the problem would be to rename the files virtualbox.

Jeffrey

---

### Post by Jeffreytooker on 2012-11-01
> **Jeffreytooker said:**
> My guess is that the Virtualbox purge does not find the four files mentioned above as they are titled Vbox not virtualbox.

I would guess temp fix is to modify the purge command.  A correction to the problem would be to rename the files virtualbox.

Jeffrey

  	 	 	 	 	 	   The above mentioned files were found this way.  Open Synaptic.  Click search.  In Search enter: Virtualbox.  For the look in entry choose “Provide packages”.  Choose Search.  Search yields two items.  Right click the 4.2 entry.  Choose properties then installed files.  This gives the files and their location.  It also shows they come from Virtualbox 4.2.  
 

 I would like to remove these files.  I would guess that this is a pretty critical place to be removing files.  I would like some good advice on this issue. Noobie.
 

 Jeffrey

---

### Post by NikTh on 2012-11-02
> **Jeffreytooker said:**
> Files above removed as directed.  Also removed VB in C Prog files as a flag said Ubuntu was picking up a file in C/users/Jeffrey of my Windows HDD.  Two seperate HDD's, boot Ubuntu in second HDD from BIOS.  Ubuntu has access to Win HDD C.  Still nothing changed.  Finally found four VB files in: Home Folder/file system**/etc/init.d/vbox**.  Tried to remove the four files with shift delete.  No joy.  How does one do it.  These files were found under VB 4.2.  Under VB 4.1 I found none.
> **Jeffreytooker said:**
> My guess is that the Virtualbox purge does not find the four files mentioned above as they are titled Vbox not virtualbox.


These files are the modules of VirtualBox . Will be removed automatically from /init.d/ when you purge the VB files (as you did).

It is weird why the purge command not purged (vanished) the VB. This switch (purge) is for that reason , to vanish everything. Even the configuration files. 


Can you give the result of these commands ? 

```
sudo parted -l 
dpkg -l | grep -i virtualbox
```

Ubuntu has nothing to do with your Windows installation. (if are installed separately and not through wubi). In any case you can unmount your Windows partition if its configured to mount automatically in every boot (through /etc/fstab). 

Have you tried to install VB from Oracle's Website as suggested ?

Thanks

---

### Post by Jeffreytooker on 2012-11-02
To All:

Checked synaptic, both VB 4.1 and 4.2 uninstalled.  VB 4.2 still coming up from icon in Dash.  4.2 still crippled and will not take inputs under "New". I found a Wine tile in the icon bar on lower left of screen, opened it. This is where my 4.2 is coming from.  Went to "Ubuntu Software" removed Wine. Went back to VB icon in Dash, VB now will not open from icon.  Went to Main Menu, Applications, Wine, Wine programs, Oracle VM Virtualbox is there.  Removed Oracle VM Virtualbox. Went to Downloads and loaded Oracle VM Virtualbox (from Oracle) with Ubuntu Software.  Tried to start VB from Dash icon.  Will not start.  Went to Synaptic, VB 4.2 is installed. 



 Conclusion!!!


VB 4.2 is loaded and is set to open with Wine.  Since Wine is removed VB 4.2 can not open.


I thought VB 4.2 loaded directly into Ubuntu 12.04.  If this is so, how do we get VB 4.2 to come directly up in Ubuntu 12.04?


Jeffrey

---

### Post by howefield on 2012-11-02
> **Jeffreytooker said:**
> I thought VB 4.2 loaded directly into Ubuntu 12.04.  If this is so, how do we get VB 4.2 to come directly up in Ubuntu 12.04?

Can't help but suggest a reinstall of 12.04.1 and a fresh install of the correct Virtualbox. ;-)

You may be having fun cracking this particular nut, nothing wrong with that, but in terms of time it'd be much quicker.

I'd also suggest taking an image of the drive (or partitions) once you have fixed the issue. Screw ups then don't matter quite so much.

---

### Post by CharlesA on 2012-11-02
> **howefield said:**
> Can't help but suggest a reinstall of 12.04.1 and a fresh install of the correct Virtualbox. ;-)

You may be having fun cracking this particular nut, nothing wrong with that, but in terms of time it'd be much quicker.

I'd also suggest taking an image of the drive (or partitions) once you have fixed the issue. Screw ups then don't matter quite so much.
Agreed. I wonder why or how it installed the windows version in wine...

---

### Post by NM5TF on 2012-11-02
> **Jeffreytooker said:**
> To All:

Checked synaptic, both VB 4.1 and 4.2 uninstalled.  VB 4.2 still coming up from icon in Dash.  4.2 still crippled and will not take inputs under "New". I found a Wine tile in the icon bar on lower left of screen, opened it. This is where my 4.2 is coming from.  Went to "Ubuntu Software" removed Wine. Went back to VB icon in Dash, VB now will not open from icon.  Went to Main Menu, Applications, Wine, Wine programs, Oracle VM Virtualbox is there.  Removed Oracle VM Virtualbox. Went to Downloads and loaded Oracle VM Virtualbox (from Oracle) with Ubuntu Software.  Tried to start VB from Dash icon.  Will not start.  Went to Synaptic, VB 4.2 is installed. 



 Conclusion!!!


VB 4.2 is loaded and is set to open with Wine.  Since Wine is removed VB 4.2 can not open.


I thought VB 4.2 loaded directly into Ubuntu 12.04.  If this is so, how do we get VB 4.2 to come directly up in Ubuntu 12.04?


Jeffrey

now I'm ***really confused***....you say that you removed WINE...
then you say that it is still there under Apps....:(

I also must ask why you are trying to use VB if you already have seperate
Windoze/Ubuntu installs....what are you trying to accomplish???

am I missing something here:confused:

you said something in an earlier post about problems with your HP all-in-one printer....does it work correctly under Windoze???...does
it work correctly under Ubuntu???

FYI...I also have a HP F4180 all-in-one...it works flawlessly under Ubuntu
and also in VB running Win XP Pro....

what kind of problems are you having with it???

Tommy

---

### Post by Jeffreytooker on 2012-11-02
> **NM5TF said:**
> now I'm ***really confused***....you say that you removed WINE...
then you say that it is still there under Apps....:(

I also must ask why you are trying to use VB if you already have seperate
Windoze/Ubuntu installs....what are you trying to accomplish???

am I missing something here:confused:

you said something in an earlier post about problems with your HP all-in-one printer....does it work correctly under Windoze???...does
it work correctly under Ubuntu???

FYI...I also have a HP F4180 all-in-one...it works flawlessly under Ubuntu
and also in VB running Win XP Pro....

what kind of problems are you having with it???

Tommy


To All:

Took Howefield's advice above.  Loaded new 12.04.  Virtualbox loaded well.  It may have been a problem that the 12.04 I was using was an update from 10.04.  Thanks to all for all of the very good help.  I learned a lot about, Synaptic, Command Line, and Ubuntu in general.

Tommy:

I will start a new thread here "Virtual Box and HP All In Ones".  That way I can answer your VB/HP questions.

Jeffrey

---

### Post by NM5TF on 2012-11-03
most XCLNT news Jeffery....

please mark this thread as SOLVED

will read your new post next

Tommy

---

### Post by Jeffreytooker on 2012-11-03
how does one change the RE: to Solved?

Jeffrey

---

### Post by newb85 on 2012-11-03
Above the first post on this page, there should be a "Thread Tools" menu.  Click it and select "Mark Thread as Solved".  Thanks!

---

