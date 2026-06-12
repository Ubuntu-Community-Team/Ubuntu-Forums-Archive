---
title: "Gnome 14.4  and gnome 3.12  im Confused ;("
date: 2014-08-03
forum: New to Ubuntu
---

### Post by firas2 on 2014-08-03
Good day

Can any one please explain what is going on ? because I am very confused  and a Little  tired from reading every thing and trying every thing out ,  for the last 3 days and NOTHING  seems to be working 

I have Gnome 14.4  64X  installed on my Virtual machine   ,  I go to visit gnome look.org  to get some eye-candy    ,  but that is not working out for me to  because it seems the tut  is talking about a complete different version then what I have 

so as i keep searching and reading   I found this   [http://linuxg.net/how-to-install-gnome-3-12-on-ubuntu-gnome-14-04-trusty-tahr/](http://linuxg.net/how-to-install-gnome-3-12-on-ubuntu-gnome-14-04-trusty-tahr/)

how to install gnome 3.12  on gnome 14.4    do i need this ??    is this the reason i am having a hard time to install any thing ??

i dont get it   I would Love if one of the members here explain to me  , what i need to get started with my gnome 14.4  and how to start enjoying it  please

I am  new  and would love to learn 

thank u

---

### Post by coffeecat on 2014-08-03
> **firas2 said:**
> I have Gnome 14.4  64X  installed on my Virtual machine 

So that people can help, please explain what you mean by "Gnome 14.4".

Do you mean standard Ubuntu 14.04, or standard Ubuntu 14.04 with either or both of gnome-shell or gnome-session-fallback installed? Or did you install the [Ubuntu Gnome 14.04 respin](http://ubuntugnome.org/download/)?

---

### Post by firas2 on 2014-08-03
Hi I have installed this   [Ubuntu GNOME 14.04 LTS]("http://ubuntugnome.org/ubuntu-gnome-14-04-lts-is-released/")[FONT=Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#373737]   64x om my VM[/COLOR][/FONT]

[FONT=Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#373737]and i was thinking as I start learning about UBUNTU  i get some nice eye candy  and start doing the necessary installs and updates 

thank u[/COLOR][/FONT]

---

### Post by coffeecat on 2014-08-03
I've added the UbuntuGnome prefix to your thread title which will hopefully attract those able to help you with that.

Good luck!

---

### Post by ajgreeny on 2014-08-03
Just to clarify things for you a bit as you have been confused by all the numbering and nomenclature of things.

You are using the operating system **Ubuntu GNOME 14.04** which uses the desktop environment **gnome 13.10**.  There is no such thing as gnome 14.4.

The link you gave us showed how to add gnome 3.12 to the standard unity version of Ubuntu, and I have no idea about updating gnome 3.10 for gnome 3.12, but I suspect it will not be too big a problem.  However I do not use, and have not used gnome since version 2.# (can't remember exactly which any more), so I am the wrong person to tell you more about this.

---

### Post by firas2 on 2014-08-03
Ok Great  many thanks to both of you

@ajgreeny  many many thanks for clearing that up 

so I will reinstall from fresh to get a new start

any Advice on what version i should Install ?? so i can have a same  version of what every buddy els is using ??

also I think i will go with Kubuntu   is this the same as ubuntu ??  and can i also add some shells and so on ??

many thanks

---

### Post by coffeecat on 2014-08-03
@firas2, I think you need to do a bit of research into the Ubuntu derivatives and their respective desktops. List of official derivatives here with links to their websites:

[http://www.ubuntu.com/about/about-ubuntu/derivatives](http://www.ubuntu.com/about/about-ubuntu/derivatives)

Kubuntu is based on Ubuntu but uses the KDE desktop which is very different from either Unity, the desktop that comes with standard Ubuntu, or Gnome-Shell which is what you have in UbuntuGnome. KDE is very configurable, so it might appeal to you if you like to customise your desktop.

You can start with Ubuntu or any derivative and then install other desktops, which can be chosen at the login page.

---

### Post by firas2 on 2014-08-03
OH   thanks again  now every thing is clearing up 


So Basically  i can install Ubuntu 14.4  and then add  any desktop to it later on  right ??

ok let me do some more reading   that is if my eyes can handle it :)  and see what happens 

I appreciate your help

thank u

---

### Post by buzzingrobot on 2014-08-03
The most recent Ubuntu release is 14.04.1, which is an update to 14.04 (and 14.04 users will be upgraded to it via their normal updates).

A variety of interfaces -- aka Desktop Environments -- are available for Ubuntu in addition to the Unity interface provided by default on Ubuntu.

Some of those interfaces are used by other distributions that use a different interface and remain part of the Ubuntu family.  Kubuntu uses the KDE interface.  Ubuntu Gnome uses the Gnome interface. Xubuntu uses the XFCE interface.  Lubuntu uses LXDE. Beyond the desktop environment, the software that comes with it, and any tuning that might be done, the distributions are all essentially the same.

The availablity of install images that run in "live" mode off a DVD/USBstick means you don't need to install a distribution just to check out its interface.

In addition, a very large number of other unofficial independently made Ubuntu derivative distributions are available.

KDE, Gnome, XFCE, LXDE, etc., can also be installed on an existing Ubuntu installation. Be aware, though, that they are complex collections of software and cleanly removing them after installation can be difficult. (Unless you are extremely short of disk space, I wouldn't remove them.)

Re:  Ubuntu Gnome -- The current Ubuntu Gnome release is based on 14.04 and uses the Gnome 3.10 release. The Gnome 3.12 release can be installed from unofficial and unsupported repositories -- PPA's.  However, before using these PPA's to install Gnome 3.12, you should read  these pages:  [https://wiki.ubuntu.com/UbuntuGNOME/FAQ#Why_Ubuntu_GNOME_is_not_shipped_with_the_latest_version_of_GNOME.3F](https://wiki.ubuntu.com/UbuntuGNOME/FAQ#Why_Ubuntu_GNOME_is_not_shipped_with_the_latest_version_of_GNOME.3F) and [https://wiki.ubuntu.com/UbuntuGNOME/Developers](https://wiki.ubuntu.com/UbuntuGNOME/Developers). Note that only one of those PPA's contains stable software intended for ordinary users to install.

---

### Post by ajgreeny on 2014-08-03
If you really don't want unity, the standard ubuntu desktop environment, there is no point in installing standard ubuntu then adding the desktop you want; just start by installing **Ubuntu GNOME** or **Kubuntu**, or whatever you prefer having read about all of them, and perhaps tried them all in a live system.  If you want to upgrade the gnome 3.10 desktop to gnome 3.12 you can do it by using a ppa repository, but do take note of those links provided by buzzingrobot.

---

### Post by firas2 on 2014-08-03
Thanks 
Ja  that is what i am doing ,  so far I am with[COLOR=#000000] Kubuntu  and checking it out   I have installed   version 14.4  LTS 64X[/COLOR]

---

### Post by firas2 on 2014-08-03
Ok so while i am doing some updates and other software 

I keep getting this   can any one help   thank u

[IMG]http://i60.tinypic.com/292sg8g.jpg[/IMG]

---

### Post by oldos2er on 2014-08-03
There's no trusty (14.04) version for that PPA; I would remove it from your software sources.

---

### Post by buzzingrobot on 2014-08-03
The "404 Not Found" is returned by the server when the requested URL is not available.  The elements in the URL's in your image that begin with "http://ppa.launchpad.net/noobslab..." represent individual directories on that server.  The 404 was sent back because one of those directories can't be found.  

In this case, I believe it's the "trusty" directory that can't be found. If you look here at the page on Launchpad for Noobslab's "Best Malys Themes" ([https://launchpad.net/~noobslab/+archive/ubuntu/malys-themes?field.series_filter=](https://launchpad.net/~noobslab/+archive/ubuntu/malys-themes?field.series_filter=)) and click the "Any Series" dropdown on the middle left, you'll see that no packages are available for Trusty.  And, I don't see any Malys packages at all for Trusty at the primary Noobslab theme collection ([https://launchpad.net/~noobslab/+archive/ubuntu/themes?field.series_filter=trusty](https://launchpad.net/~noobslab/+archive/ubuntu/themes?field.series_filter=trusty).

So, in short, Noobslab has no Mayls themes available for Trusty.

---

### Post by firas2 on 2014-08-03
ok thanks how do i move it ??    and is it any problem just keeping it ??

thanks

---

### Post by buzzingrobot on 2014-08-03
Installing and using ppa-purge will remove that PPA from the list of sources used by your system.  It will also remove any packages installed from the PPA.  It's a character-based tool.  Open a terminal, then, "sudo ppa-purge <name of PPA>".

I've seen it complain when I haven't actually installed anything from a PPA, but it still removed the PPA from the list of sources.

---

### Post by firas2 on 2014-08-04
> **buzzingrobot said:**
> Installing and using ppa-purge will remove that PPA from the list of sources used by your system.  It will also remove any packages installed from the PPA.  It's a character-based tool.  Open a terminal, then, "sudo ppa-purge <name of PPA>".

I've seen it complain when I haven't actually installed anything from a PPA, but it still removed the PPA from the list of sources.

Thanks will try that out

---

