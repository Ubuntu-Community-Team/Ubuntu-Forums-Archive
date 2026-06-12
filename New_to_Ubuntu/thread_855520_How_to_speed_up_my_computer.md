---
title: "How to speed up my computer?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Narcoleptic_Insomniac on 2008-07-10
Hi All, I recently installed 8.04 and my computer is a tad choppy (but a lot faster than Feisty was) and I was just wondering if there's anything I can do to speed up this computer without buying new hardware. It's an old computer, I got a good deal, 180 dollars. It's processor is an Intel Celeron, not sure which model. I'm currently deleting lots of files. Any other techniques?

---

### Post by Dark_Stang on 2008-07-10
On that old of a machine make sure you have desktop effects turned off and your colors set to 16 bit...

To turn off Compiz/Desktop Effects. Go System > Preferences > Appearance Preferences. Click the visual effects tab, and make sure it's set to none. If you're on an older computer you don't want to bog it down any.

To set your colors on your desktop to 16 bit instead of 24 bit. In a terminal run "sudo gedit /etc/X11/xorg.conf". This will open a text editor. Now just find each instance of "DefaultDepth    24" and set it to "DefaultDepth    16" and safe the file. Then restart the computer.

---

### Post by snowpine on 2008-07-10
> **Narcoleptic_Insomniac said:**
> Hi All, I recently installed 8.04 and my computer is a tad choppy (but a lot faster than Feisty was) and I was just wondering if there's anything I can do to speed up this computer without buying new hardware. It's an old computer, I got a good deal, 180 dollars. It's processor is an Intel Celeron, not sure which model. I'm currently deleting lots of files. Any other techniques?

Hi N_I, the #1 thing you can do to speed things up is install more RAM (how much do you have now?). 

Another suggestion is to go into the System menu, choose Sessions, and uncheck any that you don't need (I've noticed that unchecking the Tracker search tool makes an improvement, and I don't need Bluetooth, so I disabled that as well). 

Next suggestion is to try some lighter weight applications (epiphany instead of firefox, abiword instead of openoffice writer, etc.)

Finally, you might want to consider a different windows manager. Xcfe (used in Xubuntu) and Fluxbox are just two of the more popular alternatives to Gnome. You can experiment with windows managers by installing them and then choosing them from the Sessions menu at login; there is no need to uninstall anything or re-install from scratch. Let me know if you need a how-to.

---

### Post by VoodooLoveDog on 2008-07-10
If you can live w/o the eye candy, I would ditch reg favor Ubuntu for a distro that has a lighter windows manager. Such as Xubuntu.

sudo apt-get install xubuntu-desktop

I belive the command to remove the gnome desktop is:

sudo apt-get remove ubuntu-desktop

---

### Post by tjwoosta on 2008-07-10
i suggest xubuntu, or fluxbuntu, or some smaller distro 

(but keep in mind that the lighter and faster a distro gets, the less user friendly it will be)

---

### Post by Xerp on 2008-07-10
> **Narcoleptic_Insomniac said:**
> Hi All, I recently installed 8.04 and my computer is a tad choppy (but a lot faster than Feisty was) and I was just wondering if there's anything I can do to speed up this computer without buying new hardware. It's an old computer, I got a good deal, 180 dollars. It's processor is an Intel Celeron, not sure which model. I'm currently deleting lots of files. Any other techniques?

Well, deleting files isn't going to help speed things up, so you can safely keep your mp3 collection!

Compiz needs a fair amount of computing power, so turning off the desktop effects will give your ageing hardware a bit of a rest.

If you don't have much RAM then running as few things as possible simultaneously will also help. Finished browsing with Firefox? Then close it rather than minimise.

---

### Post by Dark_Stang on 2008-07-10
> **tjwoosta said:**
> i suggest xubuntu, or fluxbuntu, or some smaller distro 

(but keep in mind that the lighter and faster a distro gets, the less user friendly it will be)
User friendliness is different for every person and cannot be compared in this manner. Some people love KDE, I can't stand it. Some people love fluxbox, and others can't stand it. Some people like vi or emacs, and would shoot themselves if they had to use a text editor with a GUI instead.

---

### Post by Narcoleptic_Insomniac on 2008-07-10
My computer has no sound card so I just outright turned off all sounds all together, and installing ram would require more hardware, or me opening up my computer which I really don't want to do. Basically, I don't want to spend money lol.

Does Xubuntu run all the same programs as ubuntu, like Pidgin, firefox? etc. FireFox and Pidgin are a must-have for me.

