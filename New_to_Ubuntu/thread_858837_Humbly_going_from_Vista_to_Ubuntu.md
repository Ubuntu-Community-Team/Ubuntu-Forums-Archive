---
title: "Humbly going from Vista to Ubuntu"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Pastortom on 2008-07-14
Hay Guis!

I've been a faithfull Windows user since 1992, but now I've had it.. I installed Windows Vista and I've gotta say this operating system is more annoying than anything I've ever tried.. I really really hate Windows Vista.. 

My main reason for this is because every time I boot up my computer Vista totally and utterly refuses to recieve a completely healthy internet connection.. It bugs out totally and gives me all kinds of buggs and errors when I know the internett connection is 100% working.. Everything from "Limited or no connectivity" to "Invalid IP" to "THere are more than one connection to this computer", Ive been sitting probably in total about 9-10 hours trying to get Vista to accept the damn internet connection.. through my research Ive discovered that the explanation is most likely related to my spesific internal network card, the vista "compatible" driver for this network card, the router (D-link DIR-615) and the ADSL modem.. 

ANYWAYS, to my point.. 

I wanna completely forget about Windows, and go for Ubuntu Linux (as Ive been told this is in general the best Linux OS to go to after getting so used to Windows for 16 years).. 

But before I do, I wanna make sure my unique work related situation is 100% supported.. 

I use many different programs throughout the day that are workrelated like the following:

* Maximus Firmware Toolbox 4.5 (For the use of programming and patching XBox 360 dvd-drives through SATA)

* GQ-4X (for SST bios/firmware chip programming with Willem External Programmer through USB)

* Mamut (Norwegian database economic registration system)

* Newsleecher (Usenet client)

* Other flash related programs (USB/SATA/LPT1/COM)

etc etc.. 

I also use other software that I would like to be able to continue to use under Ubuntu Operating System..

Now, I've got some small amount of experience when it comes to Linux in general.. but not much, and I absoluteley prefer the GUI that Ubuntu comes with contra the plain command line that the experts might prefer.. but as far as I know the only way to allow Windows applications to be run under Linux you need some sort of Windows emulating software like "Wine"..  

So, does Wine support the programs Ive listed above? the drivers that is needed by Windows to allow these programs to communicate externally are mostly just USB related and general standard Windows .Net software.. will this be allowed and work well under Wine with Ubuntu as OS?

I also would like to have the famous game World of Warcraft accessable through Ubuntu some way, but dunno if Wine supports this as well, and/or how good considering the graphic engine support etc.. 

When it comes to other uses, like music players (Screamer Radio), video editing (Adobe Premiere Pro), plain document writing (OpenOffice), burning software (CloneCD) and etc Im guessing there are some pretty awesome replacements for Linux, am I right?
and if not, I guess you can emulate these as well with Wine?

Last question, when allowing Windows software to run with Wine, does that also include device drivers, dll drivers and hardware ports? Like my graphic card, sound card, network card, etc under Wine?

I would like the transition from Vista to Ubuntu to go as smooth and painless as possible, so any advices when it comes to software that could help me out here would be deeply appreciated.. 

THanks

---

### Post by BGFG on 2008-07-14
I'd suggest you dual boot for a bit. Get your feet wet. take a week or two to  acclimatize and test. 
I use imgburn and infrarecorder in wine with no problems at all. And with dual booting you lose nothing at all. It's either ubuntu is your new home, or because of your special circumstances you have to put up with windows for a bit more.....

Best of luck man...

The WINE homesite also has a listing of all it compatible software

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by bodhi.zazen on 2008-07-14
Well , first, welcome to Ubuntu.

Now the bad news, Linux is not a drop in replacement for Windows.

Wine is not so (new) user friendly. Simple applications work well, complex applications do not.

In general you will be best off if you can find a Linux Native application.

