---
title: "A few questions from a newbie..."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by burnoutbob on 2008-05-02
Hey guys. I'm all new and stuff, so please be nice :)

I apologize if any of these questions have been answered before, I did search first, but I didn't find anything that answered my specific questions. Though again, I do apologize if I've missed it.

Right, I've spent the last few months (in between 6 reformats, I'll have you know!) researching alternative OS's to Windows and decided that Linux is by far the best I can find. 

And following more digging, I've decided on Ubuntu (A friend recommended Fedora, but it looked a little too involved for someone who needs to use his computer straight off, rather than learning how to do everything first). 

Which brings me to my questions:-

Firstly, I've seen the minimum specification for Ubuntu, but seeing as how XP has a relatively low min spec, and yet runs like a turtle pulling France up a big hill, am I going to have the same problem with Ubuntu? My computer exceeds the minimum spec by quite a bit, but I'm running quite an old CPU (Athlon XP 2800+ I think), so I just wanted to check.

Next, how easy is it to install? I know there are literally hundreds of tutorials and "how-to's" on installing Linux distributions, but I don't want a detailed step by step guide, I just want to know if it's going to take me all day, or if it's relatively straightforward? 

Also, I although I've never used Linux before, I do have some experience with operating systems that make good use of the CLI (I was an avid *Amiga* user until like, 1998, when I finally decided I HAD to move on, and when I was in school, all we had was about a million Acorn Computers, so naturally, most of what I did was via the CLI), so my next question is, just how much will I have to use the CLI in my general daily compu-poking?

Another thing is, if I plan on installing as my only OS, not dual boot or anything, will I need to partition my master drive at all? I've read things about swap drives and such but I never really understood what it was all about. It's only 40Gb, and I don't store anything useful on there. I have two 200Gb drives for my files and music, so all i use that one for currently is XP and software.

Thanks for reading through my particularly pathetic questions and the drivel I've mixed it with  (:)) and any help you can offer with this would be much appreciated. I'm desperate to get away from MS software and it's oh so many bugs and Ram eating habits.

Cheers

Bob.

---

### Post by TeoBigusGeekus on 2008-05-02
1) If window$ goes ok on your system, Ubuntu will just FLYYYY...:lolflag:


2) It took me about an hour-hour and a half to install hardy heron.

3) At first everything will look like chinese to you, but in a few weeks you will be surprised with yourself. For everyday actions you can do everything from gui.

4) You will need 3 partitions. In the Ubuntu installer you choose manual and then create:
(a) A partition for root. This is where your filesystem will be stored.
Choose ext3 format and / as mount point.
Suggested size 18gb.
(b) A partition for your home folder. This is where the users store their data. Although it is not necessary to have a separate home folder, it is highly recommended.
Ext3 format and /home as mount point.
Suggested size 20gb
(c) A swap partition. It is a pseudo-ram on your hd that is being used whenever your system resources start to complain. I don't know what type of apps you are going to use (i.e. resource hungry or not) 
but a size of 2gb is on the safe side.

---

### Post by Diabolis on 2008-05-02
> **burnoutbob said:**
> 
Next, how easy is it to install? I know there are literally hundreds of tutorials and "how-to's" on installing Linux distributions, but I don't want a detailed step by step guide, I just want to know if it's going to take me all day, or if it's relatively straightforward? 


Installation should go pretty straightforward. My recommendation is to make 3 partitions. The first one for system files, the second one for your home folder and the third one for swap.

While partitioning set their mount points like this:
first partition:  /
second partition: /home

you don't need to set a mount point for swap, it will be picked up automatically.

Swap is used to cache files, so they can be opened faster if you have opened them before. RAM memory is used for this too and is faster, since I have a good amount of RAM, the swap is barely used. I have 1.256gb of RAM.

You can install ubuntu without a swap partition. But it won't harm if you set it with a 256mb partition, thats what I use. It all depends on what you are going to do with the machine For the average user that is enough, but some tasks require you to have a big swap. For instance, making your own live-cd or a customized live-cd requires the access to hundreds of files, so it is recommended to have a 1gb swap.

> **TeoBigusGeekus said:**
> 1) If window$ goes ok on your system, Ubuntu will just FLYYYY...:lolflag:

(c) A swap partition. It is a pseudo-ram on your hd that is being used whenever your system resources start to complain. I don't know what type of apps you are going to use (i.e. resource hungry or not) 
but a size of 2gb is on the safe side.

