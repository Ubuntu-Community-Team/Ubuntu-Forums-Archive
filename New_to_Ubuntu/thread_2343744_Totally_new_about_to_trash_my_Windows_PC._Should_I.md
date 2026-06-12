---
title: "Totally new about to trash my Windows PC. Should I migrate over?"
date: 2016-11-18
forum: New to Ubuntu
---

### Post by juntjoo2 on 2016-11-18
I just need a system I can rely on to use and synch some office files. Specifically they are word and excel docs that link together some data from the excel file to a couple word docs and I need to sych them to a cloud service that works with Android to get them on my phone. Windows is driving me mad with these functions so I gotta get out once and for all after 20 years. I've had enough. 

I just gotta know how difficult if not impossible this is to do in my situation. 

Will I need to remake my documents as openOffice docs or is there an office app that works with Windows formatted files? Does open office have similar functionality that allows you to link to spreadsheet data from a word processing app? 

I'm assuming my I'll be able to install it on my acer laptop and use my Canon printer. 

Should I do a dual boot setup to keep my windows?(dont see why as I think I will throw this out and go Mac if I can't do Ubuntu)

Just need a little advice/direction/opinion on this.

I have no idea. Like an alien just arrived to earth and wants to pick up his first car. Does it really matter? I'm not doing anything specific with my computer other then office stuff and general internet use and some video playing. Thanks!

---

### Post by ian-weisser on 2016-11-18
Since we cannot see what you are looking at, it's hard for us to know what you are seeing, or why you might be confused.

Can you help us with a bit more information?
When I look for 'Ubuntu Desktop Download' I get two choices, and the recommendation is obvious. Where are you seeing nine?

---

### Post by wildmanne39 on 2016-11-18
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by ian-weisser on 2016-11-18
Since LibreOffice is cross-platform and installs just fine on your current Windows system, why not simply test it and see for yourself?

Neither Ubuntu nor OSX are drop-in Windows replacements. Each has strengths and weaknesses that your Windows experience has not prepared you for.

---

### Post by juntjoo2 on 2016-11-18
> **ian-weisser said:**
> Since we cannot see what you are looking at, it's hard for us to know what you are seeing, or why you might be confused.

Can you help us with a bit more information?
When I look for 'Ubuntu Desktop Download' I get two choices, and the recommendation is obvious. Where are you seeing nine?

Up above when you click "Ubuntu community". Each one has a different letter in front of it thanks.

---

### Post by Frogs Hair on 2016-11-18
Ubuntu comes with Libre Office which is a fork of Open Office and a Windows version is available . You could test the suite before changing operating systems. Text documents shouldn't be a problem because you can save in .docx, though I have little experience with excel documents.

[https://www.libreoffice.org/download/](https://www.libreoffice.org/download/)

---

### Post by juntjoo2 on 2016-11-18
> **ian-weisser said:**
> Since LibreOffice is cross-platform and installs just fine on your current Windows system, why not simply test it and see for yourself?

Neither Ubuntu nor OSX are drop-in Windows replacements. Each has strengths and weaknesses that your Windows experience has not prepared you for.

Okay, gotcha. What about synching between pc and Android phone? Is there a reliable method, or at least one not known to lie to you about synching status like windows 10 oneDrive? If use Google drive but it appears to suffer similar issues through their windows app so I'm figure it's a Windows issue. 

Maybe I should have asked originally about how Ubuntu operates compared to Windows. Aside from important functions not working like synching, windows just forces stuff on you like antimalware and updates that screw things up. Even if this is somehow avoidable(often times proven not to be avoidable) windows has a way of sneaking all kinds of unwanted surprises too difficult to resolve AND it seems to hog my old PC's limited resources to almost death. My current phone has similar specs and blows my pc away. 

So I just want to be able to synch my important files more reliably and possibly have a smoother running system that relies more on the user's needs than its own nefarious background motives :p. Thanks

> **Frogs Hair said:**
> Ubuntu comes with Libre Office which is a fork of Open Office and a Windows version is available . You could test the suite before changing operating systems. Text documents shouldn't be a problem because you can save in .docx, though I have little experience with excel documents.

[https://www.libreoffice.org/download/](https://www.libreoffice.org/download/)

Thank you

---

### Post by ian-weisser on 2016-11-18
> **juntjoo2 said:**
> Up above when you click "Ubuntu community". Each one has a different letter in front of it thanks.

Each of those is a different Desktop Environment. You own preference governs. They are all similar beneath the different graphics.
If you lack a preference, go with the default Ubuntu for desktops (not server).
It's free. Download and try it. See if it meets your needs.

Ubuntu is NOT Windows. There's a lot for you to un-learn. Even something as simple as installing applications can be very different.
Also, Ubuntu is open, which gives you great power...including the power to break your system terribly. Windows power-users sometimes do that as they learn.
Finally, Ubuntu is not a vendor and you are not a customer. We're not here to sell you on Ubuntu. If you decide to participate in our project, you will be welcome.

---

### Post by juntjoo2 on 2016-11-18
thanks, is there a guide for a dual boot setup somewhere?  also, what about a backup install cd?  I've a cd drive I could do that with.  is that an option with the download? is that recommended?  I'll assume yes and yes and download and see what comes up.  I only saw something on installing from a dvd.


actually, it just finished and is an disc image file.  do I just find some software to burn this to disc or is there a guide in here?  thanks

never mind! found it

...

well it's still not straight forward or I just am not understand really what I'm reading. I'll keep digging but in the meantime, is there a dual boot set of instructions or is an option as part of the installation files?  cos if that's the case maybe I can just do that from my current windows desktop right? and maybe I can run the disc image through one of those virtual drive apps?  i'm in these installation pages and they seem to be instructions on more instructions or something lol. but nothing is actually walking me through any action. it's like attempting to have a discussion with me about things I don't know.  tell me what I need to know to follow these install instructions to get somewhere.  thanks

---

### Post by oldfred on 2016-11-18
First is this an older BIOS/MBR system? OR a newer UEFI/gpt system?
What version of Windows.

Most Windows 7 systems (and upgrades to Windows 10) are MBR and use all 4 primary MBR partitions which complicates it a bit.
UEFI Windows systems have fast start up which must be off and with UEFI you have 3 ways to boot and install. UEFI with Secure boot, standard UEFI and BIOS/CSM.

Best if you understand partitioning, not the Windows convention of calling both partitions & physical drives as drives.

       [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick
[/URL]
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 
      
 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 

 If a UEFI system see the too much info in the link in my signature, below.

---

### Post by juntjoo2 on 2016-11-18
Gee whiz!

I just got the install button and crossed my fingers. I figure the worst that could happen is ill run out of space and I don't already use much...

Oh sweet, it is holding my hand along the way. I did this once a long while back and remember it was learning a new sport or game all over again. Here's to good times ahead!

Thank you. I will check those links as troubles arise...

You guys need ways to upvote/thank people like other forums.

---

### Post by QIII on 2016-11-18
Hello!

You can just thank people in your posts.  You can mark your threads solved to help others find solutions.

We don't go much for upvote popularity contests here.  We just want to help people.

:)

---

### Post by juntjoo2 on 2016-11-18
Hey somehow my installation is in French! I was in the middle of installing before something happened mid way then I had to cook dinner now I come back to find it installed in French!  I'm in settings but only know some Spanish. Help?

Okay, I am just about to try installing again over the French but my last attempt it failed and suggested I clean my disk drive but it's new and the DVD I used is new so I shall double cross my fingers this time...

Anyone know how to get it to pop up along side windows as an option? Last time I booted it it just went automatically to Windows. Maybe that means that the french installation never completed?

---

