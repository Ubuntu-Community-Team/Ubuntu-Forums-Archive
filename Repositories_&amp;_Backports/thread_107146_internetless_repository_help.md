---
title: "internetless repository help"
date: 2005-12-22
forum: Repositories &amp; Backports
---

### Post by ithinkillgohome on 2005-12-22
I do not have broadband at home and am a complete beginner in the linux thing. I only have a modem, which I have started to try to enable but didnt I may be a little bit confused on this still, do I HAVE to have internet first? Or can I download the repositories and have them local? Or is this pointless? I may not totally understand what repositories do still. heh. Thanks.

---

### Post by towsonu2003 on 2005-12-22
[QUOTE=ithinkillgohome]I do not have broadband at home and am a complete beginner in the linux thing. I only have a modem, which I have started to try to enable but didnt I may be a little bit confused on this still, do I HAVE to have internet first? Or can I download the repositories and have them local? Or is this pointless? I may not totally understand what repositories do still. heh. Thanks.[/QUOTE]
Repositories are online pools where there is software (in .deb debian package format) that you can download and install very easily using a debian tool called apt-get or its front end (much more user friendly) synaptic (System>Administration>Synaptic)... 

as for the offline repos, I am seeing too many of those requests recently and hoping to see a wiki page on that from someone with free time. 

Until than, here are some links you might want to read and get started: 

[https://wiki.ubuntu.com/Repositories?highlight=%28repositories%29](https://wiki.ubuntu.com/Repositories?highlight=%28repositories%29) (info on what repos are)

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto) (a howto)
packages.ubuntu.com (list of packages that are in repos)
[http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862) (another howto)
[http://www.ubuntuforums.org/showthread.php?t=20217&highlight=local+repos](http://www.ubuntuforums.org/showthread.php?t=20217&highlight=local+repos) (very long discussion, may help?)

---

### Post by ithinkillgohome on 2005-12-22
Thanks a bunch. I'll look over it all when I get home from work. I've managed to download some of the deb packages here at work by just going into the pool folder and snagging the ones i wanted. Can I just run these at the command line?

---

### Post by towsonu2003 on 2005-12-22
[QUOTE=ithinkillgohome]Can I just run these at the command line?[/QUOTE]

I'm not sure. It's better to stick with the apt-get procedure. Installing those without making sure that you have all the dependencies will cause a dependency hell, which usually is the nightmare of most linux users...

When I need packages from pool but don't have a connection, I go through the dependency list of each package using packages.ubuntu.com and download each that I don't have in my ubuntu system, and start installing (sudo dpkg -i package.deb) starting from the one I have all the dependencies for. 

In other words:

I want package X

X has dependencies Y, W

Y has depndencies A, B

W has dependencies C, D

I have A and C installed already -> so I need B and D

B has dependencies E, F

D has dependencies G, H, K

I have E, F, G, H -> I need K

K has dependencies T, U

I already have T and U installed (lucky) -> install K

I now have K, G, H, E, F -> install B and D

Now I have A, B, C, D installed -> install Y, W

I now have Y and W -> install X (my target package)

If I have the second (connected) computer (OS wont matter) along with non-connected ubuntu computer, this process takes about 10 minutes (no dependencies required) to 4 hours (install frozen-bubble to fresh installed ubuntu system by checking each dependency one by one).

If you read until here, I am sure you will want to use apt-get procedures now :)

---

### Post by UbuWu on 2006-01-01
You could also get the complete repositories on DVD if you have a dvd-burner at work: [http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

---

