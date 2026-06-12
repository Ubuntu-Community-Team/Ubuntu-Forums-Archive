---
title: "Is there a distro that..."
date: 2008-03-23
forum: Other OS Talk
---

### Post by miggols99 on 2008-03-23
I love Arch, but I don't have time to keep it on my family computer. Of course I'll keep it on my laptop ;) Here's what I want for low maintenance:

[LIST]
[*]Rolling release
[*]Stable
[*]No need to "dist-upgrade" or anything similar
[*]Works well out of the box
[*]Uses sudo (or easy to set up)
[*]No Gnome please (preferred **Xfce** or **KDE** then KDE 4.1 when it's released :))
[/LIST]
It would be great for me to use Arch on here, but I don't have the time to maintain it. And it's not playing very well with it anyway (especially the ATI drivers - stupid AMD...:mad:)

---

### Post by Joeb454 on 2008-03-23
You could wait until next month and use Kubuntu 8.04, there will be an option to download a version with KDE4.

Plus it's an LTS :)

---

### Post by gfg on 2008-03-23
Sounds like PCLinuxOS or Mandriva are distors you should look into.

---

### Post by Lacrimstein on 2008-03-23
Well, Kubuntu HH KDE4 edition will not be an LTS - they specifically said so; And it is not a rolling release. I guess PCLinuxOS is allright, but I couldn't set up sudo, you have to su into root instead. Other than that, its decent (I like (K)Ubuntu more, still)

---

### Post by miggols99 on 2008-03-23
Also if it is 64bit that would be good. It looks like Mandriva is i586 only, but I don't really mind. I've found that 64bit gives a nice speedboost.

---

### Post by dptxp on 2008-03-23
If your OS works fine, there never is a reason for distribution upgrade.

Try sidux, cutting edge, but do not du.

It is KDE, and is coming with KDE 3.5.9 (I think) this month.

The light version (without OOffice or Gimp) is about 450 MB.

New versions every 3-4 months.

Will install in 5 minutes or less in new machines.

Forum support is good.

You want a rolling release but you do not want to du ?:confused:

---

### Post by miggols99 on 2008-03-23
EDIT: I don't like distros like Debian stable because it has outdated packages meaning bugs staying there for a long time...

I thought dist-upgrade was upgrading to a new release? Well I haven't used apt for a while ;)

---

### Post by cardinals_fan on 2008-03-23
It's not exactly a rolling release, but Zenwalk does emphasize the "new version" a little less strongly.

---

### Post by gfg on 2008-03-23
> **miggols99 said:**
> EDIT: I don't like distros like Debian stable because it has outdated packages meaning bugs staying there for a long time...

I thought dist-upgrade was upgrading to a new release? Well I haven't used apt for a while ;)

Siddux is based on Debian Unstable and is actually quite recent. Dist-upgrade has nothing to do with upgrading to a new release, it's just a form of "smart/safe" upgrading which I believe is supposed to check for and solve problems etc.

Edit: From the man page of apt:
> 
dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages"

---

### Post by miggols99 on 2008-03-23
I'm downloading Mandriva now...I did have a look at Sidux a while ago (early last year). How much has it changed since then? Is Sidux stable? If it's based on Debian unstable...

---

### Post by Antman on 2008-03-23
> **miggols99 said:**
> Is Sidux stable? If it's based on Debian unstable...

Sidux is Debian Sid with some custom scripts and packages to aid in dist-upgrading safely. I have found Sidux to be more stable than Ubuntu on **my** machines. 
Also, I believe the core of Ubuntu is a snapshot of Debian Sid that is of course customized with Ubuntu tweaks and addons that makes Ubuntu...  Ubuntu. :)

Sidux and of course Debian Sid, are not for the typical desktop user IMHO. Mainly because things are less automatic. You have to learn about the system and also learn the CLI in order to get things working right. But in the long run, I have found it more satisfing than Ubuntu or some of the other automatic distros that cater to the noob crowd.
Now however I have moved toward Fedora8 on most of my machines.

---

### Post by miggols99 on 2008-03-23
I just had a look at Mandriva in VirtualBox, and it looks like it hasn't changed much. It seems clogged with applications and looks cheaply made to be honest. The login/off sounds are very nice though ;) PCLinuxOS is a nogo for me for some reason. It just runs really sluggishly on the system I installed it on for some reason.

