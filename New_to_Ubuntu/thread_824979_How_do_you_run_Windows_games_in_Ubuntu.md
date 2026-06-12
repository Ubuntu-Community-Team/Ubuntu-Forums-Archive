---
title: "How do you run Windows games in Ubuntu?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by n64bomb on 2008-06-10
i've never fun ubuntu, but how do you run games in this os? i saw the tutorial and there is free word processor and excel spreadsheet with complete ms compatibility and internet access, but what do you have to do to be able to run current games? could i just insert the cd and install the game like in windows? im really confused about how to run something that isn't already built into the ubuntu core.

---

### Post by The Cosmic Hobo on 2008-06-10
There are a few options open to you.
You can't run Windows executable files in Ubuntu, so your games won't install or run. However, you can reinstall Windows to part of your hard disk or to a different drive (dual-boot); you can get a piece of software like Wine or Cedega that allows you to run Windows games through it; or you can install a "virtual machine", which runs an instance of Windows - I think they include VMware and virtualbox but I'm not sure.
Older (mostly DOS) games can be run through an emulator.

And of course, if you check out the gaming and leisure forum, you'll see all kinds of games native to Ubuntu. :)

That's the short version. I'm not so technical, so I can't explain all the ins and outs - but have a look around and see what takes your fancy.

---

### Post by dudude on 2008-06-10
To run Windows programs in Linux you must install Wine.

Not all applications will run in Wine, so just know that your results may vary.

The information to install wine can be found at [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

### Post by Het Irv on 2008-06-10
Well....
If you came to Linux hopeing you could run all of your Windows apps perfectly, prepare to be disipointed.  

There are some ways to run Windows programs, like WINE (Wine Is Not an Emulator), which is a comptatiblity layer for Windows programs, but it is far from perfect.

[www.wine-hq.com](www.wine-hq.com)

If you want to run games, your best bet is to duel-boot, that is run Windows and Ubuntu on the same computer, side-by-side.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by stchman on 2008-06-10
> **n64bomb said:**
> i've never fun ubuntu, but how do you run games in this os? i saw the tutorial and there is free word processor and excel spreadsheet with complete ms compatibility and internet access, but what do you have to do to be able to run current games? could i just insert the cd and install the game like in windows? im really confused about how to run something that isn't already built into the ubuntu core.

I can run older games like Half-Life UT, SoF, CoD.  I can even run Doom3 as it is openGL.  The newer games like Fear HL2, Splinter Cell Chaos Theory will not run.

The openGL games seem to run the best.  If you are a gamer just dual boot.

---

### Post by Sham885 on 2008-06-10
Most games I've tried won't work.  It's the main reason I reinstalled xp as a dual boot.  Although xp is currently not working from a virus...    If I get everything else working in ubuntu so I can use it as my main os I will probably reinstall xp *again* to get rid of the virus and spyware crap it keeps picking up and then run it with no internet just for playing windows games. Only way I can play viva pinata, zanzarah, age of empires, etc..  Haven't tried zeus or pharaoh but I highly doubt they'd play in ubuntu.  Especially since running my graphics card with anything but the generic driver gets me a blank white screen.

---

### Post by signseeker on 2008-06-10
Gaming on linux can be somewhat hit or miss. I use both wine and cedega - and am able to play some windows games. If you check out the lists on cedega you will see it is quite extensive and includes some relatively new titles. 

But, as was mentioned before - set up a dual boot system if you want all the features of the game to work properly. It's the quickest and least painful method.

---

### Post by blazercist on 2008-06-10
I can play HL2 games like Day of Defeat: Source TF2, CS:S HL2 all episodes....  they run almost perfectly. I can also play online poker with both pokerstars and full tilt and I can play starcraft and broodwar although the battle.net interface is a bit garbled.  The appDB on winehq.org has a list of games and their compatibility ratings....  most popular games like WoW work pretty well.  it depends alot on your hardware (mainly video card) and how old the game is... if it came out yesterday chances are it wont work perfectly right away, but after a month or two those brainiacs at wine figure it out.

---

### Post by TWO on 2008-06-10
It's just my opinion, and I don't mean to disrespect the hard work of those that make Wine/ Cedega or whatever, but the only viable option is to dual boot.

You, like me, like anyone else who wants to play games just wants to stick a disc in, install and play. Some people will tell you otherwise, but I just don't think it's worth all the hassle tweaking a program until the cows come home just to get one game to work. 

Take the easy option!;-)

TWO

---

### Post by AndrewTheArt on 2008-06-11
> **The Cosmic Hobo said:**
> You can't run Windows executable files in Ubuntu, so your games won't install or run. However... you can get a piece of software like Wine or Cedega that allows you to run Windows games through it

Stop confusing the noobies :)

Just to clear up the confusion, you can "run" many Windows executables in Ubuntu using [Wine]("http://www.winehq.org/"). You can search for app compatibility using the Wine [AppDB]("http://appdb.winehq.org/"). 

[quote=Wikipedia]Wine is a software application which aims to allow Unix-like computer operating systems on the x86 architecture to execute programs written for Microsoft Windows.[/quote]

Using Wine, many Windows games will install and run without problem. 

However, just plain ole' Wine often doesn't' cut it for many games, so there are a few tools people recommend that make the experience a lot nicer. Two things - Cedega (you have to pay for this, but it is well worth it for serious gamers), which is essentially a commercial implementation of Wine that makes the installation and running of a lot of a games much simpler, and PlayOnLinux (free), which is basically a repository of Wine install scripts and various optimizations that will make installing certain games in Ubuntu a lot simpler.

[http://www.cedega.com/](http://www.cedega.com/)
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

So try PlayOnLinux first (it's a GUI app, don't worry). If that doesn't work for you, try/pay for Cedega. So start [here]("http://www.playonlinux.com/en/download.html"), select "Ubuntu", and open a terminal up to run the commands listed there. PlayOnLinux will handle many games and make installing them very simple (it will handle inserting CD's, etc).

Your other options are basically to play native Linux games or dual boot. 

Good luck!!!

Andrew


PS - Just in case you wanted to get Wine, open a terminal and type - 

```
sudo apt-get install wine
```Now you can try to run a Windows app by simply clicking on it! Pretty cool, eh? Check that AppDB link above for compatibility - Wine is definitely not perfect, although it's very good.

---

### Post by LowSky on 2008-06-11
[I read somewhere that Valve is looking to build a linux version of Steam]("http://www.phoronix.com/scan.php?page=article&item=source_linux&num=1")


Which means easier installs and maybe some games that won't need Wine

---

