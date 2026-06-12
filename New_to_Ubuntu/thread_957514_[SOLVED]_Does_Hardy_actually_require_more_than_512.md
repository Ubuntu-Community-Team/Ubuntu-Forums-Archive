---
title: "[SOLVED] Does Hardy actually require more than 512MB memory?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Udibuntu on 2008-10-24
Hi,

After installing Hardy I realize my system works slower than the previous Feisty - app's are starting and shutting down slower, fan works harder, CPU seems to struggle a bit, etc.

I disabled effects and compiz is unchecked, AFAICT.

Can I boost performance and make Hardy work smoothly or must I buy a larger memory?

I use Thinkpad R60e with Intel Centrino Duo 1.66 GHz, Front side bus: 667 MHz, and 512 MB PC2-5300 DDR2 SDRAM.

Please advise.

Thanks,

Udi

---

### Post by alphaniner on 2008-10-24
For what it's worth, I have 1.5 GB RAM and I also experienced worse performance with Hardy than Gutsy.  But on another machine with roughly the same specs it runs beautifully.

---

### Post by Gone fishing on 2008-10-24
I've got Hardy running on some PCs with 256MB - it's not speedy but it works

---

### Post by eternalnewbee on 2008-10-24
Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

Hardy Heron. No problem.

---

### Post by philinux on 2008-10-24
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

The OP is above the recommended minimum but more memory would help, especially if you got integrated graphics.

Have a look using the top command, to see whats eating resources.

---

### Post by blackened on 2008-10-24
> **eternalnewbee said:**
> Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz **256 KB**
GeForce 7300 GT

Hardy Heron. No problem.

I'm assuming you meant **MB** :)

Granted I'm on Intrepid, but even with compiz enabled I average <400MB without buffers and cache added in. If this is the case with Hardy, then that only leaves you 112MB of freeboard for preloading applications and such. Under load you are probably swapping like crazy which, given the slow speed of laptop drives, would explain the lethargy in starting and shutting-down programs.

I would try to disable as many unnecessary applications/services as possible. What these would be depends on your system and what you use it for.

---

### Post by Crandom on 2008-10-24
The performance is better in intrepid than hardy, I can tell you that :-)

---

### Post by pluckypigeon on 2008-10-24
> **Crandom said:**
> The performance is better in intrepid than hardy, I can tell you that :-)

I wish I could

---

### Post by Udibuntu on 2008-10-24
Thanks all for the perspective.

Regarding swap - I really have noticed HDD working harder with Hardy (no pun intended...), so extra swapping sounds reasonable.

I'm currently running TB2 and FF3, and swap is at 21 percent, memory is at 76 percent, if that's of any significance. Is there more data I can make decisions upon?

How about cutting unnecessary processes? is there a guide on how to do it safely?

Cheers again,

Udi

---

