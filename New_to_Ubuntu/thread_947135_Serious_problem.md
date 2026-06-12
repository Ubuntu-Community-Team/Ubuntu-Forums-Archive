---
title: "Serious problem"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by catalytic on 2008-10-14
I've had some error with Kaspersky Internet security that crashed windows, making it completely unusable. My install cd for XP hangs at one part of the install (its a custom cd made with nlite). I've lost my disc of xp but I have the image saved on my hard drive. I have a partitioned drive C: (windows) D: (files) and another partition where I have attempted to install ubuntu....

I've tried installing ubuntu but can't use it as the mouse and keyboard is all messed up, can't click on things can't open things etc...switched back to breezy badger live cd, which is what I'm using now to post this. 

I can't mount either hda1 or hda2 can't see them using nuatilus command, can't mkdir....how do I mount my hard drives? the mount command doesn't show them listed...

The other problem is the image of my xp cd was created with magic iso....I"m guessing I can't install and run this under wine while using the live cd can i?

how can I copy this image to a cd in ubunty breezy badger live?

---

### Post by eternalnewbee on 2008-10-14
I'm not sure if I quite undestood you, but if you want to burn an iso, you can do that with Brassero in Ubuntu.
And not being able to see your hard drives could possibly have something to do with not having shut down the system properly ( I mean xp).
That's all I can help you with.
Good luck.

---

### Post by bob200800 on 2008-10-14
The Root of All Evil? is a television documentary, written and presented by Richard Dawkins, in which he argues that humanity would be better off without religion or belief in God.
_______________________________________________________________________
[Carhartt Jeans](http://www.workwear1.com/browse.cfm/2,83.html) [dubai real estate](http://www.choicepropertyinvestment.com/international-developments/dubai-property-investment/)

---

### Post by Gazneth on 2008-10-14
Try this code to mount your windows drive. You need to put in your correct harddrive location though hda1 sda2 for example.

Mount NTFS Filesystem regardless of errors
```
Sudo mount  /media/sda1 -o force

```

---

### Post by Sef on 2008-10-14
> I've tried installing ubuntu but can't use it as the mouse and keyboard is all messed up, can't click on things can't open things etc...switched back to breezy badger live cd, which is what I'm using now to post this.

What version did you try and install?

---

### Post by hyper_ch on 2008-10-14
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

---

### Post by bumanie on 2008-10-14
Someone can correct me if I am wrong, but I think you can burn a .iso from the live cd. If the image you have is a standard .iso file, it should burn OK. If you can navigate to the image via the live cd, right click on it and choose burn to disc. It will either work or won't work - worth trying.

---

### Post by catalytic on 2008-10-15
Thanks for the replies, but I lost everything on the hard drive. The ubuntu partitioner rather than resizing my drive changed the whole drive to ext3 format and destroyed all my data. I know hate ubuntu more than I hate windows but I'm stuck using it until I can figure out how to copy another windows cd.

Which leads me onto my next problem....the image I have is .daa!!! I got poweriso onto the machine, but can't figure out how to work it. I can't convert this damn .daa file to .iso. I keep getting this message...

user@user-desktop:~$ poweriso convert /home/user/Desktop/XPMediaC/XP -o /home/user/Desktop/XPMediaC/XP/WindowsXP.daa -o /home/user/Desktop/XPMediac/XP/WindowsXP.iso -ot iso

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

/home/user/Desktop/XPMediaC/XP: The file format is invalid or unsupported.


This is driving me crazy all I want to do is get windows back...but can't get my XP disk until the weekend (have a working disk but left it at mums). I need my computer back up and running today....

What am I doing wrong? I've changed all the file names etc to make it easier.....the .daa file is made by the Poweriso program, so it can't be unsupported!!!!


BTW still keep losing mouse clicks can't click on anything on the desktop, I get stuck in terminal and can't close it or click on anthing. Lucky my keyboard has a close button otherwise I would have to keep restarting x. I'm using 7.04 since its the only cd I could get to install on here, I burnt 8.04 last night but I doubt it will support my older AMD system. 5.10 worked fine for me, every distro since has been nothing but problems, no drivers for my card, no tv out support. This is why I stick with windows, since I can't do anything I want to do in Linux. For example, can't use tv out to watch movies from my pc, can't use tveristy, can't run windows programs (wine does not work, and hasn't since version 5.10). Its the same with every other distro of linux too, waiting for someone to make a linux for the average user that doesn't require all the command line bull. If I knew how to "code" I'd make one myself, so sick of inferior operating systems that don't do what I need them to do. Believe me if I could afford a Mac I'd be buying one tomorrow, when will they bring the prices down low enough for me to actually buy a Mac that has some power??!!

