---
title: "What is the Benfit of using 64-bit OS?"
date: 2011-01-07
forum: Recurring Discussions
---

### Post by Linyx on 2011-01-07
I had Google it but find Nothing Solid Answer that Clarify me, instead After reading Article i comes to know that 64-BIT OS's can Address RAM > 4GB....


I have also seen in most Notes that 64bit Programs are Run faster about **10%** as compared to 32-bit....?But **WHY**...?

Moreover, Right now i am using 32-bit Ubuntu , If i switch to 64-bit Ubuntu, what will the **Benefit** for me.....?

---

### Post by Wtower on 2011-01-07
There are many discussions in this forum concerning this matter. Briefly, I can tell you that 32-bit Linux kernel with PAE (physical address extention) can access up to 64GB RAM although for RAM above 4GB there will be a slight CPU overhead and therefore degraded performance, negligible in my opinion.

So a 64-bit kernel can overcome the previous issue. Also, certainly a pc with 8GB RAM and a 32-bit kernel without PAE will be expected to have smaller performance apparently due to caching being smaller and dozens other factors.

On the other hand, I find some incompatibilities with 64-bit kernel and existing software to be disturbing, so my personal opinion is that I prefer 32-bit-pae over 64-bit and am willing to pay the small performance overhead. Besides, I very rarely reach the barrier of 50% RAM on my pcs with 8GB. (Not all memory consumption of course occurs in the lower 4GB RAM but this is another matter of discussion).

So the question is, do you really need this performance? If you need to run memory consuming applications that would need consistently more than 4GB RAM, then go for 64-bit.

---

### Post by mastablasta on 2011-01-07
> **Linyx said:**
>  
 
[SIZE=2]I have also seen in most Notes that 64bit Programs are Run faster about **10%** as compared to 32-bit....?But **WHY**...?[/SIZE]

 
because the use the full power of the new 64bit processors.
 
32bit porgrammes on 64bit processor on the other hand run about at teh same speed sometimes even slower.
 
if you have a 64 bit procesor you can switch to AMD64 version. or not. whatever you like.
 
i use 32 bit version because it's compatible with more programmes. and a,so there won't be much benefit in running 64 bit on my computer.

---

### Post by Trandre on 2011-01-07
From what I have heard a 32 bit processor can execute a 32character command per turn. meaning 010101011 and so on. Whereas a 64 bit can execute 64characters in one turn and thus can process more commands at the same time. 

Can somebody please verify or correct this statement?

---

### Post by migs73 on 2011-01-07
I use the 32bit PAE as I have 4GB RAM but my printer drivers are pretty useless when forced to 64bit (there are no 64bit versions).

I would advise you chack ALL your hardware will work if you go 64bit and aslo tha all the software you use will work ok.

Eventually everything will be 64bit, and we will all laugh at the time we used 32bit (remember 8 and 16bit computers!!).:p

---

### Post by Linyx on 2011-01-07
Thanks for all replies....

I have Pentium-D,945 chip-set,2.8G with 2GB-DDR2/800, Realtec HD N10/ICH-7 Audio card,82945/G Integrated Graphics.....

Now if i switch to 64-bit, Will i face **Driver's issue** or something like [[COLOR=Black][/COLOR]]("http://ubuntuforums.org/member.php?u=749318")[[COLOR=Black][/COLOR]migs73 Has described...?]("http://ubuntuforums.org/member.php?u=749318")


But one thing, I think their are more softs in 32-bit as Compared to 64 , Isn't...?i am afraid if i switch to 64 and then i am unable to find softs in 64-bit version or something similar....

Well, i know that the latest softs will also come in 64-bit ...but now if i stay with 32-bit OS, Am i at loss that i am not talking **full advantage** of my ***64-bit Processor***....?

Excuse my English....;)

---

### Post by Wtower on 2011-01-07
My personal advice, stick with 32-bit for now.

---

### Post by oldos2er on 2011-01-07
What software do you need? I haven't really found anything lacking in the repositories, with a couple exceptions, Adobe Acrobat (I use Okular now), and Adobe flash. 64-bit flash exists but is not yet in the repos (click the FlashAid link in my sig for more info).

