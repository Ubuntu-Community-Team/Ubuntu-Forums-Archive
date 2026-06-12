---
title: "I want to replace Win 7 64 with Ubuntu on it's own partiton"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by J Tinsby on 2013-07-15
I read the article in PC World magazine and I d/l'd the Ubuntu .iso and burned it to a CD that I am running now. I have been so disappointed with Win 7 :icon_frown:
 		
 	
 		 			 

 		
 	
that I want to try Ubuntu instead! I have a dual boot machine with XP Pro SP3 and Win 7 64. I can easily make an Acronis image of 7 and return to it if necessary. 

Will I be limiting myself to what software I can use by installing the 64 bit version of Ubuntu? The one I am using is the 32 bit. I have no need, at present to have support for UEFI, I still have a BIOS.

I do a lot of work with audio files and photos of all kinds. I know there is Gimp for photos but how do I make and play mp3's? I have a lot of audio programs at my disposal as well as ones for photos, I hope I can get something similar for Ubuntu. I need control of the bass and treble at the very least for my files to sound halfway decent, a graphic equalizer would be great, like I have on my Creative Sound card utilities.

Will Ubuntu be able to utilize my 6GB of RAM like Win 7 does? 

I have no interest in using Win 8.

I have one DOS program that I'd like to keep and use, can I use a VM like I do in Win 7?

Must I use Wine, if it's still being used, or some other program to allow me to run a program like Winamp?

I'm fine with the old DOS commands but the ones in Linux are completely foreign to me <sigh> I hope I can manage to avoid them! Lol

Thanks to all in advance any and all advice appreciated! This is a big step and I'm not sure I should take it, but I sure am sick of MS!


J T :D

---

### Post by DaveMcC on 2013-07-15
I know this is of no real help, but having testing photo editing programs on win8, stay away from it, slow and useless
Ubuntu64bit does use your 6gb of RAM as does win7 64bit
gimp for photo editing, it's not bad, but if you use a camera manufacturers own RAW converter "win based" ?  gimp does have it's use, funny thing is gimp 2.8 runs on Lubuntu but 2.6 on ubuntu  12.04lts with gimp 2.8 run windows/single page now it looks like most other photo editing programs all one page...

Audio, sorry not my thing

When I get this computer re-set, it will be the same as your set up

XP sp3 + ubuntu one one drive, drive 2 is all my stored work, and drive 3 is win7

Dave

---

### Post by oldfred on 2013-07-15
If you backup Windows 7 be sure to backup the Windows 7 boot files which probably are in your XP install. Windows only boots from one Windows install, usually the first, formatted NTFS with the boot flag.
       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

If new to Ubuntu I really suggest dual booting. It took me years before I could totally wean myself from XP as I had one application in Windows I liked and then the equivalent was not as good in Linux. While equivalent still was not as good it became better and booting XP occasionally was just not worth it so I finally shut it down.

To properly use the full amount of RAM you do need the 64 bit version of Ubuntu. The 32bit will somewhat use it but it is limited to one app at a time and in effect is swapping RAM in an out.
      
 Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

Linux is not Windows and it really is best to find apps that are equivalent in Linux. Some actually are better, many are just as good but different so there is a learning curve and some just not as good. So it depends on what you want to do.
      
 Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

   Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)


 Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)
