---
title: "iso burn and download"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by rchubcitywihwy1480 on 2013-02-23
To download the ubuntu  12.04 it says to have the cd or stick handy, do you have to burn it as you download it?

i have a 32 bit vist and a 64 bit win 7, it says 32 bit recommended?

usually you "save" then burn?
tks

---

### Post by howefield on 2013-02-23
> **rchubcitywihwy1480 said:**
> usually you "save" then burn?

And that's exactly what to do...

32 is recommended because it is pretty much guaranteed to work on both 32 and 64 bit machines, whereas 64 bit obviously needs a 64 bit capable machine.

Sounds like 64 bit is what you want.

---

### Post by doja on 2013-02-23
I use the 12.04 64 bit  version and have no problems, therefore, I can only recommend it.

If the machine  is 64 bit I would take 64 bit OS.

%%%%

If you use CD:
1. download + save
2. burn
3. Install

If you make installation from USB-stick, I don't know how to make the 2nd step.  ;)

---

### Post by Jimmyfj on 2013-02-23
I would say that it depends on the amount of RAM you have installed. For 64 bit system you need minimum 4 GB RAM in your Pc

---

### Post by haqking on 2013-02-23
> **Jimmyfj said:**
> I would say that it depends on the amount of RAM you have installed. For 64 bit system you need minimum 4 GB RAM in your Pc

you dont need 4Gb ram to use x64.

x64 can address more RAM than x86 32 bit but it doesnt mean you "need" 4 Gb ram,.

I am running x64 Fedora right now with 4 windows open including a browser with 8 tabs and a VM running, I am using a total of 2.2GB ram. (though I have 16)

---

### Post by doja on 2013-02-23
> **Jimmyfj said:**
> I would say that it depends on the amount of RAM you have installed. For 64 bit system you need minimum 4 GB RAM in your Pc

I'm no expert and  I don't want argue, but I  have only 3GB RAM.

---

### Post by grahammechanical on 2013-02-23
And I only have 1GB and Ubuntu works fine - 12.04, 12.10 and 13.04 under development. Which I am using now with 2 Libreoffice documents open, Chromium with 3 tabs including streaming a BBC radio program and System Monitor says I am using 78% RAM.

> The minimum memory requirement for Ubuntu 12.10 is 768 MB of memory and 5 GB of disk space for Ubuntu Desktop. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal; however, it will complete successfully, and the system will perform adequately once installed.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop")

Regards.

---

### Post by rchubcitywihwy1480 on 2013-02-23
A cousin of mine is trying to get me running ubuntu, i have win 7 toshiba 64 bit c655 laptop, wifi connected through my desktop and linksys router, 4 g ram 320gb hd, only about 10 gb free presently.

when you use  the iso ubuntu, do you fully install or just run from the cd and when you shut down, you close out everything and remove the cd, you are back to windows, is the iso the live cd?

on the cd live web page, "desktop"  is referred to, is that  just a general term or does it mean a desktop pc period?
[http://livecdlist.com/](http://livecdlist.com/)

it's just onboard video on this pc also, do i need a dedicated video card?

thanks to all

i may buy another laptop to do this,, suggestions?

i think i have a 10.4 or 11 version i was mailed, could i use those?


what  am i missing i have been a member 6 years and still haven't done this?

---

### Post by doja on 2013-02-24
As I mentioned before I'm no expert either, but before someone more competent gives you better answers I try to help you.

It seems to me that you try do it right and are little bit scared of  doing something wrong. But in normal case it is not so difficult get Ubuntu to run.

 You mentioned you have also eldery distributions of Ubuntu. You can use them but why?  The only reason can be that they maybe don't need so much space on HDD (But I don't know if it is so)  and that they may run maybe little bit faster if the pc is old. If you have no special reason is the 12.04 LTS in my opinion better. The elder distros have the disadvantage that they are not up to date, which can bring you some problems.

I have more then 10GB space on my HDD for Ubuntu and can not say if 10 GB are sufficient. For the operating system (OS) maybe, but if you add some programs maybe you sometimes reach  limits of the space.    If you take 20GB it will be enough. If you don't have enough space on HDD then clean up the HDD at first or copy some data to external HDD. But I'm sure  you definitively don't need a new PC because of UBUNTU. For making more space on HDD for Ubuntu look for partitioning.  If you want install additionally OS on pc you have to partition your HDD in any case.  Before partitioning you should make defragmentation under windows, or at least it was so   when I used win XP.  