---

### Post by Linyx on 2011-01-07
Currently i am on 32-bit Os's , I had triple boot "Linux(Gnome/KDE) & 7" and all are in 32-bit......but if i have some benefit of using 64-bit, or if i can get much **better performance** in 64-bit, i must switch to 64-bit then.......but my RAM is not too much as i have Only 2GB.....

---

### Post by psusi on 2011-01-07
32-bit programs only have access to like 5 general purpose registers to hold values they are worthing with and pass arguments between functions.  64-bit mode has 32 or something.  This means less stuff has to be pushed onto the relatively slower stack and can stay in the registers instead.

---

### Post by pbpersson on 2011-01-07
> **oldos2er said:**
>  Adobe Acrobat (I use Okular now), and Adobe flash. 64-bit flash exists but is not yet in the repos (click the FlashAid link in my sig for more info).

What happens if I install 64-bit Ubuntu and then install the Ubuntu-Restricted-Extras?  You are saying Flash does not work?

I am currently using 64-bit Mint version 8 and Flash works perfectly.  I was planning to upgrade to the 64-bit version of Ubuntu 10.04

Are you saying that some things are still broken on the LTS version?  I thought I had waited long enough for them to get the bugs out.

---

### Post by walt.smith1960 on 2011-01-07
It wasn't a major problem but when installing a Brother MFD, the Brother .deb would not install using a GUI. I had to do command line and use the --force switch in order to get it to install.  It then installed and worked properly, just an irritation.

---

### Post by Linyx on 2011-01-07
> **oldos2er said:**
> What software do you need? I haven't really found anything lacking in the repositories, with a couple exceptions, Adobe Acrobat (I use Okular now), and Adobe flash. 64-bit flash exists but is not yet in the repos (click the FlashAid link in my sig for more info).

Right now i am not using Special software that i will care for....but i want my Full-performance of the CPU....i thought that 64-bit OS' will make my performance quite better as compared to 32.....

I am talking about both i-e Linux as well as Windows.....

---

### Post by migs73 on 2011-01-07
> **walt.smith1960 said:**
> It wasn't a major problem but when installing a Brother MFD, the Brother .deb would not install using a GUI. I had to do command line and use the --force switch in order to get it to install.  It then installed and worked properly, just an irritation.

It is Brother drivers that have stopped me making the plunge, I have never tried, but I know others who have had nothing but problems with them. I think you are lucky.
I don't think it's worth the hassle, as 32bit PAE suits all my needs.

---

### Post by bodhi.zazen on 2011-01-07
*Thread moved to **Recurring Discussions**.*

It kind of gives you a warm and fuzzy feeling inside ?

Depending on what you do with your CPU you may or may not see a benefit. If you use things (printers, some wireless cards) you may have problems.

In general 64 bit works well for most people, fall back to 32 bit if you have a problem.

---

### Post by hansolo4949 on 2011-01-07
You should go for 64 bit. the only downside to 64 bit is that occaisonly a program won't work on it, and some old hardware might not have 64 bit drivers, but that's about it.


hope that helps!

hansolo4949

---

### Post by blind2314 on 2011-01-07
> **psusi said:**
> 32-bit programs only have access to like 5 general purpose registers to hold values they are worthing with and pass arguments between functions. 64-bit mode has 32 or something. This means less stuff has to be pushed onto the relatively slower stack and can stay in the registers instead.
 
This isn't always true. It is architecure specific and can be chip specific as well.

---

### Post by lykwydchykyn on 2011-01-07
> **bodhi.zazen said:**
> *Thread moved to **Recurring Discussions**.*

It kind of gives you a warm and fuzzy feeling inside ?

Depending on what you do with your CPU you may or may not see a benefit. If you use things (printers, some wireless cards) you may have problems.

In general 64 bit works well for most people, fall back to 32 bit if you have a problem.

I agree.  

I switched over to 64 bit when I got a new computer at work last summer.  If there's a performance difference, it wasn't terribly noticeable to me.

Biggest difference was that it took all my Linux-hacker mojo to get some necessary 32-bit-only programs to actually install.

---

