---
title: "Toshiba Satellite M30X-S221ST"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by pancho5 on 2014-03-18
I have a Toshiba Satellite M30X-S221ST and it doesn't show up on the Linux on Laptops list.  Should I assume that my machine WILL NOT WORK WELL with Ubuntu 12.04.4, or, is it just a list of user who have successfully used a different version of Linux on their machine and it works well?

The reason why I ask is that Ubuntu 12.04.4 documentation says "Laptops are also supported and nowadays most laptops work out of the box.In case a laptop contains specialized or proprietary hardware, some specificfunctions may not be supported.  To see if your particular laptop works wellwith GNU/Linux, see for example the[Linux Laptop pages]("http://www.linux-laptop.net/")."  :confused:

---

### Post by Dave_L on 2014-03-18
The only real way to find out is to install Ubuntu and see if it works.

---

### Post by pancho5 on 2014-03-18
That's what I thought.  The concern that I have is that this is the only computer that I have.  If it doesn't work, I'm hosed!  BTW, during the installation of Ubuntu 12.04.4, will it ask me how much space I need for my partition or will it automatically assign an amount for my partition?

---

### Post by monkeybrain20122 on 2014-03-18
What are the specs of your laptop, especially graphic card. 
The list is just a small subset of what works, it is by no means comprehensive.

---

### Post by pancho5 on 2014-03-18
Intel(R)82852/82855 GM/GME Graphics Controller.  Is this what you need?  I'm new at this...pls be patient,

---

### Post by buzzingrobot on 2014-03-18
No, I wouldn't assume that.  The Linux versions listed at that site are several years old, so it doesn't appear very current. My ThinkPad came out in 2012, happily runs any version of Linux I throw at it, and is not listed there.

You can search on your specific laptop to look for any issues/solutions other Linux users may have found. 

Best bet:  When you boot an Ubuntu install image, from USB or a DVD, you will have the option to test it in "live" mode.  That's a chance to to see if all your hardware components work. If you have problems, ask for help on these forums. (Live mode on a USB is reasonably speedy; live mode on a DVD is reasonably slow.)

---

### Post by pancho5 on 2014-03-18
I hear what you are saying and I appreciate your feedback, really I do.  But, I'm running WindowsXP and I have no choice but to convert it (support ends 4/8/2014). I will take your advice on the help forums, hopefully the system will be able to run at a point where I can access the internet to ask questions.

---

### Post by buzzingrobot on 2014-03-18
> **pancho5 said:**
> That's what I thought.  The concern that I have is that this is the only computer that I have.  If it doesn't work, I'm hosed!  BTW, during the installation of Ubuntu 12.04.4, will it ask me how much space I need for my partition or will it automatically assign an amount for my partition?

The installer does both, basically.  You'll see an option to *replace* any existing OS the installer finds, another option to install Ubuntu *alongside* any existing the OS finds, and an option to do "Something Else". That last option brings up a GUI that allows manual partitioning. The first two options handle partitioning automatically.

The *replace* option does just that: removes what's there and installs Ubuntu. 
 The "Alongside" option is typically selected when a user wants to dual-boot Ubuntu and Windows. There can be issues and potential sticking points about dual booting related to Windows 8, Secure Boot, etc.  This forum has many threads on that subject, so it's a good place to scan for info before you jump in.

[If you know you want to replace XP with Ubuntu, I'd just go with the "Replace" option and all will very likely be fine.  Do, however, check things out in the "Live" mode first.]

---

### Post by pancho5 on 2014-03-18
Ok...two more questions.  #1) My laptop has a 1.60Ghz processor, 1.96GB RAM, and a 40GB HD.  The Installation guide says I will need 15GB to install Ubuntu.  That leaves 35GB of free space in my HD.  Am I correct in this?  #2) I have two USB Flash drives.  One is a Lexar that has three folders.  One for Mac(which i don't use), one for Windows(which I don't use), and the other for Vaults.  The Vault folder is where I store my MS Word docs, Xcel, and photos.  Will I be able to read/open/update those files after I mount the USB?

---

### Post by buzzingrobot on 2014-03-18
> **pancho5 said:**
> Ok...two more questions.  #1) My laptop has a 1.60Ghz processor, 1.96GB RAM, and a 40GB HD.  The Installation guide says I will need 15GB to install Ubuntu.  That leaves 35GB of free space in my HD.  Am I correct in this?  

You'd have 25GB, not 35. 

If XP is using the entire drive -- all 40GB -- and you select the "Replace" option, Ubuntu will use all 40 GB, i.e, the entire disk.

The "15GB" is an approximate measure of the amount of space all the files in a typical fresh Ubuntu install require.  What you add after that, of course, uses more space.

So, after the install, you'd have 15GB of Ubuntu system on the drive and 25 GB of space in the Ubuntu filesystem at your disposal.

> #2) I have two USB Flash drives.  One is a Lexar that has three folders.  One for Mac(which i don't use), one for Windows(which I don't use), and the other for Vaults.  The Vault folder is where I store my MS Word docs, Xcel, and photos.  Will I be able to read/open/update those files after I mount the USB?

Sorry, can't answer that.  Maybe someone else who knows about Vaults can respond.

---

### Post by Vladlenin5000 on 2014-03-18
> **buzzingrobot said:**
>   Maybe someone else who knows about Vaults can respond.

It's an encryption software bundled with many Lexar JumpDrive and others. _Compatible with MacOS and Windows only_ therefore my suggestion is to backup the contents and then just delete the vaults. 
If you need an encrypted partition/volume in that drive (or any other) you can later create it using Truecrypt (multi-platform, free and open-source, noticeably better performance, etc.).

---

### Post by Mark Phelps on 2014-03-18
> The Vault folder is where I store my MS Word docs, Xcel, and photos. Will I be able to read/open/update those files after I mount the USB? 

Can't really say for sure.  Ubuntu allows for the installation of Wine -- which will then allow you to run some Windows apps.

MS Office 2007 works fairly well in Wine, as do some components of Office 2010.

But quite frankly, nothing works as well with MS Office as does MS Windows.

So, if you really depend on using MS Office components on a daily basis, it is best to keep MS Windows around for that.

---

### Post by mastablasta on 2014-03-18
> **pancho5 said:**
> That's what I thought. The concern that I have is that this is the only computer that I have. If it doesn't work, I'm hosed! BTW, during the installation of Ubuntu 12.04.4, will it ask me how much space I need for my partition or will it automatically assign an amount for my partition?

which is why there is a "Try it" option (live mode) available after you boot from USB or DVD. you can run the OS see if Wi-fi and graphics works. If it works then you can install if not well don't install it. in live mode the OS is loaded into RAM, and it takes longer to load it from DVD or USB than it will later from hard disk. but the "good" side is that once you exit all changes are lost (unless you did some disk changes) and the OS is gone into the air :-) .

I would go with Xubuntu on this maschine. if you just want to try it out a bit 8-10 GB disk is enough.

the OS itself will take about 6GB, then the kernel updates can quickly add a GB or 2GB. well with 8GB space for the OS i have about 1GB free for rpograms. not much but enough for testing etc. only i created a small swap. if swap is 2GB then ofcourse you need that part of disk as well. and if oyu want to try some wine porgrams then 15 GB at least in total.

---

### Post by NM5TF on 2014-03-18
> **pancho5 said:**
> Ok...two more questions.  #1) My laptop has a 1.60Ghz processor, 1.96GB RAM, and a 40GB HD.  The Installation guide says I will need 15GB to install Ubuntu.  That leaves 35GB of free space in my HD.  Am I correct in this?  #2) I have two USB Flash drives.  One is a Lexar that has three folders.  One for Mac(which i don't use), one for Windows(which I don't use), and the other for Vaults.  The Vault folder is where I store my MS Word docs, Xcel, and photos.  Will I be able to read/open/update those files after I mount the USB?

question #1......I believe most Linux installs only really need around 8-10 GB to run perfectly....

question #2.....yes, you will be able to read/open/update all your files with no problems using Libre Office that is
                      installed with Linux

tommy

---

### Post by buzzingrobot on 2014-03-18
LibreOffice is, loosely speaking, an Office clone.  I rarely use either. But, I gather LibreOffice is good at handling many Office formats, but still not so good at some of the newest formats.

This is easily testable in a live session.  If you have an empty USB port available, you could insert your Vault USB, launch LibreOffice, and see if it copes with the Vault encryption.  If not, as suggested, copy the de-crypted files somewhere safe until you get Ubuntu installed.

---

### Post by mastablasta on 2014-03-18
if libre office doesn't work, then there is also WPS or Kingsoft office. A popular chinese mS office clone (well actually not so much a clone since it's older than MS office i believe).

