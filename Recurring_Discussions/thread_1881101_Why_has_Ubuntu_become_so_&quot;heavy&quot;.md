---
title: "Why has Ubuntu become so &quot;heavy?&quot;"
date: 2011-11-14
forum: Recurring Discussions
---

### Post by Randymanme on 2011-11-14
First off let me admit that I'm using a ten year old Dell Dimension 8300 -- kind of shabby on resources, I know.

But it seems like ever since Lucid Lynx was released, Ubuntu has gotten progressively more resource hungry.  Natty and Oneiric just come right and tell me that I don't have the hardware to run Unity.  I have a fresh install of Oneiric that just struggles along.

But here I sit on Ubuntu Forums via Mint 12 RC on Virtualbox 4.1.6 hosted with Mint 11 ME -- and they are both running close to as well as I've ever seen an os run on this machine (with the exception of Lucid Puppy, of course) while equally sharing 1 GB of ram.

What is it that Mint's devs to Ubuntu do that results in its Gnome being so much lighter than Ubuntu's?  Or Super OS?  With the latter, one can add a Super OS package to an already running Ubuntu and give it muscle!  Why doesn't Ubuntu just do what the Super OS devs do?  Maybe it's a matter of Canonical being polite and not stepping on its derivatives' toes.

So why bother with Ubuntu at all?  Super OS and Ultimate Edition are still Ubuntu configured elsewhere.  Mint has improved on Ubuntu and contributed enough of its own innovations to be considered more than just Ubuntu.  In my mind, Ubuntu is like a beautiful woman without make-up, designer clothing, manicure, or trip to the hairdresser. Sort of like Alec Wec standing at a London bus stop just before she was "discovered."

I've just downloaded a version of Oneiric for virtual machines, so I guess it'll behoove me to delete the one I have written to physical disk and use that space to expand my Linux /home partition.

---

### Post by inobe on 2011-11-14
to be honest, in a non sarcastic way, i've become heavier after my thirties, if that means anything.

---

### Post by wolfen69 on 2011-11-15
Why has windows and osx become heavier? Because they can. Windows and Mac users aren't going to complain if they need to spend more time maintaining their OS. It's typical.

---

### Post by Copper Bezel on 2011-11-15
[QUOTE=Randymanme]So why bother with Ubuntu at all? Super OS and Ultimate Edition are still Ubuntu configured elsewhere. Mint has improved on Ubuntu and contributed enough of its own innovations to be considered more than just Ubuntu. In my mind, Ubuntu is like a beautiful woman without make-up, designer clothing, manicure, or trip to the hairdresser. Sort of like Alec Wec standing at a London bus stop just before she was "discovered."[/QUOTE]
Well, you're right at least in the sense that the differences in Mint are cosmetic. = ) I don't know what could cause the difference you're describing, though. Mint 11 *is* Natty.

---

### Post by shuttleworthwannabe on 2011-11-15
Another example of much slicker Ubuntu is PinguyOS--I have been using it on a USB as Live install, and it puts Ubuntu 11.10 (also on USB) to shame--booting is faster, apps load faster, shutdown is faster as well--and note, Pinguy 11.10 alpha comes with all the bells and whistles

---

### Post by FuturePilot on 2011-11-15
Try running Windows 7 on that machine. It will be just as "heavy" as Ubuntu if you could even install it at all. It's not just Ubuntu, it's called software evolution.

---

### Post by nothingspecial on 2011-11-15
Moved to Recurring Discussions.

---

### Post by Randymanme on 2011-11-15
Thank you for the responses.  I've heard of PinguyOS -- I'd seen something to the effect that there was a distro based on Ubuntu and Mint.  I'll download an iso for virtualbox next.

I didn't know how good I was having Oneiric until I began installing it on virtualbox.  First off, it took well over an hour.  And then after restarting, Oneiric creeped along at a snail's pace, as though it were swapping.  The Oneiric I have on physical disk -- I didn't have a blank cd or dvd so I installed Maverick and upgraded until I got to Oneiric.  So I had a lot of packages on an otherwise fresh Oneiric that the fresh iso of Oneiric doesn't have, like, for example, gnome classic and synaptic package manager.

The Oneiric on virtualbox only had two session options: Ubuntu and Ubuntu 2D -- neither of which I have the hardware to run apparently -- even on Virtualbox.  I've read in the Virtualbox help that Virtualbox doesn't need hardware virtualization and that it can present up to 32 processors.  This machine does have hardware virtualization, but I don't know (yet) how to make it virtualize a quad core processor.  I bet that would help.

