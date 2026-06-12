---
title: "Unable to boot from USB after removing Ubuntu 12.04 LTS"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by anshulsingh on 2013-04-11
[COLOR=#333333][FONT=Ubuntu Beta]Hi I am [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]reforming my original post to convey the details of my problem clearly.
I am trying to install XUbuntu 12.10 on my PC with the following configuration.(Intel celeron processor, 1 GB ram, 15 inch CRT monitor, Mercury  [/FONT][/COLOR]KOB P4M266a NDMx[COLOR=#333333][FONT=Ubuntu Beta] motherboard)
I created the bootable usb Using unibootinwhich seems to work fine.Earlier I used to work with windows XP on this desktop which used to work fine.I am no longer able to install XP back on this system due to a failed attempt to install Ubuntu on this system, so I am trying again with XUbuntu. I will mention the details of the failed Ubuntu installation at the end of the Post.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
My BIOS settings are as follows
[/FONT][/COLOR][IMG]http://i238.photobucket.com/albums/ff81/8aum/ubuntu/Capture7.jpg[/IMG][COLOR=#333333][FONT=Ubuntu Beta]
[/FONT][/COLOR]
[IMG]http://i238.photobucket.com/albums/ff81/8aum/ubuntu/Capture6.jpg[/IMG]



[IMG]http://i238.photobucket.com/albums/ff81/8aum/ubuntu/Capture9.jpg[/IMG]


[COLOR=#333333][FONT=Ubuntu Beta]First of  all when I am using my old monitor to install Xubuntu I am getting a out  frequency message after I select the install option from the uniboot menu.[/FONT][/COLOR]


[COLOR=#333333][FONT=Ubuntu Beta][IMG]http://i238.photobucket.com/albums/ff81/8aum/askubuntu.jpg[/IMG][/FONT][/COLOR]


If I am using a LCD monitor I get the followin screens instead

[IMG]http://i238.photobucket.com/albums/ff81/8aum/ubuntu/Capture2.jpg[/IMG]

I selected the Install option and pressed enter  then the second screen was

[IMG]http://i238.photobucket.com/albums/ff81/8aum/ubuntu/Capture3.jpg[/IMG]

After a waiting time of 3-4 minutes the screen changes to 

[IMG]http://i238.photobucket.com/albums/ff81/8aum/ubuntu/Capture.jpg[/IMG]

Instead of selecting the install option if i select the try ubuntu option .It takes me to following screen.

[IMG]http://i238.photobucket.com/albums/ff81/8aum/ubuntu/Capture4.jpg[/IMG]


Please help me How can I solve my problem. I hope I am clear in my question.

Details of my failed Ubuntu Installation---

[COLOR=#333333][FONT=Ubuntu Beta]I installed  ubuntu 12.04 desktop LTS on my PC using bootable usb created using  Unibootin.The installation was successful and I used ubuntu for few  days(Though it was running slow).At that time I had 22 inch LCD monitor  but I changed it to 15" CRT monitor and started getting a out of frequency  message during boot[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta].Since the ubuntu was very slow on this machine  therefore I decided to go back to windows XP so I created a windows XP  bootable USB but I am not able to boot from this USB.I created the  Ubuntu bootable usb again so that I can format the complete hard drive  but now it wont boot from this Usb also.[/FONT][/COLOR][FONT=Ubuntu Beta][COLOR=#333333]I had gone  through various methods to create bootable USB .The only one method that  works for me is--First I have to format my usb to FAT16 file system  then use Universal-USB-Installaer 1.9.2.6 to create bootable Ubuntu  12.04. All other soft-wares such as Unibootin ,Rufus etc does not work  on my PC.If my flash drive is formated in FAT32 or NTFS then the bios  wont show the boot from USB option.[/COLOR][/FONT]
[FONT=Ubuntu Beta][COLOR=#333333]Earlier I  was able to boot from my pen drive formated in FAT 32 file format also I  have installed windows XP multiple times on this system using the  pendrive.All the things have gone wrong after i installed Ubuntu. I used  to create bootable XP using WinSetupFromUSB2.2 but it wont work now. I  have checked the bios setting ,they are fine.Also my bootable xp pen  drive works fine on other machines.So there in no mistake in creating  this drive. [/COLOR][/FONT]
[FONT=Ubuntu Beta][COLOR=#333333]I was also  able to create  bootable usb of "ultimate boot CD" using  Universal-USB-Installaer 1.9.2.6 and its working this proves that  something has gone wrong when I tried to remove ubuntu but I am not sure  what.[/COLOR][/FONT]
[FONT=Ubuntu Beta][COLOR=#333333]The whole  requirement is to prepare the system for a complete new install for  windows XP as this is the only OX that will run fine with my  configuration.[/COLOR][/FONT]
[COLOR=#333333][FONT=Ubuntu Beta]Can any one please help me to solve this problem so that I can install My XP back again.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
[/FONT][/COLOR]

Thanks a lot

---

### Post by zrdc28 on 2013-04-11
If xp will run on that computer lubuntu or xubuntu will run fine, lubuntu will be twice as fast as xp.  For a new install of xp
can you not just put your xp cd in and just tell it to format c: that will clear everything!

---

### Post by anshulsingh on 2013-04-12
> **zrdc28 said:**
> If xp will run on that computer lubuntu or xubuntu will run fine, lubuntu will be twice as fast as xp.  For a new install of xp
can you not just put your xp cd in and just tell it to format c: that will clear everything!

I dont have optical drive to install xp. Bootable USB of xp wont boot now.

---

### Post by black veils on 2013-04-12
i know this is not what you specifically asked, but as stated you can run lubuntu or xubuntu as lighter alternatives.

if you can boot the slow ubuntu system, install the xfce4 desktop environment, this will add another graphical user interface session, which you choose from the login screen.

run the command ```
sudo apt-get install xubuntu-desktop xfce4-goodies
```

it is configurable, yet easy to use. you can change the appearance/layout to suit you.

---

### Post by fantab on 2013-04-12
HOW did you remove Ubuntu?

BACK UP DATA/IMPORTANT FILES FIRST. Boot with ubuntu LiveUSB. Run Gparted and DELETE all the partitions. Close Gparted and shut down the machine.

Boot with XP and start the installation with creating partitons. (XP will not install on Linux file-systems).

If you've found Ubuntu to be slow then, as suggested, try Xubuntu or Lubuntu. I would recommend Lubuntu.

---

### Post by anshulsingh on 2013-04-12
> **black veils said:**
> i know this is not what you specifically asked, but as stated you can run lubuntu or xubuntu as lighter alternatives.

if you can boot the slow ubuntu system, install the xfce4 desktop environment, this will add another graphical user interface session, which you choose from the login screen.

run the command ```
sudo apt-get install xubuntu-desktop xfce4-goodies
```

it is configurable, yet easy to use. you can change the appearance/layout to suit you.

I am able to boot using XUbuntu 12.10 32bit Bootable USB created using Universal-USB Installer.The first screen that I get is a blank screen with Keyboard=Man symbol at the bottom. This screen remains there for aboit 3-4 minutes. Then there is another blank screen with cursor blinking on top left.It remains there for about 1-2 min. Then I receive a third Screen Loading XUbuntu with four dots blinking one after another. This keep on going for about 4-5 minutes and then I receive a screen with out of frequency message as attached in the original post. What shoul I do now?

> **fantab said:**
> HOW did you remove Ubuntu?

BACK UP DATA/IMPORTANT FILES FIRST. Boot with ubuntu LiveUSB. Run Gparted and DELETE all the partitions. Close Gparted and shut down the machine.

Boot with XP and start the installation with creating partitons. (XP will not install on Linux file-systems).

If you've found Ubuntu to be slow then, as suggested, try Xubuntu or Lubuntu. I would recommend Lubuntu.

I removed the Ubuntu using ubuntu USB that I created . in the screen there were options such as install ubunu, try ubuntu , and try something else. I entered into try something else option and manualy deleted all the partitions and saved it and then turned off the system then to plug in another usb with bootable XP in it.

I also tried booting from live Live USB but was not able to start the Gparted as it was too slow ie i waited for 30-40 minutes for the program to start and i tried this for 4-5 times then I gave up and and deleted them as mentioned above.

Also when I am trying to install  Xubuntu , why am I getting the out of frequency message. Is there any work around this?

---

### Post by fantab on 2013-04-12
You can use just use [Gparted Live]("http://gparted.sourceforge.net/livecd.php"). 

Re-reading your posts.. Why not try your old screen and see if that sorts out the issue " out of frequency". This generally happens if the "refresh rate" of your monitor is set too high than it supports. Perhaps you can boot with UbuntuLiveUSB and set the display to any supported resolution and refresh rate. you can use Ubuntu System Settings - Display to reset. [More info]("http://askubuntu.com/questions/153040/frequency-out-of-range-please-change-display-mode").

---

### Post by anshulsingh on 2013-04-12
> **fantab said:**
> You can use just use [Gparted Live]("http://gparted.sourceforge.net/livecd.php"). 

Re-reading your posts.. Why not try your old screen and see if that sorts out the issue " out of frequency". This generally happens if the "refresh rate" of your monitor is set too high than it supports. Perhaps you can boot with UbuntuLiveUSB and set the display to any supported resolution and refresh rate. you can use Ubuntu System Settings - Display to reset. [More info]("http://askubuntu.com/questions/153040/frequency-out-of-range-please-change-display-mode").

I have tried to run Gparted from Live Ubuntu USB, Hiren boot CD and also Ultimate boot Cd .It did not run I think the software is too heavy for my machine.
XUbuntu is suppose to run on old hardware. Why am I getting this message while performing fresh Install?

---

### Post by fantab on 2013-04-13
I suspect that the monitor is not running on supported resolution and/or refresh rate. Try to unplug the monitor and re-plugin. 
The Gparted only LiveCD/USB is very light weight. Just follow the gparted link I gave you.

OR

There could be some failing Hardware on your machine.. its a guess.

---

### Post by anshulsingh on 2013-04-13
> **fantab said:**
> I suspect that the monitor is not running on supported resolution and/or refresh rate. Try to unplug the monitor and re-plugin. 
The Gparted only LiveCD/USB is very light weight. Just follow the gparted link I gave you.

OR

There could be some failing Hardware on your machine.. its a guess.

Hi I downloaded Gparted and deleted the complete HD with it and then formated it NTFS to install XP. There was no luck with installing the XP.

Meanwhile I replaced the old monitor with the LCD to install Xubuntu. I was able to pass all the boot screens to a state where it asks me to choose language. At this point i was getting the display on only half of my screen (top half and that too was fuzzy) the bottom half was black . [IMG]http://en.community.dell.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-19-54-92-05/laptop_5F00_screen_5F00_2_5F00_20x20.JPG[/IMG] [IMG]http://i45.tinypic.com/24b4ro3.png[/IMG]


I was barelyable to readfrom the screem. [COLOR=#ff0000]The above images are kind of example that i have attached to demonstrate the kind of image that i was getting. It is not a actual screenshot ot the screen My screen only was on top half of the monitor the bottom half was black.[/COLOR]
The auto adjustment and the mannual adjustment buttons on the LCD did not resolved the problem.

With Gparted i was getting the display on complete screen on both the monitors. So i think it should not be a problem due to a failing hardware.Any ways how can i test that if one of my hardware is failing.

Any work around this problem is appreated

---

### Post by fantab on 2013-04-14
What Graphics card do you have on your machine?

Instead of installing xubuntu rightaway, can you load a live desktop? I mean, are you able to "Try (X)Ubuntu"?

Tell us what happens if you append '[**nomodeset**]("http://ubuntuforums.org/showthread.php?t=1613132")' option to the kernel line at boot.

---

### Post by anshulsingh on 2013-04-14
> **fantab said:**
> What Graphics card do you have on your machine?

Instead of installing xubuntu rightaway, can you load a live desktop? I mean, are you able to "Try (X)Ubuntu"?

Tell us what happens if you append '[**nomodeset**]("http://ubuntuforums.org/showthread.php?t=1613132")' option to the kernel line at boot.
I dont have a dedicated graphic card on my machine.
The screen is too fuzzy to read what different options are available to me ,I could only make out that there were different language option to choose from .I couldnot even make clear where my mouse pointer was on the screen.

---

### Post by fantab on 2013-04-14
There will be a graphic card, either built in to the mother board or separate. Without it, I don't think there won't be any graphics. Some Graphic driver are not well supported in Linux and for such cards there is often a workaround.

---

### Post by anshulsingh on 2013-04-14
> **fantab said:**
> There will be a graphic card, either built in to the mother board or separate. Without it, I don't think there won't be any graphics. Some Graphic driver are not well supported in Linux and for such cards there is often a workaround.

My motherboard is **KOB P4M266a NDM****x** and processor isintel celeron

---

### Post by squakie on 2013-04-15
Obviously a driver problem, but you can't really solve a driver problem at that point.  However, there are options you can try - like VGA= and a mode number or other boot options that should be able to at least get you booted.  I am curious of something though:  did you make an installation media on the USB, or did you make a bootable Ubuntu installation on the USB?  If you did the 2nd, you would also have needed to create it with persistence or it won't remember anything from boot to boot.  I ask this because the normal installation process isn't going to bring up a browser as shown in one of your screen posts.  In fact, I'm curious as to what you are doing when you show a capture of Internet Explorer running.  If you want to delete Ubuntu and reload Windows and you can't get your Windows USB to boot, then you should look into what you did to create the media.  The media must be bootable, and that selection will need to made at the time you are building the USB.  In addition, the USB will need to be, I believe, and Windows install media, not a running Windows installation.  You should be able to find the answers you need for all the Windows problems in a Windows forum.  For Ubuntu, read up on boot options for video and how to specify them.  You will find many things - such as the VGA= parameter - in that reading.  I still suspect, however, that you have created a running installation on USB - if you want to install it, create an install media on USB.

---

### Post by anshulsingh on 2013-04-15
> **squakie said:**
> Obviously a driver problem, but you can't really solve a driver problem at that point.  However, there are options you can try - like VGA= and a mode number or other boot options that should be able to at least get you booted.  I am curious of something though:  did you make an installation media on the USB, or did you make a bootable Ubuntu installation on the USB?  If you did the 2nd, you would also have needed to create it with persistence or it won't remember anything from boot to boot.  I ask this because the normal installation process isn't going to bring up a browser as shown in one of your screen posts.  In fact, I'm curious as to what you are doing when you show a capture of Internet Explorer running.  If you want to delete Ubuntu and reload Windows and you can't get your Windows USB to boot, then you should look into what you did to create the media.  The media must be bootable, and that selection will need to made at the time you are building the USB.  In addition, the USB will need to be, I believe, and Windows install media, not a running Windows installation.  You should be able to find the answers you need for all the Windows problems in a Windows forum.  For Ubuntu, read up on boot options for video and how to specify them.  You will find many things - such as the VGA= parameter - in that reading.  I still suspect, however, that you have created a running installation on USB - if you want to install it, create an install media on USB.

Hi ,First of all I would like to clear the fact that the internet explorer image in the previous post is just to convey that how a fuzzy screen looks like in my case.When i searched for the keyword fuzzy computer screen on the internet I got a lot of different images and i selected the one in which the noise and disturbance looked like mine. This image is not the actual image of my case as I was not able to capture one.

Secondly I have not installed the Ubuntu on my USB but created the bootable USB Using Unibootin in my first attempt and with Linux-live-usb-creator in second step.In my second step i assigned a persistance of 256 mb.In both the attempts I was getting distorted screen.

I am not trying to install windows at this step.The above image should be looked only to get an idea of kind of distorted screen that i am getting.

I have reformed my original post to better convey my problem. Please look back in to the original post to get a better understanding of my problem.

---

### Post by squakie on 2013-04-16
Did you read up on the boot parameters that can be used for video as I recommended?  It still applies.

---

### Post by squakie on 2013-04-16
The reason I ask you to look up these boot parameters is that right now the horizontal and vertical scan rates are out of range for your monitor, and this is giving you screwy screen.  If you select one of the lower VGA= values, say the 24 or 32 bit for 800x600, it will hopefully adapt the scan rates so that perhaps your screen will be clear.  If you can get that part, you can install the appropriate video driver after you install - just don't over shoot the scan rates on your monitor.

---

### Post by anshulsingh on 2013-04-18
> **squakie said:**
> The reason I ask you to look up these boot parameters is that right now the horizontal and vertical scan rates are out of range for your monitor, and this is giving you screwy screen.  If you select one of the lower VGA= values, say the 24 or 32 bit for 800x600, it will hopefully adapt the scan rates so that perhaps your screen will be clear.  If you can get that part, you can install the appropriate video driver after you install - just don't over shoot the scan rates on your monitor.

Where do I select these lower VGA values.I found this link on mofying VGA values
[http://pierre.baudu.in/other/grub.vga.modes.html](http://pierre.baudu.in/other/grub.vga.modes.html)  but I cannot find menu.lst file on my installation media. Is this what you meant to say in your previous post?

I also followed the following link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) but as you see in my original post no such screen is available to me during the boot.

---

### Post by feketedani4 on 2013-12-11
I have the same motherboard, and the integrated graphic card isn't compatible with ubuntu from the 11.04 version. Try it with an AGP video card. For the boot problem, try to do a BIOS upgrade [http://www.mercury-pc.com/downloads_list.php?productid=333](http://www.mercury-pc.com/downloads_list.php?productid=333). And sorry for my bad English..

---

### Post by wlraider70 on 2013-12-11
Have you considered a Command Line only setup? It seems daunting at first, but you get used to it.

---

