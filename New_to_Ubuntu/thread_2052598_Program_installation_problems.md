---
title: "Program installation problems"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by Scott B ME on 2012-09-03
I amtrying to install a program j-pilot on my Dell Inspirion 4300 with Ubuntu 12.04. I downloaded the program onto a USB drive. It extraced into a folder under my home folder. I search for the software in the Ubuntu Software Center. I see under the all software tab the J-Pilot. However, all it has it a button for more info. nothing allowing me to install. Also I do not have internet connection.

---

### Post by roger_1960 on 2012-09-03
What format is the extracted program file?  .deb?

Edit Just looked it up.  Perhaps gnome pilot would be better?  J-pilot seems to be for Palm devices.  If you want J-Pilot it is the software center - suggest you install it from there if you can.

---

### Post by Scott B ME on 2012-09-03
> **roger_1960 said:**
> What format is the extracted program file? .deb?
 
Edit Just looked it up. Perhaps gnome pilot would be better? J-pilot seems to be for Palm devices
 
I moved the tarball file, tar.gz, into my home folder. I clcked on it the it extracted a whole bunch of files into a folder with the same name. I do not see any .deb file. My original probmem is getting my Palm to interface as a broadband mobile connection.  From what I have read using J-pilot will help. I did see gnome pilot as well. I did copy that onto my hard drive but the software center did not even dectect that.

---

### Post by roger_1960 on 2012-09-03
If you have a "docs" folder in your extracted files, have a look at manual.html  The one from j-pilots website has instructions for compiling the software which is what you need to do I think.

---

### Post by Scott B ME on 2012-09-03
> **roger_1960 said:**
> If you have a "docs" folder in your extracted files, have a look at manual.html The one from j-pilots website has instructions for compiling the software which is what you need to do I think.
 
That is what is says I need to do.... How do I compile the software? it says to do ./configure. I do this from the terminal and it does not recognise the command

---

### Post by NikTh on 2012-09-03
Hello , 

If you refer to this program 

**apt-cache show jpilot**
```
J-Pilot is a desktop organizer application for PalmOS devices. It is
 meant to be an alternative to the Palm Desktop provided by Palm.
```It is in Ubuntu's Official repositories , so you don't need to download or compile anything. 

Just open a terminal and 

```
sudo apt-get install jpilot jpilot-plugins
```Thanks

---

### Post by Scott B ME on 2012-09-03
> **NikTh said:**
> Hello , 
 
If you refer to this program 
 
**apt-cache show jpilot**
```
J-Pilot is a desktop organizer application for PalmOS devices. It is
 meant to be an alternative to the Palm Desktop provided by Palm.
```It is in Ubuntu's Official repositories , so you don't need to download or compile anything. 
 
Just open a terminal and 
 
```
sudo apt-get install jpilot jpilot-plugins
```Thanks
 
Thanks for the info. I just did this and in terminal it says it cannot locate jpilot or jpilot plugins. I am sure there is something really simple I need to do to get this to locate the package. This has been driving me nuts

---

### Post by NikTh on 2012-09-03
Hello , 
give the results of this command 

```
cat /etc/apt/sources.list
```

Please put the results between ```
 brackets so can be readable

[noparse][code]The Results Here
```[/noparse]

Thanks

---

### Post by pdc on 2012-09-03
I notice in post #1 that Scott said

> Also I do not have internet connection.

---

### Post by NikTh on 2012-09-03
> **pdc said:**
> I notice in post #1 that Scott said

Haha .. I am blind :P 

If OP has not Internet connection then he must  follow the difficult road (for a new user) .
Compiling the already downloaded tar.gz file. 

Thanks

---

### Post by Scott B ME on 2012-09-03
Here are the results. I copied them from my linux machine and put them into Libre office writer then changed format to an RTF file. I hope I did not loose anything in the traslation  
 
 
[Code results] 
 
[FONT=Batang][SIZE=3]scott@scott-Dimension-4300:~$ cat /etc/apt/sources.list[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted[/SIZE][/FONT]
[FONT=Batang][SIZE=3]# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://archive.ubuntu.com/ubuntu precise main restricted #Added by software-properties[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to[/SIZE][/FONT]
[FONT=Batang][SIZE=3]# newer versions of the distribution.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]## Major bug fix updates produced after the final release of the[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## distribution.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## team. Also, please note that software in universe WILL NOT receive any[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## review or updates from the Ubuntu security team.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://us.archive.ubuntu.com/ubuntu/ precise universe[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## team, and may not be under a free licence. Please satisfy yourself as to[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## your rights to use the software. Also, please note that software in[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## multiverse WILL NOT receive any review or updates from the Ubuntu[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## security team.[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]## N.B. software from this repository may not have been tested as[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## extensively as that contained in the main release, although it includes[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## newer versions of some applications which may provide useful features.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## Also, please note that software in backports WILL NOT receive any review[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## or updates from the Ubuntu security team.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted multiverse[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security restricted main multiverse universe #Added by software-properties[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]## Uncomment the following two lines to add software from Canonical's[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## 'partner' repository.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## This software is not part of Ubuntu, but is offered by Canonical and the[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## respective vendors as a service to Ubuntu users.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://archive.canonical.com/ubuntu precise partner[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://archive.canonical.com/ubuntu precise partner[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]## This software is not part of Ubuntu, but is offered by third-party[/SIZE][/FONT]
[FONT=Batang][SIZE=3]## developers who want to ship their latest software.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb http://extras.ubuntu.com/ubuntu precise main[/SIZE][/FONT]
[FONT=Batang][SIZE=3]deb-src http://extras.ubuntu.com/ubuntu precise main[/SIZE][/FONT]
[FONT=Batang][SIZE=3]scott@scott-Dimension-4300:~$[/SIZE][/FONT]
[code] results [code]

---

### Post by NikTh on 2012-09-04
Hello , 

Please read the posts #9 and #10. If you have not a working Internet connection ,you will not be able to install anything.

Also to put the results between ```
 brackets , you can highlight the text and click the # symbol on message toolbar.  You missed a backslash / at the second [code] bracket. 

[noparse][code]The Results Here
```[/noparse]. Between . 

Thanks

---

### Post by Scott B ME on 2012-09-04
> **NikTh said:**
> Hello , 
 
Please read the posts #9 and #10. If you have not a working Internet connection ,you will not be able to install anything.
 
Also to put the results between ```
 brackets , you can highlight the text and click the # symbol on message toolbar. You missed a backslash / at the second [code] bracket. 
 
[noparse][code]The Results Here
```[/noparse]. Between . 
 
Thanks
 
That is true I do not have a working internet connection on my linux computer. I am extremely limited where I live. All I have is my cellphone to connect and this why I am trying to load either jpilot or gnome pilot for my Palm smartphone.

---

### Post by Scott B ME on 2012-09-05
> **Scott B ME said:**
> That is true I do not have a working internet connection on my linux computer. I am extremely limited where I live. All I have is my cellphone to connect and this why I am trying to load either jpilot or gnome pilot for my Palm smartphone.
 
Ouch.... :( So I need to find somewhere I can plug my desktop into ab ethernet jack... ? Before I can load the programs

---

### Post by NikTh on 2012-09-05
> **Scott B ME said:**
> Ouch.... :( So I need to find somewhere I can plug my desktop into ab ethernet jack... ? Before I can load the programs

Or you can go to another computer that has internet and download the programs you want to Usb stick and install them . 

Packages for Ubuntu releases can be found here : [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Thanks

---

