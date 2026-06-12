---
title: "Is Ubuntu getting too fat?"
date: 2010-01-07
forum: Recurring Discussions
---

### Post by lakelovers on 2010-01-07
This is not a problem, just curious as to how this happened. I think it was when I upgraded to 9.04, that my HD filled up and I had to scramble to make more space. Then I upgraded to 9.10, and everything fell apart (you know the story), so I downgraded all the way to 8.04, where I am now, and everything works as it should. The curious thing is that I gained significant drive space. I have an 80gb drive. The whole drive was filled by the time I had upgraded to 9.04. Now, I have 63 GB free in 8.04. I'm assuming that going to 8.10, then to 9.04 and finally to 9.10, added a whole bunch of apps which I probably didn't need. Or, is Ubuntu just getting really fat like so many systems do as they evolve. Just curious.

---

### Post by Sef on 2010-01-07
Moved to Recurring Discussions.

---

### Post by Techsnap on 2010-01-07
Ubuntu is without a doubt the most bloated Gnome distro I've used. Even when you remove all the junk it still uses more resources and generally runs slower than other gnome distros with similar configurations.

Then APT (Debians problem too) pulls in dependencies which really aren't needed just adding to that.

---

### Post by underquark on 2010-01-07
Given that I installed 9.04 from a single CD and have recently done it on another machine from a 1Gb USB stick I would say it isn't *that* fat.  A quick look at my system shows about 12Gb programs, settings etc. etc. after installing loads of stuff.  The rest is data - maps, photos, videos, music.  Did you maybe have a partition lost somewhere along the line or a biq swap partition lying idle?

---

### Post by blueshiftoverwatch on 2010-01-07
Uhm, if anything Ubuntu doesn't come with enough software by default. It's one of the only distros that still tries to fit onto a single CD while everyone else (Windows, OSX, most other distros) come on a DVD. Eventually Ubuntu is going to have to get with the rest of the world and realize that not everything is going to fit onto a CD.

---

### Post by edd07 on 2010-01-07
> **blueshiftoverwatch said:**
> Uhm, if anything Ubuntu doesn't come with enough software by default. It's one of the only distros that still tries to fit onto a single CD while everyone else (Windows, OSX, most other distros) come on a DVD. Eventually Ubuntu is going to have to get with the rest of the world and realize that not everything is going to fit onto a CD.
Actually, I think that having the goal of fitting in one CD is a good thing. It prevents developers from adding lotst of bloat to it. I find it amazing that it can have so many thing on such a small space, it's great it keeps adding great features without growing in size (I'm, looking at you, Windows and OSX!). 
I think an OS should contain the lowest common denominator of what people need, not trying to include everything anyone will ever need. The repos are for specialized apps. However, I'm all in favor of an extra DVD of apps and stuff for people who don't have regular access to broadband or simply prefer to have installable stuff offline (I think Fedora or OpenSUSE do this)

And to answer the OP's question, I think it's not getting fat at all. I've had the same root partition size (10GB) since Feisty with all my apps installed and I've never needed more space. My Windows 7 installation, with less apps installed than Ubuntu, is over 30GB. I think Ubuntu's doing a great job.

---

### Post by snowpine on 2010-01-07
> **lakelovers said:**
> This is not a problem, just curious as to how this happened. I think it was when I upgraded to 9.04, that my HD filled up and I had to scramble to make more space. Then I upgraded to 9.10, and everything fell apart (you know the story), so I downgraded all the way to 8.04, where I am now, and everything works as it should. The curious thing is that I gained significant drive space. I have an 80gb drive. The whole drive was filled by the time I had upgraded to 9.04. Now, I have 63 GB free in 8.04. I'm assuming that going to 8.10, then to 9.04 and finally to 9.10, added a whole bunch of apps which I probably didn't need. Or, is Ubuntu just getting really fat like so many systems do as they evolve. Just curious.

