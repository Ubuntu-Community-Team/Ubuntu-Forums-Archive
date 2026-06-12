---
title: "Nvidia driver compile instructions for Ubuntu 6.06 &quot;Dapper Drake&quot; 32 bit."
date: 2006-09-18
forum: Outdated Tutorials &amp; Tips
---

### Post by nudnik on 2006-09-18
A rather rough, but hopefully beneficial guide to compiling the new driver.
The following directions are intended for Gnome.

Nvidia driver compile instructions for Ubuntu 6.06 "Dapper Drake" 32 bit.

All "CODE" must be typed and entered into the "Terminal" interface accessible from the upper left hand of the desktop by clicking on the "Applications" tab. A dialog box will drop down from which you should choose "Accessories" which will cause another box to appear from which you can activate the Terminal.

Navigate to [www.nvidia.com](www.nvidia.com) and download the latest IA32 driver to the desktop. (Currently NVIDIA-Linux-x86-1.0-8774-pkg1.run)

Install the necessary build libraries, components from the repositories.
         CODE
sudo apt-get install gcc

sudo apt-get install libc6dev

[Additionally the following may be needed:
sudo apt-get install nvidia-kernel-common
sudo apt-get install nvidia-kernel-source
sudo apt-get install xorg-dev
sudo apt-get install xserver-xorg-dev]

Press Ctrl+Alt+F1 to exit graphical mode and access the command line. 

Log in.

Go root to avoid potential annoying problems.
 
 CODE
sudo -s

Stop the Gnome display manager.
            CODE
sudo /etc/init.d/gdm stop
Navigate to the Desktop directory.
   CODE
cd Desktop

Begin dialog with driver compiler/installer.
                CODE
sh NVIDIA-Linux-x86-1.0-8774-pkg1.run

Accept the license agreement.

Nvidia package states your kernel is not compatible with the version it is attempting to install. The package will ask permission to check the Nvidia site for pre-compiled drivers compatible with your kernel. Click "OK". It will find none. The package will then offer to compile a driver for your kernel. Click "OK". The package should then compile a driver for your kernel. The package will then ask if you wish the configuration of your xserver settings. Answer in the affirmative.
 
Reboot the machine.
CODE
reboot

---

### Post by frodon on 2006-09-18
Just for the record, you can easily install the latest NVIDIA and ATI drivers through synaptic using this repository :
[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

---

### Post by nudnik on 2006-09-18
> Just for the record, you can easily install the latest NVIDIA and ATI drivers through synaptic using this repository :
[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

Very good to know. I do find it useful to know these things however, in the event something goes awry or for some reason the repositories are unavailable, which happens on rare occasion.

Its fun too. O:) 

(I secretly fear your alien status and organic USB interface.):shock: 

](*,) <<The Ubuntu Mascot :biggrin:

---

### Post by dresdn on 2006-09-26
> **frodon said:**
> Just for the record, you can easily install the latest NVIDIA and ATI drivers through synaptic using this repository :
[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

That's great if you are a "normal" user. ;)  Are there any special steps to "hand installing" an NVIDIA driver w/o using a .deb for Ubuntu?  I recently did a apt-get remove --purge nvidia-glx, then installed whatever driver I wanted.  It works great except when I reboot, X fails to start as it complains about version mis-matches.  What's odd is that it's finding a module from the 7xxx series, which is from ages ago!

So the question is, what does Ubuntu do that's special that the NVIDIA-xxx.run files don't fix/replace/remove?

Thanks!

-Mike

---

### Post by frodon on 2006-09-26
> **dresdn said:**
> So the question is, what does Ubuntu do that's special that the NVIDIA-xxx.run files don't fix/replace/remove?

Thanks!

-MikeNothing you can do that without any problems if you know what you're doing, i give you another link to a great guide on the topic :
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by dresdn on 2006-09-26
> **frodon said:**
> 
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Thanks! That's **exactly** what I was looking for.

-Mike

---

### Post by Compwiz on 2006-09-27
> **nudnik said:**
> A rather rough, but hopefully beneficial guide to compiling the new driver.
The following directions are intended for Gnome.

Nvidia driver compile instructions for Ubuntu 6.06 "Dapper Drake" 32 bit.

All "CODE" must be typed and entered into the "Terminal" interface accessible from the upper left hand of the desktop by clicking on the "Applications" tab. A dialog box will drop down from which you should choose "Accessories" which will cause another box to appear from which you can activate the Terminal.

Navigate to [www.nvidia.com](www.nvidia.com) and download the latest IA32 driver to the desktop. (Currently NVIDIA-Linux-x86-1.0-8774-pkg1.run)

Install the necessary build libraries, components from the repositories.
         CODE
sudo apt-get install gcc

sudo apt-get install libc6dev

[Additionally the following may be needed:
sudo apt-get install nvidia-kernel-common
sudo apt-get install nvidia-kernel-source
sudo apt-get install xorg-dev
sudo apt-get install xserver-xorg-dev]

Press Ctrl+Alt+F1 to exit graphical mode and access the command line. 

Log in.

Go root to avoid potential annoying problems.
 
 CODE
sudo -s

Stop the Gnome display manager.
            CODE
sudo /etc/init.d/gdm stop
Navigate to the Desktop directory.
   CODE
cd Desktop

Begin dialog with driver compiler/installer.
                CODE
sh NVIDIA-Linux-x86-1.0-8774-pkg1.run

Accept the license agreement.

Nvidia package states your kernel is not compatible with the version it is attempting to install. The package will ask permission to check the Nvidia site for pre-compiled drivers compatible with your kernel. Click "OK". It will find none. The package will then offer to compile a driver for your kernel. Click "OK". The package should then compile a driver for your kernel. The package will then ask if you wish the configuration of your xserver settings. Answer in the affirmative.
 
Reboot the machine.
CODE
reboot
those steps are very easy and understandable, and fixed my glx problem! :D thanks!

---

### Post by f.l.u.f. on 2006-09-28
> **nudnik said:**
> 
sudo apt-get install libc6dev


I get an error of E: Couldn't find package libc6dev when I try to install.  Am I missing a repository?

Thanks.

---

### Post by ChineseDriver on 2006-12-21
> **f.l.u.f. said:**
> I get an error of E: Couldn't find package libc6dev when I try to install.  Am I missing a repository?

Thanks.

same here

---

### Post by ChineseDriver on 2006-12-21
> **f.l.u.f. said:**
> I get an error of E: Couldn't find package libc6dev when I try to install.  Am I missing a repository?

Thanks.

sudo apt-get install libc6-dev

if im correct the file name has a dash in it that was missing

had to correct myself here

---

