---
title: "Upgrading to 13.04 from 12.10 on ChromeBook (Acer C7)"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by dalethomasnyc on 2013-04-25
[SIZE=2][FONT=arial]
Hi guys - this is my absolute first post on this forum.  I hope I provide you with enough information to help. 

I am running an Acer C7 Chromebook.  I was able to successfully install 12.10, dual boot, to the system.  This is my first experience with Linux.  I love it so far.  

I know would like to upgrade to 13.04 and I could use some help.  I am really looking for a dumb down step by step guide. 

I did find this resource [http://marcin.juszkiewicz.com.pl/2013/02/16/how-to-update-chrubuntu-12-04-to-ubuntu-13-04/](http://marcin.juszkiewicz.com.pl/2013/02/16/how-to-update-chrubuntu-12-04-to-ubuntu-13-04/)

However, I am not sure how to do even this "[COLOR=#444444]Open terminal (Ctrl+LAlt+t), get root and edit APT sources so they will point to “raring” instead of “precise”." 

Can anyone provide any guidance?  

Appreciate the help. [/COLOR][/FONT][/SIZE]

---

### Post by ibjsb4 on 2013-04-25
First I would wait a few days, the servers will be loaded down for a while and upgrading your system could be a very, very slow process.

Here's some links to read up on.

[https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes?action=show&redirect=RaringRingtail%2FTechnicalOverview](https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes?action=show&redirect=RaringRingtail%2FTechnicalOverview)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=upgrade+12.10+to+13.04&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=upgrade+12.10+to+13.04&sa=Search&cof=FORID:9)

And welcome to the forums :)

---

### Post by deadflowr on 2013-04-25
^+1

The release day is the worst day to run a network upgrade.
This is from experience.
The easiest way to upgrade is through the updater.
Sometimes though, you have to change a settings in the software sources
Notify me of new ubuntu versions. This sometimes is set for LTS releases.
If so, change it to any new release.
You can get to the software sources by running
```
software-properties-gtk
```

Normally when it is set up, simply running the updater will point you to the new release.(Look at the top of the updaters update page)
Of, course this is the first release using software updater over the old update manager, so I don't know how well it will work.

---

### Post by dalethomasnyc on 2013-04-25
Cool thanks guys!!  I should have also added that I was able to successfully install a Beta to my desktop.  It's just my Chromebook that is a pain.

I guess I will wait a couple of days and try to upgrade through the system.

---

### Post by Curtis6767 on 2013-04-25
> **dalethomasnyc said:**
> Cool thanks guys!!  I should have also added that I was able to successfully install a Beta to my desktop.  It's just my Chromebook that is a pain.

I guess I will wait a couple of days and try to upgrade through the system.

Is that a Beta of 12.10 or 13.04? If it's 12.10 then the first thing you need to do is update it.

Hit ctrl +alt+t at the same time to open a terminal and then enter the following. Just copy and paste it at the prompt and hit enter. You'll then be asked for your password, which will not show up as you type. After you type your password, then hit Enter. After a while you'll get another prompt asking if you want to install the upgrades. Do that and the first batch of upgrades will down load and install. You'll most likely be asked a second time if you want to install another set of upgrades. Do that and after all that, reboot and your 12.10 will be good to go and ready for 13.04.

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

```

This will bring your current version up to date, which you need to do before upgrading to 13.04. After that, and at your convenience, open the Software Updater and look for the button that says something like "Upgrade Available." Click on that and your 12.10 will morph into 13.04. 

GL

---

