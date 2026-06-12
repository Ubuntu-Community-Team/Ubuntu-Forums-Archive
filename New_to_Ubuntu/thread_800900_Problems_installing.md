---
title: "Problems installing"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by sc4s2cg on 2008-05-20
Hi,

I just made the switch from Vista to XP to Ubuntu and, as you can probably imagine, I'm having a little difficulty adjusting. I've been using XP all my life, about 10 or so years, and now I cannot figure out for the life of me how to install applications.

I realize I have to double click on a file once I extracted everything from the archive, and that after that I need to click "run"...but that's where I stop. I click run but the installation doesn't open. At first I thought that that is just how Ubuntu installs programs, but when I open the program to see if it has updated (in this case firefox 3 b5, wanted to update it to RC1) but it hasn't.

I cannot install basket, wine, firefox 3 RC1, or any other application for that matter. Am I just missing something?

My second question has to do with .exe files, am I right to assume that they just plain do not work with Ubuntu?

Thanks much,
sc

---

### Post by joshedmonds on 2008-05-20
In your top menu bar, select Applications -> Add/Remove. You will be prompted to enter your password and then be able to add programs at will. If you want more advanced options, use the Synaptic Package Manager under System -> Administration.

You will find that some proprietary codecs aren't included by default, but if your internet connection works you will be prompted to download the appropriate files when you try and play something.

Apps like the FF3RC1 probably aren't in the repositories for download, but you can install them through the command line.

As for the .exe files, once you install Wine, SOME .exe files will work, but some won't -  a better bet is to try and find a FOSS (free and open source) replacement, usually they're as good as proprietary systems if not better, and if not, make it so!

If you have a real need for software that won't work in Wine, you might want to try an emulator like VMWare - but you should probably spend a couple of weeks tweaking your new system and learning the ropes first.

---

### Post by stefangr1 on 2008-05-20
Installing things in Ubuntu is nothing like it is in windows.

There are basically two ways in Ubuntu:
(1) the easy way: by the synaptic or adept package managers. When you start them trough the applications panel in the main menu, you can browse trough lots of programs that can be downloaded and installed trough the repositories.
(2) the hard way: from the command line trough sudo apt-get programname. But I guess that's for later.

Good luck!

---

### Post by sc4s2cg on 2008-05-20
Hi, 

I went where you directed, is there a button or something inside the Add/Remove program that allows me to browse for the program I downloaded?

---

### Post by joshedmonds on 2008-05-20
Depends on the program you installed. If it has a graphical user interface, generally it will appear in the menus under Applications. If not you need to take note of the name in Synaptic (when the application is selected, go to the installed files tab and look at the path for the app) then press Alt+F2 and enter the name in the dialogue box.

---

### Post by sc4s2cg on 2008-05-20
> **joshedmonds said:**
> Depends on the program you installed. If it has a graphical user interface, generally it will appear in the menus under Applications. If not you need to take note of the name in Synaptic (when the application is selected, go to the installed files tab and look at the path for the app) then press Alt+F2 and enter the name in the dialogue box.

Well, I tried to do what you suggested, but couldn't find the installation tab anywhere. So just did alt-F2 and then dragged the installation file into it, using this method somehow I managed to run Firefox 3 RC1. 

But it seems like all I did was run it. Is there a way to install over the default FF3 b5?

Or, could anyone teach me how to install Basket (OneNote equivalent) into Ubuntu. That way I can learn to fish and feed myself for a while, so to speak.

Edit: I think I might have solved the problem, through the link below I was able to install basket and wine, will fool around with it some more after breakfast and my morning run.
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by jesse100 on 2008-05-20
I am a newbie and I am making very slow progress with this. I put a .deb file on my desktop and I simply can't get it to install. I have the Freespire version and I can't find synaptic or anything else like that except karchiver. The karchiver will not do it (can't find configure script). I can't install anything! Very frustrating.

Jesse

---

### Post by unutbu on 2008-05-20
Hi jesse100, I think if you double click on the .deb file it should automatically install. At least, that's how it works with plain Ubuntu.

If that does not work, you could open a terminal and type:

```
sudo dpkg -i /path/to/*.deb
```

Of course, replace /path/to/*.deb with the path to your .deb file.

---