'sudo apt-get clean' would have cleaned out your package cache. You probably had many cached packages from the various upgrades over the years.

There's also the possibility you used different filesystems or partitioning schemes, I really can't say.

No release of Ubuntu has ever used more than 4gb for the standard install; it simply wouldn't fit on a single CD otherwise.

---

### Post by Twitch6000 on 2010-01-07
> **Techsnap said:**
> Ubuntu is without a doubt the most bloated Gnome distro I've used. Even when you remove all the junk it still uses more resources and generally runs slower than other gnome distros with similar configurations.

Then APT (Debians problem too) pulls in dependencies which really aren't needed just adding to that.

+1 to this statement

---

### Post by -kg- on 2010-01-07
[LIST]
[/LIST]

Much the same from me.  I just installed 9.10 Karmic.  I have under a 10 GB root partition, have some installed programs, and I'm using 3.72 GB.  While I store the majority of my files in a separate partition on an external hard drive, I do have some files stored in my /home partition...around 527 MB worth.  This is as it has always been.

Of course, I don't upgrade...I fresh install every new release.  I've seen no significant increase in installation size since I started with Hardy.  It's all how you do it; if you upgrade, you carry baggage with you...possibly unneeded baggage.

I'm still of the school that backs up the data they want and installs completely from scratch.  It might take a little longer setting the new distro up, but it's a clean install and there will be ample room to replace the data you need.  Or, you can store and work with it elsewhere and not have to backup your data at all.  That's what I do.

I tried the upgrade method from Jaunty to Karmic, and it didn't go well for me.  Once I clean installed and replaced data, it all worked like a charm.  And it *certainly* didn't take more room than Jaunty; at least not that I could notice.

---

### Post by leveled on 2010-01-07
> **edd07 said:**
> Actually, I think that having the goal of fitting in one CD is a good thing. It prevents developers from adding lotst of bloat to it. I find it amazing that it can have so many thing on such a small space, it's great it keeps adding great features without growing in size (I'm, looking at you, Windows and OSX!). 


People installing the Snow Leopard via upgrade from Leopard have reported gaining back many GB in hard drive space.

---

### Post by edd07 on 2010-01-07
> **-kg- said:**
> Of course, I don't upgrade...I fresh install every new release.  I've seen no significant increase in installation size since I started with Hardy.  It's all how you do it; if you upgrade, you carry baggage with you...possibly unneeded baggage.
I do upgrades, and the OS's size remains unchanged (or at least the growth is unnoticeable). The baggage gets deleted just fine

> **leveled said:**
> People installing the Snow Leopard via upgrade from Leopard have reported gaining back many GB in hard drive space.
You are right, and I stand corrected. My point stands about Windows (I did the Vista-7 upgrade).

---

### Post by jlperry on 2010-01-07
> **snowpine said:**
> 'sudo apt-get clean' would have cleaned out your package cache. You probably had many cached packages from the various upgrades over the years.

There's also the possibility you used different filesystems or partitioning schemes, I really can't say.

No release of Ubuntu has ever used more than 4gb for the standard install; it simply wouldn't fit on a single CD otherwise.

I agree snowpine is on the right track for the original question. Sometimes upgrading doesn't fully clear out old packages and caches that are no longer needed. You may need to just do some "spring-cleaning" on your system.

1) sudo apt-get autoremove
2) sudo apt-get clean
3) Remove old headers from Synaptic Package Manager (manually). It may be possible that you have all the headers from 2.6.23-xx to 2.6.31-xx . 

Headers related to the old kernel version and packages no longer needed are just wasting space. The system doesn't automatically clean these in case the user requires any of it for what ever reason and also an attempt to keep your existing apps and configs compatible with the upgraded kernel.

---

### Post by pythonscript on 2010-01-07
Also, if you create the /etc/apt/apt.conf file with the following lines:

