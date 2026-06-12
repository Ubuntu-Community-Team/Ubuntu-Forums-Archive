---
title: "How do I install flash 8 on ubuntu"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Southsidepoker on 2008-08-10
Title says it all. I have ultimate bet (poker software) installed but after I login it says you need flash 8 to play. The text is a link but I click it and nothing happens. All I use my computer for is to play poker and that is the only site I play on. Please help me I am screaming at my computer I have tried everything please help before I break my laptop in half I have been trying to get this to work for over 4 hours.

---

### Post by Vivaldi Gloria on 2008-08-10
Start

system menu > admin > synaptic

Enable restricted and multiverse repositories from the repository settings to get a complete list. Then click refresh. 

Now you can search and install 

```
flashplugin-nonfree
```

---

### Post by SZ07 on 2008-08-10
Vivaldi Gloria's instructions will install flash 9 I think.

First, do you have flash currently installed? If not then follow Vivaldi Gloria's directions.

If you need Flash 8 specifically, its probably hard to find (I don't even know if it was released for linux).

That said, the site should work with flash 9 because I doubt a lot of people are still running 8.

Lastly, sometimes flash just doesn't work properly in Firefox. If you still can't fix your problem, you might want to install wine and then install Firefox 3 (windows version) and try to access your poker site. This method work for me with a few websites that just don't work with the linux flash player.

---

### Post by gjoellee on 2008-08-10
Why do you want to install flash8? You should actually use flash10 beta!

---

### Post by AusIV4 on 2008-08-10
Flash 8 was never released for Linux. Adobe skipped from Flash 7 to Flash 9 on the Linux version (and Flash 7 was fairly sketchy, IIRC).

Flash 9 should be backwards compatible with Flash 8, and it's in the repositories.

Install [flashplugin-nonfree]("apt:flashplugin-nonfree") with your favorite package manager.

---

### Post by bpowell2005 on 2008-08-10
> **Southsidepoker said:**
> Title says it all. I have ultimate bet (poker software) installed but after I login it says you need flash 8 to play. The text is a link but I click it and nothing happens. All I use my computer for is to play poker and that is the only site I play on. Please help me I am screaming at my computer I have tried everything please help before I break my laptop in half I have been trying to get this to work for over 4 hours.

Just to clarify; you're running Ultimate Bet in WINE, right? When you run UB, it's asking for Flash 8.

So, I think you need to install Flash in WINE...I'm not sure Wine applications can access or take advantage of your Ubuntu Flash installation, but I may be wrong here.

---

### Post by Vivaldi Gloria on 2008-08-10
> **bpowell2005 said:**
> Just to clarify; you're running Ultimate Bet in WINE, right? When you run UB, it's asking for Flash 8.

So, I think you need to install Flash in WINE...I'm not sure Wine applications can access or take advantage of your Ubuntu Flash installation, but I may be wrong here.

Oh, if that program is running in wine then my method is no good. I don't know how you install flash in wine.

---

### Post by suprfish on 2008-08-10
Does flashplugin-nonfree install to the Wine C:/ (etc) or just use Wine libraries (and live somewhere else)? In the OP's [original thread]("http://ubuntuforums.org/showthread.php?t=885197"), he installed flashplugin-nonfree but still UB complained that there was no Flash plugin installed.

Southside, you have wine-doors installed correct? **Install Flash Player 9 using it** (ss [here]("http://i37.tinypic.com/xp3cs6.png")).

---

### Post by Lhynnan on 2008-08-10
:) I know you've got loads of useful comments here and I just thought I'd throw mine in for good measure...

I don't know anything about Wine but if you are trying to just install flash as a plugin to firefox... I had awful trouble getting mine to work too... 

in the end I had to uninstall everything to do with flash, gnash thru synaptic and manually install flash9 from the adobe website - for some reason it wouldnt work when i tried to install thru synaptic or thru the firefox plug-in installer.

you may have to get to grips with the terminal (applications>accessories>terminal) in order to manually install the file you download from the adobe website (the adobe website does have a nice step-by-step guide to install the file they give you..

I think the only info they dont give you is how to navigate to the file you download to your desktop in terminal, the command you'll need for that is:

cd ~user/desktop/install_flash_player_9_linux


((WARNING)) I'm a no0b - all of my advice should be taken with about a tonne of salt...

Lhynn x

---

### Post by bpowell2005 on 2008-08-10
> **Lhynnan said:**
> 

((WARNING)) I'm a no0b - all of my advice should be taken with about a tonne of salt...

Lhynn x

That is what Ubuntu is all about; users helping users! 

Welcome to the forum.

---

### Post by SunnyRabbiera on 2008-08-10
I dont see why flash 9 cant work for flash 8 sites as its basically the same thing.
There was little differences between the two to my understanding coding wise.

---