### Post by Crandom on 2008-10-24
> **pluckypigeon said:**
> I wish I could
You can; just lie. (I'm telling the truth :-))

OP, you could try this guide: [http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

---

### Post by eternalnewbee on 2008-10-24
> I'm assuming you meant MB :
This is what I meant.

---

### Post by eolson on 2008-10-24
I'd opt for the swap .... I have an old system with 568M and it shows 4 percent swap so a 512M system will be using quite a bit more swap. The system I am using with 2G shows zero swap.

---

### Post by jerome1232 on 2008-10-24
> **eternalnewbee said:**
> :
This is what I meant.

I've never seen anyone mention their L2 cache before :) I think FSB would be more important than that.

---

### Post by Therion on 2008-10-24
> **jerome1232 said:**
> I've never seen anyone mention their L2 cache before :) I think FSB would be more important than that.
Mmmm... Tough call, that one.  I'd have a hard time coming down on one side or the other (on L2 vs FSB).  All that being said, if pressed for an answer, I'd have to go with FSB as well though.  Maybe... Ack!  I dunno... To hard to call.  My brain is now in total "vapor-lock" over this conundrum!  I hope you're happy!

:wink:

---

### Post by Udibuntu on 2008-10-24
> **Therion said:**
> Mmmm... Tough call, that one.  I'd have a hard time coming down on one side or the other (on L2 vs FSB).  All that being said, if pressed for an answer, I'd have to go with FSB as well though.  Maybe... Ack!  I dunno... To hard to call.  My brain is now in total "vapor-lock" over this conundrum!  I hope you're happy!

:wink:

Uh, can this help me in any way?:rolleyes:

---

### Post by Therion on 2008-10-24
> **Udibuntu said:**
> 

Uh, can this help me in any way?:rolleyes:


No; not that I can see.  It **IS** an interesting question though and has the potential for keeping me awake this evening whilst I ponder the implications.

Why do you ask about your L2 cache, anyway?  It's not like you can buy more.  You'd need to upgrade your processor to increase the amount onboard L1/2/3 cache.  More is better though.  Always.

---

### Post by LowSky on 2008-10-24
I would find out what application are starting at bootup, remove things you dont use like bluetooth support if you dont use them often. the less things being loaded mean more RAM availible., which would use less swap. Also switching to another GUI like Xubuntu or IceWM, or Fuxbox woill save some RAM space as well. Personally I have an old laptop running on 256RAM and a 1Ghz processor, it isn't dfast but it work fine enough whne I cut dont the app loading on start up.. Also since its a laptop turn off speedstepping when its plugged in. This way the computer doesn't throttle the processor speed, you should be able to do that from the BIOS.

Good Luck

---

### Post by jerome1232 on 2008-10-24
> **Udibuntu said:**
> Uh, can this help me in any way?:rolleyes:

Probably not but I don't think your issues are ram related. I

I just knocked myself down to 512 MB of ram and everything is fine, It does take a bit longer to load apps but I'm guessing it's because there's not much ram left for cache and preloading. I'm not noticing anything going 'slow' though. Login was snappy, nearly probably about 4-5 seconds 'till I could open firefox, instant open, opened rhythmbox probably took 3-4 seconds to open. Compiz is on.

So to sum it up seems like it's enough ram to function just fine, I'm not swapping, just not enough to maintain a decent cache. Note I'm running 64bit so ram issues are actually worse for me as 64 bit uses a little bit more ram than 32 bit would.

This is on 8.10 x86_64 AMD64 3700+ @ 2.4 GHZ, 512 MB SDRAM, Nvidia 5700LE
output of free -m while running rhythmbox, gedit, firefox 2 tabs, and gnome-terminal.

```
             total       used       free     shared    buffers     cached
Mem:           496        489          6          0          6         88
-/+ buffers/cache:        394        101
Swap:         2925         24       2901
```

---

### Post by azebuski on 2008-10-24
I run Hardy Heron on an old Compaq Deskpro Pentium III 450mhz with 256 MB RAM, 6 gig HD, and an old Voodoo3 PCI graphics card.  Of course I can't run compiz or fancy eye candy toys, but the system does what I need wireless internet and all.
With Hardy Heron installed, plus Firefox, Thunderbird, Gimp, OpenOffice 3.0, and tons of other programs I am only using 40% of my little 6 gig HD!  But, as you can tell from my system monitor screenshot, just running firefox causes my CPU to run 90 to 100%. But everything does run fine.

---

### Post by frankleeee on 2008-10-24
> **Gone fishing said:**
> I've got Hardy running on some PCs with 256MB - it's not speedy but it works

I have the same ram but a 1.8 gig cpu no problems.

---

### Post by blackened on 2008-10-24
> **Therion said:**
> Why do you ask about your L2 cache, anyway?  It's not like you can buy more.  You'd need to upgrade your processor to increase the amount onboard L1/2/3 cache.  More is better though.  Always.

S/he didn't, it was just my mistaken understanding of eternalnewbee's post.

**Udibuntu:** It might be easier (and a little more future proof) to upgrade your RAM. A quick search of a site like newegg or tigerdirect will turn up tons of modules priced below $20 US. Your machine is by no means outdated, just a bit thin on resources.

---

### Post by Udibuntu on 2008-10-24
Thanks all for your comments.

I'd appreciate getting tips on how to safely remove unnecessary processes, though I guess I can just Google it up.

> **blackened said:**
> S/he didn't, it was just my mistaken understanding of eternalnewbee's post.

**Udibuntu:** It might be easier (and a little more future proof) to upgrade your RAM. A quick search of a site like newegg or tigerdirect will turn up tons of modules priced below $20 US. Your machine is by no means outdated, just a bit thin on resources.

I didn't, and I'm sure as hell a he...8)

I think getting more RAM, plus removing some stuff will do the trick. BTW, is this also expected next time I upgrade?

---

### Post by Tak11 on 2008-10-24
You might want to make sure all of your drivers are updated/working,

---

### Post by blackened on 2008-10-25
> **Udibuntu said:**
> Thanks all for your comments.

I'd appreciate getting tips on how to safely remove unnecessary processes, though I guess I can just Google it up.

A good place to start would be System->Administration->Services.

> **Udibuntu said:**
> I didn't, and I'm sure as hell a he...8)

