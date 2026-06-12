---
title: "Old hardware ((1) Celeron (2) AMD Athlon) ok for Ubuntu 12.04 ?  If not, then what?"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by Rich53201 on 2013-03-04
Thanks for this forum & the participation.  

I am having trouble with speed in wubi ubuntu 12.04 LTS installations; have learned ('trying to un-lag Ubuntu' [http://ubuntuforums.org/showthread.php?t=2116780&highlight=wubi](http://ubuntuforums.org/showthread.php?t=2116780&highlight=wubi) ) that it's best not to go with wubi except for short term trials. Will give up on wubi.  

Background: I have my own Win XP computer and also take care of Mom's. They're working mostly OK but as XP is near end of life and insecure, it's time to move on. I'm frugal and want to avoid buying new hardware if possible; these computers do everything we need them to at this time; the only issue is XP.  I have little computer experience except it's been helpful recalling bits from a Unix/C one-semester course I had about three decades ago. Maybe I should buy some books; thinking a beginner's guide and an advanced user's manual.  

Questions:   

(1) Do you think the below two hardwares are OK for a full Ubuntu 12.04 LTS install (from a 700 Mb CD)? Or should I seek an alternate version like Lubuntu or ..? Our most demanding uses might be web surfing including videos. Other than that, it's word processing, email, and the like. The wubi installations froze for minutes at a time esp. with flash (youtube).  XP performance is just okay.

(2) Should I get different HDDs to plug in so as not to risk ruining Windows XP by trying to partition the current HDDs? Very worried about upsetting our current user computers.  

(3) Any highly recommended books for Ubuntu noobs &/or intermediate users? I learned where all the special characters on the keyboard were during a course or two many years ago, remember commands like 'cat' and 'ls -l', but that's about where my expertise ends.  

Mom's hardware 
Computer: emachines T3882 
Processor: Celeron D 2.8 GHz 
RAM: 2 Gb (I added up to the max possible some time ago) 
HDD: 77 Gb, about 1/2 free 
Graphics: Intel 82865G, BIOS version 3363, I think this has no dedicated memory. 
emachines page with more spec for this product: [http://support.gateway.com/us/en/emac/product/default.aspx?tab=1&modelId=1590](http://support.gateway.com/us/en/emac/product/default.aspx?tab=1&modelId=1590)  

My hardware 
Computer: emachines T6524 
Processor: AMD Athlon 64 3500+ 2.19 GHz 
Ram: 2 Gb (thoght I had added more, up to the max possible, but system says 2 Gb). 
HDD: ~190 Gb, about 2/3 free 
Graphics: ATI / MSI Radeon Express 200 Series, I think it says it has 128 Mb onboard video memory  

Again, thanks 

 Rich

---

### Post by mastablasta on 2013-03-04
1. 
in both cases the CPU's are well enough to handle stock Ubuntu. you also have plenty of ram. the bottle neck are the graphics chips GPU. the first one is weak, the second one is a bit better but suffers from lack of AMD support. it was dropped long time ago. opensource drivers are available for this chip, but they are not so good in case of this chip. which could be the issue since Unity uses 3D a lot.

solution - get a better supported GPU card (they have some a bit more newer models really cheap) or get an older/used Graphics card that has good opensource driver support. 

ofcourse it will also be beneficial to run lighter desktop. i suggets Xubuntu. it is easilly cusomizable and you can make it look sort of like winXP really easy. Lubuntu is also good but still young. You can also give KDE a try with special effects turned off (so you don't stress the GPU unnecessary). there are a lot of other options but Flash might still stutter if the GPU doesn't have good support.

just something to think about i can run youtube video (not full screen) reasonably well on 32MB chip on a notebook with 256MB total ram and 1.2Ghz CPU. running XFCE with debian stable as base.

i also have Kubuntu (KDE) running on celeron (i think it's dual core)  with 1,3 GB ram and old ATI 9600 GPU. it runs fast and very good.

i have a very similar Athlon build and plan to put Kubutnu on it. i tested it and works fast. i have better GPU though and intend to add a bit of ram (at least 2 maybe 4...). note for windows XP to see 4 GB ram you need PAE kernel installed. also it should then report 3GB, and it actualyl works that 1 GB is then reserved for system and 3 GB are for various progs. i hope your RAM stick is OK or that you fit it propperly.


2. if you wish. using another HDD (can be external) can be safer, especially if you unplug the working one. 
but if you eventually want to install on current disk you will need (well it's in your best interest) to backup data before partitioning and also do defragmentation before partitioning. 

you can also install it in virtual box to try it out or run it live. in fact you should run it live before you do any instal. just to see if it all works well.

the cool think about linus is that it works even without any hard drive.

i recomend community made 
Ubuntu manual (see my sig)
Ubuntu official wiki help pages
and this webstie is very good resoruce  and offers some basic info and how to start in a simple way: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by prodigy_ on 2013-03-04
I'd use Xfce (e.g. Xubuntu) with those. Or LXDE (Lubuntu) if you want to squeeze every last bit of performance.

---

### Post by Rich53201 on 2013-03-04
Thanks, sounds good.  Xubuntu it is! (EDIT: Ubuntu 12.04 runs great on both machines from CD Rom, wil try that install next.)  Have learned some already even w/o consulting those sources.  Will have to write an ISO image on a CD (can do that, in fact did do that, but didn't want to risk making a partition), and will have the CD burner run at a slow speed & at the end compare md5 checksums (new to me).  Will back up critical docs, maybe to a thumb drive (don't need most of what's on these, just some of the docs.).  Already ran defrag a couple of times before trying wubi, but there was some 'unmovable' data in the middle of the drive; will this impact partitioning?

One thing I liked about the 'unity desktop' or whatever that toolbar on the left is called in Ubuntu 12.04, is that clicking a button once starts a program in a window, clicking a 2nd time brings that same window to the top, rather than starting a new instance or window.  I think this would help a lot in reducing Mom confusion.  I will want to make the Xubuntu interface do the same thing.  Also, the little carats that tell you what's running and how many windows are open were very nice.

I will want to customize to reduce the number of buttons on Mom's screen.  Want buttons for email, browser, word processing, a file manager that opens the 'my documents' directory, and maybe the print monitor.  That's all.  Liked that the Unity desktop allowed that sort of customization fairly easily, sounds like Xubuntu will be similar.

---

### Post by mastablasta on 2013-03-05
yes unmovable data can be a problme. however if you restart computer and try defrag again it might be that they would be movable the seocnd time arround. depends what file is that.

you can try Ubuntu 12.04 but use Unity 2D. I am not sure if it is easy to get same funcitons in Xubuntu. It's a completelly different desktop interface. i mena it could be done, but probably not easy.

Kubuntu with classic style menu (right click on K select classic menu) looks preety much like windows XP (control panel and all that...) ;-)

---

### Post by Rich53201 on 2013-03-06
Thank you so much mastablasta.  The manual and other links &c are very helpful.

What I've done so far -

Backed up Mom's important data files on my computer and vice-versa.  Uninstalled the Wubi versions.  Had defragged &c both machines earlier so not doing this again.  **There are 'unmovable' file(s) mid-disk but these are probably Windows temporary files.  The Ubuntu installer can handle & avoid this, right ???**

Manually checked the checksum on the previously downloaded iso, Ubuntu 12.04 LTS i386 - ok

Manually checked the previously-burned CD's files checksums - found one that didn't match.  The non-match was the very long file with 'directory structure' or some such in the name.  So, I tossed that CD.

Burned a new CD with the drive running at the slowest speed, which was 4x.  Burned using DeepBurner (free version) which I had installed a long time ago.

Meanwhile, learned that the CD has a self-checking program, just have to hold down any key when booting.  Took a few tries to get that right (the Shift key does not qualify as 'any key', apparently).  This CD checked OK.

Ran it on Mom's system without installing.  Ran great.  Don't want to take any risk of hosing Mom's system so didn't go to a full install.  Will try my computer first. ** From my reading, seems like 99% of the time, installing a Ubuntu Linux partition from the CD does not ruin the Windows boot.  Hope this is correct.  (???)**

There is a version of 12.04 LTS (and for that matter, of the (current) 12.10 release also) that's optimized for AMD 64 computers, which I have.  So, downloaded that version, burned it & checked it as above, and booted it.  As I type this, am running from the CD.  Seems great. Will try an install next.

Want to try Ubuntu 12.04 LTS rather than the ligher versions; really like the Unity Launcher.   Will look for the Unity 2D install if I have trouble attributable to the default Unity 3D.  I think it's covered in the manual - says it works exactly the same aside from 3D effects ( transparent, fade, and such).  I can do without 3D effects.

Thanks again

Rich

---

### Post by dardack on 2013-03-06
I know you said you were going with Xubuntu, but lately (the past few years) Xubuntu has had the same ram requirement as regular ubuntu.  It seems to still use gnome and auto install other standard hungry apps.

I've recently made the switch to Lubuntu and love it.  I have the original ION systems it runs on and it's been very very nice.

---

### Post by Rich53201 on 2013-03-06
Going to try regular Ubuntu, but 12.04 LTS because I want it to 'just work' & enjoy using it.  I don't have a need for the latest & best, usually.

---