You could look at these links : 
[http://linuxappfinder.com/windows](http://linuxappfinder.com/windows)
[http://doc.gwos.org/index.php/AppHelper](http://doc.gwos.org/index.php/AppHelper)

The other option, especially as you transition, is to run windows in VMWare , VirtualBox, kvm.

---

### Post by anjilslaire on 2008-07-14
Interesting. What kind of work are you in that involves patching 360 drives? Last I checked, there weren't any authorized 360 repair centers for MS in Norway...

---

### Post by tuxxy on 2008-07-14
Welcome you made the right choice,

> My main reason for this is because every time I boot up my computer Vista totally and utterly refuses to recieve a completely healthy internet connection.. It bugs out totally and gives me all kinds of buggs and errors when I know the internett connection is 100% working.. Everything from "Limited or no connectivity" to "Invalid IP" to "THere are more than one connection to this computer", Ive been sitting probably in total about 9-10 hours trying to get Vista to accept the damn internet connection.. through my research Ive discovered that the explanation is most likely related to my spesific internal network card, the vista "compatible" driver for this network card, the router (D-link DIR-615) and the ADSL modem..

I had some funny issues when I tried Vista too, it would D/C after 20 minutes of being online with the only solution being reboots... lol

Now all them main work applications you listed either work in WINE, you can check the WINE website for what is supported and if there not just load windows in virtualbox and use as normal ;)

The secondary apps you list there are great replacements for as you say and a much greater selection

---

### Post by kansasnoob on 2008-07-14
I'll second the suggestion to do a dual boot. That way you'll have your old OS to revert to while you work out any issues, get past the learning curve, etc. Below is a very simple guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by BGFG on 2008-07-14
I forgot the virtual box option. i use both that and wine. although for me VB was just a project. I installed xp then sp2 then realized i had nothing else to do in windows. so i deleted the Virtual machine. VB integrates wonderfully with the network devices though. Simultaneous browsing in both OS'es are a breeze.

But it's true, i don't know what in greyskull happens in the back of vista. but in Ubuntu i have a lot more bandwith.

I think you should be safe and dual boot till you achieve a comfort level and can make your own informed decision.

---

### Post by Pastortom on 2008-07-14
Thank you all for your replies, Im really looking forward to really throw myself into the awesome software world of Linux Ubuntu.. 

I'm now burning out Kubuntu-8.04-dvd to install Ubuntu as dualboot to my already existing Vista OS, and since Ive already prepared for this 6 months ago I can use my 20gb partition on my 10 000 rpm's 74gb WD sata2 harddrive, to avoid shrinking in vista etc.. 

But in general, when it comes to driversupport for differnet kind of hardware, will there be any problems for me?

I've got a Asus Asrock 939-SATA2 motherboard, with XFX Nvidia PCI-E 7950GTX graphic card, SATA1 and SATA 2 harddrives (74gb, 320gb, 2x 750gb), Sata and USB internal cards, etc.. 

Especially considering Asrock isnt that known, will Ubuntu have any troubles understanding all the different hardware integrated in the motherboard? Remember I used Redhat linux awhile ago, and it didnt find the network card at all :) But this was probably 5 years ago, so that might explain it.. 

Thanks again guys, awesome replies, hope anyone got any advice to my above worries when it comes to Ubuntu.. 

and to answer anjilslaire reply:

In Norway people who buys XBox 360 consoles would rather go to a amateur electronic service worker like myself instead of waiting 2-3 months for Microsoft to fix their XBox 360's..  + They also prefer taking backups of their original XBox 360 games, so their families with kids wont ruin the original ones with scratches/bitemarks etc.. 

Hope that answered your question, anjilslaire..

Thanks again, guys!

---

### Post by munkyboy on 2008-07-14
You can get newsleecher to work through wine, but if you want a decent native News Reader and Binary reader, Ive found Klibido works best.

---

### Post by Pastortom on 2008-07-14
> **munkyboy said:**
> You can get newsleecher to work through wine, but if you want a decent native News Reader and Binary reader, Ive found Klibido works best.

Sweet.. thanks :)

---

