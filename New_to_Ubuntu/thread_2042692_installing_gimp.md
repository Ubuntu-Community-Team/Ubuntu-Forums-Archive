---
title: "installing gimp"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by smoothcriminal17 on 2012-08-15
i'v dowloaded gimp-2.8.0.tar.bz2, moved it to a folder made by me
how do i install it now ?
i know DOS bt nothing about terminal
also software centre has issues lately
the info of alredy installed proggrams is available, bt when i try 2 install sumthing new, i click more info & it says source is 'universe' & some other things, dosent evn show screenshot or size

---

### Post by smoothcriminal17 on 2012-08-15
also a few months after installing ubuntu, applets started to go missing, i looked in administrative tools & panel's preferences

---

### Post by newb85 on 2012-08-15
When you say "when I try to install something new", do you mean when you try to install something from the repositories, or only when you try to install from a .tar file?

Could you be a little more specific about the message Software Center is giving you?

Have you considered installing Gimp 2.8 from a repository, rather than from a .tar file?

---

### Post by newb85 on 2012-08-15
> **smoothcriminal17 said:**
> also a few months after installing ubuntu, applets started to go missing, i looked in administrative tools & panel's preferences

Again, can you be more specific?  What applets started to go missing?

---

### Post by smoothcriminal17 on 2012-08-15
when i tried 2 install from the sofware cente, i clicked on more info, it only showed "available from the "main" source" & no other details
i treid wid some other softwares, same thing happens, only source may b different
i had upgraded mozilla by downloading the tar & extracting its contents where the older version was installed & it worked
bt jst by extracting, gimp wont run

what is a repository ?

---

### Post by smoothcriminal17 on 2012-08-15
the gnome eyes, the applet showing network strength, the power button, hide all windows button
also mobile network selection from the panel

---

### Post by newb85 on 2012-08-15
> **smoothcriminal17 said:**
> when i tried 2 install from the sofware cente, i clicked on more info, it only showed "available from the "main" source" & no other details
i treid wid some other softwares, same thing happens, only source may b different
i had upgraded mozilla by downloading the tar & extracting its contents where the older version was installed & it worked
bt jst by extracting, gimp wont run

what is a repository ?

Ah...okay, crash course time.  First, Ubuntu (like most Linux distros) uses a package manager, which is basically a software package designed to handle the installation, update, and removal of all other software packages.  The Software Center is a graphical interface for the package manager.

Now, the preferred way to install software is to use repositories (sometimes called repos or ppas), which are basically online software sources that the package manager interfaces with directly.  By default, Ubuntu comes with a few repositories set up, and more can be added to the list.  Adding repositories can expand the list of available packages, or make the ones already there more up-to-date.

