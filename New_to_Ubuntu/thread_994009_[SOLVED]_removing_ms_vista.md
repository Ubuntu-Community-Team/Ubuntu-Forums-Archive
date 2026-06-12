---
title: "[SOLVED] removing ms vista"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by capnthommo on 2008-11-26
Hi, i just simply want to know can someone tell me how i actually go about removing vista from my computer.  I have looked at other threads but they dont seem to address quite what i want, which is along the lines of 'go to control panel and hilite and press delete'.  know what i mean?  Sort of instructions for dummies.  Sorry to be such a pain but i am trying to get over 50 years of working with hands not brain and its tough going.  I installed ubuntu on a dual install at first (tho i dont remember actually partitioning my disk - it has the drive split into two, C: and E: thats all i know).  It all seemed to go very straightforwardly which was fortunate as i am a bit too used to windows style functions. Any of the few functions like sat nav and itunes that i might need to access can be done on my desktop pc.  Anyway, im sorry to go on at such length but i just need real simple instruction on how to remove as much of the windows based stuff as i can.  i have other questions but they can wait, another day will do, or i shall work them out
thanks for any help

---

### Post by billgoldberg on 2008-11-26
> **capnthommo said:**
> Hi, i just simply want to know can someone tell me how i actually go about removing vista from my computer.  I have looked at other threads but they dont seem to address quite what i want, which is along the lines of 'go to control panel and hilite and press delete'.  know what i mean?  Sort of instructions for dummies.  Sorry to be such a pain but i am trying to get over 50 years of working with hands not brain and its tough going.  I installed ubuntu on a dual install at first (tho i dont remember actually partitioning my disk - it has the drive split into two, C: and E: thats all i know).  It all seemed to go very straightforwardly which was fortunate as i am a bit too used to windows style functions. Any of the few functions like sat nav and itunes that i might need to access can be done on my desktop pc.  Anyway, im sorry to go on at such length but i just need real simple instruction on how to remove as much of the windows based stuff as i can.  i have other questions but they can wait, another day will do, or i shall work them out
thanks for any help

I'll start by saying that, in Ubuntu, there is no C or D drive.

That is Windows terminology.

To remove Vista, you could just format it's partition. It will then be erased.

You could then either just let it be (and put files on it or something) or merge the partition together with the Ubuntu partition.

I would just leave it.

--

Install gparted in Ubuntu.

Using gparted, you can right click the Vista partition *(look at the file system, it will be ntfs or fat32)* and format it to "ext3".

Press apply.

Done.

[I](I don't think grub will give you any problems, however it will most likely still say "Windows Vista" when you boot up your pc. 

You can remove the Windows Vista mention in the grub (boot loader) using BUM (boot up manager, not installed by default), or so I think.)[/I]

Note: any data on the Vista partition will be deleted, including all documents and media files.

Make sure you format the right partition, for obvious reasons.

---

### Post by laurielegit on 2008-11-26
I suggest that, unless you have a hard drive under 100gb large, that you do not delete vista. For all that Ubuntu is great, there are certain areas were Windows remains the only reasonable choice, such as video editing. Also, you probably paid quite a lot of money for your vista, and you do *not* want to have to pay that again if you decide that Ubuntu is not for you.

Good luck,

Laurie

---

### Post by billgoldberg on 2008-11-26
> **laurielegit said:**
> I suggest that, unless you have a hard drive under 100gb large, that you do not delete vista. For all that Ubuntu is great, there are certain areas were Windows remains the only reasonable choice, such as video editing. Also, you probably paid quite a lot of money for your vista, and you do *not* want to have to pay that again if you decide that Ubuntu is not for you.

Good luck,

Laurie

It might come to a suprise for you, but 99% of the people don't edit videos.

And Ubuntu can do that just fine.

Sure, not for pro's, but I don't think avarage users pay thousands of dollars for a pro video editing solution.

---

