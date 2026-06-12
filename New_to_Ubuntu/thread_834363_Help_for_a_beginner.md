---
title: "Help for a beginner"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Ddub on 2008-06-19
So I finally got fed up with windows and made the switch to the greener pastures that is linux. Now i'm stuck with an os I only half understand and can't really use.

So here's what I want to be able to do:
   connect to the public wireless network in my city (which I was able 
   to do on windows)

   Use WINE, Win4Lin, or something to make windows games run

   Be able to listen to music (which I have read takes extra codecs)

My computer specs are:
   1.8gz pentium 4
   128mb geforce FX7something or other
   some off band sound card
   A realtek wireless adapter

Any help would be greatly appreciated.

---

### Post by Pjotr123 on 2008-06-19
Read up a bit on this site with how-to's and tips:
[http://ubuntutip.googlepages.com/home](http://ubuntutip.googlepages.com/home)

---

### Post by xdarkday on 2008-06-19
> **Ddub said:**
> So I finally got fed up with windows and made the switch to the greener pastures that is linux. Now i'm stuck with an os I only half understand and can't really use.

So here's what I want to be able to do:
   connect to the public wireless network in my city (which I was able 
   to do on windows)

   Use WINE, Win4Lin, or something to make windows games run

   Be able to listen to music (which I have read takes extra codecs)

My computer specs are:
   1.8gz pentium 4
   128mb geforce FX7something or other
   some off band sound card
   A realtek wireless adapter

Any help would be greatly appreciated.

The "codecs" problem should be answered with the first post's link.(fyi i have never had a problem with listening to music with stock ubuntu)
Wine will not work properly with all windows programs. Check out the wine site for more info, here is a link to some working programs [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Joshua Netterfield on 2008-06-19
> **Ddub said:**
> So I finally got fed up with windows and made the switch to the greener pastures that is linux. Now i'm stuck with an os I only half understand and can't really use.

So here's what I want to be able to do:
   connect to the public wireless network in my city (which I was able 
   to do on windows)
A realtek wireless adapter is not very specific. Wireless is actually one of Ubuntu's weakest points. Is it inside your computer or USB? Which model is it (if it is inside your computer and you are not sure which model it is, open a terminal [Applications>Accessories>Terminal] and run
```
lspci
```.
> 
   Use WINE, Win4Lin, or something to make windows games run

First of all, when you use WINE, please keep in mind that the project will never be complete. Microsoft didn't even get it perfect when they made Windows Vista. First of all make sure you have WINE (if you don't go to Applications>Add/Remove...), then you can just click on a Windows exe file. A lot of programs need modifications, so look for details for each program at appdb.winehq.org

I would personally recommend trying (and then maybe buying) Crossover Office (based on wine):

[http://www.codeweavers.com/](http://www.codeweavers.com/)

> 
   Be able to listen to music (which I have read takes extra codecs)
When you try to play music (click on a song), you should be asked if you want to install the right codecs. They are not included by default for legal reasons.

There are a bunch of things like this (for example Sun Java, Microsoft fonts, etc). To install all of these, open up a terminal (Applications>Accessories>Terminal) and run:
```

sudo apt-get install ubuntu-restricted-extras

```

Hope this helps.

---

### Post by billgoldberg on 2008-06-19
Install audio and video codecs, flash, ...

first in a terminal (applications -> accessories), copy/paste this:

```
sudo apt-get install ubuntu-restricted-extras
```

After it's ready copy/paste this:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

then

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then

```
sudo apt-get install libdvdcss2
```

Then

```
sudo apt-get install non-free-codecs
```

and if you want, you can install vlc

```
sudo apt-get install vlc
```

This all should take around 10 minutes to finish and you'll have all the codecs you'll ever need.

For wine

```
sudo apt-get install wine
```

Check here for specific game install instructions:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

note: far from all games work in wine. The ones that work the best: counterstrike source, half-life 2, WoW, call of duty 4, ...

You can also try getdeb.net to search for games, or the ubuntu repositories.

For wireless:

first check "system -> administration -> restricted hardware drivers".

Install everything in there.

If your wireless card isn't in there, try this:

[http://ankurs.com/2008/04/installing-ndiswrapper-on-ubuntu-804/](http://ankurs.com/2008/04/installing-ndiswrapper-on-ubuntu-804/)

Since you're new, here's a guide to customizing ubuntu:

[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

Hope this was of some help to you.

note: I gave lots of commands, if you want you can use the gui (system -> administration -> synaptic package manager) instead. But the commands are faster and you only need to copy/paste.

---

### Post by azurepancake on 2008-06-19
The three links in my signature can be quite helpful.

---

### Post by shifty_powers on 2008-06-19
ditto my links ;)

psychocats rocks :D

---

### Post by hyper_ch on 2008-06-19
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by avtolle on 2008-06-19
The wireless thing may be your biggest hurdle. What wireless card do you have?

---

### Post by metalf8801 on 2008-06-19
for playing games using Wine a free tool that can help is [Play On Linux]("http://www.playonlinux.com/en") 

to installing open a terminal 
Applications>Accessories>Terminal 

then copy and past 
```
sudo wget http://playonlinux.botux.net/playonlinux_hardy.list -O /etc/apt/sources.list.d/playonlinux.list
``` 
press enter then it will ask for you pass word 

```
 wget -q http://playonlinux.botux.net/pol.gpg -O- | sudo apt-key add - 
```

```
sudo apt-get update 
```

```
 sudo apt-get install playonlinux 
```

type y when you are asked "Do you want to continue"  
the wait for it to download and install 

you should then be able to find Play on Linux 
Applications>Games>PlayOnLinux (look for the Eyes) 

also look for games that are native to Linux 

look at this thread for information about games for Linux [http://ubuntuforums.org/showthread.php?t=743296](http://ubuntuforums.org/showthread.php?t=743296)

---

### Post by Ddub on 2008-06-19
Wow, I didn't think responses would be this quick kudos to you guys. My wireless adapter is a Realtek RTL8187 usb. It works on my XP and Ubuntu recognizes it and even picks up networks via roaming mode but can't connect to them using the exact same setup as the XP.

---