[http://www.linuxalt.com/](http://www.linuxalt.com/)

   Best Free Software for Linux
[http://www.techsupportalert.com/content/best-free-software-linux.htm](http://www.techsupportalert.com/content/best-free-software-linux.htm)

Use live installer DVD or flash and run that to see if all your hardware is supported.

---

### Post by J Tinsby on 2013-07-16
Thank you for your replies. I got eh latest 64 bit version 13.xxx and tried to run it from a DVD not installing it. To my surprise I find I have no USB mouse support, when using the 32 bit earlier version I did. There is no PS-2 port on my MB for another mouse.

Trouble rears it's ugly head, and I've only started!

J T

---

### Post by oldfred on 2013-07-16
Some of us consider that part of the "fun" of figuring out why. Others just get frustrated and leave. But I think that is why I left Windows was the frustration was higher with Windows.

Do you have a USB setting for mouse & keyboard in BIOS or a legacy setting for USB?

---

### Post by J Tinsby on 2013-07-16
> **oldfred said:**
> Some of us consider that part of the "fun" of figuring out why. Others just get frustrated and leave. But I think that is why I left Windows was the frustration was higher with Windows.

Do you have a USB setting for mouse & keyboard in BIOS or a legacy setting for USB?

Hi OldFred,
Well offhand I can't say but when I'm in there later today I'll check it out. Seems odd it worked in the 32 bit version but won't now, and I haven't changed any settings since getting the newer 64 bit one.

Well I've been using Wijndoze since v 3 so you can imagine all the frustration and back biting I've been through all these years. If 7 would run like it should I'd stay with it. But when I install programs either as admin or not, when I click the shortcut they won't open. Then the next time I try the same program it WILL open and run normally. I've done so many re-installs I could do it in my sleep. Mercifully I have good old XP Pro to do my REAL work!

I'll check it out!

Cheers,

JT

---

### Post by J Tinsby on 2013-07-16
Oldfred:

I have only 2 settings in the BIOS one is for legacy keyboards and the other pertains to legacy USB support. The latter is set to AUTO changing the former did nothing.

But more important is that I tried to DL the version 13.04 32 bit to see if that would work. When I ran the DVD the program showed me that I had the option to install version 12.04.xx LTS NOT 13.04! 

Why is it doing this> IE: Showing me one download and presenting me with another?

I'd think that others would be complaining about this error but I don't see once complaint! Surely I am not the only one that is getting the latest version.

Thank you and still no joy on the mouse business... as I can't find a version that will allow it to work other than the version I started with!

Thank you,

J T

---

### Post by oldfred on 2013-07-16
I have not downloaded a 32 bit verison since 9.04, so I do not know if that is the case or not. 

What site did you download from as there are mirrors worldwide. I generally download from a local mirror not from the Ubuntu download page.

---

### Post by 1clue on 2013-07-16
Personally when I have an OEM Windows that I might want again, I just yank the hard drive out and install another one.  Put the original in a safe place, then if you want to go back to the dark side you can do so easily and with no doubts.

If you have a fully licensed boxed windows, you might install an extra drive if you have room for it, install *Buntu on that, and then use your windows installation as a KVM guest.  Similar to VMware.

Use the 64 bit version.  There's no reason for you to limit yourself, 64 can run both 32 and 64-bit.

The 64-bit version definitely has USB mouse support.

---

### Post by J Tinsby on 2013-07-16
Hi 1clue and others,

I have no need to get another HD involved I'd be happy to have Ubuntu run on a partition of my main drive.

That said I have d/l from various sites the 64 bit version to no avail. No matter how I configure the BIOS the USB mouse will not function. In one instance I noticed the keyboard lights were flashing off and on while the mouse didn't work so I changed the BIOS setting then tried again. This time not only did the mouse not work I got no dock on the left side of the screen! There were no icons there at all just a vertical stripe.

I should have stayed with the earlier version of Ubuntu that I got the other day, oddly enough everything worked on that one even tho' it was 32 bit. Lord knows what would have happened if I'd installed it and then "upgraded!"

Before I entirely give up I will tell you that I have an Asus Rampage Extreme MB with 6Gb of RAM , an Intel Quad Core Processor Q6600 an Nvidia 8800 GeForce graphics card and sound from the HD X-Fi sound card.

I did encounter the fact that even though I dl a copy of what was supposed to be 3.04 when running from the DVD it showed v12.04 again making no sense so I kept trying various sites to get a version that might be the most current one. There was no way to tell by looking at the files on the DVD what version I really ended up with. All I know is that both the 32 and 64 bit won't work on my machine as it is now.

I think Linux is fine, my Acronis program uses it to restore images of the HD.

Right now there is no hope or making it work as I doubt that the end product is worth all the hair pulling and aggravation. I have enough of that with Win 7 64. Although I love to problem solve there's no need to create more for myself, I have plenty to work on as it is.

Thank you all very much I really appreciate your taking the time to try and help me. Maybe I expect too much from Ubuntu but I don't think having a working mouse is too much to ask. All the best and keep enjoying your Ubuntu systems!! :D

Cheers and beers,

J Tinsby

---

