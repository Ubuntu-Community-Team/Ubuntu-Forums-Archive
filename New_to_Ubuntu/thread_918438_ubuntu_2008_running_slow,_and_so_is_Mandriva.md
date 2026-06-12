---
title: "ubuntu 2008 running slow, and so is Mandriva"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by tetsujin29 on 2008-09-12
I have an emachine running intel celeron 2.2GHZ with 1GB of RAM.  I have recently installed Mandriva and found the performance to be imperfect (firefox slow, general windows speed slower than VISTA).  So I switched to Ubuntu.  While I like the GNome interface more than KDE Mandriva, I find that the interface is still slower than the windows counterpart.  Firefox is not speedy, apps take about 5-10 seconds to launch, and switching desktops using the 3D desktop invokes slowdowns and lower resolution.  Can someone point out the problem please??  Under the same specs windows VISTA would be flying but why is Ubuntu (and linux in general) slower?  I have read numerous posts on this forum (and others) complaining the same thing and no one really offered any solid solutions to the problem.  I don't want to switch to Kubuntu Xubuntu before I try out some solutions with Ubuntu itself.  Please help and thanks!

---

### Post by knattlhuber on 2008-09-13
I'm not sure if Vista would be 'flying' with a 2.2GHz Celeron...:)

I had a 3.8GHz Celeron running Ubuntu with 2GB of RAM and I wasn't impressed at all. I think it's the processor.

---

### Post by Bush_Roo on 2008-09-13
> **knattlhuber said:**
> I'm not sure if Vista would be 'flying' with a 2.2GHz Celeron...:)Agree

What sort of graphic card do you have?

Terminal:
```
lspci
```

---

### Post by tetsujin29 on 2008-09-13
Here is my graphics card information:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) (prog-if 00 [VGA controller])
Subsystem: Trigem Computer Inc. Unknown device 3189
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at f0000000 (32-bit, prefetchable) [size=128M]
Memory at e8000000 (32-bit, non-prefetchable) [size=512K]
Capabilities: [d0] Power Management version 1
Kernel modules: intelfb, i2c-i810

Would an upgraded video card help?   

Thanks!

---

### Post by Bush_Roo on 2008-09-14
Sorry for the late reply... I have little time these days.

The on-board graphics card isn't enough to make Compiz run smoothly. A NVIDIA card will help out there and fix the problem right away. Otherwise it is recommended to disable Compiz, and check the performance.

Simple compiz disable: System > Preferences > Appearance > Visual Effects (5th tab up top) > None

Check it out and see if it helps.

I'm really slow with replies, and I apologize for that... something that I can't help.

---

### Post by Bush_Roo on 2008-09-14
Btw, I have a Celeron 2 gig with 768 mb RAM, and Firefox takes around 5 to 10 seconds to launch. I run other computers with Ubuntu (P4 2.8 gig 2 gig RAM etc.) and it is a bit slow on them too. Once it gets going though, it is OK. Your Firefox startup time is normal.

---

### Post by knattlhuber on 2008-09-14
> **tetsujin29 said:**
> 
Would an upgraded video card help?   


I don't know that specific card, but Intel graphics cards aren't really famous for their performance.
I exchanged my low-end ATI card for a nVIDIA GeForce 7700 and that resulted in some speed improvement on my machine. You can also squeeze more RAM into your machine but eventually you need to upgrade your processor if you want better performance. Celeron just doesn't cut it.

---

### Post by tetsujin29 on 2008-09-14
I have disabled compiz (now using only 4 desktops with no animations) but it is still slower than expected (i.e. all programs have a 5-10 second blank period between when the icon is clicked and when the window is actually opened).  Perhaps the processor is the problem - I just thought linux might be okay on an celeron processor.

---

