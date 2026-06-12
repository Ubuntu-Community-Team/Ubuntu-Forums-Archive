---
title: "Need some advice for an old machine"
date: 2008-05-07
forum: Other OS Talk
---

### Post by kk0sse54 on 2008-05-07
Was talking to my friend on the phone yesterday and he was telling me about an old dell dimension that he was going to throw away and I said that i would take it instead as it was a perfectly fine working computer except for the fact that xp is so painfully slow that it's almost impossible to use right now. I want to  install a lightweight Linux distro and breath some new life in to it. All that I know of the specs so far is that it has 256MB RAM and a 40GB HD. I was thinking of installing fluxbuntu or maybe arch. Does anyone have any other distros they think might work  better?

---

### Post by tdrusk on 2008-05-07
> **C!oud said:**
> Was talking to my friend on the phone yesterday and he was telling me about an old dell dimension that he was going to throw away and I said that i would take it instead as it was a perfectly fine working computer except for the fact that xp is so painfully slow that it's almost impossible to use right now. I want to  install a lightweight Linux distro and breath some new life in to it. All that I know of the specs so far is that it has 256MB RAM and a 40GB HD. I was thinking of installing fluxbuntu or maybe arch. Does anyone have any other distros they think might work  better?
This is my trick for older machines especially with that much ram.

Install Debian Etch and when the tasksel comes up just select standard system (and laptop if you are using this for a laptop).

Then install kde. The whole package. The whole thing is an excellent metapackage.

When the wizard comes up tell it that you don't want much eye candy. Then when you boot into your system go into Konqueror and go to settings>configure konqueror. Go to performance, and preload it. 

Use koffice, because it loads a buttload faster than openoffice. You should have everything you need with the rest of the kde apps.

I used to dislike KDE before I got used to it and realized how fast the system I just described was.

---

### Post by kk0sse54 on 2008-05-07
Thanks I'll check it out as for KDE or GNOME i don't like KDE much but it won't matter for me here if I can get a fast enough stable system and then I'll give it to my little sister.

---

### Post by wolfen69 on 2008-05-07
ive installed xubuntu on machines with similar specs with good results. use the alternate cd to install.

---

### Post by prshah on 2008-05-07
> **C!oud said:**
> Was talking to my friend on the phone yesterday and he was telling me about an old dell dimension that he was going to throw away and I said that i would take it  All that I know of the specs so far is that it has 256MB RAM and a 40GB HD. I was thinking of installing fluxbuntu or maybe arch. Does anyone have any other distros they think might work  better?

I use xubuntu on many many old machines, with RAM as low as 128 Mb. It's a comfortable, though not stellar, experience.

I also have a bunch of 486, Pentium and CeleronA machines, with RAM ranging from 16Mb~64Mb, on which I run DSL.

For your machine, xubuntu should do just fine, and if you have a decent graphics card that does not share memory, even ubuntu will click.

---

### Post by kk0sse54 on 2008-05-07
I have used xubuntu before and not only did I have problems but to me by far it's the ugliest which was why I was looking into fluxbuntu as a possibility.

---

### Post by smoker on 2008-05-07
this may be a worth a look:
[http://www.mypclinuxos.com/doku.php/news:minime-2008](http://www.mypclinuxos.com/doku.php/news:minime-2008)
>  Here is a little MiniMe 2008 (296mb) you can play with and customize the way you want. Comes with 2.6.22.15 kernel, Alsa 1.0.15 and a very basic KDE 3.5.8 desktop. This is a minimal LiveCD that is bootable, plus it can be installed. Add in your own background, window decoration, localizations, preferred applications and supporting libraries to fully trick out your desktop. In addition you can remaster your own custom version of PCLinuxOS. Have fun! 

---

### Post by kk0sse54 on 2008-05-07
Thanks smoker that is awesome. Definitely something I'm going to look into.

---

### Post by funrider on 2008-05-07
recently i gave my p4 2.2 a second life by getting extra ram i found from PC neighbors threw away. Now that i have 1GB on it i am loading ubuntu 8.04 32bit on it. (yea yea i know it isnt really old but it is running ddr ram only)

my plan was having this box the box sitting in my living room as a media center. I am going to load all my emulators and roms from my major PC to there as well as the mp3 collections. It will hook to my living room speak system as well for some not-so-serious movie time. I will also use this box for bit torrents.

the major problem was that it is not able to connect to the internet either from the mobo lan port or the one from the pci card. spent two weeks and got no luck. I am going to get another card for more testing (doh should have got the lan card from that machine as well, doh)

---

### Post by stream303 on 2008-05-08
Another option is to do it yourself using the server install as a base to lay everything else on.  Who needs customized distros when you can pick exactly what you want? :)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by kk0sse54 on 2008-05-08
Update: Tried out the PClinuxOS MiniMe, thought it was a great idea but unfortunately it's still way too slow. Synaptic takes forever to load and konquerer is slow as molasses. Will still the keep the CD and try to play around with it on a different computer. Next I'm going to try out Debian Etch and the alternative Ubuntu server iso see if it works out.

---

### Post by cardinals_fan on 2008-05-08
Zenwalk

---

### Post by RedSquirrel on 2008-05-08
The other way of doing an Ubuntu minimal installation:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by jesusfreak107 on 2008-05-09
Get Puppy Linux.  It is quite speedy on my 700MHz 192MB RAM laptop.

---

### Post by MONODA on 2008-05-09
checkout: [http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/)

---

### Post by maybeway36 on 2008-05-09
You might not need to download the server iso, you can use the alternate CD to install the base system also.
I would recommend doing a Puppy frugal install as another boot option. You can't really go wrong.

---

### Post by kk0sse54 on 2008-05-09
Thanks everybody for all the help, I installed and am currently running puppy Linux. Works great, it's fast and stable. Also thank you to MONODA for that link, it gave me some great ideas so if my sister can't make any use out of this machine I'll try one of those.:)

---

### Post by LaRoza on 2008-05-09
> **C!oud said:**
> Thanks everybody for all the help, I installed and am currently running puppy Linux. Works great, it's fast and stable. Also thank you to MONODA for that link, it gave me some great ideas so if my sister can't make any use out of this machine I'll try one of those.:)

For a distro that worked well on an old machine that had issues with everything else (the old computer that is in my blog) I used Wolvix. It is supposed to be a live distro, but it works very well installed.

The packages are up to date and there are two versions (or more). Its KDE handles very well also, although I am not a KDE user.

---

### Post by Ripfox on 2008-05-10
> **LaRoza said:**
> For a distro that worked well on an old machine that had issues with everything else (the old computer that is in my blog) I used Wolvix. It is supposed to be a live distro, but it works very well installed.

The packages are up to date and there are two versions (or more). Its KDE handles very well also, although I am not a KDE user.

Wolvix (even cub) seems to run like a dog (no pun) on my old machines. Since I discovered Dragon Puppy Jr. I have not looked back for old machines. It is Puppy with XFCE, and it rocks the pants off anything I've used.

Edit: here's a working link as the dev's link seems to be dead [http://www.puppylinux.ca/puppyfiles/custom/DragonPuppy-2-Junior.iso](http://www.puppylinux.ca/puppyfiles/custom/DragonPuppy-2-Junior.iso)

---

