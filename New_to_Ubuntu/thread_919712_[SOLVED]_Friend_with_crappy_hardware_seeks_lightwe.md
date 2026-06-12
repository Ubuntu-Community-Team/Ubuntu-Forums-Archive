---
title: "[SOLVED] Friend with crappy hardware seeks lightweight OS..."
date: 2008-09-14
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-14
...can you all help me recommend an OS?  

She's got a laptop with a P3 at 866Mhz, 384MB RAM, and  a 30 GB HD.  Do you all think she could run Ubuntu?  If so, is there a way to get KDE running on it?  This is my business partner, and I'm trying to get her used to the OS and DE we'll be using in our company, and we can't afford to buy her new hardware just yet.  Regardless, some *NIX flavor is needed to give her hunk-of-junk portable hard drive some new life.  Ideas?  Recommendations?  Derison?

---

### Post by northern lights on 2008-09-14
384 megs of RAM are the official minimum system requirement for Hardy and Intrepid.

Still, I'd recommend Xubuntu, if your friend plans on running a decent amount of applications simultaneously.

---

### Post by OutOfReach on 2008-09-14
It could probably run Ubuntu, but it will get a little slow. How about [Crunchbang Linux]("http://crunchbang.org/")? or Xubuntu?

---

### Post by Mornedhel on 2008-09-14
> **tarahmarie said:**
> Derison?

Well, you *are* using "KDE" and "lightweight" in the same sentence.

More seriously, the distributions run like this (keeping in mind this is a Ubuntu-centric forum), in a more-resource-consuming to less-resource-consuming order :

Kubuntu -> Ubuntu -> Xubuntu -> Fluxbuntu -> Puppy Linux -> Damn Small Linux

---

### Post by houbysoft.xf.cz on 2008-09-14
> **tarahmarie said:**
> ...can you all help me recommend an OS?  

She's got a laptop with a P3 at 866Mhz, 384MB RAM, and  a 30 GB HD.  Do you all think she could run Ubuntu?  If so, is there a way to get KDE running on it?  This is my business partner, and I'm trying to get her used to the OS and DE we'll be using in our company, and we can't afford to buy her new hardware just yet.  Regardless, some *NIX flavor is needed to give her hunk-of-junk portable hard drive some new life.  Ideas?  Recommendations?  Derison?

Yeah, Xubuntu. Or Windows 2000 :lolflag:

---

### Post by wawadave on 2008-09-14
i have hardy running on 1200mhz with 256megs of ram.

it gets slow at times do to limited ram. your specks will do just fine for current ubuntu

you can add kde through synaptic package manager.

---

### Post by lswb on 2008-09-14
That system isn't so bad. I've had ubuntu hardy running on an old thinkpad 600E 366 Mhz pentium 2 with 288 MB memory, not recommended :) 

I also have hardy installed on an old compaq armada with a Pentium3 650Mhz, though with 512MB memory. The armada works just fine. I would say try ubuntu or kubuntu first, if it seems too slow, then switch to xubuntu.

---

### Post by starcannon on 2008-09-14
Xubuntu would run very sweetly on that system. If you can get her up to 512mb of RAM then Ubuntu, Kubuntu would also run very sweetly. As has been stated earlier, Ubuntu and Kubuntu will run on those specs, but it is a little anemic and might be a bit sluggish. I'd load Xubuntu if it were my friend.

GL and have fun.

---

### Post by tarahmarie on 2008-09-14
> **starcannon said:**
> Xubuntu would run very sweetly on that system. If you can get her up to 512mb of RAM then Ubuntu, Kubuntu would also run very sweetly. As has been stated earlier, Ubuntu and Kubuntu will run on those specs, but it is a little anemic and might be a bit sluggish. I'd load Xubuntu if it were my friend.

GL and have fun.

Awesomeness.  She works at Best Buy; I bet she could pick up laptop memory out of the dang trash for that system.  So far, I'm thinking Xubuntu; she doesn't really do anything with puters like I do (she's the money, I'm the machines ;-), so a machine that has wi-fi, browses, prints things, and has desktop wallpaper she can change is all she needs right now.  When we can upgrade her, I'll pimp her DE like mine (KDE4, compiz, emerald, superkaramba, much coolness), and another convert will be born!