### Post by psusi on 2011-01-07
> **blind2314 said:**
> This isn't always true. It is architecure specific and can be chip specific as well.

Well yea, but we are only talking about two specific architectures here:  i386 and amd64.  The context of the discussion is around which Ubuntu release, not the theoretical difference between an unknown 32 and 64 bit processor in the generic sense.

I looked it up and it's actually only 16 registers, not 32 on amd64.  Still, quite a bit better than the 8 on i386.

---

### Post by handy on 2011-01-07
The benefit of a 64bit system over a 32bit system running on the same 64bit machine is that just about everything is faster under 64bit:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by janpol on 2011-01-07
> **handy said:**
> The benefit of a 64bit system over a 32bit system running on the same 64bit machine is that just about everything is faster under 64bit:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

Regarding to "everything is faster under 64bits":

.Only 64 bit apps, 32 bit apps will run slower on a 64bit os

.The performance difference is unnoticeable for most apps

.Some things still have compatibility issues (I had a really nasty bug with the 64 bit version of my network card driver). This is the reason why the Ubuntu download page recommends the 32bit version for Desktops.

.Read that phoronix article again, some things are faster, not everything. Also, try installing a 64bit OS and use it for your every day tasks, you won't feel much diference (unless you use daily an app that really takes advantage of 64 bit technology :P)

OFC, I am talking about people who use 4Gb of Ram, If you have a huge amount of Ram, go for the 64bit version ;)

Regards!

---

### Post by waltervalderrama on 2011-01-07
I've never found any issue with 64 bits kernel besides adobe reader. Personally I use 64 bits kernel for testing -  virtual machines purposes.
For me everything works great, and performance is excellent.

---

### Post by johntaylor1887 on 2011-01-07
> **Wtower said:**
> 
On the other hand, I find some incompatibilities with 64-bit kernel and existing software to be disturbing

Such as? I see no difference in the packages available. I imagine there may be a few esoteric apps that won't work in 64, but the average person should not be affected by this. Even 64bit flash is pretty solid at this point. I just don't see the point in running 32bit anymore. 

If you do any kind of media transcoding, number crunching, or heavy multi-tasker, 64bit is definitely the way to go. But if you just check email and surf, it probably won't matter much.


> **janpol said:**
> Also, try installing a 64bit OS and use it for your every day tasks, **you won't feel much diference** (unless you use daily an app that really takes advantage of 64 bit technology :P)

OFC, I am talking about people who use 4Gb of Ram, If you have a huge amount of Ram, go for the 64bit version ;)

Regards!
I actually did a comparison on the same computer, and found 64bit to be a little bit "snappier". Is it a big difference? No. But I'll always take faster over slower any day. 64bit is here to stay.

---

### Post by bodhi.zazen on 2011-01-07
> **johntaylor1887 said:**
> Such as? I see no difference in the packages available. I imagine there may be a few esoteric apps that won't work in 64, but the average person should not be affected by this. Even 64bit flash is pretty solid at this point. I just don't see the point in running 32bit anymore.

See, this is why the thread was removed =)

@johntaylor1887 - I have to disagree with that. There are some hardware that does not work in 64 bit, if you do not have the hardware it will not affect you, but it may affect others.

In addition I would not claim 64 bit flash to be on par with 32 bit. First of all 64 bit is in Beta and second of all Adobe does not maintain 64 bit flash as much as 32 bit. Case in point is the security problem they had, they did not patch the 64 bit version, and for a while it (64 bit flash) was unsupported.

In fact your claims of r64 bit flash are not supported by adobe:

[http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)

> Because this is a preview version of Flash Player, we don’t expect it to be as stable as a final release version of Flash Player. Use caution when installing Flash Player "Square" on production machines.

Considering there is a stable 32 bit flash, and no stable 64 bit flash, you are overstating the benefits of 64 bit Ubuntu.

While it may work for you, you need to recognize it does not always work for everyone and when you over sell a product you are asking for disappointment.

Please keep your posts more realistic ;)

---

### Post by janpol on 2011-01-07
> **johntaylor1887 said:**
> Such as?

