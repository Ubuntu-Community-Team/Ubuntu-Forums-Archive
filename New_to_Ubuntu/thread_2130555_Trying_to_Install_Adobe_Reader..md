---
title: "Trying to Install Adobe Reader."
date: 2013-03-29
forum: New to Ubuntu
---

### Post by Cmiller2 on 2013-03-29
I'm running Ubuntu 12.10, and downloading Adobe Reader v. 9.5.4

I went to the adobe website and downloaded this file: **AdbeRdr9.5.4-1_i486linux_enu.bin** Download size is 40.0 MB.

However, no program will open it. How do I install Adobe Reader on Linux? Or is there some easier way? Thanks in advanced.

Kind Regards,

Cmiller

---

### Post by kc1di on 2013-03-29
the easiest way to install adobe acrobat is to enable the conical partners repository.  
you can do that by going to Software Center >Edit>Software Sources> Other Software and checking the Conical Partners box.

then do a search in software center for acroread.  and install it from there.

or once you get the boxed check you can go to a terminal and type the following to install it.
```
sudo apt-get update && sudo apt-get install acroread
```

If you want to install the program you down loaded you need to go to a terminal and CD to the directory where you downloaded the file and type
```
sudo ./AdbeRdr9.5.4-1_i486linux_enu.bin
```

how ever though it may install it may not install all dependencies and may not add an entry in the menu. 

Good luck

---

### Post by ajgreeny on 2013-03-29
Use the repositories rather than go direct; much easier!

Install **flashplugin-installer** package

Whoops! Sorry I meant **acroread**, not **flashplugin-installer**.  The use of the word Adobe just took my thoughts the wrong way!!

---

### Post by Cmiller2 on 2013-03-30
I wasn't actually able to figure out what you guys were saying. I tried those commands and none of them worked. Anyway, I just found out Linux already has a pre-installed PDF veiwer. So I'll stick with that. But I still want to figure out how to install programs from direct sites. I will need to do more research.

---

### Post by 3rdalbum on 2013-03-30
> **Cmiller2 said:**
> I wasn't actually able to figure out what you guys were saying. I tried those commands and none of them worked.

This isn't really a very useful thing to say. Did you get any error messages? If so, what messages **exactly** did you get? Those two commands should have worked - or you could just go to Ubuntu Software Center and find Acrobat Reader in there. When installed, right-click on the Ubuntu logo in the top-left of the screen and choose Applications. Acrobat Reader will appear in there.

> Anyway, I just found out Linux already has a pre-installed PDF veiwer. So I'll stick with that. But I still want to figure out how to install programs from direct sites. I will need to do more research.

There's no standard procedure for "installing programs directly from websites". It's not even recommended; there's a better way. The best way to install software is through Ubuntu Software Center. If the program is not there, you can add a "PPA" to your system that tells Software Center how to download and install the software.

---

### Post by OrangeCrate on 2013-03-30
> **Cmiller2 said:**
> I'm running Ubuntu 12.10, and downloading Adobe Reader v. 9.5.4

I went to the adobe website and downloaded this file: AdbeRdr9.5.4-1_i486linux_enu.bin Download size is 40.0 MB.

However, no program will open it. **How do I install Adobe Reader on Linux?** Or is there some easier way? Thanks in advanced.

Kind Regards,

Cmiller

As said, from the repositories would be the easiest way, but, I see from your other post, that you'd like to learn how to download and install directly from remote sites. For Adobe Reader, here's how you do it...

Go back to the adobe page and above the download box you will see a link that says "Do you have a different language or operating system?" Select that and make your three "step" choices from the boxes provided. First, the operating system would be Linux. Second, your language would be English (I assume), and finally choose the .deb option, and download. Then install the "Gdebi" package from the software center to handle this, and all future .deb installations. (Change the application of choice in your Downloads file to Gdebi. It will not only install the .deb package, but, will resolve any dependency issues automatically.)

---

### Post by Redcougar27 on 2013-04-15
Hello,

I have installed Adobe Reader 9 using Ubuntu Software Center. Installed BUT all the menus are black (file, edit, view ...). 

--> unusable

