---
title: "HOWTO:  Install extra deskop environments"
date: 2009-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Dullstar on 2009-11-17
I see this question pop up all the time, so here's a tutorial.
Note that these packages should be possible to get through Synaptic or another package manager, but the terminal is used in this tutorial.  To search in a package manager, when it says

```
sudo apt-get install [insert package here]
```you would put everything after the word install into your package manager search box, in this case it would be [insert package here].

GNOME (recommended command)
```
sudo apt-get install ubuntu-desktop
```Alternate command to install GNOME
```
sudo apt-get install gnome
```KDE (recommended command)
If you want more customization options, I would recommend installing both KDE and Kubuntu Desktop (KDE alone appears to be missing a few things, although more customization exists)
If this isn't clear, please read the [_third post in this thread_](http://ubuntuforums.org/showthread.php?p=8491703#post8491703)
```
sudo apt-get install kubuntu-desktop
```Alternate command to install KDE
```
sudo apt-get install kde
```XFCE (recommended command)
```
sudo apt-get install xubuntu-desktop
```Alternate command to install XFCE
```
sudo apt-get install xfce
```LXDE
Currently, this is the command to use (read section for more details)
```
sudo apt-get install lxde
```[http://en.wikipedia.org/wiki/Lubuntu](http://en.wikipedia.org/wiki/Lubuntu) - The reason I have linked to this article is because "Lubuntu" will supposedly one day supposed to become an official deriative.  If anyone is interested to see if this will happen, attempt running
```
sudo apt-get install lubuntu-desktop
```My guess is it will be by 10.04.  If anyone is interested, you can try running the command just to see if anything is detected.  So far, though, the output is
```
E: Couldn't find package lubuntu-desktop
```We will probably have to wait for 10.04 for another oppurtunity for it to pop up, though.  Then again, I still use Jaunty, so this command might work in Karmic.  If it works for you, report back with what version you are using (you don't have to let me know what variant).

IceWM
```
sudo apt-get install icewm
```JWM
```
sudo apt-get install jwm
```**How to open the terminal**
GNOME
Applications -> Accessories -> Terminal

KDE
Note:  It doesn't make a difference were whether you are using the Kick-Off or the classic style menu.
System - Konsole Terminal
Note2:  If you find something that just says "Terminal" or just "Konsole" that will work too.

For other DE's, I need to be using them to tell you what to do.  Let me know if you can't find your terminal, and I will help you.

If you want some information about the desktop environments before installation, please refer to these Wikipeida articles.

[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)
[http://en.wikipedia.org/wiki/KDE](http://en.wikipedia.org/wiki/KDE)
[http://en.wikipedia.org/wiki/XFCE](http://en.wikipedia.org/wiki/XFCE)
[http://en.wikipedia.org/wiki/LXDE](http://en.wikipedia.org/wiki/LXDE)
[http://en.wikipedia.org/wiki/IceWM](http://en.wikipedia.org/wiki/IceWM)
[http://en.wikipedia.org/wiki/JWM](http://en.wikipedia.org/wiki/JWM)

If you feel clarification is needed, or if there's a DE you know of that I forgot, let me know.

Version 1.1

**Changelog**
1.0:  Original Tutorial

1.1:  Changed KDE information.  It is best to install both if you want a lot of customization options from my own experience..

---

### Post by adeypoop on 2009-11-25
> **Dullstar said:**
> 
```
sudo apt-get install lubuntu-desktop
```My guess is it will be by 10.04.  If anyone is interested, you can try running the command just to see if anything is detected.

I just tried that command and it found about 254MB of packages to download! looks like it must be official already :o

---

### Post by Dullstar on 2009-12-13
It appears that for the best KDE experience in Ubuntu, one should install both the Kubuntu Desktop and KDE packages over an existing Ubuntu installation, and not just go with Kubuntu.

```
sudo apt-get install kubuntu-desktop
```
then run
```
sudo apt-get install kde
```Order does not matter.

---

