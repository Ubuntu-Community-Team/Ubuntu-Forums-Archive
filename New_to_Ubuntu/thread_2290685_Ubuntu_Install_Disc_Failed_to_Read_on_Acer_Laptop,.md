---
title: "Ubuntu Install Disc Failed to Read on Acer Laptop, OK on others"
date: 2015-08-14
forum: New to Ubuntu
---

### Post by Peter_Brixey on 2015-08-14
I am new to Linux having been a Windows and Mac user for decades, but my recent unfavorable evaluation of a Windows 10 Enterprise installation has finally given me a reason to investigate Ubuntu.
 
I downloaded Ubuntu 14.04.3 LTS 32 bit and 64 bit ISO files and burned them to discs. Both worked fine when I let a Dell E6400 boot to disc.
 
I then tried to do an install on a 32 bit Acer laptop running XP SP3 installed on a partitioned HD but the laptop would not read either of the discs. The HD file system is NTSF. The Acer is otherwise OK and will read and install other discs with apps and files on them.
 
Can anyone shed some light on a resolution to this? 
 
Thanks in advance,
 
Peter B.

---

### Post by Peter_Brixey on 2015-08-14
Progress Report 1.

I downloaded Ubuntu again but this time I did it on the Acer, then burned the disc in the Acer optical burner. Same issue, it blew right past the CD/DVD drive and started the XP Op Sys. I checked the boot sequence and CD/DVD was first in line. Hmmm...

Then I tried the disc on a Dell 755 desktop, the same thing happened, the Win 7 Op Sys started. I checked the boot sequence in BIOS and it showed CD/DVD first. Restarting the Dell 75 and this time it booted to the DVD disc. Hmmm...I had made no changes to the boot sequence.

The plot thickens.

Peter B.

---

### Post by Peter_Brixey on 2015-08-14
It also will not boot to disc on my Sony Vaio VGNZ running Windows 7 Pro. I cannot read the disc using Windows Explorer either even though the drive is recognized in Windows Explorer, Device Manager and Disc Management. The disc will not mount.
 
Does anyone have clue how to fix this?

Peter B.

---

### Post by Bashing-om on 2015-08-14
Peter_Brixey; Hey !

As I understand it 'Acer' and UEFI has it's difficulties due to vendor lock in. 
Maybe await oldfred to respond to this thread. Or search some of his threads in respect to booting up on the Acer .

[INDENT][INDENT]If I knew better
[INDENT][INDENT][INDENT][INDENT]I would say different
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2015-08-14
>   What program did you use to burn the iso?   (unetbooting, pendrivelinux, startup disk creator)???
>   Are you sure you saved your BIOS changes on "all" your PC's (usually F10 or similar)
>   IF any PC is UEFI, did you turn off secure boot??? 
>   Did you try burning a usb-flash-stick???
>   Booting a 64 bit dvd on a 32 bit laptop is a non-starter

Do you have any PC that provides a bootup menu that allows selection of usb-sticks (like my System76 Galago Ultra Pro - - what a breeze to run live or install OS media)

Below . . still best way to get Linux on a PC . . . is the same way most folks got it on there current PC's . . . (if can do this way for Windows, then, . . . why not for Linux???)

