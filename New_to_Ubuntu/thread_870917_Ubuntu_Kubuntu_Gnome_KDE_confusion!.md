---
title: "Ubuntu Kubuntu Gnome KDE confusion!"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Midahed on 2008-07-26
Sorry to post another 'Ubuntu or Kubuntu' thread but, despite searching and reading loads of posts, I'm still a bit confused about my options.

I've been using Ubuntu 7.04 Feisty with the Gnome desktop and standard applications for quite a while.  I get on with it OK, but having decided to re-build my system from scratch using a later release, I thought I'd have a look at the other options.  So I downloaded the live-CD for Ubuntu 8.04 LTS and for Kubuntu 8.04.

While I like Ubuntu and Gnome OK, I really much prefer the KDE desktop provided by Kubuntu.  I also prefer the majority of the KDE apps which somehow make their Gnome equivalents look distinctly 'clunky'.

I'm not yearning for Windows - before anyone suggests that!  I hate Windows  for many reasons and I will never again use it as my main OS, but I do like the 'Windows look and feel' of KDE.

Sorry if that offends anyone. ;)

Because I don't regularly re-build my system, I decided to go for the LTS release of Ubuntu.  I assumed there would be an equivalent for Kubuntu, but it appears not.  Support for Kubuntu 8.04 expires in October 2009, whereas Ubuntu 8.04 LTS is supported until 2011.  Does Kubuntu not have LTS releases?

Elsewhere I've read that Kubuntu 8.04 is really Ubuntu 7.1 (specifically not 8.04) with KDE.  Other posters have said that Kubuntu is 'just Ubuntu with a different desktop environment', but yet other posters have complained that Kubuntu is Ubuntu's poor relation and doesn't get the same level of support.

How are all these things true if the two versions are, to all intents and purposes, the same thing bar the desktop and apps?

If Ubuntu and Kubuntu are that similar, why bother having two discrete versions?

If Ubuntu and Kubuntu are 'the same under the covers', why is there no 'LTS' release for Kubuntu?

I really want to go the 'LTS' route, but I'd like to give KDE a try.

Can I achieve this by just installing the KDE-desktop on my new Ubuntu build?  If I do that, and default my session to KDE am I effectively then using a system that's exactly the same as Kubuntu, or will there be other aspects of the Kubuntu environment missing?

Also, does installing the KDE desktop automatically provide all the KDE apps that are bundled as part of the Kubuntu build, or is it necessary to install them all separately?

Sorry about the long post and numerous questions, but I really don't understand the differences between Kubuntu and using Ubuntu with KDE.

Mike

---

### Post by eightmillion on 2008-07-26
This version of kubuntu does not have a LTS release. KDE 4 wasn't quite ready to go and canonical isn't expecting to support KDE 3 for 3 more years. The underlying system will be supported for 3 years, but the KDE components won't be. 

If you just install plain ubuntu, then you can install kubuntu-desktop and default to KDE and you have a system that is kubuntu.

> Also, does installing the KDE desktop automatically provide all the KDE apps that are bundled as part of the Kubuntu build, or is it necessary to install them all separately?

If you install the package kubuntu-desktop then you get everything that comes along with the default kubuntu install.

Hope this answers all your questions. :)

---

### Post by Midahed on 2008-07-26
> **eightmillion said:**
> ...Hope this answers all your questions. :)
It does indeed! :)

Not sure now why something so simple managed to confuse the hell out of me.

I'll base the system on Ubuntu 8.04 LTS with all my existing Gnome apps and data, and I'll bung KDE-desktop on there as well (using aptitude, not apt-get) and see how it all works.

Thanks for your help.

---

### Post by eightmillion on 2008-07-26
No problem.

You might give KDE 4 a shot too. You can have all 3 installed and choose which one you want to run on your login screen.

---

### Post by anjilslaire on 2008-07-26
> **Midahed said:**
> 

I'll base the system on Ubuntu 8.04 LTS with all my existing Gnome apps and data, and I'll bung KDE-desktop on there as well (using aptitude, not apt-get) and see how it all works.

Thanks for your help.

Why the fear of apt-get? It's not going to hurt anything, despite what you may have heard. For that matter, if you're going to be installing Ubuntu 8.04 & then throwing kubuntu-desktop on afterwards, just open Synaptic from gnome, do a search for kubuntu-desktop, and just install it from there. 

I've installed it from synaptic, as well as a straight kubuntu install. No problems either way, and I run kubuntu as my main DE

---

### Post by SunnyRabbiera on 2008-07-26
Installing kubuntu desktop via the repositories will not do any harm to your system I assure you.

---

### Post by stmiller on 2008-07-26
> **Midahed said:**
> 
I really want to go the 'LTS' route, but I'd like to give KDE a try.


Do you need LTS? The whole LTS thing is mainly for servers or persons who need one solid install to last with several years of security updates. 

The latest and greatest stable ubuntu releases arrive every six months...

---

### Post by SunnyRabbiera on 2008-07-26
well one can stay the lts route but still experiment if they know what they are doing.

---

### Post by Midahed on 2008-07-26
> **anjilslaire said:**
> Why the fear of apt-get? It's not going to hurt anything, despite what you may have heard.
Unfortunately I can't find the posts, but I read from several separate sources that synaptic installs the kubuntu-desktop just fine, but doesn't properly remove it if a later un-install is required.

Something to do with the installation log that synaptic creates (or doesn't create?).

Maybe it's not true...?

---

### Post by SunnyRabbiera on 2008-07-26
Nah, it will be fine though there might be some residual crap here and there but its easy to remedy without hurting the system.

---

### Post by Midahed on 2008-07-26
> **stmiller said:**
> Do you need LTS? The whole LTS thing is mainly for servers or persons who need one solid install to last with several years of security updates. 

The latest and greatest stable ubuntu releases arrive every six months...
Basically because I want the long-term support - or at least the option of sticking with that version for quite a while.  I don't like doing rebuilds from scratch.  It always seems to take ages to get the system back how I like it.

I will install other distros and play with new Ubuntu releases - either under VMware or on a separate box, but I want my base system to be around for a while without the need to upgrade/rebuild.

---

### Post by kansasnoob on 2008-07-26
Have a look here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Especially the section:

> Playing Around
Enable Desktop Effects
KDE/Gnome Comparison
Install Gnome
Install KDE
Install XFCE
Install IceWM
Install XPDE
Pure Gnome
Pure KDE
Pure XFCE
A faster KDE
Replacing Nautilus 

---

