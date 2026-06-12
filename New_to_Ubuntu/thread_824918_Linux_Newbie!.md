---
title: "Linux Newbie!"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Graahl on 2008-06-10
Hi! My name is Chris and I just changed from Windows Vista to Linux Ubunto!

Huzzah for me! Anyway I have a series of questions some will be stupid and some will be... the same as above. (I am new to Linux)

I am running Linux on a Acer Extensa 5420G laptop with:
AMD Turion 64 2 Mobile Tec TL-58, 1,9 GHz Duo core.

15.4" LCD Monitor

ATI Mobility Radeon HD 2400 XT HyperMemory (Up to 1279 mb)

4 GB DDR2 RAM

160 GB HDD

And I just got a few questions...

So yeah, I haven't really had any experiance with Linux and I haven't really had any problems yet, and I don't wanna have any either :D

So yeah I've just installed the OS and I managed to get my wireless network working, I am not to sure about my Graphic card but it says it's working..

Question one:

How can I check my computer specs?

Two:

I can't get flash working (Can't check youtube)

Three:

I've installed KDE because a friend of mine told me there was a "cube"? >.< But now I got **** loads of new applications under my application thingy up to the right screen. Do I need em?

Four:

Are there any good mp3 players for Linux? That functions alot like WinAMP a friend of mine said something on M... But I can't figure it o

Anyway I am just learning at the moment...

Please help me answering theese silly questions :D

---

### Post by wolfen69 on 2008-06-10
KDE is not needed to get the cube. you were fine as you were. to get flash, go to system>admin>software sources and make sure everything is checked. you can leave cd rom unchecked. close and reload. then open terminal and:```
sudo apt-get install flashplugin-nonfree
``` any other questions feel free to ask.

---

### Post by SunnyRabbiera on 2008-06-10
No questions are silly.

lets go down your list:
How can I check my computer specs?
go to system, then to administration then to system monitor.

Two:
I can't get flash working (Can't check youtube)

You need flashplugin-nonfree... but fair warning flash on a 64bit kernel is rather... sucky, its not our fault mind you, but many have experienced issues with this.

Three:

I've installed KDE because a friend of mine told me there was a "cube"? >.< But now I got **** loads of new applications under my application thingy up to the right screen. Do I need em?

KDE is just another user interface, it doesnt help with the cube...

Four:

Are there any good mp3 players for Linux? That functions alot like WinAMP a friend of mine said something on M.

Try audacity, its very winamp like.

---

### Post by wolfen69 on 2008-06-10
> **Graahl said:**
> 
Four:

Are there any good mp3 players for Linux? That functions alot like WinAMP a friend of mine said something on M... But I can't figure it o

Anyway I am just learning at the moment...

Please help me answering theese silly questions :D

yes, but you will need codec support. 

```
sudo apt-get install mplayer vlc 
``` will allow you to play almost anything.

---

### Post by halitech on 2008-06-10
if you want something very Winamp looking, try XMMS, its very winamp looking

---