[http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

### Post by sandyd on 2015-08-15
Have you tried a USB drive installer?

You can use the [Win32 Disk Imager]("http://sourceforge.net/projects/win32diskimager/") to write the ISO to USB drive. The USB drive should then be bootable on most modern computers.

Please also check MD5SUM of images to verify integrity, or use Torrent to download (which automatically verifies integrity). Instructions for verifying integrity available [here]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows")

---

### Post by johnny35 on 2015-08-15
Have you tried **imgburn **? thats pretty much the only isoburning software that i use. i used it to burn a kali linux but after restarting the system posted the error message, "security boot failed". so my advise is the source of your iso might have issues, so find a new source. however using the same app and the same disk, i installed ubuntu unto my duel boot system and it is working fine.

---

### Post by Peter_Brixey on 2015-08-16
Hello all,
 
I have continued pursuing the install of Ubuntu on the Acer and will not give up until success is achieved; I am not giving in to Microsoft either.
 
To recap for a moment:
 
Each machine that I have tried booting the disc on has had the boot sequence checked to ensure that CD/DVD is selected as first.
 
Several DVD copies have been burned from the ISOs using different PCs and software including Imgburn, NTI and CloneDVD. So far none of the DVDs will boot on the Acer or the Sony VGNZ. The Dell E6400 laptop and Sony laptops are both 64 bit. The Dell E6400 will boot both the 32 and 64 bit discs, the Sony will boot neither; my focus remains with the Acer. My Dell 755 will boot after boot sequence changed to CD\DVD first.
 
The (32 bit) ISO checksum has been verified using winMD5Sum and is OK.
 
I have not yet tried a USB flash drive; that will be my next step along with chasing down the UEFI issue including safe boot. I do not believe that the Acer will boot from a USB drive but that remains to be seen.

Here is the text from the boot.ini file:
 
*[boot loader]*
*timeout=30*
*default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS*
*[operating systems]*
*multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect*
*C:\wubildr.mbr = "Ubuntu"*
 
I installed WinCDEmu then rebooted the Acer with the disc in the DVD drive.
 
I hit F12 to check that the CD\DVD was the first boot device. A dos screen then opens with choice of Windows or Ubuntu.
 
When I select Ubuntu and hit enter the following screen appears on screen:
 
*Try (hd0,0): FAT32: No WUBILDR*
*Try (hd0,1): NTFS: __*
 
Then this screen:
 
*Completing the Ubuntu installation,*
*For more installation boot options, press &#8216;ESC&#8217; now&#8230;*
*0*
 
Then this in the center (GUI-like) screen:
 
*Ubuntu*
* . . . . .*
 
The dots clock back and forth for a while then this appears on screen:
 
*Completing the Ubuntu installation,*
*For more installation boot options, press &#8216;ESC&#8217; now&#8230;*
*0*
*[   8.104177] ACPI PCC probe failed.*
*BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-inshell (ash)*
*Enter &#8216;help&#8217; for a list of built-in commands.*
*(initramfs) Unable to find a medium contaianing a live file system*
_
 
Then the Acer is dead in the water. Hmmm...

Peter B.

---

### Post by Bashing-om on 2015-08-16
Peter_Brixey; Ouch ??


Just a thought !
> 
C:\wubildr.mbr = "Ubuntu"

You are not attempting to install ubuntu within Windows as a "WUBI" install are you ? As WUBI and UEFI are in-compatible and WUBI is no longer supported .

You want a true dual boot situation. Each operating system installed independently in their own partitions.
The 1st step in achieving this goal is the ability to boot the chosen ubuntu system in the "try ubuntu" mode.
All is as expected and functional in the "try ubuntu" mode, 
Then depending on your end goal install ubuntu
a) Along side
b) stand alone ( erase disk and install ubuntu)
c) something else - you set up the partitioning ( or have set them up before hand)

By far the simplest install method is to allow the install wizard to make all the decisions with the option "install along side" Making sure that you boot the machine in UEFI mode .

I still think I recall that with Acer one has to trick the firmware around that vendor lockin to be able to install any other operating system.

[INDENT][INDENT]I hope I help
[/INDENT][/INDENT]

---

### Post by Peter_Brixey on 2015-08-16
> **Bashing-om said:**
> Peter_Brixey; Ouch ??

Just a thought !

You are not attempting to install ubuntu within Windows as a "WUBI" install are you ? As WUBI and UEFI are in-compatible and WUBI is no longer supported .

You want a true dual boot situation. Each operating system installed independently in their own partitions.
The 1st step in achieving this goal is the ability to boot the chosen ubuntu system in the "try ubuntu" mode.
All is as expected and functional in the "try ubuntu" mode, 

Originally I was going to install it in it's own partition like I did on the Dell E6400 before I removed it and installed an evaluation edition of WIndows 10 Enterprise---Yuk!

I created a second partition on the Acer then tried to get the Ubuntu OS to boot from the disc where I should have had choice of run from disc or install instead of or as well as etc. But the disc would not mount. Then I tried WinCDEmu with the ISO file on the HD to emulate a drive but that did not work either.

I am going to recreate the second partition again, move the ISO file to it and try WinCDEmu again and see if I have any better luck. At least it will be on a clean empty partition.

Peter B.

---

### Post by Bashing-om on 2015-08-16
Peter_Brixey; Hey ...

