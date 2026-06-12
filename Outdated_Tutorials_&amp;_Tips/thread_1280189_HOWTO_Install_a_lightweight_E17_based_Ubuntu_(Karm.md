---
title: "HOWTO: Install a lightweight E17 based Ubuntu (Karmic)"
date: 2009-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by kappa962 on 2009-10-01
Here is my procedure for installing an Enlightenment E17 based Ubuntu. This method starts from a minimal command line install, and avoids any unnecessary Gnome baggage. It relies exclusively on the official Ubuntu and Enlightenment repos. For a less lightweight E17 that can be installed after a full Ubuntu install check [this other Howto]("http://ubuntuforums.org/showthread.php?t=1350575").)

E17 features my favorite user interface of any window manager/desktop environment. Also, E17 is very fast and responsive, and should be good for older computers. On my computer, this OS takes just over 1GB of disk space, and uses 84MB of RAM, as opposed to 4.5GB of disk space and 211MB RAM for a normal Ubuntu installation. You'll use the Alternate install CD for this installation. (The minimal or Server install CDs should work too.)

(Two other good options for E17 based Ubuntu distros are [OpenGEU]("http://opengeu.intilinux.com/Home.html") and [MoonOS]("http://www.moonos.co.cc/"). Advantages for these are live CDs, and ease of installation. Advantages for the method described in this HowTo are less baggage, more control, and a more recent Ubuntu release.)

