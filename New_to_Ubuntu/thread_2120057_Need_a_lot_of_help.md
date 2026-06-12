---
title: "Need a lot of help"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by whs37 on 2013-02-25
I have installed Ubuntu. Took forever to do the updates. But now it works.
 
However, what a mess. This UNITY interface is no good for me. I cannot even find the Terminal. Is there some skin a la Zorin or Mint Mate with a proper toolbar where I can pin applications and folders and a proper start menu where one finds things. I would be grateful for advice.

---

### Post by Vaphell on 2013-02-25
> a proper start menu where one finds things
ubuntu icon/WIN key is your friend
btw, press and hold WIN key to see main shortcuts supported by unity

> I cannot even find the Terminal
ctrl+alt+t
WIN/ubuntu icon, 'terminal'

> a proper toolbar where I can pin applications and folders
you can pin stuff in the taskbar: run app, right click its icon in taskbar, pin.

either way, if you don't like unity you can install other desktop environments right from the official repo: kde, xfce, lxde, ... whatever floats your boat.

---

### Post by HermanAB on 2013-02-25
You can install xfce or kde, but gnome3 cocks up the system so that you will have problems with those.  It will be better to do a fresh install with Xubuntu. The default Ubuntu is strictly for masochists.

---

### Post by pierceTN on 2013-02-25
You can install the mate Desktop.  Look [HERE]("http://wiki.mate-desktop.org/download") for install directions. It is pretty simple, just a few terminal commands.


You can also install another desktop like: cinnamon, Gnome 3, KDE, XFCE, or LXDE.


Hope that helps.



-Pierce

---

### Post by Michael Dooley on 2013-02-25
> This UNITY interface is no good for me. I cannot even find the Terminal. Is there some skin a la Zorin or Mint Mate with a proper toolbar where I can pin applications and folders and a proper start menu where one finds things.

Please take a look at this page:

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

A useable desktop is not very far away (in time spent) from your present set-up.

---

### Post by whs37 on 2013-02-25
Thanks guys. This is all very helpful. I will now 'experiment' with the suggestions. Since I run in VMware, I do not run a big risk. I copy my VMware folder for backup before things can go south.

---

### Post by whs37 on 2013-02-25
Hi guys, Just a little update.
 
I found Terminal and was able to install my VMware Tools. This is essential for me so that I can move stuff into Ubuntu from my Windows 7 host.
 
I tried the Win+Ubuntu Start button. That brought up some random stuff which was pretty useless.
 
What I still did not find are 'Preferences' and 'Administration'. Where are they.
 
I have not yet embarqued into other skins. There seem to be some risks and I am also not skilled emought to really do it. I may try Xubuntu though.
 
Another question: How do I get this so called 'Taskbar' from the top to the bottom and how can I make it larger and pin things to it.
 
