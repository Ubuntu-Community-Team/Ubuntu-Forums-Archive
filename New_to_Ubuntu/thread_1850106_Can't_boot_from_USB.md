---
title: "Can't boot from USB"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by BonbonRose on 2011-09-25
Hi all,

I was trying to try Ubuntu 10.04 (32-bit) but it won't boot.. 

In the boot menu, I get many options regarding booting form an USB; There is USB-FDD, USB-ZIP, USB-CDROM and USB-HDD.

I tried them all but only two, USB-ZIP and USB-HDD, responded. A window showing Ubuntu option list appears. When I choose to try Ubuntu, the screen for a second gets black with writing scrolling down fast  (something like the matrix effect) and then an (Ubuntu waiting screen with dots lighting up) shows and nothing happens. When I tried to get out of this window by pressing Esc, a black screen showed, reporting what's happening which was mostly repeating "can't open /dev/se0: no medium found"

Hope I was clear enough
Is there any information you need to now?
My USB is HDD0

---

### Post by wildmanne39 on 2011-09-25
Hi, it sounds like a the  files are corrupt, or it is not reading the usb right.

I suggest trying to download ubuntu again using the bit torrent option, it makes sure the files are good.

Also what version of ubuntu are you trying to install.
Thank you

---

### Post by BonbonRose on 2011-09-25
Hi,

Ok. I'll try the bit torrent and write back what happens. I was trying Ubuntu 10.04 (32-bit)

---

### Post by BonbonRose on 2011-09-28
Hi,

I downloaded the torrent and the same thing happened

---

### Post by wildmanne39 on 2011-09-28
Hi, you can try what this link says it may get you into ubuntu, but I am not sure about that exact error, I have been researching it but I did not find any exact answers.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I do not think this will help but it might.

How did you create the bootable usb? did you use the way the website said? 

How long did you wait when the screen with the dots came up? it takes a while for it to load when you use the cd.
Thank you

---

### Post by BonbonRose on 2011-09-28
Hi,

Ok, I'll check the link and get back to you.

I followed the instructions literally. 
As for me waiting, I think I didn't wait that long. As soon as I found these error reports the couple of times I tried to boot the USB, I would restart the PC. And finally I posted in here.

I found out from the BIOS window that my USB is HDD0, other than that I know nothing. So, I'm wondering is there any thing I should make sure of or do regarding my USB?

---

### Post by oldfred on 2011-09-28
My motherboard has all those USB options to boot. And when I first created a bootable Flash drive I also could not get it to boot. I tested it in my portable and it booted there, so I knew it was configured correctly.

Then one day I was playing with grub and installed it to another drive. When I went in to choose to boot another drive (and happened to have flash plugged in) there it was. Even with all the USB choices a flash drive is just seen as another hard drive.

I also can boot flash from f12 choose hard drive and then it is a choice. F12 is the one time boot key in my system.

---

### Post by amjjawad on 2011-09-28
Hi there,

Have you tried this [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) ???


Hello wildmanne and oldfred :)

---

### Post by WasMeHere on 2011-09-28
> **BonbonRose said:**
> Hi all,

I was trying to try Ubuntu 10.04 (32-bit) but it won't boot.. 

In the boot menu, I get many options regarding booting form an USB; There is USB-FDD, USB-ZIP, USB-CDROM and USB-HDD.

I tried them all but only two, USB-ZIP and USB-HDD, responded. A window showing Ubuntu option list appears. When I choose to try Ubuntu, the screen for a second gets black with writing scrolling down fast  (something like the matrix effect) and then an (Ubuntu waiting screen with dots lighting up) shows and nothing happens. When I tried to get out of this window by pressing Esc, a black screen showed, reporting what's happening which was mostly repeating "can't open /dev/se0: no medium found"

Hope I was clear enough
Is there any information you need to now?
My USB is HDD0

1. Maybe your system was still loading (during the waiting screen with dots lighting up) and you did not wait long enough for it to finish and arrive at the desktop screen. If the USB drive was not available to the system, I think there would be no waiting screen with dots.

2. How did you make the bootable USB? I have good experience with Unetbootin.

3. If your system treats your USB key as a hard disk, enter the BIOS menu and change the boot order so that the USB 'disk' is selected first.

*Edit: I agree with **kurt18947** that it can be important to prepare your USB drive in a good way. I use 'gparted' and delete whatever in on it before. Then I make a **FAT32 partition with boot flag and lba flag**. Make a label if you want to identfy it easily!*

---

### Post by kurt18947 on 2011-09-28
What motherboard or BIOS do you have? I have one desktop with a Gigabyte MoBo, 785 chipset and Award Modular Bios v. 6.xxx.  I prepared several bootable USB drives with both Startup Disk Creator and unetbootin.  The USB drives would boot in another desktop and a Thinkpad but not in this one desktop.  I'd get a "boot error" message or "grub rescue" prompt.  After some research the fix was to format the USB drive in Windows 7 then create the bootable Linux drive.  I'm not sure what the difference was but it did work.  If you have access to a Win 7 install that might be worth a try.

---

### Post by I2k4 on 2011-09-28
I've been running Live USB trying various versions for some months.  I suggest following these instructions very slowly step by step, using at least a 4GB USB and whichever Ubuntu ISO you want to try.  

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I  also suggest setting "Persistence" on the installer software to about 2.5GB, that way you can install extra software and save all your settings while testing out the installation.

First thing, of course, is to be sure that USB drive is set to be the first BIOS priority for booting.

---

### Post by mikechant on 2011-09-30
On my Dell 530 desktop, I've booted from an 8Gb USB stick (can't remember type), a 2GB SD card in a USB reader, and two 4GB Kingston USB sticks.
The first two can be set up and seen as if they are normal hard drives - i.e. with a partition table. The Kingston drives fail on boot if they're formatted that way and had to be formatted unpartitioned.
I think you can do this in Windows but I did it in Linux using the command
```
sudo mkdosfs -I /dev/sdx
```
changing sdx to whatever your USB stick mounts as and being sure to use 'sdx' not 'sdx1' etc.

then you can use unetbootin to install to the USB stick in the normal way. 

The general point is that different USB sticks behave differently when used as boot devices and how/whether they boot  will depend on the type of stick and the BIOS of the machine you're booting from. They were not necessarily designed as boot devices so this doesn't mean there's anything wrong with them!

---

### Post by BonbonRose on 2011-09-30
Hi,

I decided to try booting again and this time I waited. It took about one hour and a half for Ubuntu to open. Though I don't think so, is this normal?

---

### Post by amjjawad on 2011-09-30
> **BonbonRose said:**
> Hi,