---

### Post by kk0sse54 on 2008-09-14
A net or minimal  install of pretty much any distro along with a light Windows Manager ,Openbox or Fluxbox etc etc, would work well in her situation. As for a Ubuntu based distro I would recommend either Xubuntu or Fluxbox both which would probably work just fine.

---

### Post by R_T_H on 2008-09-14
Vector Linux is quite good; a Slackware based system. Faster, perhaps, than Xubuntu. However, Xubuntu has the advantage of not using slapt-get (a total abomination ;)) for package management. The repos for *ubuntu are also huge, and quite up to date.

---

### Post by liquidfunk on 2008-09-14
A net install of Debian, with XFCE is a good choice I think. Either that or I'd recommend TinyME (PcLinuxOS based) or Crunchbang!

---

### Post by northern lights on 2008-09-14
While all of the possible distributions posted undoubtedly have their unique advantages, let me try to make a convincing case for Xubuntu:

Since the preconditions are a Linux convert getting her first distribution and her comp being a P3 866 MHz with 384 megs of RAM (which is not that ancient) this is why I believe Xubuntu to be the perfect choice:

Within the Ubuntu family, Fluxbuntu might be even more lightweight, but is of course naturally also even slimmer. Fluxbox is, especially graphically, not as powerful as XFCE. Since Xubuntu would mean no lesser performance it makes sense to pick it over Fluxbuntu.

Further within the family, both Kubuntu and Ubuntu would run on the system. The never ending KDE vs. GNOME discussion aside, either would already use up a considerable amount of system resources. Vista, for instance, will also run on an Athlon XP 1500 with 512MB RAM - just that a browser or a media player will then already have the CPU and the memory at 90+% usage. So for the sake of not writing to SWAP within an hour of uptime, Xubuntu should be picked over (K)Ubuntu.

If you were looking for a distribution that runs on a mid-nineties 386 architecture with 16MB EDO RAM, Damn Small Linux would be a great choice. On the laptop in question such slickness is not necessarily required.

As an aside, I like Puppy and Slackware, I never ran Vector Linux or some of the other distribution that might have been mentioned. Still to sum up the case against any non Ubuntu family distribution:
There are distributions (Arch for instance) with way more up-to-date repositories than Ubuntu. However Ubuntu repositories are updated frequently and never far from the latest releases while balancing this with stability concerns. If you're looking for the lowest possible amount of maintenance work, updating from the Ubuntu repositories is a good start.
It's the same story with an easy install and configuration process.
Further, since, as with any OS and/or Linux distribution, you will eventually run into a problem you can't solve on your own, Ubuntu is amongst the candidates for best non-commercial support (Amazingly active forums, Launchpad).

I think that's it for now, but I'm sure this can be extended...         ;)

---

### Post by bobpur on 2008-09-14
I was wondering when someone was going to suggest maxing the RAM in that laptop. I read down as far as Starcannons post to see that someone did.
You might try [www.crucial.com](www.crucial.com). Their sight has a memory configurator that will tell you how much of which kind of RAM that machine will hold. All you need is some basic info about the machine in question.
[www.newegg.com](www.newegg.com), also, has a memory configurator but might not go back to some older machines.
Oh Yeah, My vote for a lightweight OS is LinuxMint. Either the Mint KDE Community Edition or the Mint XFCE Community Edition. Both are based on Kubuntu and Xubuntu respectively.

Good Luck.

---

### Post by tarahmarie on 2008-09-14
Ok, so I'm definitely going to go with Xubuntu for my friend.  Now, I can walk her through burning the distro to CD, formatting and installing, but the one thing I want to make sure she has (that she doesn't know she needs yet) is a separate home partition.  For those of you who have tried Xubuntu, is the creation of a separate home partition idiot-proof?  I'm going to have her backup all her data and fully format the HD, so what's the best way to guarantee the proper formation of a root/swap/home partition system for her machine?  Also, given that she's got a 30GB HD, what do you all think the optimal sizes for each partition would be?  Say, 6GB/2GB/22GB?  Accept the default options?

I'm in a different state from her right now, so I need to be able to explain what she's supposed to do over the phone.

---

