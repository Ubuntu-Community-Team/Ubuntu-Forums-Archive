---
title: "Behind the aesthetics, what is really the difference?"
date: 2010-06-02
forum: Recurring Discussions
---

### Post by roobinatube on 2010-06-02
Hey guys,

About a year ago I tried to use Fedora Core 4, and kept it for about a month, before getting a little fed up of my graphics driver and wireless card driver giving me problems (both were 3rd party pieces of software because there was no linux support for mine).

Anyway I have now got a new computer, with windows 7, which means i have a spare hard drive from my old computer, to play around with linux, and hopefully make the switch when I am confident to use it for work as well as spare time.

My question is... I know there are different user interfaces, and that makes a difference, and I know that there is a difference between rpm and deb based distros, but does it go any further than that? If I learn to use one distro, then decide I need another one for other things and change, will I be totally lost? Also my [much] younger brother wants to install linux on his computer, and I almost decided that Mint would be good for him because from using the liveCD I realise it is the easiest to use in the same way as windows. However, if I chose ubuntu... getting quite likely... would I be able to give him support if he got lost?

I appreciate any help

---

### Post by XubuRoxMySox on 2010-06-02
Mint *is* Ubuntu, basically, with some very cool tools and artwork added. The difference between them is about 10 minutes worth of downloading and installing software like Ubuntu-restricted-extras. Except that Synaptic Package manager is "crippled" in Linux Mint, to encourage users to use the MintInstall app instead. It's actually a pretty good safeguard for newbies.

> 
I know there are different user interfaces, and that makes a difference, and I know that there is a difference between rpm and deb based distros, but does it go any further than that?


Some of the interfaces are faster on older hardware (like [LXDE]("http://lxde.org"), which has very few extra features but is lightning fast - my big brother calls it "Windows98ish"). [Xfce]("http://xfce.org") (my favorite) is lightweight but still offers alot more features (panel applets and stuff) and has more of it's own integrated applications. I think of Xfce as kinda like "Gnome Lite." It runs superbly on my old hand-me-down Dell, and it's pretty! KDE has lots of wonderful eye candy and looks very Windowsy (more like Vista) and has some awesome integrated applications. It's too demanding on my poor old 'puter's resources though. Gnome - well, you already know Gnome I guess. Very cool, very simple, very functional and configurable.

The other difference is that the different desktop environments (Gnome, KDE, Xfce, LXDE, etc) have their own versions of certain applications. For example, LXDE's file manager is PCManFM, Xfce uses Thunar, Gnome uses Nautilis I think, and KDE uses Dolphin. They all do pretty much the same job, but they "fit" best with their native environment. But the good news is that you can freely mix 'n' match them! Alot of Gnome users love KDE's CD burner, for example. It works just as well in any environment, but when you mix and match you get *libraries* from the other desktop environment. That's no problem if you have plenty of disk space though. 

The different "flavors" of Ubuntu - Xubuntu, Kubuntu, and Lubuntu - are designed for easy use in the Xfce, KDE, and LXDE environments respectively. "Plain vanilla" Ubuntu uses the Gnome environment.

> 
If I learn to use one distro, then decide I need another one for other things and change, will I be totally lost?
 

RPM and deb distros are both pretty simple. In fact the RPM distros I've played with even use the Synaptic Package Manager, so you might not even notice any difference in installing and removing software. 

The real issue is **hardware compatibility**. This is crucial when distro-hopping! Some distros work great on my machine and others - despite being wonderful distros for lots of users - just don't work on my hardware. So it's important to check thei distro's web site for compatibility with your particular hardware. I really like PCLinuxOS, for example (awesome implementation of KDE!), but my hardware balks at it, while it hums along sweetly on Xubuntu. Check hardware compatibility before you "distro hop" and save yourself some headaches!

> 
Also my [much] younger brother wants to install linux on his computer, and I almost decided that Mint would be good for him because from using the liveCD I realise it is the easiest to use in the same way as windows. However, if I chose ubuntu... getting quite likely... would I be able to give him support if he got lost?


Most Mint users come here to the Ubuntu Forums for help when things get dicey beyond the simple quick fixes on Mint. It's a great distro! But like I said, it's "Ubuntu with green paint," preinstalled multimedia codecs (Ubuntu-restricted-extras), and some really nice and very useful tools added. But it's still Ubuntu, so I don't think you would have any trouble helping your brother. And these forums are the bestest, most awesomest community support in the history of ever! You (and he) can always come here and get wonderful support. Mint has some very cool forums of it's own, very friendly. But many Mint users rely mostly on Ubuntu's forums for support.