From your text I understand that you have already one cd with the  Ubuntu iso on it.

Then put the CD in PC and start it at first without installation to see if it is running. If you use it this way maybe some functionality doesn't work (this is normal). But you can check if your graphic card is supported etc.  and if you like it.  But this modus is not intended for really working with Ubuntu.  This modus doesn't make any changes on the HDD, that means after shut down Ubuntu everything will be like before.

If you want  really use Ubuntu you have to install it properly.  - make install - choose the free space on HDD - create SWAP and \root (and maybe separately \home).

After the installation from CD connect at first your pc per cable to the internet (in case your W-lan card isn't directly supported after installation from CD), make updates and install additional drivers (for example for W-lan) and programs.

and **BACKUP YOUR IMPORTANT DATA BEFORE INSTALLATION OR DEFRAGMENTATION **in case something goes wrong.

good luck

---

### Post by howefield on 2013-02-24
> **rchubcitywihwy1480 said:**
> A cousin of mine is trying to get me running ubuntu, i have win 7 toshiba 64 bit c655 laptop, wifi connected through my desktop and linksys router, 4 g ram 320gb hd, only about 10 gb free presently.

Are you sure you only have 10 gigs free ?

In other words you have 310 gig of data on the machine ? If that is the case you probably need that free space for the smooth running of your Windows installation.

> when you use  the iso ubuntu, do you fully install or just run from the cd and when you shut down, you close out everything and remove the cd, you are back to windows, is the iso the live cd?

By burning the iso image to either a CD/DVD or USB memory stick you are creating the LIVE MEDIUM.

The choice is yours, you can run Ubuntu from the Live CD/DVD which means you will not touch the existing hard drive, but lose everything when you shut down, or you can instead of using CD/DVD burn the iso to a USB memory stick with "persistence" which means you can make changes, install applications and save documents to the USB memory stick, or of course you can install to the machines hard drive using your LIVE medium.

> on the cd live web page, "desktop"  is referred to, is that  just a general term or does it mean a desktop pc period?
[http://livecdlist.com/](http://livecdlist.com/)

Desktop pretty much means anything that is not a server, so includes laptops, notebooks, full desktop machines ect.

> it's just onboard video on this pc also, do i need a dedicated video card?

No, not necessarily. 

> i may buy another laptop to do this,, suggestions?

That may well be overkill ;-) 

> i think i have a 10.4 or 11 version i was mailed, could i use those?

Probably not a good idea in either case, 10.04 goes end of life in a few weeks, as does 11.10. 11.04 is already end of life. YOu could use them to install and them upgrade to a supported version, however it would be much easier and less likely to error by using a current version, I'd recommend 12.04.2 for you.

> what  am i missing i have been a member 6 years and still haven't done this?

Welcome and good luck ;-)

---

### Post by rchubcitywihwy1480 on 2013-02-24
Thanks

I  can easily remove some data to dvds

If and when i have the live media to insert, if i am going to run it from the live media, do i have to boot to that or just open it?


tks

---

### Post by mastablasta on 2013-02-25
you have to boot to that to load the OS. it will load the OS from DVD to ram.

---

### Post by doja on 2013-02-25
In standard case the first device the pc is booting from is a cd/dvd device.
Means, if you put the cd in the pc it should boot automatically.
If not you have to go in the boot manager and change the booting order.

---

### Post by rchubcitywihwy1480 on 2013-02-25
i think when the l top boots up it shows either f2 or f12 on the tray, so it might be if i put the cd or dvd in would recognize it?  what am i going to run into with wifi?  just enter the password or are there other issues?
tks

---

### Post by doja on 2013-02-25
> **rchubcitywihwy1480 said:**
> i think when the l top boots up it shows either f2 or f12 on the tray, so it might be if i put the cd or dvd in would recognize it?  what am i going to run into with wifi?  just enter the password or are there other issues?
tks

Sorry, I don't understand what is your problem.
If you have the CD put it in the slot and restart your pc. There should appear a menu where you chose to start Ubuntu without install. There is no need of wifi or internet connection at all. You can do it without internet connection.

As far as I know, if you are asked for some password it has nothing to do with starting Ubuntu from cd, but rather with some options on your computer.  If you just downloaded the OS from the internet there is no possibility to ask you a password.

---

### Post by Impavidus on 2013-02-25
The point with wifi is that you may need additional drivers to get it working. Sometimes the drivers are build into linux, sometimes you need separate proprietary drivers to get it working and sometimes it doesn't work at all. It all depends on the manufacturer of your wifi chipset. You can test it whilst using the live dvd, but it's no problem to install without wifi and get it sorted out later.