I decided to try booting again and this time I waited. It took about one hour and a half for Ubuntu to open. Though I don't think so, is this normal?

1.5 hour? definitely it's NOT.

Edit: Not sure if it's mentioned somewhere here (sorry if I didn't go through the whole thread again) but have you checked MD5SUM for your downloaded image of Ubuntu?

---

### Post by WasMeHere on 2011-09-30
> **amjjawad said:**
> 1.5 hour? definitely it's NOT.

Edit: Not sure if it's mentioned somewhere here (sorry if I didn't go through the whole thread again) but have you checked MD5SUM for your downloaded image of Ubuntu?
*Better late than never* ;-)

What computer is it? Did it respond reasonably fast, when it finally had installed the live system? (Could you do normal tasks like browsing local files, browsing the internet, monitoring the system?)

Did your system fall back to USB 1.1? Or were there errors reading or transferring data from the USB drive? Or was it very difficult and time-consuming to identify the hardware of your computer?

---

### Post by amjjawad on 2011-09-30
Ok few words and I'm logging off ...

I have checked the thread and didn't find any post mentioning MD5SUM so that must be step no.1 IMHO.

Step no.2 is: if your current USB Drive didn't work, try another one.

As for BIOS, 99% I say it must be USB-HDD so I guess you are ok at that point but it must be something else that preventing your system from booting.

Finally, make sure you are following the right procedure to create your LiveUSB and most important than this, use a good tool for that and try to test it on another machine if possible.

That's all what I could think of :)

Good luck and keep us updated :)

Edit:
It might be worth to try another USB Port. Sometimes, there could be a problem with one particular port and it happened to me and others all the time so just try another USB Port, you won't lose anything ;)

---

### Post by BonbonRose on 2011-10-04
Hi,

> What computer is it? Did it respond reasonably fast, when it finally had installed the live system? (Could you do normal tasks like browsing local files, browsing the internet, monitoring the system?)I have XP Professional SP3. As soon as Ubuntu opened it was fairly normal and every thing opened well.

> Did your system fall back to USB 1.1? Or were there errors reading or transferring data from the USB drive? Or was it very difficult and time-consuming to identify the hardware of your computer? I just don't know where the problem is.

I've been trying to get the MD5SUM and found a number/ code. From what I got here [(https://help.ubuntu.com/community/HowToMD5SUM)]("http://ubuntuforums.org/I%20don%27t%20think%20it%27s%20what") I don't think it should be just a text. Also I'm not sure what I opened here at my PC is a terminal window. It's called "HyperTerminal" but it doesn't work, just some windows popping up.  (Start > All Prog. > Accessories > Communications > Hyper Terminal)

Can someone tell me what's wrong.. This is all new to me.

---

### Post by WasMeHere on 2011-10-05
1. Something went extremely slowly during the live boot with your usb stick. We don't know why. Maybe it would be faster with another stick. But I think that once booted, it's OK. From the live system, I think you can install Ubuntu to your hard disk and get a good operating system. I suggest that you install it side-by-side with Winxp (dual boot).

2. If you want to check the md5sum of a file run ```
md5sum filename
``` and compare the output with what you find via the internet, e.g.
```
8b1085bed498b82ef1485ef19074c281 ubuntu-11.04-desktop-i386.iso 
```

Edit: In Ubuntu you start a terminal window with *ctrl + alt + t*
or via the menu Program -- Accessories -- Terminal
In Windows the corresponding program is sometimes called DOSprompt or terminal window. I think you find in the menu All Programs -- Accessories. It is also started via 'run a program' with the command *cmd*

---

### Post by amjjawad on 2011-10-05
ALL what you need is here:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

and here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Read through these two and you'll be good to go.

---

### Post by BonbonRose on 2011-10-14
Hi, 

[LEFT]OK. I manged to open a terminal window in both Windows and Ubuntu, but I couldn't get the command line right. I tried everything in the "HowToMD5SUM" but I just get error messages like "not recognized as internal or external command" and "can't find the patch specified"

Sorry if this seems silly, but this is all new to me.
[/LEFT]

---

### Post by amjjawad on 2011-10-15
> **BonbonRose said:**
> Hi, 

[LEFT]OK. I manged to open a terminal window in both Windows and Ubuntu, but I couldn't get the command line right. I tried everything in the "HowToMD5SUM" but I just get error messages like "not recognized as internal or external command" and "can't find the patch specified"

Sorry if this seems silly, but this is all new to me.
[/LEFT]


Nothing called silly here as we are all learning so feel free to ask whatever you want ;)

If you are using Windows to check MD5SUM, then: [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

I could simply copy-paste and that's all but it's better to check the link :)
It looks easier in Windows if you are a Windows User more than a Linux User but IMHO, it's much easier in Linux because you don't have to install or download anything, it's all from Terminal.

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Linux](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Linux)

Just make sure you are on the right directory.
When you open the Terminal, you are actually in the **/home/yourname** directory by default.

If your iso in your Download Directory then:

```
ubuntu@ubuntu-desktop:~$ cd Downloads
```

Linux is case sensitive (like C Programming Language) so "Downloads" is not "downloads".

I think I see why you are confused. The Wiki page needs to be updated and I guess I'll do that.

Or you can simple place your iso file in your home directly and that's all.

Or ... k3b is a very powerful tool to create LiveCD or any other type and by default, it does calculate MD5SUM for you so you just need to compare that with the hashes.

It's so easy :)

---

### Post by amjjawad on 2011-10-15
I updated the **[page]("https://help.ubuntu.com/community/HowToMD5SUM")** but it needs more updates IMHO. I might do that later because I'm so tired now. Logging off :)

---

### Post by BonbonRose on 2011-10-15
WOW! that didn't even take a minute and the results were up, thanks :D 
Both MD5SUMs match.. Now, what's the next step?

---

### Post by amjjawad on 2011-10-15
> **BonbonRose said:**
> WOW! that didn't even take a minute and the results were up, thanks :D 
Both MD5SUMs match.. Now, what's the next step?

Yes, I understand why you were confused because the wiki page wasn't updated, it was talking about Ubuntu 8.04.
Glad you managed to do it :D

Well, your next step is: you need to create the Live Media (CD or USB).
If your machine is cable of booting from USB, please create a LiveUSB, this is how: 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Otherwise, just go classic and create the Live CD, this is how:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
Enjoy!


For USB, please make sure your BIOS is set to boot first from USB.

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]


Yes, I know your BIOS might look different but the concept is the same :)

---

