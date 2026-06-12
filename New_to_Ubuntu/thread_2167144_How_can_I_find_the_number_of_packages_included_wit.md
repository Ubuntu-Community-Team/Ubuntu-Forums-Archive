---
title: "How can I find the number of packages included with a given distro?"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by jeriko2 on 2013-08-12
I've done some searching and haven't found any solid answers on this.  Are the free and supported "Main" packages of Ubuntu, for example, included in the install?  As another example, looking at the x86_64 architecture packages of Arch Linux, [4500 are listed]("https://www.archlinux.org/packages/?sort=&arch=x86_64&q=&maintainer=&flagged=").  Are all 4500 packages included in the install or are there 4500 packages available to install, with only some in the list (Core?) being included?

My main reason for asking is that I'm trying to find a Linux distro that is immediately usable and functional straight off, without it having extra, non-necessary software.  From what I read, Java can't be included for legal reasons, but I wouldn't want it to be anyway for security reasons; legal restrictions may not be an issue with other insecure software, however.

---

### Post by cortman on 2013-08-12
Debian (and therefore, Ubuntu as well, roughly) has some 40,000 packages.
But no distro comes with *all* the packages from the repository installed!

> **jeriko2 said:**
> 
My main reason for asking is that I'm trying to find a Linux distro that is immediately usable and functional straight off, without it having extra, non-necessary software.

That sounds like about any major distro these days. What's wrong with Ubuntu, Debian, Fedora, Slackware, Mint, (ad infinitum)? They all come usable and fucntional OOTB, with useful software already installed. And if you don't like any of the preinstalled packages, uninstalling is just a click (or command) away.

---

### Post by jeriko2 on 2013-08-12
> **cortman said:**
> Debian (and therefore, Ubuntu as well, roughly) has some 40,000 packages.
But no distro comes with *all* the packages from the repository installed!

That sounds like about any major distro these days. What's wrong with Ubuntu, Debian, Fedora, Slackware, Mint, (ad infinitum)? They all come usable and fucntional OOTB, with useful software already installed. And if you don't like any of the preinstalled packages, uninstalling is just a click (or command) away.

This didn't provide me with much information.  I know there are a very large number of packages available for major distros, but I'd like to know what to look for in their respective package searches (if they have one) to know what comes with a fresh install.

For example, Linux Mint comes with Flash installed.  While it may be easy enough to uninstall Flash, I'd prefer the approach of getting a distro that is fairly trim, but affords me the baseline to easily acquire what I need via its package manager.  I'm also curious to know how Mint can include Flash, but Ubuntu legally can't (if this is still true, since Adobe partnered with Canonical at some point).

I never said anything was wrong with the distros you mentioned either, but if you had truly intended to address my question, you would've told me how to find out what comes with a fresh install of these distros and I could've chosen from there.

Nonetheless, thank you for your reply.

---

### Post by Cheesemill on 2013-08-12
The method for finding the number of installed packages varies depending on the package management system the distro uses.

Debian/Ubuntu based distros...
```
dpkg --get-selections | wc -l
```

Arch and derivatives...
```
pacman -Q | wc -l
```

Red-Hat/Fedora based distros...
```
rpm -qa | wc -l
```

---

