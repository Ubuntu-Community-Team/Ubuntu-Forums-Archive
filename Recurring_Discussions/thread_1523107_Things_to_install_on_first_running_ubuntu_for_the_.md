---
title: "Things to install on first running ubuntu for the first time"
date: 2010-07-03
forum: Recurring Discussions
---

### Post by gnarliprime on 2010-07-03
What are your normal procedures for setting up a Ubuntu desktop once it's installed?

First, of course is to get your hardware working. Which, ubuntu makes very easy(as long as you don't have a old matrox card) by downloading the proprietary drivers. System -> Administration ->Hardware Drivers

Basic Must haves for me
Gnome do (makes my life at work so much more efficient)
Chromium
OpenSSh
VNC server, or client depending on which system i'm setting up
Remmina (actually saves VNC passwords)
qbitorrent (lets face it, transmission is awful zombie process business)
mobloquer (again, depending on your situation, does nice with not  interrupting most internet usage)
filezilla
vmware client
wine (useful for those things at work that don't apply to linux users)
Startup disk manager (for those pesky dual boot configurations)
VLC
Adobe Flash
[picasa ]("http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb")(recommeded by kukker32)

-Customizing your life-
compiz settings manager(for those fancy moves)
compiz extra plugins
ubuntu tweak
themes
Move the window buttons to the top gnome panel, delete the bottom panel  and install AWN(Avant Window Manager)
[http://mobloquer.foutrelis.com/download](http://mobloquer.foutrelis.com/download)

-If you are used to using windows to stream your media to your xbox or ps3, you may want to look into Java PS3 media server. It has worked for me, however runs on java so you'll have to install the runtime environment, although I tend to stay away from Java, it was able to even simultaneous stream to both the PS3 and the 360. 

additionally, for remote computing, I've found rdesktop to be rather compelling but sincerely unstable. Maybe it's just my applications of the software.

---

### Post by kukker32 on 2010-07-03
i think you missed out the **Ubuntu restricted extras** which is what's called codecs in windows... making it possible to play more video/sound formats

in terminal
sudo apt-get install ubuntu-restricted-extras

and to play dvds
 sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by gnarliprime on 2010-07-03
Good point. I tend to keep to VLC so i forget that that would be necessary running other media players.

---

### Post by theozzlives on 2010-07-03
That may be great for you, but other people may have other needs. It depends on how your using your computer.

---

### Post by kukker32 on 2010-07-03
yea vlc can play alot..

but i was reffering to new ubuntu users.. which proberly uses rhythmbox as their media player sad...

EDIT:
and a IM program might be usefull personally i found emesene best, homever webcam function sucks in it..
[http://emesene.org/download.html](http://emesene.org/download.html)

but amsn can do that (use software center)

now we are about it libmimic is needed for webcam conversations
[http://packages.ubuntu.com/karmic/libmimic0](http://packages.ubuntu.com/karmic/libmimic0)

---

### Post by gnarliprime on 2010-07-03
> **kukker32 said:**
> yea vlc can play alot..

but i was reffering to new ubuntu users.. which proberly uses rhythmbox as their media player sad...

agreed. That's why i threw VLC as one of the things to install. I guess I was more creating this post as a question/discussion as to what everyone does upon a fresh install. I imagine that my wording was just incomplete as the previous post subtly pointed out.

---

### Post by kukker32 on 2010-07-03
but my experience with vlc (windows) is it's no more than a hall of pain to make a playlist..

but i haven't tried in ubuntu, but that might be near the same. i can't imagine there can be so much difference between them...

and what about picture editing, since gimp xxxxx...

google picassa
[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)

take it as a suggestion to this thread.... :D

---

### Post by gnarliprime on 2010-07-03
> **kukker32 said:**
> but my experience with vlc (windows) is it's no more than a hall of pain to make a playlist..

but i haven't tried in ubuntu, but that might be near the same. i can't imagine there can be so much difference between them...

touche! vlc doesnt have any fast playlist creation support besides listing what you've already created, I generally use it for playing Movies/TV off of my NAS server. VLC is nice because it has the main codecs, can mount images, and mostly has an http remote control. For Music I have been experiementing lately with banshee. 

> **kukker32 said:**
> and what about picture editing, since gimp xxxxx...

google picassa
[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)

take it as a suggestion to this thread.... :D
Good to see we're on the same page. Gimp can be wretched at times but useful when you're in a fix. I'll edit the first post to include Picasa

---

### Post by Yarui on 2010-07-03
> **gnarliprime said:**
> What are your normal procedures for setting up a Ubuntu desktop once it's installed?

First, of course is to get your hardware working. Which, ubuntu makes very easy(as long as you don't have a old matrox card) by downloading the proprietary drivers. System -> Administration ->Hardware Drivers
I don't exactly have a normal procedure for setting up Ubuntu after installation.  I always make sure to install the restricted extras package, but for the most part I just install stuff as I need it.  As far as getting the hardware working, it's also not always easy if you have a relatively new video card.  I always have a terrible time getting my ATI card working properly.  The hardware drivers tool has never worked for me, for some reason.

> **kukker32 said:**
> yea vlc can play alot..

but i was reffering to new ubuntu users.. which proberly uses rhythmbox as their media player sad...[]("http://packages.ubuntu.com/karmic/libmimic0")
I don't know what you are talking about.  rhythmbox is an excellent music player.  That's why it is bundled with Ubuntu.  There are plenty of other good ones out there, but there is nothing wrong with using rhythmbox.  I wouldn't say that it's an app that is just for new Ubuntu users.

---

### Post by philinux on 2010-07-03
Moved to Recurring Discussions.

---

### Post by gnarliprime on 2010-07-03
> **Yarui said:**
> I don't exactly have a normal procedure for setting up Ubuntu after installation.  I always make sure to install the restricted extras package, but for the most part I just install stuff as I need it.  As far as getting the hardware working, it's also not always easy if you have a relatively new video card.  I always have a terrible time getting my ATI card working properly.  The hardware drivers tool has never worked for me, for some reason.

This may be herecy but have you tried Suse? I was having a lot of problems getting Ubuntu/new Xorg without a config to recognize an old matrox dual head card on my brothers' computer correctly. However Suse found it and allowed me to configure it with no problem. I only tried KDE however.

---

### Post by Yarui on 2010-07-05
> **gnarliprime said:**
> This may be herecy but have you tried Suse? I was having a lot of problems getting Ubuntu/new Xorg without a config to recognize an old matrox dual head card on my brothers' computer correctly. However Suse found it and allowed me to configure it with no problem. I only tried KDE however.
Well, the problem I have is that it never seems to be able to do the download and activate the driver, it detects the ATI card.  I always get it set up manually, though.  I haven't tried Suse.  For some reason it's one of the few distros that has never really interested me.  I have tried out almost every other distro you could think of and am now using Ubuntu, Arch and Gentoo on 3 different machines fairly happily.

---

### Post by Chame_Wizard on 2010-07-06
1.Upgrading the package manager.
2.Adding PPA(back-ports etc etc).
3.Update the Linux kernel and GRUB(always reboot).
4.Installing necessary software and debug symbols.
The last one is customization.

:lolflag:

---

### Post by RiceMonster on 2010-07-06
> **Chame_Wizard said:**
> 1.Upgrading the package manager.
2.Adding PPA(back-ports etc etc).
3.Update the Linux kernel and GRUB(always reboot).
4.Installing necessary software and debug symbols.
The last one is customization.

:lolflag:

What's so funny?

---

### Post by sataris on 2010-07-06
1.Adding PPA(back-ports etc etc).
2.Update the Linux kernel and GRUB(always reboot).
3.Installing VLC, Google Apps (Chrome included), ubuntu-restricted-extras, hardware drivers, etc
4.Customization - I love to constantly change my desktop

I always install several themes, 10-20 wallpapers, and several other things. Love tweaking my system.

---

### Post by Chame_Wizard on 2010-07-07
> **RiceMonster said:**
> What's so funny?
You always learn something new by tweaking,which is fun to do.

Poor M$ Winlows(from XP to 7 Ultimate) die hard/power users,no real freedom is not good at all(especially with humongous options to customize/choose with GNULinux/BSD).:popcorn:

---