### Post by bob53124 on 2011-10-15
Try Downloading PLOP boot manager burning it to a disk or a floppy and then select usb when it loads up or you could try a different port

---

### Post by oldfred on 2011-10-15
@amjjawad
I see you have rapid boot enabled. I do not and have seen one or two cases where that seemed to be the problem in getting system to see a USB drive or get keyboard working. I assume you have no issues.

---

### Post by naradluffy on 2011-10-15
I think your usb installer is corrupt. What's your installer program to make usb boot?

---

### Post by BonbonRose on 2011-10-16
I tried Universal USB Installer as recommended on the Ubuntu download page. Right now I'm trying again using UNetbootin.

Actually, I'm having difficulties with it.. 
In step two: extracting and copying files, when it reaches about 70%, the program becomes ''not responding'' for a third time in a row now. And I have to close it, delete the copied files and start all over again.

---

### Post by amjjawad on 2011-10-16
> **BonbonRose said:**
> I tried Universal USB Installer as recommended on the Ubuntu download page. Right now I'm trying again using UNetbootin.

Actually, I'm having difficulties with it.. 
In step two: extracting and copying files, when it reaches about 70%, the program becomes ''not responding'' for a third time in a row now. And I have to close it, delete the copied files and start all over again.

Just format your USB (FAT or FAT32) then try again. It happened with me before some times using UNetbootin.

---

### Post by amjjawad on 2011-10-16
> **oldfred said:**
> @amjjawad
I see you have rapid boot enabled. I do not and have seen one or two cases where that seemed to be the problem in getting system to see a USB drive or get keyboard working. I assume you have no issues.

Hello oldfred,

Yes, I have no problems at all. However, I'll double check to be extra sure :)
My BIOS can detect any USB and boot from it.

---

### Post by BonbonRose on 2011-10-25
Hi,

Ok. I tried UNetbootin and I got the same result; actually I tried other USBs using UNetbootin and Universal USB Installer and I got the same result.

In UNetbootin there's an option to check disk for defects and I got after two hours or maybe more: errors found in ''1" files!
Is there a way to get a report of this check to know what's the problem.

I don't know if that's how it supposed to be, but I noticed this in both UNetbootin and Universal USB Installer.. 
- During installation of the iso file to the USB and booting the "casper" file kind of hangs during the process.
- Even the USB is just reformatted my antivirus pops a window "Access to the file 'H:\autorun.inf' was blocked for your security."
Concerning this 'autorun.inf'.. At the end of installing the iso file using Universal USB Installer, the program reports an error message about it but I can't remember it literally.

Hope I was clear enough.. :?

---

### Post by amjjawad on 2011-10-25
Hi again,

Few questions:

1- Have you tried your Live-USB on another machine?
2- Are you using Windows or Linux to create that Live-USB?
3- If you are using Linux and you have GParted, have you tired this instead of formatting?

[IMG]http://ubuntuforums.org/picture.php?albumid=2395&pictureid=8073[/IMG]

4- How old your machine is? you didn't mention anything about it?!
5- When you boot from the Live-USB, do you see UNetbootin Menu? it last for 10 seconds so you can see it.
6- Where exactly your machine stops responding? at the UNetbootin Menu? at "Try Ubuntu without installation"? at the Ubuntu Logo and the 5 dots? or after that?

---

### Post by BonbonRose on 2011-10-26
Hi,

1. No, I haven't
2. I'm using Windows and this is my first Linux try.
4. It's about five years "young" now but I just had it upgraded couple of months ago.
Windows XP SP3, Pentium(R) Dual-Core CPU, 3.2 GB of RAM.. mm.. What do you want to know else?
5. Yes. I see the UNetbootin and Universal USB Installer Menus.
6. At the Ubuntu Logo and the 5 dots.

---

### Post by amjjawad on 2011-10-27
Hi :)

> 1. No, I haven't
If it's possible, try that :)

> 5. Yes. I see the UNetbootin and Universal USB Installer Menus.

Then I think the problem is not with your USB or anything related to that.

> 6. At the Ubuntu Logo and the 5 dots.
Have you tried this: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by oldfred on 2011-10-27
amjjawad's link on boot options is very good.

You may just want to try the f6 and add the nomodeset option as the link says. That often solves video issues. Sometimes other settings are required and you just have to experiment or search for someone with an identical computer to find the exact settings you need.

---

### Post by BonbonRose on 2011-10-30
Hi,

I don't know what to say to you.. : ( 
None of the things mentioned in that link appears on my screen.. the welcome page options, advanced welcome page nor the boot options.

Only in the Universal USB Installer Menu, there's an option "advanced options" but it's empty.. When I click it, the only option is "back".

---

### Post by amjjawad on 2011-10-30
> **BonbonRose said:**
> Hi,

I don't know what to say to you.. : ( 
None of the things mentioned in that link appears on my screen.. the welcome page options, advanced welcome page nor the boot options.

Only in the Universal USB Installer Menu, there's an option "advanced options" but it's empty.. When I click it, the only option is "back".

What is the FULL NAME of the iso file that you are using to create your Live Media and that you have downloaded?
It ends with ".iso".

---

### Post by BonbonRose on 2011-10-30
It's "ubuntu-10.04.3-desktop-i386.iso"

---

### Post by amjjawad on 2011-10-31
> **BonbonRose said:**
> It's "ubuntu-10.04.3-desktop-i386.iso"

Hi BonbonRose,

Before I completely be out of ideas, I'd suggest few things:

1- Please, read your entire thread again from the beginning. I just did trying to figure out what is missing so please try the same :) that does help sometimes. Usually, with so much suggestions, you could miss one or two points and it happens to me all the time.

2- What are the full details of your machine? or to be more accurate, what is your Graphics Card?
If your machine is 5+ years old, it's just like mine that I'm using now and it has Intel Graphics Controller:

```
*-display               
       description: VGA compatible controller
       [COLOR=Red]product: 82945G/GZ Integrated Graphics Controller[/COLOR]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: [COLOR=Red]driver=i915[/COLOR] latency=0
       resources: irq:16 memory:e0200000-e027ffff ioport:b000(size=8) memory:d0000000-dfffffff memory:e0280000-e02bffff

```

3- Just to make sure there is NOTHING wrong with your USB, please try it on another machine if possible. If you don't have another machine and can't even find one from a friend, try to use another USB Drive. If that is not possible, what's wrong with your CD Drive? If I remember correctly, I didn't read anything mentioned here related to your CD-Drive, I mean why not to try it as an alternative option?

