---
title: "What to install in Ubuntu?"
date: 2014-09-17
forum: New to Ubuntu
---

### Post by nineteen-73 on 2014-09-17
Hello all!

I just recently installed Ubuntu on my HP Pavillion G7 2325DX. Actually, it's my third install in a week as I'm tweaking far too much too soon.

Initially, I had a hell of time getting Ubuntu to install because of UEFI and Windows 8. Prior to installing Ubuntu, I disabled Secure Boot and EUFI and installed Windows 7 successfully. But somewhere between here and there, I must've *broke* something because I had to use Boot Repair and Gparted to get Ubuntu to properly install, which by the way, without Ubuntu Forums help, I may have ended up going back to Windows! 

Today, I reinstalled Ubuntu and have just started reading the following sites for what to do next:

[http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr#ppas](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr#ppas)

[http://m.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html?m=1](http://m.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html?m=1)

I don't think I'll install Gnome 3 because I like Ubuntu's environment. I'm also skeptical to go and install this, that, and the other. So, any advice as to what to install and stay away from?

I've currently done the intial update and installed VLC, Gimp, Getdeb, and Playdeb.

I also plan on installing Steam and Wine. (To play Star Wars Galaxies via SWGEmu and Tarkin.org =) )

---

### Post by Sword90 on 2014-09-17
Libreoffice (not sure if it is preinstalled in Ubuntu since I use Lubuntu)
Blender, krita, inkscape, mtpaint, pencil (if you work creative)
scribus (if you write and edit articles etc.)
xchat (if you use irc's which I highly recommend especially as a beginner)
kate/kwrite (if you code)

That's my personal must have list.

Be careful with additional repositories. Do not add any if it is not neccessarily needed. In the most cases the stable versions from the software-center are perfect for you. VLC for example works no matter what. A daily build is actually more likely to be unstable than the stable software-center versions.

Have fun on your long UNIX journey :-)

---

### Post by nineteen-73 on 2014-09-17
Thanks for the reply! I having a good time researching these apps and OS.

---

### Post by sammiev on 2014-09-17
I do recommend ( Synaptic Package Manager )

---

### Post by deadflowr on 2014-09-18
I would install unity-tweak-tool for starters.
Allow you to change some basic settings, like themes and icons and the like.
Ubuntu's built-in theme changer in Appearance is quite limited and I don't recall an icon changer available at all in it.
You won't be able to move the launcher on the left, nor the panel on top, but at least you'll be able to make it somewhat more thematically pleasing for yourself.

Also +1 for synaptic.

---

### Post by fantab on 2014-09-18
> I don't think I'll install Gnome 3 because I like Ubuntu's environment.  I'm also skeptical to go and install this, that, and the other. So, any  advice as to what to install and stay away from?

As long as you install applications from Ubuntu repositories you are good.
To install third-party or proprietory software enable 'Partner' repositories. For instance, Skype.
Ubuntu does not offer these software via official repositories because of licensing issues.

Another must have is 'ubuntu-restricted-extras'... this package offers support for MP3 and other proprietory file formats... it also installs microsoft fonts... It is a good idea to have ms-fonts.

+1 for 'synaptic' and unity-tweak-tool...

---

### Post by mastablasta on 2014-09-18
add a playdeb repository and install some nice opensource games from there.

---

### Post by nineteen-73 on 2014-09-18
Today, I'll install Synaptic Package Manager.  I visited a website describing some features, but could someone explain what it does in more detail please? 

Also, I ran Software and Updates and looked to see what additional drivers were listed. The only item listed was for my AMD APU. I left the default options where they were. I visited AMD to see if there were current drivers to install, but did no upgrades, since my exact APU wasn't listed. I didn't install Autodetect because it was for a Windows OS. At this point, I don't intend on upgrading ANY drivers since everything seems to be working well. Any advice on this?

---

### Post by fantab on 2014-09-18
Well 'synaptic' is a package manager like Ubuntu software center... but with more features.

---

### Post by grahammechanical on 2014-09-18
> [COLOR=#000000] it's my third install in a week as I'm tweaking far too much too soon.[/COLOR]

Have you learned the lesson from that experience? Then do not install stuff that you do not need. Ubuntu comes with a default set of utilities and applications. Use those and become familiar with Ubuntu. Only install applications if you need them.

Browse the forums and notice what other people do that breaks the OS and do not do the same thing. Each of us have our own preferences. And some of us will say, "do this" and "do that." But is it what you want to do?

And remember, sometimes (in fact it is often) the easiest way to fix what we have broken is to re-install. If we are not prepared for doing that then keep Ubuntu as you find it when it is freshly installed.

Regards.

---

### Post by nineteen-73 on 2014-09-18
> **grahammechanical said:**
> Have you learned the lesson from that experience? Then do not install stuff that you do not need. Ubuntu comes with a default set of utilities and applications. Use those and become familiar with Ubuntu. Only install applications if you need them.

Browse the forums and notice what other people do that breaks the OS and do not do the same thing. Each of us have our own preferences. And some of us will say, "do this" and "do that." But is it what you want to do?

And remember, sometimes (in fact it is often) the easiest way to fix what we have broken is to re-install. If we are not prepared for doing that then keep Ubuntu as you find it when it is freshly installed.

Regards.

I agree and intend on reading posts with the forums. 

In the case of reinstalling Ubuntu if need be is something that will happen from time to time. It takes breaking  something, analyzing the problem, and fixing it to learn. I intend on breaking things.

Going back to the subject of Synaptic, other than having more features, does it provide a repository of applications and utilities that Software Center doesn't. What features does Synaptic provide that makes it stand apart from Ubuntu's preinstalled app?

---

### Post by Rob Sayer on 2014-09-18
Synaptic is recommended by scads of extremely knowledgeable linux geeks here.  I mean much more knowledgeable than a lot of those people who write those blogs you're using.

Just because someone writes a linux blog does *not* imply they know what the hell they're doing.  Some of them are good.  A lot of them are worse than useless because they give bad info and, at worst, can put malware on your system.

And noobs like you *cannot tell the difference*.

If there's one piece of advice I'd give a linux noob it's don't install from 3rd party untested and untrusted ppa's unless you actually know what the hell you're doing.

On synaptic, I always either use that or the terminal to install/remove apps.  It's been some time since I've used ubuntu software center.  That program stinks.

---

### Post by endlessinstant on 2014-09-18
Ubuntu Software Center is nice if you are new.  It has big, friendly graphics and is fairly straightforward to use.  However, it can be sluggish and glitchy.  Synaptic is more like the geek's alternative.  It is still fairly easy to use to find new software but it lists most software by package name without nonessentials like reviews and screenshots.   Sometimes it can be difficult to find something specific and it isn't always as useful for browsing or seeing what is popular.   OTOH I don't think I've ever had synaptic crash on me.   It is an important program if you would like to deepen your understanding of Linux and you will probably eventually migrate to it.   Before the Software Center existed it was the preinstalled package manager in Ubuntu so plenty of us long-timers have experience with it because of that.

---

### Post by Tadaen_Sylvermane on 2014-09-18
The beauty of any linux distro is the ability to customize virtually anything. Those guides are usually a waste of time as every single persons needs or desires are different. Install Ubuntu, use it. Find what you want to change or add then do that. Don't follow the opinion of someone else as gospel. "Best things to do" is extremely subjective. One persons best could be another's, or your worst nightmare.

One example of this is I could make a blog post about how I find the unity default theme ugly as sin. You may look at it and say you love it. Would you change it to fit my opinion?

---

### Post by nineteen-73 on 2014-09-18
I made the right decision getting involved with this forum. Thanks to everyones advice and direction. I look forward to developing my knowledge of Linux within this community.

---

### Post by olliemonster on 2014-09-21
Glad you like the fourm and ubuntu
Now to your question 
If you are creative i recomend Scribus openshot or kdenlive and (if you write music) denemo
If you like games i recomend supertux openarena or nexuiz also i really like supertuxkart 
If you think you fit in both catogries you could install them all with the command 
```
sudo apt-get install scribus openshot kdenlive denemo supertux nexuiz openarena
```

Since you're new only run commands if they are from a well rated online site eg lifehacker, the ubuntu docs or if alot of people recomnend it on this fourm and you think it sounds useful

---