### Post by starcannon on 2008-09-14
> **tarahmarie said:**
> Ok, so I'm definitely going to go with Xubuntu for my friend.  Now, I can walk her through burning the distro to CD, formatting and installing, but the one thing I want to make sure she has (that she doesn't know she needs yet) is a separate home partition.  For those of you who have tried Xubuntu, is the creation of a separate home partition idiot-proof?  I'm going to have her backup all her data and fully format the HD, so what's the best way to guarantee the proper formation of a root/swap/home partition system for her machine?  Also, given that she's got a 30GB HD, what do you all think the optimal sizes for each partition would be?  Say, 6GB/2GB/22GB?  Accept the default options?

I'm in a different state from her right now, so I need to be able to explain what she's supposed to do over the phone.

No, its not idiot proof, if you delete the wrong partition.... poof its all gone.

---

### Post by tarahmarie on 2008-09-14
I'm going to have her format her hard drive; I'll be able to have her create the partitions during install.  Googling "xubuntu partition creation" leads me to some other threads here, but none tell me whether xubuntu is 'smart' about partition creation, i.e. does it automatically select the correct size for root/swap, and create the third data partition with the rest of the HD and automatically mount that partition as home?  If it is smart about that, I can just tell my friend to use the default option when formatting/installing with her xubuntu live disk.

---

### Post by Sef on 2008-09-14
> I'm going to have her format her hard drive; I'll be able to have her create the partitions during install. Googling "xubuntu partition creation" leads me to some other threads here, but none tell me whether xubuntu is 'smart' about partition creation, i.e. does it automatically select the correct size for root/swap, and create the third data partition with the rest of the HD and automatically mount that partition as home? If it is smart about that, I can just tell my friend to use the default option when formatting/installing with her xubuntu live disk.

To set up a home partition requires manually partitioning the hard drive.  It is not that hard, but it can be frustrating the first time.

---

### Post by halitech on 2008-09-14
> **liquidfunk said:**
> A net install of Debian, with XFCE is a good choice I think. Either that or I'd recommend TinyME (PcLinuxOS based) or Crunchbang!

+1 on the net install of Debian with XFCE. I just set up an old Toshiba (p266 with 96meg of ram) using the net install and added XFCE after I had the rest done and for the age of the machine, it actually works well and surprised me. If my Compaq Armada M700 hadn't died, it was getting the same treatment. I've also done that install on a P3 866 with 256 and it runs very nicely on a 10gig drive.

---

### Post by Greyed on 2008-09-14
I actually recommend against XUbuntu at this time. Unless the huge memory leak has been fixed.  I had to switch from XFCE to KDE because KDE used less memory after about 1-2 hours of usage.  No joke.

I'm running KUbuntu 8.04 (KDe 3.5.10, not 4.1) on a PIII 667Mhz machine with 256Mb of RAM.  It can handle Firefox/Thunderbird/Pidgin all at the same time with no swap.  Well, no swap unless I open like 30 web pages at the time which I sometimes do.  If I want to use OOo I have to close down TBird or Firefox and even then there is some swapping.  However, her machine has 128Mb more RAM and my swap never gets over 90Mb so she might be good.

Actually I just realized I know she'd be good.  I am running KUbuntu 8.04 (KDE 4.1) inside a VBox VM w/384Mb of RAM and haven't had any problems with it so far.

```
{grey@igbuntu:~} free
             total       used       free     shared    buffers     cached
Mem:        385536     380340       5196          0       3152     157244
-/+ buffers/cache:     219944     165592
Swap:       401400      73376     328024

```

That's with TBird, Firefox and OOo open.  Tbird's got my account open on the inbox, Firefox has this web page open and OOo Writer is open but no file loaded.  Still have 165Mb of free space so plenty of breathing room.

---

### Post by tarahmarie on 2008-09-14
> **Greyed said:**
> I actually recommend against XUbuntu at this time. Unless the huge memory leak has been fixed.  I had to switch from XFCE to KDE because KDE used less memory after about 1-2 hours of usage.  No joke.