4- Have you considered trying another Distribution? just to check what is going on? trying to use Ubuntu doesn't mean you'll be able to try and install it, sometimes you can't for some reason. Better to try another distribution and see whether that will work or not or try the latest version of Ubuntu (11.10) because it has the newer Kernel.
If you want to go for Ubuntu 11.10, download it, check MD5SUM and you know the rest :)
If you want to try another Distribution, I suggest Lubuntu, Xubuntu, Linux Mint 11 or any other Distribution but please ... don't confuse yourself. Trying lots of alternatives sometimes is a headache, ask me about that :D

So far, that is all what I could think about at the moment. Perhaps my other friends have better suggestions? 

Please do exactly what I have asked you to do and hopefully we could reach some where :)

Waiting for your reply :)

---

### Post by BonbonRose on 2011-11-08
Hi,

Ok. these what I managed to get is that all or there's something missing

```

Card name: Intel(R) G41 Express Chipset
Manufacturer: Intel Corporation
Chip type: Intel(R) 4 Series Express Chipset Family
DAC type: Internal
Display Memory: 1024.0 MB
Current Mode: 1024 x 768 (32 bit) (60Hz)
Monitor: Plug and Play Monitor

Driver Name: igxprd32.dll
Driver Version: 6.14.0010.5259 (English)
Driver Date/Size: 4/21/2010 02:42:38, 57344 bytes
WHQL Logo'd: Yes
Mini VDD: igxpmp32.sys
VDD: n/a
DDI Version: 9 (or higher)

```> Just to make sure there is NOTHING wrong with your USB, please try it on  another machine if possible. If you don't have another machine and  can't even find one from a friendI did that, and the same thing happened, but to be honest, my friend's pc might just be as mine except that I did an upgrade lately.

> what's wrong with your CD Drive?Nothing, I just thought using a bootable USB would be easier and more practical.

> Have you considered trying another Distribution?Yes, in fact I intended to try both Ubuntu and Mint's all editions because I don't know the difference between them yet.



I forget to post this last time. This window pops in the middle of creating the bootable USB; mainly in Universal USB Installer. 
[IMG]http://ubuntuforums.org/[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-10-21_154206.jpg[/IMG]
[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-10-21_154206.jpg[/IMG]

And I once got this too

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-11-06_042224.jpg[/IMG]

Hope this help moving things forward..
[IMG]http://s215.photobucket.com/albums/cc30/RosyIvory/?action=view&current=2011-10-21_154206.jpg[/IMG]

---

### Post by oldfred on 2011-11-08
Is avira your Anti-virus protection? It is set to prevent unauthorized booting of your system. You probably have to turn it off.

---

### Post by amjjawad on 2011-11-09
> **BonbonRose said:**
> I did that, and the same thing happened, but to be honest, my friend's pc might just be as mine except that I did an upgrade lately.

Hello again :)

1- If you have tried the same USB that you were trying on your machine and it failed to boot then it could be something wrong on that USB Drive. To make sure that stand correct:

a- Format by creating new partition table as explained previously and create FAT Partition then try again to create a Live-USB

b- Follow the same steps as (a) but on different machine - create the Live-USB on different machine.

If the same thing will happen yet again, I could only think of one thing - that USB is damaged.

 
2- If you tried ANOTHER USB Drive both on your machine and your friend's machine and it did NOT work, that means the process of creating the Live-USB is wrong, assuming that all other steps are done perfectly, like double check BIOS, MD5SUM, etc.

Other than above, I'm totally out of ideas :)

> Nothing, I just thought using a bootable USB would be easier and more practical.

I'm one of those who never give up and keep trying but to save time and effort, I would go for the easier solution - Keep It Simple and Short. Having that said, I'd suggest to go for Live-CD for now.
At least, you'll check your machine and see if there is nothing wrong with the booting Process.

By the way, not sure if I have mentioned that but if your Live-USB Failed to boot and your Live-CD will fail too boot, I suggest to reset your BIOS to its factory default settings **[COLOR=Red]BUT PLEASE DO NOT DO THAT if you don't know how to set some settings back.[/COLOR]**

> Yes, in fact I intended to try both Ubuntu and Mint's all editions because I don't know the difference between them yet.

Nothing much except Mint has more options than Ubuntu. You could try Ubuntu, Lubuntu, Xubuntu, Kubuntu which are the variants of Ubuntu. Or try totally different distribution.

> I forget to post this last time. This window pops in the middle of creating the bootable USB; mainly in Universal USB Installer. 
[IMG]http://ubuntuforums.org/[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-10-21_154206.jpg[/IMG]
[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-10-21_154206.jpg[/IMG]

And I once got this too

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-11-06_042224.jpg[/IMG]

Hope this help moving things forward..
[IMG]http://s215.photobucket.com/albums/cc30/RosyIvory/?action=view&current=2011-10-21_154206.jpg[/IMG]

As oldfred already suggested, try to turn your Anti-Virus off.
For me, I would suggest to try to create your Live-USB from different machine and/or Operating System. I assume you have XP and not sure how old that installation is but after all, you are using Windows and needless to say one of the reasons I'm using Linux is such error messages :P

Other than all what I wrote above, I have no more ideas!

---

### Post by BonbonRose on 2011-11-11
Hi,

Well, there's kind of a big problem apart from launching Ubuntu just happened.. 
I created the partition table but when I tried to create the Live-USB.. That's what I found

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-11-11_203318.jpg[/IMG]

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-11-11_203331.jpg[/IMG]

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/2011-11-11_203343.jpg[/IMG]

I don't know what to say.. Can it be fixed or what?

---

### Post by amjjawad on 2011-11-11
What did you do exactly?

---

### Post by BonbonRose on 2011-11-11
[LEFT]I launched Ubuntu from the USB, created a new partition table with the default setting, I believe it was msdos, because there was no FAT option in there.. Closed Ubuntu and checked to see what happened, then I found out the problem.. That's all.
[/LEFT]

---

### Post by amjjawad on 2011-11-11
> **BonbonRose said:**
> [LEFT]I launched Ubuntu from the USB, created a new partition table with the default setting, I believe it was msdos, because there was no FAT option in there.. Closed Ubuntu and checked to see what happened, then I found out the problem.. That's all.
[/LEFT]

Sorry but how did you launch Ubuntu from the USB if you can't create a bootable USB to begin with? I don't get it??!!

---

### Post by BonbonRose on 2011-11-11
I can launch it but it takes nearly 1.5 hour for Ubuntu to start.. That was the problem in the first place.

---

### Post by amjjawad on 2011-11-11
> **BonbonRose said:**
> I can launch it but it takes nearly 1.5 hour for Ubuntu to start.. That was the problem in the first place.
Sorry but this thread is quite old, from 2 months if I'm not wrong so I really need to go back to the beginning every time you post :)
However, I still think there is something missing.

To summarize:
Are you trying to tell us that you have a Live-USB that needs 1.5 hour to boot into Ubuntu? 
Then while you are logged in to the Live Session of Ubuntu from the Live-USB, you formatted the USB using GParted as explained before? 
Did you format the same USB that you are using to try Ubuntu? if that's what you are talking about so I think there is something wrong. You can't format while you are using it - please someone correct me if I'm wrong.

On another different note - no offense taken please - why it took so long? I already lost my focus because you post every now and then and I do need to go back to the first post to remember what we have done beside, you are not answering ALL the questions I'm asking you ... you go offline then come back with new thing :)

Sorry but I'm totally out of ideas!

---

### Post by BonbonRose on 2011-11-11
> Sorry but this thread is quite old, from 2 months if I'm not wrong so I  really need to go back to the beginning every time you post :smile:WOW, I didn't realize it's been that long.. Sorry for that :oops: 

> Are you trying to tell us that you have a Live-USB that needs 1.5 hour to boot into Ubuntu? Yes.

> Then while you are logged in to the Live Session of Ubuntu from the  Live-USB, you formatted the USB using GParted as explained before? Yes.

> Did you format the same USB that you are using to try Ubuntu? if that's  what you are talking about so I think there is something wrong. You  can't format while you are using it - please someone correct me if I'm  wrong.I thought that too but I did it anyway hoping nothing would happen. And nothing happened.. the Live Session kept going and I closed Ubuntu normally with no interruptions or anything like that.

> On another different note - no offense taken please - why it took so  long? I already lost my focus because you post every now and then and I  do need to go back to the first post to remember what we have done  beside, you are not answering ALL the questions I'm asking you ... you  go offline then come back with new thing :smile:Non taken.. I've been busy for quite sometime now and I couldn't follow up the topic right away besides it takes me sometime to figure out some of the things you're asking me due to my lack of knowledge :oops: But I'll try to be straightaway in my replies
I know you're helping me and I really appreciate that.. I do try to answer all I can and post back the results of what I've done.

---

### Post by amjjawad on 2011-11-11
Whenever you can't understand something whether from my post or anyone's else post, please ask :) don't think twice and ask right away and we'll be more than glad to explain more :)

