---
title: "newbie looking for some basic help"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by mattfurlani on 2008-09-17
Hi everyone.

I decided after rumors of better operations that I would install UBUNTU on my computer. 

I don't understand much and I'm trying to do things I didn't know how to do in windows or was easier.

I have two major problems right now and i imagine they will lead to more issues later. But for the time being I do not have the proper 'drivers' for my video card and java script has **** the bed. So no online games or 3d games at all. not even super chess.

I downloaded JavaScript programs 5 and 6 control panel and their respective policy tools (none of which I understand how to use) plus something called openJDK 6 policy tool. 

I have no leeway on the Video driver although I have identified something called nividia X may be on my computer. I don't know but it seems like looking through my list of available supported downloads that it has something to do with video cards.

on another note, I have a program i found called wine which seemse to be how you make some windows games work for your compy. don't know how to use that but somehow that doesn't matter yet because i have no 3d.

sub secondly, is there a program that will turn my word processor 'OpenOffice.org' into a windows compatable file so I can have people read attachments that i have written.

and finally my wireless card also has no driver and if anyone knows how to work on that i'd be happy to listen. 

I know i should some UBUNTU for dummies guide but right now i'm more concerned with rent and college to have the motivation to read through 100 pages of 'how to' stuff. I will hopefully find someone who can help me

SO

IF you know any of this... the most important right now is the video driver thing. Please help and feel free to point out my newbness. I know its bad.... yeah

TY


Matt

---

### Post by panhandle on 2008-09-17
To your most-important question,open a terminal and type the following command:

```
lshw -C video
```

This will list your VGA controller and will help with installing the correct drivers. Post the results here.

As for your wireless card:

```
lshw -C network
```

so we can get started.

As for openoffice, when you "save as" you'll be able to select the format of the file.

What exactly is wrong with Javascript? Can you use the quick reply box at the bottom of this page?

---

### Post by sudo_chop on 2008-09-17
> **mattfurlani said:**
> 
 
sub secondly, is there a program that will turn my word processor 'OpenOffice.org' into a windows compatable file so I can have people read attachments that i have written.
 

 
Sorry, I can only help you with the least of your problems, as I know nothing about driver issues. But, OpenOffice should give you the option when you are saving a file to save it as a .doc which is the MS Word file extension.
 
Have no fear, others will chime in about the driver stuff.
 
-sudo chop

---

### Post by porchrat on 2008-09-17
Open Office can save files as a .doc (windows format) which will make it readable under windows...merely select .doc as the file suffix when you use the "save as" function under the "file" menu.

the java version I would recommend you use is the sun java 6 version.  To set it type this into the terminal (you will find the terminal under accessories in the top left corner of your screen):

```
sudo update-alternatives --config java
```

Then select the java-6-sun option by typing in the number that corresponds to it on the list that you are presented with (on this list will be java 5 and the openJDK).

There is definately a thread that already exists somewhere on this forum to help you with your wireless card but in order for us to direct you to the right one we need to know what wireless card you are running...to do this please type the following command into the terminal:

```
lshw -C network
```

Copy and paste the ouput and post it on this thread so we can take a look.

Hope this helps

(please note that linux is generally case sensitive so you need to use a capital C)

---

### Post by Paqman on 2008-09-17
Regarding your graphics and wireless drivers: have you checked in the Hardware Drivers manager to see if Ubuntu is suggesting a driver to install? Go to System > Admin > Hardware Drivers.

As for Java, there is a great package called ubuntu-restricted-extras that includes Java, multimedia codecs and a whole bunch of other handy stuff. It's usually one of the first things I install.

---

### Post by panhandle on 2008-09-17
Along the lines of Paqman's comments, consider the following thread for the your multimedia needs:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

This is an excellent guide.

---

### Post by mattfurlani on 2008-09-19
TY everyone for your suggestions. I will try this when i get home... whenever that happens. I appreciate your time and effort and will get back to you guys tomorrow afternoon. 