I think getting more RAM, plus removing some stuff will do the trick. BTW, is this also expected next time I upgrade?

It's not necessarily expected or required on any machine, but I always do it anyway. I just don't see the point in keeping things running that I either just don't need or never use (especially services I lack the hardware to exploit e.g. bluetooth).

---

### Post by Udibuntu on 2008-10-25
> **Tak11 said:**
> You might want to make sure all of your drivers are updated/working,

Cheers Tak, but I just installed Hardy and checked 151 updates. How do I know if some are outdated?

---

### Post by Udibuntu on 2008-10-25
> **blackened said:**
> A good place to start would be System->Administration->Services.



It's not necessarily expected or required on any machine, but I always do it anyway. I just don't see the point in keeping things running that I either just don't need or never use (especially services I lack the hardware to exploit e.g. bluetooth).

Thanks, though how would I know if processes I kill will not damage my system and/or show themselves again next time I boot? (Bluetooth is disabled since I have a wireless kill switch, which is in the off position).

BTW, if I get more RAM, do I have to enlarge my swap to keep the recommended "swap is 2 times the RAM" ratio? I'm thinking of buying 1G RAM and thus having 1.5 G RAM..

---

### Post by Yashiro on 2008-10-25
Disable tracker (run tracker-preferences) and/or stop the daemon running on startup (run gnome-session-properties).

---

### Post by arheon on 2008-10-25
well,i've got 1.46 C2D,2Gb 667 ram & have ~350mb used O_o 
but it's intrepid beta

---

### Post by Udibuntu on 2008-10-25
> **Yashiro said:**
> Disable tracker (run tracker-preferences) and/or stop the daemon running on startup (run gnome-session-properties).

Thanks. What are the risks and what am I gaining/losing by doing so?

BTW, I do notice my HDD is working extra in short, intensive bursts. My intuition tells me this is swap, am I right?

---

### Post by Kushal Sejwal on 2008-10-25
I agree hardy is more resource hungry than feisty but 512MB is more than for hardy to run smoothly even with Compiz enabled.

Heard Intrepid required less memory than Hardy, so keeping my finger crossed, so that I don't need to buy another RAM :D

---

### Post by Udibuntu on 2008-10-25
> **Kushal Sejwal said:**
> I agree hardy is more resource hungry than feisty but 512MB is more than for hardy to run smoothly even with Compiz enabled.

Heard Intrepid required less memory than Hardy, so keeping my finger crossed, so that I don't need to buy another RAM :D

The whole point in upgrading from Feisty, which I loved, was to enjoy an LTS and better performance... :) So moving to Intrepid is not something I would prefer to do..

I think I'll make a strategic investment and get another 1G RAM in addition to current 512MB.

Any idea on need to change swap to 3G if RAM is 1.5G?

---

### Post by blackened on 2008-10-25
I think common opinion varies on RAM/Swap ratio. From what I've read, swap is necessary if you are on a laptop and hibernate your machine. That said, I have no swap partition: apparently Intrepid doesn't make one by default but goes the way of Windows and uses a swap file. So far I've had no problems hibernating with no swap partition and 2GB of ram, though this will likely not be the case if you *do* already have a swap partition.