### Post by Ahunt on 2008-07-14
Just some suggested reading to prepare any Windows user for Ubuntu:

    * Is Ubuntu for You? by A.Y. Siu [http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)
    * The Linux Desktop Myth also by A.Y. Siu [http://ubuntucat.wordpress.com/2006/07/28/the-linux-desktop-myth/](http://ubuntucat.wordpress.com/2006/07/28/the-linux-desktop-myth/)
    * Linux is Not Windows by Dominic Humphries [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
    * Ubuntu Criticism & FAQ by wiki.ubuntu.com [https://wiki.ubuntu.com/CriticismFAQ](https://wiki.ubuntu.com/CriticismFAQ)

All of these are a bit harsh in my opinion - Ubuntu 8.04 works better than you might think from those articles, but they will give you some food for thought.

I agree that partion, dual boot and patience ar eth best ways to proceed.

---

### Post by Pastortom on 2008-07-14
Well, I just tried installing Ubuntu, 3 different ways, each resulting in the infamous "Blank Screen".. 

Is my hardware really that messed up?

Is blank screen normal, and should I just wait 10 minutes to see if something happens?

I tried "safe graphics mode" and the "Live" option but nothing works.. Ubuntu progress bar just fills up and then blank screen like the monitor isnt getting any videofeed or the computer is off..

---

### Post by Ahunt on 2008-07-14
During my last install I got a black screen, waited about 40 minutes to find that all was well - it had just gone into screensaver mode after the install, which only took about 20 minutes. The default screensaver is black. Hope your situation is as simple.

---

### Post by bodhi.zazen on 2008-07-14
In general, hardware support is better on Linux then on Windows in that Linux runs on more hardware then Windows.

Not much help though if your hardware is giving you a problem.

I do not see any major issues with the hardware you listed, go ahead and install and let us know if you have problems.

---

### Post by timjohn7 on 2008-07-14
> **Pastortom said:**
> Well, I just tried installing Ubuntu, 3 different ways, each resulting in the infamous "Blank Screen".. 

Is my hardware really that messed up?

Is blank screen normal, and should I just wait 10 minutes to see if something happens?

I tried "safe graphics mode" and the "Live" option but nothing works.. Ubuntu progress bar just fills up and then blank screen like the monitor isnt getting any videofeed or the computer is off..

Hi,
Although some of your hardware sounds a bit exotic, you should have no problem with Ubuntu.  It may take a while to get the answers to all the eccentricites, but to date (6 months) I have always been able to solve my problems.

Regarding the blank screen during installation, reduce your screen resolution to VESA (800 x 600) for install and then adjust it up to your desired settings once installation is finished.

I have had lots of problems with Wine, but almost none with VBox... I highly recommend it and there are plenty of posts for resolving issues which you may have.

I still have a Windows partition, but I don't know why.  The 2 or 3 software apps that I was using under windows (ie no adequate Linux replacement) run fine in VBox.  I have resized my win partition down twice and the next time could be goodbye forever.

I think that the main advantage of switching to Ubuntu is that my interest in my computer & computing has been reawakened and its fun again... not without problems, but nothing like the pure frustration of Win hassles.

Also, the help available in this forum is quick, knowledgeable and friendly... as opposed to MS.

Regards,

Tim

---

### Post by kansasnoob on 2008-07-14
> Especially considering Asrock isnt that known, will Ubuntu have any troubles understanding all the different hardware integrated in the motherboard? Remember I used Redhat linux awhile ago, and it didnt find the network card at all

Possibly! I prefer Ubuntu by far but I've found that Linux Mint does seem to play nicer with some networking situations (Ubuntu Intrepid Ibex is supposed to be far improved in that regard come October). I've had screen resolution problems with every Kubuntu install I've done, but they've all been reasonably easy to work out.

This is why I prefer a dual boot. If Kubuntu doesn't suit your fancy you can change it to a Gnome desktop or it can easily be deleted with Gparted and then you can try something different. I read somewhere that there are now as many Linux distros as there are Linux users:)

Ya gotta love the choices!

---

### Post by kansasnoob on 2008-07-14
You'll find this invaluable:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by Martje_001 on 2008-07-14
> **Pastortom said:**
> Well, I just tried installing Ubuntu, 3 different ways, each resulting in the infamous "Blank Screen".. 

Is my hardware really that messed up?

Is blank screen normal, and should I just wait 10 minutes to see if something happens?

I tried "safe graphics mode" and the "Live" option but nothing works.. Ubuntu progress bar just fills up and then blank screen like the monitor isnt getting any videofeed or the computer is off..
When you get the blank screen do this (if you have more than 1GB memory):

Press CTRL + ALT + F1. You'll get a terminal. Type:
```
sudo apt-get -y install envyng
```
this installs the program 'envyng' which is used to install videocard drivers. Now do:
```
sudo envyng
```
and choose your option.

Press CTRL + ALT + F7/8/9 until you have the blank screen again. Now press CTRL + ALT + BACKSPACE. Does it work?

*Note: Do not restart when envy ask you to!*

---

### Post by Martje_001 on 2008-07-14
Ow and btw, sabnzbd is (if you only download via nzb's) a very good replacement for newsleecher! See my signature, the program is not in the Ubuntu repository's.

---

### Post by krendar on 2008-07-14
For newsleecher replacement try the HellaNZB/LottaNZB combination.

First download Hellanzb via Ubuntu's repositories. Using Synaptic find and install **HellaNZB** and **Unrar** (for some reason unrar is not a requirement to install hellanzb although hellanzb does not start without it).

After that is installed go to Lottanzb's homepage and download the ubuntu package ( [http://lottanzb.org/](http://lottanzb.org/) )

Hellanzb is a commandline appplication, LottaNZB makes it easier by being a GUI application and it integrates fine with Firefox.


World of Warcraft works perfectly fine on Ubuntu via the Wine-emulator. I always use the guide on the ubuntu wiki for a flawless installation:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Pastortom on 2008-07-14
Thanks alot guys..

But Im still having some troubles installing Ubunto unto my computer.. 

Ive got 3 harddrives internally installed, 2x 750GB SATA2 drives and 1x 74gb 10 000 rpms WD harddrive (Vista partition 30gb and 34gb free for Linux)..

I got the installer to work through Text-base mode and I chose the MBR to be written to allow Ubuntu to dual boot as a choice with Vista.. but when I restarted the computer, Vista booted up automatically.. So I tried to install Ubuntu again, with the same options, to make sure I wasnt doing anything wrong and still nothing..

I tried reading up on some bootloader issues and used Easy BCD to try and fix this, so I installed Ubuntu again and chose not to write the MBR but instead write to the Bootsector of the Linux Native Partition (Harddrive 0, Partition 1) and used EasyBCD in windows to create a GRUB loader referring to that partition.. 

But when I restarted and it seemed to work I got this screen:

Ubuntu (and some numbers)
Ubuntu (and some numbers) safemode
Ubuntu (and some numbers) memtest
Other OS:
Windows Vista/Longhorn bootloader


So I chose the 1. option and I got this error message: 
"No Such Partition"

So I chose 'e' to edit the first chooice and noticed that for some reason it was pointing to harddrive 2 and partition 4 (2,4) which is completely wrong.. and I changed it to harddrive 0 and partition 1, which Easy BCD states that the Linux Native partition is installed on.. But when I pushed 'b' to boot this option another error message came up :"Cannot Mount Selected Partition"..

Why the hell is this so incredibly hard?

I got a computer with Vista installed on, I created a free partition for Linux to be installed on, I followed all instructions and have both tried writing the bootsector to the LInux partition (alternative) and the normal way by writing MBR to the Vista partition, but nothing works..

The strange thing is that EasyBCD shows this as the valid (0,1) Linux Native bootsector:

Name:  Ubuntu
BCD ID:  {38efe763-51d1-11dd-9de8-00138fa2c40c}
Drive:  C:\
Bootloader Path:  \NST\nst_grub-878B3A6C0CD1344D5FB50B4CF7AF689C.mbr

which is completely wrong, as its not the C:\ Drive which has this partition.. but Harddrive 0 and partition 1.. Vista is located on Harddrive 0 and partition 0.. why doesnt this work?

---

### Post by Pastortom on 2008-07-14
Finally, some progress, after extensive research and forum lurking I found out the following:

It's possible to edit Grub loader if the partition set to load Ubuntu is wrong (i.e. set to HD1,4 when HD0,4 is the correct one)..

Super Grub is an awesome automated program which should fix any issue with GRUB during bootup, and automaticly set the bootup to load GRUB and set the right partition for Ubuntu (in my case 0,4)..

I tried first Super Grub, but it hung at the following line:

Running "embed/boot/grub/e2fs_stage1_5(HD0)"

and the above lines on my screen (didnt write them down :P) said that it found the Ubuntu kernel and the necessary files to make GRUB able to load Ubuntu when chosen to.. so I realised from the above lines that it wasnt HD0,1 which I had thought from before and which Easey BCD tells me, but indeed HD0,4 which Super Grub told me.. 

So I rebooted, went into Grub loader, pushed 'e' to edit the first line and chose: root (HD0,4) instead of (HD2,4) which was implented from before.. then I pushed esc and 'b' to boot the line "root (HD0,4)" and everything worked fine.. I thought.. for about 15 seconds..

I saw the Kubuntu loading screen, and I even saw a mouse arrow come up on the screen, but then total freeze.. I couldnt push num lock, and the HD led was continues lighting.. same as before when Super Grub ran "Running "embed/boot/grub/e2fs_stage1_5(HD0)""..

Now, at least Ive come abit further in my hellroad to learning Ubuntu.. but this is really really annoying guys, its like I hit one wall trying to install Ubuntu, then I found out how to go further, but then hit another wall, then another wall, then another wall.. its like theres no end to all the walls Im supposed to hit before I can finally browse [www.google.no](www.google.no) under OS Ubuntu =(.. 

Help?!

---

### Post by kansasnoob on 2008-07-14
Well, #1 just Google LVM, but also twice last week I had to switch friends computers from using GRUB (which had worked fine for quite a while) to using Vista's boot-loader. I don't know why. I used page 4 of this guide to do it:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

But you can at least boot Vista right?

Therein is the beauty of a dual boot rather than just jumping in before testing the water. Just take a deep breathe, take time to calm down and come back to it when your mind is clear.

How large of a partition is Ubuntu on?

Personally I can see things much more clearly with screenshots from Gparted if that's possible. I just can't do menu.lst stuff.

---

### Post by bodhi.zazen on 2008-07-14
Looks like you are trying to install with wubi. Why not go the standard route ?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by kansasnoob on 2008-07-14
As long as you can boot Vista do NOTHING until you calm down! Angry minds don't work clearly!

Your install is not easy, it's complicated. I started with a test box with one 30gb hard drive. Believe me this can all be worked out.

Where would you be now if you'd ditched Vista altogether and had no OS?

I need to go help prepare about 80 chickens for market but I'll check back then.

---

### Post by kansasnoob on 2008-07-14
> **bodhi.zazen said:**
> Looks like you are trying to install with wubi. Why not go the standard route ?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Wow, I didn't catch that, thanks! I thought they used the alternate CD:confused:

---

### Post by Pastortom on 2008-07-14
Im using "!RnE - 2008.07.14 06.28.17 - kubuntu-8.04-dvd-i386"

Which is the standard DVD-version of Ubuntu 8.04 and not the alternative version..

For those of you that havent read this entire thread:
I tried to install using the normal solution and not the text-based mode first, but my computer froze after Kubuntu had loaded finished and my screen power button flashed like it didnt get any videofeed or like when the computer is turned off.. 

So I tried the text-based mode installation, and it seemed to work fine.. and Ive followed this guide: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

on how to make a successfull dual boot Vista and Ubuntu when already having Vista installed first, but when I came to the last option with Ubuntu installer I chose to write MBR to the Vista partition (as the guide said) and that I would get Grub on my next bootup, which I didnt..

Vista started automatically after the Ubuntu install and Ive been at this for 12 hours now, trying to figure this out.. 

I pushed Ctrl+Alt+F2 during bootup of the Ubuntu CD to see what fdisk would have to say on the partitions, and it showed Linux Native partition as /dev/sda5 but the VIsta partition as /dev/sda1 and flagged for bootup choice.. 

So, by following this guide: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux) I tried to install Ubuntu again but this time exclude the MBR writing of Grub and instead just write the bootsector to the Linux Native partition (HD0,4) as the guide said.. but when I restarted and had configured the new option with EBCD I got error during bootup etc..

So I used Super Grub to try and find out what I did wrong, and I learned that the Linux partition drive was HD0,4 and not HD1,5 or whatever EBCD told me.. and through Super Grub and some help from EBCD I managed to get Ubuntu to load up.. 

(as explained above by pushing 'e' to edit root and changing it to root (hd0,4) which is where the Ubuntu partition is located.. )

But when Ubuntu was finished with loading and was going into the GUI I noticed the mouse popping up in the middle of the screen but then it froze and totally crashed.. 

I even tried rebooting and pushing control + alt + "-" or control + alt + "+" to change the video resolution fast enough before it crashed, as this is most likely the reason for it crashing, using a faulty driver or fauly resolution for my graphics card..

Im soo tired of this.. but Im somehow making progress, so could someone hint me in the right direction here? Shall I reinstall Ubuntu? Shall I Use Supergrub again? or how can I make this work?

---

### Post by bodhi.zazen on 2008-07-14
I suggest you fall back to "standard" methods.

First, what is your videocard again, nvidia ?

Second, use the desktop CD, or possibly the DVD. Boot the DVD -> On the first screen, select your language (English) THEN USE BOOT IN SAFE GRAPHICS.

If that fails -> alternate CD.

Post install we can install the nvidia drivers.

It looks like you are trying to configure the windows boot loader ...

---

### Post by BGFG on 2008-07-14
Since you know for sure which partition you're using now, i'd do a re-install. Not like there's anything for you to loose in kubuntu. 
Just so you have some hope, i too use EasyBCD and my system dual boots perfectly.
I know this may argued by others, but i noticed you're using kubuntu. how bout trying an ubuntu install. you can always just change the desktop to KDE once you're up and running. I only say this cause my ubuntu install went flawlessly and i have no experience with kubuntu.

---

### Post by Pastortom on 2008-07-14
Okey, Ive now managed to write GRUB to the MBR and it seems to bootup properly when I restart my computer, but still it freezes when I choose to load the Ubuntu kernel.. it loads up, shows the nice splashlogo but when the meter fills and its supposed to show the GUI with a mouse and everything it just freezes.. Really annoying..

I did this to manage to write GRUB to the MBR:
----------------------------------------------------------------
grub> root (hd0,4)
grub> setup (hd0)

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded... Succeeded

Running "install /boot/grub/stage1_5(hd0) (hd0)1+16 p (hd0,4) /boot/grub/stage2/boot/grub/menu.lst"... Succeeded
Done.

grub>
----------------------------------------------------------------

After I did this I rebooted, and now instead of Vista bootloader the GRUB bootloader started automaticly, and I got 3 Ubuntu choices and 1 Vista choice.. 

So I hit Ubuntu, but as stated in the beginning of the post it just freezes.. when I hit Vista in the grub installer it says "NTDLR Missing, push Ctrl+Alt+Del" so I did and edited the Vista protocol in Grub and for some weird reason it said (hd2,0) for Vista.. and (hd2, hd0), (hd0, hd2) on the next lines..  so I changed the first line to root (hd0,0) and when I then booted Vista bootloader started and I could boot up to VIsta fine..

After these 12 hours of hard research and work I have managed the following:

To install Ubuntu and Grub bootloader on a Vista computer with dualboot option, but still not able to actually boot into Ubuntu..

Who would have known, huh? 12 hours.. just to install Ubuntu and get Grub to work.. Now I have to use god-knows how many hours to get it to actually bootup.. 

Im giving up for now, Im tired and annoyed.. and my roomate wants his internet back (Vista wont accept my DIR-615 router, even though 5 other computers with XP on the same network does, so Ive been connected straight up to the ADSL modem all this time)

But tomorrow I will try some more, or perhaps later tonight.. 

So, please.. anyone.. help me out here..

are there any options to set the GUI that Ubuntu uses and shows after the loading bar fills up to the lowest graphic resolution? or some how force a safe-mode bootup? cause Im betting theres a graphic driver issue here, that makes my computer freeze every time Ubuntu loads up

---

### Post by Pastortom on 2008-07-14
> **BGFG said:**
> Since you know for sure which partition you're using now, i'd do a re-install. Not like there's anything for you to loose in kubuntu. 
Just so you have some hope, i too use EasyBCD and my system dual boots perfectly.
I know this may argued by others, but i noticed you're using kubuntu. how bout trying an ubuntu install. you can always just change the desktop to KDE once you're up and running. I only say this cause my ubuntu install went flawlessly and i have no experience with kubuntu.

I have no idea why I chose Kubuntu.. I was searching on newzbin and didnt see any difference between Xubuntu, Kubuntu and Ubunut :confused::confused:..

But downloading "Ubuntu 8.04 (Hardy Heron) - Desktop CD x86" version now, and I will try the normal installation, hopefully that will work..

---

### Post by bodhi.zazen on 2008-07-14
Progress :)

Boot -> at the grub screen select the other ubuntu, recovery mode

From there try the "xfix" option -> safe graphics (vesa)

I think part of the problem is you chose several non-standard installation techniques :)

The other part is you do not know enough about Linux yet. If you think that was bad, try installing Vista without your recovery disk :)

---

### Post by Pastortom on 2008-07-14
Thanks mate.. I will try..

But now Ive gotten another issue that somewhat frightens me..

I tried running EasyBCD, and it gives lots of errors regarding the MBR, and EBCD cant fix it.. it gives this last error:

"The store import operation has failed.
The requested system device cannot be found"

and I know its related to Vistas bootloader, since in succeeded in writing the grub bootloader to vistas partition and by doing so overwriting vistas bootloader in some form.. but am able to boot vista through editing Grubs vista choice and choosing root (hd0,0).. 

Ive learned alot these last hours, and Ive had some progress, Ill just hope this normal "ubuntu-8.04-desktop-i386" fixes all issues  and works as it should :) If not, Im going to bed ^^