I couldn't get the Oneiric on vbox to invoke synaptic package manager to save my life -- and each attempt took around 10 mintues.  When I typed in "package manager," it opened Ubuntu Software Center.  It was there that I discovered that synaptic wasn't even installed!  It took Ubuntu Software Center 12 to 13 minutes to install synaptic!  So far, synaptic is the only part of this Oneiric to move fairly quick.  I'm installing, among other things, gnome session, gnome fallback, openbox, and gnome 2.24 suite.  Hopefully things will get faster. 

Needless to say, I'm posting this with the Mint 11 host which is running just fine on 512 MBs of ram.  Oneiric's release notes claim it'll perform adequately on 384 MBs of ram, although it'll take "longer than normal" to install.  I doubt that to be taken literally.

I do have Windows 7 Ultimate on sda -- I rarely use it, only in "must have" situations.  I plan on using a VMware tool I've read about to turn it into a virtual appliance and then run it in a virtual machine.  If Oneiric ran as well as Windows 7, I'd have no complaint.

---

### Post by Copper Bezel on 2011-11-15
> The Oneiric on virtualbox only had two session options: Ubuntu and Ubuntu 2D -- neither of which I have the hardware to run apparently -- even on Virtualbox. I've read in the Virtualbox help that Virtualbox doesn't need hardware virtualization and that it can present up to 32 processors. This machine does have hardware virtualization, but I don't know (yet) how to make it virtualize a quad core processor. I bet that would help.
Virtualbox doesn't support hardware-accelerated video for Linux guests. You're stuck using Unity 2D and Gnome Fallback that way.

I'm shocked by how painfully slow the Software Center is every time I launch it. I assume it's a temporary problem, since it wasn't the case in Natty. Still, it's a bear. I really wanted to see how long I would last using it rather than falling back to Synaptic, gdebi, and apt-get on my 11.10 install, but since the issue with Google Chrome being read as a broken package and rejected by the Software Center still hasn't been fixed, that was five minutes, most of which was waiting for it to load. = ) (I don't really care whether the problem is on Google's end. It's not acceptable for that problem to persist over two releases without Ubuntu doing something about it.)

---