I hope I've helped. Enjoy Ubuntu!

-Robin

---

### Post by roobinatube on 2010-06-02
That is a great, fantastic answer.

Thank you very much indeed.

---

### Post by XubuRoxMySox on 2010-06-02
:) :D :) I'm so glad I can help! My Ubuntu/Xubuntu experience has been so trouble-free that I have very little experience in actually solving problems, lol. So it's a real pleasure when I can give an answer that is helpful!

Cheerfully,
Robin

---

### Post by Universal344 on 2010-06-02
Just a couple extra notes.  RPM and DEB based ditros use different package managers.  However you may only notice this if you have to go to the command line to install stuff.  Luckily they are all relatively similar and well documented.  And if you go with something other than regular Ubuntu (e.g. Kubuntu, Lubuntu), you may miss out on some cool features (Ubuntu One, Me Menu, Messaging Menu, Windicators, etc.).

---

### Post by Soul-Sing on 2010-06-02
Is Mint a "blessed" project from Canonical? I am just curious.

---

### Post by XubuRoxMySox on 2010-06-02
> **leoquant said:**
> Is Mint a "blessed" project from Canonical? I am just curious.

No. It is what they call a "fork" (like in a tree). Completely separate, but it uses the Ubuntu repositories. Lotsa other OSes are forked from Ubuntu and use Ubuntu's repositories (and therefore storage space and bandwidth), Ubuntu's installer, and even Ubuntu's forums.

It's perfectly legal. But it sure doesn't "feel" right. I get yelled at every time I say so, but it doesn't change the way I feel.

To be fair, Ubuntu is a fork of Debian. But Ubuntu has made changes to the kernel (the base of it's Linux core) which make it less compatible with Debian, and Ubuntu does not use all of Debian's repositories. It's not "copied" and re-branded in any way that is comparable to Mint's re-branding of Ubuntu. 

-Robin

---

### Post by LowSky on 2010-06-02
The one thing Mint has going for it is the much better eye candy. Even Grub looks nice.

I am moving more and more toward Arch Linux. Its a distro that really gets you to learn about the stuff that Ubuntu and full feature distro hide behind the GUI. So I'm learning more and more all the time. Many of the commands are the same but expect a few issues in where files are kept and the use of root between distros. It does seem Sudo is becoming a bit more popular which does make thing easier on users.

---

### Post by roobinatube on 2010-06-03
> **dixiedancer said:**
> 
The real issue is **hardware compatibility**. This is crucial when distro-hopping! Some distros work great on my machine and others - despite being wonderful distros for lots of users - just don't work on my hardware. So it's important to check thei distro's web site for compatibility with your particular hardware. I really like PCLinuxOS, for example (awesome implementation of KDE!), but my hardware balks at it, while it hums along sweetly on Xubuntu. Check hardware compatibility before you "distro hop" and save yourself some headaches!


Is the Live disk a reliable way to do this? If everything works fine on live disk, will it work the same after install? also what about the other way around, if some things do not work properly, will they not work properly after install?

For example, im looking around distros atm, and MoonOS, the graphics arent so great on the live disk, where as in Mint and ubuntu everything works fine. Does this mean that MoonOS would not work on my hardware?

---

### Post by philinux on 2010-06-03
Moved to Recurring Discussions.

---

### Post by XubuRoxMySox on 2010-06-03
> **roobinatube said:**
> Is the Live disk a reliable way to do this? If everything works fine on live disk, will it work the same after install?

*Usually*, but not always. I was told, "if it works using a LiveCD, it'll work installed." Not always true in my limited experience, but usually so. It's pro'lly better to write down your 'puter's information and see if it's listed on your distro's hardware compatibility page. I found mine listed by computer make and model number at OpenSUSE's page! I hope other big distros follow suit and make it that easy.

> ...Iim looking around distros atm, and MoonOS, the graphics arent so great on the live disk, where as in Mint and ubuntu everything works fine. Does this mean that MoonOS would not work on my hardware?

MoonOS is built on an earlier version of Ubuntu. Alot of the hardware compatibility is built into the kernel, and the later kernels have better hardware support (for the most part - there are exceptions sometimes where a kernel update will b0rk something that worked perfectly before).

Mint is sweet (the Xfce editions of Gloria and Helena are superb - PulseAudio free, effortless, full-featured, and fast)! Ubuntu is about 10 minutes of work to make just as sweet (except for the very wicked-kewl Mint Tools that are especially useful for newbies).

Hope that helps,
Robin

---

