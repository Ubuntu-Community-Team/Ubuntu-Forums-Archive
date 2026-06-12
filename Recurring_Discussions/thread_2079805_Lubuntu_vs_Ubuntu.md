---
title: "Lubuntu vs Ubuntu"
date: 2012-11-02
forum: Recurring Discussions
---

### Post by james1986 on 2012-11-02
Hi

I have been using ubuntu for the past 12 months and I have recently started to use lubuntu on my 10 year old desktop PC.  It is useable once again!

This got me thinking, why would you reserve Lubutu for old hardware?  Does anyone else run lubuntu on modern hardware and why?

Thanks

James

---

### Post by snowpine on 2012-11-02
Lubuntu is simply Ubuntu with LXDE desktop environment. Lots of people run LXDE on modern hardware. (Although I've personally never cared for it; I prefer Openbox, which is the older project from which LXDE is descended.) "Lightweight" desktop environments are not just for old computers; they are also for any user that prefers a simpler workflow without all the bells & whistles. :)

---

### Post by nothingspecial on 2012-11-02
Not support, moved to the cafe.

I use Lubuntu on modern hardware because I like it, simple as that.

---

### Post by james1986 on 2012-11-02
> **snowpine said:**
> Lubuntu is simply Ubuntu with LXDE desktop environment. Lots of people run LXDE on modern hardware. (Although I've personally never cared for it; I prefer Openbox, which is the older project from which LXDE is descended.) "Lightweight" desktop environments are not just for old computers; they are also for any user that prefers a simpler workflow without all the bells & whistles. :)

Thanks for your answer.  I'm thinking of using it as my main OS as I like an operating system to boot and then get out of the way.  My PC feels so snappy with lubuntu too which is nice.

Ill have to try openbox though :)

---

### Post by Elfy on 2012-11-02
*Thread moved to **Recurring Discussions**.*
Another this vs that thread ... 

I moved to xubuntu from ubuntu personally for much the same thing

---

### Post by nothingspecial on 2012-11-02
> **james1986 said:**
> 

Ill have to try openbox though :)

You are already using it. LXDE is openbox with some extra stuff plus some applications included.

---

### Post by snowpine on 2012-11-02
+1, and also you don't need to reinstall Lubuntu to get LXDE or openbox, they can be added to any Ubuntu/Xubuntu/Kubuntu install, and you can even switch between desktop environments based on your mood that day!

---

### Post by TenPlus1 on 2012-11-02
Oh yes, Lubuntu 12.10 is installed on my main desktop for simplicity and speed...

---

### Post by matt_symes on 2012-11-02
I boot into LXDE desktop environment when i want to run virtual machines (and that is quite a bit recently) otherwise i boot into Unity.
 
They are both excellent and both fit different work flows that i have.

---

### Post by zer010 on 2012-11-02
I use Lubuntu mostly because of my machine's specs (see sig), but I've also tried other DEs and LXDE just feels right.  I tried Unity for about a week and I just couldn't get used to the flow or the lenses. It seemed that menus were sparsely populated with the programs I was looking for and overpopulated with those that had nothing to do with what I wanted....  LXDE seemed to fall in line with the GNOME standard of one menu broken into categories which I've always liked.  It's simply intuitive and fast and that's what a computer experience should be.  I'd like to thank Canonical again for making Lubuntu an official flavor and hope that it only gets better. ^_^d

---

### Post by vasa1 on 2012-11-03
While on 12.04, I had Ubuntu onto which I added Xfce 4.10 and the Lubuntu desktop.
IMO, even when logging into a Lubuntu session, there is stuff running that you won't see if you have a pure Lubuntu installation.
That's why I'm now giving pure Lubuntu a six-month try on the same laptop: Dell 1545 laptop with 4GB RAM and Intel Core2 Duo.
No complaints.

---

### Post by pajoohesh on 2012-12-26
I have an Intel atom processor and it was running with Ubuntu. Not so nice experience. SLOW!

I just tried Lubuntu on one day and it was such a nice experience. The speed is much much more. no delay when opening folders in nautilus anymore. Ram is always empty. DAMN FAST.

I hope they keep this as an official release.

---

### Post by kansasnoob on 2013-01-01
With so many changes coming in Gnome I've been giving Lubuntu a much closer look:

[http://ubuntuforums.org/showthread.php?t=2099506](http://ubuntuforums.org/showthread.php?t=2099506)

I'm now playing with LXMenuEditor:

[http://lxmed.sourceforge.net/index.html](http://lxmed.sourceforge.net/index.html)

Part of my reasoning behind this is not just due to the UI but the fact that even more and more apps are becoming far too heavy, I believe due to OpenGL, and IMHO a desktop environment/window manager should use as few resources as possible :)

It's all good clean fun :guitar:

---

### Post by vasa1 on 2013-01-01
> **kansasnoob said:**
> ...
I'm now playing with LXMenuEditor ...
What exactly are you doing with it? Although I've seen quite a few mentions of it, I stayed away from installing it.

---

### Post by Linuxisfast on 2013-01-01
Lubuntu however good it maybe is not for newbies, drivers don't automount, many of the conveniences that we get used to in Ubuntu just don't work, one needs to configure all that separately and its not a job for newbies. Even on my small 2GB netbook with AMD Brazos, Ubuntu works and works good.

---

### Post by kansasnoob on 2013-01-02
> **vasa1 said:**
> What exactly are you doing with it? Although I've seen quite a few mentions of it, I stayed away from installing it.

So far I'm just wrecking things with it :biggrin:

I've blown up my .config a few times and had to start over, but I ultimately hope to rearrange the menu in a somewhat more gnome-2-ish manner, and hide a few things w/o actually removing them.

I posted some about my own needs and desires here:

[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)

---

### Post by vasa1 on 2013-01-02
> **kansasnoob said:**
> ..., but I ultimately hope to rearrange the menu in a somewhat more gnome-2-ish manner, and hide a few things w/o actually removing them.
...
One reason I don't use it is that I understand it needs Java and I don't need Java for anything else. If I did, I guess I may have given it a look.

Also, since fiddling with menus isn't that frequent, I'd rather edit the relevant text files to get what I want.

As far as hiding things goes, one can just comment out things since the actual menu format is xml (in /etc/xdg/menus/lxde-applications.menu and /etc/xdg/lubuntu/menus/lxde-applications.menu). And the .desktop files in /usr/share/applications can be edited with NoDisplay=True to make their corresponding entries vanish.

---

### Post by kansasnoob on 2013-01-02
> **vasa1 said:**
> One reason I don't use it is that I understand it needs Java and I don't need Java for anything else. If I did, I guess I may have given it a look.

Also, since fiddling with menus isn't that frequent, I'd rather edit the relevant text files to get what I want.

As far as hiding things goes, one can just comment out things since the actual menu format is xml (in /etc/xdg/menus/lxde-applications.menu and /etc/xdg/lubuntu/menus/lxde-applications.menu). And the .desktop files in /usr/share/applications can be edited with NoDisplay=True to make their corresponding entries vanish.

Great info, many thanks :guitar:

I also prefer a rather minimalist approach as far as installing packages and/or PPA's ....... basically *less is more* ;)

---

### Post by kansasnoob on 2013-01-02
@ vasa1,

On a somewhat more specific note, one of the things I'd like to accomplish is moving PCManFM from "accessories" to the main menu and have it display a "tree view", but I realize that may be a steep mountain to climb.

To me it's all good clean fun. I run a multi-boot so I can test and blow things up with no worries, and if I get burned out I can just boot into a stable installation and go back to playing when I'm in the mood ;)

I'm an old retired guy and this beats the heck out of building jigsaw puzzles :lolflag:

---

### Post by vasa1 on 2013-01-02
> **kansasnoob said:**
> ... On a somewhat more specific note, one of the things I'd like to accomplish is moving PCManFM from "accessories" to the main menu and have it display a "tree view", but I realize that may be a steep mountain to climb.
...
There are two parts there. I too would like to get what I access most often directly into the main menu but from the little I tried, I get the feeling that the main menu is "reserved" for headings that point to whatever else. In other words, it should be possible to have something called, say, "FM" that would have a right arrow pointing to PCManFM. I'm not sure that we can PCManFM there directly. But, to counter that there's "Run" just above "Logout" so it maybe doable.

I really haven't looked deeply into this because I mostly rely on ~/.config/openbox/lubuntu-rc.xml to set up keyboard short cuts to the programs I use frequently. (Lubuntu-rc.xml also is the place to go to to simulate a poor man's aero snap.)

Re. the "tree view", even if it's possible, I think it would be **static** since it would reflect the corresponding entries in the menu files. In other words, if you do create a new folder, or delete a folder, it wouldn't automatically reflect in the tree view if I understand what you want correctly.

BTW, you may want to look at Sean Davis' Menu Libre (for 12.04 and 12.10).

---