On Ubuntu 10.10, Slackware 13.1 or Gentoo 64 bits my network card randomly dies and refuses to work (after a while it gets up again), I even tried dual-booting with Windows and, when this happens, if I boot to Windows the card wont work even there (and Windows 7 freezes xD). The same if I use a live cd (of any distro, 32 or 64 bits) after the card stops working, I don't know if something gets heated up in the Mobo (when I get the time, I'll try to hunt the problem down), but it doesn't happen if I am using a 32bit OS.

Switched to Ubuntu 10.10 32bits and it has been working like a charm for 2 months, the other day I tried the 64bit version again....and after a few days the card died (and then works again, it's completely random).

> **johntaylor1887 said:**
> Such as? I actually did a comparison on the same computer, and found 64bit to be a little bit "snappier". Is it a big difference? No. But I'll always take faster over slower any day. 64bit is here to stay.

64bit is the future, no doubt of that, but I'll wait a little bit ;)

---

### Post by handy on 2011-01-07
> **janpol said:**
> 
Regarding to "everything is faster under 64bits":

You selectively quoted me, I said "just about everything". :)

> **janpol said:**
> 
.Only 64 bit apps, 32 bit apps will run slower on a 64bit os 

So this is something that you have found?

> **janpol said:**
> 
.The performance difference is unnoticeable for most apps 

I agree.

> **janpol said:**
> 
.Some things still have compatibility issues (I had a really nasty bug with the 64 bit version of my network card driver). This is the reason why the Ubuntu download page recommends the 32bit version for Desktops. 

That is still a problem with Linux & the like, though it is an ever diminishing problem.

> **janpol said:**
> 
.Read that phoronix article again, some things are faster, not everything. Also, try installing a 64bit OS and use it for your every day tasks, you won't feel much diference (unless you use daily an app that really takes advantage of 64 bit technology :P) 

Remember, that misquote I pointed out at the start? :P :P

I don't know about the difference from experience as I've been using 64bit since Breezy, & haven't had any problems due to 64bit for years now. (Though I've been on Arch for the last 2 years & 10 months.)

As far as using software that takes advantage of 64bit is concerned, personally I encode & transcode a lot of video from time to time; - both 64bit & definitely SMP help a great deal in that task.

If someone has 64bit hardware I can see no problem in giving a 64bit LiveCD a spin & seeing if there are any deal breakers. If there are none then give it a go & find out from daily use if there are any problems. 

If you have a NIC that doesn't have a 64bit driver & you have a computer that you can add cards to you could replace the unsupported card or install a supported card & turn off the on-board in the BIOS (if you so desired?). These cards are so cheap now that they are almost giving them away.

Unless you are unlucky enough to have one of the increasingly rare driver problems life will continue as usual with the exception that some tasks that you may or may not happen to do will be noticeably faster.

***[edit:]** I have no problems with 64bit flash. I kept using it after the security scare, NoScript kept me safe. :) *

---

### Post by psusi on 2011-01-07
> **handy said:**
> If you have a NIC that doesn't have a 64bit driver & you have a computer that you can add cards to you could replace the unsupported card or install a supported card & turn off the on-board in the BIOS (if you so desired?). These cards are so cheap now that they are almost giving them away.


I don't think anybody uses proprietary linux drivers for ethernet, so this isn't a concern.  Some people do however, use ndiswrapper to load the proprietary windows drivers for wireless cards that don't have Linux drivers, so this would be a problem on 64bit.

Other than that, the only problems are with proprietary crapware like Flash.  Open source software isn't written by morons and has no problem being built and running 64 bit from day one.  These days even flash works ok on 64bit.

---

### Post by Evil-Monkey on 2011-01-07
I found when I bought my l500 Toshiba Satellite Pro laptop recently, that Ubuntu 10.10 would freeze when I watched DVDs and when the screensaver was activated.

This problem was immediately fixed when I switched from 32-bit to 64-bit Ubuntu.

I'm not really sure of why, however this was definitely the only thing that fixed my freezing.
:KS

---

### Post by handy on 2011-01-07
> **psusi said:**
> 
I don't think anybody uses proprietary linux drivers for ethernet, so this isn't a concern.  Some people do however, use ndiswrapper to load the proprietary windows drivers for wireless cards that don't have Linux drivers, so this would be a problem on 64bit. 

