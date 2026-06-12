---
title: "ok, I give, how do you get new software?"
date: 2005-03-02
forum: Repositories &amp; Backports
---

### Post by Gorf on 2005-03-02
I have followed multiple threads, and links from various places including here in the forums, and ubuntuguide.org.  And I don't get it.  How do you get latest software to show up in Synaptic?  

I'll be honest, I really like Ubuntu, but I was drawn to it because I was told how awesome the package management was.  But I must be doing something wrong, cause I am not seeing it.

For instance, Gaim is on 1.1.4 now, yet in Synaptic all I see is 1.0.0.  And Thunderbird is only available in 0.8, and Firefox in 0.99.  

For reference, here is my /etc/apt/sources.list:

 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted 


I hope someone can point me at what I am doing wrong.  I just have a hard time imagining that popular apps like these get updated in the repository so slowly.  

Ok so in speaking with some people on the IRC channel, I am lead to believe that even with these changes in the config file, I will not see all the more current versions of software.  Can someone confirm this for me?

Thanks all

---

### Post by techn9ne on 2005-03-02
The default apt sources list will only show minor upgrades for software and security stuff for stability.

If you want the latest and greatest firefox, gaim and thunderbird use backports :

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

Take out what you have for backports and add this :

# backport
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted

## EDIT ##

Umm I don't like synaptic. Go into console and type:

 sudo apt-get update && sudo apt-get upgrade

that will upgrade your firefox, thunderbird and gaim

---

### Post by doitashimashite on 2005-03-02
Thank you techn9ne! I was looking for this information too.

---

### Post by gopalraj on 2005-03-02
Me too!

---

### Post by Jet2k5 on 2005-03-02
Hi guys.

I've seen stuff like this and I've asked my self if I have the right sources.  I mean does Ubuntu have official universe packages or whatever mirror is incharged of handeling the extra apps as you would call them in Archlinux.  By extra apps I mean like gaim, firefox and stuff like that.  Not including updates.

I have the sources from ubuntuguide.org, but are those the safest and most stable packages?  I just want the mirrors that Ubuntu would recommend, for their packages.  

I hope I have the right stuff, since I've been having some issues with firefox.

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=Jet2k5]
I have the sources from ubuntuguide.org, but are those the safest and most stable packages?  I just want the mirrors that Ubuntu would recommend, for their packages.  
[/QUOTE]


No. The Ubuntu devs don't recommend backports....hell they don't even recommend the Universe. 

The backports project is the work of jdong to provide an unstable repo for those people who like the bleeding edge but don't want the REALLY bleeding edge of Hoary. Its not supported or recommended by the Ubuntu devs.

Simply put, Warty is not supposed to have the newest stuff. It is realised, "in the bag" so to speak, and the devs don't spend their time putting new software in the official Universe repo. Luckily Jdong donates his time to do that, but his work is not supported. If you want new, stable, supported software you must wait to upgrade your programs every six months when the newest stable release occurs (the next one will be in April).

---

### Post by Jet2k5 on 2005-03-07
I see, that sorta sucks, I thought ubuntu would have new packages.

Man that's sorta disappointing , is it too much work or what?

---

### Post by DJ_Max on 2005-03-07
[QUOTE=Jet2k5]I see, that sorta sucks, I thought ubuntu would have new packages.

Man that's sorta disappointing , is it too much work or what?[/QUOTE]
 See for yourself.
[http://www.debian.org/doc/manuals/maint-guide/index.en.html](http://www.debian.org/doc/manuals/maint-guide/index.en.html)

If you need the software now, you can grab the source and compile it.

---

### Post by tymark on 2005-03-07
it's a normal release cycle as you'll find in many distributions.  Mandrake, Fedora, etc all use this sort of release cycle.  New version of the distro every 6 months with new versions of the programs.  In between, you get security updates and maybe bug fixes, but rarely (never, in almost all cases) do you get new full versions of any program.

knowing that you used arch previously, you've had experience with a rolling release cycle.  that is, new versions are always being put into the repo's as they become stable, and the stable branch is packaged up every 6 months as a new version.

---

### Post by snaga on 2005-04-01
Having come from Gentoo, with its rolling release, I can understand a little of the disappointment. However, I have found that the more stable, less often updated environment to be better for me. In fact, my decision to go to Hoary early, before its official, is one that I now regret. I get constant updates now, which is annoying to me. I'm a bit OCD about being up-to-date I guess  ;-)

---

### Post by jubuntus on 2005-04-04
Hi everyone.
From reading this thread I now understand that syntaptic does not upgrade packages, but should update packages, particularly security fixes.
I installed hoary-rc recently. I have noticed that thunderbird has not been updated to 1.02 from 1.0 and as far as I know this was a security release. There are also a few other packages which have not been updated either. aibword for example (2.2.2 installed, most recent is 2.2.6) and a few others. Now I realise that this is a release candidate, but I recall  noticing this also in warty, a stable release.
So, my question is, how do you contact the package maintainers to give them a gentle nudge/reminder/notification that a newer package has been released with potential critical bug fixes/security fixes???
Thanks all you Ubuntumeisters, in advance.

---

### Post by jubuntus on 2005-04-05
Forget the question, I posted a new thread for this. [http://www.ubuntuforums.org/showthread.php?p=116337#post116337](http://www.ubuntuforums.org/showthread.php?p=116337#post116337)

---

### Post by echo_high on 2005-04-08
Finally, surely someone here will be able to give me some answers...

If one doesn't have access to the internet from the computer running Ubuntu, how can you download packages without use of "repositories".  I'd just like to download the .deb files to a USB drive, to take home and install.  But for the life of me I can't figure out where you can get the files from.  I am running the AMD64 version of Warty and just want to listen to my MP3s!!!

Please someone, I am sure this is really stupid, but someone will be able to explain (at which point I will likely realise I am a moron).

Cheers

Eddie

---

### Post by naser on 2006-10-01
> **techn9ne said:**
> The default apt sources list will only show minor upgrades for software and security stuff for stability.

If you want the latest and greatest firefox, gaim and thunderbird use backports :

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

Take out what you have for backports and add this :

# backport
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted

## EDIT ##

Umm I don't like synaptic. Go into console and type:

 sudo apt-get update && sudo apt-get upgrade

that will upgrade your firefox, thunderbird and gaim

Hello, but this solution didn't work either. On top of that, I think the repositories you posted a link to aren't working right now :( I followed  the instructions at [Backports section]("http://backports.ubuntuforums.org/wiki/index.php/Main_Page") of the ubuntu wiki, but their repository didn't work either. I'm still seeing the latest version of Firefox available as v 1.0.8 where as the latest stable version is something like FF v 1.5.X.X **Any idea what to do**?

---

### Post by cjm5229 on 2006-10-01
> **naser said:**
> Hello, but this solution didn't work either. On top of that, I think the repositories you posted a link to aren't working right now :( I followed  the instructions at [Backports section]("http://backports.ubuntuforums.org/wiki/index.php/Main_Page") of the ubuntu wiki, but their repository didn't work either. I'm still seeing the latest version of Firefox available as v 1.0.8 where as the latest stable version is something like FF v 1.5.X.X **Any idea what to do**?


Check the dates on this post, it's about a year and a half old. This was posted when Warty was in release candidate.

---