```
APT::Install-Recommends "0";
APT::Install-Suggets "0";
```you can disable apt-get from downloading the recommended/suggested packages when it installs a package. Right now, I have these sets of commands stored in a script, and they seem to keep my system pretty minimal (under 8 GB for my root partition, about 3 GB worth is just Mathematica 7 for Linux) just on their own. 

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove -y
sudo deborphan | xargs sudo apt-get purge -y
sudo localepurge
```

Just these, apart from my other streamlining, keeps my system pretty bare in terms of what I need and what I don't. Coming from Arch and Tiny Core, though, everything seems pretty bloated, to be honest... That's the price we pay for having a system that "just works" most of the time.

---

### Post by lakelovers on 2010-01-07
I've learned a few things, here. I will do fresh installs in the future. I did a fresh install when downgrading to 8.04. I did run into one problem though that I have not solved. I had backups of my files on an external usb drive using sbackup. When I tried to restore the files, some restored okay, but most did not. Responses to my post indicated that some of the sbackup dependencies were not installed. I couldn't figure out how to repair the sitution. Reinstalling sbackup didn't fix any dependencies if that was the problem. Anyway, I have things pretty much back to normal.

---

### Post by Gramps on 2010-01-07
> **lakelovers said:**
> I've learned a few things, here. I will do fresh installs in the future. I did a fresh install when downgrading to 8.04. I did run into one problem though that I have not solved. I had backups of my files on an external usb drive using sbackup. When I tried to restore the files, some restored okay, but most did not. Responses to my post indicated that some of the sbackup dependencies were not installed. I couldn't figure out how to repair the sitution. Reinstalling sbackup didn't fix any dependencies if that was the problem. Anyway, I have things pretty much back to normal.

Through the years a backup program has caused me more problems 
than I care to remember. I've tested them and all but it seems that when you really need it, something went arye and you could not recover the file(s). Do a Google search for  rsync backup using this method your files are in their native format so they can be copied back or use rsync in reverse to restore them.

---

### Post by Warren Watts on 2010-01-08
> **Techsnap said:**
> Ubuntu is without a doubt the most bloated Gnome distro I've used. Even when you remove all the junk it still uses more resources and generally runs slower than other gnome distros with similar configurations.

Then APT (Debians problem too) pulls in dependencies which really aren't needed just adding to that.

> **Twitch6000 said:**
> +1 to this statement

Add my +1 as well.  If you don't believe it, download and burn a Zenwalk Gnome Live CD and see how much more efficient it is than Ubuntu.

Ubuntu has it all over Zenwalk (which is Slackware based) in terms of available packages and ease of use for noobies, but the Gnome edition of Zenwalk runs really fast and smoothly on older PCs that a full install of 9.10  kinda stumbles with.  I attribute that primarily to Ubuntu bloat.

---

### Post by Tibuda on 2010-01-08
> **pythonscript said:**
> Also, if you create the /etc/apt/apt.conf file with the following lines:

```
APT::Install-Recommends "0";
APT::Install-Suggets "0";
```you can disable apt-get from downloading the recommended/suggested packages when it installs a package. Right now, I have these sets of commands stored in a script, and they seem to keep my system pretty minimal (under 8 GB for my root partition, about 3 GB worth is just Mathematica 7 for Linux) just on their own. 

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove -y
sudo deborphan | xargs sudo apt-get purge -y
sudo localepurge
```

Just these, apart from my other streamlining, keeps my system pretty bare in terms of what I need and what I don't. Coming from Arch and Tiny Core, though, everything seems pretty bloated, to be honest... That's the price we pay for having a system that "just works" most of the time.

**dpkg -l | grep "^rc"** lists some extra orphan packages not listed by deborphan, so I would add this line to your script:
```
dpkg -l | grep "^rc" | awk "{print \$2}" | xargs sudo apt-get purge -y
```

You can also install [BleachBit]("http://bleachbit.sourceforge.net/"), which helps on getting rid of hidden config files in home dir.

---

### Post by MooPi on 2010-01-08
I have my 4gig netbook installed with Juanty and still have 1.6 gig's left. Granted its not gnome but Openbox.