> Sidux is Debian Sid with some custom scripts and packages to aid in dist-upgrading safely. I have found Sidux to be more stable than Ubuntu on my machines. 
Also, I believe the core of Ubuntu is a snapshot of Debian Sid that is of course customized with Ubuntu tweaks and addons that makes Ubuntu... Ubuntu. 

Sidux and of course Debian Sid, are not for the typical desktop user IMHO. Mainly because things are less automatic. You have to learn about the system and also learn the CLI in order to get things working right. But in the long run, I have found it more satisfing than Ubuntu or some of the other automatic distros that cater to the noob crowd.
Now however I have moved toward Fedora8 on most of my machines.
Well if that's the case I don't really want to use it. I've already learnt Arch Linux (mostly) and I don't want to learn another distro...Sidux is a lot like Arch then?

---

### Post by LookTJ on 2008-03-23
What's wrong with Arch on the family desktop? You could install ssh and ssh into the desktop to maintain without kicking anyone off. You can also install sudo of course.

What are problems with Arch on your family's desktop if you did all that?

---

### Post by miggols99 on 2008-03-23
There are a few problems with Arch.

**The ATI Catalyst driver**
Now I wish I had a Nvidia card! I've been having crashes that are only recoverable by holding down the power button. Not sure if this is Arch specific.

