---
title: "First time using Ubuntu, and this forum"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Line_Circle_Square on 2011-09-13
This is my first time using Ubuntu, and this forum. I am not a complete stranger to computers in general, but I never went beyond what came out of the box. I'm looking to go beyond that, as I just recently built a machine to only run Linux distros. I currently own 2 desktops and one laptop (HP Pavilion Slimline 5560, Dell Optiplex GX520 and a Macbook Pro build 1,1). The specs of what I am using to run Ubuntu is as follows:

Dell Optiplex GX520
Pentium Celeron @ 2.4ghtz
160 gig SATA HDD
Onboard video and sound
Belkin N Wireless USB adapter
512mb RAM (soon to be 2gigs, got a great deal on ebay)

The computer itself was a great deal, $30 at a yard sale, came with a 15 gig HDD loaded with Windows XP which I swapped out with the 160 gig. I have zero issues installing Ubuntu via a pendrive, and I have been spending the last week getting used to the new feel, the file system and using the command line.

These forums are a vast flood of information, so much so, I dont know where to start except for making this introduction and hoping you folks will point this newb in the right direction. Some questions I have:

1. After installing Ubuntu 11.04, I installed all the available updates, and I don't know where to go next. Some recommended software? I already installed Chrome (its my browser of choice on my HP) but I am looking for more. I am sort of familiar with Wine, as I used it on my Mac to run PC only programs. Is this a good Windows emulator to use with Linux, or is there better?

2. I spent last night reading the Ubuntu Pocket Guide made available in the stickies of this forum. It was a great introduction, as it got me more familiar with the file system and command line. However, the Ubuntu version they were using was well behind 11.04 (I forget what version they used). Is there any newb-friendly walkthroughs that cover later versions of Ubuntu?

3. Is LibreOffice any different than OpenOffice? Is one better than the other?

4. I have a couple CD-RW drives and a DVD-ROM drive I want to install into the Dell, but I am stuck trying to find the right drivers, Ubuntu doesn't recognize the drives being there. Any suggestions?

5. Is it possible to network my HP (currently runs W7) to the Dell running Ubuntu? Can Windows and Linux "talk" to each other? It was a passing thought, I would just like to be able to access my vast amount of files (1.5 TB total storage)through Ubuntu. 


Anyway, thats all I have for now. I'll keep reading and trying to learn more. I would eventually like to get to the point where I can use Ubuntu as easily as I can Windows or Mac. Thanks for reading!

---

### Post by 2F4U on 2011-09-13
> 1. After installing Ubuntu 11.04, I installed all the available updates,  and I don't know where to go next. Some recommended software? I already  installed Chrome (its my browser of choice on my HP) but I am looking  for more. I am sort of familiar with Wine, as I used it on my Mac to run  PC only programs. Is this a good Windows emulator to use with Linux, or  is there better?

Very broad question. Could you explain what you want to achieve? Then it may be easier to recommend software.

> 2. I spent last night reading the Ubuntu Pocket Guide made available in  the stickies of this forum. It was a great introduction, as it got me  more familiar with the file system and command line. However, the Ubuntu  version they were using was well behind 11.04 (I forget what version  they used). Is there any newb-friendly walkthroughs that cover later  versions of Ubuntu?

The way the file system and command line works doesn't change much between different versions of Ubuntu.

> 
 3. Is LibreOffice any different than OpenOffice? Is one better than the other?

LIbre Office seems to be more actively developed, since after the split  from Oracle and OpenOffice, many developers switched to LibreOffice. And  almost all distros I know switched to LibreOffice.

> 5. Is it possible to network my HP (currently runs W7) to the Dell  running Ubuntu? Can Windows and Linux "talk" to each other? It was a  passing thought, I would just like to be able to access my vast amount  of files (1.5 TB total storage)through Ubuntu. 

You might want to look into Samba. It is the default software when it comes to getting Windows and Linux to work together.

---

### Post by sanderd17 on 2011-09-13
For the DVD drives: you don't need aditional drivers (if they are ide drives).

Just check that they get power, that the ide buses are connected and that the jumpers are set correctly.

Also, you won't find a trace of a CD drive until you put some CD in it.

---

### Post by blackbird34 on 2011-09-13
THunderbird, openshot, clementine, vlc, gimp... who knows?

There is Crossover which you can try out for free to replace wine, it's proprietary, might be a bit further ahead.

---

### Post by roodypoo on 2011-09-13
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by MG&amp;TL on 2011-09-13
A lot of stuff will require terminal. Learn the basics first...Linuxcommand.org.

---

### Post by Line_Circle_Square on 2011-09-13
> **2F4U said:**
> Very broad question. Could you explain what you want to achieve? Then it may be easier to recommend software.


I probably should have elaborated, but I am looking to do basic tasks,  web surfing, word processing... maybe even some games until I know my  way around a little better.

---

### Post by VtecHonda on 2011-09-13
Hey [Line_Circle_Square]("http://ubuntuforums.org/member.php?u=1437790").. 

i am new to Ubuntu as well. (although not new to computers, im a tech but have mainly worked on windows O.S.'s....) 

Its good to know im not the only new guy..haha

---

### Post by sarwiz on 2011-09-14
ANother Newb here, even thought I have been a member since 08, but you have to stay with it to keep learning more. I tend to get lazy and migrate back to windows, but not am back here again. I love the look of Ububntu 11.04 now. Samba works, just be patient with it and come back here if you have any problems. I would recommend Inkscape, a great artist program, and get some games for sure.
 User 25479

---

### Post by dfarrell07 on 2011-09-14
Some of the first things I install on a new Ubuntu boot:
- Deluge BitTorrent client
- Chromium 
- 7zip (gives you some more options as far as file compression, encryption)
- unrar (non-free licensed, but free to you, software that works well with .rar archives)
- FreeCiv (game I like)
- Skype
- VLC

More advanced ones, with narrower usage domains:
- A bunch of IDEs (integrated development environments for programming)
    --- Eclipse for Java and maybe C
    --- NetBeans for C or C++
    --- Texmaker for LaTeX (HTML for PDF files)
- VirtualBox for installing Virtual Machines (I do this to try out and play with other OSs. I have like 15+ installed in VMs)

---

