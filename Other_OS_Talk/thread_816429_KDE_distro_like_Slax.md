---
title: "KDE distro like Slax"
date: 2008-06-02
forum: Other OS Talk
---

### Post by L815 on 2008-06-02
I ran Slax visa usb recently and loved the way Kde 3.5 was setup compared to many others. The menu was responsive and very clean and trimmed down. Kde just felt good.

I tried kubuntu but didn't like it because it felt sluggish and had too many things everywhere :/

What other distros have a similar feel with Kde similar to Slax, or just a trimmed down version?

---

### Post by cardinals_fan on 2008-06-02
What's wrong with SLAX?  I'm running it installed on my desktop at this very moment...

---

### Post by R_T_H on 2008-06-02
Vector Linux, maybe? KDE (if you use the SOHO edition), very fast even on an old computer - the equivalent of Xubuntu even though it's not Xfce. Not my favourite though - I don't like KDE :(

---

### Post by L815 on 2008-06-02
> **cardinals_fan said:**
> What's wrong with SLAX?  I'm running it installed on my desktop at this very moment...


Atm I can't resize my Vista partition using its manager, and last time I did it with Gparted, it took 12+ hours. So Wubi is the only thing I will use for now, and in the process I want to try out some distros for when I resize my partitions (live cd/usb). 

I couldn't figure out how to configure my wireless. Every distro except PClinuxOS and Slax have been able to run out of the box wireless, but with Slax, it says it looks for a connection, but it's out of range?!? It was using the Kiwi manager (can't remember exact name)

That's not the only reason, I'm just hoppin to experience a couple of distros.

If I can configure my wireless in Slax, that would be awesome!

---

### Post by pelle.k on 2008-06-02
> The menu was responsive and very clean and trimmed down. Kde just felt good.
Guess what? That is what a *vanilla* kde is supposed to feel like. Slackware and derivatives are often "untouched" like that, and i guess the speed of slackware doesn't harm as well. :)
You could try the vanilla "kde" in arch linux to have much the same experience, unless you keep on slackin' that is!

PS. wlassistant is totally underrated IMHO. You'll have to compile it manually in slax though. But it's pretty much "./configure && make && make install"...

---

### Post by cardinals_fan on 2008-06-02
> **L815 said:**
> Atm I can't resize my Vista partition using its manager, and last time I did it with Gparted, it took 12+ hours. So Wubi is the only thing I will use for now, and in the process I want to try out some distros for when I resize my partitions (live cd/usb). 

I couldn't figure out how to configure my wireless. Every distro except PClinuxOS and Slax have been able to run out of the box wireless, but with Slax, it says it looks for a connection, but it's out of range?!? It was using the Kiwi manager (can't remember exact name)

That's not the only reason, I'm just hoppin to experience a couple of distros.

If I can configure my wireless in Slax, that would be awesome!
Try cfdisk for partition work, and follow these instructions from the SLAX forums:> I've uploaded it here :

[http://backtrack.serveftp.com/backtrack/misctools/slax6-install.kmdr](http://backtrack.serveftp.com/backtrack/misctools/slax6-install.kmdr)

Its a kmdr script, so download it to where you want, say /usr/share/slax/, then run it using the following :

```
/usr/bin/kmdr-executor /usr/share/slax/slax6-install.kmdr
```

Ignore the portion on the "live" version install, use the "real" version install.

As for the wifi, what wireless card do you have?

---

### Post by L815 on 2008-06-02
Thanks everyone for the suggestions, I will give them a try when I have some spare time. Finals are this week, I will wait till next week to start partition work.

 I also found myself many times wondering what *vanilla xxxx* meant, now I know :)

For my wireless card, on the sony website it says "Intel® Wireless WiFI Network Connection". Not sure the exact model of it as I've never had to find that information out. My Laptop model is a VGN-FZ240E if that's any help.


EDIT: Since we are on the topic of KDE, is it possible to install a vanilla kde 3.5 on ubuntu?

---

### Post by cardinals_fan on 2008-06-02
> **L815 said:**
> 
For my wireless card, on the sony website it says "Intel® Wireless WiFI Network Connection". Not sure the exact model of it as I've never had to find that information out. My Laptop model is a VGN-FZ240E if that's any help.
You have an Intel® PRO/Wireless 4965AGN Network Connection.  Try the following and let me know if it works: ```
#rmmod iwl4965
#modprobe iwl4965
#iwconfig
see which is your wireless, in my case I have wlan0 so I type
#ifconfig wlan0 up
#iwconfig wlan0 essid "your_essid" key "your_key"
#dhcpcd wlan0
```

---

### Post by mips on 2008-06-03
If you like KDE then try [Arch]("http://www.archlinux.org/") + [KDEmod]("http://kdemod.ath.cx/")

KDemod is very modular and you only install the parts/apps you want instead of the whole meta package.

---

### Post by pelle.k on 2008-06-03
> Since we are on the topic of KDE, is it possible to install a vanilla kde 3.5 on ubuntu?
Sure, just do a command line install, and apt-get "kde", "xserver-xorg" and you'll have a *fairly* vanilla kde. It's somewhat modified, but much faster than a regular "kubuntu-desktop".

---