### Post by Sorivenul on 2008-09-14
I run preload on all my machines, old and new alike, and get a nice little performance boost.  See the following links, and if interested it's in the repository.
[http://www.techthrob.com/tech/preload.php]("http://www.techthrob.com/tech/preload.php")
[http://www.techthrob.com/tech/preload_files/preload.pdf]("http://www.techthrob.com/tech/preload_files/preload.pdf")
Or use Opera, Midori, or Dillo for faster browser startups - they all launch faster than FF, on my systems.

---

### Post by Bush_Roo on 2008-09-14
There is one other things I can think of that particularly slows down programs from starting (like a 5 odd second wait for EACH program), and that is when you re-name your computer alias incorrectly (I can't explain it very well, but am trying to find some details). If you go into network settings and under the hosts tab change the alias of 127.0.1.1 you will certainly run into problems with things starting very slowly.

Apparently it is NOT your graphics card that is the problem. Mind you, I don't believe that it is enough to run compiz smoothly anyway--NVIDIA is best for that.

Celerons are great machines (much slower than your's) for running Linux. This Celeron here, when I installed Ubuntu only had 256 megs of RAM without a graphics card, and it worked really well.

I'll see if I can get more details on renaming the localhost alias thingi (please mind my technical terms)

---

### Post by SunnyRabbiera on 2008-09-14
> **Bush_Roo said:**
> There is one other things I can think of that particularly slows down programs from starting (like a 5 odd second wait for EACH program), and that is when you re-name your computer alias incorrectly (I can't explain it very well, but am trying to find some details). If you go into network settings and under the hosts tab change the alias of 127.0.1.1 you will certainly run into problems with things starting very slowly.

Apparently it is NOT your graphics card that is the problem. Mind you, I don't believe that it is enough to run compiz smoothly anyway--NVIDIA is best for that.

Celerons are great machines (much slower than your's) for running Linux. This Celeron here, when I installed Ubuntu only had 256 megs of RAM without a graphics card, and it worked really well.

I'll see if I can get more details on renaming the localhost alias thingi (please mind my technical terms)

Well my intel card seems to run effects pretty well though, but it depends on the card I guess.

---

### Post by Bush_Roo on 2008-09-14
It is interesting, but I came across problems when I messed about with the /etc/hosts file, like giving 127.0.1.1 a new alias without changing /etc/hostname

or was it the other way around?

Anyway, I have been working to try and replicate the problem, and it seems like a bug that has been fixed for me. There could be other things: I can't remember, but I don't think the computer was networked to other computers back then and now it is. So if that was the problem, then I can't test it.

All I can think of for now is see if alias of 127.0.1.1 in /etc/hosts and /etc/hostname match perfectly.

My configuration (as an example):

```
timothy@tower:~$ cat /etc/hostname
tower
``````
timothy@tower:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 tower

``````
timothy@tower:~$ hostname
tower
```

That's all I can think of for now.

---

### Post by tetsujin29 on 2008-09-15
THanks for all the help.  Right now I am not sure where the problem is - is it the amount of RAM (when I run free -m there is usually about only 15-20MB free out of the 1GB that's installed, and there is small amount of swapping).  Or is it the processor itself?  Mine is a 2.2ghz celeron which is a decent speed...  But programs are definitely running sluggishly.  There is lag all the time - if I have VLC open with firefox everything just slows down and the firefox webpages become grayed out....  If I run Azureus then every other program become much slower as well... 

Is it worthwhile to upgrade my processor?  I can upgrade to a new Celeron processor (which is about 60-70$) but the 2.2ghz that I have shouldn't be this slow, even though it is a celeron.  My laptop is a 1.2ghz Pentium III running VISTA with a 1GB and it is much faster than this machine...

---

### Post by knattlhuber on 2008-09-15
Don't worry about the little amount of free RAM. Linux automatically uses all free RAM for buffer cache, this is normal behavior. As soon as an application needs RAM, it is made available.
The behavior you described with VLC and FF running I also had on my Celeron machine. If I were you, I'd probably add a GB memory or two. A new Celeron processor is probably more expensive than the RAM and less effective. Also, the processor may not be easy to replace if it is soldered. Upgrading to a duo core processor requires a new motherboard, new RAM, etc.
What is beyond me is how your 1.2GHz P3 runs Vista smoothly. Did you switch off Aero?

---

### Post by Bush_Roo on 2008-09-15
Well, I can't understand why it would be running slowly... keep trying though--try different things. There may be a hardware issue, but I wouldn't put it down the the fact that it is a Celeron. The RAM should be fine though--I have Ubuntu running quite well on P3s with 256 megs of RAM (playing DVDs even).

Just don't give up, and good luck :)

---

### Post by eragon100 on 2008-09-15
> **knattlhuber said:**
> Don't worry about the little amount of free RAM. Linux automatically uses all free RAM for buffer cache, this is normal behavior. As soon as an application needs RAM, it is made available.
The behavior you described with VLC and FF running I also had on my Celeron machine. If I were you, I'd probably add a GB memory or two. A new Celeron processor is probably more expensive than the RAM and less effective. Also, the processor may not be easy to replace if it is soldered. Upgrading to a duo core processor requires a new motherboard, new RAM, etc.
What is beyond me is how your 1.2GHz P3 runs Vista smoothly. Did you switch off Aero?

If the RAM is normal behaviour, well, do I have a problem then, because for me it says:

eragon@Asgard:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3041        843       2198          0        131        391
-/+ buffers/cache:        321       2720
Swap:         8911          0       8911

---

### Post by Bush_Roo on 2008-09-15
> **eragon100 said:**
> If the RAM is normal behaviour, well, do I have a problem then, because for me it says:

eragon@Asgard:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3041        843       2198          0        131        391
-/+ buffers/cache:        321       2720
Swap:         8911          0       8911

Wow, what a beast! :guitar::):)

---

### Post by tetsujin29 on 2008-09-15
> **knattlhuber said:**
>  What is beyond me is how your 1.2GHz P3 runs Vista smoothly. Did you switch off Aero?

Yes I am not running Aero.  But normally programs open/close much faster w/ no lag.  For my emachine even when I disable compizfusion things are sluggish..  I just want to be able to have more than two programs open w/o feeling like the system is straining...

---

### Post by nowshining on 2008-09-15
> **Bush_Roo said:**
> It is interesting, but I came across problems when I messed about with the /etc/hosts file, like giving 127.0.1.1 a new alias without changing /etc/hostname

or was it the other way around?

Anyway, I have been working to try and replicate the problem, and it seems like a bug that has been fixed for me. There could be other things: I can't remember, but I don't think the computer was networked to other computers back then and now it is. So if that was the problem, then I can't test it.

All I can think of for now is see if alias of 127.0.1.1 in /etc/hosts and /etc/hostname match perfectly.

My configuration (as an example):

```
timothy@tower:~$ cat /etc/hostname
tower
``````
timothy@tower:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 tower

``````
timothy@tower:~$ hostname
tower
```

That's all I can think of for now.


Actually /etc/hosts at top should look something similiar to this:

```
HOSTNAME="tower".
lo="lo 127.0.0.1"
INTERFACES=(lo)
127.0.0.1 localhost.localdomain localhost tower
127.0.0.1 localhost

```

however after posting i noticed a problem with mine :P

---

### Post by Isaac Karjala on 2008-09-15
Xubuntu 7.x will run fine on 128MiB RAM, 300MB swap and a 32b 800Mhz Pentium (II or III, I can't remember); can't remember if that computer had a video card.
Ubuntu 7.x will run fine on 512MiB RAM, 1GB swap, 32b 1.8Ghz Atholon XP and a Radeon Video card (want to say 7800, but can't remember)
I don't know what kind of minimal specs Ubuntu 8.x will run on since the only machine I've ran it on is no where near minimal, but I really doubt that Hardy takes that much more then Feisty...

---

### Post by egalvan on 2008-09-15
Slow-loading software can also be caused by a slow hard drive.
Some drives can be as slow as 4200rpm.
Moving to a 7200rpm can make a big difference.

In my experience, the following order of up-grades made the biggest difference...

RAM.... but above 512m not as much
hard drive speed... 4200rpm is slow, and newer/bigger drives are faster, even if only 5400rpm
cpu, although jumping from a Celeron-class did make a larger difference.

my  2 pennies

---

### Post by tetsujin29 on 2008-09-15
Would an upgraded graphics card improve the speed if I am NOT using compizfusion?  I was looking at a NVIDIA Geforce 512MB 8500GT - is that excessive?  I don't mind updating the graphics card and/or harddrive.  But I am wondering whether if it is worthwhile to upgrade the processor which is more difficult to install.  With my celeron processor at 2.2ghZ, I am inclined to think that the problem is elsewhere.

---

### Post by nowshining on 2008-09-15
the card u get depends on what you plan to do, if you plan on intense gaming - that would prob. be a good card, but to get 3D performance you'll need to install the Nvidia Graphics Drivers from the Nvidia site - easy to do and many people recommend getting rid of the one ubuntu wants to install.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

and alas it may require editing the xorg.conf but nvidia has an automatic way of doing this.. and will ask at the end.. :) or it may again require manuall editing depending on your environment..

---

### Post by OldTimeTech on 2008-09-15
Check this url out....it talks about the difference between the Celeron and a Pentium 4...

[http://computer.howstuffworks.com/question268.htm](http://computer.howstuffworks.com/question268.htm)

As an old tech....we never advised anyone to buy Celeron as they are always considered slower...much slower than other chips!

---

### Post by nowshining on 2008-09-15
i reaad a thing on celeron - it was due to it not having onboard cache or something.. :/

---

### Post by Bush_Roo on 2008-09-15
> **nowshining said:**
> Actually /etc/hosts at top should look something similiar to this:

```
HOSTNAME="tower".
lo="lo 127.0.0.1"
INTERFACES=(lo)
127.0.0.1 localhost.localdomain localhost tower
127.0.0.1 localhost

```

however after posting i noticed a problem with mine :PSome earlier version of Ubuntu (and Debian) had to have 'odd' yet elaborate setups for the /etc/hosts file. I ahve noticed that these 'bugs' have been fixed, so the setup can be simple now :)

---

### Post by Bush_Roo on 2008-09-15
> **Isaac Karjala said:**
> Xubuntu 7.x will run fine on 128MiB RAM, 300MB swap and a 32b 800Mhz Pentium (II or III, I can't remember); can't remember...

That would be P3 :)

P2... yuck... $50 will get something better...

---

### Post by Bush_Roo on 2008-09-15
> **tetsujin29 said:**
> Would an upgraded graphics card improve the speed if I am NOT using compizfusion?  I was looking at a NVIDIA Geforce 512MB 8500GT - is that excessive?  I don't mind updating the graphics card and/or harddrive.  But I am wondering whether if it is worthwhile to upgrade the processor which is more difficult to install.  With my celeron processor at 2.2ghZ, I am inclined to think that the problem is elsewhere.I got a little old FX 5500 in this one, and it doesn't really do much for the old bom. In fact, it's graphics performance isn't much better. I put it down to the fact that it is an old Celeron.

As a rule, I avoid Celerons these days when I poke about with 2nd hand puters. In a way, I can't wait for this machine to die...

Edit: Oh yes, and I did a benchmark test with this Celeron (2.0 gig 768mb RAM) and a P3 running at 1 gig with 384mb RAM. The P3 in fact OUTPERFORMED the Celeron in almost all the tests!! I can't remember which ones, but I was proving to a couple of people just how slow Celerons really are. I think I proved the point ;)

---

### Post by halitech on 2008-09-15
just out of curiousity, have you tried checking the ram with the memtester option that shows up when you boot? maybe you have a stick of ram going bad but not bad enough to shut you down yet

---

### Post by nowshining on 2008-09-15
> **Bush_Roo said:**
> Some earlier version of Ubuntu (and Debian) had to have 'odd' yet elaborate setups for the /etc/hosts file. I ahve noticed that these 'bugs' have been fixed, so the setup can be simple now :)

i never knew about the bug or forgot about reading about it, but it works just fine and it also ads a small speedup to the system that way...

---

### Post by tetsujin29 on 2008-09-15
I did a memtest yesterday and there are no errors.  I think many of you are confirming the fact that the main problem is simply the Celeron processor.  Perhaps I should think about getting a new machine..  sigh...

---

### Post by nowshining on 2008-09-15
that and emachines are not good machines to begin with..how ol' is this emachine machine?

---

### Post by tetsujin29 on 2008-09-15
> **nowshining said:**
> that and emachines are not good machines to begin with..how ol' is this emachine machine?

About two years old - actually a hand-me-down from a co-worker.  It's got a DVD-ROM and CD-burner so I thought I'd put Ubuntu on it and make it usable again, but the Celeron processor has been really disappointing..  

I have a pentium III compaq computer (probably around 600mhz) from 6-yrs ago.  Would it be worthwhile to upgrade the processor on that machine and try to install ubuntu on it?  Would a 6-yr-old P3 have better performance than a 2-yr-old celeron processor?  Even if I have to upgrade both the processor + graphics card + new hd it would probably be still cheaper than buying a whole new tower..

---

### Post by nowshining on 2008-09-15
i've had an emachine before and it was bad :/ and hard to upgrade - small case, it too was given to me, and more than likely the compaq w/ the P3 cpu would more than likely suffice and be better than the emachine computer ie: no need to upgrade unless you want too... if you can go for the new tower if this includes all the cpu, etc..:)

---

### Post by Bush_Roo on 2008-09-16
> **tetsujin29 said:**
> I did a memtest yesterday and there are no errors.  I think many of you are confirming the fact that the main problem is simply the Celeron processor.  Perhaps I should think about getting a new machine..  sigh...

*sigh* really sorry to hear that ya can't get it to work smoothly...

> **nowshining said:**
> i never knew about the bug or forgot about reading about it, but it works just fine and it also ads a small speedup to the system that way...Thanks, I'll keep that in mind :)

Just to confirm a problem: I did come across "something" odd a bit back. I start some app or anything that needs to execute and it simply sat there for 4 or so seconds DOING NOTHING before the app eventually started to load. Worse yet, I didn't write down what I did (like a dope) and I haven't been able to replicate this problem. I think it may have been on Gusty... I really can't remember. I poked around with the hostname (something like that??) and it started working right again. *shrug*

Sorry if my story seems to change, but I just can't remember all the details... I think I had my sister and her husband over that day... ugh... :p

---

### Post by nowshining on 2008-09-16
> **Bush_Roo said:**
> *sigh* really sorry to hear that ya can't get it to work smoothly...

Thanks, I'll keep that in mind :)

Just to confirm a problem: I did come across "something" odd a bit back. I start some app or anything that needs to execute and it simply sat there for 4 or so seconds DOING NOTHING before the app eventually started to load. Worse yet, I didn't write down what I did (like a dope) and I haven't been able to replicate this problem. I think it may have been on Gusty... I really can't remember. I poked around with the hostname (something like that??) and it started working right again. *shrug*

Sorry if my story seems to change, but I just can't remember all the details... I think I had my sister and her husband over that day... ugh... :p


hehe, i forget a lot too.

If you want you can also set your hostname via sysctl setting :) or basically something..

kernel.hostname=hostname

---

### Post by brdokoky on 2008-09-16
When you want to speed up ubuntu , tray to install ubuntu on reiserfs. Ext3 is too slow.

---

### Post by xeth_delta on 2008-09-16
To the OP. Can you please post the output of the following:
```
glxinfo | grep -i direct
glxinfo | grep -i opengl
```

Also, is the interface slow only when opening a program or also when switching or moving windows?

My laptop with an on-board intel 945GM graphics card and 1GB of RAM runs compiz quite nicely and smooth ( at least at 1280x800, I have not tried higher resolutions, since that is the native one of the TFT panel), so unless your card is much slower, I don't see problem there, if using the correct driver.

What kind of HDD do you have on that machine? Could very well be a problem with dma being disabled.

---

### Post by Casper Hansen on 2008-09-16
> **Bush_Roo said:**
> 
The on-board graphics card isn't enough to make Compiz run smoothly. A NVIDIA card will help out there and fix the problem right away. Otherwise it is recommended to disable Compiz, and check the performance.


Compiz runs smoothly on my laptop with an X3100 onboard card.

---

### Post by thiebaude on 2008-09-16
Try fluxbox

---

### Post by Casper Hansen on 2008-09-16
> **brdokoky said:**
> When you want to speed up ubuntu , tray to install ubuntu on reiserfs. Ext3 is too slow.

Just hope it doens't kill you... Sorry couldn't resist!

---

