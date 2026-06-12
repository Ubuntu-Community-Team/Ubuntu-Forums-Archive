---
title: "Pro's amd Con's of LXDE DE on Ubuntu 12.10 and Lubuntu 12.10"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by musshan on 2013-01-29
Hello People,

                       I want to know your opinion about the pro's and con's of intalling LXDE on Ubuntu and Lubuntu. Which one do you recommend and why?:confused:

Unity was running very slow on my Laptop with 1GB RAM, it was very cumbersome and almost unworkable. So I decided to try various DE's. I installed LXDE, XFCE, MATE, GNOME Classic, E17. But now I notice there are lots of programs that have installed with these DE's, some f them are duplicates. I installed all through terminal apt-get from various how to's from google. Now that I have settled for LXDE I want to know how to remove these other DE's and the programs they brought.

Please share your opinions on these. Thank you folks.

---

### Post by vasa1 on 2013-01-29
If you like LXDE, just do a clean install of Lubuntu 12.10. If you like Xfce, just do a clean install of Xubuntu 12.10.

---

### Post by santosh83 on 2013-01-29
> **musshan said:**
> Hello People,

                       I want to know your opinion about the pro's and con's of intalling LXDE on Ubuntu and Lubuntu. Which one do you recommend and why?:confused:

Unity was running very slow on my Laptop with 1GB RAM, it was very cumbersome and almost unworkable. So I decided to try various DE's. I installed LXDE, XFCE, MATE, GNOME Classic, E17. But now I notice there are lots of programs that have installed with these DE's, some f them are duplicates. I installed all through terminal apt-get from various how to's from google. Now that I have settled for LXDE I want to know how to remove these other DE's and the programs they brought.

Please share your opinions on these. Thank you folks.

I guess Lubuntu would be a tad bit more suited to run LXDE than Ubuntu, since it's specifically meant for that. In particular some conflicts may be avoided. But if you've already installed LXDE under Ubuntu, then IMO the trouble to do another clean install of Lubuntu may not be worth it. Simply log into LXDE and you won't ever see Unity.

As for removing the other desktops you can use Synaptic package manager to do so. If there is a meta-package for each desktop which depends on all the packages distributed with that desktop then I think removing the meta-package will select all the others to be removed too. If not, then you'll have to individually identify all the packages installed under each desktop and select them for removal. Be careful you don't remove any package essential for proper functioning like the log-in manager, and don't remove the packages that were installed as a normal part of the initial Ubuntu installation since LXDE, XFCE and other desktops still utilise many libraries and apps from GTK and such.

---

### Post by kc1di on 2013-01-29
Hello musshan and welcome to ubuntu

IMO unless you have a ton of files already stored on ubuntu I'd do a clean install of Lubuntu would be better than trying identify all the other files to uninstall.

good luck and happy computing :)

---