Another thing which is so important. You need to follow up with your thread more often so you won't be lost and same applies to us :)

I got an idea while writing this. Why not create a LiveCD, boot your machine from it, plug your USB, start GParted, create new partition table and format it as FAT? 

I can't think of more at the moment :)

---

### Post by BonbonRose on 2011-11-11
> I got an idea while writing this. Why not create a LiveCD, boot your  machine from it, plug your USB, start GParted, create new partition  table and format it as FAT? I think that would be great too but If I did the LiveCD would I find the "FAT" option! Because I didn't find it when I tried to create the  partition table this time.

---

### Post by amjjawad on 2011-11-11
> **BonbonRose said:**
> I think that would be great too but If I did the LiveCD would I find the "FAT" option! Because I didn't find it when I tried to create the  partition table this time.

[http://forum.lxde.org/viewtopic.php?f=8&t=31411](http://forum.lxde.org/viewtopic.php?f=8&t=31411)

How about that? ;)

---

### Post by BonbonRose on 2011-11-11
I'll devour this and come back to you :biggrin:

---

### Post by amjjawad on 2011-11-11
> **BonbonRose said:**
> I'll devour this and come back to you :biggrin:
Just make sure you'll come back ... don't fade away ;)

---

### Post by amjjawad on 2011-11-11
On a side note ... why not try Lubuntu? :D
If you have any question regarding Lubuntu, have a look at my signature - Lubuntu One Stop Thread.

---

### Post by BonbonRose on 2011-11-12
Hi,

My updates..
I made a LiveCD but the computer didn't boot from it. So, I decided to re-download the iso file and start this all over again. But meanwhile I thought we can check my BIOS settings to make sure nothing wrong with them because I was able to boot from CDs before I change them to boot from the USB.

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/P1060021.jpg[/IMG]

Are these information enough or should I take some more photos?

---

### Post by amjjawad on 2011-11-12
> **BonbonRose said:**
> Hi,

Are these information enough or should I take some more photos?

Hi,

Let me check the screenshot and get back to you :)

---

### Post by amjjawad on 2011-11-12
What options do you have inside: **CD/DVD Boot Options**?

Does your machine skip booting from CD and go directly to Windows? or there is some kind of error message or something?

When you boot from CD, have you taken the USB out? unplugged it?

---

### Post by oldfred on 2011-11-12
In my BIOS USB-HDD never booted a flash drive. I always found USB flash drives under hard disk choices.

I prefer to set hard disk as first in BIOS and use one time boot key (f12 on mine) whenever I want to boot something else.

---

### Post by BonbonRose on 2011-11-12
> What options do you have inside: **CD/DVD Boot Options**? NON-EFI, EFI and AUTO

> Does your machine skip booting from CD and go directly to Windows? Yes.

> When you boot from CD, have you taken the USB out? unplugged it?      Yes.

> In my BIOS USB-HDD never booted a flash drive. I always found USB flash drives under hard disk choices.

I prefer to set hard disk as first in BIOS and use one time boot key (f12 on mine) whenever I want to boot something else. I just went with the basics I knew then and didn't want to change anything to just keep it going tell I'm done.

---

### Post by amjjawad on 2011-11-12
> **BonbonRose said:**
> NON-EFI, EFI and AUTO

 Yes.

 Yes.

Ok, keep that as AUTO and set the HDD to be the 2nd device to boot from while USB-HDD the 3rd. Let's see what will happen.

Have you checked MD5SUM and made sure you created a Bootable CD?

---

### Post by BonbonRose on 2011-11-12
Ok. and Yes, I checked. I followed the instructions in the download page literally.. Is there a way to check!

---

### Post by amjjawad on 2011-11-12
> **BonbonRose said:**
> Ok. and Yes, I checked. I followed the instructions in the download page literally.. Is there a way to check!

Either to create new Live-CD (burn it at the lowest speed - say 4x or 8x) OR try your current CD on different machine.

---

### Post by BonbonRose on 2011-11-12
:lolflag:  Hi

If you can't see me right now, I'm jumping here.. It worked perfectly.. I opened Ubuntu and closed it in less than 5min.. \\:D/ Though the case was like an earthquake going down there ; )

I used this > set the HDD to be the 2nd device to boot from while USB-HDD the 3rd But just remembered it was like this before ```
HDD to be the 2nd device and Legacy LAN as the 3rd
``` So I tried it, and it worked too.   