Worse I cannot uninstall the program. When trying with Ubuntu Software Center, I receive the error message:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 162190 files and directories currently installed.) 
Unpacking acroread-bin (from .../acroread-bin_9.5.4-1quantal1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/acroread-bin_9.5.4-1quantal1_i386.deb (--unpack): 
 trying to overwrite '/opt/Adobe/Reader9/Reader/AcroVersion', which is also in package adobereader-enu 9.5.1 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Processing triggers for man-db ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/acroread-bin_9.5.4-1quantal1_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of acroread: 
 acroread depends on acroread-bin; however: 
  Package acroread-bin is not installed. 
dpkg: error processing acroread (--configure): 
 dependency problems - leaving unconfigured

Adobe Reader is there but USC is not able to remove it and I don't know thie program is located. I am therefore unable to remove it using the terminal. 

Thanks in advance. Cheers.

---

### Post by Aks1 on 2013-04-15
What is the need for Adobe Reader??
I mean there is a Document Viewer option in Ubuntu.Try and open your pdf documents using that.
It consist of the basic need of the pdf file.
If your pdf files are before in Windows and  were open using Adode reader then, in ubuntu it directly opens from Document viewer. I guess its easy if you ont want the additional features of the pdf like writing and other permissions. :)

---

### Post by Aks1 on 2013-04-17
> **Cmiller2 said:**
> I'm running Ubuntu 12.10, and downloading Adobe Reader v. 9.5.4

I went to the adobe website and downloaded this file: **AdbeRdr9.5.4-1_i486linux_enu.bin** Download size is 40.0 MB.

However, no program will open it. How do I install Adobe Reader on Linux? Or is there some easier way? Thanks in advanced.

Kind Regards,

Cmiller

Well,document viewer is enough for ur need, as i mentioned above. But one more optimal way to get Adobe Reader.
Here is the Solution of your problem:
Go to the link and install it but before see the sys need below:
[http://get.adobe.com/reader/?promoid=HRZAC](http://get.adobe.com/reader/?promoid=HRZAC)

Here is the requirements for the Linux system,u can check that ur sys matches with it.>>
[h=4]Linux[/h] 
[LIST]
[*]32-bit Intel Pentium® processor or equivalent
[*]Red Hat® Linux WS 5, SUSE® Linux Enterprise Desktop (SLED) 10 SP2 or Ubuntu™ 7.10
[*]GNOME or KDE Desktop Environment
[*]512MB of RAM (1GB recommended)
[*]150MB of available hard-disk space (additional 75MB required for all supported font packs)
[*]GTK+ (GIMP Toolkit) user interface library, version 2.6 or later
[*]Firefox 2.x or 3.0
[*]OpenLDAP and CUPS libraries
[/LIST]

Or what u need to do is>>
Directly go to the Ubuntu Software center which is there in ur Os Ubuntu and check inside the "All Software" part. There u search Adobe Reader and install it,its 60 mb in size.u can get their more info about it.

I think now u can get it.

---

### Post by mastablasta on 2013-04-17
well since we talk abotu PDF readers perhaps it is worth mentioning that PDF's can be edited in libre office draw. ;-)

---

### Post by pinballwizard on 2013-04-17
> **Redcougar27 said:**
> Hello,

I have installed Adobe Reader 9 using Ubuntu Software Center. Installed BUT all the menus are black (file, edit, view ...). 

--> unusable

Worse I cannot uninstall the program. When trying with Ubuntu Software Center, I receive the error message:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 162190 files and directories currently installed.) 
Unpacking acroread-bin (from .../acroread-bin_9.5.4-1quantal1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/acroread-bin_9.5.4-1quantal1_i386.deb (--unpack): 
 trying to overwrite '/opt/Adobe/Reader9/Reader/AcroVersion', which is also in package adobereader-enu 9.5.1 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Processing triggers for man-db ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/acroread-bin_9.5.4-1quantal1_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of acroread: 
 acroread depends on acroread-bin; however: 
  Package acroread-bin is not installed. 
dpkg: error processing acroread (--configure): 
 dependency problems - leaving unconfigured

Adobe Reader is there but USC is not able to remove it and I don't know thie program is located. I am therefore unable to remove it using the terminal. 

Thanks in advance. Cheers.

@OP, you can natively open .pdf with Ubuntu as it is.

@everyone else, maybe help the guy with his dpkg problem?

I'll volunteer that @OP opens a terminal and runs 
```

dpkg -l | grep acroread
``` 

To see if it's even actually installed

Then run
```
sudo dpkg --configure -a
```

And then, just try and open the .pdf file?

---