Also, if you're planning on adding a 1GB module, then you should make sure that you have only one 512MB module installed instead of 2x256MB.

---

### Post by steveneddy on 2008-10-25
> **Udibuntu said:**
> Thanks all for the perspective.

Regarding swap - I really have noticed HDD working harder with Hardy (no pun intended...), so extra swapping sounds reasonable.

I'm currently running TB2 and FF3, and swap is at 21 percent, memory is at 76 percent, if that's of any significance. Is there more data I can make decisions upon?

How about cutting unnecessary processes? is there a guide on how to do it safely?

Cheers again,

Udi

This would indicate that if you are swapping at 21% then you could benefit from some more RAM.

All operating systems will benefit from more RAM, Ubuntu included.

Any modern OS will probably require more RAM, Hardy included.

RAM is cheap and if you can afford it, double your RAM and see how your PC performs.

---

### Post by Helios1276 on 2008-10-25
> **Udibuntu said:**
> The whole point in upgrading from Feisty, which I loved, was to enjoy an LTS and better performance... :) So moving to Intrepid is not something I would prefer to do..

I think I'll make a strategic investment and get another 1G RAM in addition to current 512MB.

Any idea on need to change swap to 3G if RAM is 1.5G?

1gb Swap should be loads but there are others who would set a more conservative(1.5/2) number.

---

### Post by Udibuntu on 2008-10-26
> **blackened said:**
> I think common opinion varies on RAM/Swap ratio. From what I've read, swap is necessary if you are on a laptop and hibernate your machine. That said, I have no swap partition: apparently Intrepid doesn't make one by default but goes the way of Windows and uses a swap file. So far I've had no problems hibernating with no swap partition and 2GB of ram, though this will likely not be the case if you *do* already have a swap partition.

Also, if you're planning on adding a 1GB module, then you should make sure that you have only one 512MB module installed instead of 2x256MB.

Thanks BE. I do already have a swap partition, and will probably leave it as is and see how performance fares.

Yes, it's a 512MB module installed, I will add a 1024MB next to it. It should be more than enough until I retire Hardy (being an LTS) 2 years from now, if all goes well, that is.

---

### Post by Udibuntu on 2008-10-26
> **steveneddy said:**
> This would indicate that if you are swapping at 21% then you could benefit from some more RAM.

All operating systems will benefit from more RAM, Ubuntu included.

Any modern OS will probably require more RAM, Hardy included.

RAM is cheap and if you can afford it, double your RAM and see how your PC performs.

Answers can't be delivered in a better fashion, Steven - thanks. This is exactly what I'm going to do.

---

### Post by Udibuntu on 2008-10-26
> **Helios1276 said:**
> 1gb Swap should be loads but there are others who would set a more conservative(1.5/2) number.

Thanks Helios, I'll stay with 1G swap and see how id copes with work.

Should I mark this SOLVED or let it hang open for people to comment?

---

### Post by Tak11 on 2008-10-27
> **Udibuntu said:**
> Cheers Tak, but I just installed Hardy and checked 151 updates. How do I know if some are outdated?

check your package manager, for the specific drivers, and install the "non free" ones if any, they handle your hardware better, thought not supported.

---

### Post by Udibuntu on 2008-11-02
Installed another 1G of RAM, working like magic with GE, TB and FF on jobs.

Should I alter swap or am I in the safe zone with 1G of swap?

Cheers,

Udi

---

### Post by ugm6hr on 2008-11-02
> **Udibuntu said:**
> Should I alter swap or am I in the safe zone with 1G of swap?

You only need more swap if you intend to use suspend to RAM.

---

### Post by Udibuntu on 2008-11-02
> **ugm6hr said:**
> You only need more swap if you intend to use suspend to RAM.

i.e Hibernate? due to network manager problems on wake up I seldom use this feature.

Without any app's running on the desktop Hardy required about 560MB of RAM just to be there; I guess I have an answer to my original question.

Thanks.

---