I'm running KUbuntu 8.04 (KDe 3.5.10, not 4.1) on a PIII 667Mhz machine with 256Mb of RAM.  It can handle Firefox/Thunderbird/Pidgin all at the same time with no swap.  Well, no swap unless I open like 30 web pages at the time which I sometimes do.  If I want to use OOo I have to close down TBird or Firefox and even then there is some swapping.  However, her machine has 128Mb more RAM and my swap never gets over 90Mb so she might be good.

Actually I just realized I know she'd be good.  I am running KUbuntu 8.04 (KDE 4.1) inside a VBox VM w/384Mb of RAM and haven't had any problems with it so far.

```
{grey@igbuntu:~} free
             total       used       free     shared    buffers     cached
Mem:        385536     380340       5196          0       3152     157244
-/+ buffers/cache:     219944     165592
Swap:       401400      73376     328024

```

That's with TBird, Firefox and OOo open.  Tbird's got my account open on the inbox, Firefox has this web page open and OOo Writer is open but no file loaded.  Still have 165Mb of free space so plenty of breathing room.

Well, I would certainly PREFER to have her running Kubuntu; it's what I use, and I'm in the unenviable position of being only two steps ahead of her in what I know about Linux anyway.  I don't know how much help I can give her when it comes to configuring XFCE.  Of course, the big diff between her and me is that I've spent more than a decade learning my Windows S#1% and she knows very little about computers, so she doesn't have to "unlearn" the way I'm having to do.  Do you think maybe if she got rid of compiz that KDE would be lightweight enough?  CAN you get rid of compiz?  With the package installer?

---

### Post by Greyed on 2008-09-14
> **tarahmarie said:**
> Do you think maybe if she got rid of compiz that KDE would be lightweight enough?  CAN you get rid of compiz?  With the package installer?

From what I've seen you have to explicitly add compiz.  But yes, you can remove it.  I don't run either of the listed KUbuntu installs with compiz.  The laptop does not have a 3-D card and the VM obvious does not.  I've dabbled with compiz on my game machine install of KUbuntu but honestly, it's pretty but after the "wow, neat!" factor wears off it doesn't add anything to the actual usability of the machine.  But I digress.  Yes, you can remove it if it somehow turns up by default.  In fact, I would highly recommend it.

---

### Post by doorknob60 on 2008-09-14
You could use any *buntu, although Xubuntu would work the best. You could also use Debian + KDE, in my experiences it's about as light as Xubuntu :O (not kidding)

---

### Post by halitech on 2008-09-15
I would have to say Debian + XFCE is lighter then Xubuntu. I have an old P3 866 with 256meg of ram that will boot to the desktop in under 3 minutes with a Debian+XFCE setup

Just realized you said Debian+KDE. Might give it a go and see how that compares to booting XFCE and running it.

---

### Post by tarahmarie on 2008-09-19
Hi, all:

I was trying to help my friend install Kubuntu on her laptop tonight.  (I'm doing this over the phone...)

We have a problem: she's using a Dell Inspiron 8000.  Her Kubuntu CD didn't boot; it keeps booting straight to XP.  I tried to help her get into the BIOS to alter the boot order.  We tried every combination of function keys, and the only one that got her into any kind of setup mode was the F2 key.  (The F8 key took her into the boot option menu, but there was apparently no "boot from CD" option there)  It took her into some kind of hardware configuration screen (recall that I can't see what she's doing, and so after she read the screen to me, I couldn't tell if there was some option there that would get her into Setup, or some location where she could change the boot order).  

How do I help her?  Can someone give me the correct keys to get her to the boot option screen in BIOS?  She's going to format and go fully Kubuntu, but not if she can't get the CD to boot.  Can she change the boot order from within Windows XP Pro?  If there's a GUI option, I could walk her through that, as well.

Thanks!

---

### Post by Greyed on 2008-09-19
F2 is the right key on a Dell.  It does take you into a custom BIOS screen.  She's just going to have to read each and every option... 

Hmm, actually Google knows all..

[http://support.dell.com/support/edocs/systems/opgx240/en/ug/advfeat.htm#1101564](http://support.dell.com/support/edocs/systems/opgx240/en/ug/advfeat.htm#1101564)

CNTL-ALT-F8 looks like a likely candidate.  Mind you that's from a completely different model of Dell but give it a whirl.

---

### Post by bodhi.zazen on 2008-09-20
[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

        [http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/](http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) 
        [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