### Post by Skripka on 2008-11-26
> **laurielegit said:**
> I suggest that, unless you have a hard drive under 100gb large, that you do not delete vista. For all that Ubuntu is great, there are certain areas were Windows remains the only reasonable choice, such as video editing. Also, you probably paid quite a lot of money for your vista, and you do *not* want to have to pay that again if you decide that Ubuntu is not for you.

Good luck,

Laurie

+1

There are times when one finds themselves wanting a real Winderz install--as Wine is not perfect enough sometimes, and VMs don't run well enough.  I keep a 2nd drive for an XP-SP3 install that I use for my professional software, as well as gaming, apart from that it gets little use.

Storage space is one of the cheapest upgrades today anyway.

---

### Post by clive littlewood on 2008-11-26
Hi

If you have backed up all your Ubuntu data (you have havent you !!! )

The simplest way is to just re install Ubuntu with the Live CD and when it gets to the partitioning stage use the automatic complete drive option.

Then add your data.

Regards

Clive         :)

---

### Post by ElderDrake on 2008-11-26
If you are wanting to install Ubuntu and completely get rid of Vista, when you do the partitioning use the option *Guided: Use entire disk* during install.

Here are some instructions:
[http://www.drakefire.com/?p=31](http://www.drakefire.com/?p=31)

---

### Post by capnthommo on 2008-11-26
ok thanks to both of you.  i dont feel any great compelling need to see the back of windows; i have used it for years now and its only that i have gotten fed up with slowing down and insecurity and so on allied with the fact that i liked this system from the first time i tried it.  i just need tolern how to cooperate wih the software instead of simply being an end user; i think thats what happens with windows type systems, you are only a consumer ot a partner.  if it really wont hurt i may keep it but i hear there are issues around firewalls and so forth - that windows doesnt like sharing its toys. also i paid probably an equal amount of money for the drive space as for the software and i dont really like the idea that it is occupied by a big lump that i dont use (in the time since i installed ubuntu i have only logged onto windows 2 or 3 times and then only for tasks related to moving to ubuntu).
anyway, 1. thanks for the advice on how to,  and 2. i wont dump it till i am sure - thats one of the benefits with growing older and slower, you have hopefully learned from prior mistakes.
cheers
nigel
p.s. to all the respondents who i have just noticed whilst i was typing this reply, thanks to yo all as well.  quite correct, i dont game and i dont edit video.  mostly i use it for email, browsing, open office word, spreadsheets and music and listening to ragio.  really under used i guess, but different strokes hey?

---

### Post by laurielegit on 2008-11-26
> **billgoldberg said:**
> It might come to a suprise for you, but 99% of the people don't edit videos.

And Ubuntu can do that just fine.

Sure, not for pro's, but I don't think avarage users pay thousands of dollars for a pro video editing solution.

Hate to tell you but around 40% of people I know participate in some kind of video making/editing. As I go to your bog standered modern comprehensive, I know a wide variety of people. The pro video editing software they use costs £80. So I think it may come as a surprise to you, but more than 1% of people will edit videos in the future. As for a linux alternative, there are some video editing suites, but *none* that I, or anyone else I know, would ever use.

---

### Post by peakshysteria on 2008-11-26
> **laurielegit said:**
> Hate to tell you but around 40% of people I know participate in some kind of video making/editing. As I go to your bog standered modern comprehensive, I know a wide variety of people. The pro video editing software they use costs £80. So I think it may come as a surprise to you, but more than 1% of people will edit videos in the future. As for a linux alternative, there are some video editing suites, but *none* that I, or anyone else I know, would ever use.

The question is **asked and answered**. Making remarks like yours about video editing is besides the point I not constructive at all (besides that I myself lecture in film studies and sometimes Media science, all my machines are running Ubuntu. All film I show the students are prepared on my machines without problems. Those working professional mainly use, or prefer MAC before Windows). No matter what you think about Windows and it's usefulness, the thread owner has stated his problem/question.

Solution:

> **ElderDrake said:**
> If you are wanting to install Ubuntu and completely get rid of Vista, when you do the partitioning use the option *Guided: Use entire disk* during install.

Here are some instructions:
[http://www.drakefire.com/?p=31](http://www.drakefire.com/?p=31)

---