Do these threads help:
[http://ubuntuforums.org/showthread.php?t=2290594&highlight=Acer](http://ubuntuforums.org/showthread.php?t=2290594&highlight=Acer)
[http://ubuntuforums.org/showthread.php?t=2290276&highlight=Acer](http://ubuntuforums.org/showthread.php?t=2290276&highlight=Acer)

As advised, oldfred has the skinny on installing/booting on the Acer product.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by sandyd on 2015-08-16
> **Peter_Brixey said:**
> Originally I was going to install it in it's own partition like I did on the Dell E6400 before I removed it and installed an evaluation edition of WIndows 10 Enterprise---Yuk!

I created a second partition on the Acer then tried to get the Ubuntu OS to boot from the disc where I should have had choice of run from disc or install instead of or as well as etc. But the disc would not mount. Then I tried WinCDEmu with the ISO file on the HD to emulate a drive but that did not work either.

I am going to recreate the second partition again, move the ISO file to it and try WinCDEmu again and see if I have any better luck. At least it will be on a clean empty partition.

Peter B.

Hi, mounting the ISO on windows will only allow Wubi as an install method - which is no longer reccomended.

---

### Post by Peter_Brixey on 2015-08-17
> **sandyd said:**
> Hi, mounting the ISO on windows will only allow Wubi as an install method - which is no longer reccomended.

Thanks Sandy, so I understand, I have been reading up on this but there is so much to dig through. I shall keep on plugging and chugging until it works or kills me. :D

Peter B.

---

### Post by oldfred on 2015-08-17
If this is an older system then it is BIOS only, not the new UEFI.
If it really requires 32bit as it has limited RAM and older processor, then full Ubuntu will not work as Unity also requires better video which your older system will not have.

Are you downloading 32 bit Lubuntu? That should work on systems up to 10 or so years old. If much older then maybe something even more lightweight may be required.
But systems from about 9 years ago had 64 bit processors. My Toshiba from 2006 runs 64 bit, but not full Ubuntu as Intel video just is not powerful enough.

What are specs on your Acer? CPU, RAM, Video chip?

You cannot use wubi or anything loaded from inside Windows, but must reboot system and choose DVD or flash drive. Only systems in about last 10 years can boot from flash drive. Does you BIOS offer a USB/flash drive boot option?

       Lubuntu is an Operating System that is using LXDE.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[URL="https://wiki.ubuntu.com/Lubuntu"]https://wiki.ubuntu.com/Lubuntu

[/URL]
 Older hardware suggestions - mörgæs
[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

[URL="https://wiki.ubuntu.com/Lubuntu"]
[/URL]

---

### Post by Peter_Brixey on 2015-08-17
Hi there oldfred,
 
The Acer has been a great laptop despite any short comings. I have retired it a few times but thought that it might make a good platform for a shakedown cruise with Ubuntu, my first venture down that road.
 
Here are the specs:
Acer Aspire 1642WLMi purchased in 2006
Intel Pentium M 740 Processor
(1.73 GHz, 533 MHz FSB, 2 MB L2 Cache)
15.4” WXGA Acer CrystalBrite TFT LCD
Intel Graphics Media Accelerator 900
40GB HDD
DVD-Dual double-layer
(support DVD+R Double Layer/DVD+-RW)
512MB DDR2 (Support dual-channel)
802.11g/g wireless LAN
System BIOS Version 3A05
VGA BIOS Version Alviso 1219
 
The BIOS does not offer USB/Flash Drive, but it will show USB/Floppy if I plug one in, not that that helps.
 
Is there a lighter version of Ubuntu that I could download which may work?
 
It is interesting or should I say troublesome that the CD/DVD drive will not mount the 32 bit discs, yet it will mount some others. The discs mount OK in a Dell E6400.
 
I will check out the links you posted.
 
Thanks, :)
 
Peter B.

---

### Post by Peter_Brixey on 2015-08-17
Oops I forgot to mention the Acer is running XP SP3.

Peter B.

---

### Post by Bashing-om on 2015-08-17
Peter_Brixey; Hey;

A bit long in the tooth, but (L)ubuntu can cope, with a bit of help. Be aware 512 MB of ram is the lower limit. Do not expect great performance.
[https://help.ubuntu.com/community/PAE/PentiumM](https://help.ubuntu.com/community/PAE/PentiumM)
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

[INDENT][INDENT]we whoop this sucker into shape
[INDENT][INDENT][INDENT]one way or another
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Peter_Brixey on 2015-08-24
I burned the Mini version to a CD and tried today to install it, this is how it went:
 
·         Booted from CD drive
·         Selected Install from the Installer Boot Menu
·         Selected the default language
·         Selected the home country
·         Configured the Keyboard
·         Selected WIRELESS from the Network configure menu (no Ethernet in my shop, only wireless. This laptop connects OK from Windows)
·         Selected my SSID
·         Selected WPA/WPA2 PSK
·         Entered my Passphrase
·         Screen showed Configuring the network with DHCP
·         Then it showed Network autoconfiguration failed&#8230;

I tried manually configuring it but that did not work either and so I could not select an Ubuntu Archive Mirror. 
 
That is where I am right now. At least I could mount the CD with the Mini version on it. Some progress at least, albeit small steps but at least they are steps. 

Peter B.

---

### Post by mörgæs on 2015-08-25
Much easier if you bring the computer to a place with wired internet access during install.

---

### Post by Peter_Brixey on 2015-08-25
> **mörgæs said:**
> Much easier if you bring the computer to a place with wired internet access during install.
Agreed, but if the wireless card works on Windows, it should work with Ubuntu. It is turned on BTW.

Peter B.

---

### Post by Bashing-om on 2015-08-25
Peter_Brixey; Hey;

Consider, there are many many WIFI drivers out there, the installer can not have all of them available. From a wired connection the chances of installing the WIFI driver are good.

[INDENT][INDENT]for the worth of it
[/INDENT][/INDENT]

---

### Post by howefield on 2015-08-26
> **Peter_Brixey said:**
> Agreed, but if the wireless card works on Windows, it should work with Ubuntu.

What an odd assumption.

Try plugging in an alternative wireless adapter if you have one.

---

### Post by mörgæs on 2015-08-26
According to the [specifications]("http://www.cnet.com/products/acer-aspire-1642wlmi-pentium-m-740-1-73-ghz-512-mb-ram-80-gb-hdd/specs/") which *may or may not *be relevant for your particular computer (components often change, also for the same model number) the wifi card is an Intel PRO/Wireless 2200BG. 

Buntu has drivers for this card but they are not necessarily part of the minimal ISO, which is ... well, minimal.

---

### Post by Peter_Brixey on 2015-08-26
> **mörgæs said:**
> ... the wifi card is an Intel PRO/Wireless 2200BG. 

Buntu has drivers for this card but they are not necessarily part of the minimal ISO, which is ... well, minimal. mörgæs, bashing_om et al,...minimal, a good point. Today, time permitting I will connect to a hard wire router and give her another go.

We'll get there I am sure, just have to pick the right path through the forest.

Peter B.

---

### Post by Bashing-om on 2015-08-26
Peter_Brixey; Atta Boy !

That's the spirit. I assure you the end justifies the effort.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by Peter_Brixey on 2015-08-26
> **Bashing-om said:**
> Peter_Brixey; Atta Boy !
That's the spirit. I assure you the end justifies the effort.[INDENT][INDENT]together we can
[/INDENT]
[/INDENT]
 Here we go, connected to Internet via Ethernet. Installing Mini on the Acer now as I type (on my Mac Pro) desktop. I selected use entire disc with LVM or whatever the terminology is. Stand by for further bulletins. If this is successful, I will consider replacing the HD in one of my later Dell Laptops (an E6400) and installing a full version there. There right now at least I can boot off the DVD drive to 14.04.3 LTS "Trust Tahr" 32 bit, or maybe the 64 bit version instead.

Thanks to all for the help.

Peter B.

---

### Post by Peter_Brixey on 2015-08-26
> **Peter_Brixey said:**
> Here we go, connected to Internet via Ethernet. Installing Mini on the Acer now as I type (on my Mac Pro) desktop. I selected use entire disc with LVM or whatever the terminology is. Stand by for further bulletins. If this is successful, I will consider replacing the HD in one of my later Dell Laptops (an E6400) and installing a full version there. There right now at least I can boot off the DVD drive to 14.04.3 LTS "Trust Tahr" 32 bit, or maybe the 64 bit version instead.

Thanks to all for the help.

Peter B.I finally got Mini installed and working. WiFi connection too, it connected automatically without any help from me. Now the real adventure begins.

I am sure I will have lots of questions as I move along. Thanks for the help everyone, I just wish there was time to read through all the links that were provided, but if I had read them all, and I did read some, nothing else would have been done, and I would probably been more confused than ever. Is there a dictionary of terms with Peter Rabbit explanations?

Peter B.

---

### Post by Bashing-om on 2015-08-26
Peter_Brixey; Outstanding !

Glad you made it ! Welcome to our world .

I invite your attention to "Popular Pages" on my signature. In amongst all the other great helps and tutorials you will find a glossary.

As You are now up, 
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Feel free to open new threads on any situation you encounter - like dead men -> one to a box. We are here to guide and assist.

[INDENT][INDENT][INDENT]Up Up and Away !
[/INDENT][/INDENT][/INDENT]

---

### Post by Peter_Brixey on 2015-08-27
Today I will mark this thread as SOLVED. I have downloaded a few apps for Lubuntu and will see how they perform.

Thanks everyone that made a positive and helpful contribution. If I have more questions or need more information, I will start a new thread.

Best regards to all.

Peter B.

---