My usage of "NIC" was meant to include wireless NICs too. I should have been more articulate. :) 

> **psusi said:**
> 
Other than that, the only problems are with proprietary crapware like Flash.  Open source software isn't written by morons and has no problem being built and running 64 bit from day one.  These days even flash works ok on 64bit.

What he said. ^ ...

---

### Post by Linyx on 2011-01-08
I didn't used 64-bit OS, therefore not know about that............I have seen some members are Saying that they had a problem with Drivers.....and some of the Important softs like flash.

As far as i know, Older cards/Softwares will have problem with Drivers in 64-bit but i don't think so that newer cards/softs will have the same issue, Moreover, If one can try the 64-bit OS from Live-Cd and check out whether his/her all Drivers are Getting or not...I think this is the simple way to test the PC on 64-bit platform.

And i have seen one post something like this that...

 "*64-bit Core can Execute 64-Characters per-turn and Vice versa*....Is that true...?"

If this statement is true then i think 64-bit performance will be better as compared to that of 32.....

---

### Post by cascade9 on 2011-01-08
> **Linyx said:**
> I didn't used 64-bit OS, therefore not know about that............I have seen some members are Saying that they had a problem with Drivers.....and some of the Important softs like flash.

As far as i know, Older cards/Softwares will have problem with Drivers in 64-bit but i don't think so that newer cards/softs will have the same issue, Moreover, If one can try the 64-bit OS from Live-Cd and check out whether his/her all Drivers are Getting or not...I think this is the simple way to test the PC on 64-bit platform.

There are always people that have problems with flash. I'd guess that a lot of them were using 32bit flash in a wrapper, which is more buggy than 32bit flash on 32bit. 64bit native flash works as well as flash ever does on linux, and there is a tool for managing flash with frefox (flash-aid, made by lovinglinux, who is  amember here) if you dont want to manually install 64bit flash. 

migs73 driver issues are for a brother printer. Almost everything runs under 64bit, thats a rare exception. I dont know whatmigs73 tried to get the drivers going, or how long ago. Its possible that it didnt work when then but does now. 

You shouldnt have any issues with older video cards, sound cards, etc or linux native software under 64bit. 

I'd try 64bit...but dont expect a huge difference between 32bit and 64bit in performance for most programs. If you want to see a big difference, try doing some video or audio encoding on 64bit and compare it to 32bit....

---

### Post by Linyx on 2011-01-08
> **cascade9 said:**
> migs73 driver issues are for a brother printer. Almost everything runs under 64bit, thats a rare exception. I dont know whatmigs73 tried to get the drivers going, or how long ago. Its possible that it didnt work when then but does now. 

You shouldnt have any issues with older video cards, sound cards, etc or linux native software under 64bit.


I think their will some driver issues with older cards, because i had read it in many places....Not meant to say that **all** cards...... but Max older cards i means.

Now i think that it depends on the need of User......If someone is  dealing with video editing, CAD and image packages then it would be  especially beneficial to be able to work with over 4GB of RAM amongst  the other improvements.

I had read the somewhere ,Which was something like this  "32-bit application on 64-bit OS will run slower as compared to that run on 32,...."

Thats strange..!! As 64-bit CPU has More registry space so why will 32-bit application run slower on that......:confused:

---