---

### Post by BGFG on 2008-07-14
Dude.... Ok first, i think you should run a disk check and allow it to repair any errors in windows before anything else. After that a recent system restore if the disk check doesn't work. that error does not look promising

[http://neosmart.net/forums/showthread.php?t=2052](http://neosmart.net/forums/showthread.php?t=2052)

[http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/](http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/)

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

hope these links help man....
May linus be with you....

---

### Post by Pastortom on 2008-07-14
> **BGFG said:**
> Dude.... Ok first, i think you should run a disk check and allow it to repair any errors in windows before anything else. After that a recent system restore if the disk check doesn't work. that error does not look promising

[http://neosmart.net/forums/showthread.php?t=2052](http://neosmart.net/forums/showthread.php?t=2052)

[http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/](http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/)

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

hope these links help man....
May linus be with you....

FINALLY!!

Ive managed to get Kubuntu 8.04 up and running.. as well as the normal Ubuntu 8.04.. sitting on Kubuntu now and everything seems to work pretty good..

I only have ONE big problem though.. and while I found a temporary solution to this problem I found out why Ive had problems with installing Ubuntu from the start.. And yes, Im talking the ground zero for all the problems Ive had since my first post in this thread.. 

The reason why Ubuntu ALWAYS froze during either install GUI or bootup GUI after successfull install was this: ACPI caused complete and utterly CRASH..

All I had to do to make Kubuntu and Ubuntu load was the following:
add ACPI=off and VGA=773 at the end of the kernel line, and I also removed 'splash' 

Then both OS's boot up perfectly..

Now my only problems so far are these 3:

1) My bootloader wont work as it should, and I have to manually edit the first line to make it boot the correct kernel in the correct partition.. so for now I have to edit Root (HD1,4) to Root (HD0,6) and then it chooses the correct partition for the ubuntu kernel.. 

I've tried Super Grub and reinstalling Ubuntu 6 times to fix this, still wont work.. the only way I managed to get Grub to replace Vista's bootloader was to manually type this during a EDCB instated Grub command line:
Root (hd0,4)
Setup (hd0)

(hd0,4 was my previous partition for Ubuntu)

but I still have to manually change the Root(hdx,x) line for Grub to find the correct partition..  How can i fix this?

2) As default ACPI is enabled and because of this during the GUI bootup (startx or what its called) it totally crashed and freezes my computer.. by manually typing ACPI=off in the end of the kernel line in Grub I can skip this and manage to load the GUI/startx.. 
How can I fix this? 