### Post by jjex22 on 2011-11-15
When wasn't it? it's one of the main full desktop linux. Ive been using since 9.10 (okay the last 2 weeks of 9.10 - that's when I learned about 6 month cycles!) it's the beauty of Linux - we have distro's aimed at all purposes and the large full desktop editions should aim to be the cutting edge of what linux can do... or what's the point? 

The great thing we have with linux is that you can change your desktop environment to give your computer some breathing room in ram and graphics. On old or limited hardware we have xubuntu, lubuntu etc, or all kind of ubuntu based resource light distros at distrowatch... you can even select 2D mode in the current release (my choice when on my netbook) The spectrum of hardware you can run ubuntu on is massive especially compared to mac and windows to which it is compared (as I have learned the hard way mac just cut support for your hardware off after a few years - always a risk when your os is made by the same company as your hardware.) 

Also it's based on debian which boasts 29000 packages as soon as you get to their site (aparently they lost over 1000 over the summer... careless)It is getting harder to run full blown ubuntu on my older/limited hardware, but I expect this to happen, my emac can't run snow leopard, my old mac can't run tiger, and that grey win 98 box in the loft will not run windows 7!

But they will all run a currently available linux

---

### Post by JayKay3OOO on 2011-11-15
Sign of the times man.

Computers get faster, games look better and video goes higher quality and bigger file size.

OS simply aims to make the most of new hardware. A 10 year old machine is like a fossil in computing terms.

Thankfully for people who hate upgrading there are plenty of other distributions and versions of Ubuntu that cater for old hardware.

---

### Post by beew on 2011-11-15
That is called progress. Hardware is becoming cheaper and more powerful and as a full featured Desktop OS it is right for Ubuntu to take advantage of it, and it is still very light weight comparing to Windows. You can't expect an actively developing OS with an eye towards the future to use 10 year old antique hardware as it bench mark.
> 
  Mint has improved on Ubuntu and contributed enough of its own  innovations to be considered more than just Ubuntu.  In my mind, Ubuntu  is like a beautiful woman without make-up, designer clothing, manicure,  or trip to the hairdresser. Sort of like Alec Wec standing at a London  bus stop just before she was "discovered."

Mint = Ubuntu with  a Windows 95 wanable look + some codecs. Your woman comparison is not only sexist, it is completely off base, Ubuntu is way more glamorous than Mint.

---

### Post by BrokenKingpin on 2011-11-15
I have noticed the same thing. I have since switched to Xubuntu and an very happy with the performance, and looks just as nice as Ubuntu in my opinion. It really does balance features/looks with performance very nicely.

Xubuntu runs perfectly fine on my netbook, which is a few years old. Ubuntu or Kubuntu run like crap on it.

---

### Post by FuturePilot on 2011-11-15
> **Randymanme said:**
> Thank you for the responses.  I've heard of PinguyOS -- I'd seen something to the effect that there was a distro based on Ubuntu and Mint.  I'll download an iso for virtualbox next.

I didn't know how good I was having Oneiric until I began installing it on virtualbox.  First off, it took well over an hour.  And then after restarting, Oneiric creeped along at a snail's pace, as though it were swapping.  The Oneiric I have on physical disk -- I didn't have a blank cd or dvd so I installed Maverick and upgraded until I got to Oneiric.  So I had a lot of packages on an otherwise fresh Oneiric that the fresh iso of Oneiric doesn't have, like, for example, gnome classic and synaptic package manager.

The Oneiric on virtualbox only had two session options: Ubuntu and Ubuntu 2D -- neither of which I have the hardware to run apparently -- even on Virtualbox.  I've read in the Virtualbox help that Virtualbox doesn't need hardware virtualization and that it can present up to 32 processors.  This machine does have hardware virtualization, but I don't know (yet) how to make it virtualize a quad core processor.  I bet that would help.

I couldn't get the Oneiric on vbox to invoke synaptic package manager to save my life -- and each attempt took around 10 mintues.  When I typed in "package manager," it opened Ubuntu Software Center.  It was there that I discovered that synaptic wasn't even installed!  It took Ubuntu Software Center 12 to 13 minutes to install synaptic!  So far, synaptic is the only part of this Oneiric to move fairly quick.  I'm installing, among other things, gnome session, gnome fallback, openbox, and gnome 2.24 suite.  Hopefully things will get faster. 

Needless to say, I'm posting this with the Mint 11 host which is running just fine on 512 MBs of ram.  Oneiric's release notes claim it'll perform adequately on 384 MBs of ram, although it'll take "longer than normal" to install.  I doubt that to be taken literally.

I do have Windows 7 Ultimate on sda -- I rarely use it, only in "must have" situations.  I plan on using a VMware tool I've read about to turn it into a virtual appliance and then run it in a virtual machine.  If Oneiric ran as well as Windows 7, I'd have no complaint.

Now I'm confused. You say this computer is 10 years old but it has a quad core processor in it?

> **Copper Bezel said:**
> Virtualbox doesn't support hardware-accelerated video for Linux guests. You're stuck using Unity 2D and Gnome Fallback that way.

Yes it does.

---

### Post by Copper Bezel on 2011-11-15
I stand corrected. I had no idea. When did that happen? I remember there being an issue with this re: Unity.

---

### Post by collisionystm on 2011-11-15
> **wolfen69 said:**
> Why has windows and osx become heavier? Because they can. Windows and Mac users aren't going to complain if they need to spend more time maintaining their OS. It's typical.


Windows 7 being what it is is actually pretty fast for the amount of processes that run on it. 

I remember on XP I always had my system running with no more than 19. Now-a-days thats just impossible. :(

---

### Post by KiwiNZ on 2011-11-15
You cannot have it both ways, that is light weight and catering for every PC since Methuselah.

Your PC is 10 years old, it has 1GB of Ram and a 80GB HDD, run on it that for which is was designed, a 10 year old OS or a minimalist OS. 

Your issue is not indicative of Ubuntu 11.10 or any modern OS.

---

### Post by snowpine on 2011-11-15
"Distro X is slow in VirtualBox" tells you more about VirtualBox than Distro X. If a distro is brand new (like Ubuntu 11.10) it will take a little while for the VirtualBox developers to support it. You'll get the most accurate assessment of a distro's speed (especially a distro released in the last 6 months) by actually installing it on physical hardware.

That being said, nobody really considers Unity "lightweight" so don't be too quick to judge it on that criterion (especially if you have an unsupported graphics card). That's like complaining your Hummer gets bad gas mileage. :) Xfce, LXDE, Fluxbox, etc. are always available and supported as lightweight options. Not to mention CrunchBang, AntiX, Puppy, SliTaz, Tinycore, etc... :)