### Post by areteichi on 2011-01-08
> **handy said:**
> [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

These benchmarks really make me want to install 64-bit Ubuntu :D
I think I will upgrade my laptop to a 64-bit CPU (Intel Core 2 Duo) this summer.

---

### Post by cascade9 on 2011-01-08
> **Linyx said:**
> I think their will some driver issues with older cards, because i had read it in many places....Not meant to say that **all** cards...... but Max older cards i means.

I'd really, really doubt it. Almost all the 'older cards' use open surce drivers (all the non-HD ATI card, all the 71.xx supported nvidia cards, etc). They will runnfine on 64bit. 

ATI and nvidia drivers have no issue with 64bit in my experince (though I havent used a 'FX/5XXX' series card using 173.xx drivers on 64bit). If there are driver issues, they would be semi-obscure and junk cards (VIA and SiS, I'm looking at you) 

> **Linyx said:**
> Now i think that it depends on the need of User......If someone is  dealing with video editing, CAD and image packages then it would be  especially beneficial to be able to work with over 4GB of RAM amongst  the other improvements.

Even with 2GB of RAM 64bit helps. Though to be honest,. I'm not sure about how much improvement you will get for video editing and CAD with linux 64bit version. 

> **Linyx said:**
> I had read the somewhere ,Which was something like this  "32-bit application on 64-bit OS will run slower as compared to that run on 32,...."

Thats strange..!! As 64-bit CPU has More registry space so why will 32-bit application run slower on that......:confused:

Somebody is talking about the old, horrible intel 'Itanium' architechture. That was not x86 and had nasty 32bit emulation. Or they were talking about 32bit programs on windows 64bit. 

Almost everything you'll find in the repos for linux distros should have a 64bit version so its not really worth worring over.

---

### Post by Linyx on 2011-01-08
Right now i have 1Gb-DDR2, and now i have decided to increase it to 2G so that i can Run 64-Bit OS......

One thing comes to my mind,  Maybe wrong , but let me explain...

As far as i know, 64-bit can Execute more Data per Turn then 32-bit, so if we try to install a software, let suppose 64-bit Software , i think it will be install faster because the Raw-information will be executed faster by 64 as Compared to 32.....isn't?

---

### Post by psusi on 2011-01-08
> **Linyx said:**
> 
Thats strange..!! As 64-bit CPU has More registry space so why will 32-bit application run slower on that......:confused:

Because a 32-bit application is't using the new registers, so it sees no benefit.  It sees a slight ( not really noticeable ) loss because when it makes system calls to the 64 bit kernel, translation must be done.

---

### Post by Linyx on 2011-01-08
> **psusi said:**
> Because a 32-bit application is't using the new registers, so it sees no benefit.  It sees a slight ( not really noticeable ) loss because when it makes system calls to the 64 bit kernel, translation must be done.

Yes Of-course, but i think you didn't get my words Correctly..........

The sentence means that  "32-bit application on 64-bit OS will run **slower** **as compare to 32**"

Edit : - If i have Ubuntu-64 and i want to run 32-bit application, it won't run right....?It will be more useful if OS-x64 also run 32-bit application (because its not Require more Registry-space),

---

### Post by psusi on 2011-01-08
> **Linyx said:**
> Yes Of-course, but i think you didn't get my words Correctly..........

The sentence means that  "32-bit application on 64-bit OS will run **slower** **as compare to 32**"

Yes, and I Just explained why.

---

### Post by oldos2er on 2011-01-08
> **Linyx said:**
> Currently i am on 32-bit Os's , I had triple boot "Linux(Gnome/KDE) & 7" and all are in 32-bit......but if i have some benefit of using 64-bit, or if i can get much **better performance** in 64-bit, i must switch to 64-bit then.......but my RAM is not too much as i have Only 2GB.....

I ran 64-bit Ubuntu for a long time with 2GB RAM; works great. If you do CPU-intensive tasks e.g. video encoding, they will be noticeably faster.

---

### Post by handy on 2011-01-08
> **Linyx said:**
> Right now i have 1Gb-DDR2, and now i have decided to increase it to 2G so that i can Run 64-Bit OS......

You don't need to add more RAM. I have only 1GB on my iMac (main machine) & it runs perfectly well on 64bit. My 2nd machine has 2GB of RAM, it also runs 64bit perfectly well.

Only upgrade your RAM if you have another reason to do so.

---

### Post by tekkidd on 2011-01-08
If you have 4+ GB of ram, a 64 bit OS can address all of it rather than just 4GB (or 3.2 in my case) that a 32bit can

---

### Post by handy on 2011-01-09
> **tekkidd said:**
> If you have 4+ GB of ram, a 64 bit OS can address all of it rather than just 4GB (or 3.2 in my case) that a 32bit can

Yeh! What he ^ said. :) (too)

---

### Post by Linyx on 2011-01-09
Is someone here using Ubuntu-64 so that i know how much ram it consume without running other processes(Only OS)...

And i think no one notice my **Post #35** :

---

### Post by handy on 2011-01-09
> **Linyx said:**
> Is someone here using Ubuntu-64 so that i know how much ram it consume without running other processes(Only OS)...

And i think no one notice my **Post #35** :

I noticed your post_35, my answer to it was that you do NOT have to add anymore RAM to run 64bit. It makes no noticeable difference to the amount of RAM that you are using.

Running 64bit gives your system the *ability* to access RAM beyond the boundary set by 32bit architecture. Most of us don't even need 4GB let alone more. My main 64bit system is very happy with 1GB & has been for years.

---

### Post by Linyx on 2011-01-09
> **handy said:**
> I noticed your post_35, my answer to it was that you do NOT have to add anymore RAM to run 64bit. It makes no noticeable difference to the amount of RAM that you are using.

Running 64bit gives your system the *ability* to access RAM beyond the boundary set by 32bit architecture. Most of us don't even need 4GB let alone more. My main 64bit system is very happy with 1GB & has been for years.

Thanks, i Will try it :P

---

### Post by psusi on 2011-01-09
> **tekkidd said:**
> If you have 4+ GB of ram, a 64 bit OS can address all of it rather than just 4GB (or 3.2 in my case) that a 32bit can

The 32 bit pae kernel can address more than 4gb of ram, but a single process is still limited to 3gb.

---

### Post by Linyx on 2011-01-11
Another thing....Probably not belong to this thread...

"I have 1Gb DDR2 with a Frequency of 533Mhz and if i replace this one with same Memory DDR2 having 800-Frequency...Would it make me some Benefit, Well , it simple that higher the Frequency ,greater will be the rate at which data transfer to cache Or North-Bridge > CPU but one thing is Puzzling me and that is my FSB , i have 800MT/S....which has 200Mhz of frequency so if i increase my Ram-frequency, will it be **bottle-neck** .....? "

---

### Post by psusi on 2011-01-11
> **Linyx said:**
> Another thing....Probably not belong to this thread...

"I have 1Gb DDR2 with a Frequency of 533Mhz and if i replace this one with same Memory DDR2 having 800-Frequency...Would it make me some Benefit, Well , it simple that higher the Frequency ,greater will be the rate at which data transfer to cache Or North-Bridge > CPU but one thing is Puzzling me and that is my FSB , i have 800MT/S....which has 200Mhz of frequency so if i increase my Ram-frequency, will it be **bottle-neck** .....? "

Yes, it will help some.

IIRC, they mislabel DDR memory frequency.  It is actually 200 MHz, but transfers data 4 times per clock, just like your FSB.

---

### Post by cascade9 on 2011-01-11
> **psusi said:**
> IIRC, they mislabel DDR memory frequency. It is actually 200 MHz, but transfers data 4 times per clock, just like your FSB.

Wrong, actually. DDR runs at half the 'rated' speed (so DDR400 is 200MHz, DDR2-800 is 400MHz, etc). 

Maybe you got confused with intels 'quad pumped' FSB for P4s (so when intel said 533 FSB, they meant 133Mhz quad pumped)

> **Linyx said:**
> Another thing....Probably not belong to this thread...

"I have 1Gb DDR2 with a Frequency of 533Mhz and if i replace this one with same Memory DDR2 having 800-Frequency...Would it make me some Benefit, Well , it simple that higher the Frequency ,greater will be the rate at which data transfer to cache Or North-Bridge > CPU but one thing is Puzzling me and that is my FSB , i have 800MT/S....which has 200Mhz of frequency so if i increase my Ram-frequency, will it be **bottle-neck** .....? "

You are running a 800MT/s / 200Mhz FSB with 533Mhz (266MHz in reality) DDR2? Thats a bottleneck. Increasing it to DDR2-800 would help. Aside from extra memroy bandwidth it 'cleans up' the complex interplay between FSB and RAM MHz (with 800/200 FSB and 533/266 RAM, the clock cycles dont coincide, so sometimes the CPU needs to wait longer for the memory to refresh etc. With 200/800 FSB and 400/800 RAM the cycles do line up)

---

### Post by psusi on 2011-01-11
> **cascade9 said:**
> Wrong, actually. DDR runs at half the 'rated' speed (so DDR400 is 200MHz, DDR2-800 is 400MHz, etc). 

Maybe you got confused with intels 'quad pumped' FSB for P4s (so when intel said 533 FSB, they meant 133Mhz quad pumped)


That's true for DDR, but DDR2 is quad pumped isn't it?

---

### Post by cascade9 on 2011-01-11
> **psusi said:**
> That's true for DDR, but DDR2 is quad pumped isn't it?

Sort of. The internal clock is quad-pumped (in some ways), DDR2 runs internally at 1/4 of the 'rated speed'.The actual I/O clock is double that. DDR3 internally is 1/8th of the rated speed, but I/O is still 1/2 the rated speed.

---

### Post by Linyx on 2011-01-11
> **cascade9 said:**
> 
You are running a 800MT/s / 200Mhz FSB with 533Mhz (266MHz in reality) DDR2? Thats a bottleneck. Increasing it to DDR2-800 would help. Aside from extra memroy bandwidth it 'cleans up' the complex interplay between FSB and RAM MHz (with 800/200 FSB and 533/266 RAM, **the clock cycles dont coincide, so sometimes the CPU needs to wait longer for the memory to refresh etc. With 200/800 FSB and 400/800 RAM the cycles do line up)**

Thanks for this nice suggestion,But one thing i didn't get from your post, you have mentioned that My-CPU wait sometime because of low-frequency Ram...?

My FBS is 200MHz so it means that i won't run faster then 200..So if I increase my ram Frequency from 266 to 400....Am confuse about this :confused:

And also ,
Can you explain the **Bold-part** of your above post so that i can Completely get your words....

---

### Post by psusi on 2011-01-11
> **Linyx said:**
> 
My FBS is 200MHz so it means that i won't run faster then 200..So if I increase my ram Frequency from 266 to 400....Am confuse about this :confused:


We're saying that the frequency of your ram is actually 133, and you are considering upgrading to 200.  They label the ram twice as high as the actual frequency though, because it is double pumped.

---

### Post by Linyx on 2011-01-11
> **psusi said:**
> We're saying that the frequency of your ram is actually 133, and you are considering upgrading to 200.  They label the ram twice as high as the actual frequency though, because it is double pumped.

oh...But my Ram is label is 533Mhz...As mentioned by you that they rated that as twice so how can my ram Frequency become 133..!!???

533/2 =**266Mhz**....isn't?

---

### Post by psusi on 2011-01-11
> **Linyx said:**
> oh...But my Ram is label is 533Mhz...As mentioned by you that they rated that as twice so how can my ram Frequency become 133..!!???

533/2 =**266Mhz**....isn't?

DDR is labeled twice as fast, but DDR2 is 4x.

---

### Post by Linyx on 2011-01-12
> **psusi said:**
> DDR is labeled twice as fast, but DDR2 is 4x.

OMG..!! Can i know why they label wrong...?and DDR2 Is 1/4 of LABEL...???!!

Edit:- I think the label number means frequency times Num-of-transfer/sec...like FSB...may be..

---

### Post by psusi on 2011-01-12
> **Linyx said:**
> OMG..!! Can i know why they label wrong...?and DDR2 Is 1/4 of LABEL...???!!


Because it is quad pumped, so it transfers data 4x faster than the frequency.

---

### Post by Linyx on 2011-01-13
> **psusi said:**
> Because it is quad pumped, so it transfers data 4x faster than the frequency.

Thanks, I got this, that means that it transfer  4 bits of data per cycle..

I had brought DDR2-667Mhz(means 166Mhz in Actual) , Not Exactly know what the Model is, when i install it into one of my Four Slot, i doesn't Worked, then i try to install it on another, same Problem(My CPU Front LED becomes** Red**), then at last i try the third DIMM-Slot and it worked...!!

However all my slots are **Fine**, i had Currently installed (2 X 512) in dual-Channel..

Any Idea about that,,why its not working in **another** SLOTS...?

Edit:-Mother-Board is [SIZE=2]Intel-945 Pentium-D 2.8Mhz[/SIZE]....

---