---

### Post by pythonscript on 2010-01-08
> **danielrmt said:**
> **dpkg -l | grep "^rc"** lists some extra orphan packages not listed by deborphan, so I would add this line to your script:
```
dpkg -l | grep "^rc" | awk "{print \$2}" | xargs sudo apt-get purge -y
```You can also install [BleachBit]("http://bleachbit.sourceforge.net/"), which helps on getting rid of hidden config files in home dir.

Thanks for this! I'll definitely add this.

---

### Post by bobbob1016 on 2010-01-14
> **leveled said:**
> People installing the Snow Leopard via upgrade from Leopard have reported gaining back many GB in hard drive space.

That is because Snow-Leopard dropped support for IBM PPC CPU's.  So they were simply able to drop half of their code (not really half, but for simplicity's sake we'll call it half).  Also Snow-Leopard uses base 10 for hard drive size, not base 8.  As in when you buy a 500gig hard drive, and formatted it is 480gig or something, Snow-Leopard would show it as 500gig formatted.

Ubuntu, and Linux in general, support more hardware daily, and keep legacy support, without growing exponentially.  The bloat can be made less if you take out support for things you won't use.  This is the reason the EEEPC-lean kernel is smaller than normal kernels, the lean kernel doesn't have PCIe support, or Printer Port support, or anything that can't be put into an EEEPC.

---

### Post by MasterNetra on 2010-01-14
I maybe getting fat but I don't think Ubuntu really is.

---

### Post by arvevans on 2010-01-14
Interesting to read this thread and observe how it got morphed into something different than the original post/question.
[LIST=1]
[*]Ubuntu runs slow because it is too fat.
[*]Ubuntu takes up too much space on install disk because it is too fat.
[*]Ubuntu "just works" because of the fat.
[*]Here is how you remove unused files.
[*]Ubuntu is "fatter" than this other distro.
[/LIST]
Seems that the original post was addressing speed issues arising from bloat of in-core processes, and not how convenient or inconvenient it might be to install from a CD (FYI, network based installs can be done from a very small CD).  Then the original post was hijacked by everyone's keying in on the word "bloat" without really reading the original post.

Now for my 2-cents worth:

Slowing of Ubuntu (and other Linux) execution is usually from three causes:

  1) Too much real bloat (i.e. core-locked processes, usually kernal processes, being loaded and not unloaded when not needed).

  2) Poorly written programs which install themselves in a way to continuously use CPU cycles and thus slow down the system.

  3) Very large footprint applications which use up all your RAM and force use of swap in order to keep the program running.

Most Linux applications are just files, which only use disk space (not CPU cycles) when they are not being used.  These do not slow-down your system, unless you try to launch many at the same time.

Run the "top" command to see just what might be using your CPU cycles, and contributing to slow down.  If it is like my computer you will see xorg and firefox usually on the top few lines. From that you can make some guesses as to what is slowing your system.
_._

---

### Post by -kg- on 2010-01-16
> **arvevans]Seems that the original post was addressing speed issues arising from bloat of in-core processes, and not how convenient or inconvenient it might be to install from a CD (FYI, network based installs can be done from a very small CD). Then the original post was hijacked by everyone's keying in on the word "bloat" without really reading the original post.[/QUOTE]

OK, let's look at the original post:

[QUOTE=lakelovers said:**
> This is not a problem, just curious as to how this happened. I think it was when I upgraded to 9.04, that my HD filled up and I had to scramble to make more space. Then I upgraded to 9.10, and everything fell apart (you know the story), so I downgraded all the way to 8.04, where I am now, and everything works as it should. The curious thing is that I gained significant drive space. I have an 80gb drive. The whole drive was filled by the time I had upgraded to 9.04. Now, I have 63 GB free in 8.04. I'm assuming that going to 8.10, then to 9.04 and finally to 9.10, added a whole bunch of apps which I probably didn't need. Or, is Ubuntu just getting really fat like so many systems do as they evolve. Just curious.

Sure looks like he's talking about bloat issues on his hard drive to me, but that might just be me.  I see no reference to "speed issues arising from bloat of in-core processes".  He was talking about his 80 GB hard drive filling up from upgrade to upgrade, and when he "downgraded all the way to 8.04" (ostensibly by a clean install), that he "gained significant drive space."

Of course, I know he said he "upgraded to 9.10, and everything fell apart (you know the story)", but no, apparently we don't know the story.  Did everything slow down and become unusable, or was he unable to do the upgrade properly because he had no more room on the hard drive?

Only the OP can make a repost and tell us for sure, but I would surmise that it was more a hard drive room problem than a core process speed issue.  Of course, I might be wrong.

The only way to tell for sure is to do a fresh install of Karmic.  He says he has 63 GB free in his Hardy installation.  You and I both know that this is more than enough to do a fresh installation of Karmic for a test.  My bet is that it would run fine, and not take near the space that all the upgrades took.

Apparently, you might have read the OP, but you didn't read the ET (entire thread).  The OPer did post back with the following:

> **lakelovers said:**
> I've learned a few things, here. I will do fresh installs in the future. I did a fresh install when downgrading to 8.04. I did run into one problem though that I have not solved. I had backups of my files on an external usb drive using sbackup. When I tried to restore the files, some restored okay, but most did not. Responses to my post indicated that some of the sbackup dependencies were not installed. I couldn't figure out how to repair the sitution. Reinstalling sbackup didn't fix any dependencies if that was the problem. Anyway, I have things pretty much back to normal.

If he has things pretty much back to normal, perhaps he already fresh installed Karmic.  If not, I'm sure he can do so and have no problem with it.

I don't even pretend to know everything about Linux and Ubuntu, but I do know that a Karmic installation doesn't take 80 GB of hard drive space, and by what I read in the OP, he didn't say that his system slowed down at all.

---

### Post by lakelovers on 2010-02-03
After reading all these post in answer to my original question, I need to be more specific describing my actions. I did an "upgrade" for 9.10 (from 9.04), I experienced random freezes requiring reboots. I tried a fresh install downloading bittorrent but I couldn't burn a disk getting an error message that there was not enough room on the CD. Reading posts on this forum I saw that others were having problems with random freezes and also having problems burning a CD. That why I asked about "bloat." I did do a fresh install with 8.04, I saw that some apps I used (eg. GIMP) were older versions. So, I did a fresh install of 9.04. That's were I'm sitting now and everything seems to be operating properly. I'd move to 9.10 is I was sure I wouldn't have any unsurmountable problems. I hope I haven't created confusion with this lengthy description of my actions. It goes without saying that I'm not the sharpest knife in the drawer when it comes to Ubuntu and Linux.

---

### Post by Psumi on 2010-02-03
> **Techsnap said:**
> Ubuntu is without a doubt the most bloated Gnome distro I've used. Even when you remove all the junk it still uses more resources and generally runs slower than other gnome distros with similar configurations.

Then APT (Debians problem too) pulls in dependencies which really aren't needed just adding to that.

With mini.iso:

```
sudo apt-get install gnome-core gdm xorg gksu
```

uses 98 MB of RAM until you start using applications, especially firefox (takes up to 100 MB of RAM at times alone.)

---

### Post by humphreybc on 2010-02-13
I think I might start a project to slim down some unnecessary things in Ubuntu. I'll put it forward at UDS-M.

There is a lot of stuff that's now obsolete, mainly old Gnome stuff that doesn't fit well with Ubuntu's image anymore - like the "fish eyes" panel applet, and the Windows 95-esque selection of default window borders.

---

### Post by blueshiftoverwatch on 2010-02-13
> **humphreybc said:**
> There is a lot of stuff that's now obsolete, mainly old Gnome stuff that doesn't fit well with Ubuntu's image anymore - like the "fish eyes" panel applet, and the Windows 95-esque selection of default window borders.
I don't think the fish eyes applet takes up that much room and I like the Windows 95 style themes in Appearance Preferences.

If they want to get rid of something they can start with Wubi. If someone wants to run Ubuntu on Windows they can use a VM like Virtualbox. If they're not tech savvy enough to download a VM on their own and set it up they're not tech savvy enough to use Linux.

---

### Post by terrybennett on 2010-03-11
I am having a problem with fitting 9.10 on an 8.5GB partition.  My problem sounds similar to the original poster.  I had no problem with 9.04 but 9.10 filled the partition and I cannot even run updates.

I resized and reformatted the partition before doing a clean install.  

Could I have formated wrong?  What file type should I have used?  How can I tell now?

I am new to Linux.  Have only used it a few months.

---

### Post by Tibuda on 2010-03-11
I think Canonical doesn't  want that image. The rebranding wiki page says they want Ubuntu to be lightware.

---

### Post by Tristam Green on 2010-03-11
> **blueshiftoverwatch said:**
> I don't think the fish eyes applet takes up that much room and I like the Windows 95 style themes in Appearance Preferences.

If they want to get rid of something they can start with Wubi. If someone wants to run Ubuntu on Windows they can use a VM like Virtualbox. If they're not tech savvy enough to download a VM on their own and set it up they're not tech savvy enough to use Linux.

That's awfully arrogant.  The entire idea behind Wubi was to make it as easy as possible to set up for Windows users.

---

### Post by KiwiNZ on 2010-03-11
> **blueshiftoverwatch said:**
> I don't think the fish eyes applet takes up that much room and I like the Windows 95 style themes in Appearance Preferences.

If they want to get rid of something they can start with Wubi. If someone wants to run Ubuntu on Windows they can use a VM like Virtualbox. If they're not tech savvy enough to download a VM on their own and set it up they're not tech savvy enough to use Linux.

I have to agree with Tristram green this is the type of attitude that turns so many off linux and Ubuntu.
It is not welcome on Ubuntu Forums.

---

### Post by Post Monkeh on 2010-03-11
there are a lot of things about ubuntu that are far easier than the windows equivilent, a lot of it is just re-education.  granted there are some hardware issues that are nigh on impossible for the average user to fix without help, but  if you're one of the many lucky ones who has a hardware setup where everything important works without hassle, then i think you'd be surprised how easy it is for the less tech savy people to use.
not everyone wants to modify their system all the time, some people just like to switch on a computer, download the basic programs they need to listen to music, browse the internet, check their email, and do basic office tasks.  
personally i would find it easier to teach someone who knew nothing about computers how to do that on an ubuntu system than a windows system (provided there were no hardware issues of course, which CAN be a killer, but shouldn't ever lead to the assumption that you HAVE to be a computer whizz to use linux)

---

### Post by NightwishFan on 2010-03-11
I like my machines mainly being close to the upstream configuration. Odd for a Linux user yes, but I do customize hither and thither at my will to get a desired setup. The default Ubuntu set-up is beginning to use such things as indicator applets and essentially the rest of things in this article. [http://www.omgubuntu.co.uk/2010/03/16-things-that-could-be-improved-in.html](http://www.omgubuntu.co.uk/2010/03/16-things-that-could-be-improved-in.html) The indicator applets especially merely make some programs have different functionality to learn than other ones, and remove the ability to use tray applets in the Gnome Shell.

On a default install and boot of Ubuntu 9.10 and 10.04 my RAM usage is around 600 out of 900mb. That compares to Hardy which used around 300mb, or Debian Sid which uses 180. I know for a fact that Ubuntu is not fat, as I can get 'similar' results to Debian by installing a minimal Gnome. It is just an issue with the default configuration and purpose of Ubuntu does not fit my tastes. I always recommend it to beginner users though, but no longer ones with a lower end machine.

---