### Post by sudodus on 2013-01-29
Here is a link describing how to install various desktop environments and how to get a pure system of a particular kind (if you don't want a mixture).

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

I run ***Lubuntu*** 12.04 with xubuntu-desktop (to get some extra tools, that come with Xubuntu). After installing Lubuntu from a live disk, run
```
sudo apt-get install xubuntu-desktop
```

---

### Post by whatthefunk on 2013-01-29
> **musshan said:**
> Hello People,

                       I want to know your opinion about the pro's and con's of intalling LXDE on Ubuntu and Lubuntu. Which one do you recommend and why?:confused:

Unity was running very slow on my Laptop with 1GB RAM, it was very cumbersome and almost unworkable. So I decided to try various DE's. I installed LXDE, XFCE, MATE, GNOME Classic, E17. But now I notice there are lots of programs that have installed with these DE's, some f them are duplicates. I installed all through terminal apt-get from various how to's from google. Now that I have settled for LXDE I want to know how to remove these other DE's and the programs they brought.

Please share your opinions on these. Thank you folks.

My guess is that you installed a bunch of meta packages.  A clean install of Lubuntu would probably be the easies tthing to do.  If you dant want to do that, unistall the meta packages you installed.

---

### Post by SeijiSensei on 2013-01-29
The absence of a default wireless network manager in LXDE is very annoying.  XFCE has the same problem.  All I've seen online is instructions about installing wicd or some similar approach.  To me, the absence of an equivalent to the NetworkManager application in Ubuntu and Kubuntu makes both the other desktops extemely lacking and would certainly deter a novice from installing either of them.

I installed LXDE on an older laptop just a couple of weeks ago.  It is connected to a wired network and works fine.  Wifi is another matter entirely.

---

### Post by snowpine on 2013-01-29
To fully convert Ubuntu to Lubuntu:

[http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

---

### Post by whatthefunk on 2013-01-29
> **SeijiSensei said:**
> The absence of a default wireless network manager in LXDE is very annoying.  XFCE has the same problem.  All I've seen online is instructions about installing wicd or some similar approach.  To me, the absence of an equivalent to the NetworkManager application in Ubuntu and Kubuntu makes both the other desktops extemely lacking and would certainly deter a novice from installing either of them.

I installed LXDE on an older laptop just a couple of weeks ago.  It is connected to a wired network and works fine.  Wifi is another matter entirely.

Last time I installed Lubuntu it came with Network Manager...

---

### Post by frank604 on 2013-01-29
Last time I installed xubuntu it came with network manager....

---

### Post by monkeybrain2012 on 2013-01-29
> **SeijiSensei said:**
> The absence of a default wireless network manager in LXDE is very annoying.  XFCE has the same problem.  All I've seen online is instructions about installing wicd or some similar approach.  To me, the absence of an equivalent to the NetworkManager application in Ubuntu and Kubuntu makes both the other desktops extemely lacking and would certainly deter a novice from installing either of them.

I installed LXDE on an older laptop just a couple of weeks ago.  It is connected to a wired network and works fine.  Wifi is another matter entirely.
Lubuntu comes with the network manager, haven't tried xubuntu since 10.04 but it came with the network manager as well.

@OP

+1 for clean install.

---

### Post by SeijiSensei on 2013-01-30
Maybe it's because I installed LXDE over an existing Kubuntu system with "sudo apt-get install lxde"?

I looked again through each and every entry in the program menu, and there is no mention of NetworkManager anywhere. [This article](http://wiki.lxde.org/en/PCMan%27s_Complete_LXDE_Setup_Guide) on the LXDE wiki says that it is deliberatly disabled in some distros, but that it can be enabled with LX Session Edit.  I don't see that in any of the menus either.  I'm hardly a Linux novice, but if this were my first experience with LXDE, I'd be very frustrated if I needed to correct over wifi.

So perhaps a clean install of Lubuntu provides the network manager, but an installation of just the LXDE metapackage does not?  Installing XFCE with "sudo apt-get install xfce4" didn't get me the network manager either.

Oh, and in the [FAQs]("http://wiki.lxde.org/en/LXDE:Questions") on the LXDE wiki, question 8.1 asks which network manager is provided with LXDE.  The answer given is [LXNM]("http://wiki.lxde.org/en/LXNM"), but if you follow that link it says that program is no longer in development and suggests using NetworkManager and nm-applet.  From my perspective, if the networking applet doesn't appear in the system tray by default, it's going to lead to a lot of hair-pulling by novice users.

---

### Post by snowpine on 2013-01-30
"LXDE" and "Lubuntu" are not synonymous terms.

---

### Post by frank604 on 2013-01-30
I agree with snowpine.

A new linux user should not be downloading ubuntu and sudo apt-get install xfce4 or other DE.

That just installs a vanilla pack for a DE.  A beginner should stick to 1) an easy distro, ie. ubuntu/linuxmint.  2)download a preset DE or flavor, ie. ubuntu, xubuntu, lubuntu, kubuntu.

Having a new linux user, getting vanilla packages of a DE, and setting it up for their PC is ... logically not something meant for a new user.

---

### Post by sudodus on 2013-01-30
> **SeijiSensei said:**
> Maybe it's because I installed LXDE over an existing Kubuntu system with "sudo apt-get install lxde"?

I looked again through each and every entry in the program menu, and there is no mention of NetworkManager anywhere. [This article](http://wiki.lxde.org/en/PCMan%27s_Complete_LXDE_Setup_Guide) on the LXDE wiki says that it is deliberatly disabled in some distros, but that it can be enabled with LX Session Edit.  I don't see that in any of the menus either.  I'm hardly a Linux novice, but if this were my first experience with LXDE, I'd be very frustrated if I needed to correct over wifi.

So perhaps a clean install of Lubuntu provides the network manager, but an installation of just the LXDE metapackage does not?  Installing XFCE with "sudo apt-get install xfce4" didn't get me the network manager either.

Oh, and in the [FAQs]("http://wiki.lxde.org/en/LXDE:Questions") on the LXDE wiki, question 8.1 asks which network manager is provided with LXDE.  The answer given is [LXNM]("http://wiki.lxde.org/en/LXNM"), but if you follow that link it says that program is no longer in development and suggests using NetworkManager and nm-applet.  From my perspective, if the networking applet doesn't appear in the system tray by default, it's going to lead to a lot of hair-pulling by novice users.
Try with
```
sudo apt-get install lubuntu-desktop
``` and you will get Lubuntu's look and tools, not only the desktop environment LXDE.

---

### Post by SeijiSensei on 2013-01-30
> **sudodus said:**
> Try with
```
sudo apt-get install lubuntu-desktop
``` and you will get Lubuntu's look and tools, not only the desktop environment LXDE.

I'll try that.  I do see people asking here about how to switch from, say, Unity to another desktop environment.  When I decided to do that, the suggestions I read online said to install the lxde package, not lubuntu-desktop.  If other people follow those suggestions, they'll encounter the same problem I did.

Personally, I cannot understand why the stock LXDE package doesn't include a network manager, even if I don't install the whole Lubuntu desktop.  It seems like a basic and necessary tool.

---

### Post by snowpine on 2013-01-30
> **SeijiSensei said:**
> Personally, I cannot understand why the stock LXDE package doesn't include a network manager, even if I don't install the whole Lubuntu desktop.  It seems like a basic and necessary tool.

The "L" in "LXDE" stands for "lightweight." Some people do not require network-manager and would consider it "bloat." Other people might prefer to install a different network app such as wicd.

Also consider that most users will be installing the lxde package on top of an existing system using their network connection, therefore ideally the package should not replace/supersede whatever existing network managing application is already in place.

Isn't it wonderful Ubuntu gives us the **choice** of "vanilla" LXDE as intended by its upstream developers, as well as lubuntu-desktop with customizations and additional software for a more complete and appealing out-of-the-box experience? :)

---

### Post by vasa1 on 2013-01-30
> **whatthefunk said:**
> Last time I installed Lubuntu it came with Network Manager...
True for 12.10.

---

### Post by vasa1 on 2013-01-30
> **SeijiSensei said:**
> ... it's going to lead to a lot of hair-pulling by novice users.
That's why I prefer (and suggest) a clean install of the OS itself.

---

### Post by Bucky Ball on 2013-01-30
Sounds like you didn't install the desktop environments only. For xfce and lxde you install xfce4 and lxde respectively, *not* xubuntu-desktop or lubuntu-desktop. Then you will get duplicates, as you've discovered, and a more bogged down, resource hungry beast than you had before ...

---

### Post by santosh83 on 2013-01-31
> **SeijiSensei said:**
> 
Personally, I cannot understand why the stock LXDE package doesn't include a network manager, even if I don't install the whole Lubuntu desktop.  It seems like a basic and necessary tool.

I guess that's because the NetworkManager is not part of the LXDE project, and therefore different setups may have different types of 'network manager' installed. In theory all the software components of a modern system are supposed to perfectly cooperate with each other, allowing any component to discover and use any other component seamlessly, but so far it has remained theory.

In fact, that's why we need so-called 'distributions' in the first place, because components don't automatically and intelligently interoperate but must be patched together with a huge amount of work. :-)

---

