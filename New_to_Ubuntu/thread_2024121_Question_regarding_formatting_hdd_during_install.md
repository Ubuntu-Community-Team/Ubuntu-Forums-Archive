---
title: "Question regarding formatting hdd during install"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by JonofPDX on 2012-07-13
Hi all—

So, my question is an incredibly simple one as I have never used linux before and am not all that computer savvy (ie: I get around fine and I know how to get into my bios but I have never built a computer or installed a new os except for Windows). Basically, I am just hoping that someone here can tell me if installing ubuntu can fix my problem. 

I have a 3 year old windows pc that failed last night. After poking around in the bios, trying to boot from a recovery cd and running a system diagnostic it appears that the hdd has just failed. This is a pain as it is out of warranty and HP wants to charge me $150.00 to replace the hdd and os.

I do, however, have access to a hdd out of a computer at my work. They are happy to let me have it but it will need to be formatted and a new os will need to be installed. As I do not have a fresh copy of windows I was considering ubuntu as a work-around. 

So—my question is this: if I just install the new hdd into the computer and turn it on w/ an ubuntu cd in the drive (boot priority is set to the cd drive) will it allow me to format the hdd and install a fresh copy of the os the way a windows cd would?

I would appreciate any help anyone could give me on this. I really don’t have the money to spend $150 right now and am hoping this may be my answer. Also, please forgive me if I have missed a similar post. I looked back a few pages but the search tool was giving me a hard time on my phone. 

Thank you for your help--Jon

---

### Post by MG&amp;TL on 2012-07-13
As far as I know, the Ubuntu installer can format whole disks. It has worked for me in the past.

Yeah, this forum isn't very small-screen friendly. :)

Try it, see if you like it, poke around for a few days. If you have  problems, feel free to post here. :)

---

### Post by GreatDanton on 2012-07-13
Depends. If nothing is wrong with HDD (it's not damaged), and you are able to connect it to the other computer, then you will be able to do it. However I don't understand why you don't burn cd with Ubuntu on it, and install it on 1. computer (in your case computer with bad hdd). Ubuntu is able to format HDD and you don't have to pull HDD out of the computer, just to format it.

EDIT: I misunderstood you. Yes if you install new HDD in computer, then there won't be any problems.

---

### Post by SirWhy on 2012-07-13
Ubuntu is capable of formatting HDDs and creating partitions during install

---

### Post by JonofPDX on 2012-07-13
Wow--quick response. 

Thanks for the help guys--it really is much appreciated. I will give it a shot tonight. 

Jon

---

### Post by ajgreeny on 2012-07-13
It is very worthwhile using manual partitioning when you install and adding a separate /home partition.

All the instructions are at [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") but these are for an older ubuntu version, so where these instructions say you should choose "**Specify partitions manually (advanced)" **you will need to choose "Something Else"  You can then delete all the current partitions on this new disk and then follow on, making new partitions, one for root /, one for swap, and the rest for /home.

All will become clear as you do it, and by following the instructions in that post you should be up an running in about 30 minutes or less.

---