As for the USB I didn't find the "FAT" option in "create a new partition table".. So Do you know any other Linux distro that has this option and I could try it as well or at least an app that I can use separately to do so?

---

### Post by amjjawad on 2011-11-12
> **BonbonRose said:**
> :lolflag:  Hi

If you can't see me right now, I'm jumping here.. It worked perfectly.. I opened Ubuntu and closed it in less than 5min.. \\:D/ Though the case was like an earthquake going down there ; )

I used this  But just remembered it was like this before ```
HDD to be the 2nd device and Legacy LAN as the 3rd
``` So I tried it, and it worked too.   

Hahaha, well, I have told you that since long time but you insisted to use the USB :)
WELL DONE :)

I think you are stubborn just like me :P no offense taken yet again ;)

> As for the USB I didn't find the "FAT" option in "create a new partition table".. So Do you know any other Linux distro that has this option and I could try it as well or at least an app that I can use separately to do so?
As far as I know, GParted has lots of File Types and FAT is one of them. FAT32 should do the job too.

---

### Post by oldfred on 2011-11-12
Gparted can create FAT32 or NTFS. Only use FAT32 on flash drives or other smaller devices. Use NTFS to share with Windows for USB hard drives or internal drives to share with Windows. I prefer to use gparted to create partition in advance and then use manual install for all full installs.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Mikesla on 2011-11-12
Oops, I didn't read the original first. Please disregard.

---

### Post by BonbonRose on 2011-11-13
Hi,

> I think you are stubborn just like me :razz: no offense taken yet again :wink: You have no idea.. One time I kept trying like for 4 months :biggrin:

> As far as I know, GParted has lots of File Types and FAT is one of them. FAT32 should do the job too.     I took this screen cap from Ubuntu and these are only the available file types..
[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/Screenshot2.png[/IMG]

Is there anyone of them would work or will I have to download GParted separately just to fix the USB?

> GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) Thank you for the links : ) This tutorial really has some intense information.. It would take me quite sometime to comprehend it all.

---

### Post by amjjawad on 2011-11-13
You are looking at the wrong place. These types are NOT file types. These are the Partition Table Types. Just leave everything as it is please. "msdos" is the default.

Have you checked my GParted small guide? it should help you :)

File Types related to partitions. When you format a partition, you can choose what file type to use with that partition. Hope that helps :)

---

### Post by scradock on 2011-11-13
The screen-shot you show is showing the partitions of your main HD. DON'T mess with that!

Use the combo-box at the top right to find the partitions of the USB drive, which may be sdb or sdc, perhaps. It may look awfully uninteresting, but it will tell you what you do have on the USB drive.

Then, you need to Create a Partition, NOT create a partition table! Gparted will make a new partition table for you if there isn't one. Among the Partition Types you WILL find FAT32, NTFS, and a whole slew of others. The list you are showing above is a list of partition TABLE types, which you don't want to mess with.

Hope that helps - get back to us!

---

### Post by amjjawad on 2011-11-13
[http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

LXDE Website is down so I found this from the old days ;)

@oldfred
Do you remember that thread? :D

---

### Post by amjjawad on 2011-11-13
YES PLEASE DO NOT MESS WITH YOUR HDD PARTITIONS. You MUST select the correct drive which is as far as I think sdb NOT sda.

PLEASE pay more attention!!!!

---

### Post by BonbonRose on 2011-11-13
Then thank God I shot this picture.. I will go now and create a partition and get back to you and I will pay attention to the drive

---

### Post by amjjawad on 2011-11-13
> **BonbonRose said:**
> Then thank God I shot this picture.. I will go now and create a partition and get back to you and I will pay attention to the drive

Indeed Thank God :)

Take your time and be careful please :)

---

### Post by BonbonRose on 2011-11-13
It's good now.. the USB is acting normal but to be sure I took this 

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/Screenshot-Applyingpendingoperations.png[/IMG]

What do you think?

And just a quick question.. Is it normal that there's no internet connection when I run Ubuntu?

---

### Post by amjjawad on 2011-11-13
> **BonbonRose said:**
> It's good now.. the USB is acting normal but to be sure I took this 

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/Screenshot-Applyingpendingoperations.png[/IMG]

What do you think?

I think you are doing a great job and finally we can see some progress :)

Now, use UNetbootin to create the Live-USB.

My Signature > Lubuntu One Stop Thread > Section G > UNetbootin

> And just a quick question.. Is it normal that there's no internet connection when I run Ubuntu?
If you don't have Wired Connection (LAN) then yes, you need to connect to your Wireless Connection. Sometimes, Ubuntu detects your Network Adapters and sometimes it does not.

---

### Post by amjjawad on 2011-11-13
Please check the attached screenshot, I took it from your other post and cropped it.

Do you see the Wireless Icon next to your sound control icon? click on that and if you are lucky, it will detect your wireless network and you can connect to the Internet. If you don't have Wireless Internet anyway, usually it should be connected automatically to the LAN (Wired) Network but perhaps with 10.04 you need to click something over there (Network Applet).
God, I miss 10.04 ... it's totally different now :( that's why I'm not using Ubuntu anymore. Anyway ... just check and let us know. 

To be sure, you can run this command from Terminal:

```
sudo lshw -C network
```

This will show if you have the driver or not.

---

### Post by BonbonRose on 2011-11-14
Hi, 

The USB acted the same.. You mentioned before how the USB might be damaged, is that the case here?

As for the internet connection (DSL), I ran the command and got this

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/Screenshot.png[/IMG]

Just to know my way around.. What should I expect when I run Live CD/USB.. What should be working and what should not? What should be there and what should not?

---

### Post by amjjawad on 2011-11-14
> **BonbonRose said:**
> Hi, 

The USB acted the same.. You mentioned before how the USB might be damaged, is that the case here?

Hi,

Better to try it on another machine to make whether it's damaged or not. Or, try to save some data on it and see whether everything is ok or not. It could be your machine, not your USB or perhaps the other way around. 

> 
As for the internet connection (DSL), I ran the command and got this

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/Screenshot.png[/IMG]


Did you plug the LAN cable to your machine?
Are you using Wireless or Wired Network?