Gimp is in the "Main" repository, but the version contained there isn't the newest version.  There are other repos which contain newer versions.  For example, adding the webupd8 ppa should bring you up to 2.8, as well as add many plugins.  Issue the following commands in the terminal:

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gimp-plugin-registry
```

(If you don't want to install the extra plugins, you may omit the last line.)

---

### Post by newb85 on 2012-08-15
> **smoothcriminal17 said:**
> the gnome eyes, the applet showing network strength, the power button, hide all windows button
also mobile network selection from the panel

It's been a couple years since I've used an environment with the gnome-panels, but if I remember right, you can add the applets you've mentioned by right-clicking where you want them and clicking "Add to panel...", or something like that.

By the way, are you really still using Ubuntu 10.10?  Have you considered upgrading?

---

### Post by philinux on 2012-08-15
> **smoothcriminal17 said:**
> i'v dowloaded gimp-2.8.0.tar.bz2, moved it to a folder made by me
how do i install it now ?
i know DOS bt nothing about terminal
also software centre has issues lately
the info of alredy installed proggrams is available, bt when i try 2 install sumthing new, i click more info & it says source is 'universe' & some other things, dosent evn show screenshot or size

I assume you know that 10.10 reached end of life this April.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

---

### Post by Kickinthedoor on 2012-08-15
I do some fairly heavy graphic design work for my silk screening operation and have uses gimp but honestly i think your better off running photoshop in wine. Just my opinion though

---

### Post by smoothcriminal17 on 2012-08-15
I'v tried add 2 panel, those applets werent there
when i booted i gt a message dat this & dat applet was missing

i'm using 10.10 cuz i got celeron d, 256 ram piece of junk bought in 2006

i did find a repository :)
the synaptic package manager, it gave gimp 2.6, bt i can go with dat

thnx all

---

### Post by newb85 on 2012-08-15
> **smoothcriminal17 said:**
> I'v tried add 2 panel, those applets werent there
when i booted i gt a message dat this & dat applet was missing

i'm using 10.10 cuz i got celeron d, 256 ram piece of junk bought in 2006

i did find a repository :)
the synaptic package manager, it gave gimp 2.6, bt i can go with dat

thnx all

You might search for the applets in synaptic.  I'm not certain they're independent packages, but it's worth a shot.

With your system specs, you definitely should NOT run photoshop on WINE.

10.10 is no longer supported.  You no longer receive security updates, or for that matter any updates that come through the official repositories.  It would be a good idea to move to something newer and currently supported.

Your machine falls a little short of the system requirements for any version of Ubuntu after 10.10, so I recommend you take a look at a couple lighter official variants.  The Ubuntu developers offer the same support for both Xubuntu and Lubuntu.  12.04 is a LTS for all three, so they will be supported until April 2015 (by which time you will probably need to retire that machine, anyway).

You could run Lubuntu and Xubuntu from a LiveCD and see which one works better/you like best.  Xubuntu 12.04 recommends 512 MB RAM, but says that 256 should work.  Lubuntu is even lighter.

---

### Post by GreatDanton on 2012-08-15
Install Lubuntu, since it's made for machines like yours. Xubuntu is not so lightweight any more.

---

### Post by walker195 on 2012-08-15
you can install gimp through Ubuntu software center

---

### Post by audiomick on 2012-08-15
And learn to use proper English spelling and punctuation.

---

### Post by Miljet on 2012-08-15
> 12.04 is a LTS for all three, so they will be supported until April 2015 

I beg to differ with you, but Lubuntu 12.04 is NOT a LTS version.

This quote is from this link:  [https://wiki.ubuntu.com/Lubuntu/Announcement/12.04](https://wiki.ubuntu.com/Lubuntu/Announcement/12.04)
> Unlike Ubuntu, Lubuntu 12.04 is not a LTS, this version will be supported for 18 months. However, a lot of work has been done to improve the stability of the system. 

---

### Post by newb85 on 2012-08-15
@ Miljet - My mistake.  I'm not sure where I got that idea.

@ walker195 - Actually, smoothcriminal17 wanted to install a more up-to-date version of Gimp than the one in the Main repo.

@ audiomick - Yes, the guidelines say to use proper grammar and punctuation.  They also say be friendly to everyone.   :)

---

### Post by newb85 on 2012-08-24
> **newb85 said:**
> Now, the preferred way to install software is to use repositories (sometimes called repos or ppas), which are basically online software sources that the package manager interfaces with directly.  By default, Ubuntu comes with a few repositories set up, and more can be added to the list. 

I seem to have misspoken here.  There is actually a difference between repos and ppas.  PPA stands for Personal Package Archive, while the Repositories are archives set up by the distribution developers.  The repos are set up (though not necessarily activated) by default, while PPAs can be added.  Aside from that, they interact with the package manager in much the same way.

---

### Post by SeijiSensei on 2012-08-24
Gimp will be a performance nightmare on a machine with just 256M of memory regardless of which flavor of Ubuntu you choose to install.  Like any graphics editor it uses a lot of memory to carry out image transformations.  You can try to end-run this problem by having a large swap partition or file, but then your machine will spend its time thrashing the hard drive as it reads and writes to virtual memory on disk.

If you must run gimp on this machine, I'd add at least another 512M of memory unless you're a *very* patient person.

---