On a side note, sorry to the forum I swore. I don't even realize it etc etc. I used to be in the Marines so swearing is a facet of my being.

Anyways update you laters, bye

[-o<

---

### Post by mattfurlani on 2008-09-20
> **Paqman said:**
> Regarding your graphics and wireless drivers: have you checked in the Hardware Drivers manager to see if Ubuntu is suggesting a driver to install? Go to System > Admin > Hardware Drivers.

As for Java, there is a great package called ubuntu-restricted-extras that includes Java, multimedia codecs and a whole bunch of other handy stuff. It's usually one of the first things I install.


paqman, I have a 'Atheros HAL '(hardware acess layer) and a 'support for atheros 802.11 wireless lan card'

it says nothing else about anything

---

### Post by k33bz on 2008-09-20
for your wireless we ned to start by identifying your wireless card. In the terminal type this in and paste results here.

```
lspci
```

---

### Post by mattfurlani on 2008-09-20
> **panhandle said:**
> To your most-important question,open a terminal and type the following command:

```
lshw -C video
```

This will list your VGA controller and will help with installing the correct drivers. Post the results here.

As for your wireless card:

```
lshw -C network
```

so we can get started.

As for openoffice, when you "save as" you'll be able to select the format of the file.

What exactly is wrong with Javascript? Can you use the quick reply box at the bottom of this page?

the network and the video both lead me to the same menu which says this

matt@matt-laptop:~$ lshw - version
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

matt@matt-laptop:~$ 


so i don't know how to ask it what version of hardware i have maybe you could explain this menu to me a little bit?

ty

---

### Post by mattfurlani on 2008-09-20
> **panhandle said:**
> Along the lines of Paqman's comments, consider the following thread for the your multimedia needs:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

This is an excellent guide.

ty ty ty i got javascript 6 openjdk to work. now when i'm bored i can play my silly free online games :) you all have made me a little happy. i'm still working on the video card drivers problem

---

### Post by mattfurlani on 2008-09-20
> **k33bz said:**
> for your wireless we ned to start by identifying your wireless card. In the terminal type this in and paste results here.

```
lspci
```

matt@matt-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by hyper_ch on 2008-09-20
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by mattfurlani on 2008-09-21
well I dunno i guess i figured it was the simplest way to describe my problems. next time i'll break it down more though. do you have any advice about the video driver?

---

### Post by perlluver on 2008-09-21
Your video card is a SIS Vga, as far as I know there are no Proprietary drivers for that, only the open source ones that come with the kernel.  What kind of problems are you having with it?

---

### Post by mattfurlani on 2008-09-22
it does not support any sort of complex/three dimensional games or things like that. If i try to run a game it either says that it will not support the game or it is so slow i can't play it. even games that aren't truly 3d

I know this computer is capable of 3d because i can play runescape and other online games which are 3d

i dunno if that answers your question?

---

### Post by perlluver on 2008-09-22
> **mattfurlani said:**
> it does not support any sort of complex/three dimensional games or things like that. If i try to run a game it either says that it will not support the game or it is so slow i can't play it. even games that aren't truly 3d

I know this computer is capable of 3d because i can play runescape and other online games which are 3d

i dunno if that answers your question?

Indeed that stems from the open source drivers, SIS, is only supported via open source.  Intel, Nvidia, and ATI, will all run 3d effects, and 3d games.  But Nvidia and ATI, have proprietary drivers, as in not maintained by Ubuntu, or Linux.  As far as I know, with a SIS onboard graphics driver, 3d effects won't run in Ubuntu.

---

### Post by mattfurlani on 2008-09-22
> **perlluver said:**
> Indeed that stems from the open source drivers, SIS, is only supported via open source.  Intel, Nvidia, and ATI, will all run 3d effects, and 3d games.  But Nvidia and ATI, have proprietary drivers, as in not maintained by Ubuntu, or Linux.  As far as I know, with a SIS onboard graphics driver, 3d effects won't run in Ubuntu.

so i cant play 3d games on my compy w/o windows?

what am i supposed to do?

---

### Post by porchrat on 2008-09-25
> **mattfurlani said:**
> so i cant play 3d games on my compy w/o windows?

what am i supposed to do?

Dual boot anyone?

---

### Post by WWSmith36 on 2008-09-25
Secondly regarding Open Office

Sometimes documents don´t visualize exactly the same in Open Office as they do in MS Word. This is a font related issue

Install msttcorefonts

Enable the multiverse repository:

Open System->Administration->Software sources-> [ Tab Ubuntu software ]
enable "Software restrictecd by copyright or legal issue ( multiverse )"
Close and confirm the repository reload.

```
sudo aptitude update
sudo aptitude install cabextract
sudo aptitude install msttcorefonts
```

---

### Post by stalkingwolf on 2008-09-25
> Install msttcorefonts
This is part of the " restricted extras" package.

You can dual boot or run windows in a virtual machine for your games.

---

### Post by mattfurlani on 2008-09-25
> **WWSmith36 said:**
> Secondly regarding Open Office

Sometimes documents don´t visualize exactly the same in Open Office as they do in MS Word. This is a font related issue

Install msttcorefonts

Enable the multiverse repository:

Open System->Administration->Software sources-> [ Tab Ubuntu software ]
enable "Software restrictecd by copyright or legal issue ( multiverse )"
Close and confirm the repository reload.

```
sudo aptitude update
sudo aptitude install cabextract
sudo aptitude install msttcorefonts
```



So this program will automatically reformat my open office.org files into the correct format of msword? what exactly does it change? When i chnage he format in openoffice it will make sure it dosn't come out all messed up when someone opens it in windows?

---

### Post by mattfurlani on 2008-09-25
> **stalkingwolf said:**
> This is part of the " restricted extras" package.

You can dual boot or run windows in a virtual machine for your games.

Will windows come with the SiS driver? I've been looking forward to learning Linux. Windows would take up another X number of GB of hardrive space. My father has a free Xp can you dual boot with XP?

---

### Post by stalkingwolf on 2008-09-30
Not sure about the driver.

Yes you can dual boot with XP.  You can install 8.04 inside xp (wubi).

When you finish your document in OO.O and save it you can choose to save it as a .doc(xp format) file or several other options.  You can also save it as a PDF or print it directly as I recall.

---

### Post by mattfurlani on 2008-10-03
> **stalkingwolf said:**
> Not sure about the driver.

Yes you can dual boot with XP.  You can install 8.04 inside xp (wubi).

When you finish your document in OO.O and save it you can choose to save it as a .doc(xp format) file or several other options.  You can also save it as a PDF or print it directly as I recall.

what about installing xp in ubuntu?

---

### Post by Ferb on 2008-10-03
> **mattfurlani said:**
> what about installing xp in ubuntu?

Why do you want to install xp in ubuntu is it game related? Or for a specific game? If it is game related virtual machine might not be your best option. 

BTW Have you cleared up the Open Office problem?

---

### Post by stalkingwolf on 2008-10-04
Yes you can install windows in a virtual box inside Ubuntu , but as stated
games may be an issue.  Also as I recall Ram is also an issue.  If you dont have enough everything is slow.

---

### Post by mattfurlani on 2008-10-04
> **Ferb said:**
> Why do you want to install xp in ubuntu is it game related? Or for a specific game? If it is game related virtual machine might not be your best option. 

BTW Have you cleared up the Open Office problem?

yes and i think so. I haven't sent any oo.o related files since... haven't tried it. but i'm sure its fixed

---

### Post by mattfurlani on 2008-10-04
> **stalkingwolf said:**
> Yes you can install windows in a virtual box inside Ubuntu , but as stated
games may be an issue.  Also as I recall Ram is also an issue.  If you dont have enough everything is slow.

my ram is an issue anyways.... an allmighty 400mb of it. anyways i'm collecting that a dual boot with xp is probably my better choice and just have windows for games and linux for all the important stuff. like school and such

---