Just put the dvd in the tray and reboot your computer. If it goes straight into windows get into the bios (I assume F2 or F12 on your laptop) and change the boot order.

---

### Post by doja on 2013-02-25
[[COLOR=#000000]rchubcitywihwy1480[/COLOR]]("http://ubuntuforums.org/member.php?u=236089") you must at least tell us at which point of the installation you are to make it possible to help you.

[[COLOR=#000000]Impavidus[/COLOR]]("http://ubuntuforums.org/member.php?u=1417721") is right and I wrote to you the same before - > first install ubuntu and then download additional drivers if Ubuntu doesn't support all your hardware. 

But before Ubuntu is installed there is no need to care about the internet. If your wifi is not supported directly after installation then you should connect your pc per cable to the internet and look for a driver. But this is a different task. At first install Ubuntu.

1. try if Ubuntu is running from the live medium (without install).
2. If you get it then there will be a big task for you to install it properly.
3. then you care about all others (for example wifi)

Tell us if you get the first point or where you have a problem with the first point.

---

### Post by rchubcitywihwy1480 on 2013-02-25
it appears do to how i use these 2 pcs and are both wifi, that i get another pc to do this
tks

---

### Post by doja on 2013-02-25
> **rchubcitywihwy1480 said:**
> it appears do to how i use these 2 pcs and are both wifi, that i get another pc to do this
tks

????
try it again. I don't understand you.

---

### Post by rchubcitywihwy1480 on 2013-02-25
i don't want to chance messing either of these pcs up so i am going to wait till i get another on

---

### Post by rchubcitywihwy1480 on 2013-02-26
F 12 is the boot manager

a few questions again

1  once i get the iso burned and insert into the drive before 
    booting, i am going to tap the F 12 key?  

2  i assume then a window will show  giving mean option to boot?

3  then it is going to recognize the cd/dvd to install?

4   how long does it take to go through this process?

5   If it is successful it will   tell me?

6  If  it is not successful will it tell me?

7.  If  it is successful what do i do next?

8  It will show a task bar explorer bar, will firefox be 
   shown  here or i am not connected at this time to the 
    internet?

9    if i am not connected to the internet on my wife how do i 
    do  that being i have no internet connection as the  live cd 
    is in and i would not be running windows?

10  what will tell me if my lap top is capabloe of running 
    ubuntu?

11,  if it is not successful what do i do to shut it  down?

12.  is there a system restore point?

---

### Post by doja on 2013-02-26
1  once i get the iso burned and insert into the drive before 
    booting, i am going to tap the F 12 key? 

You put the CD in a tray and restart pc

A.  if a ubuntu menu appears you are over the booting task - no hitting f12 necessary. 

B. If windows is booting after restart then - Yes hit some tap, I can't say if it is  f12 on your machine because on my pc I tap "delete" taste. But it is right, after starting your pc and  before anything happen tap the "f12" or "f2" or "delete".

2  i assume then a window will show  giving mean option to boot? 

Yes, this menu window has a basic graphic, quite simple and you have
to use arrow taps "->" to navigate the cursor and hit "enter" or "esc" for chose or deny and on the bottom line is a menu list for the keys "f1" - "f12" which you have to follow. Then you have to chose from menu something like "boot" and there you must find the booting order list where you put on the first place your cd drive and on the second the HDD.

3  then it is going to recognize the cd/dvd to install? 

If you manage the boot task, then the cd is recognized and a ubuntu menu appear. THERE you chose start ubuntu without install.

4   how long does it take to go through this process? 

booting - depens only on your skill (1-2min maximum if you know what to do)
ubuntu loading - some minutes ca 3-4 can't tell exacltly. Depens on machine may be even 10 minutes if the machine is old.

5   If it is successful it will   tell me? 

If it is successful the desktop of Ubuntu will appear 

6  If  it is not successful will it tell me?

I can't say, I hope - it depends also on the kind of the problem.

7.  If  it is successful what do i do next? 

Then enjoy the "demo" version of Ubuntu for some while and repeat the proceeding one or twice again - to practice.  

8  It will show a task bar explorer bar, will firefox be 
   shown  here or i am not connected at this time to the 
    internet? 

Yes - Firefox will be there

If you are connected to the internet it depends if your hardware  is supported. 

If you use a cable connection the internet should work  even in the "demo" modus (Ithing). But you are still only in "demo" modus.

9    if i am not connected to the internet on my wife how do i 
    do  that being i have no internet connection as the  live cd 
    is in and i would not be running windows? 

This is a point. If you start Ubuntu, there is no Windows.
There is Ubuntu and only the basic installation of Ubuntu.
That means - like under windows - you need sometimes for additionally hardware (wlan or graphic card, ect.)  additional drivers.  If you use Lan cable Internet will work. And with the cable connection you can download a driver, then you install a driver and then you can start your connection to the internet per wlan.

10  what will tell me if my lap top is capabloe of running 
    ubuntu? 

I'm sure the laptop is capable. But you have to try it - put the cd in and start it.
Then you will see.

11,  if it is not successful what do i do to shut it  down? 

Usualy there come popup menu that say something is wrong and ask
if the process should be canceled.

Because you didn't install anything on the pc nothing can happen, you can broke the process, put the cd out and restart the machine. Then the machine will boot the windows OS.


12.  is there a system restore point? 

As far as I know no. But you start Ubuntu from cd, you load it from cd and you don't change anything on the HDD then what the hell do you want restore??

Your windows has not been changed. If you put the cd out and restart pc windows will boot from HDD again.

In the worst case that can happen (I haven&#8217;t this problem yet) you have to reinstall your windows. And if you backup your data as I told you nothing can happen.


___________________________________________________

But if you will learn install Ubuntu you have to try !!!

---

### Post by rchubcitywihwy1480 on 2013-02-26
so if i have win 7 hp, 64 bit, do i still use the ubuntu 32 bit?

i see comments that 12.4 and 12. 10 are under development, so which link should i use to burn so i ca run it from cd/or dvd, is the file size now so dvd is required

is there a specific burn speed that is better 4x or 8x on dvd if cd what speed?
tks

---

### Post by gnueliafnak on 2013-02-26
> **rchubcitywihwy1480 said:**
> so if i have win 7 hp, 64 bit, do i still use the ubuntu 32 bit?

i see comments that 12.4 and 12. 10 are under development, so which link should i use to burn so i ca run it from cd/or dvd, is the file size now so dvd is required

is there a specific burn speed that is better 4x or 8x on dvd if cd what speed?
tks

both are stable versions, just that the 12.4 version will be supported longer and 12.10 is only supported for 18 months according to the installation page.

If you're using Win 7 in 64 bit that means you have a CPU that has multiple cores which would benefit from a 64 bit environment. In this case I would go with the 64 bit download version.

I'm a new Linux user overall and new to Ubuntu also and yesterday was my first time installing 12.10 64 bit on my desktop and it runs great. I use it as a HTPC mainly.

As for burn speed, normally the "auto default" speed will do. The file size is actually below 800mb, I believe it meets the requirements for a regular CD burn hence LiveCD instead of DVD.

---

### Post by rchubcitywihwy1480 on 2013-02-26
1,  why is 32 bit recommended?
2. so download  the 12.4?
3 the buen phase is different than  i have ever done.usually you down load to your pc than open your burner drag the file to it and burn  after inserting your blank media// here they say insert your media, right click on the iso, is that after its downloaded, sounds like a confused direction?

---

### Post by mastablasta on 2013-02-27
> **rchubcitywihwy1480 said:**
> 1, why is 32 bit recommended?

Becuase 32 bit works just as well on 32bit CPU as it does on 64 bit CPU. But 64bit version only works on 64 bit CPU. and not everyone has those yet. plenty of people with older hardware and no money or need to replace it.
 
> 
2. so download the 12.4?

 
12.04 is a bti more polished since it is LTS. it is based on previous stable version and usually LTS version doesn't include many new experimenta features. while 12.10 though stable will have new features in it. it will also have new kernel which in linux also means new drivers for newer hadrware.
 
> 
3 the buen phase is different than i have ever done.usually you down load to your pc than open your burner drag the file to it and burn after inserting your blank media// here they say insert your media, right click on the iso, is that after its downloaded, sounds like a confused direction?
 
burn phase is different as you need to use the image of the operating system you downloaded to create a bootable media (DVD/CD) that can actually boot and install the operating system. bootable disk has a special "flag"/file that enable it to boot.
for example in windows the command to do this is i think ```
format /s
```. or at least it used to be. it created a system disk one could use to boot into the OS. and your system disk in windows has also this booting capability. after all you can boto with it into the OS.
 
what programme are you using to burn the media? seems to me that instructions here are preety clear: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
yes, right-click on iso after you download it and after you checked the file integrity.

---

### Post by rchubcitywihwy1480 on 2013-02-27
ImgBurn is the  program i use a lot to burn, when i open the program you can drag and drop or use the browse for file and add it to the project, when the dvd or cd is full or you are ready to proceed you follow the  the process to finalize.

My win 7 toshiba 64 bit laptop is 3 years old and was rather inexpensive 400.00 , not a lot of money.

what is the right link for the 12 version to do the live cd or dvd?

will the ImgBurn program do this right?

isee there is reference to use or not use the alternative? refers to desktop?

---

### Post by mastablasta on 2013-02-27
> **rchubcitywihwy1480 said:**
> ImgBurn is the program i use a lot to burn, when i open the program you can drag and drop or use the browse for file and add it to the project, when the dvd or cd is full or you are ready to proceed you follow the the process to finalize.

oh yeah. it's a good one i use it sometimes as well. you do it like so in imgburn: [http://forum.imgburn.com/index.php?showtopic=61](http://forum.imgburn.com/index.php?showtopic=61)
 
> 
My win 7 toshiba 64 bit laptop is 3 years old and was rather inexpensive 400.00 , not a lot of money.

is that USD? let's say it's USD. there are plenty countries where people earn less than 100 USD a month as average salary. and then you have to know that usually 80% or more have much less than the national average. so yeah for some it can be A LOT of money. for me that would be a big cost especially since i have a mashcine that is already working well enough for what i need it to do. though the mashicne is old AMD64 CPU but still. many have P4 from similar era and those are not all 64bit. 
 
>  
what is the right link for the 12 version to do the live cd or dvd?

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
 
you can also go here for images & checksums:
12.04: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
12.10: [http://releases.ubuntu.com/quantal/](http://releases.ubuntu.com/quantal/)
 
>  
isee there is reference to use or not use the alternative? refers to desktop? 

 
not sure which alternative. but there is an alternate image of Ubuntu which uses text based install. i think it was dropped not long ago. but the minimal iso (no desktop, basic services) is still available. also known as net install since you install it all from internet later on.

---

### Post by rchubcitywihwy1480 on 2013-02-27
[https://help.ubuntu.com/12.04/installation-guide/index.html](https://help.ubuntu.com/12.04/installation-guide/index.html)

the one below refers to "alternate" to avoid?


[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Preparing your LiveCD

You need to create, borrow, buy or request an Ubuntu CD or Usb-stick. Once you have an Ubuntu Cd or Usb it should work as an installer and as a !LiveCD or LiveUsb. There are some downloads, such as the Alternate Cd that cannot be used as !LiveCd/Usb.

To create a LiveCd

    Download Ubuntu. For a live CD, avoid the "alternate CD" & the Server Edition because it has no desktop. For installing, using the alternate CD is a good idea, if installing using the standard CD does not work. 


yeas i see now AMD 64 was a beast a few years ago almost bought one.

so i should use .04 or .10

---

### Post by rchubcitywihwy1480 on 2013-02-28
[http://www.omgubuntu.co.uk/2012/09/its-official-the-ubuntu-livecd-is-dead](http://www.omgubuntu.co.uk/2012/09/its-official-the-ubuntu-livecd-is-dead)

i tried  to download it tonight  12/10   and it came in 2 files one was a disc image the other a binary file

i did not try to burn it, deleted it.

apparently it has o be a dvd?

is the download supposed to be in 1 file and an iso or disc image?

---

### Post by sleash78 on 2013-03-01
yes you probally want to save then burn. after you save it you may want to check the md5sum. with windows you can download fciv.exe [http://support.microsoft.com/kb/841290](http://support.microsoft.com/kb/841290) . the md5sums are under MD5SUM for each iso you can download [http://releases.ubuntu.com/](http://releases.ubuntu.com/).

---

### Post by rchubcitywihwy1480 on 2013-03-01
> **sleash78 said:**
> yes you probally want to save then burn. after you save it you may want to check the md5sum. with windows you can download fciv.exe [http://support.microsoft.com/kb/841290](http://support.microsoft.com/kb/841290) . the md5sums are under MD5SUM for each iso you can download [http://releases.ubuntu.com/](http://releases.ubuntu.com/).


i think i am going to forgo this for the time being

tks

---

### Post by rchubcitywihwy1480 on 2013-03-18
i did download and burn the iso  12.10.  with IMGBurn, i did not do the check , is that really necessary?  If i use it it will be live dvd, mot installede.
tks

---

