---
title: "Ubuntu V Windows"
date: 2013-01-20
forum: Recurring Discussions
---

### Post by SteveTyrer on 2013-01-20
I have been using Ubuntu for about 2 years now and it has become my preferred operating system running on one server (music and films 6Tb) and two laptops.
I still use Windows on my media centre computer that drives my home theatre as I like WMC and My Movies also I rip DVD using Any DVD which will only run on Windows.

What I cannot understand is with Windows operating systems you have to de-frag the hard drive to keep it running smoothly but Linux all you need to do is delete the old Kernels after upgrades; so Linux is much easer to maintain can anyone explain to my why you don’t need to de-frag Linux?
:p

---

### Post by MG&amp;TL on 2013-01-20
> **SteveTyrer said:**
> 
What I cannot understand is with Windows operating systems you have to de-frag the hard drive to keep it running smoothly but Linux all you need to do is delete the old Kernels after upgrades; so Linux is much easer to maintain can anyone explain to my why you don’t need to de-frag Linux?
:p

You don't need to remove old kernels after upgrades, only if you're really that short of a few MB and/or are obsessive about clean boot menus. ;)

Well, the reason you need to defragment disks is due to the filesystem getting clogged up with 'bits' of files. Filesystems are what determines where and how files are stored on disk. Technically linux filesystems still need defragmenting, but it only becomes a problem on most filesystems if your disk is very full (more than 90%, I believe). See [http://en.wikipedia.org/wiki/File_system_fragmentation](http://en.wikipedia.org/wiki/File_system_fragmentation)

IMHO the various linux filesystems are better designed than NTFS (the default windows filesystem), which leads to less maintenance required.

---

### Post by forrestcupp on 2013-01-20
The simple explanation is this. Windows tries to place all of your files toward the front of the hard drive, so when you delete files, and save other files, they become fragmented because the files' sizes don't necessarily match the freed up slot available. Linux file systems spread files out more over the hard drive, so it's not as often that files need to be fragmented, unless the hard drive is full, like MG&TL said.

---

### Post by rrnbtter on 2013-01-20
Greetings,
My contention with Windows has always been its hughmongous swap file that it will use even with a terabyte of ram installed.  Then turn on file indexing/fast search and you will have a real dog.  Then give it a tmp dir with a gig or so of ancient garbage and the whole system begins to bog. All of this was not a problem for me. I was never unhappy with Windows but I made a good income off of my customers and still do for  a residual few.  Now that I have no corporate software needs Ubuntu 13.04 and the 3.8RC4 kernel is a pure delight.  I can't wait until the Beta in April.

---

### Post by grahammechanical on 2013-01-20
This is old but it does give something of an explanation.

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

And if you want a laugh, just look at the argument that it started in the comments section. This put a smile on my face:

> And finally Windows Vista should have _defrag scheduled_ so fragmentation will finally be a problem of the past.

So, scheduling automatic defrag solves the fragmentation problem, does it? The fragmentation is still happening.

Regards.

---

### Post by SteveTyrer on 2013-01-20
Thanks everyone for your explanations on fragmentation, which continue to prove to me Linux's superiority over the Windows operating system :KS

---

### Post by sffvba[e0rt on 2013-01-20
*Thread moved to **Recurring Discussions**.*


404

---

### Post by rrnbtter on 2013-01-20
Greetings,
For a nice little performance enhancement I put my root and user partitions on EXT2 partitions since they don't benefit from journaling and file overhead is speedier. I put home on an EXT4 file system for security.  I also use a 500Meg EXT2 boot partition.   All of this makes encryption and protection of home easier and allows for a fast reinstall if needed. Just some of my own experience if you are interested.

---

### Post by mike acker on 2013-01-20
I think this article <a href="http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/" target="_blank"> Windows v Linux Security Question</a> is good reading -- for all of us

it really helps to understand why the win/os get hit all the time

at the end when i was running win7 i had added a program called "WinPatrol" . as I was running Windows ... my "Scotty" kept barking and barking -- as my system got hit with one update after another . this was a huge factor in me pulling the plug on windows and i find Linux suits me ok.  just 'ok' : it needs polish here and there .

i think our biggest concern in Linux is that java script could alter the working of our browser . we should all be running Firefox within apparmor for this reason b ut i wish we had a tutorial on the Canonical supplied apparmor profile

---

### Post by MadmanRB on 2013-01-20
For a decent linux alternative to windows media center try XBMC, I personally like it better then media center.
As for DVD ripping, well there are plenty of DVD rippers out there, since DVD ripping is considered piracy I wont name software but it exists and most DVD ripping tools are comparable to the ones found on windows.

---

### Post by sunfromhere on 2013-01-20
Usually I'm for the - if it does the job, I don't care which OS it is. However, my recent two annoyances with Windows:

1. why for the love of everything do I need administrator permissions to start a simple user application, for example a book keeping program? Why do user applications even get those options? I try to maintain 2 office computers, but it's insane that every simple user application requires admin permissions.... :confused: Why can they be made that way? So theoretically I can put a password that protects the computer, but practically I need to hand out this password because she'll be unable to run the necessary programs.

2. Windows are a very untidy OS. F.e. Vista. Did you see that little hidden folder, in MyDocuments, named AppData? It had more than 20GB of files in it, saving parts of each and every single program that was installed since the first boot of the computer. And yes, I did run various cleaning programs regularly.

---

### Post by SteveTyrer on 2013-01-21
> **MadmanRB said:**
> For a decent linux alternative to windows media center try XBMC, I personally like it better then media center.
As for DVD ripping, well there are plenty of DVD rippers out there, since DVD ripping is considered piracy I wont name software but it exists and most DVD ripping tools are comparable to the ones found on windows.

I have tried XBMC but found it was no very good handling classical music which I have a large Db of, as to the ripping of DVD I have close to 500 on the server and have purchased them all and  have the hard copy of each one to show. So technically you could say they are pirated but as I have paid for all the material I think is a mute point :P

---

### Post by forrestcupp on 2013-01-21
> **mike acker said:**
> I think this article <a href="http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/" target="_blank"> Windows v Linux Security Question</a> is good reading -- for all of us
Hey, just so you'll know, the forum uses shortcode instead of html code. So you do a link like this:

(url=http...)text(/url) 

only replace the ( ) with [ ]

---