I also added VGA=773 and removed 'splash' but havent found out if these are also needed to manage bootup.. 

3) Vista's bootloader is totally screwed and the only way I can bootup to Vista is through Grub and manuall editing the Root line to look like this:
Root (Hd0,0)
and then push 'b' to bootup.. and firs then the Vista bootloader appears and lets me choose windows Vista to bootup.. 

I would like to thank all of you for helping me out so far, if it wasnt for your continues help I wouldnt have managed to keep at it and discover the solution, or at least, parts of the solution to my problems..

:guitar::popcorn:

---

### Post by kansasnoob on 2008-07-14
> All I had to do to make Kubuntu and Ubuntu load was the following:
add ACPI=off and VGA=773 at the end of the kernel line, and I also removed 'splash'

GREAT! Sorry to shout but that's worth a shout! Hopefully you'll be able help someone else with a similar problem somewhere down the road.

But since you say, "Ive managed to get Kubuntu 8.04 up and running.. as well as the normal Ubuntu 8.04." I think it's time to back off abit and see just what you have where. With 3 hard drives and multiple partitions that's not simple and I absolutely can't deal with complicated menu.lst's.

It would be a good time to look at Gparted (aka, Partition Editor) NOT TO MAKE CHANGES, but rather just to see what you have where!

Now, I'm not sure this will work but I don't see how it can break anything, and I'm not sure if this works the same in Kubuntu, but in Ubuntu if you install the simple gui "startupmanager" by going to Synaptic Package Manager you may be able to change much of what you need to change without much work.