Another thing I noticed is that in the past I tried using Kubuntu (not a fan myself), I installed it through the terminal, and deleted gnome, which slowed my computer down terribly, so  I tried putting gnome back on, and deleting KDE, and it got even slower, so would it be better to so a full re-installation of Xubuntu?

---

### Post by tjwoosta on 2008-07-10
> User friendliness is different for every person and cannot be compared in this manner. Some people love KDE, I can't stand it. Some people love fluxbox, and others can't stand it. Some people like vi or emacs, and would shoot themselves if they had to use a text editor with a GUI instead.


i definatly agree

i love fluxbox! (its definatly faster and easier to get stuff done when using command lines rather then GUI, but there is definatly a learning curve)

i just think for someone who is new to linux and never dealt with window managers  or command lines that fluxbox or xfce wont be as easy as gnome or kde

> Does Xubuntu run all the same programs as ubuntu, like Pidgin, firefox? etc. FireFox and Pidgin are a must-have for me.

yep, you should be all set with all that stuff  (xubuntu still uses the same package manager and everything)

---

### Post by Narcoleptic_Insomniac on 2008-07-10
> **tjwoosta said:**
> i definatly agree

i love fluxbox! (its definatly faster and easier to get stuff done when using command lines rather then GUI, but there is definatly a learning curve)

i just think for someone who is new to linux and never dealt with window managers  or command lines that fluxbox or xfce wont be as easy as gnome or kde



yep, you should be all set with all that stuff  (xubuntu still uses the same package manager and everything)

Eep, I seen you mentioned command lines. I'm kinda new, theres a few command lines I know, like sudo apt-get install, and sudo apt-get remove, update, I don't know what dpkg --configure -a does but I've used that a few times lol. Is Xubuntu command line only?

---

### Post by LowSky on 2008-07-10
If you only use it for simple tings like Firefox, Pidgin, and maybe Office. Why not use a lighter weight distro. It will run quicker and alllow you to get more work done. An OS like Puppy Linux has all that support without all the extra fluff that you may not ever use.
[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by Dark_Stang on 2008-07-10
No, Xubuntu isn't command line only. It just uses XFCE instead of gnome. The best way I can describe XFCE is... it's like a highly stripped down version of gnome.

---

### Post by kk0sse54 on 2008-07-10
Xubuntu is definitely not just command line. All it is is Ubuntu using xfce so you don't have to go and download the iso just go into gnome-terminal and type ```
sudo apt-get install xfce4
```

---

### Post by snowpine on 2008-07-10
> **Narcoleptic_Insomniac said:**
> Eep, I seen you mentioned command lines. I'm kinda new, theres a few command lines I know, like sudo apt-get install, and sudo apt-get remove, update, I don't know what dpkg --configure -a does but I've used that a few times lol. Is Xubuntu command line only?

No, Xubuntu is very similar to Ubuntu, with drop down menus, desktop icons, panels, etc. It is not scary. :)

You can see screen shots and such at [www.xubuntu.com](www.xubuntu.com).

You will learn to love the command line, I promise. It is really useful when you are trying to help people over the internet. Saying "Type 'sudo apt-get install firefox'" is easier than saying "Go to your applications menu, now choose Add/Remove, now click the Internet category, then scroll down until you see Firefox, check the little box next to it, now click the Apply Changes button..." :)

---

### Post by kk0sse54 on 2008-07-10
Another really good light simple wm that I have enjoyed using is openbox which is just like Fluxbox except a bit less advanced

---

### Post by Narcoleptic_Insomniac on 2008-07-10
> **snowpine said:**
> No, Xubuntu is very similar to Ubuntu, with drop down menus, desktop icons, panels, etc. It is not scary. :)

You can see screen shots and such at [www.xubuntu.com](www.xubuntu.com).

You will learn to love the command line, I promise. It is really useful when you are trying to help people over the internet. Saying "Type 'sudo apt-get install firefox'" is easier than saying "Go to your applications menu, now choose Add/Remove, now click the Internet category, then scroll down until you see Firefox, check the little box next to it, now click the Apply Changes button..." :)

Oh I love the ideas of command lines, they are a lot fast when you have to go digging through your computer to find program files and what not. I just don't know how to learn them, all I've been doing is asking people on these forums what command line I need to use to do this and that. Anyway, with that said, I'm going to play with Xfce, I just installed Xubuntu, see what I can do with it. I'll check back on the forums later for more help probably, thanks a lot fellas, my comp is running SO MUCH FASTER.

---

### Post by kansasnoob on 2008-07-10
So what do you have?

Here's mine:

[ATTACH]77187[/ATTACH]

Just go to System > Administration > System Monitor

---

### Post by sayakb on 2008-07-10
Click on other tabs....

Also see this: [http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php](http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php)

---