Rant over....

---

### Post by catalytic on 2008-10-15
I tried moving the .daa to the desktop, still wont work, now it tells me there is no such file. Someone PLEASE tell me what command I use to convert the file WindowsXP.daa to and iso. The file is on my desktop.

---

### Post by catalytic on 2008-10-15
I've tried the command poweriso convert WindowsXP.daa -o WindowsXP.iso -ot iso

no such filename


Does the filename have to be in special characters of something??? does it need to be in another language....this is driving me crazy :bangs head against wall:

---

### Post by bobnutfield on 2008-10-15
Sorry. disregard post.  Found incorrect info.

---

### Post by catalytic on 2008-10-15
This has kept me in front of the computer for two whole days now, all I want is Windows not crappy Ubuntu that no average person can possibly use. You must need to be a computer genius to use Ubuntu!! I must no absolutely nothing about computers because no matter what I do I can't seem to do the simplest things, even when copying and pasting code directly into the terminal, the instructions for most of this programs may as well be in another language....I'm begging pleading, someone please walk me through converting a .daa to an iso in simple steps. I'm seriously about to take the computer out the back and burn it...at least with windows I can usually google my issue and the problem is solved.


Sorry...as you can tell I'm extremely frustrated and just want my computer back the way it was.


Poweriso will  just not recognize the .daa it just keeps telling me such file or directory!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by catalytic on 2008-10-15
This is seriously #####!! NONE OF THE BASH COMMANDS WORK....

cd 
cd desktop
cd ~/desktop

I can't navigate to any folder through the terminal it keeps telling me the command cd does not exist!!!

My version of Ubuntu must be completely stuffed...

---

### Post by starcannon on 2008-10-15
> Thanks for the replies, but I lost everything on the hard drive. The ubuntu partitioner rather than resizing my drive changed the whole drive to ext3 format and destroyed all my data. I know hate ubuntu more than I hate windows but I'm stuck using it until I can figure out how to copy another windows cd.

Okay first, don't despair to greatly yet, much of your data can be recovered, and that should be first priority, the more you use the hard drive, the more data that may be permanently lost.

So First:

[LIST]
[*]Grab this software [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[*]Get a USB or another internal Hard Drive to put the recovered files on, trust me you'll find more than you bargained for, and it will take some time to sort through it all, and it will take plenty of space to stash it on.
[*]Follow this guide [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[/LIST]
Second: Ubuntu did not destroy anything, I hope I don't sound too harsh here, but when one is installing a new OS, regardless of what OS it may be, one should always back up important files before doing anything else. Then one must read and understand each and every dialog box before proceeding the next dialog box; indeed there was a warning during the install process that said it was about to destroy everything on the drive.

Third: Again forgive me if I'm I don't sound the way I intend, but its generally bad form to tell someone how much you hate the product you are asking them for FREE advice on. I love my Ubuntu, and because I'm a nice guy I thought I'd post a way for you to get a great deal of your lost files back; however, it would have been nice to have had an appreciative recipient.

Good Luck with everything, I truly hope you find computational bliss.

---

### Post by catalytic on 2008-10-15
Apparently I can burn daa directly with Gburner...like I said can't get anything to work with wine...

user@user-desktop:~/Desktop/porgrams/gBurner$ wine gBurner.exe
fixme:process:IsWow64Process (0xffffffff 0x33fd9c) stub!
wine: Unhandled page fault on read access to 0x045d2ff0 at address 0x7e508631 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x045d2ff0 in 32-bit code (0x7e508631).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e508631 ESP:0033f09c EBP:0033f0d4 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000048 EBX:7e557fe4 ECX:ffffffff EDX:00000000
 ESI:045d2ff0 EDI:7c140420
Stack dump:
0x0033f09c:  ffffffff ffffffff 00000360 00000048
0x0033f0ac:  00000000 00000000 00000000 00000000
0x0033f0bc:  7c1408a0 7c140420 00000000 045d2ff0
0x0033f0cc:  00000120 7e556bc0 0033f294 7e5049ae
0x0033f0dc:  00000120 00000018 045d2ff0 00000360
0x0033f0ec:  7c140420 fffffb80 00002400 00000018
Backtrace:
=>1 0x7e508631 in winex11 (+0x28631) (0x0033f0d4)
  2 0x7e5049ae in winex11 (+0x249ae) (0x0033f294)
  3 0x7e50699a X11DRV_SetDIBits+0x1da() in winex11 (0x0033f344)
  4 0x7eb97143 SetDIBits+0x93() in gdi32 (0x0033f384)
  5 0x7eb989bf StretchDIBits+0x1bf() in gdi32 (0x0033f404)
  6 0x004a9891 in gburner (+0xa9891) (0x0033f458)
  7 0x004b5fa9 in gburner (+0xb5fa9) (0x0033f494)
  8 0x004632a0 in gburner (+0x632a0) (0x007cf1b0)
  9 0x00000001 (0x004c3f50)
  10 0x00436b70 in gburner (+0x36b70) (0x004368a0)
  11 0x9090c300 (0x4c2da8b8)
  12 0x00000000 (0x00000000)
0x7e508631: movl        0x0(%esi),%edx
Modules:
Module  Address                 Debug info      Name (83 modules)
PE      400000-5f2000   Export          gburner
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d766000-7d76a000       Deferred        libgpg-error.so.0
ELF     7d76a000-7d7bb000       Deferred        libgcrypt.so.11
ELF     7d7bb000-7d7d0000       Deferred        libtasn1.so.3
ELF     7d7d0000-7d7fe000       Deferred        libcrypt.so.1
ELF     7d808000-7d878000       Deferred        libgnutls.so.13
ELF     7d878000-7d8a9000       Deferred        libcups.so.2
ELF     7d8d6000-7d908000       Deferred        uxtheme<elf>
  \-PE  7d8e0000-7d908000       \               uxtheme
ELF     7d908000-7d91d000       Deferred        midimap<elf>
  \-PE  7d910000-7d91d000       \               midimap
ELF     7d91d000-7d943000       Deferred        msacm32<elf>
  \-PE  7d920000-7d943000       \               msacm32
ELF     7d943000-7d95b000       Deferred        msacm32<elf>
  \-PE  7d950000-7d95b000       \               msacm32
ELF     7d95b000-7d997000       Deferred        wineoss<elf>
  \-PE  7d960000-7d997000       \               wineoss
ELF     7d999000-7d99e000       Deferred        libxfixes.so.3
ELF     7d99e000-7d9a7000       Deferred        libxcursor.so.1
ELF     7d9a7000-7d9c4000       Deferred        imm32<elf>
  \-PE  7d9b0000-7d9c4000       \               imm32
ELF     7d9c4000-7d9ca000       Deferred        libxrandr.so.2
ELF     7d9ca000-7d9d2000       Deferred        libxrender.so.1
ELF     7d9d2000-7d9d5000       Deferred        libxinerama.so.1
ELF     7e0c8000-7e33d000       Deferred        r200_dri.so
ELF     7e33d000-7e346000       Deferred        libdrm.so.2
ELF     7e346000-7e3a6000       Deferred        libgl.so.1
ELF     7e3a6000-7e3ab000       Deferred        libxdmcp.so.6
ELF     7e3ab000-7e3ae000       Deferred        libxau.so.6
ELF     7e3ae000-7e49f000       Deferred        libx11.so.6
ELF     7e49f000-7e4ad000       Deferred        libxext.so.6
ELF     7e4ad000-7e4b2000       Deferred        libxxf86vm.so.1
ELF     7e4b2000-7e4ca000       Deferred        libice.so.6
ELF     7e4ca000-7e4d3000       Deferred        libsm.so.6
ELF     7e4d3000-7e561000       Export          winex11<elf>
  \-PE  7e4e0000-7e561000       \               winex11
ELF     7e5da000-7e5fa000       Deferred        libexpat.so.1
ELF     7e5fa000-7e625000       Deferred        libfontconfig.so.1
ELF     7e625000-7e639000       Deferred        libz.so.1
ELF     7e639000-7e6a4000       Deferred        libfreetype.so.6
ELF     7e6a4000-7e6c6000       Deferred        oledlg<elf>
  \-PE  7e6b0000-7e6c6000       \               oledlg
ELF     7e6c6000-7e6f9000       Deferred        winspool<elf>
  \-PE  7e6d0000-7e6f9000       \               winspool
ELF     7e6f9000-7e7b5000       Deferred        comctl32<elf>
  \-PE  7e700000-7e7b5000       \               comctl32
ELF     7e7b5000-7e8aa000       Deferred        shell32<elf>
  \-PE  7e7d0000-7e8aa000       \               shell32
ELF     7e8aa000-7e94a000       Deferred        comdlg32<elf>
  \-PE  7e8b0000-7e94a000       \               comdlg32
ELF     7e94a000-7e9d9000       Deferred        winmm<elf>
  \-PE  7e960000-7e9d9000       \               winmm
ELF     7e9d9000-7e9ec000       Deferred        libresolv.so.2
ELF     7e9ec000-7ea0a000       Deferred        iphlpapi<elf>
  \-PE  7e9f0000-7ea0a000       \               iphlpapi
ELF     7ea0a000-7ea5f000       Deferred        rpcrt4<elf>
  \-PE  7ea20000-7ea5f000       \               rpcrt4
ELF     7ea5f000-7ea6b000       Deferred        libgcc_s.so.1
ELF     7eb5f000-7ec1c000       Export          gdi32<elf>
  \-PE  7eb80000-7ec1c000       \               gdi32
ELF     7ec1c000-7ed58000       Deferred        user32<elf>
  \-PE  7ec40000-7ed58000       \               user32
ELF     7ed58000-7ed9e000       Deferred        advapi32<elf>
  \-PE  7ed60000-7ed9e000       \               advapi32
ELF     7ed9e000-7ee38000       Deferred        ole32<elf>
  \-PE  7edb0000-7ee38000       \               ole32
ELF     7ee38000-7ee91000       Deferred        shlwapi<elf>
  \-PE  7ee50000-7ee91000       \               shlwapi
ELF     7efa3000-7efae000       Deferred        libnss_files.so.2
ELF     7efae000-7efb8000       Deferred        libnss_nis.so.2
ELF     7efb8000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff6000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cc7000-b7ccb000       Deferred        libdl.so.2
ELF     b7ccb000-b7e0c000       Deferred        libc.so.6
ELF     b7e0c000-b7e23000       Deferred        libpthread.so.0
ELF     b7e2d000-b7f3e000       Deferred        libwine.so.1
ELF     b7f40000-b7f5b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\user\Desktop\porgrams\gBurner\gBurner.exe
        00000009    0 <==


What the hell does all that mean??

---

### Post by catalytic on 2008-10-15
> **starcannon said:**
> Okay first, don't despair to greatly yet, much of your data can be recovered, and that should be first priority, the more you use the hard drive, the more data that may be permanently lost.

So First:

[LIST]
[*]Grab this software [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[*]Get a USB or another internal Hard Drive to put the recovered files on, trust me you'll find more than you bargained for, and it will take some time to sort through it all, and it will take plenty of space to stash it on.
[*]Follow this guide [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[/LIST]
Second: Ubuntu did not destroy anything, I hope I don't sound too harsh here, but when one is installing a new OS, regardless of what OS it may be, one should always back up important files before doing anything else. Then one must read and understand each and every dialog box before proceeding the next dialog box; indeed there was a warning during the install process that said it was about to destroy everything on the drive.

Third: Again forgive me if I'm I don't sound the way I intend, but its generally bad form to tell someone how much you hate the product you are asking them for FREE advice on. I love my Ubuntu, and because I'm a nice guy I thought I'd post a way for you to get a great deal of your lost files back; however, it would have been nice to have had an appreciative recipient.

Good Luck with everything, I truly hope you find computational bliss.

I don't mean to sound ungrateful, because I'm not, its just that what you are suggesting there is impossible. The whole hard drive and all data is lost, I ended up installing ubuntu on the partition that was stuffed since it would not let me install it anywhere else. 

I don't have a usb drive, I don't have an extra hard drive and I can't afford to get one. I may be able to put the software you suggested on a blank cd but then what do I do with it? I'm positive the whole lot is gone since the ubuntu partitioner DID stuff up my drive. It gave an error suggesting the process hadn't worked, yet it had completely turned my 60GB partition into ext3...

I don't back up, don't know how other than to put everything on disk. This is why I had a partitioned drive so that all my files were seperate from my operating system. I don't have the money to be constantly buying disks that get lost of scratched by the kids...I can't even afford to get a new hard drive so I guess this computer is going to the tip.

I'm sorry I"m just so upset that I've lost all the photo's of my daughtet that I have no way of getting back because I can't afford to pay for someone to fix my computer..

---

### Post by catalytic on 2008-10-15
I just don't understand what I'm meant to do with that program, I don't understand the instructions or how I can burn it to a cd when I have no mouse function.

If someone could walk me through what I'm meant to do, I may be able to fix the problem.... I'm guessing no one is going to help me. Sorry I HATE UBUNTU, just like most of you probably hate windows. I came here for help since it seems to be the only place where people who use ubuntu can give me advice. I'll delete my account and wont be back to bother you again....in the meantime if someone can find it in there heart to help me out step by step with images if possible email [email]jass6314@gmail.com[/email].

I downloaded photorec to the desktop exttracted it now when I type in the command
sudo testdisk-6.9/linux/photorec_static  I get "command not found". Doesn't do me much good does it?

This is the same problem I keep having every time I try to do anything from the command line "command not found" WTF??? Can't poweriso, can't use gburner, can't use photorec. All have same issue, COMMAND NOT FOUND!!!!!!!!!!!!!!! Yes I"m using root and double checking file names.

---

### Post by dmizer on 2008-10-15
Please think about what you're complaining about.

You're trying to use Breezy badger. This is only the 3rd version of Ubuntu (we'll be releasing our 9th version in 14 days). Breezy is more than 3 years old and reached the end of it's support life 2 years ago. Back then, more command line was required and things were far from working perfectly.

In essence, you're complaining about how bad Windows 95 is compared to Mac OSx Leopard.

You may be running into a lot of problems SPECIFICALLY related to using Breezy. First of all, the repositories are no longer maintained and could be feeding you bad data, and the software provided by these repositories is most certainly not current, and may even be broken.

I know this doesn't really help your specific problem, but you should really make an effort to try a more current Ubuntu release to solve your problems. If not that, you should try a more current release of ANY distribution, as many distributions now have live cds.

You can even order free CD's of Ubuntu. Look here: [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Edit:
This command should work even in Breezy:
```
dd if=[COLOR="Red"]windows.iso[/COLOR] of=[COLOR="Blue"]/dev/hdc1[/COLOR]
```
You'll need to change:
[COLOR="Red"]windows.iso[/COLOR] to the actual file name of your windows iso
[COLOR="Blue"]/dev/hdc1[/COLOR] to the match your writable cdrom device.

---

### Post by Keen101 on 2008-10-16
First i suggest trying out the latest Ubuntu version. It should work a lot better than the older version you are using. Try using the Live-CD to see if it even runs on your system first.

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Second, your computer should have come with a xp restore disk.

oh, and if you need to partition i recommend the Gparted Live-CD.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by starcannon on 2008-10-16
> I downloaded photorec to the desktop exttracted it now when I type in the command
sudo testdisk-6.9/linux/photorec_static  I get "command not found". Doesn't do me much good does it?

While it would be recommended to have the the latest LTS version of Ubuntu, I strongly discourage installing anything else until AFTER the lost files have been recovered. Another install attempt could make many files unretrievable; so, learn to use testdisks's photorec software and get you stuff back first.
 
Your command is almost right, but needs a little tweaking.
Lets make sure your using the correct version of Photorec:

```
uname -r
```if it reports 2.4.x.x then Download: [http://www.cgsecurity.org/testdisk-6.10.linux24.tar.bz2](http://www.cgsecurity.org/testdisk-6.10.linux24.tar.bz2)

if it reports 2.6.x.x then Download: [http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2)
R-click and choose "extract here".

Now assuming the download went to your desktop.
```

cd ~/Desktop/testdisk-6.10/linux
sudo ./photorec_static

```
If the program complains that it needs 25 lines, just grab and drag a corner of your terminal window and make it bigger, might require restarting the program for changes to take affect.
Follow the screens and the guide from testdisk's website. And watch for the section where you get to choose the files your interested in recovering. If you do an "Everything" style recovery, it will never all fit on the hdd along with all of the os and other things there, so really try to narrow it down to the "must haves".

.

---