I must get back to cleaning chickens (it's slaughter day) but I'll be back with some screenshots and stuff. 

Just be patient!

---

### Post by Pastortom on 2008-07-14
> **kansasnoob said:**
> GREAT! Sorry to shout but that's worth a shout! Hopefully you'll be able help someone else with a similar problem somewhere down the road.

But since you say, "Ive managed to get Kubuntu 8.04 up and running.. as well as the normal Ubuntu 8.04." I think it's time to back off abit and see just what you have where. With 3 hard drives and multiple partitions that's not simple and I absolutely can't deal with complicated menu.lst's.

It would be a good time to look at Gparted (aka, Partition Editor) NOT TO MAKE CHANGES, but rather just to see what you have where!

Now, I'm not sure this will work but I don't see how it can break anything, and I'm not sure if this works the same in Kubuntu, but in Ubuntu if you install the simple gui "startupmanager" by going to Synaptic Package Manager you may be able to change much of what you need to change without much work.

I must get back to cleaning chickens (it's slaughter day) but I'll be back with some screenshots and stuff. 

Just be patient!


Thanks mate.. but what the hell does ACPI=off do? and what the hell is it for? Excuse my french, but something tells me this isnt the permanent fix to my problems, rather cutting off the broken arm instead of bandaging it..

---

### Post by kansasnoob on 2008-07-14
Advanced Configuration and Power Interface

I'm not that smart, I just Google!

[http://en.wikipedia.org/wiki/ACPI](http://en.wikipedia.org/wiki/ACPI)

---

### Post by a0u on 2008-07-14
FYI, ACPI allows the operating system to control power distribution to peripherals.  The OS can instruct the BIOS to power down peripherals when they are not needed, primarily as a means of conserving power in laptops.

---

### Post by kansasnoob on 2008-07-14
Just a bit of reading tells me that ACPI is honed to help Windows configure the hardware resources! It's possible that might benefit you with Vista if you ever change hardware.

What I'd like to see, and please wait for a second opinion here, is just what your drives and partitions look like. Mine is very simple right now:

[ATTACH]77763[/ATTACH]

You see in the upper right hand corner where mine says "/dev/sda (bla-bla)"? That's where you can select drives to LOOK AT! I shout "look at" because you want to absolutely know what you're doing from here forward. I'd say NOT to do anything until it's been verified by a second source

Many people will try and decipher your menu.lst which is fine, but verify!!!! Three hard drives and who knows how many partitions and what they hold is nothing to approach willy-nilly!

I CAN NOT deal with menu.lst's. the long columns of #### which is the Linux way of "commenting out" entries triggers seizures for me. I can not and will not do it!

More to come1

---

### Post by BGFG on 2008-07-14
Glad to see you're up and running now man... You guys have gone a bit past my level now but i use QGRUB editor for maintenance. Hope this helps
and best of luck  ;)....

---

### Post by kansasnoob on 2008-07-14
Sorry, other things to tend to. What I'd like to see you try is installing startupmanager in whatever Ubuntu distro you want to use. I think it's more likely to work with the last distro you installed.

From what you've said that's Ubuntu, eh? If so, after you're booted into Ubuntu, go to System > Administration > Synaptic Package Manager and search for startupmanager. 

[ATTACH]77765[/ATTACH]

Once it's installed you can look at the menus in it by going to System > Administration > StartUp-Manager ........... and you'll see this:

[ATTACH]77766[/ATTACH]

[ATTACH]77767[/ATTACH]

[ATTACH]77768[/ATTACH]

[ATTACH]77769[/ATTACH]

Now, digest that and I'll be back.

---

### Post by kansasnoob on 2008-07-14
You see on the first screen shot (Boot Options Tab) where it says Default Operating System? Click on the "up-down" arrows and see if it shows all your OS's. Like this:

[ATTACH]77770[/ATTACH]

Then you can select which OS to boot first!

Neat huh?

I'm sorry you had so much trouble, but now you can see why it was wise not to just pitch Vista, I only wish I'd asked how many drives/partitions you already had.

Honestly I'll never understand why someone would trust so much data to any installed drive. And you were ready to blame Vista for all your problems. Maybe data management is part of the problem, eh?

---

### Post by bodhi.zazen on 2008-07-14
Welcome to Ubuntu :)

Yes it takes a while to learn a new OS, be patient.

Well done by the way.

Best link on GRUB :

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Pastortom on 2008-07-15
> **Martje_001 said:**
> Ow and btw, sabnzbd is (if you only download via nzb's) a very good replacement for newsleecher! See my signature, the program is not in the Ubuntu repository's.

Hi again bud, Ive gotten Ubuntu 8.04 to run very smoothly so far..

Just tweaking and configuring some small stuff before I crash my bed.. 

About your NZB program, considering since Im so new to Linux theres plenty of stuff I dont know yet, what about automatically unpacking of rar files?

I use newzbin.com every day and I would prefer an automatic unpacking of rar files like Newsleecher offers.. Does your NZB program support this? if not, do you know of one that does?

Also, to the rest of you Linux gurus, Ive tried to configure Start-Up Manager to fix Grub permanently, as its been a pain in the *** ever since I managed to manually write it to the MBR of my HD0 (vista and linux partitioned harddrive).. 

Every time I reboot it shows Ubuntu as "root(hd3,4)" when its supposed to be "root(hd0,4)" and I have to manually edit this every time.. same goes for Vista, I have to manually type in "root(hd0,0)" to be able to boot into Vista's bootloader.. real pain in the ****..

Anyon got a clue how to fix this permanently?

And, again, thank you all for your patience with me as well as your advices, Ive spent around 20 hours trying to get Ubuntu up and running, and finally Im sitting here playing with fancy effects, listening to Daft Punk on Rhythmbox, surfing the net with Firefox and enjoying the full resolution with installed 3D drivers for my Nvidia 7950GTX PCI-E graphic card..  This is indeed the best OS Ive ever used.. I get a mental-orgasm every time I notice it automatically installing codecs and drivers for whatever I need at the time.. this is BLISS! I LOVE UBUNTU!

---

### Post by Pastortom on 2008-07-15
Then I've finally managed to edit the Grub bootloader, and now everything works fine.. Ubuntu boots ubuntu and Vista boots vista :)

Used this guide to edit Grub: [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Now I only need to successfully mount the windows harddrives (NTSF)..

---

### Post by bodhi.zazen on 2008-07-15
Add your changes to the configuration file, open a terminal

```
gksu gedit /boot/grub/menu.lst
```

On the top of the file you will see configuration options.

Grub is different from linux in that NORMALLY lines with a # are comments

# Like this

BUT in grub, lines with a SINGLE # == configuration, and two ## = comments

## Comments
# Option / configuration.

Now, edit the top of the file to point to the correct root partitions.

Edit the bottom of the file

title Ubuntu
root (hdx,y)
kernel
initrd

See the grub link I gave you for details (I know it is a little long, but it reviews grub).

See also : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

---

### Post by Pastortom on 2008-07-15
> **bodhi.zazen said:**
> Add your changes to the configuration file, open a terminal

```
gksu gedit /boot/grub/menu.lst
```

On the top of the file you will see configuration options.

Grub is different from linux in that NORMALLY lines with a # are comments

# Like this

BUT in grub, lines with a SINGLE # == configuration, and two ## = comments

## Comments
# Option / configuration.

Now, edit the top of the file to point to the correct root partitions.

Edit the bottom of the file

title Ubuntu
root (hdx,y)
kernel
initrd

See the grub link I gave you for details (I know it is a little long, but it reviews grub).

See also : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")


Thanks mate.. but Ive managed to fix Grub more or less, Vista choice boots vista (without going through Vista bootloader:)) and Ubuntu choice boots ubuntu.. but whenever my external harddrive (containing just iso files and mp3's) isnt hooked up, Grub malfunctions, and gives me error 22.. Im guessing this has to do with the GRUB harddrive and partition interpretation (hd0 = /dev/sdda1) etc..  Ill look into it with the link you gave me.. 

my biggest issue now is not being able to mount windows harddrives properly.. Ive tried editing the fstab file for mounted drives, using this guide: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) but it doesnt work, and it doesnt look the same as in the guide, it gives error at the line Ive edited after I save it and mount.. 

Any ideas?

---

### Post by bodhi.zazen on 2008-07-15
What partition are you trying to mount (in Linux speak please), what line in fstab, and what error message ?

It sounds like grub is installed in your external drive, you can install it into your MBR (of your internal drive).

---

### Post by jhenager on 2008-08-05
bodhi's got the right advice for you, my friend.

---

### Post by silverglade00 on 2008-08-05
Pastortom, 

I just wanted to interject for a moment. I have been reading this thread and watching as you come in with a problem, take advice, then leave for a while. When you come back, you have managed to struggle and google your way a little further to the next hurdle. You are learning a lot about GRUB, Linux, partitioning and other Linuxy things by asking for advice and searching on your own. By these virtues alone, you have shown that you are the perfect kind of person to go very far in using Linux. We have all struggled to learn a new way of doing everything on a computer. We have all had problems with Linux that were impossible to solve... until we did. Please don't give up. Trust me. It will all be worth it when you finally get it working and a whole new world opens up for you. This struggle sucks now, but once you get it going, you will start out with a good base of knowledge that will come in very handy as you keep exploring.

In short, you're gonna be just fine :)

Edit:
I just scrolled down a little more and saw that you got it going. Congrats and welcome! You will probably be the answering the questions on here in a day or two!

---

