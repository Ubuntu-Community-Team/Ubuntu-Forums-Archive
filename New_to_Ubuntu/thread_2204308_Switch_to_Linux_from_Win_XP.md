---
title: "Switch to Linux from Win XP"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by ken15 on 2014-02-07
Windows user for the last 30 years and now wish to swap to Linux Ubutu. Have a new and additional HD installed with dual boot. The Linux program which supposedly installed does not look like anything I have seen previously and the book I have received from my local library is dated 2002.Am unable to remove many programs that I do not require now or ever and so far have not been able to install those that I do. So I am playing blind with a jigsaw with several pieces missing. Where do I go from here ?

---

### Post by Vladlenin5000 on 2014-02-07
A book from 2002 is quite old and certainly outdated regarding most things related to the current Ubuntu.
Assuming you already have a vanilla Ubuntu installed - single OS or dual-boot is irrelevant for that matter - perhaps you should start by describing exactly what programs you need to install, what programs do you want to remove... Then someone should be able to help you with suggestions/troubleshooting.

---

### Post by brokenhachi on 2014-02-07
> perhaps you should start by describing exactly what programs you need to install, what programs do you want to remove... Then someone should be able to help you with suggestions/troubleshooting.  
^this

Software can be Installed/removed via the *Ubuntu Software Center*, or the terminal via commands if you so desire.