There is also caligra office etc. depends what kind of format one uses. lately libre ofice has imporved a lot on using the MS office format.

---

### Post by Frogs Hair on 2014-03-18
If 15 of 40 GB is used for ubuntu than 25 remains and there is a swap consideration also. Most MSO documents will open in Libre Office and can can be saved as MSO documents. Photo extensions such as .jpg , .png and so on are common both operating systems and Shotwell is the default photo manager.

 [http://www.yorba.org/projects/shotwell/](http://www.yorba.org/projects/shotwell/)

---

### Post by squakie on 2014-03-18
Have you tried running off a live media first - such as the dvd or USB?  I'd try that before I' try anything else.  If things look good there we can proceed with helping you with the install.  If not, STOP and post back the nature of the problem(s) and any relevant screen captures, error messages, etc..  This way you don't "lose" you PC until after we get things settled down a little.

For Office, I can only go by my recent experience.    The documents I worked with MSOffice 2007 documents.  I didn't have too much trouble with them, although sometimes the formatting got messed up.  The real problem came in sharing those documents back to someone with Windows after I had updated them in LibreOffice.  Again, the formatting was messed up.  Was not pleasant making a lot of changes over an extended amount of time only to find they didn't appear the same in MSOffice on a Windows platform.  My experience could be unique.  It could be that there was something I missed that I needed to do.  I'm not a big user of MSOffice on the Windows side or LibreOffice on the Linux side.  I do some VERY basic things.  The ones I had problems with were somethings I was trying to rescure from my brother in-law's failing notebook (read:  virus in Windows, only way to get the PC to boot was either by Linux live media or the eventual reinstall of Windows).

---

### Post by mörgæs on 2014-03-19
For your hardware I would recommend Lubuntu 13.10. You need to add this xorg.conf after installation:
[https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html)

I don't understand why people are still bothering with office packages. I suggest loading it all into Google Docs.

---

### Post by mastablasta on 2014-03-19
oh yes, also cloud offices work.

however i have blocked access to them at work :-)
> [FONT=Helvetica][SIZE=2]Your request was denied because of its content categorization: "File Storage/Sharing;Office/Business Applications" [/SIZE][/FONT]

---

### Post by Vladlenin5000 on 2014-03-19
> **mörgæs said:**
> I don't understand why people are still bothering with office packages. I suggest loading it all into Google Docs.

A good suggestion I often follow. However I'm not an *hardcore* "office" user, far from it. I know a lot of writers and people who need to do text revision and translations in a daily basis and they all complain about GDocs limitations, namely the absence of dictionaries. Hence, the recommendation to have LibreOffice + KingSoft Office (WPS) and only as the last resort for those who can't/won't go without the Microsoft product install it emulated or in a VM.

---

### Post by pancho5 on 2014-03-19
What am I doing wrong?:confused:  I Dl'd 12.04.4 ISO to a DVD-R, on a different computer.  My own Laptop only has DVD-R/CD-RW capability. I changed my BIOS setting to read the CD first, then the HD in that order.  After I shutdown my Laptop, power it up so that it will read the DVD, it attempts to read the DVD, but after a number of clicks from the drive it stops, then it starts to bring up WindowsXP.

My objective to the above is to "Try" Ubuntu first BEFORE installing it on my laptop.  Any help would be much appreciated.:mad:

---

### Post by su:bhatta on 2014-03-19
Hi.

You will have to provide some details before being advised.
Did you do a MD5 checksum of your downloaded  iso for errors ?  You can use the help page here : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you burn the DVD right using 'Burn Image', was it successfully burned?

The make of your laptop, it's hardware details will be also useful if you can provide them. CPU, Graphics card etc. not right away but. it helps.

---

