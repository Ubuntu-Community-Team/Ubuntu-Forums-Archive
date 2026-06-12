---
title: "How do you upgrade to 12.04?"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by carega on 2012-04-23
Hi there

I have never upgraded ubuntu before. I'm currently using 10.10 but it has already warned  me that it is no longer being supported. What I want to know is what's going to happen to all my software and documents when I upgrade, are they going to be deleted? what about the personal settings I have on 10.10, will everything be reset? Any answers would be appreciated.

---

### Post by UnknownFearNG on 2012-04-23
Instead of doing an upgrade via update-manager, I think if you download a LiveCD of 12.04, it does give you the option to upgrade from 11.10. I think it keeps all your files and upgrades your applications to 12.04. Don't quote me on that as I've never done it, just wishful thinking :)

---

### Post by PhantomTurtle on 2012-04-23
It does keep your files and programs, but I would backup any important stuff. oh and it can be done through update manager when 12.04 is released or with a live cd.

---

### Post by audiomick on 2012-04-23
Bear in mind that 10.10 will not directly upgrade to 12.04. 10.04, the last LTS version, would do so, but 10.10 wont. It must go through 11.04 and 11.10 first. It may be quicker to do a fresh install. 

If you do a fresh install, you will need to copy out all your data on to an external drive. If you want to keep your config files, you will need to copy out the hidden files as well. To see them, you need to enable "view hidden files" in the "view" menu of the file manager.

Another option is to create a seperate partition for your /home folder.
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")
after which you can do a fresh install and re-use the new /home partition.

Whatever you choose to do, you should back up really important files before you start.

If you choose to upgrade with the upgrade manager through the various versions, let it do all the updates it wants to do before you go on to the next version. It will be time consuming, but it is safer that way.

---

### Post by wbosher on 2012-04-23
I've been using 12.04 for a few weeks now, updating regularly. When it is officially released in a few days, will I need to do a fresh install or just carry on as I'm doing - updating daily?

---

### Post by Bartender on 2012-04-23
If you have an external device for backingup your personal data, a fresh install of 12.04 would in all likelihood be the superior method.

---

### Post by audiomick on 2012-04-23
I'd do it fresh too. I believe that it is officially "safe" to just upgrade, but I'm a bit sceptical. ;)

---

### Post by bodhi.zazen on 2012-04-23
> **carega said:**
> Hi there

I have never upgraded ubuntu before. I'm currently using 10.10 but it has already warned  me that it is no longer being supported. What I want to know is what's going to happen to all my software and documents when I upgrade, are they going to be deleted? what about the personal settings I have on 10.10, will everything be reset? Any answers would be appreciated.

It is going to be easier, faster, less error prone, less time, and less bandwidth to do a fresh install.

You can either back up your data, do a fresh install, and then restore your data, or my advice would be to dual boot.

boot 12.04, resize your 10.10 partition to make space for 12.04, install 12.04, boot 12.04, move any data or settings you need from 10.10 to 12.04.

IMO there are significant enough changes, at least to gnome, that I doubt you can keep your settings. Of course other settings, such as in .ssh/ , .bashrc, .vimrc, etc should be fine.

---

### Post by Krytarik on 2012-04-23
> **wbosher said:**
> I've been using 12.04 for a few weeks now, updating regularly. When it is officially released in a few days, will I need to do a fresh install or just carry on as I'm doing - updating daily?
The latter. ;-)

Regards.

---

### Post by 3rdalbum on 2012-04-23
On the Ubuntu installer it will give the option to "Upgrade". This is actually a fresh install, but it preserves your existing home folder and settings. These will work fine in 12.04 but of course many of the desktop settings will be irrelevent in Unity.

If you have a pre-release version of Ubuntu 12.04 you just run the normal updates as you would for a released version and you will be updated to the final release. A fresh install is unnecessary, there are only a few packages of difference and these will get updated.

---

### Post by wbosher on 2012-04-25
Thanks for the replies guys. That's going to save me a lot of time and messing around with backups and reinstalling apps. :)

---

### Post by ericpeac0ck79 on 2012-04-25
I was on 10.04 LTS x64... had it set up and customized great....
I don't really like the unity desktop and haven't liked what i've seen of 11.10, etc... but i figured if 12 is the next LTS I should go ahead and upgrade.... ick....
of course i backed up my personal folder stuff to another hdd, but i also exported a list of my current installed packages to a txt file.
```
 dpkg --get-selections > ~/my-packages 
```the upgrade download was taking way too long, so i downloaded a .iso of Precise Pangolin and booted off of it.
there is the option to upgrade the current install when you choose install.
this didn;t take too long.
when it was done and i got logged in, i saw that less than half of my programs were still there.

the most important VMWare Workstation 8 was totally gone!

arrgh.
i tried to reinstall and got several errors which i didn't bother to read fully.
i tried reinstalling from the original installation file i had but still got errors.

so i've done a full fresh install.

i'm most of the way thru reinstalling my packages now, 
```
 sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade 
``` (i did edit that list before running this code... why would i want to install kernel 2.3 on PP? haha)

.... it's slow going and frustrating, but such is life :lol:

anyway, that's my .02

---

### Post by ericpeac0ck79 on 2012-04-25
> **ericpeac0ck79 said:**
> I was on 10.04 LTS x64... had it set up and customized great....
I don't really like the unity desktop and haven't liked what i've seen of 11.10, etc... but i figured if 12 is the next LTS I should go ahead and upgrade.... ick....
of course i backed up my personal folder stuff to another hdd, but i also exported a list of my current installed packages to a txt file.
```
 dpkg --get-selections > ~/my-packages 
```
........
so i've done a full fresh install.

i'm most of the way thru reinstalling my packages now, 
```
 sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade 
``` (i did edit that l

ok,[SIZE=2]_***DON'T DO THAT***_[/SIZE] if you don;t know exactly what you are doing (as is the case of the person typing this)
it's still not done, but i REALLY don't like some of the things i just saw scroll by on my terminal window.... example "removing ubuntu-desktop"

eek, i think i might have hosed this fresh install.... i'll find out in a bit i think..... :confused:

---

### Post by maknesium on 2012-04-26
> **carega said:**
> Hi there

I have never upgraded ubuntu before. I'm currently using 10.10 but it has already warned  me that it is no longer being supported. What I want to know is what's going to happen to all my software and documents when I upgrade, are they going to be deleted? what about the personal settings I have on 10.10, will everything be reset? Any answers would be appreciated.


If you would like to have a step by step upgrade guide with screenshots, maybe try:

[http://www.maknesium.de/upgrade-ubuntu-from-11-10-oneiric-ocelot-to-12-04-lts-precise-pangolin](http://www.maknesium.de/upgrade-ubuntu-from-11-10-oneiric-ocelot-to-12-04-lts-precise-pangolin)

---

