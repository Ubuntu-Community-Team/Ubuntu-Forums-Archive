---
title: "Software Update InRelease"
date: 2014-12-21
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-12-21
I noticed a few days (7 or 8 days) ago that I wasn't receiving many updates when I run the software updater.
I changed repositories to the main repository thinking there might be some sort of problem with the mirror.
Today I ran the software updater again and was told my machine is up to date.

I thought I'd see if there are any messages if I run:
```
sudo apt-get update
```

I noticed that several of the entries have InRelease next to them.  I've not seen this before.  Does anyone know what it means?
```
Ign http://archive.canonical.com trusty InRelease 
Ign http://ppa.launchpad.net trusty InRelease  

```

Is there a way to insure that I am, in fact, up to date?

---

### Post by grahammechanical on 2014-12-21
You are using 14.04 and that is a stable release of Ubuntu. 

> [COLOR=#333333][FONT=Ubuntu Beta]Once an Ubuntu release has been completed and published, updates for it are only released under certain circumstances, and must follow a special procedure called a "stable release update" or SRU.[/FONT][/COLOR]

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Software Updater is a GUI front-end for the apt-get set of commands. The update process includes comparing lists of software versions installed our machine with lists of updated software packages on the Ubuntu servers/repositories. If newer versions of packages have not been put in the repositories then it is because newer versions are not ready or available to put in the repositories.

I am using the development release of 15.04 code named Vivid Veret. I update daily. Some days the download is many mega bytes. For the last two days the download has only been a few mega bytes. It is the weekend. When I run apt-get update I see this:

> Ign [http://archive.canonical.com](http://archive.canonical.com) vivid InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) vivid InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-updates InRelease                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) vivid-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security InRelease 





I do not worry about it. I know that the extras and the backports repositories are not open during the development period and it seems that it also applies to the InRelease repository as well, even though I have no idea what the InRelease repository is used for.

Regards.

---

### Post by GrouchyGaijin on 2014-12-21
Thank you for the reply.

---