True if windows ran in your machine, ubuntu will fit perfectly.

A 2gb is way too much, you don't need it. And if you are not comfortable with your partitions after installing Ubuntu, you can always resize them with gparted.

---

### Post by forrestcupp on 2008-05-02
Ubuntu should run at least as good as XP, maybe better.  You won't have slowdowns from spyware, etc.

I have installed XP, Vista and Ubuntu numerous times, and in my opinion, Ubuntu is the easiest and quickest to install.

You do not need to use the CLI in your day to day computing.  The CLI is mainly used for tweaking, and it's getting to the point to where there are GUI options even for most of your tweaking.  It's possible to hardly ever touch the CLI if you know how to get around the GUI.  But you will find that a lot of the support in these forums refer to the CLI instead of the GUI options because it's easy to copy and paste commands.

You don't really need to even worry about partitions.  It is part of the installation process, and there is even an option to let Ubuntu's installer do it for you automatically with the guided partitioning.

---

### Post by burnoutbob on 2008-05-02
Thanks a lot for the quick replies :)

That's cleared up a lot for me and has made up my mind! Esp on the swap file. That was confusing me. I'm gathering it's just like the paging file then in windows? I have 2Gb ram, and the most resource hungry program I'm going to be using is a word processor (!!!), so going by what you've said, I shouldn't need too big a swap file. 

That decides it then...

Tomorrow, it begins!!

Thanks again friends! :):)

---

### Post by linuxlizard on 2008-05-02
Hey, my main box is an amd 2800+ and it runs hardy very fast. Firfox opens in about 2 seconds. you have plenty of power there.

---

### Post by redbob on 2008-05-02
Talking about your box configuration, I think it's pretty. I've got three computers at my home. The "lazier" of them is a Sempron 3100+, so it's just a bit faster than yours. After I changed my machines to Ubuntu, never worried about upgrade anymore. But if something you could invest on it is RAM. 1Gb for your machine is pretty enough.

---

### Post by halitech on 2008-05-02
Welcome to the board and I'm sure you will find yourself very happy and very surprised with Ubuntu :)

I have a P4 1.8 with 896meg ram and I find most of the time (unless I'm using ManDVD) that the system flies along pretty well so your system should scream pretty well all the time and if you ever decide to get rid of that "old" cpu, feel free to toss it my way ;)

far as the install, like the others have said, anywhere from 60-90 minutes, depending on your ram and the speed of your cd rom. I would also recommend, like the others to do the 3 partitions for easier upgrades in the future. 

far as the CLI, I hardly use it anymore on a daily basis but I will open it now and then if I know a particular program I want to install and do a 
```
sudo apt-get install program-name-here
```
just because it is easier and faster then opening Synaptic or for some other task that I know I can do faster in the CLI but that is not very often.

Once you get Ubuntu installed, you will need to mount the 200gig drives but that should be easy enough afterwards so as a precaution, might want to disconnect them before doing the install so you don't hit the wrong drive for the install (been there done that :8 )

again, welcome to the board and if you have any problems, let us know :)

---

### Post by Ptero-4 on 2008-05-04
I currently have a Celeron lappy which is quite snappy all the time. I can tell you that your box is gonna FLY with linux.

---

### Post by the8thstar on 2008-05-04
> **burnoutbob said:**
> Thanks a lot for the quick replies :)

That's cleared up a lot for me and has made up my mind! Esp on the swap file. That was confusing me. I'm gathering it's just like the paging file then in windows? I have 2Gb ram, and the most resource hungry program I'm going to be using is a word processor (!!!), so going by what you've said, I shouldn't need too big a swap file. 

That decides it then...

Tomorrow, it begins!!

Thanks again friends! :):)

Yes, the swap acts like pagefile.sys on Windows. It also acts as hiberfile.sys too, which means that the swap partition is also used to suspend and hibernate your computer if you so choose.

Alternatively, you could choose to install the swapfile inside / or /home. But at this point in time, it's better to just do it that way for now. You're too young (in Ubuntu terms) to understand everything yet. :)

For the record, swap should be between equal to RAM x 1.5 or RAM x 2 (better)

---

### Post by burnoutbob on 2008-05-05
Well, I finally did it. And after much messing around trying to install drivers and such for my gfx card it's all working nicely now.

Thanks for answering my questions guys :) 

I don't think I'll be going back to Windoze :))

---