> Just to know my way around.. What should I expect when I run Live CD/USB.. What should be working and what should not? What should be there and what should not?
Yes. You can make sure whether Ubuntu will detect and will work well with your hardware or not without the need to install on the Hard Drive.

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[http://en.wikipedia.org/wiki/Live_CD](http://en.wikipedia.org/wiki/Live_CD)

---

### Post by BonbonRose on 2011-11-14
> Better to try it on another machine to make whether it's damaged or not.  Or, try to save some data on it and see whether everything is ok or  not. It could be your machine, not your USB or perhaps the other way  around. Ok. I'll work on that.

> Did you plug the LAN cable to your machine?
Are you using Wireless or Wired Network? I have Wired Network and made sure the cable is plugged.

Thanks for the links I'll start reading right now : )

---

### Post by amjjawad on 2011-11-15
> **BonbonRose said:**
> Ok. I'll work on that.
Yes please!

>   I have Wired Network and made sure the cable is plugged.

I haven't heard before about that Vendor of yours. Looks like Ubuntu didn't pick up the driver for that adapter.

Perhaps Wildmanne39 knows how to deal with such situation because he's better than me in Networking :)

> Thanks for the links I'll start reading right now : )
You welcome. At this point, the more you read, the better :)
I'm telling you that from experience. This is how I learned more about Linux. Of course reading and trying/doing that practically :)

---

### Post by BonbonRose on 2011-12-07
Hi,

I'm SO sorry for the late reply, I had some personal problems and I couldn't even open the computer. 
But I read the two articles, tried the LiveUSB on couple of different machines and made a Mint LiveCD for comparison.

  As you said and the articles stated, every thing should work and that did happen only when I used Mint LiveCD not Ubuntu's - except the internet. (I recently reformatted my PC completely, So  I don't have a wide variety of file extensions) but from what I have.. Ubuntu didn't open any kind of video or audio files including .mp3 .avi .mkv .flv .wmv .amr

[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/Screenshot1.png[/IMG]
[IMG]http://i215.photobucket.com/albums/cc30/RosyIvory/Screenshot2-2.png[/IMG]

As for the LiveUSB, 
-On a Windows 7 Ultimate, a black screen with "Windows Error Recovery" and "launch start up repair or Start windows normally" options.
-On windows XP SP2 the computer ignored/ couldn't feel the USB and started windows, though I adjusted the BIOS to boot from USB and used the f12 key many times.
-Finally to my relief that the USB isn't damaged *I'm still praying* On Windows 7 home edition it worked even better than the LiveCD. I almost forget.. I was able to log onto the internet when Ubuntu booted.

PS: Since I know nothing about these dark software stuff like the BIOS..etc. I can only use things you told me and don't mess with what I don't know. So there might have been something else to be done to these machines other than f12 and boot priority, and I didn't know about it or how to.



In the first link amjjawad gave me, [https://help.ubuntu.com/community/LiveCD#Other_Ways_to_Try_Ubuntu](https://help.ubuntu.com/community/LiveCD#Other_Ways_to_Try_Ubuntu) there was something about Wubi.. Do you recommend using it? Is there similar installations for other Linux distros? I tried searching this but I didn't find anything other than Ubuntu installer

---

### Post by oldfred on 2011-12-08
I often post this link on wubi from amjjawad.:)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

But wubi is good for very new users who only boot Windows and do not know how to repartition their system. It is more like an extended version of the liveCD, but does allow updates. It really is just a file inside the Windows NTFS partition, so if Windows gets corrupted, so is wubi. It also is limited on the size of the file you can make.

From the author of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by amjjawad on 2011-12-08
> **BonbonRose said:**
> Hi,

I'm SO sorry for the late reply, I had some personal problems and I couldn't even open the computer. 

Hi,

It's ok, I've been there too and still so I know what you mean. I didn't post anything for few days now and I'm trying now to make some posts then log off. Life is getting too hard.

Back to topic ... 


> But I read the two articles, tried the LiveUSB on couple of different machines and made a Mint LiveCD for comparison.
Good to know you've done that :)


  > As you said and the articles stated, **every thing should work** and that did happen only when I used Mint LiveCD not Ubuntu's - except the internet. 

Let me explain that in a different approach from my own experience not form any article or wiki page :)

The main purpose of LiveCD or LiveUSB is (IMHO and from my own experience) to make sure ALL your Hardware will be recognized and work well with the system you are trying to install, period.

As for programs and stuff, that should NOT be a problem :)
Why? because Linux is VERY flexible and you are free to use whatever works for you and meet your needs. So, if one or two programs didn't work from the LiveCD or LiveUSB, that's a minor issue IMHO but YMMV :)

We usually use LiveCDs/LiveUSBs to make sure our Network Adapter will work, our Graphic Cad will be recognized, etc.

Again, from my own experience, I don't even bother with any LiveCD that will not recognize my Network Adapter. It's not because I'm too lazy to try but as long as there are more than 300 Active Linux Distributions out there, why would I stick with one and waste time while 10 others will work out of the box? :)

I hope you got my point.

> (I recently reformatted my PC completely, So  I don't have a wide variety of file extensions) but from what I have.. Ubuntu didn't open any kind of video or audio files including .mp3 .avi .mkv .flv .wmv .amr
This is a very known issue:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


> As for the LiveUSB, 
-On a Windows 7 Ultimate, a black screen with "Windows Error Recovery" and "launch start up repair or Start windows normally" options.
-On windows XP SP2 the computer ignored/ couldn't feel the USB and started windows, though I adjusted the BIOS to boot from USB and used the f12 key many times.
-Finally to my relief that the USB isn't damaged *I'm still praying* On Windows 7 home edition it worked even better than the LiveCD. I almost forget.. I was able to log onto the internet when Ubuntu booted.
All the above on the same machine with different Systems or different machines?

> PS: Since I know nothing about these dark software stuff like the BIOS..etc. I can only use things you told me and don't mess with what I don't know. So there might have been something else to be done to these machines other than f12 and boot priority, and I didn't know about it or how to.
Basic knowledge, IMHO is required not only with Linux but with Windows as well. However, I think it's more required when it comes to Linux. Not because Linux is so hard but because with Linux, you will have a better understanding of what your machine is doing. 

Each machine has different BIOS that require a specific key so that you can enter to BIOS. I think I have already mentioned it earlier.
Usually, when you turn your machine on, on the very bottom of the screen, you'll see a line on the left stating which Key you need to press to enter BIOS.
If you couldn't find it for any reason (new machines are fast so it's hard to catch that - however, you can set 5 seconds delay from BIOS but again you need to enter BIOS first) then a simple google search or reading the manual should be helpful.

I have two PCs, one of them, I need to press "Del" to enter BIOS while the other I need to press F2.


> In the first link amjjawad gave me, [https://help.ubuntu.com/community/LiveCD#Other_Ways_to_Try_Ubuntu](https://help.ubuntu.com/community/LiveCD#Other_Ways_to_Try_Ubuntu) there was something about Wubi.. Do you recommend using it? 

amjjawad doesn't recommend that :) but that's me.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29)