---

### Post by dh04000 on 2011-11-15
OP:
My parents have a P4 machine with 768mb ram (333), a 120 GB hardrive, and a nvidia card that was middle range for the time. Ubuntu 11.10 runs fine on it. If your having an issue, try to upgrade your GPU, since I bet that would be the performance bottle neck on that system.

I'm typing fro a Generation 1 intel atom N270, which is equal to a really fast P3, so the CPU is not the limit in your system by any stretch, which suggests the GPU is the issue.

Good Luck.

---

### Post by Randymanme on 2011-11-16
No, my 8-year old Dell isn't quad-core (I thought 10 years old, but, no, eight).  I've read in the Oracle VM VirtualBox User Manual, Version 4.0.6 Edition. Copyright © 2004-2011 Oracle Corporation.  [http://www.virtualbox.org](http://www.virtualbox.org).  In Chapter one, First Steps and in section 1.3, Features Overview, the following: 

Great hardware support. Among others, VirtualBox supports:


[LIST]
[*]No hardware virtualization required.  For many scenarios, VirtualBox does not require the processor features  built into newer hardware like Intel VT-x or AMD-V. As opposed to many  other virtualization solutions, you can therefore use VirtualBox even on  older hardware where these features are not present. The technical  details are explained in [[COLOR=#0000ff]_Section 10.3, “Hardware vs. software virtualization”_[/COLOR]]("http://ubuntuforums.org/ch10s03.html").
[/LIST]

[LIST]
[*] Guest multiprocessing (SMP).  VirtualBox can present up to 32 virtual CPUs to each virtual machine,   irrespective of how many CPU cores are physically present on your host.
[/LIST]
I haven't seen how to accomplish that just yet, but I'm hoping to work up to it.  As I have it in my mind; the typical, 8 to 10 year old budget gaming computer is all I'll ever need sol long as I can learn what to do with it.  As it is, the 30,000+ software packages available to Ubuntu users are far more than I'll ever dream of making proper use of even if I live to be 100.

I was reading just yesterday on the Ultimatix website where Thee Mahn wrote last March that " . . both [Ultimate Edition]("http://ultimateedition.info/") 1.8+ x86 / x64, as well as the Gamers edition of the same, also x86 based, are 
**intended to run on [Ultimate Edition]("http://ultimateedition.info/") 1.8+ / UBUNTU 8.04+ / Debian (untested)**."   Now that's what I'm talking about.  Were I to ever get good at this stuff, Hardy and this computer are all I'll ever need.

Cheers  


[[COLOR=#0000FF]__[/COLOR]]("http://ubuntuforums.org/ch01.html")[[COLOR=#0000ff]__[/COLOR]]("http://ubuntuforums.org/ch01s03.html")p, li { white-space: pre-wrap; }    p, li { white-space: pre-wrap; }

---

### Post by Gatemaze on 2011-11-16
For a lighter system use xubuntu, lubuntu or another lighter distro. Ubuntu is trying to take advantage of latest hardware developments like all other main operating systems do.

---

### Post by snowpine on 2011-11-16
> **Randymanme said:**
> Were I to ever get good at this stuff, Hardy and this computer are all I'll ever need.

Hardy is end-of-life and completely unsupported, sorry. :(

---

### Post by haqking on 2011-11-16
> **Copper Bezel said:**
> [B]Virtualbox doesn't support hardware-accelerated video for Linux guests. You're stuck using Unity 2D and Gnome Fallback that way.
[/B]
I

I have 11.10 in a virtual machine in Vbox running Unity 3D and have done since 11.10 was released

---

### Post by shuttleworthwannabe on 2011-11-17
> **Gatemaze said:**
> For a lighter system use xubuntu, lubuntu or another lighter distro. Ubuntu is trying to take advantage of latest hardware developments like all other main operating systems do.

This is inevitable and sound approach--But a good one will use resources efficiently; not hog all the available resources. Point in case is OS X and Windows 8 (DP)--you will notice how quick and agile these systems are, not slow as molasses. Ubuntu 'used' to be quick and agile, and I beleive can do too--take a look at PinguyOS 11.10 beta; this has the same codebase as Ubuntu, but performs much better than mother Ubuntu, uses less RAM on initial boot with no apps open (just about 450MB on my system).

---

### Post by nixblog on 2011-11-17
> **Gatemaze said:**
> For a lighter system use xubuntu, lubuntu or another lighter distro. Ubuntu is trying to take advantage of latest hardware developments like all other main operating systems do.

Yep, but not everyone has the latest Intel Core I9 with 16GB RAM. However, as you stated, the beauty of Linux is that if Ubuntu doesn't fit the bill then something else will.

---

### Post by beew on 2011-11-18
> **nixblog said:**
> Yep, but not everyone has the latest Intel Core I9 with 16GB RAM. However, as you stated, the beauty of Linux is that if Ubuntu doesn't fit the bill then something else will.

 Let's not exaggerate.

 I tested Ubuntu 11.04 on a 6 year old Dell D410 with single core and 1 G of ram  and a stock Intel graphic card. It is quite fast and smooth, I get Unity 3d after the first post install update  (though Xubuntu not surprisingly performs even better on such specs). Usually people having problems with Ubuntu resource wise are people with 8- 0 year old antique machines. The complaints about Ubuntu's resource requirements are usually coming from these people (probably the same people who still complain about grub2 and advise new users to rip out pulseaudio as the first thing to do after installing Ubuntu and then leave them wondering why sound is broken) These complaints are then repeated by others uncritically. 

Ubuntu is a modern full feature OS and it should not be benchmarked by 10 year old standard, for people with such machines they always have other choices in the Linux world.

---

### Post by Randymanme on 2011-11-21
> **snowpine said:**
> Hardy is end-of-life and completely unsupported, sorry. :(

Sounds like you've not heard of Kubuntu Trinity.  
[https://wiki.kubuntu.org/Kubuntu/Kde3/Lucid](https://wiki.kubuntu.org/Kubuntu/Kde3/Lucid)

My point is that just because Canonical doesn't support a particular release doesn't necessarily mean that it won't get supported.  I think it's safe to say that Ultimatix will provide support for any of its releases based on Hardy that it's still releasing packages for.

---

### Post by snowpine on 2011-11-21
> **Randymanme said:**
> Sounds like you've not heard of Kubuntu Trinity.  
[https://wiki.kubuntu.org/Kubuntu/Kde3/Lucid](https://wiki.kubuntu.org/Kubuntu/Kde3/Lucid)

My point is that just because Canonical doesn't support a particular release doesn't necessarily mean that it won't get supported.  I think it's safe to say that Ultimatix will provide support for any of its releases based on Hardy that it's still releasing packages for.

Ubuntu 8.04 Hardy is "end of life" since April 2011 (except servers) and your link confirms this by suggesting users upgrade to 10.04. :)

---

### Post by ratcheer on 2011-11-21
IMHO, the answer to the original question is that Ubuntu wants to compete with Windows for market share.

Personally, I appreciate the idea of "light" OS's and I am trying to use Arch Linux in pursuit of that ideal. However, I find it quite difficult to get things done in Arch because, to keep things simple, they make things difficult. So, I still spend 95% of my time in Ubuntu.

Both approaches have their pros and cons.

Tim

---

### Post by 3rdalbum on 2011-11-23
> **beew said:**
> (probably the same people who still complain about grub2 and advise new users to rip out pulseaudio as the first thing to do after installing Ubuntu and then leave them wondering why sound is broken)

I thought I was the only one who noticed that; new user posts something like "How can I tell Skype to use my headset microphone instead of my webcam microphone" and somebody tells them to remove Pulseaudio; then the poor newbie posts back "I've done that, but now I don't have any sound at all!" and by this time the helpful advisor has disappeared, presumably back to their Hardy or Jaunty system.

This annoys me even more than "Oh, your wireless says that the firmware is missing? You need to remove Network Manager and install Wicd instead. Network Manager sucks." and the inevitable "Okay, done that, but Wicd reports firmware missing as well, and now I've lost my wired connection too!" reply.

Sorry to go off-topic here, but I was just surprised that someone else noticed the "remove Pulseaudio to fix your problems" brigade.

---

### Post by Randymanme on 2011-11-23
[SIZE=2]> **beew said:**
> 
I tested Ubuntu 11.04 on a 6 year old Dell D410 with single core and 1 G of ram and a stock Intel graphic card. It is quite fast and smooth, I get Unity 3d after the first post install update (though Xubuntu not surprisingly performs even better on such specs). Usually people having problems with Ubuntu resource wise are people with 8- 0 year old antique machines. 

Ubuntu is a modern full feature OS and it should not be benchmarked by 10 year old standard, for people with such machines they always have other choices in the Linux world.

Presently, I'm making this post with Oneiric, Ubuntu desktop.  I have Xubuntu, Xfce session, Gnome, Gnome Classic, Gnome/Openbox,  Ubuntu, and Ubuntu 2D to choose from.  The only one that doesn't  work very well is Gnome (but it begins to work okay after I select “Openbox session, the only problem with that, though, is having to wait a long time for the desktop to open, first).  After reading a Lubuntu review that concluded that Lubuntu was only marginally faster than Ubuntu and that it utulized an awful lot of xfce packages in spite of claiming to be based on lxde, I decided not to try Lubuntu.  [/SIZE] 
 

 [SIZE=2]I ended up “throwing in the towel” on my previous Oneiric; I deleted it and re-installed Maverick.  I played around with Maverick until I broke it (trashed it, more like).  I'd gotten the idea, after browsing through Pinguy's packages and etc/sources.list, to get different packages from different Ubuntu's and  derivative's repositories and see what I might come up with.  Gradually, it seemed to me that the right, optimum, mix of Openbox and OpenGL packages could go a long way towards eliminating Ubuntu bloat (Ubuntu bloat is not nearly as burdensome as KDE bloat; I keep KDE packages down to a minimum).  But after doing so, I realized that I'd forgotten to use the Linux /home on this computer for Maverick's /home, so I deleted Maverick and re-installed another one utilizing Linux /home.  I played around with  that one for a few hours before deciding to upgrade to Natty.  Natty was cool (that one), but I decided to try to install Gnome 3 session to it.  It seems that the Maverick upgrade tool “observes” that my computer doesn't have the hardware to run Unity and doesn't bother to put it on![/SIZE]
 

 [SIZE=2]Well, Unity didn't work very well at all on Natty.  I decided that Oneiric couldn't be any worse and that with the inclusion of of some Openbox and OpenGL packages, it might work pretty good.  So I upgraded to Oneiric.  And I'm rather pleased with it, now that it works on this computer. I don't see much difference between Ubuntu and Ubuntu 2D; Ubuntu is slower but smoother.  Gnome classic with the Openbox session enabled is as fast as Maverick was.  I wish I could select an openbox session with Ubuntu or Ubuntu 2D.  Perhaps some could tell me how to do that.[/SIZE]
 

 [SIZE=2]I read that Ubuntu Studio uses Xfce for its default desktop.  That ought to be fun.  I installed it with synaptic, but so far it's not listed under options on the login page.  Perhaps someone could help me with that.[/SIZE]
 

 [SIZE=2]I happened to run across a post in Ultimate Edition Forums; below is the poster's signature.  I figured that if he can run those OSes with a  Pentium 4 processor and one GB of ram, I can run Ubuntu 11.10 with the same.  It's just a matter of me learning how to best utilize what I have.[/SIZE]
 

 [SIZE=2][COLOR=#0040ff]**JOHNNYG**[/COLOR]
[IMG]http://i52.tinypic.com/j11wgk.gif[/IMG]
[COLOR=#0000ff]Ultimate Edition[/COLOR]
[COLOR=#ffbf40]Ultimate Edition STUDIO[/COLOR]
[COLOR=#4000bf]Onyx 64[/COLOR]
[COLOR=#bf40bf]Ubuntu Precise Pangolin[/COLOR][COLOR=#bf40bf] [/COLOR]
Custom tower
Intel Pentium 4 processor
2x512 Kingston DDR memory w/cooling fins
Maxtor Diamondmax 200 gig/Maxtor maxline 80 gig
ATI 9600 series (RV350 AQ)graphics card
Sony DVD/CD Rewritable Drive DOUBLE LAYER DRU-820A/Sony DRU-800A CD DVD±RW Dual DVD Recorder [/SIZE] 
 

 [SIZE=2]Cheers[/SIZE]

---

### Post by Linuxratty on 2011-11-29
Ubuntu is heavy? I never noticed.

---