**1.** Boot up the Alternate install CD and select "Install command-line system" from the F4 Modes menu. Go through the text-based install. This part should be fairly straightforward, and is a good way to start any lightweight Ubuntu install. (see Distrowatch.com's [minimal Xubuntu article]("http://distrowatch.com/weekly.php?issue=20090504#feature")) (Using Karmic Beta, I had to "sudo update-grub" after installing in order to get my other OSs to show up in the GRUB menu.)

**2.** Add in the Enlightenment repo. Add this to the end of your /etc/apt/sources.list```
deb http://packages.enlightenment.org/ubuntu karmic main extras
```
Then add the key:
```
wget http://packages.enlightenment.org/repo.key -O - | sudo apt-key add -

sudo apt-get update
```

**3.** Install the software:```

sudo aptitude install xorg e17 wicd lxterminal gnome-icon-theme mousepad emodule-places emodule-tclock emodule-calendar unrar rar xarchiver gpicview

sudo aptitude install firefox thunar vlc -R
```
**xorg** and **e17** are, obviously, the essential packages for this installation.
You might want to install **ecomorph-e17** instead of **e17** for the compiz eye candy.
**wicd** for network/wifi management. I would use exalt (package name:**emodule-exalt**), but I can't get it to work. At all.
**lxterminal** as a lightweight terminal program that is significantly better than xterm
**mousepad** is my choice for a full-featured, lightweight text editor. **scite** and **Leafpad** are two other options
**gnome-icon-theme** is necesary in order for the icons in the menus and in Thunar to look right.
**xarchiver** is a nice, lightweight program for working with compressed files; **rar** and **unrar** are needed for it to work properly
**gpicview** is a nice, lightweight picture viewer
**emodule-places**, **emodule-tclock**, and **emodule-calendar** are just three extra emodules that I really like to use.
The -R option is important for **Firefox**. Otherwise it installs piles and piles of gnome-related packages. Another,  more lightweight option is to [install Chromium]("http://ubuntuforums.org/showthread.php?t=1237680&highlight=chromium").
**thunar** is my choice for a full-featured, lightweight file manager
**vlc** is, of course, the standard linux media player

Modify this list to suit your needs. Other packages you might want to install:
**abiword**: lightweight word processor. It's still a pretty bulky program, so consider using the -R option with aptitude, which will cut the installed size in half.
**galculator**: basic calculator program.

**4.** Get audio working: ```
sudo nano /etc/group
``` then add your username to the audio group.
Then, ```
sudo aptitude install alsa-base alsa-oss
```

**5.** Setup SLiM, a lightweight login manager(GDM replacement):
```
wget http://us.archive.ubuntu.com/ubuntu/pool/universe/s/slim/slim_1.3.0-2_i386.deb
sudo dpkg -i slim_1.3.0-2_i386.deb
```

or for a 64-bit version:
```
wget http://us.archive.ubuntu.com/ubuntu/pool/universe/s/slim/slim_1.3.0-2_amd64.deb
sudo dpkg -i slim_1.3.0-2_amd64.deb
```

You may want to change the theme or otherwise customize the SLiM login manager. Go here for more info: [http://slim.berlios.de/](http://slim.berlios.de/)


**6.** Reboot and setup E17 as it directs you. From a terminal, run alsamixer and unmute/turn up the appropriate things

**7.** Configure E17. Here are the things I do.
[LIST]
[*]Enlightenment can have problems mounting partitions, etc. I get around this by using the Places module and modifying my PolicyKit.conf as described here: [http://code.google.com/p/e17mods/wiki/Places](http://code.google.com/p/e17mods/wiki/Places) (edit /etc/PolicyKit/PolicyKit.conf and add <match action="org.freedesktop.hal.storage.*"><match user="[your user name]"><return result="yes"/></match></match> after <define_admin_auth group="admin"/>. If the file doesn't exist, install policykit.)
[*]If you want to disable tap-to-click: [http://ubuntuforums.org/archive/index.php/t-875016.html](http://ubuntuforums.org/archive/index.php/t-875016.html)
[*]Fix all the missing icons: menu->settings->settings panel->look->icon theme, pick "gnome"
[*]You will probably want to modify the alt-tab and window focus behaviors: menu->settings->settings panel->windows->window list and window focus
[*]The edge binding settings will probably also need modification: menu->settings->settings panel->input->edge bindings
[*]If you want the mac dock-like thingy: menu->settings->shelves->add a shelf and set up its contents with only the IBar. Then, under the advanced settings, select the invisible style.
[*]Install a more interesting theme from [http://www.e17-stuff.org](http://www.e17-stuff.org) or [http://exchange.enlightenment.org/theme](http://exchange.enlightenment.org/theme) or, my favorite, [http://www1.get-e.org/Themes/E17/](http://www1.get-e.org/Themes/E17/). Apparently some older themes may not play nicely with your new E17 installation. You can mix and match functional parts of the themes if needed.
[*]I used to install usplash, but I can't get it or xsplash to work in Karmic.*
[/LIST]

This is all that I do to get my base OS installed. Let me know if there is anything else you would recommend for an E17 based system. Hopefully I can figure out how to get Entrance login manager and a splash screen working and add those things into this howto.

*I finally got usplash to work by doing [this]("http://ubuntuforums.org/showpost.php?p=8024427&postcount=17") and [this]("http://ubuntuforums.org/showthread.php?t=1283710#8"). Given the current state of usplash and xsplash, I'm going to hold off adding this into the main part of this howto until those packages have stabilized.

---

### Post by Tux Aubrey on 2009-10-06
Excellent HOWTO, kappa962.  That is a nice light desktop!

I have been doing something similar with a very basic Karmic server install.  I'll add a couple of suggestions:

Modules: there are lots of other e17 modules that are useful and work very well.  I'd include taskbar, net and mail by default and use them as desktop gadgets (or on a shelf) and also systray (even though it has an annoying minor bug in the current packaged version).  On my latest install, I simply installed all the avaiable modules (_emodules-all_) and, surprisingly, haven't had any problems at all - although I have not tried to load and use them all yet.

I'm not a fan of EFM, the native e17 filemanager, so I install _thunar_.  There was a problem with thunar throwing an error on shutdown on Jaunty Jackalope e17 installs that does not seem to occur now with Karmic.

I second your recommendation of _wicd_ as a superor network manager for e17.

I always install _scite_ as my text editor.  It has lots of useful features for marking up code.

I'm experimenting at the moment with lightweight browsers - _Google Chromium _(from the launchpad repos) is heading my list right now.  Much lighter and faster than Firefox (but not as versatile).

I usually install _gdm_ too - but the version now in Karmic is pretty slow and the gdmsetup utility does not work in e17.  Still looking for a decent graphical login/display manager.

I certainly agree that some of e17's default settings need changing - window focus being an essential first step.  I also get rid of all edge bindings (Settings>Input>Edge Bindings) to stop the virtual desktops sliding around when the mouse hits the edge of the screen.

People do need to be aware that some (most) older e17 themes will not work well without tweaking the "Advanced" settings.  In particular, many will need to have the "Widgets" function linked back to the default theme so that the systems dialog displays properly.

My setup (like yours, I believe) is suitable for either a full size machine, a laptop or a netbook.  With my netbook install, I make the menu fonts large so that I can see them clearly from a normal viewing distance and keep the desktop pretty clear.

It will be interesting to see whetehr other people have alternative suggestions for apps and modules.

---

### Post by kappa962 on 2009-10-07
Thanks. I've updated the howto in light of your suggestions. Also, I finally got usplash to work, so I added a note on that.

I agree with you about EFM. I really hope that the Enlightenment people are putting some effort into EFM, Entrance(d), and Exalt. If those three things were more usable, it would go a long way towards getting more people using E17.

---

### Post by sh4d0w808 on 2009-10-07
For application, I recommend Abiword as a lightweight word processor.

Anyway: thx for this good work, keep it up! Do U think that will this run on P2 300 with 128 MB RAM laptop?

---

### Post by Tux Aubrey on 2009-10-08
> **sh4d0w808 said:**
> For application, I recommend Abiword as a lightweight word processor.



+1 for Abiword!  I usually put an e17 desktop over Xubuntu and therefor Abiword (and Thunar) is already installed.  Strangely, there has been bug in recent Karmic Xubuntu builds that pulls in the _whole _OpenOffice suite into an install (but its NOT on the Live CD).  OpenOffice sort of defeats the purpose of a "lightweight" distro (although Xfce is getting pretty bloated and slow too, IMO)

Overall, the current (beta) Karmic Xubuntu is a terrible platform for e17.  The new GDM and Xsplash are unconfiguarable via the supplied GUIs (they will not unlock or just crash in e17) and they actually take so long to run that the speed of e17 startup is totally masked.

> Do U think that will this run on P2 300 with 128 MB RAM laptop?

On a minimal install (as per the OP), I _think _it would work.  Please let us know!

---

### Post by kevinguillorytraining on 2009-10-09
Excellent howto. Thanks

---

### Post by kappa962 on 2009-10-09
> **Tux Aubrey said:**
> Overall, the current (beta) Karmic Xubuntu is a terrible platform for e17.  The new GDM and Xsplash are unconfiguarable via the supplied GUIs (they will not unlock or just crash in e17) and they actually take so long to run that the speed of e17 startup is totally masked.

My understanding is that Xubuntu isn't really intended to be lightweight. It's actually heavier than normal Ubuntu in some ways. If you want a lightweight version of Xubuntu, I recommend distrowatch.com's minimal Xubuntu article linked in my howto. With xsplash being so new, I'm expecting things to get a lot better with ease of configuration. For now, I don't have it installed. Usplash is finally working for me, and I'm hoping that subsequent updates will make installation easier.

---

### Post by sh4d0w808 on 2009-10-10
> On a minimal install (as per the OP), I _think _it would work.  Please let us know!

I will let U know. I like these old Thinkpads :D

I've done, here is my desktop:
[http://picasaweb.google.com/sh4d0w808/Screenshots#5391075770664123106](http://picasaweb.google.com/sh4d0w808/Screenshots#5391075770664123106)

---

### Post by Tux Aubrey on 2009-10-12
> **sh4d0w808 said:**
> I will let U know. I like these old Thinkpads :D

I've done, here is my desktop:
[http://picasaweb.google.com/sh4d0w808/Screenshots#5391075770664123106](http://picasaweb.google.com/sh4d0w808/Screenshots#5391075770664123106)

Sweet!  What is performance like?

---

### Post by sh4d0w808 on 2009-10-14
Not exactly equal to my expectations, but usable. It was a surprise for me that only 2-3 megs of RAM available after bootup - but it could be an issue of Karmic, not Enlightenment.

---

### Post by kappa962 on 2009-10-15
> **sh4d0w808 said:**
> Not exactly equal to my expectations, but usable. It was a surprise for me that only 2-3 megs of RAM available after bootup - but it could be an issue of Karmic, not Enlightenment.

That's surprising to me too. I'm very happy with my installation, but it is using much more memory than seems necessary. Give me a few days and I'll hopefully find a fix.

EDIT: nevermind, I was reading the output of free -m wrong. My OS is only using 84 megs of RAM. I don't know why yours would be using so much.

---

### Post by sh4d0w808 on 2009-10-18
First I have checked the output of top. Now I have run free -m and saw, that 68 MB reserved for cache and 50 MB is free of it.

---

### Post by antonym on 2009-10-21
Awesome howto, kappa962... I've set this up on a netbook with a tiny SSD and I'm really looking forward to using it. :)

I've noticed, however, that the non-elightenment-native applications (ie. lxterminal, wicd, thunar) all have a gigantic font for the menus and dialog boxes. I've fiddled with the Enlightenment font settings, but I haven't been able to fix this -- do you have any idea how I might bring it down to a reasonable size? (and perhaps even apply a gtk theme or something to them, to help them match the enlightenment theme somewhat?)

Thanks in advance :)

---

### Post by raprap30 on 2009-10-21
You guys should try OpenGEU, it is an e17 based Ubuntu distro [http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

---

### Post by Igneo676 on 2009-10-22
I am definitely considering installing this on my little Toshiba NB205...
...though I was wondering if you all knew how good the battery life is on this compared to a standard Ubuntu install.

I typically get about 6 hours on a full charge, XP (before I wiped it) got 9 hours.

Beyond that, any additional packages I need to install to manage battery life, optimize for battery life, etc?

Never really have done this sort of thing before, heh

I also went for this install on my main desktop on my 2nd hard drive just to try it out: ecomorph was extremely buggy and a quick replacement with standard E17 finished the job quite nicely and ended my seg-faults.

I also noticed that I couldn't set myself up for an auto-login since the /etc/init/tty1.conf didn't exist. Did I do something wrong? I noticed rungetty either didn't run or simply appeared the same as the standard command-line login indicative of the CLI. Given, I typed out the bash file by hand and I may have done something wrong there as it didn't automatically run startx though that shouldn't interfere with rungetty, should it?

Just a tad bit annoying when you have to automatically run startx and login yourself when you want an OS that boots with significantly smaller boot times.

Edit: Come to think of it, maybe ecomorph's segfaults were the result of not installing the necessary Nvidia drivers? I need to find some documentation on installing nvidia drivers without using Envy or the native Ubuntu driver installer...

---

### Post by kappa962 on 2009-10-22
> **raprap30 said:**
> You guys should try OpenGEU, it is an e17 based Ubuntu distro [http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

OpenGEU is a decent E17-Ubuntu distro, as is MoonOS (which appears to be inspired by Linux Mint and OpenGEU). Both of them are a little too heavy for my tastes, and I like having an OS based off a more recent Ubuntu release. A modified MoonOS was my primary OS for a while. However, now that it's so easy to get an E17 based Ubuntu with the official E17 repos, there's not really many advantages for me using a separate distro.

I've just updated my howto and added links to both of those distros.

---

### Post by kappa962 on 2009-10-22
> **Igneo676 said:**
> I am definitely considering installing this on my little Toshiba NB205...
...though I was wondering if you all knew how good the battery life is on this compared to a standard Ubuntu install.

I typically get about 6 hours on a full charge, XP (before I wiped it) got 9 hours.

Beyond that, any additional packages I need to install to manage battery life, optimize for battery life, etc?

Never really have done this sort of thing before, heh

I also went for this install on my main desktop on my 2nd hard drive just to try it out: ecomorph was extremely buggy and a quick replacement with standard E17 finished the job quite nicely and ended my seg-faults.

I also noticed that I couldn't set myself up for an auto-login since the /etc/init/tty1.conf didn't exist. Did I do something wrong? I noticed rungetty either didn't run or simply appeared the same as the standard command-line login indicative of the CLI. Given, I typed out the bash file by hand and I may have done something wrong there as it didn't automatically run startx though that shouldn't interfere with rungetty, should it?

Just a tad bit annoying when you have to automatically run startx and login yourself when you want an OS that boots with significantly smaller boot times.

That's odd. What files are in your /etc/init/ directory? There should be .conf files for tty1-tty6. Also, can you CTRL-ALT-F# to switch between terminals?

Now that you have the OS runnable, you can just open ~/.bash_profile in your text editor and copy and paste the text from your browser. That should get startx to autorun.

I haven't actually timed my bootup yet, but it seems much faster than other Ubuntu's I have used. Karmic seems to have made some huge strides in shortening bootup times, and E17 starts up nearly instantaneously.

E17 automatically installs e-modules for cpu-frequency scaling and battery-related tasks. I don't use them, but I believe they are functional. I wouldn't expect this E17-Ubuntu install to be much better than normal Ubuntu for battery life. Let me know if you notice it being significantly different.

---

### Post by Igneo676 on 2009-10-22
Ah, my own eyes are treacherous

I thought it was ttyl, not tty1. I was typing this ALL in manually and so therein lies the mistake. I'll get everything working and report back from the desktop.

Any advice for getting ecomorph to work? I would rather get it going than not and I'm not entirely sure how to install the drivers for my Nvidia card...

Edit: Success! Everything boots perfectly and works as it should have. I feel rather noobish now, heh. And even got my nvidia driver installed.

I'll be doing this on my lappy before long

---

### Post by kappa962 on 2009-10-23
> **Igneo676 said:**
> Any advice for getting ecomorph to work? I would rather get it going than not and I'm not entirely sure how to install the drivers for my Nvidia card...


Unfortunately, I can't get ecomorph to work either. I'm hoping to tackle that issue soon. As far as drivers go, most drivers that you might need are installed with the Ubuntu kernel and/or Xorg. So you should, theoretically, already have them. Compiz works with my video card in Gnome, but E17-ecomorph doesn't seem to know how to use it.

---

### Post by Igneo676 on 2009-10-24
At one point I went through with Envy and discovered it does work, and it ended my segfaults on Ecomorph...
...my issue became how to enable the fancy effects. I loaded up the ecomorph module and couldn't figure out how to do it. It did have a section on activated the required part like standard Compiz, and it did slow me down for a second, but ultimately there was no change.

Do you know the file that the configuration module edits? Maybe manually editing the configuration and restarting will fix it?

---

### Post by Drackonn on 2009-10-30
as anyone tried something like this on an eeepc? I have a 1005ha running Ubuntu 9.10 NBR ... but I have always loved enlightment, and to be honest I feel like Ubuntu has so much extra garbage that I dont need on the netbook.

So i was looking to see everyone elses experiences, either way I will be trying this out in the next few days and keep everyone posted.

---

### Post by Tux Aubrey on 2009-10-31
> anyone tried something like this on an eeepc?

Not an eepc, but I have installed e17 from these repos onto Ubuntu on my Dell Latitude 2100 (atom-based netbook) and it flies and has been rock solid.  I didn't start from a minimal Ubuntu, but went the other way - removing things and replacing them with lighter/more e-friendly alternatives (wicd, Abiword, Chromium browser etc).

---

### Post by Drackonn on 2009-10-31
the problem I am having is that some of the function keys dont work in e17 ... which im sort of confused about, because everything works under gnome.


right now im just running a normal 9.10 NBR install and installed e17 to check it out before committing myself to anything ... glad I did because half of the stuff doesnt work.


wireless and things like that work, but things like my volume control/brightness dont work. but imho netbooks are about convenience, so having half of my shortcut keys not working, kind of defeats the purpose :(

---

### Post by Tux Aubrey on 2009-11-01
> **Drackonn said:**
> the problem I am having is that some of the function keys dont work in e17

Did you look into Settings>Settings Panel>Input>Key Bindings ?

---

### Post by kevdog on 2009-11-01
What's the best way to add e17 to karmic?  This method or using ruispais' script for svn?

---

### Post by Tux Aubrey on 2009-11-01
> What's the best way to add e17 to karmic? This method or using ruispais' script for svn? 

Hi kevdog

Its a matter of choice, really.

This method will give you a recent and fairly stable build of e17 and is quick and "normal" (ie using standard repos and tools).  It is highly likely that the .deb packages will be rebuilt around svn freezes and e17 is Very Close to an official beta.

The e17-svn way is up-to-date to the minute you install it or update it.  It does take a long time to install (download, make and install for every component) and you can get the occasional "bad" update that requires fixing manually.  Normally I'd say it is way better as any bug fixes and improvements are available instantly, but right now I honestly can't point to any significant differences between the packages.enlightenment.org repo version and the ones I update daily from svn - most of the work going on right now is very minor or related to translations.  There are still few minor bugs - but they don't seem to get any attention.

I am using both methods on different machines.  Both work well on Karmic.

All of the above relates to a fairly "vanilla" install.  If you want to use modules or add-ons from outside the main trunk (like ecomorph), you are pretty much on your own.

Good Luck!

---

### Post by Drackonn on 2009-11-02
> **Tux Aubrey said:**
> Did you look into Settings>Settings Panel>Input>Key Bindings ?


Ok I got everything working, the thing is right now all I was doing was running e17 as an alternate at boot instead of gnome, when I log in, but I cannot get the internet to work.

I am using 9.10 NBR ... so if I try to get wicd, it tries to remove gnome-network-manager, if I do this then I dont have the nifty little network manager in the upper right corner when Im logged into NBR. so for right now I cant get the full feel for e17 ... I will probably repartition my drive and do 2 seperate installs, one with 9.10 NBR since its stable and everything works. and 1 with a minimal e17 install to see which one I prefer.


Since I am running all this on a netbook, I am really looking for speed ... all I use it for is for internet access, email, music on the go ... so the faster the better ... we shall see in the next few days.


I just tried to run wicd on 9.10 NBR ... I cannot for the life of me get it to work, it cannot find any of my local networks etc ... and I cannot get gnome-network-manager to wok in e17 ...

---

### Post by Takenover83 on 2009-11-02
I was going to give this a shot, but from the looks of it, there is no repository for the powerpc, which is what the PS3 uses :(

---

### Post by Zezu on 2009-11-04
Hey everyone.
Nice job on the install guide. I have 3 issues I am dealing with right now:
1. Loading nm-applet on login
    - I know you suggested wicd as the default, but for whatever reason, it had a hard time connecting to the various routers on campus. Also, it displays each individual router, even if thay all have the same ssid. For these reasons, i chose to go back to NetworkManager. But now I cant get it to load on login, and i have to call it manually. Im a n00b at scripting, and did try my hand at it, but without any luck.

2. I cant get the alt-ctrl-backspace behaviour to come back. I tried modifying xorg.conf, but had no luck. any suggestions?

3. enlightenment seems to freeze randomly on login. restarting enlightenment fixes the issue, and i dont have any more problems until my next login. any suggestions on where to start with this on?

Thanks all!


Edit:

I have now fixed all three. First line gets alt-ctrl-backspace back.

<code> 
#!/bin/bash

setxkbmap -option terminate:ctrl_alt_bksp
nm-applet&
</code>

---

### Post by Drackonn on 2009-11-04
There is a howto somewhere on getting networkmanager to lauch at startup in e17, I cant seem to find it though .... 

as for me, I will be back to running NBR, until I can figure something else out, wicd doesnt work well with the hidden networks at my job, so i cant use the internet there, exalt doesnt work ...

Im also not linux savvy enough to install ubuntu and then strip it down to what I want without breaking things, and the minimal installs dont recognize my network adapter on the eeepc to install a command line or minimal install ... so I will be waiting for some more 1005ha support before attempting this again.

---

### Post by kappa962 on 2009-11-05
There should be nothing to keep networkmanager from working fine with E17. The problem seems to be that there are no GUIs for it that work with lightweight OSes. Some people have gotten it to work by using a system tray program for E17. Some of the pages that show up by googling "networkmanager "without gnome"" may be a starting point for tackling this problem.

WICD works for most purposes, but I'm not sure why it is necessary to reinvent the wheel here. Surely we aren't the only people who would like to use networkmanager without gnome.


Zezu, at what point does enlightenment freeze? How do you restart it at that point? Rebooting? ctrl-alt-backspace?

---

### Post by clodio on 2009-11-05
I use network manager with e17 and it works very well.
Anyone know how to use mail module? I can't work it

---

### Post by Zezu on 2009-11-05
> **kappa962 said:**
>  Some people have gotten it to work by using a system tray program for E17. Some of the pages that show up by googling "networkmanager "without gnome"" may be a starting point for tackling this problem.

Im using Fbpanel as my sys tray, but I have to manually call up nm-applet each time I log in. After that, I dont have any issues. 


> **kappa962 said:**
> 
Zezu, at what point does enlightenment freeze? How do you restart it at that point? Rebooting? ctrl-alt-backspace?

After I log in, the splash screen comes back up. After loading for about another 10 sec, the splash logo goes away, the splash background remains and my cursor appears. I can move the cursor around, but clicking does nothing. I use alt-ctrl-end to restart enlightenment and everything is good after that. I still havent figured out how to get alt-ctrl-backspace to work with enlightenment without inputting a command in the terminal every time I log in. :?

---

### Post by Duskao on 2009-11-09
Is it possible to install the E17 desktop aside the default gnome desktop and choose between them during login? I have no problems with the bloat of the gnome stuff still being around, but it would be nice to try out my own E17 desktop as opposed to MoonOS which I tried and while it was nice and all, I found it a wee bit cumbersome.

---

### Post by Tux Aubrey on 2009-11-09
> **Duskao said:**
> Is it possible to install the E17 desktop aside the default gnome desktop and choose between them during login? I have no problems with the bloat of the gnome stuff still being around, but it would be nice to try out my own E17 desktop as opposed to MoonOS which I tried and while it was nice and all, I found it a wee bit cumbersome.

Not a problem:

Add in the Enlightenment repo. Add this to the end of your /etc/apt/sources.list (assuming you are on karmic):

```
deb http://packages.enlightenment.org/ubuntu karmic main extras
```
Then add the key:

```
wget http://packages.enlightenment.org/repo.key -O - | sudo apt-key add -
```

```
sudo apt-get update
```

Install the software:

```
sudo aptitude install e17 emodules-all
```

Logout and you should have an "Enlightenment" session available from gdm.

The first time you log in, you will get a guided set-up - choose the "system" (or gnome) menus and a "standard" profile.

---

### Post by cheshire on 2009-11-11
I have a pentium 3 800mhz laptop w/ 256mb ram that has an ATI Rage Mobility M3 AGP 2X graphics card in it.  I am new to linux and wanted to try ubuntu on it.  I have discovered that I need to stay with something before the 9.0 releases to use the ATI drivers for my graphics card to get proper screen resolution and was wondering if you can use an alternate install of Ubuntu 8.04LTS w/ E17  describe here?  Would that be a good fit for my machine?  Seems like it would be lite enough to run well.  Any input would be much appreciated.  Thanks.

---

### Post by julianb on 2009-11-11
Cheshire - I know from experience that it's possible to run Ubuntu (standard version with GNOME) on a laptop with 256MB ram. For me, Ubuntu 9.04 was much quicker than WinXP. 

However, there's no reason you shouldn't try something lighter, like the E17+Ubuntu 8.04 setup you mention. 

Another option is to [install the packages that "masonux" uses]("http://sites.google.com/site/masonux/home/notes-to-myself") on top of a [minimal Ubuntu]("https://help.ubuntu.com/community/Installation/MinimalCD") setup.

---

### Post by kappa962 on 2009-11-12
> **cheshire said:**
> I have a pentium 3 800mhz laptop w/ 256mb ram that has an ATI Rage Mobility M3 AGP 2X graphics card in it.  I am new to linux and wanted to try ubuntu on it.  I have discovered that I need to stay with something before the 9.0 releases to use the ATI drivers for my graphics card to get proper screen resolution and was wondering if you can use an alternate install of Ubuntu 8.04LTS w/ E17  describe here?  Would that be a good fit for my machine?  Seems like it would be lite enough to run well.  Any input would be much appreciated.  Thanks.

It definitely can work with earlier Ubuntu releases, however, some of the packages I recommended will not be in the Ubuntu repos for the earlier releases. You'll either need to use alternate packages or find other repos. Or install them without the help of Apt.


Zezu, I haven't forgotten about you, I'm hoping to try and find some answers to your questions, but I just switched computers to a Macbook, and I'm fighting with all sorts of problems of my own right now (mostly relating to getting my linux partitions bootable.) Also, if you want to run a command before going into enlightenment, you can just put that in your ~/.bash_profile file, right before startx. I don't know if that could help your ctrl-alt-backspace issue or not. At one point I was using a command to enable the use of my right alt key (which Ubuntu disables for some reason) and I put the command there.

---

### Post by Duskao on 2009-11-12
Cheshire you could also use the open source drivers. You will likely get better performance from them as your card is rather old.

---

### Post by Duskao on 2009-11-12
Eeeeeek.... Followed what you posted and this popped up. I'm unsure about it as I don't want to funky up my network manager. Any thoughs??

Here is what it showed.

The following packages have unmet dependencies:
  network-manager-gnome: Depends: network-manager (>= 0.8~a~git.20090831t055002) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
network-manager-gnome

Leave the following dependencies unresolved:
ubuntu-desktop recommends network-manager-gnome
Score is -81

Accept this solution? [Y/n/q/?]

---

### Post by Leighman on 2009-11-16
I'd also be interested in some feedback on the above.

Thanks

---

### Post by Zezu on 2009-11-16
> **Zezu said:**
> Hey everyone.
Nice job on the install guide. I have 3 issues I am dealing with right now:

3. enlightenment seems to freeze randomly on login. restarting enlightenment fixes the issue, and i dont have any more problems until my next login. any suggestions on where to start with this on?

Thanks all!

So I figured this one out. The new X-splash screen that shows up when you login was messing up and hanging e17. I figured this out after removing the splash. As a side effect, my login time dropped by a good 10-15 sec. The X-splash is a set loop, so if you have it enabled, your just wasting your time.

To remove X-splash:
```
mv /etc/gdm/PreSession/Default /etc/gdm/PreSession/Default.disabled
```

if something goes wrong, just change it back.

Special thanks for code to Fanf
[http://fanf42.blogspot.com/2009/09/faster-log-in-in-ubuntu-910-karmic.html]("http://fanf42.blogspot.com/2009/09/faster-log-in-in-ubuntu-910-karmic.html")

EDIT:
Note, this won't remove xsplash from running during boot. It will just stop it from loading after login.

---

### Post by kappa962 on 2009-11-17
> **Zezu said:**
> So I figured this one out. The new X-splash screen that shows up when you login was messing up and hanging e17. I figured this out after removing the splash. As a side effect, my login time dropped by a good 10-15 sec. The X-splash is a set loop, so if you have it enabled, your just wasting your time.

Sweet. It seems like the idea for xsplash is a good one, but it hasn't quite worked out yet. I'm looking forward to the day that it is a little more developed, and better documented. Hopefully for Lucid: [http://www.netsplit.com/2009/09/02/making-a-splash/](http://www.netsplit.com/2009/09/02/making-a-splash/)

---

### Post by Zezu on 2009-11-17
> **kappa962 said:**
> Sweet. It seems like the idea for xsplash is a good one, but it hasn't quite worked out yet. I'm looking forward to the day that it is a little more developed, and better documented. Hopefully for Lucid: [http://www.netsplit.com/2009/09/02/making-a-splash/](http://www.netsplit.com/2009/09/02/making-a-splash/)

I agree completely. Moving towards xsplash in the coming releases should help with the boot speed. But the current setup of going back to xsplash after login is not necessary for enlightenment.

 Looking at the code in /etc/gdm/PreSession/Default , it seems like they were trying to create a visual buffer for the time it takes for your desktop manager to load. As enlightenment is light weight by its nature, this should be about 1-2 sec of time. Thus this splash really isnt needed.

---

### Post by jmrey on 2009-11-18
Hi, great post. 

I finally managed to install E17 in my karmic box but when I try to install Entrance it does not found in the repositories?

Any other source apart from CVS to get entrance? Are there any other repositories?

Rgrds, 
---
Juanma.

---

### Post by kappa962 on 2009-11-18
> **jmrey said:**
> I finally managed to install E17 in my karmic box but when I try to install Entrance it does not found in the repositories?

Any other source apart from CVS to get entrance? Are there any other repositories?


Not to my knowledge. The reason I'm doing the hack with rungetty and the .bash_profile script is because I couldn't find a repo with Entrance, and I didn't want to use GDM. If it ever shows up in a repo, I'd love to try it.

---

### Post by Darko82 on 2009-11-19
I installed Slim from jaunty packages and it works really fine on karmic ;)

---

### Post by kappa962 on 2009-11-19
> **Darko82 said:**
> I installed Slim from jaunty packages and it works really fine on karmic ;)

Thanks for posting this. Somehow, I never found SLiM while I was looking for GDM replacements. It's great. I'm planning to update the howto soon to use SLiM instead of the rungetty/bash_profile hack.

EDIT: The howto is now updated.

---

### Post by meditatingfrog on 2009-11-19
great idea, great how to.  i installed enlightenment, e17 on my system (ubuntu jaunty) after trying out moonOS in a vm.  i installed it using svn, and compiling the dependencies and the main binary manually (though i recently read there's a script that can install via svn for you).  

i tried out your recommendation to use wicd, and i'm having trouble with it.  It works okay in gnome (except i can't connect to my own encrypted network).  In enlightenment, there doesn't appear to be a place for the wicd-client system tray to go.  I think i'll have to remove wicd and reinstall nm-applet, and run nm-applet out of a terminal like I was before.  enlightenment is pretty useless without being able to connect to the network.

---

### Post by kappa962 on 2009-11-19
> **meditatingfrog said:**
> i tried out your recommendation to use wicd, and i'm having trouble with it.  It works okay in gnome (except i can't connect to my own encrypted network).  In enlightenment, there doesn't appear to be a place for the wicd-client system tray to go.  I think i'll have to remove wicd and reinstall nm-applet, and run nm-applet out of a terminal like I was before.  enlightenment is pretty useless without being able to connect to the network.

You shouldn't need system tray. The WICD service starts at bootup, before GNOME or E17 are started. As long as you can run the WICD GUI to set it up, it should work. It should also work with encrypted networks. What does it do when you try to log into your network?

---

### Post by Tux Aubrey on 2009-11-19
> **meditatingfrog said:**
> In enlightenment, there doesn't appear to be a place for the wicd-client system tray to go.

Have you got the "systray" module loaded (Settings>Modules>systray>Load) and the systray gadget on your desktop (Settings>Gadgets>...)?  It isn't loaded by default but it should be available as it is part of the main "e" package.  It does have a bug that makes it difficult to move around the desktop - you have to drag the borders and "resize" it to where you want it on the desktop.  Apart from that it works fine for wicd (as well as transmission and TomBoy notes and lots of other things that don't close down completely or iconize).

---

### Post by meditatingfrog on 2009-11-19
> **kappa962 said:**
> You shouldn't need system tray. The WICD service starts at bootup, before GNOME or E17 are started. As long as you can run the WICD GUI to set it up, it should work. It should also work with encrypted networks. What does it do when you try to log into your network?

When i execute wicd in e17 a gui doesn't run.  Ah, didn't try the wicd-client until i tried it out in gnome. i should reinstall it and try executing wicd-client in e17.  

when i tried connecting to my network in wicd, i got this error:  "required encryption information is missing."

---

### Post by meditatingfrog on 2009-11-20
> **Tux Aubrey said:**
> Have you got the "systray" module loaded (Settings>Modules>systray>Load) and the systray gadget on your desktop (Settings>Gadgets>...)?  It isn't loaded by default but it should be available as it is part of the main "e" package.  It does have a bug that makes it difficult to move around the desktop - you have to drag the borders and "resize" it to where you want it on the desktop.  Apart from that it works fine for wicd (as well as transmission and TomBoy notes and lots of other things that don't close down completely or iconize).

Sorry I didn't answer your original question.  I don't have a systray gadget that is selectable in settings > gadgets.  I have start, ibar, ibox, clock, battery, cpufreq, temperature, pager, mixer, and settings.

I got back on here to let everyone know that i did manage to get wicd working.  It's kind of weird.  If I would type wicd-client in a terminal, wicd wouldn't start up, I have to start it under run command > wicd-client then select the wicd-client (network manager) icon to see the gui.  i spent about 20 minutes trying to get wicd working without the wicd-client gui, but pretty much got nowhere after reading several man pages.

btw, thanks for your post.

---

### Post by meditatingfrog on 2009-11-20
I would also point out that in enlightenment for me, the battery warning icon, and battery indicator is more accurate than gnome-power-manager's.  I know this sounds weird, but i think maybe compiling from source had something to do with it.

---

### Post by Tux Aubrey on 2009-11-20
> **meditatingfrog said:**
> I don't have a systray gadget that is selectable in settings > gadgets.  I have start, ibar, ibox, clock, battery, cpufreq, temperature, pager, mixer, and settings.


Those are just the modules loaded by default.  Go to Settings>Modules (not "Gadgets") and you'll see what is available and loaded.  Systray should be on the list to the left (along with some other non-default modules like taskbar and places that I use all the time).  Load it and THEN go to Settings>Gadgets - it should be available to select and place on the desktop.

You can also unload modules you don't need - that helps speed things up a bit (and reduces the amount of stuff that can go wrong).

---

### Post by Duskao on 2009-11-20
Well, I got everything working, mostly perfectly, I am really liking e17, can do pretty much anything with it. However, I for some reason cannot use the Ubuntu Software Centre, or Add-Remove Applications. Any thoughts?

---

### Post by Darko82 on 2009-11-20
> **kappa962 said:**
> Thanks for posting this. Somehow, I never found SLiM while I was looking for GDM replacements. It's great. I'm planning to update the howto soon to use SLiM instead of the rungetty/bash_profile hack.

EDIT: The howto is now updated.

If you want that your login desktop is the same of your desktop background do this:

backup the default Slim background (or the background of the Slim theme you want to use)
```
sudo mv /usr/share/slim/themes/default/background.jpg /usr/share/slim/themes/default/background.old.jpg
```

do a symbolic link of your desktop background into the default Slim theme directory (or the theme you want to use)
```
sudo ln -s PATH_OF_YOUR_DESKTOP_BACKGROUND.jpg /usr/share/slim/themes/default/background.jpg
```

The Slim theme used is setted in /etc/slim.conf

---

### Post by Tux Aubrey on 2009-11-20
> **Duskao said:**
> Well, I got everything working, mostly perfectly, I am really liking e17, can do pretty much anything with it. However, I for some reason cannot use the Ubuntu Software Centre, or Add-Remove Applications. Any thoughts?

If they are appearing in your menus, starting OK but now doing anything when you select install, it could be a permissions problem.

Easy fix:

1.Open the app

2. RIGHT CLICK the titlebar

3. select "edit icon"

4. insert "gksudo " at the start of the "executable" line

5. Apply - Close

6. close and restart the app (you should be asked for your password.)

This happened to me with the Software Center (but not Add/Remove) on a recent Karmic install using e17 from svn.  It often happens with Synaptic too - but you get a message about not having admin privileges.

---

### Post by Duskao on 2009-11-20
Thanks alot!

---

### Post by meditatingfrog on 2009-11-20
> **Tux Aubrey said:**
> Those are just the modules loaded by default.  Go to Settings>Modules (not "Gadgets") and you'll see what is available and loaded.  Systray should be on the list to the left (along with some other non-default modules like taskbar and places that I use all the time).  Load it and THEN go to Settings>Gadgets - it should be available to select and place on the desktop.

You can also unload modules you don't need - that helps speed things up a bit (and reduces the amount of stuff that can go wrong).

Looks like systray isn't in the cards for me.  I don't think i need it though (thankfully).  When I added the module from settings > modules there wasn't a problem, but when I tried adding the systray in settings > gadgets E17 "SEGV'd" so I had to recover.  I tried two or three times and got the same error.  I'm using ver 0.16.999.62.

One thing that I'm kind of bummed out by is my inability to specify a dark background with a bright font for higher contrast for all applications by default (e.g. mousepad, etc).  Anyone know if this is possible in E17?

---

### Post by Duskao on 2009-11-20
As you mentioned before, you are a fan of Thunar, I am also a fan of it, but my only issue here is that when I try to open up a folder (home, second hd, I am just getting folders in a window, not really a file manager, is there a way I can set thunar as the default?

---

### Post by Duskao on 2009-11-20
Also I'm having issues with mounting as you mentioned earlier in the HowTo:. But I tried following what you said to do, but I have had no luck with it. I'm getting this error.


Can't Mount Device

org.freedesktop.Hal.Device.Volume.PermissionDenied
Device /dev/sr0 is listed in /etc/fstab. Refusing to Mount.

Did I do something wrong?

---

### Post by Tux Aubrey on 2009-11-20
> **Duskao said:**
> As you mentioned before, you are a fan of Thunar, I am also a fan of it, but my only issue here is that when I try to open up a folder (home, second hd, I am just getting folders in a window, not really a file manager, is there a way I can set thunar as the default?

The "folders in a window" is the Enlightenment Filemanager (EFM).  I generally turn it off (under Modules - ie. just unload it) - but that _will_ also take away icons on your desktop.  You can then put Thunar on a launcher (on the shelf or on a free-floating ibar gadget.  

The easiest way to create a launcher icon is to start the app from the command line : >thunar , RIGHT CLICK the title bar and select "Add Application..." , select "To Launcher" and "default" (assuming you still only have the one "ibar").

If you are using the "Places" Module and Gadget and it isn't opening Thunar when you click on a drive/partition icon, it has a "configuration" dialog (RIGHT CLICK) that you can use to point it to the right file.

Just as a tip, it is usually better in e to specify the full path when setting up a launcher - ie "/usr/share/bin/thunar".  If something doesn't work properly first time, try the full path method.

By the way, I and several other users put together a set of tutorials on using the e desktop (they are [here]("http://cafelinux.org/OzOs/content/how-index")).  Some are little old now but the basics have not changed much (you can ignore most warnings about things causing seg faults - most of that has been fixed).

EDIT: If the OP or a Mod wants to split this thread (say, make one about "e17 Desktop Tips"), I'm happy to follow it.

---

### Post by kappa962 on 2009-11-20
> **Duskao said:**
> Also I'm having issues with mounting as you mentioned earlier in the HowTo:. But I tried following what you said to do, but I have had no luck with it. I'm getting this error.


Can't Mount Device

org.freedesktop.Hal.Device.Volume.PermissionDenied
Device /dev/sr0 is listed in /etc/fstab. Refusing to Mount.

Did I do something wrong?

Can you post your PolicyKit.conf file?

---

### Post by Duskao on 2009-11-22
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <match user="USERNAME">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
</config>




There is the PolicyKit.conf I tried to make the changes and such, but they didn't work. Also, I do have my actual user name where "USERNAME" is, but I didn't feel it was any one else need to know :D.

---

### Post by kappa962 on 2009-11-22
> **Duskao said:**
> <?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <match user="USERNAME">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
</config>




There is the PolicyKit.conf I tried to make the changes and such, but they didn't work. Also, I do have my actual user name where "USERNAME" is, but I didn't feel it was any one else need to know :D.

That definitely seems like it should work. Here is mine:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
    <match action="org.freedesktop.hal.storage.*">
        <match user="[your user name]">
            <return result="yes"/>
        </match>
    </match>
</config>
```

What's really odd to me is that I forgot to replace [your user name] with my actual username and it still works. So it seems like yours should work, and mine shouldn't. But, somehow, the opposite is true. Bizarre. You did try rebooting, right? The new .conf file doesn't take effect until you reboot (unless it is possible to restart the service in charge of granting those permissions.)

---

### Post by Duskao on 2009-11-23
Got it working. Yeah, did everything, had a guy on the #e irc help me out. Took a fair amount of work though. Thanks for the help anyway.

---

### Post by Tux Aubrey on 2009-11-23
> **Duskao said:**
> Got it working. Yeah, did everything, had a guy on the #e irc help me out. Took a fair amount of work though. Thanks for the help anyway.

So what was the trick?  This is a pretty common problem (but not usually fatal for me because either Thunar or the "Places" module will mount the drive/partition when "clicked")

---

### Post by emendelson on 2009-12-17
Terrific thread. Many thanks for this lightweight system.

Quick question: after a lot of searching, I can't figure out how to turn OFF the titlebar animation - the effect that slides the titlebar up or down when switching windows. Does anyone know the way to fix this??

Thanks!

---

### Post by emendelson on 2009-12-17
Also, how do you setup a printer in this setup??

---

### Post by ciborium on 2010-01-01
I followed tutorial, and resurrected a free box that formerly ran Win98.  I love it and will probably try it on my netbook.

I have one problem though.  When I had vanilla Ubuntu on this box (it ran like molasses in Antarctica) the sound worked fine out of the box.  Now, even with all the alsa sliders up all the way, there is still no sound.  

I have done nothing else to solve the problem yet, but as this is not exactly the normal install, I wasn't sure that any of the usual published stuff would help.

I don't really care if video ever works, but I do like to listen to my favorite classical music station when I work: [http://wguc.org](http://wguc.org)

EDIT: The mixer widget volume control is upside down.  You need to slide it DOWN to increase the volume.

---

### Post by stanca on 2010-01-22
E17-Ecomorph in Ubuntu Karmic x64::popcorn:

---

### Post by Igneo676 on 2010-01-27
OpenGEU PPA was just opened today for Karmic...
...now that is pretty exciting for the world of E17 Ubuntu

---

### Post by Leighman on 2010-01-27
Where can we find it?

---

### Post by Igneo676 on 2010-01-28
[http://opengeu.intilinux.com/news](http://opengeu.intilinux.com/news)

They are waiting to offer an ISO soon but they have the news there and eventually a link to a How TO in their wiki.

Not something I have personally tried due to the fact that I JUST got a new distro on my laptop and I want the full ISO before I muddle around on my 2nd hard drive.

I'll be waiting for that ISO

---

### Post by Mttechserv on 2010-03-01
Hey folks... looking for a bit of input here. 
Really doesn't seem like there's all too many of us running E17 on Karmic.
 
I have installed from the Enlightenment repos, not from SVN. I've ran across a few issues, but nothing I couldn't solve or work around so far, with the exception of one.

For no apparent reason, on an intermittent basis, all of my icons disappear from my iBar.
All of the shortcuts still work, I get text when I mouseover them, but they have no icons. 
( When I first log in, everything is fine )
As a bonus, sometimes it's only some of the App shortcuts that are affected. ( also seemingly random )

Also, how would I set Chrome as my default browser in E17?
( I've yet to see any simple way to set a default App to perform an action )

The computer is an HP DC5100MT ( Minitower ) with an Intel GMA950 integrated video card ( and I'm curious if that might be the cause of my issues ). Sadly, no AGP port in the machine. 

Any input would be greatly appreciated.

Cheers.

---

### Post by wsonar on 2010-03-15
I've installed e17 but it's not an option how to I add it to my sessions?

---

### Post by wsonar on 2010-03-15
These instructions are incomplete

> **kappa962 said:**
> Here is my procedure for installing an Enlightenment E17 based Ubuntu. This method starts from a minimal command line install, and avoids any unnecessary Gnome baggage. It relies exclusively on the official Ubuntu and Enlightenment repos. For a less lightweight E17 that can be installed after a full Ubuntu install check [this other Howto]("http://ubuntuforums.org/showthread.php?t=1350575").)

E17 features my favorite user interface of any window manager/desktop environment. Also, E17 is very fast and responsive, and should be good for older computers. On my computer, this OS takes just over 1GB of disk space, and uses 84MB of RAM, as opposed to 4.5GB of disk space and 211MB RAM for a normal Ubuntu installation. You'll use the Alternate install CD for this installation. (The minimal or Server install CDs should work too.)

(Two other good options for E17 based Ubuntu distros are [OpenGEU]("http://opengeu.intilinux.com/Home.html") and [MoonOS]("http://www.moonos.co.cc/"). Advantages for these are live CDs, and ease of installation. Advantages for the method described in this HowTo are less baggage, more control, and a more recent Ubuntu release.)

**1.** Boot up the Alternate install CD and select "Install command-line system" from the F4 Modes menu. Go through the text-based install. This part should be fairly straightforward, and is a good way to start any lightweight Ubuntu install. (see Distrowatch.com's [minimal Xubuntu article]("http://distrowatch.com/weekly.php?issue=20090504#feature")) (Using Karmic Beta, I had to "sudo update-grub" after installing in order to get my other OSs to show up in the GRUB menu.)

**2.** Add in the Enlightenment repo. Add this to the end of your /etc/apt/sources.list```
deb http://packages.enlightenment.org/ubuntu karmic main extras
```
Then add the key:
```
wget http://packages.enlightenment.org/repo.key -O - | sudo apt-key add -

sudo apt-get update
```

**3.** Install the software:```

sudo aptitude install xorg e17 wicd lxterminal gnome-icon-theme mousepad emodule-places emodule-tclock emodule-calendar unrar rar xarchiver gpicview

sudo aptitude install firefox thunar vlc -R
```
**xorg** and **e17** are, obviously, the essential packages for this installation.
You might want to install **ecomorph-e17** instead of **e17** for the compiz eye candy.
**wicd** for network/wifi management. I would use exalt (package name:**emodule-exalt**), but I can't get it to work. At all.
**lxterminal** as a lightweight terminal program that is significantly better than xterm
**mousepad** is my choice for a full-featured, lightweight text editor. **scite** and **Leafpad** are two other options
**gnome-icon-theme** is necesary in order for the icons in the menus and in Thunar to look right.
**xarchiver** is a nice, lightweight program for working with compressed files; **rar** and **unrar** are needed for it to work properly
**gpicview** is a nice, lightweight picture viewer
**emodule-places**, **emodule-tclock**, and **emodule-calendar** are just three extra emodules that I really like to use.
The -R option is important for **Firefox**. Otherwise it installs piles and piles of gnome-related packages. Another,  more lightweight option is to [install Chromium]("http://ubuntuforums.org/showthread.php?t=1237680&highlight=chromium").
**thunar** is my choice for a full-featured, lightweight file manager
**vlc** is, of course, the standard linux media player

Modify this list to suit your needs. Other packages you might want to install:
**abiword**: lightweight word processor. It's still a pretty bulky program, so consider using the -R option with aptitude, which will cut the installed size in half.
**galculator**: basic calculator program.

**4.** Get audio working: ```
sudo nano /etc/group
``` then add your username to the audio group.
Then, ```
sudo aptitude install alsa-base alsa-oss
```

**5.** Setup SLiM, a lightweight login manager(GDM replacement):
```
wget http://us.archive.ubuntu.com/ubuntu/pool/universe/s/slim/slim_1.3.0-2_i386.deb
sudo dpkg -i slim_1.3.0-2_i386.deb
```

or for a 64-bit version:
```
wget http://us.archive.ubuntu.com/ubuntu/pool/universe/s/slim/slim_1.3.0-2_amd64.deb
sudo dpkg -i slim_1.3.0-2_amd64.deb
```

You may want to change the theme or otherwise customize the SLiM login manager. Go here for more info: [http://slim.berlios.de/](http://slim.berlios.de/)


**6.** Reboot and setup E17 as it directs you. From a terminal, run alsamixer and unmute/turn up the appropriate things

**7.** Configure E17. Here are the things I do.
[LIST]
[*]Enlightenment can have problems mounting partitions, etc. I get around this by using the Places module and modifying my PolicyKit.conf as described here: [http://code.google.com/p/e17mods/wiki/Places](http://code.google.com/p/e17mods/wiki/Places) (edit /etc/PolicyKit/PolicyKit.conf and add <match action="org.freedesktop.hal.storage.*"><match user="[your user name]"><return result="yes"/></match></match> after <define_admin_auth group="admin"/>. If the file doesn't exist, install policykit.)
[*]If you want to disable tap-to-click: [http://ubuntuforums.org/archive/index.php/t-875016.html](http://ubuntuforums.org/archive/index.php/t-875016.html)
[*]Fix all the missing icons: menu->settings->settings panel->look->icon theme, pick "gnome"
[*]You will probably want to modify the alt-tab and window focus behaviors: menu->settings->settings panel->windows->window list and window focus
[*]The edge binding settings will probably also need modification: menu->settings->settings panel->input->edge bindings
[*]If you want the mac dock-like thingy: menu->settings->shelves->add a shelf and set up its contents with only the IBar. Then, under the advanced settings, select the invisible style.
[*]Install a more interesting theme from [http://www.e17-stuff.org](http://www.e17-stuff.org) or [http://exchange.enlightenment.org/theme](http://exchange.enlightenment.org/theme) or, my favorite, [http://www1.get-e.org/Themes/E17/](http://www1.get-e.org/Themes/E17/). Apparently some older themes may not play nicely with your new E17 installation. You can mix and match functional parts of the themes if needed.
[*]I used to install usplash, but I can't get it or xsplash to work in Karmic.*
[/LIST]

This is all that I do to get my base OS installed. Let me know if there is anything else you would recommend for an E17 based system. Hopefully I can figure out how to get Entrance login manager and a splash screen working and add those things into this howto.

*I finally got usplash to work by doing [this]("http://ubuntuforums.org/showpost.php?p=8024427&postcount=17") and [this]("http://ubuntuforums.org/showthread.php?t=1283710#8"). Given the current state of usplash and xsplash, I'm going to hold off adding this into the main part of this howto until those packages have stabilized.




I could not find anything in these instructions to add e17 or ecomorph to the slim sessions any help please

---

### Post by wsonar on 2010-03-15
> **kappa962 said:**
> 


**6.** Reboot and setup E17 as it directs you. From a terminal, run alsamixer and unmute/turn up the appropriate things


I reboot but come to the slim login that does not have an entry for e17

---

### Post by wsonar on 2010-03-15
the slim documentation seems real incomplete and dosen't tell me anything

---

### Post by wsonar on 2010-03-15
lots of googling and still not able to find appropriate answer for Xubuntu slim

do I need to edit the .xinitrc file like in arch

this is real frustrating

how did anybody else follow the directions and get past this???

---

### Post by wsonar on 2010-03-15
So I installed entrance it installed no problem and had my sessions listed

---

### Post by Mttechserv on 2010-03-16
> **wsonar said:**
> So I installed entrance it installed no problem and had my sessions listed

I was about to say something about running gdmsetup to add it to GDM, but it sounds like you beat me to it.

---

### Post by forgetclosure on 2010-03-17
do you think it would be easier to use the usermod command instead to add the user to the audio group? ```
usermod -a -G audio username
```

---

### Post by Fred the Penguin on 2010-04-12
When I try to update my sources list, I get this error:

404 Not Found [IP: 53.251.179.13 80]
and the other packages were ignored.

---

### Post by Fred the Penguin on 2010-04-14
Never mind. I made a stupid mistake. Thanks for the great how-to!:)

---

### Post by davis15 on 2010-06-05
Hello, I have a  number of problems:

First, how can remove  all hard drives or partitions on the desktop without removing all the  icons?

Second: I installed lxpanel and  tint2, work but will not let me maximize windows how can I can fix this?

Third and last: I have as a file manager thunar but  when I close it throws me an error message.

---