### Post by jonwop on 2008-06-10
audio players: [http://lindesk.com/2008/03/top-10-linux-mp3-players/](http://lindesk.com/2008/03/top-10-linux-mp3-players/)

the "cube" that your friend might be talking about is probally a function in compiz which is a 3d desktop environment that you can use to "make it pretty" vista has one as well i think it's call aero or something.

if you go to youtube, using firefox (default) just below the address bar it should say "install missing plug-ins" click on it and go through the steps to install for linux 

here's a step by step link just in case: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

to find your specs go into your terminal and type:   $sudo lshw
you can get more specific using the -C flag:      $sudo lshw -C disk

and the "application thingy" might be your updates yes do what it asks that way your system is up to date 

hope this helps

cheers

---

### Post by eriqjaffe on 2008-06-10
> **halitech said:**
> if you want something very Winamp looking, try XMMS, its very winamp lookingExcept that xmms isn't in the Hardy repos.  ;)

Audacious (as has been mentioned above) is the continuation of xmms, and is **extremely** WinAmp-like.

---

### Post by avtolle on 2008-06-10
> **eriqjaffe said:**
> Except that xmms isn't in the Hardy repos.  ;)

Audacious (as has been mentioned above) is the continuation of xmms, and is **extremely** WinAmp-like.
Agreed.

---

### Post by starfunker on 2008-06-10
I have a 64bit system.  I downloaded ubuntu-restricted-extras and my flash just started to work.

Go to your synaptic package manager under 'administration' and search for ubuntu-restricted-extras.

---

### Post by wootah on 2008-06-10
> **Graahl said:**
> Hi! My name is Chris and I just changed from Windows Vista to Linux Ubunto!

Huzzah for me! Anyway I have a series of questions some will be stupid and some will be... the same as above. (I am new to Linux)

Yey congrats :D

> 
<snip>

And I just got a few questions...

So yeah, I haven't really had any experiance with Linux and I haven't really had any problems yet, and I don't wanna have any either :D

So yeah I've just installed the OS and I managed to get my wireless network working, I am not to sure about my Graphic card but it says it's working..

Question one:

How can I check my computer specs?

Open up a terminal and type the following:
```
sudo apt-get install hwinfo
```
Then run it:
```
hwinfo
```
This will spit out a TON of highly detailed information. If you want, you can redirect this information to a text file so you can read it later :)
```

hwinfo > ~/HardwareInfo.txt

```
or you can read it by using the **less** command so you can scroll around:
```
hwinfo | less
```

> 
Two:

I can't get flash working (Can't check youtube)

I think this was answered above?
> 

Three:

I've installed KDE because a friend of mine told me there was a "cube"? >.< But now I got **** loads of new applications under my application thingy up to the right screen. Do I need em?

You don't need KDE for the 'cube' effect. This is part of the compiz-fusion package that is provided with both distros (Kubuntu and Ubuntu), afaik. In Ubuntu, you would go under Preferences then Appearance and under one of the tabs is the extra effects.

I'm not 100% sure of how to do the same with KDE.
> 

Four:

Are there any good mp3 players for Linux? That functions alot like WinAMP a friend of mine said something on M... But I can't figure it out

Many, many good media players are available for Linux. Amarok is my favorite, but XMMS more closely resembles the older versions of Winamp. Mplayer, Totem and VLC are available for video playback as well, but you will need to enable the restricted repositories to get the proper codecs (it's not as bad as it sounds :))

> 
Anyway I am just learning at the moment...

Please help me answering theese silly questions :D

That's what the community is here for :)

---

### Post by newbuntuxx on 2008-06-10
also, if you install flash and get problems with firefox 3 beta when you play flash media, eg. firefox crashes, or no sound or things of that nature, dont waste alot of time searching for a solution. Just downgrade to firefox 2, and that will solve 90% of the problems. 

You may need to reinstall flash after you downgrade firefox.

---

### Post by Paqman on 2008-06-10
> **starfunker said:**
> I have a 64bit system.  I downloaded ubuntu-restricted-extras and my flash just started to work.

Go to your synaptic package manager under 'administration' and search for ubuntu-restricted-extras.

On KDE that would be kubuntu-restricted-extras instead.

+1 on the 64-bit Flash situation. No problems here either. Flash just isn't an issue on 64-bit any more.

As for media players, i'd recommend Amarok. It's probably the most widely-used Linux media player, and for a good reason.

---

### Post by Graahl on 2008-06-10
Everyone...

Wow! Thanks alot for the help I got it's been really helpful! Honestly
really great replies and nice responce.

I am looking forward to hanging out here with everyone and learning more about Linux!

Thanks once again.

---

### Post by avtolle on 2008-06-10
If, for whatever reason, you decide to dump KDE and use Gnome as the desktop, Exaile is another media player to suggest; quite nice, has a lot of the same features as Amarok, but with a Gnome, rather than KDE front-end. Either is really good, so, IMHO, you can't go wrong. I've three machines going; on one, I've quod libet; on one, I've Audacious; and Exaile is on the third. Just like to experiment. Used XMMS from 5.10 through 7.10, and really liked it, but it's not available through the repositories in 8.04, thus the experimentation.

---