> Is there similar installations for other Linux distros? I tried searching this but I didn't find anything other than Ubuntu installer
Wubi can be found in Ubuntu only.

---

### Post by amjjawad on 2011-12-08
> **oldfred said:**
> I often post this link on wubi from amjjawad.:)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

But wubi is good for very new users who only boot Windows and do not know how to repartition their system. It is more like an extended version of the liveCD, but does allow updates. It really is just a file inside the Windows NTFS partition, so if Windows gets corrupted, so is wubi. It also is limited on the size of the file you can make.

From the author of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

+1

Thank you, oldfred :D

---

### Post by BonbonRose on 2011-12-12
Hi, and always thanks for the links :)


It's OK then if this isn't a real problem and everything will be alright if I install it.


> All the above on the same machine with different Systems or different machines? Each system was on a different machine from friends and even Internet cafés.


> amjjawad doesn't recommend that :)
> Wubi can be found in Ubuntu only 
If that's the case, then this won't help me. I was hoping to be able to try all the distros I wanted to try in a kind of a stable installation to form a fair opinion instead of having to restart everything each time I use the CD or the USB.

---

### Post by amjjawad on 2011-12-13
> **BonbonRose said:**
> Hi, and always thanks for the links :)

Hi,

As always, you welcome :)


> It's OK then if this isn't a real problem and everything will be alright if I install it.
Even if there is a problem, it can be fixed :) I believe in this and I also believe that one should not give up trying because after all, it's a part of the learning process. 


> If that's the case, then this won't help me. I was hoping to be able to try all the distros I wanted to try in a kind of a stable installation to form a fair opinion instead of having to restart everything each time I use the CD or the USB.

If restarting is not a good idea for you, you can always try Virtual Machines.

[http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)
[https://www.virtualbox.org/](https://www.virtualbox.org/)

For me, I don't mind restarting. I always do some tests so I need a real installation or a real hardware. I don't install any distribution unless I like it and I can decide that from the LiveCD or LiveUSB. I have Virtual Machine on a Windows laptop (HP) but I don't use it much. I keep a dedicated machine for testing and it has many systems.

[IMG]http://i40.tinypic.com/qprlv5.jpg[/IMG]

By the way, I'm NOT a fan of Xubuntu but I keep it just for testing and comparing between Xubuntu and Lubuntu :P

---

### Post by BonbonRose on 2011-12-26
Hi and again sorry, I had internet connection problems.. it's just my luck.. I never had this many problems while discussing a problem on a forum before.

I tried the Virtual Machine program.. It's very helpful but what I meant by restarting not restarting the computer but the process of restarting everything each time I boot the CD, no continuity.
 

I feel like I'm stretching the topic and exhausting you all. So I read the whole topic to come up with main points.. 

Oping Ubuntu using the USB on my computer took 1.5 hour while on a other machines didn't work at all mostly BIOS settings and only one Windows 7 opened Ubuntu right away. 
When I boot from my computer neither Welcome nor Advanced Welcome page options appear.

These again are my computer details 
```

Card name: Intel(R) G41 Express Chipset 
Manufacturer: Intel Corporation 
Chip type: Intel(R) 4 Series Express Chipset Family 
DAC type: Internal 
Display Memory: 1024.0 MB 
Current Mode: 1024 x 768 (32 bit) (60Hz) 
Monitor: Plug and Play Monitor 


Driver Name: igxprd32.dll 
Driver Version: 6.14.0010.5259 (English) 
Driver Date/Size: 4/21/2010 02:42:38, 57344 bytes 
WHQL Logo'd: Yes 
Mini VDD: igxpmp32.sys 
VDD: n/a
DDI Version: 9 (or higher)

```And What are the best way to try any Linux distro?

---

### Post by oldfred on 2011-12-27
@BonbonRose
I have also lost track of what we have done & what you have installed. What works and what does not.

I have a portable with Intel core dual that originally came with XP so it is 5 or 6 years old. It uses the Intel video and just works. I have booted from both USB full install and installed to the hard drive without even any special settings.

---

### Post by amjjawad on 2011-12-29
> **oldfred said:**
> @BonbonRose
I have also lost track of what we have done & what you have installed. What works and what does not.
I second that.

I'm sure I have done/wrote all what I could think about. I'm sure the solution can be found between the lines in one of the posts here but to be very honest, I can't go back and read everything, sorry :)
If I'll do that and go back to post 1 and read all over again, I'll simply repeat myself and re-write what I already did.

Edit:
I do understand you have some problems but when you start a thread, it's better to follow up more often, otherwise everyone will lose track of what is going on :) I have mentioned that previously too :)

---

### Post by BonbonRose on 2011-12-30
Hi,

I'm sure you've done all you could to help me, and thank you SO MUCH for that :)

Just for the completion of the thread.. What's the best way to continue with trying other distros?

---

### Post by BlinkinCat on 2011-12-31
> **BonbonRose said:**
> Hi,

I'm sure you've done all you could to help me, and thank you SO MUCH for that :)

Just for the completion of the thread.. What's the best way to continue with trying other distros?

Hi BonBonRose - As it has been many hours since the last post, it would be my suggestion that you mark this thread as solved via the thread tools at the top of the page and then ask a separate question on a new thread regarding trying other distros. (which isn't all that hard by the way) Hopefully this thread may be helpful to others.

Cheers and a Happy New Year - :P

---

### Post by amjjawad on 2011-12-31
> **BonbonRose said:**
> Just for the completion of the thread.. What's the best way to continue with **trying** other distros?

Just for the completion of this thread:

1- LiveCD
2- LiveUSB
3- Virtual Box/Machine

:)

P.S.
Happy New Year to you :)

---

### Post by BonbonRose on 2012-01-05
Hi,

Thanks for your help I really appreciate it and sorry if I bothered you in any way

Happy New Year to you all  :smile:

---

### Post by amjjawad on 2012-01-12
> **BonbonRose said:**
> Hi,

Thanks for your help I really appreciate it and sorry if I bothered you in any way

Happy New Year to you all  :smile:

Hi there :)

You did not bother me and I'm sure you did not bother anyone here :) everyone here likes to help others and we enjoy that, otherwise we wouldn't do it :)

Hope this thread will give you some better ideas in future and sorry if we couldn't give you what you were exactly looking for. Please don't let that stop you from posting more Questions but please start new thread for that :)

If you ever think to use Lubuntu, I'm here for that ;)

Good Luck and Happy New Year!

---