All this was very simple in Zorin with which I had no problems at all - see here: [http://www.sevenforums.com/chillout-room/276418-having-fun-zorin.html#post2275421](http://www.sevenforums.com/chillout-room/276418-having-fun-zorin.html#post2275421)
 
Also, FireFox is very slow (it is lightning fast in Zorin). I had already noticed that a couple of years ago when I made my first experiments with Ubuntu. Is there a reason? I am downloading Chromium now which is usually fast - we'll see.

---

### Post by sirriffsalot on 2013-02-25
I can help with a few things.. 

If you liked what Ubuntu had to offer before Unity, just get the older desktop environments, such as GNOME2. XFCE is another good choice for more lightweight resource-usage. If you're after real lightweight yet beautiful DE's I recommend giving Enligtenment (E17) a look. I am using it with Ubuntu Studio and produces more efficient results than XFCE! It's also very customizable.

If your applications are slow from the very start, give "preload" a try

```
 sudo apt-get install preload 
```

or get it from synaptic or the software center

```
 sudo synaptic 
```

```
 sudo software-center 
```

in case you can't get it up as with the terminal issue you had.

Preload basically lets your most frequent appplications start faster, hehe. Always helps with a good quick start on the things you want to do. Give Opera a try if Firefox is generally slow, as Opera I find is somewhat faster.. Konqueror is also another option which is in the repositories, ready to be installed if I recall correctly!

---

### Post by whs37 on 2013-02-25
Thanks for your Input. Not everything is slow - just FF. Chromium is a lot faster and behaves as you would expect. The preload is an idea, but it would probably lengthen the boot time.
 
I will toy around a bit more with Ubuntu but I don't think it is really worth persuing. This Unity is too odd and I like my systems to work 'out of the box'. Tweaking and twisting is not my style.
 
Too bad I had so much trouble with the VMware tools in Mint Mate. That looked like a nice system that I would like. Fortunately I still have my Zorin which runs well and does everything I want. Else I have 2xVista, 4xWindows 7 and 1xWindows 8 plus a tablet with Android. So there is no lack of systems.

---

### Post by Vaphell on 2013-02-25
> What I still did not find are 'Preferences' and 'Administration'. Where are they.

some customizations are available under the grid menu in top right corner (system settings).
In dash (that thing that appears after you press win) typing system settings should present you with the same options. Also in dash there are icons at the bottom. One of them is strictly for applications and you can filter by old fashioned categories like System, Accessories...
Dash is supposed to be smart and simply typing what you want should give it to you without clicking through bunch of menus.

> Another question: How do I get this so called 'Taskbar' from the top to the bottom and how can I make it larger and pin things to it.


I don't understand the 'how do i get' part, but the rest is: you run your program, right click on the icon that appears in the taskbar, select pin to taskbar, just like in win7. In 'Appearance' you have a slider that controls the icon size.



Do you run ubuntu in virtual machine? If so you are probably gimping yourself, as the latest iterations of Unity require compositing and if the hardware acceleration is not enabled in the system, the fallback mode is not some barebone version of the thing but the CPU heavy software mode. Ubuntu with Unity DE is likely to be dog slow when virtualized.

---

### Post by arpanaut on 2013-02-26
It is possible to install the "Mate" DE on Ubuntu, I don't know the details, but the information is out there.

---

### Post by mastablasta on 2013-02-26
> **arpanaut said:**
> It is possible to install the "Mate" DE on Ubuntu, I don't know the details, but the information is out there.
 
 
exactly. you can install any desktop you would like.
 
KDE looks kind of like widnows. uses qt libraries. for more see Kubuntu
razor qt is like light KDe (still under development)
XFCE looks and feels like old Gnome2 you talk about (see Xubuntu)
Mate is old gnome 2 as gnome 2 is not supported anymore in Ubuntu.
LXDE looks like win98 still under development. but already in a very good shape (see Lubuntu).
 
then there are others such as E17 (can be complicated to setup from scratch but then there is Ubuntu based Bodhi Linux that does plenty of seting up for you)
Openbox
IceWM (windows manager that looks kind of like win95 but is light and fast)
 
and some others.
 
point is there is plenty of choices mostly abailable in software center.
 
i use Xubuntu in virtual box becuase it is not as heavy, it is easilly modifiable (most is done by right click and then changing propperties) so i can easilly make it take even less reosurces by simple selecting less demanding theme and such easy steps.
 
further more to all this choice, you can get Gnome classic panel in Ubuntu 12.04 which looks more or less like old gnome2 (needs to be installed) and there is also unity 2D (in 12.04). both should speed things up a bit in a virtual maschine.

---

### Post by whs37 on 2013-02-26
Thanks Vaphell  and Mastablasta for the suggestions. I will try those out.
 
Yes I run Ubuntu under VMware like Mint and Zorin. The other distros are a lot faster. I think I will probably stay with Zorin. That is the nicest distro for me. Mint would be nice too, but I cannot get the VMware tools to work. They install properly and are as expected in the startups, but they just do not work - go figure. The tools do work in Ubuntu and Zorin though.
 
Since it was suggested already several times, I guess I have to have a look at Xubuntu.

---

### Post by mastablasta on 2013-02-27
If Zorin work very good and you like it, then by all means use Zorin.
 
why "torture" yourself? :-)

---

### Post by Paqman on 2013-02-27
> **Vaphell said:**
> Ubuntu with Unity DE is likely to be dog slow when virtualized.

The default 3D version probably would be. If you're running the LTS I'd suggest running it in 2D in a VM.

Log out, click the icon next to your user name and select "Unity 2D" then log back in. Much snappier than the 3D version on machines without mad graphics.

---