**Flash**
Since I'm using 64bit, I have to use nspluginwrapper, which is relatively easy to set up, but I'm getting errors with it like in [this thread](http://bbs.archlinux.org/viewtopic.php?pid=331034).

So unfortunately I have to move away from Arch. I really don't want to change but I have to because the computer doesn't belong to me :(

---

### Post by LookTJ on 2008-03-23
> **miggols99 said:**
> There are a few problems with Arch.

**The ATI Catalyst driver**
Now I wish I had a Nvidia card! I've been having crashes that are only recoverable by holding down the power button. Not sure if this is Arch specific.

**Flash**
Since I'm using 64bit, I have to use nspluginwrapper, which is relatively easy to set up, but I'm getting errors with it like in [this thread]("http://bbs.archlinux.org/viewtopic.php?pid=331034").

So unfortunately I have to move away from Arch. I really don't want to change but I have to because the computer doesn't belong to me :(
Despite knowing very little about flash on 64bit, what ati package have you tried? Both open and proprietary drivers.

---

### Post by miggols99 on 2008-03-23
Well I tried the open one as well but everything ran really slow. I need good 3D rendering because I have quite a few games on there. The closed one is the one with the crashes.

---

### Post by LookTJ on 2008-03-23
> **miggols99 said:**
> Well I tried the open one as well but everything ran really slow. I need good 3D rendering because I have quite a few games on there. The closed one is the one with the crashes.Try hwd(install it and run "hwd -xa") and restart xorg(ctrl+alt+bkspace) and see how the open driver goes again.

---

### Post by tom56 on 2008-03-23
> **miggols99 said:**
> It would be great for me to use Arch on here, but I don't have the time to maintain it.

Any rolling release requires maintenence. That's the point of regular stable releases; the maintenence is done for you.

---

### Post by miggols99 on 2008-03-23
Well my laptop requires hardly no maintenance, and it is running Arch, this is because it has Linux friendly hardware, my family computer doesn't unfortunately. I didn't know about Linux when we bought it. Ahh I remember that great feeling when I discovered Linux :)

---

### Post by miggols99 on 2008-03-24
> **Taylor said:**
> Try hwd(install it and run "hwd -xa") and restart xorg(ctrl+alt+bkspace) and see how the open driver goes again.
Hmm well I tried that and removed everything about catalyst and installed mesa, **and** rebooted a few times, but it's still as slow as ever. How is the radeonhd driver coming along? Is it ready yet?

---

### Post by pelle.k on 2008-03-24
I've never run PCLinuxOS on any of my own systems, because it hasn't got the flexibility i need as a power user- but if i was looking for a stable, rolling release, kde distro for a family computer, PCLinuxOS is pretty much the only candidate there is. Nuff said.

---

### Post by LookTJ on 2008-03-24
> **miggols99 said:**
> Hmm well I tried that and removed everything about catalyst and installed mesa, **and** rebooted a few times, but it's still as slow as ever. How is the radeonhd driver coming along? Is it ready yet?
Since there's no distro that requires low maintaince on rolling release schedule, I will try to help you with ATI problems. 

You installed [this](http://www.archlinux.org/packages/13747/)?

If so, good

then you installed [hwd](http://www.archlinux.org/packages/3946/)?

then ran:

```
sudo hwd -xa
```

If all that, and it's still slow, I might need some more detailed information of some sort.

---

### Post by Hallvor on 2008-03-24
> **pelle.k said:**
> I've never run PCLinuxOS on any of my own systems, because it hasn't got the flexibility i need as a power user- but if i was looking for a stable, rolling release, kde distro for a family computer, PCLinuxOS is pretty much the only candidate there is. Nuff said.

+1 for PCLinuxOS. It is a rolling release and is very easy to get up and running and maintaining.

---

### Post by LaRoza on 2008-03-24
> **pelle.k said:**
> I've never run PCLinuxOS on any of my own systems, because it hasn't got the flexibility i need as a power user- but if i was looking for a stable, rolling release, kde distro for a family computer, PCLinuxOS is pretty much the only candidate there is. Nuff said.

I would sticky OpenSuSE in that slot as well. 

It would likely be usable as it is on an install for the average computer user.

---

### Post by miggols99 on 2008-03-24
Does it use root user as default? If so how do I remove it? I don't like using the root user...does it use sudo?

---

### Post by LookTJ on 2008-03-24
> **miggols99 said:**
> Does it use root user as default? If so how do I remove it? I don't like using the root user...does it use sudo?
If PCLOS(I'm assuming you're talking about that distro) has sudo, make sure to lock the root account

```
sudo passwd -l root
```

Just a reminder ;)

---

### Post by miggols99 on 2008-03-24
How about openSUSE?

---

### Post by LaRoza on 2008-03-24
> **miggols99 said:**
> How about openSUSE?

It uses su, and it similar to Ubuntu in most ways.

---

### Post by cardinals_fan on 2008-03-24
> **Taylor said:**
> If PCLOS(I'm assuming you're talking about that distro) has sudo, make sure to lock the root account

```
sudo passwd -l root
```

Just a reminder ;)

Are you saying root isn't locked by default?  How can that be?

---

### Post by Hallvor on 2008-03-25
> **cardinals_fan said:**
> Are you saying root isn't locked by default?  How can that be?

It isn`t locked the same way it isn`t locked in Mandriva or even Debian. Just make sure you have a strong root password and you`ll be fine.

---

### Post by miggols99 on 2008-03-25
I've installed openSUSE now, but the fonts are hideous! How can I enable subpixel hinting?

---

### Post by RAV TUX on 2008-03-25
> **miggols99 said:**
> I love Arch, but I don't have time to keep it on my family computer. Of course I'll keep it on my laptop ;) Here's what I want for low maintenance:
[LIST]
[*]Rolling release
[*]Stable
[*]No need to "dist-upgrade" or anything similar
[*]Works well out of the box
[*]Uses sudo (or easy to set up)
[*]No Gnome please (preferred **Xfce** or **KDE** then KDE 4.1 when it's released :))[/LIST]It would be great for me to use Arch on here, but I don't have the time to maintain it. And it's not playing very well with it anyway (especially the ATI drivers - stupid AMD...:mad:)
Have you tried [PC-BSD]("http://www.pcbsd.org/")? (NOT Linux but BSD)

---

### Post by miggols99 on 2008-03-25
Would that work well? Apparently BSD has even worse wireless support than Linux... (yes my family computer is wireless only - the wire trailing through the house was getting quite annoying) the card is broadcom based..

---

### Post by miggols99 on 2008-03-28
Well I tried Mandriva but it didn't want to boot. It worked fine on my laptop, so I guess it just hates my family computer...

---

### Post by PGTips91 on 2008-03-28
Have you looked at Klikit-Linux? They are at RC1 stage now and when 1.0 is released it will be self-updating, based on KUbuntu 7.10 with another release based on 8.4 to follow soon after.

I have been using Klikit since a beta version and found it very stable, easy to maintain and configure. You might like to have a look-see.

---

### Post by MONODA on 2008-03-30
Mandriva drove me insane! very unstable

---

### Post by miggols99 on 2008-03-30
Wow! Really? In the end, I've went back with Arch Linux with e17. Hopefully things will work better, because last time I was using KDE 4 (SVN repo - very stable on my laptop) and it had constant crashes...wish me luck :) I'll be posting a guide and screenshots on my website. See my signature.

---

### Post by Twitch6000 on 2008-04-01
Dreamlinux might meet your needs :).
It has xfce and gnome.
Here is a link.
[http://www.dreamlinux.com.br/download.html](http://www.dreamlinux.com.br/download.html)

---