Software center tutorial in 12.04: [https://www.youtube.com/watch?v=XnGeqfe-nsY](https://www.youtube.com/watch?v=XnGeqfe-nsY)

---

### Post by stinkeye on 2014-02-07
Ubuntu is a Debian-based Linux operating system.
What you may have installed is another Linux distrobution.
The first release of Ubuntu 4.10 (Warty Warthog) came out in 2004.

**_[COLOR="#B22222"]Download[/COLOR]_** and install the latest release.

If your installing Ubuntu to a second hard drive, choose this drive for grub install during the installation process.
[https://help.ubuntu.com/community/Grub2/Installing#Installation_Options_.28LiveCD.29](https://help.ubuntu.com/community/Grub2/Installing#Installation_Options_.28LiveCD.29)

This will leave your Windows drive untouched so it wont be necessary to reinstall your windows boot loader if you
decide to remove Ubuntu.

Set your Ubuntu drive as the first boot drive in your BIOS and grub will pickup your Windows install and display this as a boot option.

---

### Post by Bucky Ball on 2014-02-07
Welcome. 

Dry from XP??? Unity, the Ubuntu desktop environment, would be a compu-culture shock. Install Xubuntu, Lubuntu or log out and choose 'Gnome fallback' for something more recognisable.

But then, if you're up for the Unity learning curve, go for it. ;)

---

### Post by craig10x on 2014-02-07
If you have ever seen or played with a mac (apple) computer, then unity shouldn't be too scary for you...it's just a dock, really, except it is on the left instead of the bottom (but can auto-hide just like the mac's dock can)...the current ubuntu is 13.10 and 14.04 will be released in april...

---

### Post by deadflowr on 2014-02-07
> The Linux program which supposedly installed does not look like anything  I have seen previously and the book I have received from my local  library is dated 2002.

I should hope not, something that runs the exact same as it did 12 years ago might show signs of a lack of progress, to a degree.
Even XP of today runs with newer features as compared to when it first arrived.

> Am unable to remove many programs that I do not  require now or ever and so far have not been able to install those that I  do. 

More info needed on what programs YOU* think* you don't need and how you are trying to remove them.
Ubuntu isn't Windows, so don't expect the installation and removal of programs to act to same way.

---

### Post by Bill Tetzeli on 2014-02-07
For an XP user I would say go with [Linux Mint]("http://www.linuxmint.com").  Download and install Mint 16, Cinnamon version.  You'll find the interface very familiar and easy to use.  Plus it's unique among Linux distros as being universally hailed both by complete newbies and hardcore geeks.

It would help if you gave us more of an idea of what programs you do and don't need.  Here are some basic ones you can find:

Libre-Office (replaces MS Office - installed by default)
GIMP (replaces Photoshop - installed by default)
Skype (available in Software Center or typing "sudo apt-get install skype" in a terminal window)
Audacious (replaces Winamp - same installation method as Skype (actually, this applies to most programs))
Banshee (replaces iTunes)
Spotify (instructions on installing [here]("https://www.spotify.com/us/download/previews/") - if you know how to copy and paste, you're golden)
Netflix (instructions on installing desktop app [here]("http://www.ubuntugeek.com/install-netflix-in-ubuntu-13-1013-04-using-ppa.html") - requires a faster computer)

Also, many Windows applications will run under Wine.  Just install Winetricks ("sudo apt-get install winetricks" or get it from the Software Center), download the Windows installation file from the appropriate site, right click on it, select properties and associate it with Wine Windows Program Loader in the "Open With" tab.  After that, double clicking on a Windows .exe file will automatically start the installation process.  If you're installing from a CD, you should be able to navigate to a setup.exe or install.exe file on the CD itself and double click on that to install.

As far as the programs you don't want, there's really no harm in leaving them.  Most of them are far smaller than their Windows equivalents and you may end up using them after all.  Of course, if you really want them gone you can remove them via the Software Center or typing "sudo apt-get remove thisdamnprogramidontneed" in terminal.  Keep in mind when using the terminal that the actual program names are all lower case, and sometimes different from the names they present to the user (e.g. Disk Usage Analyzer is actually baobab, Libre-Office is actually libreoffice, etc.  I know.  Me too.) The description of any program in the Software Center will also include its actual, system-recognized name.

Again, if you give us more of an idea of what you need and don't need, we can give you better tips.  Again, try Mint.  You'll love it.

---

### Post by sudodus on 2014-02-08
Hi *ken15*,

- please tell us what linux distro, version and flavour you installed

- and please tell us about your computer

Brand name and model of the computer or motherboard
CPU
RAM (size)
graphics chip/card
wifi chip/card (if any)

Knowing this will make it much easier to give advice. Otherwise we can only give general advice or guess what you need.

---

### Post by kurt18947 on 2014-02-08
I'd recommend Mint as well for someone unfamiliar with the GNU/Linux way of doing things.  Once you 'get your feet wet' you can experiment with live CDs/USBs if you want.  A live Mint USB would be an option as well just to get a taste without changing your existing setup.

---

### Post by Bucky Ball on 2014-02-08
Create a bunch of disks/USB installers and try them all 'live'. See what you like and what your machine likes. You don't need to install any of them until you're ready. A good thing for a new user to do. You taste the various flavours and get a feel for how things work in Linux/Ubuntu.

PS: Take notes as some flavours are highly customisable and you can use elements/apps in one from another flavour without installing the whole OS. Hybridisation!

PPS: Linux Mint is not supported in the general support areas of the forums here but appears to have a fairly active community [HERE]("http://forums.linuxmint.com/").

By all means, feel free to post in 'Other OS' sections, support and chat, here about it if you go that way. ;)

---

### Post by wamses2 on 2014-02-08
Where do I go from here ?

If you have Ubuntu 12.0.4 I would start here [https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html) 
It should give you enough pointers to get going quickly, including instructions on removing software you don't need. If you are running a different version I suspect there will be an equivalent guide. 
Good luck, it really is worth spending a little time getting to grips with Ubuntu, and if you've been using XP I am sure you would be even less happy going to Windows 8 wouldn't you?

---

### Post by 3rdalbum on 2014-02-08
> **ken15 said:**
> Windows user for the last 30 years and now wish to swap to Linux Ubutu. Have a new and additional HD installed with dual boot. The Linux program which supposedly installed does not look like anything I have seen previously and the book I have received from my local library is dated 2002.Am unable to remove many programs that I do not require now or ever and so far have not been able to install those that I do. So I am playing blind with a jigsaw with several pieces missing. Where do I go from here ?

As others have mentioned, a Linux book from 2002 is going to be totally obsolete. Linux moves very quickly. Even a Linux book from 2010 would be too old to be very useful. You should check out some online documentation such as Ubuntu Manual ([http://ubuntu-manual.org/](http://ubuntu-manual.org/)) which is free to download and up-to-date.

I would advise not removing any programs at this stage. While there's no danger in removing things like Libreoffice, I see a lot of newbies looking through the list of installed packages and removing things that are actually critical to the system. "This Python thing - says it's a programming language - I'm not a programmer so I don't need it". The system warns them that removing Python will also remove 72 programs that depend on it, but the new user often ignores the warning and then complains that their computer won't work anymore.

As for installing software, you need to use the Ubuntu Software Center program to find, download and install software. You don't generally go trawling on the web to find programs, download them in your web browser and then double-click to install. That's not how things work on Linux. Use Ubuntu Software Center, it has about a thousand programs available for easy installation. When you get more experienced you can look at other methods of getting software, if you wish - but I've been using Ubuntu for 8 years and I rarely venture outside Ubuntu Software Center's directory.

Other than that, play around! Read a lot of things online, but of course you should only read what has been recently written. Most things from 2012 and 2013 will be fine. You can learn a lot from experience, and if there's anything you don't understand you can look it up online.

---

### Post by ken15 on 2014-02-08
Well, I have several replies already so thankyou . I presume that this reply will be read and digested by all, so here goes : The computer that I am using to try Linux is an old Compac that my wife has just discarded. It is a Compac Presario ED 865AA. and still works fine for XP . I have upped the RAm to 2 1\2 G and fitted an additional 200Gb HD. the original being an 80. I also have a new Dell using Win 7. but I intend not to use that for experimenting with Linux. However i will continue to use it for communication via this forum.
So what do I want. Firstly a looksee at Linux to see if I can or want to drive it, so as yet I am not an raving enthusast.

The version of Linux that was put on via a nerd is UBUTU 12. The installation includes a dual boot option: was far as I can see is a failure., inas much as altho it boots up into a balck scree showing UBUTU with 3 red dots that fades out to the backgroung with some icons on the LHS.  However the info contained within in them is as dim as a Toc H lantern.  Not only does this display do much for me but It would seem that i have lost access to my XP prog. which concerns me. As regards the version of Ubutu I am using, Gawd knows and he ain't telling . As for flavor ? I am in a candy store and no one has told me what I have. You will gather from this, my lackof appropriate knowledge . BUT so far I ain't impressed.  A second tome I have obtained from my local library so far would make a good blocking for a wobbly table.  So i willing to persist  -- but only up to a point since I am 87 and have other things to worry about . Thanks anyhow.  ken

---

### Post by ken15 on 2014-02-08
Please don't baffle me further  
Ken

---

### Post by sudodus on 2014-02-08
Hi again Ken,

From the information in post #14, I would suggest that you download and test ***Xubuntu 12.04 LTS, 32 bits***. With that amount of RAM you should get the ***desktop*** iso file. It has a medium light desktop environment, lighter than standard Ubuntu, and it looks more like Windows too. See this link where the torrent is recommended, but you can also get it from one of the mirrors, or ask the nerd to help you get it ;-)

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

[URL="http://torrent.ubuntu.com/xubuntu/releases/precise/release/desktop/xubuntu-12.04.4-desktop-i386.iso.torrent"]http://torrent.ubuntu.com/xubuntu/releases/precise/release/desktop/xubuntu-12.04.4-desktop-i386.iso.torrent
[/URL]

---

### Post by ken15 on 2014-02-08
Get my feet wet ! ! I have yet to find where the water is

---

### Post by Bill Tetzeli on 2014-02-08
> **ken15 said:**
> Get my feet wet ! ! I have yet to find where the water is

[Edited after reading post #14]

Consider us your dowsing rod. :-)

Again, I'm casting my vote for [Linux Mint 16]("http://linuxmint.com") (Cinnamon version) - stable, easy to use, XP-like interface.  You will face the shortest learning curve with it.  While not the most "lightweight" distro, I run it with ease on my netbook, which has a 1.6 Ghz processor and 2 GB RAM.  

So [here's the water]("http://www.linuxmint.com/download.php").  There is a list of different versions of Mint 16, you should choose the standard Cinnamon.  Click the "32-bit" link and download the .iso image to your computer.  You can then either burn it to DVD or use [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to create a bootable USB drive.  Then you can boot into either of those and either try out Mint or install it.

BUT...

(sober thought time)

Forgive me if I'm being presumptuous, but when I read in your post that you're 87, it occurred to me that the last thing you want is to waste time on a computer.  Even at the tender young age of 49, I am becoming intensely aware that time is more precious than gold, and try not to waste it but to prioritize how I use it.

You have a brand new computer with Windows 7.  IMHO that is the most user-friendly OS ever, if not the most secure (and that's easily taken care of with Avast, Windows Defender and sensible web browsing).  It's supported until 2020.  My feeling is you should just enjoy that computer and forget about Linux.  Six months is not an unusual learning curve for Linux, whereas the differences between XP and 7 are minor and mostly for the better.  It took me three months to be comfortable enough with Linux to port my email folder over to it and another three or six months before I got rid of Windows entirely.  Do you want to spend your time learning how to use a new operating system (which will isolate you), or do you want to use an OS you're already familiar with to make the best use of your time (to stay in touch with family and friends, e.g.)?

If I knew you and lived close by I would gladly install Linux for you and give you the Reader's Digest version of how to use it.  But the problem you describe with your older computer, the dim screen, is something I've faced with older computers too, and I'm pretty sure you'll run into it no matter what distro you use.  Most computers are well supported by Linux these days, but some still have problems.  You would have to either go into your computer's settings to brighten the screen each time you booted up or use some workaround that would require hours or days of googling and forum browsing.  Again, is that how you want to spend your time?

So if I were you I would ask two questions.  1) "Is there anything I want to do in Linux that I can't do in Windows?"  If the answer is "yes", then question 2) "How much time is that worth to me?"  If it's "no", I'd say stick with Windows 7 on your new computer and enjoy it.  For all the well-deserved flack MS takes, it's an excellent operating system and if Ballmer had stuck with that model and not gone with the Win 8 abomination, I'd still be happy on the Redmond plantation today.

---

### Post by Bucky Ball on 2014-02-08
Well, the way to the water has been clearly pointed out to you. Install Xubuntu. Download the ISO from here:

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

Choose a torrent or a mirror site for the download and choose 12.04 LTS desktop, 32bit. That should give you the least grief.

Once downloaded, burn a disk image to a DVD, reboot the computer and boot from the DVD. When you get to the option 'Try Xubuntu', try Xubuntu.

That's it. If you hit any brickwalls along the way, please let us know and we can help. Until you actually attempt something and get specific about what you are having problems with there's not a lot we can do to help bar repeating ourselves. ;)

PS: If you have any problems in any step of this, that we can help you with. Clearly state what the issue is.

---

### Post by ken15 on 2014-02-08
Sagacious advice indeed. Yes I have 7 up and running for some time but I am happier with XP. Nevertheless with the end of support for it I am attempting to get set for a replacement. However, I am a cussed 87 and would like to have a go with Linux. That said I find I am baffled by the new and fruity terminology and am beginning to sense that Linux is more than a bit oversold. I have downloaded the three files recommended by one of your colleagues on this site but am darned if I am able to open them. Perhaps there should be yet another section here for the really absolute beginners. As for the Live DVDs these seemed to have some attraction for me if only to take a look at Linux and decide if I wanted it, but I have been unable to download one. Furthermore my order to the Linux store is DECLINED for reasons unstated,so that is why I am attempting to download it to a unique HD where it won't be able to screw up my Win 7.  Nevertheless thanks for your concern.  Ken

---

### Post by Bucky Ball on 2014-02-08
As for installing, you can try this and go from the section that says, 'Install Ubuntu 12.04 Precise Pangolin'. Don't worry about the fact you are installing Xubuntu. Same in this part:

[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin#.UvcHK6EvBxA](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin#.UvcHK6EvBxA)

Not sure what those three files were but if they were Ubuntu then you don't open them. You burn the ISO to a disk and boot from the disk. ;)

When you are trying Ubuntu from the Live session (booted from the DVD) there is an install icon on the desktop. You can install to whichever partition/drive you wish. ;)

---

### Post by Bill Tetzeli on 2014-02-09
> **ken15 said:**
> I am a cussed 87

Well hell, have at it then! :lol:

> **ken15 said:**
> I am baffled by the new and fruity terminology

Hoo brother, you, me and everyone else who speaks English as a first language!

> **ken15 said:**
> I have downloaded the three files recommended by one of your colleagues on this site but am darned if I am able to open them.

If you're talking about the .iso files, you don't open them.  You burn them to DVD.  This is a [minute and a half video]("http://www.youtube.com/watch?v=bAr6NkMvImA") that explains how to in Windows 7. (BTW, this kid gets it: short and sweet, no "uh uh uh"ing, no random life observations - like this one. ;-))  After that put the DVD back in the drive, reboot and you're off to the races.

So, while I still hold out for Mint, which will be most familiar to an XP user, if you're going to use Xubuntu you should definitely go with 12.04 LTS because it's less buggy.  Here are some differences you should be prepared for:

- The start menu, taskbar and system tray are located at the top of the screen instead of the bottom.
- The bottom of the screen contains shortcuts to programs and system tools, just like the launcher at the bottom of the Windows 7 desktop.  To create a shortcut there (or on the desktop) the easiest way is to drag it from the start menu ("applications menu" in Linuxese) to the bottom.  You may have to do a bit of a double-dip down there for it to really take (you'll see what I mean).  But it's a great feature because you can load it with way more program shortcuts than the Windows 7 task launcher, mainly because that's all that's down there.

As far as the screen dimness problem goes, I misspoke when I said you'd have to go into the system settings to fix it.  You probably can deal with it by holding down the Fn (aka Function) key and pressing the increase brightness key repeatedly (usually at the top of the keyboard, somewhere between F6-F9 - look for a simple picture like a sun with an arrow next to it).  You'll still have to do that every time you boot up, but it'll be relatively simple.

---

### Post by ken15 on 2014-02-09
I have viewed the UTube clip and learned nothing from it since I had already burnt the 3 files to a DVD.  Two UBUNTUs and one Torrent. As for being off to the races, my nag won't budge with any type of booting. Regarding screen brightness . My monitor has excellent colour and resolution for all features other than the drop down menus. IE the background picture is that of the Big Eye in London UK and has excellent colour. Perhaps the Flotation test is next. 

Ken

---

### Post by sudodus on 2014-02-09
> **ken15 said:**
> I have viewed the UTube clip and learned nothing from it since I had already burnt the 3 files to a DVD.  Two UBUNTUs and one Torrent. 

Ken

If you have burnt 3 files to a DVD (the same DVD), it won't boot. You need to burn in another way. 'Burning an iso image file to the device' is different from burning a file or three files to a DVD in data-DVD mode.

If you have problems with burning the image, I suggest that you ask the 'nerd' (who installed Ubuntu the first time) for help, he will probably be happy to help you get a system which is more similar to Windows, and therefore easier to learn.

---

### Post by Bill Tetzeli on 2014-02-09
It sounds like you didn't actually try following the vid's directions, but burned all three .iso files to one DVD as a data disc.  That's not how you create a bootable DVD from an .iso image.  Go back to the video, and actually follow it step by step.  I guarantee if you do that you'll get much better results.

You can also try burning the files using [Infrarecorder]("http://infrarecorder.org/?page_id=5").  The first thing you see when you start the program is six different options, one of which is "Write Image".  Couldn't be more obvious.  Click on it, select the .iso image you want to burn (no more than one!) and the rest should be easy to follow.

As far as your screen brightness goes, are you referring to how it looks in Windows?  The problem is that your display may require a proprietary driver that's part of your Windows install but not available in Linux (though many are).  Without that driver, even though you have no brightness problems when running XP, when you boot into a Linux live CD, or Linux even after it's installed on your hard drive, the generic open source driver used for your display might not give you a sufficiently bright screen without your having to use the brightness function key (which I mentioned before) to make it brighter.  I have this problem with a Toshiba Satellite that's only four or five years old, so with a system as old as yours I wouldn't be surprised if that was the problem.

[NOTICE AT THE FIRST CIRCLE OF THE LINUX INFERNO]

Creating a bootable DVD from an .iso image is basic knowledge when dealing with Linux.  Not trying to denigrate yours, just warning you that it IS only going to get tougher from here on out.


Note: Some computers just aren't that Linux-compatible, either.  I spent many years tearing my hair out trying to install Linux on different Dell laptops.  When I finally abandoned Dell (which I should have long before) I discovered the problem was Dell, not Linux.  I've had no problems installing and using Linux on my Toshiba, Compaq, Acer and Lenovo notebooks.  Maybe yours is just determined to be a mule and you should try a different computer.  Get a cheap laptop on eBay for < $100 and experiment on that.  The brands I listed are probably good bets.  Acer, especially.  Their netbooks originally shipped with Linux, so their hardware is probably certain to be compatible.  You can also google "[computer brand (or model)] linux issues (or "compatibility", "problems", etc.) and see if the model you're considering is a good bet for Linux or not.

---

### Post by whitesmith on 2014-02-09
By all means check out *Linux Is Not Windows* in my sig line ... could save you a lot of trouble and frustration. Best regards.

---

### Post by whitesmith on 2014-02-09
> **ken15 said:**
> Please don't baffle me furtherBest possible reason to read *Linux Is Not Windows* from my sig line. I've posted this twice as an indication of importance. Read it and absorb it before doing *anything* with Linux. This OS isn't for everyone. Regards.

---

### Post by Bill Tetzeli on 2014-02-09
A little information to explain the difference between burning a data DVD (which you don't want to do) and creating a bootable DVD from an .iso image (which you want to do):

First, an .iso file is actually not so much a file as a container of files, sort of like a .zip file.  If you burn the .iso file to DVD in data-DVD mode, all you get is an exact copy of the .iso file - essentially inert.  For the .iso file to do its job, the files and folders it contains have to be unpacked and written to DVD in a special way that will make the computer boot into the DVD instead of your hard drive when you turn it on.  That's what happens when you burn an .iso to DVD in image writing mode.  That mode not only unpacks and writes the files and folders to the DVD but also makes the DVD bootable.  I don't know the ins and outs of how or why it works that way, I only know that it does work that way.  That's why I encourage you to look again at the video I linked to and actually follow along with it step by step, or else try Infrarecorder.

This is not an operation unique to Linux.  I was burning backup .iso images of Windows installation media and other bootable software (Norton Antivirus, e.g.) quite a while before I ever wanted to tinker with Linux.

---

### Post by monkeybrain20122 on 2014-02-09
Can you boot from usb? If yes forget about CD, DVD and burning. This sounds like advice from 2002! :)

 [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) 

Install LILI in your Win system and grab a usb flash drive and create a live usb with the .iso you download.

---

### Post by ken15 on 2014-02-09
The 3 files i downloaded and burnt to a DVD were:-ubuntu-13,10-desktop-amd64,ubutu-12.04desktop-i386 and xubuto-i386.iso. They were burnt . I watched the burn and checked the DVD after --.they ARE on it. So if these files which are ones recommended here on this site, are incorrect please say so and quote me the correct ones .I have reviewed once again the M.O on the clip and can find no fault in what I did. but the end result is the same.-- a total inert disc. Yes there are 3 files one of being presumably the install file but the fact that there are 3 should prevent booting. I used my Win7 box to and in the process have screwed it up.I am not a happy camper and can see only one way out.   ken      .

---

### Post by ken15 on 2014-02-09
Thanks for another tip, but no thankyou .I have had enough of Linux and its many problems, 

Ken

---

### Post by Iowan on 2014-02-09
Linux isn't for everyone. Good luck with whatever you choose.

---

### Post by monkeybrain20122 on 2014-02-09
> **ken15 said:**
> The 3 files i downloaded and burnt to a DVD were:-ubuntu-13,10-desktop-amd64,ubutu-12.04desktop-i386 and xubuto-i386.iso. They were burnt . I watched the burn and checked the DVD after --.they ARE on it. So if these files which are ones recommended here on this site, are incorrect please say so and quote me the correct ones .I have reviewed once again the M.O on the clip and can find no fault in what I did. but the end result is the same.-- a total inert disc. Yes there are 3 files one of being presumably the install file but the fact that there are 3 should prevent booting. I used my Win7 box to and in the process have screwed it up.I am not a happy camper and can see only one way out.   ken      .

Well they recommend 3 OPTIONS. You should have used only one. First of all amd64 is for 64 bit machines and i386 32 bits. So You need to make a DVD with EITHER ONE of them and not burning 3 into the same disk (you can make a multiboot CD but that needs extra work) So to test drive them you need 3 DVDs (and you need the right architecture, 32 bit runs on 64 machines but not vice versa) 

Instead of burning disks the easy and fast way is to make a live usb, but they advise CD/DVD probably assuming that you have an old machine which doesn't support booting from usb (the option may needs to be enabled in the BIOS)

---

### Post by Vladlenin5000 on 2014-02-09
Please read again post #28.

---

### Post by ken15 on 2014-02-09
Thanks for your continued advice. however I am OUT. I have come to the conclusion that Llinux is a hobby for masochists. The end result of two days of my time is two wrecked computers. I note that just now I saw another elderly enquirer with exactly the same situation as me . I will keep watch to see if he succeeds. If he does I will ask how .  

Ken

---

### Post by Vladlenin5000 on 2014-02-09
The truth is you stumbled upon a step that has NOTHING to do with Linux. You're still not understanding how you burn a DVD (or CD) from an image file, despite it having been explained quite a few times.

---

### Post by monkeybrain20122 on 2014-02-09
If you burned your DVD in Windows and it didn't work (as others say you failed to understand between a data dvd and an install dvd) how is that Linux's fault? I am wondering have you ever made a bootable Windows CD/DVD from iso?

---

### Post by Bill Tetzeli on 2014-02-09
> **Vladlenin5000 said:**
> The truth is you stumbled upon a step that has NOTHING to do with Linux. You're still not understanding how you burn a DVD (or CD) from an image file, despite it having been explained quite a few times.
Plus one.  What OS are you using when trying to burn the .iso image to DVD?  Linux?  No.  This is an operation that's common across Windows, Linux and Mac.

Several people have already explained to you the difference between burning a data DVD (which is what you're doing) and writing an .iso image to DVD (which you need to do).  You say you can't find the water - we've put it right under your nose, but we can't make you drink it.

I don't know that Linux is an OS for masochists.  All I know is that it provides what I need and more, it gives me a level of security Windows can only dream of and I never have to depend on the vicissitudes of Microsoft again - there will always be an operating system that will suit my needs.  It required a down-payment of nine months of learning, questions, google searches and more.  Now I have less trouble with it than I ever had with Windows, which I had to reinstall every six to twelve months, so the investment was worth it.  And if the distro I use goes all squirrely and pulls a Windows 8, there are dozens of others that are so similar I can jump right over to one of them and not even know I did it.  But as I said several posts back, in your shoes I would just stick with Windows and be happy with that.

If you can't boot into your Win 7 computer - well, you should get your "nerd" friend to come over and help you.  I was about to give you some tips on how to restore it, but it sounds like you really need someone sitting down at the machine who can show you what to do or do it for you.

If you have your Windows 7 installation/recovery DVD, [this video may help you with your issues]("http://www.youtube.com/watch?v=zSsAy6YGwFA").  Very easy to follow in plain and simple English.


P.S.  A lot of Linux users, especially newer ones like myself, aren't really geeks at all.  We just google what we need to learn, learn it, and that's it.  Really. No different than when I needed to learn how to restore the Master Boot Record (which may be what you need to do) or edit the registry in Windows.  It's like what a friend of my brother's said many years ago when he asked her how she learned to be such a good cook.  "I can read!" :-)

---

### Post by Bucky Ball on 2014-02-09
> **ken15 said:**
> Thanks for your continued advice. however I am OUT. I have come to the conclusion that Llinux is a hobby for masochists. The end result of two days of my time is two wrecked computers. I note that just now I saw another elderly enquirer with exactly the same situation as me . I will keep watch to see if he succeeds. If he does I will ask how .  

Ken

Says it all. Post a new thread for any other questions and good luck. This one has read EOL.

*Thread closed.*

---