### Post by pancho5 on 2014-03-19
> **bhattabhishek said:**
> Hi.

You will have to provide some details before being advised.
Did you do a MD5 checksum of your downloaded  iso for errors ?  You can use the help page here : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

"Did you burn the DVD right using 'Burn Image', was it successfully burned?" I used the 'burn image', and it successfully burned.

"The make of your laptop, it's hardware details will be also useful if you can provide them. CPU, Graphics card etc. not right away but. it helps."
I have a Toshiba Satellite M30X-S221ST;
Intel(R)Pentium(R) M processor 1.60Ghz
Intel(R) 82852/82855 GM/GME Graphics controller
Matshita UJDA760 DVD/CDRW

Anything else you need?

---

### Post by grahammechanical on 2014-03-19
Please confirm that the DVD (disk) that you have burned Ubuntu to is compatible with that optical drive? Did you test out the disk on the machine that burned the disk?

Regards.

---

### Post by sudodus on 2014-03-19
> **pancho5 said:**
> "
I have a Toshiba Satellite M30X-S221ST;
[COLOR=#800080]Intel(R)Pentium(R) M processor 1.60Ghz[/COLOR]
Intel(R) 82852/82855 GM/GME Graphics controller
Matshita UJDA760 DVD/CDRW

Anything else you need?

I suspect that your CPU lacks a PAE flag. In linux, try this command

```
grep --color pae /proc/cpuinfo
```

You should get **[COLOR=#ff0000]pae[/COLOR]** with red text in the output, otherwise you don't have a PAE flag.

One alternative is to download the ***Xubuntu 12.04 LTS non-pae iso file***.

Another alternative is Lubuntu fake-pae according to this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

or if you want to try the 'latest and greatest', no I mean latest and smallest for old computers: The the 9w installer and an experimental non-pae kernel with Lubuntu Core beta 1 according to this link (posts #88 and #89 and the following posts)

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

Finally, when released in April, you will be able to get Lubuntu Trusty that will be possible to install with the boot option **forcepae** with that CPU.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by pancho5 on 2014-03-19
Did not confirm that the DVD I burned if it's compatible with my optical drive.  Don't know how to do this, and, that computer is not with me.  But, after I burned the disk, the Windows pgm that I used went back and tested the image and said it was okay...I'm sure of this.

---

### Post by pancho5 on 2014-03-19
I do not have a Linux machine.  I am attempting to convert from WindowsXP to Ubuntu due to the fact that XP will no longer be supported...plus, I am poor!

---

### Post by sudodus on 2014-03-19
You need to burn the iso image to the device, *not* burn a data DVD with the iso file on it. If you insert the DVD into any running computer, you should see a lot of files and directories (not a single iso file).

You can also try to boot another computer with the DVD disk to check that it is OK. Ask a friend or colleague ...

---

### Post by sudodus on 2014-03-19
> **pancho5 said:**
> I do not have a Linux machine.  I am attempting to convert from WindowsXP to Ubuntu due to the fact that XP will no longer be supported...plus, I am poor!

Have you got a USB pendrive, or is CD/DVD your only option for booting?

---

### Post by pancho5 on 2014-03-19
I did have a USB pendrive, but it was ruined 2-3 weeks ago when I attempted to DL the image or iso (can't remember which one I tried...got p---ed at the time), and I didn't want to purchase another pendrive to experiment and waste that one again.  That's why I reverted back to a CD/DVD.  So, I want to go the old way for safety reasons.

---

### Post by pancho5 on 2014-03-19
> **sudodus said:**
> You need to burn the iso image to the device, *not* burn a data DVD with the iso file on it. If you insert the DVD into any running computer, you should see a lot of files and directories (not a single iso file).

You can also try to boot another computer with the DVD disk to check that it is OK. Ask a friend or colleague ...

Pleas clarify what you mean that I "need to burn the iso image to the device..." I'm a newbie here since I have been a Windows "user", not a certified MS professional.:confused:

---

### Post by sudodus on 2014-03-19
I see that you are disappointed with the pendrive.

You can use ***md5summer*** in Windows to check that the md5sum of the downloaded iso file is correct.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[http://www.md5summer.org/](http://www.md5summer.org/)

Please check (in Windows), if the DVD contains one iso file or a lot of  files and directories! You might need to burn a new DVD with the  slowest burning speed possible, and as said before, burn an iso file to  the device, not a data DVD. Which burning software do you use?

---

### Post by sudodus on 2014-03-19
> **pancho5 said:**
> Pleas clarify what you mean that I "need to burn the iso image to the device..." I'm a newbie here since I have been a Windows "user", not a certified MS professional.:confused:

There are some descriptions at the internet:

[http://www.wikihow.com/Burn-ISO-Files-to-DVD](http://www.wikihow.com/Burn-ISO-Files-to-DVD)
[http://pcsupport.about.com/od/toolsofthetrade/ht/burnisofile.htm](http://pcsupport.about.com/od/toolsofthetrade/ht/burnisofile.htm)
[http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file](http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file)

---

### Post by pancho5 on 2014-03-19
> **sudodus said:**
> There are some descriptions at the internet:

[http://www.wikihow.com/Burn-ISO-Files-to-DVD](http://www.wikihow.com/Burn-ISO-Files-to-DVD)
[http://pcsupport.about.com/od/toolsofthetrade/ht/burnisofile.htm](http://pcsupport.about.com/od/toolsofthetrade/ht/burnisofile.htm)
[http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file](http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file)

Thanks for the info...in reviewing the wikihow link, I used the Windows 7 to create the DVD.  I did exactly what the instructions said pertaining to iso file burning, plus, I selected the "verify disc after burning".

But, didn't you indicate that I SHOULD NOT have created the dvd in this fashion?:confused:

---

### Post by sudodus on 2014-03-19
I did not know how you created the DVD, so I wanted to make sure you used a good method.

We need to sort out your problem, to find out what is correct and what might be wrong. One way of doing it is to check a number of things.

1. Please check (in Windows), if the DVD contains a lot of  files and directories! If that is so, you have used a suitable method.
2. Please check with md5summer that the download was good.
3. Please check in another computer, that it can boot from the DVD!
...

We don't know yet if the DVD is good or bad. We don't know yet, if the computer can boot with the operating system, that is on the DVD. We don't know if there is something wrong with the DVD drive (the hardware)...

The more we know about the computer, the better we can help. There might be problems with the drivers for the

- graphics chip/card
- wifi chip/card

and these might vary within a model, so let us know what are the specs of your particular computer. It should be possible to find via the Windows Control Panel.

---

### Post by pancho5 on 2014-03-19
> **sudodus said:**
> I did not know how you created the DVD, so I wanted to make sure you used a good method.

We need to sort out your problem, to find out what is correct and what might be wrong. One way of doing it is to check a number of things.

1. Please check (in Windows), if the DVD contains a lot of  files and directories! If that is so, you have used a suitable method.
2. Please check with md5summer that the download was good.
3. Please check in another computer, that it can boot from the DVD!
...

We don't know yet if the DVD is good or bad. We don't know yet, if the computer can boot with the operating system, that is on the DVD. We don't know if there is something wrong with the DVD drive (the hardware)...

The more we know about the computer, the better we can help. There might be problems with the drivers for the

- graphics chip/card
- wifi chip/card

and these might vary within a model, so let us know what are the specs of your particular computer. I should be possible to find via the Windows Control Panel.

This is what I know:
1. The DVD DOES NOT contain a lot of files and directories...its just one ISO file of 12.04.4 desktop i386.  As you know, I used the Windows 7 burn utility on a different computer (Dell) to generate the CD.
2. Since the DL was done on another computer, I cannot go back and check the file because I deleted it AFTER I burned the image to DVD disc.
3. I will not be able to take the burned ISO disk to another computer until sometime Thursday to see if it will boot.

There is nothing wrong with the DVD drive on my Toshiba Laptop...I play DVD's to watch movies.  Watched a move last Saturday.

The graphics chip card is: Intel(R) 82852/82855 GM/GME Graphics Controller.  The driver for it is Version 6.14.10.3722; dated 11/20/2003.

Wireless card: Intel(R) Pro/Wireless 2200BG Network Connection

Last but not least, I know you are trying to help me...and I appreciate your efforts, really I do.  But, why would the Ubuntu 12.04.4 instructions say to burn the ISO file that was Dl'd?? [http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

I don't understand why would there would be a problem with ONLY A ISO FILE??  The other files and folders are irrelevant for the install, correct?  This is true providing that their is nothing wrong with the media, correct again??

---

### Post by Vladlenin5000 on 2014-03-19
1. Wrong, as explained before.

Everything else depends on that. The method 1 here [http://www.wikihow.com/Burn-ISO-Files-to-DVD](http://www.wikihow.com/Burn-ISO-Files-to-DVD) should work provided you double-click the ISO and subsequently the given ISO is recognized as a "disc image file". Do anything else will result in a data DVD with the ISO inside, precisely what we DON'T want.

---

### Post by pancho5 on 2014-03-19
> **Vladlenin5000 said:**
> 1. Wrong, as explained before.

Everything else depends on that. The method 1 here [http://www.wikihow.com/Burn-ISO-Files-to-DVD](http://www.wikihow.com/Burn-ISO-Files-to-DVD) should work provided you double-click the ISO and subsequently the given ISO is recognized as a "disc image file". Do anything else will result in a data DVD with the ISO inside, precisely what we DON'T want.

Clarification: Are you referring to Sudodus #1, or to "my" #1?:confused:  In other words...who is wrong here? Yes, I did double click on the ISO image and burned the CD.  It is my opinion, or, understanding is that all I need is the ISO file (or image file) because it's just a single file.  When read, it opens up all the folders, sub-folder, files, etc. to load the OS, correct?  I don't need "other" files outside of the ISO file to read, do I?

---

### Post by sudodus on 2014-03-19
In one meaning, yes, the only thing you need is the iso file. But you can write it to the whole device at the low level, 'burn the iso' or you can 'burn the file' to the file system (the high level way like normal copying of a file) of the DVD and get a 'data DVD'. You must do it the correct way, otherwise it does not work.

So I am asking again: When you run Windows and insert the DVD disk into the DVD drive, you will be able to use the file browser Explorer to look at the content of the DVD:

- Do you see one and only one file, and the file has the file extension iso (somename.iso)? -- this is wrong, it will not work

- or do you see several files and directories? -- this is right, the low level copy of the iso file to the device made its content appear at the DVD level (as several files and directories)

If the DVD is wrong, you have to read very carefully the instructions at the internet links and try again until you manage to get it right. If necessary, try another program to do it.

---

### Post by pancho5 on 2014-03-19
> **sudodus said:**
> In one meaning, yes, the only thing you need is the iso file. But you can write it to the whole device at the low level, 'burn the iso' or you can 'burn the file' to the file system (the high level way like normal copying of a file) of the DVD and get a 'data DVD'. You must do it the correct way, otherwise it does not work.

So I am asking again: When you run Windows and insert the DVD disk into the DVD drive, you will be able to use the file browser Explorer to look at the content of the DVD:

- Do you see one and only one file, and the file has the file extension iso (somename.iso)? -- this is wrong, it will not work

- or do you see several files and directories? -- this is right, the low level copy of the iso file to the device made its content appear at the DVD level (as several files and directories)

If the DVD is wrong, you have to read very carefully the instructions at the internet links and try again until you manage to get it right. If necessary, try another program to do it.

Hmm...I didn't know there was a difference between a 'data dvd' and a dvd.  What I used was a Memorex DVD-R 16x 4.7GB 120min CD.  Am I okay here?

Now, when I insert the DVD 'in my Laptop', it just clunks away for about 30 seconds and stops.  Not sure what you mean using the 'file browser Explorer' to view the content of the DVD.  What I am doing is Start/My Computer/DVD-CD-RW (D). Then it says "Please insert Disk in Drive D."  The DVD is inserted in the CDROM drive.

---

### Post by Vladlenin5000 on 2014-03-19
I'll try to make it simple:
1. Properly burned - again - you'll see in the resulting disc folders (eg: isolinux) and files. That's a _bootable DVD_. You can easily check it in _any_ computer running _any_ OS, you just need _any_ file explorer to see the disc's contents like you would do for _any_ other disc, drive, whatever...
2. If there's only one file inside and it's the ISO then you just burned a simple data DVD with that file inside. It ISN'T bootable, IT DOESN'T WORK, PERIOD!

---

### Post by pancho5 on 2014-03-19
> **Vladlenin5000 said:**
> I'll try to make it simple:
1. Properly burned - again - you'll see in the resulting disc folders (eg: isolinux) and files. That's a _bootable DVD_. You can easily check it in _any_ computer running _any_ OS, you just need _any_ file explorer to see the disc's contents like you would do for _any_ other disc, drive, whatever...
2. If there's only one file inside and it's the ISO then you just burned a simple data DVD with that file inside. It ISN'T bootable, IT DOESN'T WORK, PERIOD!

Okay, without a shadow of a doubt, this is what I have...just one ISO file.  I am almost sure of it even though I cannot read the DVD with 'file explorer' in WinXP.  But, I am only following the directions when "Download Ubuntu Desktop" [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)  and selecting 32-bit machines.  I click on the 'orange' button for Ubuntu 12.04 LTS which then shows "ubuntu-12.04.4-desktop-i386.iso"..which is a WinRAR archive (731MB).  Then I save the file to start the DL.  So, you are saying I am doing this incorrectly, and/or, missing another step in the process to generate a bootable cd??

---

### Post by slooksterpsv on 2014-03-19
You have to use a program to burn the ISO to a dvd, if you're running XP or Vista you can download ISORecorder to burn a .iso file to a CD. If you have Windows 7, 8, 8.1, or above burn image is an option.

An ISO is a file that lays out how the cd should be burned, and information on how to make the cd bootable may be available in the iso file as well. The iso file is the combined contents of everything, but you have to have a program determine how to write that content to the cd/dvd - such as ISORecorder. If you take the iso file and just put that file on the cd, it won't work, a program has to do it's magic with that iso file to put the content on the cd (some items in specific places).

---

### Post by Vladlenin5000 on 2014-03-19
An ISO file is a "snapshot", an "image" of a disc, containing everything that should be in the original disc in the same folder structure and the same file system. Hence, it can be used to produce an exact copy of the original disc but the ISO file itself it's just a container. It ISN'T a WinRAR file - although WinRAR as well as hundreds of other apps can "open", edit and even extract the ISO file contents.

There are two steps in this process and, apparently, you're failing in the second only. Whatever app/method you use to burn the DVD is _completely independent_ of the download, ie, regardless of what you'll use to burn the disc you need to have the ISO file downloaded to your local drive (it doesn't matter what OS you use in this stage, provided it has at least one app capable of "burning an ISO to CD/DVD", ie, use that ISO file to make an exact copy of the original disc.
So yes, first of all you need to make sure you have a good ISO - hence the aforementioned checksum, a "tool" to verify the integrity of the downloaded file. _Usually_ you can ignore this verification, most browsers / download managers nowadays do a good job but occasionally error occur and even if successfully burned it'll give you problems during the installation process later on.
Now, assuming you already have a good ISO file the next step is use it to burn the installation media (DVD), not burn it inside a regular data DVD (DVD-ROM) ***This is the point you must understand, the sooner the better*** otherwise this thread leads to nowhere. There are dozens of free apps for Windows that can do it easily. The free InfraRecorder - [http://infrarecorder.org/](http://infrarecorder.org/) - comes to mind (also mentioned in Ubuntu tutorials) and it even has a video tutorial: [http://dai-videotutes.blogspot.com.es/2007/07/ifrarecorder-burning-iso.html](http://dai-videotutes.blogspot.com.es/2007/07/ifrarecorder-burning-iso.html)

---

### Post by pancho5 on 2014-03-19
If I could, I would buy you a pint. I did DL infrarecorder on my laptop, but when I determined I didn't have enough space on a regular CD to burn it, I had to think of other ways how to DL it. Then I didn't think about again because my brother has a win 7 machine and assumed he already had a burning utility, and what I was using would solve all my problems.

---

### Post by sudodus on 2014-03-20
An alternative is to download the Lubuntu 13.10 32-bit desktop iso file

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
and check it with the md5sum from
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

```
5e85e368b6eaf1b9f5cf88467c6570f5  lubuntu-13.10-desktop-i386.iso 
```

This iso file is small enough to fit in a CD disk. It might be possible to burn with your own machine. You need not burn a DVD, you can burn a CD. The same holds about burning the iso as has been explained by Vladlenin, slooksterpsv and me. You should also burn at the slowest possible speed, to improve the chances of success.

[COLOR=#696969]Lubuntu has a simpler desktop environment than standard Ubuntu and runs better in old computers, but it is not as fancy. An alternative between these two flavours is Xubuntu. You can get Xubuntu in two versions, 12.04 LTS and 13.10. Xubuntu is light, while Lubuntu is ultra-light.[/COLOR]

---

### Post by mörgæs on 2014-03-20
Your two threads have been merged. 
Please open only one thread on each topic.People answering are wasting their time dealing with the same hardware twice.

---

### Post by pancho5 on 2014-03-20
> **sudodus said:**
> An alternative is to download the Lubuntu 13.10 32-bit desktop iso file

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
and check it with the md5sum from
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

```
5e85e368b6eaf1b9f5cf88467c6570f5  lubuntu-13.10-desktop-i386.iso 
```

This iso file is small enough to fit in a CD disk. It might be possible to burn with your own machine. You need not burn a DVD, you can burn a CD. The same holds about burning the iso as has been explained by Vladlenin, slooksterpsv and me. You should also burn at the slowest possible speed, to improve the chances of success.

[COLOR=#696969]Lubuntu has a simpler desktop environment than standard Ubuntu and runs better in old computers, but it is not as fancy. An alternative between these two flavours is Xubuntu. You can get Xubuntu in two versions, 12.04 LTS and 13.10. Xubuntu is light, while Lubuntu is ultra-light.[/COLOR]

I appreciate the information...but I don't consider myself not even a 'novice' with any Linux OS.  I think I will stick with Ubuntu 12.04.4 for now.  Reason being that it will be supported until 2017. 13.10 only for 7 months or so.

---

### Post by Vladlenin5000 on 2014-03-20
The installation media for Ubuntu must be a DVD indeed. Since some releases ago it no longer fits a regular CD. The requirements for accurate download of the ISO file and the methods to burn it are the same though. As already mentioned there are still some Ubuntu flavors like Lubuntu that kept the installation media small enough to fit a CD. I agree you should try first the standard Ubuntu - your hardware supports it just fine - and going for a LTS is a wise choice. We'll have another one, 14.04, in just a few weeks.

Regarding the installation itself, provided the computer is able to boot from USB - it is - why don't you give it a try instead of burning several DVDs or CDs? A 1GB USB drive should be enough although 2GB is preferable...

PS - Thank you for the offer. We surely can do that - have a pint -. If you come to Galicia, just PM me.

---

### Post by sudodus on 2014-03-20
> **pancho5 said:**
> I appreciate the information...but I don't consider myself not even a 'novice' with any Linux OS.  I think I will stick with Ubuntu 12.04.4 for now.  Reason being that it will be supported until 2017. 13.10 only for 7 months or so.

Sure, you decide what you want :-) Ubuntu 12.04.4 LTS is stable and well polished, a good release with long time support. But the iso file is oversized for CD, so you need to make a DVD disk or a USB drive to install from.

If you need to burn the DVD in your brother's computer, ***please test that it can boot his computer***, and change the burning procedure until you have a DVD that can really boot his computer. Then it is likely that it can also boot your computer.

---

### Post by mörgæs on 2014-03-20
The M30X is from 2003 and has Intel 82855 graphics.

Ubuntu on this hardware will be a painfully slow experience, if you manage to get it to install at all. As already written you should go for one of the light distros regardless of how long the support is.

Bodhi Linux is light and has support through 2017.

---

### Post by pancho5 on 2014-03-20
> **Vladlenin5000 said:**
> The installation media for Ubuntu must be a DVD indeed. Since some releases ago it no longer fits a regular CD. The requirements for accurate download of the ISO file and the methods to burn it are the same though. As already mentioned there are still some Ubuntu flavors like Lubuntu that kept the installation media small enough to fit a CD. I agree you should try first the standard Ubuntu - your hardware supports it just fine - and going for a LTS is a wise choice. We'll have another one, 14.04, in just a few weeks.

Regarding the installation itself, provided the computer is able to boot from USB - it is - why don't you give it a try instead of burning several DVDs or CDs? A 1GB USB drive should be enough although 2GB is preferable...

PS - Thank you for the offer. We surely can do that - have a pint -. If you come to Galicia, just PM me.

If I had a spare USB memory stick, I would definitely try it.  As of now, I only have one and that one is a 8GB Lexar with all my data backup.  I had an 8GB Sandisk, but I ruined it trying to DL Ubuntu 12.04.4 to it...it became unrecognizable (but dig this...did a online chat with Sandisk support, they couldn't resolve my problem, so they are going to mail me a new one in a week or so...Haha!).  So for now, I must stick with DVD's.

---

### Post by pancho5 on 2014-03-20
> **mörgæs said:**
> The M30X is from 2003 and has Intel 82855 graphics.

Ubuntu on this hardware will be a painfully slow experience, if you manage to get it to install at all. As already written you should go for one of the light distros regardless of how long the support is.

Bodhi Linux is light and has support through 2017.

With all due respect, how would you know this.  Did you look up the specs of the machine, and, compared to what you use or had used at one time?  Remember...I am not a novice, but willing to learn.  I just want to make sure this will work...drivers, printer (HP Officejet 4215xi All-in-one (printer, scanner, fax, copy).  This is the only computer I have, and I must share with my spouse.

---

### Post by sudodus on 2014-03-20
I'm glad to read that Sandisk promised to send you a new pendrive :-)

There are many suggestions thrown at you from several persons trying to help. I think you should sit back and decide what to try and in which order. Try each of the alternatives thoroughly and do not skip to the next one until you have really tried hard to make it work.

For example,

- make sure the download was good; check the md5sum with md5summer
- create an install DVD that really works
- test the Ubuntu system - if you are happy with it, that is good,

otherwise

- download and check an iso file with another (lighter) operating system
- create an install DVD (should be easy now that you know how to do it) and/or when the pendrive arrives: make a USB boot drive.
- test this other system and compare with the previous one
...

until you have a system that works well for you.

---

### Post by mörgæs on 2014-03-20
> **pancho5 said:**
> Did you look up the specs of the machine
No, you posted them in the beginning of the thread. 

> **pancho5 said:**
> compared to what you use or had used at one time?
Yes. The 82855, which was born in the spring of 2003, is a common graphics card, both at my household and at Ubuntuforums.

If you want a safe bet, which I understand and support, you should go light.

---

### Post by pancho5 on 2014-03-20
> **mörgæs said:**
> No, you posted them in the beginning of the thread. 


Yes. The 82855, which was born in the spring of 2003, is a common graphics card, both at my household and at Ubuntuforums.

If you want a safe bet, which I understand and support, you should go light.

Thank you for the information...much appreciated.  If I DL the Bodhi and Lubuntu OS's as well as Ubuntu 12.04.4, will all these come with the option to evaluate it "Live" before making a final decision to install it to replace my WindowsXP?  

Also, will the 'Live' option on all OS's allow me to test out my HP Officejet 4215xi All-in-one printer?

---

### Post by sudodus on 2014-03-20
Lubuntu desktop installer and Bodhi come with the option to evaluate it "Live" before making a final decision to install it. [COLOR=#696969]There is also an alternate installer for Lubuntu. It lacks the live option, but works with lower RAM and when there are problems with the graphics.[/COLOR]

-o-

I 'm not sure about testing printers. I think it is possible to test (maybe you need install something into the live system, that will disappear at shutdown or reboot).

---

### Post by Vladlenin5000 on 2014-03-20
Albeit partially the HP Officejet 4215xi is supported: [http://hplipopensource.com/hplip-web/models/officejet/officejet_4200_series.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_4200_series.html)
I wouldn't bother trying it in a live session. It should be possible but certainly not smooth, ie, it'll be slow and installing HPLIP and running hp-setup can be troublesome. In an installed system you should have no issues. If you do just come back here and we'll help troubleshooting.

---

### Post by pancho5 on 2014-03-20
> **sudodus said:**
> Lubuntu desktop installer and Bodhi come with the option to evaluate it "Live" before making a final decision to install it. [COLOR=#696969]There is also an alternate installer for Lubuntu. It lacks the live option, but works with lower RAM and when there are problems with the graphics.[/COLOR]

-o-

I 'm not sure about testing printers. I think it is possible to test (maybe you need install something into the live system, that will disappear at shutdown or reboot).

A few more questions before I plan on DL'ing the OS's.  Lets say I install Ubuntu 12.04.4.  After making a good effort for it to run, and then decide to not use it.  I can wipe out everything by replacing it with Lubuntu, correct?  In other words, the system is not going to look at it as an upgrade, correct?  And the same goes for Bodhi?

Apps that are important to me are as follows: 

Spotify - Interested in using, and beta version in Ubuntu 12.04.4 is worth a try, and keep.  Not sure if Lubuntu or Bodhi will even support it.

Skype - Interested in using...Ubuntu 12.04.4 says it will work, but, I use it to Skype with family.

Mozilla Firefox & Google Chrome - Sorry...I have become so partial with these browsers, to use another one outside of these, and not having to be supported with Bodhi or Lubuntu is disheartening.  Any ideas or work around here?

Definitely NOT a gammer!!  Never have been...don't want to be.  Computers, marathons, and golf are my passions.

I'm heavily leaning to 12.04.4 because of Spotify & Skype, but if anyone has any additional information about these two apps with Lubuntu or Bodhi it would be greatly appreciated.

Other than the above, I am about ready to make a visit to my brothers house to create some disk images.

---

### Post by sudodus on 2014-03-20
> **pancho5 said:**
> A few more questions before I plan on DL'ing the OS's.  Lets say I install Ubuntu 12.04.4.  After making a good effort for it to run, and then decide to not use it.  I can wipe out everything by replacing it with Lubuntu, correct?  In other words, the system is not going to look at it as an upgrade, correct?  And the same goes for Bodhi?

Yes, you can wipe everything and make a fresh install.
> 
Apps that are important to me are as follows: 

Spotify - Interested in using, and beta version in Ubuntu 12.04.4 is worth a try, and keep.  Not sure if Lubuntu or Bodhi will even support it.

Skype - Interested in using...Ubuntu 12.04.4 says it will work, but, I use it to Skype with family.

Mozilla Firefox & Google Chrome - Sorry...I have become so partial with these browsers, to use another one outside of these, and not having to be supported with Bodhi or Lubuntu is disheartening.  Any ideas or work around here?

It is the same engine under the hood. Bodhi is built on Ubuntu 12.04 LTS. Lubuntu 13.10 is built on a newer version of Ubuntu, 13.10. So it is the desktop environment that makes these distros/flavours/re-spins look differently. It also means that the same application programs can be installed. I have no own experience of Spotify, but I use Skype, Firefox, Chromium-browser and Chrome are there too, as well as many other application programs, LibreOffice etc. Some are installed, some can be easily installed via the software center or a simple command line. These programs *work in all* those distros/flavours/re-spins.
> 

Definitely NOT a gammer!!  Never have been...don't want to be.  Computers, marathons, and golf are my passions.

I'm heavily leaning to 12.04.4 because of Spotify & Skype, but if anyone has any additional information about these two apps with Lubuntu or Bodhi it would be greatly appreciated.

Other than the above, I am about ready to make a visit to my brothers house to create some disk images.

---

### Post by mörgæs on 2014-03-20
> **pancho5 said:**
> Other than the above, I am about ready to make a visit to my brothers house to create some disk images.

Good that you mentioned disk and not USB, as your computer is not likely to be able to boot from USB. Sorry that you have received dubious advice in the thread. 

Please test a handful of distros and post your results. Be aware that the application menu in Bodhi appears after a right-click on the desktop (some people search and search in vain for the application / 'start' button).

All live boots and installations should be done with wired internet connection.

---

### Post by pancho5 on 2014-03-21
Lets say I choose Bodhi, or any other distro that has the Linux kernel which is supported by Ubuntu, or uses.  Does that mean that I will have to get on a different Forum for help?

---

### Post by buzzingrobot on 2014-03-21
> **pancho5 said:**
> Lets say I choose Bodhi, or any other distro that has the Linux kernel which is supported by Ubuntu, or uses.  Does that mean that I will have to get on a different Forum for help?

Probably, but not necessarily.  This forum does have an 'Other OS' section.  But, the chances of getting responses are obviously increased when you talk to users who also use the same distribution.

---

### Post by squakie on 2014-03-21
And please remember what has been posted here several times, as it is a very basic and very important step before you'll ever have success:

When you download and are ready to burn a disk - be it yourself or someone else - it must be burned using the "burn from image", NOT just burning a file to disk.  The Windows option of selecting a file and then using the option "burn to disk" will not do it, it must be burned as an image.

If you, or whomever will be doing this, has ANY questions about this, please post back before wasting another disk.  This is paramount.  You will get nowhere without doing so.  It won't matter what Linux you download - if the file is .iso, you MUST burn as an image, not a file.

I know this has been stated a lot in this thread, but it cannot be repeated enough.  You can try the live sessions, the option of PAE or not, etc., once you have a good image burned on a disk.  Without that, everything else is moot.

---

### Post by pancho5 on 2014-03-21
Thank you...that is exactly what I did!  I will be Dl'ing InfraRecorder to do this.

---

### Post by pancho5 on 2014-03-21
Apparently Bodhi Linux doesn't have a Windows version for checking the hashes using their md5 check.  I read the instructions, but its all for Linux.  Morgaes...you have any ideas?

---

### Post by slooksterpsv on 2014-03-21
You could go to another forum for help, but a lot of users have fixed/resolved issues with your system or any of the Ubuntu variants just using this forum.

Generally most of the fixes that are offered are located in the repositories. If there are bugs, they're reported, or if we're unable to help we may point to 3rd party information locations. I'd say just be sure to prepend your post with bodhi if that's what you're using, or Other OS if not available.

---

### Post by mörgæs on 2014-03-21
If the ISO has approx. the expected size you could just go ahead and burn from it. Normally I don't bother checking the MD5 sum, if the download process is normal (no major delays and so on).

I'm leaving the seven page thread now. I think you should experiment more on your own - not because you are not allowed to post but because people learn the most from that. Good luck.

---

### Post by pancho5 on 2014-03-25
Well, I guess Pentium(R) machines don't have PAE.  This is what I get: *"This kernel requires the following features not present on the CPU: pae."*  Before I try to DL Xubuntu 12.04, nOS, or Bodhi Linux does anyone have any suggestions?

---

### Post by sudodus on 2014-03-26
You have had so many suggestions already. Download more than one of these flavours and re-spins based on Ubuntu 12.04 LTS, and if there are alternatives at the download site, select a 32-bit version with a non-pae kernel or with fake-pae. Try them live before installing.

In alphabetícal order:

Bento
Bodhi
LXLE
Xubuntu

or try Knoppix, which is based on Debian. (Knoppix is made to run live.)

Check at the web sites of each of them! If you focus on one of them, tell us what flavour or re-spin you want, and you can get more detailed advice about that particular one.

---

### Post by mörgæs on 2014-04-05
In case someone finds the thread: 

Lubuntu 14.04 solves all problems mentioned here. 

[LIST=1]
[*]It [installs easily on non-PAE computers]("https://help.ubuntu.com/community/PAE"), unlike previous versions.
[*]The bug in 13.10 for Intel 8xx graphics is solved. Graphics including Flash is working but some users might get a better performance by adding an xorg.conf as described in the link in my signature.
[*]It's small enough to fit on a CD.
[/LIST]

---

### Post by pancho5 on 2014-04-14
Progress has been made.  My laptop is running LXLE but I want to use Xubuntu 12.04.4 LTS.  Now, for those of you who are new reading this thread, I definitely have a Non-PAE machine.  But, from what I have read, the Xubuntu distro that I want to use can run on a Non-PAE machine.  So, what I used was the following UNetbootin instructions to create Linux USB from Linux

 [http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/)

The ISO file that I DL'd to use is: xubuntu-12.04.4-desktop-i386.iso

The USB memory stick is 8GB, and I did not format it because I followed the instructions UNetbootin.

My laptop BIO settings is listed from top to bottom as such: Removable Devices, CD-Rom, Hard Drive, Network Boot

So, I reboot my Laptop and it doesn't try to boot from my USB.

What am I doing wrong or what should I do to resolve the problem?  Is the Xubuntu distro listed as a PAE?  I'm not sure.  Pls advise.

---

### Post by pancho5 on 2014-04-14
I guess it was all a misunderstanding on my part.  Future releases of Xubuntu 12.04.4 will NOT be Non-PAE anymore.  Therefore, does anyone have a work-a-round for this distribution?

---

### Post by mörgæs on 2014-04-14
> **pancho5 said:**
> 
So, I reboot my Laptop and it doesn't try to boot from my USB.


That's what I told you in post 62.
I have a feeling that people are running low on patience. Not writing this as a warning, just as a service to you.

---

### Post by sudodus on 2014-04-14
> **pancho5 said:**
> Progress has been made.  My laptop is running LXLE but I want to use Xubuntu 12.04.4 LTS.  Now, for those of you who are new reading this thread, I definitely have a Non-PAE machine.  But, from what I have read, the Xubuntu distro that I want to use can run on a Non-PAE machine.  So, what I used was the following UNetbootin instructions to create Linux USB from Linux

 [http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/)

The ISO file that I DL'd to use is: xubuntu-12.04.4-desktop-i386.iso

The USB memory stick is 8GB, and I did not format it because I followed the instructions UNetbootin.

My laptop BIO settings is listed from top to bottom as such: Removable Devices, CD-Rom, Hard Drive, Network Boot

So, I reboot my Laptop and it doesn't try to boot from my USB.

What am I doing wrong or what should I do to resolve the problem?  Is the Xubuntu distro listed as a PAE?  I'm not sure.  Pls advise.

I'm glad LXLE is running in your computer now. Congratulations :KS

It is OK to continue testing other flavours or re-spins of Ubuntu and also other linux distros. Many of us do, and enjoy it.

> **pancho5 said:**
> I guess it was all a misunderstanding on my part.  Future releases of Xubuntu 12.04.4 will NOT be Non-PAE anymore.  Therefore, does anyone have a work-a-round for this distribution?

But before asking the same or almost the same questions again, please read all the replies in this thread once more. It might be a good idea to take notes (write down what you think are good tips) and when you have read it all, I think you have a valuable list that will summarize what to do and what to avoid.

Good luck :-)

---

### Post by pancho5 on 2014-05-19
I am currently running LXLE on a Non-PAE machine.  I want to 'experiment' with Lubuntu 14.04 LTS with either One Button Installer or Lubuntu fake PAE, but I want to "Try Lubuntu" without installing it.

I downloaded lubuntu-14.04-desktop-i386.iso, then tried Unetbootin command line procedures to create a Linux USB.  Rebooted my machine and it doesn't recognize my USB...LXLE starts loading after 30 secs or so.

I have read the instructions for Pentium M (which I have), but it doesn't provide the boot screen options to select.  Can anyone assist me on how to resolve this?:(

---

### Post by mörgæs on 2014-05-19
We are dealing with the same hardware, so I merged your post into the old thread.

Posts 75 and 62 might (still) be worth reading.

---

### Post by sudodus on 2014-05-20
> **pancho5 said:**
> I am currently running LXLE on a Non-PAE machine.  I want to 'experiment' with Lubuntu 14.04 LTS with either One Button Installer or Lubuntu fake PAE, but I want to "Try Lubuntu" without installing it.

I downloaded lubuntu-14.04-desktop-i386.iso, then tried Unetbootin command line procedures to create a Linux USB.  Rebooted my machine and it doesn't recognize my USB...LXLE starts loading after 30 secs or so.

I have read the instructions for Pentium M (which I have), but it doesn't provide the boot screen options to select.  Can anyone assist me on how to resolve this?:(

There are detailed instructions how to enable the boot option ***forcepae*** in the following link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

The present version of One Button Installer need booting from USB, but ***the iso file of Lubuntu 14.04 LTS*** can be booted from CD, DVD and USB. This is an improvement of 14.04 LTS due to the forcepae boot option. So if the graphics works, ***you can install from a CD***. If the graphics does not work, it is better to stay with LXLE.

---