### Post by bapoumba on 2013-08-12
[http://releases.ubuntu.com/raring/ubuntu-13.04-desktop-i386.manifest](http://releases.ubuntu.com/raring/ubuntu-13.04-desktop-i386.manifest)

All the other 13.04 versions are here, just look at the manifest files: [http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)
Same for other releases, on their own pages : [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Cheesemill on 2013-08-12
So that's 1599 packages for a 13.04 desktop installation. Wow.

On my desktop Arch installation which has ***a lot*** of applications installed I get this...
```
rob@arch:~$ pacman -Q | wc -l
971
```

I think one of the main reasons for this massive difference is that by default all of a packages recommendations are installed with Ubuntu, whereas they aren't with Arch.

---

### Post by bapoumba on 2013-08-12
> **Cheesemill said:**
> So that's 1599 packages for a 13.04 desktop installation. Wow.

On my desktop Arch installation which has ***a lot*** of applications installed I get this...
```
rob@arch:~$ pacman -Q | wc -l
971
```

I think one of the main reasons for this massive difference is that by default all of a packages recommendations are installed with Ubuntu, whereas they aren't with Arch.

Seems about right :
```
dpkg --get-selections | wc -l
1799

```
Not a fresh install, 2 weeks old and I have added a few things I need.

---

### Post by Bashing-om on 2013-08-12
sysop@1304mini:~$ dpkg --get-selections | wc -l
752
sysop@1304mini:~$ 

Minimal install, xfce4 for the desktop, only a few additional packages installed.

It all depends on what you want of your operating system.

---

### Post by cortman on 2013-08-12
> **jeriko2 said:**
> This didn't provide me with much information.  I know there are a very large number of packages available for major distros, but I'd like to know what to look for in their respective package searches (if they have one) to know what comes with a fresh install.

For example, Linux Mint comes with Flash installed.  While it may be easy enough to uninstall Flash, I'd prefer the approach of getting a distro that is fairly trim, but affords me the baseline to easily acquire what I need via its package manager.  I'm also curious to know how Mint can include Flash, but Ubuntu legally can't (if this is still true, since Adobe partnered with Canonical at some point).

I never said anything was wrong with the distros you mentioned either, but if you had truly intended to address my question, you would've told me how to find out what comes with a fresh install of these distros and I could've chosen from there.

Nonetheless, thank you for your reply.

Your question was rather ambiguous; are you asking how many packages are available for a given distro in said distro's repository, or are you asking how many and what packages come bundled with the OS itself? For the latter it is not hard to find out. Just off the top of my head, something like

```
dpkg-query -l | wc -l
```

will give you a close estimate.
I don't know of any distro that posts a list of all packages included in it (at least not in any obvious place) but you are welcome to research it.
Why Mint can include Flash may have something to do with the fact that it is developed in France? Not sure. Again, I'm sure the info is out there somewhere.

---

### Post by jeriko2 on 2013-08-12
> **Cheesemill said:**
> The method for finding the number of installed packages varies depending on the package management system the distro uses.

Debian/Ubuntu based distros...
```
dpkg --get-selections | wc -l
```

Arch and derivatives...
```
pacman -Q | wc -l
```

Red-Hat/Fedora based distros...
```
rpm -qa | wc -l
```

This was something I had run across, but I would have to have the distro either installed or live I'd imagine before I could obtain this info.  Unfortunately this approach would be cumbersome as I'd need to do it for each distro and there are a lot out there.

> **bapoumba said:**
> [http://releases.ubuntu.com/raring/ubuntu-13.04-desktop-i386.manifest](http://releases.ubuntu.com/raring/ubuntu-13.04-desktop-i386.manifest)

All the other 13.04 versions are here, just look at the manifest files: [http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/)
Same for other releases, on their own pages : [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

This is probably the closest thing to what I'm looking for.  This would be the manifest for that .iso then?  I didn't find this while browsing the site, but I was on [http://packages.ubuntu.com/](http://packages.ubuntu.com/); is there a way to tell from this page what is included?  Unrelated: Firefox hangs for a good 5 seconds when trying to search "[Main]" on that page, due to the fact that it can't turn up anything for it.  Is that because script is used to load the page dynamically and Firefox chokes a bit on it?

> **Cheesemill said:**
> So that's 1599 packages for a 13.04 desktop installation. Wow.

On my desktop Arch installation which has ***a lot*** of applications installed I get this...
```
rob@arch:~$ pacman -Q | wc -l
971
```

I think one of the main reasons for this massive difference is that by default all of a packages recommendations are installed with Ubuntu, whereas they aren't with Arch.

Seems like a few of us are learning something new!  So what is the significance of a package's recommendations?

> **Bashing-om said:**
> sysop@1304mini:~$ dpkg --get-selections | wc -l
752
sysop@1304mini:~$ 

Minimal install, xfce4 for the desktop, only a few additional packages installed.

It all depends on what you want of your operating system.

Basically I'm looking for a distro that doesn't need to play games, is capable of web-browsing, basic word-processing, etc. and, should the need arise, affords me the ability to find and install software in a simple manner.  By simple manner I mean it will acquire all of its necessary dependencies and such.  If I'm not mistaken, Ubuntu includes LibreOffice; I don't need nor do I want this.  A "plain Jane" text editor suits me and if I need something more robust, I'll go to the package manager.

---

### Post by oldfred on 2013-08-12
Then maybe you want minimal install which is just kernel & enough to get on Internet to download what you really want.

 [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
Install script for minimal
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by jeriko2 on 2013-08-12
> **jeriko2 said:**
> I've done some searching and haven't found any solid answers on this. ** Are the free and supported "Main" packages of Ubuntu, for example, included in the install**?  As another example, looking at the x86_64 architecture packages of Arch Linux, [4500 are listed]("https://www.archlinux.org/packages/?sort=&arch=x86_64&q=&maintainer=&flagged="). ** Are all 4500 packages included in the install or are there 4500 packages available to install, with only some in the list (Core?) being included**?

My main reason for asking is that **I'm trying to find a Linux distro that is immediately usable and functional straight off, without it having extra, non-necessary software**.  From what I read, Java can't be included for legal reasons, but I wouldn't want it to be anyway for security reasons; legal restrictions may not be an issue with other insecure software, however.

> **cortman said:**
> Your question was rather ambiguous; are you asking how many packages are available for a given distro in said distro's repository, or are you asking how many and what packages come bundled with the OS itself? For the latter it is not hard to find out. Just off the top of my head, something like

```
dpkg-query -l | wc -l
```

will give you a close estimate.
I don't know of any distro that posts a list of all packages included in it (at least not in any obvious place) but you are welcome to research it.
Why Mint can include Flash may have something to do with the fact that it is developed in France? Not sure. Again, I'm sure the info is out there somewhere.

I've bolded the sections that I hoped would make my question as unambiguous as possible.  The way you phrased your question, "are you asking how many packages are available..." is phrased much in the same way my original statement was.

As far as the command is concerned, I'd have to do this for each distro which would be quite a chore.  I'm slowly beginning to get the impression though that it may be the only fool-proof way, as many distros likely don't make a list of packages in the OS install file available online; yet another hurdle is deciphering from lists they do make available which packages are included in a fresh install.

Finally, I have researched it and will continue to do so, but sometimes it works better to seek out a more direct response.

---

### Post by jeriko2 on 2013-08-12
> **oldfred said:**
> Then maybe you want minimal install which is just kernel & enough to get on Internet to download what you really want.

 [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
HowTo Achieve "Ubuntu-Desktop-Minimal" 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
Install script for minimal
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

Thanks Fred.  After bashing-om said something about it, I figured it was something worth looking at a bit.  Hopefully I'll find a manifest for this as well.

---

### Post by Bashing-om on 2013-08-13
@jeriko2; Weelll,
There is a lot to be said in a positive light for a minimal install and roll you own ...
The result is mean, lean and fast !
If you choose to install a standard install .. then you are guaranteed that all the applications integrate well with few -if any - problems. When you "roll your own" whether from source or binary .. it is on you to meet all the dependencies .. the applications may be written in different languages and protocols; for instance themes and icons associated with any particular ap ..GTK2/GTK3 engines ... -> gedit as "text editor of choice" screams and hollers it does not have the themes nor icons it is looking for ... it is on you to find a solution. The package manager does a great job, but it can not do everything !This approach is not for the faint at heart.
The further one progresses down to the level of compiling the more control one may exercise; but, it requires a huge amount of knowledge as well as skill.

Hey, I appreciate all the effort the developers put into the desk top environments, I really like unity as a concept and it's implementation; but, I value simplicity and work-ability more. My world is a desk top system powerful enough to do anything my little mind can conceive of. As needed I acquire the skills to relate this system with any other pieces of hardware or software that I desire. I have a need to know .. and I expect to work at low levels to attain my goals. The same can not be said for many, who just want it to work "out of the box" -> standard desk top install !

Jump into our world .. get wet all over.. look around and by then you are able to make an informed decision as to what you want. After all, it only takes 30 minutes to wipe/install (you do keep backups, now don't you ) and away you go again ...

[INDENT][INDENT]ubuntu, free, do it your way[/INDENT][/INDENT]

---

### Post by bapoumba on 2013-08-13
> **jeriko2 said:**
> 
This is probably the closest thing to what I'm looking for.  This would be the manifest for that .iso then? 
Just to answer that question : yes, these are the files on the desktop live cd.

---

