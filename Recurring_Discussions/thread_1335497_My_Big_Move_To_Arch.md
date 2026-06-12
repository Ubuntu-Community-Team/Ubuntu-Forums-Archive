---
title: "My Big Move To Arch"
date: 2009-11-23
forum: Recurring Discussions
---

### Post by IgnorantGuru on 2009-11-23
I recently migrated my primary system from Kubuntu Karmic/KDE4 to Archlinux with Openbox, so I thought I would share some of my experiences with the move.  I know this is the Ubuntu forum, but I thought some Ubuntu users might want to scope this out if they're considering changing.  I have used Ubuntu for years and when I decided to go to Arch, I wondered what I was in for!  Long story short - I love it.

First, a little background...  The first linux I used seriously was SUSE, which I liked overall, but package maintenance was a PAIN (regardless of what they claim), and eventually it just started to feel too corporate and evil-empirish, like Windows.  So a few years ago I moved to Kubuntu which I really like for its apt-get of course.  But lately I've been grumbling a lot.  I don't really like KDE4 - it's way too overdone and heavy, too much of a Vista-wannabe.  I also don't like some of the decisions Ubuntu is making in general when it comes to packages, and especially the way the recent trend is to stop the user from removing some packages - too bossy lately.  There are also security issues that IMO are beginning to enter the realm of Microsoft - things which I believe are not done for the benefit of the users.  Thus I found myself having to remove and disable all kinds of junk after a fresh install.  I've also had very poor results with reporting bugs in KDE and Ubuntu lately - they just aren't addressed, and there are way too many to begin with.  The release cycle seems rushed, and quality is the loser in this.  I was fighting against the distribution too much.  That's when I began to realize it was probably time for a bigger change.  I was reluctant because hey it's a lot of work to get used to something new.  But it can also be cool, I kept telling myself, as I remembered how cool it was to lose Windows.

I ended up selecting Arch Linux because I liked a few ideas.  One, it was supposed to have a good package manager comparable to apt-get (known as pacman).  Also, I liked the rolling release idea, where instead of releases and upgrade/reinstalls, packages are just gradually updated to their latest versions every day.  The install CDs have versions, but if you're running Arch, you're running the 'NOW' release.  This is explained more here: [http://bbs.archlinux.org/viewtopic.php?id=18063](http://bbs.archlinux.org/viewtopic.php?id=18063)  Most of all, I really like that Arch uses software packages that are presented the way the original makers designed.  Mods and alterations are very minimal.  I like this because I found so many of the bugs in Ubuntu are related to changes the packagers made which broke the functionality of the original software.  Arch honors the original software rather than trying to make it fit a particular scheme - and this includes servers and daemons.  I really REALLY like this idea because as we all know having a middleman introduces problems, and original developers take the time to make their software work more carefully than packagers.

I was also a little scared of Arch because it was supposed to be more work, less noob-friendly.  I can handle some complexity, but frankly I don't enjoy having to do everything the hard way.  There is something to be said for convenience.  Plus using a mainstream distribution like Ubuntu has its advantages - lots of packages and support.  But I decided to give it an honest chance.

I also decided I was going to drop KDE.  It's only going to get more convoluted and Windows-like IMO, so I figured I might as well get on a more fitting track.  So I was also shopping for a new desktop manager.


THE RESULTS

I have had a truly excellent experience with Arch.  It is just so neat to set things up one step at a time, and I pleasantly learned more in a week about the inner workings of linux than I have in years of using Ubuntu.  I really feel like I know my system now.  It's also a simpler system, and I know what's running and why.  It's also fast as hell!  The few problems I did have, the community support and wiki were excellent - very knowledge people who like doing things themselves.  Overall, my opinion is that any reasonably experienced Ubuntu user will feel right at home.  You've probably edited a few configuration files, entered some CLI commands, and messed with the inner workings enough on occassion that you won't be lost in Arch.  And in the long run I think it's MUCH LESS of a hassle, especially because you get a better understanding.

The 64 bit install CD (I used the net install CD) was a lot like the alternate install CD for K/Ubuntu.  Same basic stuff.  The main difference is that it just installs the core system, so you boot into a shell.  Then you install Xorg, which I thought was really cool (and very easy).  I've never installed Xorg by itself like that.  Then the nvidia driver went in without trouble, also from a package.  (Interestingly, it cured a problem I had with not being able to go back to a shell once X started in Kubuntu.  Same nvidia driver, so once again it shows that the problem was in the Ubuntu package, not NVidia's driver or Xorg!)  Then you choose your desktop and install that.  Then you edit the xinitrc file to tell X to start your desktop!  It's great knowing how it all fits together.

In my case I decided to go with Openbox desktop because it seemed to allow you to build your desktop the way you want.  Openbox is very minimal at the start - you build your desktop by adding taskbars and such that you choose.  This may seem like a lot of work, but it was really neat.  I'm also running a few KDE apps that I like, and Openbox runs them with no problems.  I chose lxpanel as my taskbar - works great and has a clock, quick-start tray, system tray, and a menu that automatically updates itself when you install software.  Reminds me of KDE3.

The pacman package installer works very well.  There were only a few programs that I wanted that it didn't have: rdate, google-earth, secure-delete, and crystal-cursors.  rdate and google-earth had community-supported build packages available.  These let you build the packages easily yourself and then install them with pacman.  secure-delete I just copied the executables from my Kubuntu partition - they run fine.  (The same was true of rdate, but that I built.)  And I found crystal-cursors and compiled it.  I learned great things about X cursors, so it was well worth the hour or so I spent with it.

Everything else, including media players, editors, KDE apps, image viewers and editors, servers, and open office were in pacman packages.  Easy as using apt-get to install them.  Plus they come out exactly as the original designers had in mind, which is neat to see - same as installing them from the websites for the most part.

One difference (which I like), is that when you install a server or daemon, such as NFS, it just puts the program on your system, it doesn't configure or start it.  I never liked the way Ubuntu started things as soon as you installed them.  This way I can look over the (usually simple) installation steps and decide how I want it to work.  For example, to auto-mount a CD when I insert it, I installed the autofs daemon right from instructions on the wiki.  Works better and solved problems I had with automounting/unmounting in Ubuntu.

And instead of all the init.d and /etc/modules complexity, there is one file (/etc/rc.conf) with simple lists of modules and daemons to start at boot.  So much cleaner and easier to maintain.

My system has so much less running on it as a result - just what I need, rather than what every Ubuntu user *might* need.  Part of this is due to dropping KDE as well.  If you do want KDE, Arch is supposed to have a good implementation of it.  There is also kdemod, which is a modified version of KDE for Arch (part of the Chakra project).

As for the rolling release, I really like it thus far.  From what I've read, occassionally new package updates will break a program and you'll have to update your config files to correct it.  But these potential problems are announced on the forums, and IMO that's simpler than going through the mess of upgrades and reinstalls, where so much changes at once.  Plus, the package updates never change your config files - you do that yourself, and when using Arch you'll know how.

Aside from the apps I use, there are NO GUI 'system settings'.  I maintain everything by editing the config files.  But what I've found is that instead of finding this too messy or laborious, I like it a lot better.  The config files have everything laid out cleanly and commented, and I have access to all of it.  Whereas GUIs rarely give you complete control, and rarely work as well.  I did have to learn a bit that used to be done in a GUI, but as a result I understand things so much better, instead of feeling confused and frustrated behind the GUI.  But if you do like the 'system settings' stuff, if you can install a more bells & whistles desktop like KDE or Gnome - then you'll get some of that.  It's just not made by Arch.  They leave it up to you to decide what programs to install, REALLY.  For example, I chose my sound server (alsa - which always worked great for me and I hated the pulse junk that Ubuntu went to.  And yes, alsa can play several sounds at once - mix.)

Here are some of the wiki entries I used, more or less in the order I used them.  You can look these over to get a pretty good idea of what you'll be doing once you've used the install CD to install the core.  The wiki is THE place to go when you want to know how to install something.  You'll usually find detailed instructions that work perfectly.  Also, since everyone uses the same version of Arch (the NOW version), you don't have to wrestle with multiple sets of instructions.  I find that the first few parts of the wiki instructions is all I use - the lower parts of the pages tend to be for more complex setups.

[http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide_Appendix](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide_Appendix)
[http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)
[http://wiki.archlinux.org/index.php/NVIDIA](http://wiki.archlinux.org/index.php/NVIDIA)
[http://wiki.archlinux.org/index.php/X11_Cursors](http://wiki.archlinux.org/index.php/X11_Cursors)
[http://wiki.archlinux.org/index.php/Openbox](http://wiki.archlinux.org/index.php/Openbox)
[http://wiki.archlinux.org/index.php/CUPS](http://wiki.archlinux.org/index.php/CUPS)
[http://wiki.archlinux.org/index.php/Brother_MFC-420CN](http://wiki.archlinux.org/index.php/Brother_MFC-420CN)
[http://wiki.archlinux.org/index.php/Configuring_network](http://wiki.archlinux.org/index.php/Configuring_network)
[http://wiki.archlinux.org/index.php/IPv6_-_Disabling_the_Module](http://wiki.archlinux.org/index.php/IPv6_-_Disabling_the_Module)
[http://wiki.archlinux.org/index.php/ALSA](http://wiki.archlinux.org/index.php/ALSA)
[http://wiki.archlinux.org/index.php/HAL](http://wiki.archlinux.org/index.php/HAL)
[http://wiki.archlinux.org/index.php/Autofs](http://wiki.archlinux.org/index.php/Autofs)
[http://wiki.archlinux.org/index.php/Sane](http://wiki.archlinux.org/index.php/Sane)

And the forums are at
[http://bbs.archlinux.org/](http://bbs.archlinux.org/)

Just keep in mind that until you get X and your desktop running, you won't have a (graphical) web browser.  So if you don't have another computer nearby, you may want to print the basics first.

That may look like a lot of manual configuration, but I found it to be very smooth and also a neat experience.  I also had many fewer problems than with a typical Kubuntu install - very few in fact.  And I had my system done in a couple days (where I was using it as my primary system instead of Kubuntu which I still have on another partition), with a couple more days for spit & polish.  And that's with my being a complete noob to Arch, and also trying out some alternative software to the ones I've been using.

K/Ubuntu was actually great training for Arch, because you tend to have to do a little manual configuring to get Kubuntu running the way you want anyway, and fixing problems.  And Arch isn't for linux noobs, so I think Kubuntu still is useful.  But if you now want to try building a more custom system from the ground up, I think Arch is an excellent choice.  Overall my system is running faster and lighter, and I'm so glad to be free of KDE, while still having some of my favorite KDE apps.

And Arch still uses Grub v1!  Although you can of course change that to v2 if you prefer.

Recommendations:  I recommend keeping a backup copy of your Kubuntu home folder - you may want parts of it to look at, especially if you drop KDE but want to run KDE apps.  There's not much, but it was handy a few times.  Also, system backups are always great to have... [http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)  Plus, instead of reconfiguring many of your programs, you can just copy their settings files from your home folder.  For example, copy the ~/.mozilla folder and you won't need to set up Firefox from scratch.

I also like building my new system on a spare partition while still being able to boot my old partition.  That way when I get frustrated or tired I get boot in to 'old reliable' and relax.  I had Arch install grub to the MBR of my second drive, so it didn't interfere with the boot process.  Grub2 detected Arch and added it with update-grub.  Then when I was ready to change the boot to my Arch partition and grub, I just installed grub to the MBR of the first drive.  Pretty painless way to try a new system, and it also lets you mount and examine your old system partition as you're setting up the new one.

Below are some software recommendations I'd thought I'd throw in.  Everyone likes different things but these are what I'm using for now.  And this will give an idea of the variety of apps you can have with Openbox and without full KDE.

First, lxpanel is a great taskbar.  In fact the whole LXDE desktop is probably good, because I saw a lot of apps from it that had a nice light but capable design.

For the most part you install these just by typing 'pacman -S PACKAGENAME', and they're ready to run.

Ark
Knotes
Krusader  (capable file manager from KDE)
Dolphin   (simple file manager from KDE)
Speedcrunch  (calculator)
GQView   (like KDE Gwenview - or Arch has Gwenview as well)
GIMP
KGrab   (from KDE, for window snapshots)
XSane
Firefox
flashplugin
jre (this pacman package install the 64 bit version of Sun Java with plugins - one step!)
KMail  (still using it for now but I may look at others)
KWalletManager
Pidgin
OpenOffice
epdfview   (like Ocular - very simply and light PDF viewer)
Kate
Ghex    (Gnome's Hex Editor)
k3b     (also needs dvd+rw-tools and cdrdao)
SMPlayer/Mplayer
VLC
avidemux
Htop   (process watcher)
Konsole
autofs   (automounts CDs/DVDs, usbsticks, and even networks if you want)
ttf-ms-fonts and ttf-dejavu      (fonts)
imagemagick
libdvdcss
mpg123		(command line MP3 player)
vorbis-tools    (for ogg123 command-line player)
alsa       (for sound)

---

### Post by &#32 Greg on 2009-11-23
Well written post. Hopefully this doesn't go the way of most Arch threads.

By the way, you might want to check out yaourt. It's a pacman frontend with AUR support.

---

### Post by ZankerH on 2009-11-23
Yep, Arch is superior to Ubuntu in just about every way besides the fact that you can't install it with zero knowledge of GNU/Linux and without even looking at the documentation. Good to see more people aboard.

---

### Post by dragos240 on 2009-11-23
Yay! Good post. :) Also I second getting yaourt.

---

### Post by RiceMonster on 2009-11-23
Been using Arch since about May 2008. Most of the novelty has worn off, but I'm not making any plans to leave because I much prefer the way it handles software in general. Pacman is fantastic, ABS makes creating packages a breeze, the AUR makes it so you don't even have to create packages yourself, and  the rolling release model is good if you're impatient like me.

---

### Post by mkvnmtr on 2009-11-23
Nice post , gives me something to think about.

---

### Post by infestor on 2009-11-23
<n00b question>
in arch, can i use deb pacakges for ubuntu? for instance i want to install dropbox, can i just download karmic package and it will work? or do i have to download the source and try to compile it and pray that it will work?

---

### Post by Bachstelze on 2009-11-23
Tl;dr

---

### Post by NoaHall on 2009-11-23
Seeing as Arch isn't built on Debian, no you can't use the .deb files.

---

### Post by &#32 Greg on 2009-11-23
> **infestor said:**
> <n00b question>
in arch, can i use deb pacakges for ubuntu? for instance i want to install dropbox, can i just download karmic package and it will work? or do i have to download the source and try to compile it and pray that it will work?

Dropbox is in the AUR already- most packages are already available in either the standard repos or the AUR. Still, there's a tool called deb2targz that converts... well, take a guess.

---

### Post by IgnorantGuru on 2009-11-23
I've added yaourt to my list of things to try - thanks.  I did read that there were front-ends for pacman, and I am a Synaptic fan so maybe I will like them.  But I figured it was good to learn pacman a little first, especially because I like making little scripts to automate things.

I think Ubuntu is better for people moving from Windows, or who just aren't as interested in handling the details as much.  Arch is good if you want to build a more custom system, since it installs just the core linux system by default and easily lets you add to it - nothing to remove or hack out.  Some linux experience is necessary though - I wouldn't have wanted to go straight from Windows.

And I'm not saying one is better than the other - I was mainly just sharing some of my experience of moving FWIW to others.  I have felt a bit betrayed by Ubuntu lately, as well as KDE.  But I guess they're just moving in a direction that doesn't appeal to me.  To each his own - isn't it great we linux users have so many choices?  I'm sure Ubuntu will be a strong OS for a long time, and I'm still using it for now on a system I maintain for another user.

---

### Post by &#32 Greg on 2009-11-23
yaourt is also command line. It supports everything pacman does, and a little more.

---

### Post by Bachstelze on 2009-11-23
> **NoaHall said:**
> Seeing as Arch isn't built on Debian, no you can't use the .deb files.

.deb isn't a proprietary Debian format... You can very well compile the apt and dpkg tools on Arch if you want.

---

### Post by earthpigg on 2009-11-23
i enjoyed reading your post :D

one thing i didn't see you mention is that dotfiles from Ubuntu for firefox, pidgin, etc, are usually very forward compatible. i backed up and restored my dotfiles from /home/username/ *en masse* to the arch system, and they all worked fine. this probably would not always be the case if you tried taking up-to-date arch .dotfiles and using them on a version of Ubuntu more than 2 or 3 months old.

im going to slightly de-rail this thread and post a bit of my arch-specific .bashrc (i use yaourt for all package management - it serves perfectly well as a front-end to pacman that includes the AUR).

```
alias yu='yaourt -Syu'
alias yi='yaourt -Sy'
```

so, with that... to update my system, both things from the AUR and things from the regular repos:

```
yu
```

and, to install a package that is either in the AUR or regular repos...

```
yi packagename
```

i dont have one that clears the package cache, cuz i dont want to make it easy on myself to do something potentially bad :D

gtkpacman is great for quickly viewing and browsing packages like synaptic, but it is not as powerful. i suggest using it to look at your packages, but stick to the command line for installing, removing, etc.

and, since we both use LXDE stuff, this is what i use for editing config files...

```
alias lpad='leafpad'
alias spad='sudo leafpad'
```

so, for example, to edit the config of the ssh daemon...

```
spad /etc/ssh/sshd_config
```

or, .bashrc...

```
lpad .bashrc
```


there is a great thread over on the arch forums dedicated to custom .bashrc stuff.

---

### Post by chucky chuckaluck on 2009-11-23
> **Bachstelze said:**
> Tl;dr

don't you have threads to close?

___________

+1 for yaourt. it makes whatever it does easier for those of us who are a little sketchy on what exactly it does.

---

### Post by NoaHall on 2009-11-23
> **Bachstelze said:**
> .deb isn't a proprietary Debian format... You can very well compile the apt and dpkg tools on Arch if you want.

Sorry, what I meant is you can't directly use it from a fresh install. And it's better not to use the .deb files.

---

### Post by IgnorantGuru on 2009-11-23
> **infestor said:**
> <n00b question>
in arch, can i use deb pacakges for ubuntu? for instance i want to install dropbox, can i just download karmic package and it will work? or do i have to download the source and try to compile it and pray that it will work?

As Noahall said, Arch isn't a debian derivative.  So it's best to find the indigenous install method for a given app.  The AUR does work well.  However, for simple apps that don't have library dependencies and such (like command-line apps), I have found that I can use the executables from Ubuntu.  I just copied them from the /usr/bin folder.  This worked for the secure-delete programs and rdate.  But in general that's a poor way of doing it - I was just lazy.

And there is good app support in Arch.  I was concerned that I would miss the huge Ubuntu repos, but I really haven't had cause for concern.  I got EVERYTHING working that I wanted.

---

### Post by Bachstelze on 2009-11-23
> **chucky chuckaluck said:**
> don't you have threads to close?

Not that I know of. Anything in mind?

---

### Post by earthpigg on 2009-11-23
> **NoaHall said:**
> Sorry, what I meant is you can't directly use it from a fresh install. And it's better not to use the .deb files.

odds are, someone has already gone to the trouble of packaging it for Arch and put it in the AUR. make sure you read the comments and discussion on that particular package build, as they often contain important info that may apply to you.

example:

[http://aur.archlinux.org/packages.php?ID=15270](http://aur.archlinux.org/packages.php?ID=15270)
> 
google-earth 5.1.3509.4636-2

...

Comment by: IgnorantGuru on Fri, 20 Nov 2009 19:58:31 +0000

    I got this working on 64 bit for GoogleEarth 5.1.3533.1731 with the following changes...

    Edit PKGBUILD and add:
    arch=('x86_64')

    Also, as I write this the PKGBUILD is for GoogleEarth version 5.1.3509.4636, so I changed the md5sum in PKGBUILD from:
    'ec0491757d3627cd3981f390b093596b'
    to:
    '2d60578f4a2e56990a053faa8b30537f'

    Then it will build and install okay.

    Then add 32 bit libraries:
    pacman -S --needed lib32-qt lib32-nvidia-utils lib32-gtk2 lib32-curl lib32-glibc

    [http://wiki.archlinux.org/index.php/Using_32-bit-applications_on_Arch64](http://wiki.archlinux.org/index.php/Using_32-bit-applications_on_Arch64)

---

### Post by IgnorantGuru on 2009-11-23
> **Bachstelze said:**
> .deb isn't a proprietary Debian format... You can very well compile the apt and dpkg tools on Arch if you want.

That's interesting.  Not sure if that would be useful in general as things are in different places and the deb files contain setups for debian derivatives, but it might be helpful in some instances.

And thanks to Greg for the deb2targz name - I was wondering if there was something to let me pry open deb files.  :)  Ubuntu does have huge repos, and a 64 bit executable is a 64 bit executable.

---

### Post by infestor on 2009-11-23
> **IgnorantGuru said:**
> As Noahall said, Arch isn't a debian derivative.  So it's best to find the indigenous install method for a given app.  The AUR does work well.  However, for simple apps that don't have library dependencies and such (like command-line apps), I have found that I can use the executables from Ubuntu.  I just copied them from the /usr/bin folder.  This worked for the secure-delete programs and rdate.  But in general that's a poor way of doing it - I was just lazy.

And there is good app support in Arch.  I was concerned that I would miss the huge Ubuntu repos, but I really haven't had cause for concern.  I got EVERYTHING working that I wanted.

> **&#32 Greg said:**
> Dropbox is in the AUR already- most packages are already available in either the standard repos or the AUR. Still, there's a tool called deb2targz that converts... well, take a guess.

wow i really got pumped...but as of now i will keep away from arch...do we have smth like AUR in ubuntu?

---

### Post by &#32 Greg on 2009-11-23
> **infestor said:**
> wow i really got pumped...but as of now i will keep away from arch...do we have smth like AUR in ubuntu?

PPAs would probably be the closest thing.

---

### Post by Naiki Muliaina on 2009-11-23
> **Bachstelze said:**
> Not that I know of. Anything in mind?

Seriously for a mod of a forum like this, your attitude sucks. 

TL;DR is often seen as inflammatory in most communities. Seeing a mod do it here followed by a response like that?

---

### Post by earthpigg on 2009-11-23
> **Naiki Muliaina said:**
> Seriously for a mod of a forum like this, your attitude sucks. 

TL;DR is often seen as inflammatory in most communities. Seeing a mod do it here followed by a response like that?

this post belongs in the forum feedback subforum, not here. and consider the context, please: he is joking around a bit in the ***community cafe***, not in the actual support forums (you know, the onest hat are 10x more vital than this forum, regardless of how much time we all like to spend here. the support forums where you may have noticed: the mod in question has well over 7k posts.).

---

### Post by snowpine on 2009-11-23
5...4...3...2...

---

### Post by IgnorantGuru on 2009-11-23
> **earthpigg said:**
> i enjoyed reading your post :D

one thing i didn't see you mention is that dotfiles from Ubuntu for firefox, pidgin, etc, are usually very forward compatible. i backed up and restored my dotfiles from /home/username/ *en masse* to the arch system, and they all worked fine. this probably would not always be the case if you tried taking up-to-date arch .dotfiles and using them on a version of Ubuntu more than 2 or 3 months old.

Right you are - I didn't have to reconfigure most of my apps, I just copied the .folders over, or in the case of some KDE apps, the rc files and apps folders (from .kde/share/).  It's also handy to have a copy of your old .kde/share/config/kdeglobals to refer to.

In some cases I did set things up from scratch even though I probably didn't need to, just to avoid any hard to resolve annoyances caused by the system change.  But not much.

> im going to slightly de-rail this thread and post a bit of my arch-specific .bashrc (i use yaourt for all package management - it serves perfectly well as a front-end to pacman that includes the AUR).

Thanks for all the input!  I will definitely be looking into this.  So much to absorb right now - I haven't been a noob in awhile so it's good for me.  :)

---

### Post by IgnorantGuru on 2009-11-23
> **earthpigg said:**
> make sure you read the comments and discussion on that particular package build, as they often contain important info that may apply to you.

example:

google-earth 5.1.3509.4636-2

Boy, there's no hiding on the internets!  :)

That particular AUR was out of date with the new Google Earth.  But google earth is easy enough to install with its own installer, which I assume works on Arch.  My real issue was figuring out which libraries I needed for 64 bit.  Had that down pat in Ubuntu.  But I found it.

---

### Post by Naiki Muliaina on 2009-11-23
> **earthpigg said:**
> this post belongs in the forum feedback subforum, not here. and consider the context, please: he is joking around a bit in the ***community cafe***, not in the actual support forums (you know, the onest hat are 10x more vital than this forum, regardless of how much time we all like to spend here. the support forums where you may have noticed: the mod in question has well over 7k posts.).

Hmm well, i apologize to the mod, and anyone else who feels i am in the wrong.

I lump TL;DR in with RTFM etc. I guess i don't 'get' the community in the cafe anymore, bit to long off the forum maybe. I haven't been 'getting' the humor in the game threads and the amount of 'you fail' kinda comments. Hmmm i will be nickin off now with a tail between my legs, please be excusing me.

---

### Post by gn2 on 2009-11-23
> **chucky chuckaluck said:**
> don't you have threads to close?

> **Bachstelze said:**
> Not that I know of. Anything in mind?

This one would be a good start.

---

### Post by earthpigg on 2009-11-23
@Naiki Muliaina:

nooo! i wasn't trying to drive you away!

its an ***Arch*** thread. from a certain POV, "rtfm" and "tl;dr" are fairly ironc comments in this context. consider that the arch install guide itself is pretty dang "tldr":  [http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

he was poking fun at ***Arch***, not the OP. :D

and, imo, we should all have a sense of humor about our distro of choice...

> Ubuntu is an ancient African word that means "I cannot configure Debian."

> Fedora: A popular slang term that loosly translates as "I cannot afford RHEL."

etc. all in good fun. no one ***actually*** thinks (i hope!) that Fedora users are all poor or that no Ubuntu users are "smart" enough for Debian.

:D

---

### Post by IgnorantGuru on 2009-11-23
> **Naiki Muliaina said:**
> TL;DR is often seen as inflammatory in most communities.

FWIW it went right over my head.  I dismissed it as a drunken post or a keyboard mapping problem - didn't realize it meant anything.  :)

It was a long post, but for those thinking of trying Arch from Ubuntu I thought it might be helpful.

---

### Post by Dharmachakra on 2009-11-23
> **gn2 said:**
> This one would be a good start.

#-o

I really don't understand why you post in Arch threads...

---

### Post by NoaHall on 2009-11-23
edit: wrong thread....

---

### Post by RiceMonster on 2009-11-23
> **Dharmachakra said:**
> #-o

I really don't understand why you post in Arch threads...

No kidding.

---

### Post by earthpigg on 2009-11-23
in the Tradition of Ubuntu threads being littered with "Try Arch!" suggestions, I will bring you this:

One advantage of rolling release is bleeding-edge end-user software.

One disadvantage of rolling release is stability, because of a bleeding-edge underlying system.

...

One advantage of Ubuntu-style releases is a more stable underlying system.

One disadvantage of Ubuntu-style releases is old end-user software.



Well, what if we could combine the advantages of two while accepting very few or none of the disadvantages?

[COLOR="Red"][SIZE="3"][getdeb.net]("http://www.getdeb.net/welcome/") now has a repository![/SIZE][/COLOR]

By the time 10.04 comes out, I suspect/expect/hope that adding getdeb.net's repo will result in:

-A stable LTS underlying system that you won't need to reinstall or upgrade for three years.
-Bleeding edge userland software, such as the latest version of firefox and openoffice.
-And, ***all*** you need to do for this to happen is add the getdeb.net repo and 'sudo apt-get upgrade' once every week or two.

PERFECT! for me, at least :D

I am fairly excited about this prospect.

---

### Post by gn2 on 2009-11-23
> **Dharmachakra said:**
> #-o

I really don't understand why you post in Arch threads...

I really don't understand why it is that Arch converts feel the need to evangelise about the emperors new clothes in the Ubuntu forums and I wish they would desist.

---

### Post by earthpigg on 2009-11-23
> **gn2 said:**
> I really don't understand why it is that Arch converts feel the need to evangelise about the emperors new clothes in the Ubuntu forums and I wish they would desist.

i like and use ***both***, and i didn't interpret the OP to be evangelizing. 

i do agree with you that the meme of "Try Arch!" in random threads is annoying, but i don't think that was the case here.

---

### Post by RiceMonster on 2009-11-23
> **gn2 said:**
> I really don't understand why it is that Arch converts feel the need to evangelise about the emperors new clothes in the Ubuntu forums and I wish they would desist.

There isn't really an evangelizing going on here. What's better - constantly preaching about Arch, or constantly complaining about Arch? That's right, neither.

---

### Post by Dharmachakra on 2009-11-23
> **gn2 said:**
> I really don't understand why it is that Arch converts feel the need to evangelise about the emperors new clothes in the Ubuntu forums and I wish they would desist.

So you go out of your way to open a thread that you know is going to annoy you? Seems like you're making it a problem for yourself... might as well go beat your head up against a wall. ](*,)

---

### Post by sertse on 2009-11-23
I'll get drawn into this recurring decision, once again ;)

This is all caused by Other Os Talk closing. Before than, the Achers here would stay into their subforum, and mostly not bother others. Now, because such discussions are in Cafe, they must coexist and interact, a it's just a receipe for conflict. We are seeing the results.

It's funny by attempting to "fix" one issue, the admins unleashed a far greater disruption on the forums.

---

### Post by kevCast on 2009-11-23
> **gn2 said:**
> I really don't understand why it is that Arch converts feel the need to evangelise about the emperors new clothes in the Ubuntu forums and I wish they would desist.
[img]http://imgur.com/zxWIr.jpg[/img]

---

### Post by wojox on 2009-11-23
Tl;dr = To long : didn't read. Wow I learn't a new acronym today ( had to Google that ). 

Yeah IngnorantGuru that is a big move, Kubuntu/KDE4 to Arch/Openbox on a 64 bit system. I agree it is pretty fun configuring Arch. Seeing how things works under the hood, so to speak. That wiki is pretty sweet.

---

### Post by Raffles10 on 2009-11-23
Arch is ok if you like high maintenance operating systems. I get the feeling many people use Arch because it makes them feel clever hence the need to tell people about it. 

Arch is simple. If you want to impress people try LFS. :lol:

---

### Post by kevCast on 2009-11-23
> **Raffles10 said:**
> Arch is ok if you like high maintenance operating systems. I get the feeling many people use Arch because it makes them feel clever hence the need to tell people about it. 

Arch is simple. If you want to impress people try LFS. :lol:
Posting something like this is ok if you like inane posts. I get the feeling people post things like this because they have to justify their opinions and can't be content with choices they've made.

Posting is simple. If you want to troll people try LFS. :lol:

---

### Post by buntunub on 2009-11-23
I run Arch now on one of my machines and I love it. Its simple, very stable, screaming edge updates, and runs fast due to being slim and optimized. You learn a ton installing the system, like how bloated Ubuntu is and how much unnecessary/unneeded software drivers and other junk you get with a base Ubuntu install and how it gums down your system to a point. There is no great harm in it however, but the speed difference between a base Arch install and a base Ubuntu install is very noticeable. One could also achieve this with Ubuntu post install if you know what your doing and with some time/great effort, but thats the real difference between Ubuntu and Arch - the philosophy. One is a "one size fits all for Linux newbies" distro (Ubuntu), and the other is a mainly hobbyist only distro (Arch) for those that crave an extra 1.000000000000000099999% optimization increase out of their system. Its all personal choice and it only underscores the true beauty of Linux as a whole.

---

### Post by gn2 on 2009-11-23
Same old rubbish time after time from Archers.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by earthpigg on 2009-11-23
here, i made a thread for both the arch user haters, and the arch fanboys, among others:

[http://ubuntuforums.org/showthread.php?t=1335672](http://ubuntuforums.org/showthread.php?t=1335672)

enjoy yourselves in that thread!

:D

---

### Post by &#32 Greg on 2009-11-23
> **gn2 said:**
> This one would be a good start.

Now you're right.

---

### Post by IgnorantGuru on 2009-11-23
> **earthpigg said:**
> One advantage of rolling release is bleeding-edge end-user software.

One disadvantage of rolling release is stability, because of a bleeding-edge underlying system.

Personally, I'm not much on having the very latest.  But I also don't like dists that are slow to adopt changes and fixes like debian (reportedly).  So for me Arch seems like a good solution, in that it just stays up-to-date.  If that means reconfiguring now and then so be it.  I find I have to do that with any OS anyway, so might as well do it little by little.  Plus, I think having a good system backup helps take the fear out of that process - I can so easily roll it back, research the issue, then upgrade again.

That said, the getdeb idea sounds like a good solution for some.  I have other problems with where Ubuntu has been going though, so it's not a solution which would satisfy me personally.

> **wojox said:**
> Yeah IngnorantGuru that is a big move, Kubuntu/KDE4 to Arch/Openbox on a 64 bit system. I agree it is pretty fun configuring Arch. Seeing how things works under the hood, so to speak. That wiki is pretty sweet.

Didn't feel that big, maybe because I was trying to change K/Ubuntu more into that - it was easier just to select it from the start.

The wiki is most fine.

> **Raffles10 said:**
> Arch is ok if you like high maintenance operating systems. I get the feeling many people use Arch because it makes them feel clever hence the need to tell people about it. 

Arch is simple. If you want to impress people try LFS. :lol:

I like simple - all truly evolved systems are.  Complexity (and the resulting problems ) are usually a sign of something that could be simplified.

As for high maintenance, I wouldn't describe Arch that way, but I'm gonna find out.  Frankly, one of my reasons for trying something new was that Ubuntu was becoming hell to maintain - lots of bugs and breakage.  I don't find it stable at all, at least for my purposes.

But I'm not trying to gain converts - I don't get a kickback on Arch.  Use whatever melts your wax.

---

### Post by IgnorantGuru on 2009-11-23
> **buntunub said:**
> I run Arch now on one of my machines and I love it. Its simple, very stable, screaming edge updates, and runs fast due to being slim and optimized. You learn a ton installing the system, like how bloated Ubuntu is and how much unnecessary/unneeded software drivers and other junk you get with a base Ubuntu install and how it gums down your system to a point. There is no great harm in it however, but the speed difference between a base Arch install and a base Ubuntu install is very noticeable. One could also achieve this with Ubuntu post install if you know what your doing and with some time/great effort, but thats the real difference between Ubuntu and Arch - the philosophy. One is a "one size fits all for Linux newbies" distro (Ubuntu), and the other is a mainly hobbyist only distro (Arch) for those that crave an extra 1.000000000000000099999% optimization increase out of their system. Its all personal choice and it only underscores the true beauty of Linux as a whole.

Very well said.

---

### Post by kevCast on 2009-11-23
> **gn2 said:**
> Same old rubbish time after time from Archers.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Not the same.

---

### Post by user1397 on 2009-11-23
/tryingtobefunnybutprollyfailingandoffendingalotofpeople

(Setting: Dating Show)

Host (the girl): "Suitor number 1, if you could describe yourself in two words, what would they be?"

Suitor #2: "Funky and sexy."

Host: "How about you suitor number 2?"

Suitor #2: "A Grade-A Badass!"

Host: "How about you suitor number 3?"

Suitor #3: "Hmm, well uh if you had to call me one thing it would probably be arch user...hmm...yup! That's what it would be, arch user!

/theend

---

### Post by Yes on 2009-11-23
> **gn2 said:**
> Same old rubbish time after time from Archers.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's not the same.

And please don't group us all together, very few Archers evangelize about it.

---

### Post by gn2 on 2009-11-23
> **kevCast said:**
> Not the same.

Thankfully.

---

### Post by RiceMonster on 2009-11-23
> **gn2 said:**
> Thankfully.

*sigh*

---

### Post by kevCast on 2009-11-23
> **gn2 said:**
> Thankfully.
Why are you so hostile toward Arch?

---

### Post by ~sHyLoCk~ on 2009-11-23
Man that is one huge essay. Can anyone summarize what the OP is trying to say? 
I'm guessing: He heard about Arch, tried it and now using it coz he thinks it's the operating system of God? Hmm sounds about right..;)

---

### Post by jaxxstorm on 2009-11-23
I recently tried Arch, it lasted about 2 days on my machine. Why?

Well, installing software from AUR is a **nightmare**, even with yaourt. Its basically compiling everything from source. It takes HOURS. I finally lost patience when I had to wait 45 minutes to install Kompozer. 
Installing from pacmans is quick and excellent, the problem is that the number of packages in the arch repos is very minimal. So you have to revert to AUR, and compiling everything. It was like running Gentoo all over again.

---

### Post by mdshann on 2009-11-23
> **gn2 said:**
> I really don't understand why it is that Arch converts feel the need to evangelise about the emperors new clothes in the Ubuntu forums and I wish they would desist.

This is the Community Cafe!

> 
The Community Chat area is for lighthearted and enjoyable discussions, like you might find around a water cooler at work.

Almost any non-tech-support topic may be discussed here. Discussions on religion and politics are not allowed, except for politics directly related to free and open source issues. Any topic or discussion that causes problems or drama will be closed. This area is intended for fun and community building, not arguments. Please take those elsewhere. Thanks!


It's meant for exactly this sort of discussion! Please refrain from trying to cause problems or drama as some of us actually want to talk about the differences between using Arch and Ubuntu! Btw, I don't use arch and I still find your comments annoying and I wish you would "desist"!

---

### Post by IgnorantGuru on 2009-11-23
I guess I'm naive, but I didn't realize this would be so contentious.  The way I look at it, Ubuntu users can also be Arch users, and it's nice to know how to work from one to the other.

FWIW, I still think highly of Ubuntu in many ways.  I will always fondly remember my 'Ubuntu days', unlike Windows where I felt like GOOD RIDDANCE!  It's not like that.  I learned a heck of lot on Ubuntu and I'm very thankful for it.  That's why I feel comfortable trying Arch now.

My suggestion: try some alternatives.  It's good for you.  You might just end up coming back to Ubuntu, and feeling a little more comfortable with your choice.  Then you won't open the 'My Big Arch Move' threads, or at least not so resentfully.  Or, you might find yourself wandering further from home, and building a new one.  You never know.  Either way, you'll learn something and it's worth the effort.  Linux users are by nature explorers - don't fight your nature.

---

### Post by mdshann on 2009-11-23
> **jaxxstorm said:**
> I recently tried Arch, it lasted about 2 days on my machine.

Gentoo takes AGES longer than Arch, but you do have a valid point. That's one of the issues though when you want to run a distro with a rolling release. In order to get the bleeding edge stuff you generally need to compile it and configure it on your own as most distros like Ubuntu that are not on a rolling release put a lot more into testing the packages and making them idiot proof to keep them as stable and as accessible to the masses as possible.

I had arch on my laptop for a while, it wasn't a big deal to get installed and working. The big deal for me was having to manually configure all of the stuff that is usually done for me in Ubuntu, such as menus, network management, etc. Not really because I didn't want to, I just needed my laptop working the way I needed quicker than I was able to with arch. That said when I get home tonight I am going to begin installing arch on my Desktop machine, along side my Windows 7 install.

Biggest reason I chose ubuntu for my laptop was I need it working correctly for work without spending hours configuring. Reason I am choosing arch for my desktop is because the only other thing I use it for is gaming, and I want to learn more about Linux and how a system fits together than I have in my 3-4 years of using Ubuntu (started with 5.10).

EDIT:

> **IgnorantGuru said:**
> I guess I'm naive, but I didn't realize this would be so contentious.  The way I look at it, Ubuntu users can also be Arch users, and it's nice to know how to work from one to the other.

FWIW, I still think highly of Ubuntu in many ways.  I will always fondly remember my 'Ubuntu days', unlike Windows where I felt like GOOD RIDDANCE!  It's not like that.  I learned a heck of lot on Ubuntu and I'm very thankful for it.  That's why I feel comfortable trying Arch now.

My suggestion: try some alternatives.  It's good for you.  You might just end up coming back to Ubuntu, and feeling a little more comfortable with your choice.  Then you won't open the 'My Big Arch Move' threads, or at least not so resentfully.  Or, you might find yourself wandering further from home, and building a new one.  You never know.  Either way, you'll learn something and it's worth the effort.  Linux users are by nature explorers - don't fight your nature.

I agree with this completely. I use Linux and Windows and I even have a Mac! I say, why limit yourself to one operating system? Learn as much as you can! Especially in my case being in the IT/Computer Repair field it makes you infinitely more valuable as an employing if you can use and repair 3 different O/S's and 2 different hardware platforms! And to be truthful, I honestly like parts of all three types of O/S. They are all good for different people and uses.

---

### Post by ~sHyLoCk~ on 2009-11-23
> **mdshann said:**
> Gentoo takes AGES longer than Arch, but you do have a valid point. **That's one of the issues though when you want to run a distro with a rolling release.** In order to get the bleeding edge stuff you generally need to compile it and configure it on your own as most distros like Ubuntu that are not on a rolling release put a lot more into testing the packages and making them idiot proof to keep them as stable and as accessible to the masses as possible.

Configure it..yes. Compile it..no. Try sidux or Debian sid.

---

### Post by mdshann on 2009-11-23
> **~sHyLoCk~ said:**
> Configure it..yes. Compile it..no. Try sidux or Debian sid.

I didn't realize there was such a thing. Thank you for pointing that out. I may try sidux here in fact I have started the download to give the live CD a whirl on my desktop. 

> That's one of the issues though when you want to run a distro with a rolling release. ...that compiles from source is more what I was meaning but I neglected to say that because tbh I didn't realize there were any that were binary distributions. My life has changed now thanks to your post lol. :D

I think I will tri-boot my desktop with arch, Win7, and sidux if all goes well!

---

### Post by ~sHyLoCk~ on 2009-11-23
Well I think there are more like: Foresight Linux, PCLinuxOS,etc.

---

### Post by IgnorantGuru on 2009-11-23
> **mdshann said:**
> Gentoo takes AGES longer than Arch, but you do have a valid point. That's one of the issues though when you want to run a distro with a rolling release. In order to get the bleeding edge stuff you generally need to compile it and configure it on your own as most distros like Ubuntu that are not on a rolling release put a lot more into testing the packages and making them idiot proof to keep them as stable and as accessible to the masses as possible.

I didn't really find much need to compile much in Arch, but maybe that's because of my particular software.  In fact I only complied three very little things, one of which I always had to compile for Ubuntu as well.  If the Arch distros weren't as complete as they are (for me), I probably couldn't bear to use it either.  But it's also a growing OS and community.

As far as idiot proof and stable packages, I know that is the philosophy of Ubuntu, but I think it has been drifting.  I was getting very frustrated with the bugs and lack of prompt updates to fix them, and from what I see on the forums I'm far from alone in this.  Keep in mind that Windows is 'stable' (in it's own way) and 'accessible to the masses'.  That doesn't mean it's a pleasure to use and not frustrating.  I hope Ubuntu doesn't go that way, but I see some signs of it.  I guess it's a hard balance to achieve.  Arch is certainly not a replacement for Ubuntu overall - they serve different purposes.

I installed a net install of Arch, which means most of it is downloaded from the latest versions, rather than the CD.  All of those packages were thus 'rolling', yet they're all working together flawlessly, and stayed that way after I did another upgrade yesterday, which included Xorg and NVidia.  They must be rolling something right.  And that's with a system that uses a mixture of Openbox, KDE, and Gnome.  So I think the idea that it's some wildly unstable environment where everything has to be compiled is a bit off.  At least in my experience.

---

### Post by earthpigg on 2009-11-23
> I guess I'm naive, but I didn't realize this would be so contentious. The way I look at it, Ubuntu users can also be Arch users, and it's nice to know how to work from one to the other.

i am both, at the same time :D

primary desktop, Arch. rest, Ubuntu-based.

---

### Post by Rainstride on 2009-11-23
> **bachstelze said:**
> tl;dr

+1

---

### Post by chucky chuckaluck on 2009-11-23
> **Raffles10 said:**
> Arch is ok if you like high maintenance operating systems. I get the feeling many people use Arch because it makes them feel clever hence the need to tell people about it.
 
i'm sure every distro has its own share of cleverness. i think calling arch, generally, high maintenance is pretty inaccurate. with less installed, there is less to go wrong. 

> Arch is simple.

make up your mind, sport.

---

### Post by Raffles10 on 2009-11-24
> **chucky chuckaluck said:**
> i'm sure every distro has its own share of cleverness. i think calling arch, generally, high maintenance is pretty inaccurate. with less installed, there is less to go wrong. 



make up your mind, sport.

Simple to install, high maintenance if you want to keep it.

Arch is community maintained, how many Archers have the testing repo' enabled ? Not many, packages get released with the minimum of testing or without even any at all. It doesn't matter how much you have installed, breakages are inevitable, did you enjoy the recent Xorg update ? Nvidia users had a whale of a time. :p

Here we are again discussing Arch at UF, some people might think the most logical place to discuss it would be the Arch forum. ;)

---

### Post by Raffles10 on 2009-11-24
> **kevCast said:**
> Posting something like this is ok if you like inane posts. I get the feeling people post things like this because they have to justify their opinions and can't be content with choices they've made.

Posting is simple. If you want to troll people try LFS. :lol:

People post things like this because they get fed up with seeing Arch stuff in Ubuntu Forums.

I would guess you're an Arch user, are you impressed with yourself ? Should we be impressed with you ? Is the reason you're trolling here because at the Arch forums you feel rather insignificant ?

Have you tried installing LFS ? Maybe if you did they'd be impressed with you at the Arch forums. ;)

---

### Post by kevCast on 2009-11-24
> **Raffles10 said:**
> People post things like this because they get fed up with seeing Arch stuff in Ubuntu Forums.

I would guess you're an Arch user, are you impressed with yourself ? Should we be impressed with you ? Is the reason you're trolling here because at the Arch forums you feel rather insignificant ?

Have you tried installing LFS ? Maybe if you did they'd be impressed with you at the Arch forums. ;)
Slackware and Ubuntu on the majority of my machines, thank you. Arch is a nice distribution as well.

My agitation with you is that you are have this idea I want you to be impressed with me. I can't speak for anyone else, so I won't. If you feel like your impressed/intimidated by someone who uses a distribution different than your own, perhaps you have bigger problems than analyzing the motives of every poster who has some praise for some distribution you supposedly don't care about.

It's a free internet, though. Do as you please.

---

### Post by ~sHyLoCk~ on 2009-11-24
Apparently installing LFS earns respect. You learn new things every day.:popcorn:

---

### Post by BenAshton24 on 2009-11-24
You have inspired me to give it a try :D

I've just finished getting X configured and am in the process of setting up gnome :)

---

### Post by bailout on 2009-11-24
Another thread tempting me to spend time trying Arch ;) I keep thinking of trying it on my netbook as iirc there is a comprehensive guide to installing it on my model and a netbook would benefit from a minimal system.

Does the Arch package manager pull in dependencies or does that have to be sorted manually?

To the op, Does the lxpanel allow autohide yet?

---

### Post by Pogeymanz on 2009-11-24
> **bailout said:**
> 
Does the Arch package manager pull in dependencies or does that have to be sorted manually?


The Arch package manager is actually better at dependencies than apt-get ever was for me in Ubuntu.

Give it a try when you have an afternoon free to figure it out. The first time can be a little challenging, but it's a great distro with the best of all worlds, in my opinion.

Please don't be driven away by the hostility towards it on these forums. It's unwarranted and very immature.

---

### Post by gn2 on 2009-11-24
> **kevCast said:**
> Why are you so hostile toward Arch?

I'm not, it's a fine distro for those people whose needs it meets.

---

### Post by RaZe42 on 2009-11-24
Yes, as you've proven several times in this thread, you seem to have something against Arch itself, not the "evangelizing users".

---

### Post by gn2 on 2009-11-24
When there is an Arch forum, why do Arch users feel the need to discuss their chosen distribution here?
Why is it that when Other OS closed, everyone else took the hint?
It is the abuse of the Ubuntu Forums by Arch users which bothers me.

---

### Post by fromthehill on 2009-11-24
testing arch right now
It is a lot harder to install compared to ubuntu
I tried a couple of distro's (fedora, suze) but they just didn't do it for me.
arch linux feels a lot more familiar to me as an ubuntu user. don't know why.

maybe I'll make the switch:popcorn:

---

### Post by Arup on 2009-11-24
> **gn2 said:**
> When there is an Arch forum, why do Arch users feel the need to discuss their chosen distribution here?
Why is it that when Other OS closed, everyone else took the hint?
It is the abuse of the Ubuntu Forums by Arch users which bothers me.

Hear hear hear hear raised to the power nth..............:D

---

### Post by RiceMonster on 2009-11-24
> **gn2 said:**
> When there is an Arch forum, why do Arch users feel the need to discuss their chosen distribution here?
Why is it that when Other OS closed, everyone else took the hint?
It is the abuse of the Ubuntu Forums by Arch users which bothers me.

You make this way more overblown than it is. People discuss other distros here too. Why don't you complain when people make threads about Fedora or SuSE? Don't say there isn't, because there has been threads about both of them, and there was a bunch of threads about the Fedora 12 release.

I come on here because there's more people here and I want to talk about Linux. I have an account on the Arch forums as well, and I do use it, though I mainly go on there to find solutions to problems because the chat sections are very slow moving.

However, I'm not going to say there's no "problem" at all. I read a post in one of the other threads saying people have made support threads for Arch here. Now THAT is ridiculous.

---

### Post by Arup on 2009-11-24
Of course, one is to discuss constructively, other is to blatantly put down the very distro this forum is about, freely spread FUD, curse Ubuntu, make silly comparisons, put down its developers, its policies, belittle its users, thats all fair game for these frustrated other distro users. They got their own forum, let em hang out there. Maybe its a lonely place out there.

---

### Post by RiceMonster on 2009-11-24
> **Arup said:**
> Of course, one is to discuss constructively, other is to blatantly put down the very distro this forum is about, freely spread FUD, curse Ubuntu, make silly comparisons, put down its developers, its policies, belittle its users, thats all fair game for these frustrated other distro users. They go their own forum, let em hang out there. Maybe its a lonely place out there.

I don't come here to do that, but any explanation will likely go in one ear and out the other. Feel free to think that if you want.

---

### Post by Arup on 2009-11-24
> **RiceMonster said:**
> I don't come here to do that, but any explanation will likely go in one ear and out the other. Feel free to think that if you want.

RM,

Why do you think I am accusing you? It wasn't addressed to you but somehow you took it upon yourself.

---

### Post by RiceMonster on 2009-11-24
Ok, my apologies then. Your post came directly after mine, so I thought it was a response to mine.

---

### Post by handy on 2009-11-24
**To the OP:** Here are a some links to info' that is well worth knowing about with Arch.  Once known there will be very few circumstances where you upgrade into trouble (which I have found to be incredibly rare on my Arch install that dates back to March 2008 ), the trouble when it does come, usually comes down from upstream & the fixes come pretty fast:

[http://www.ostalk.org/showthread.php?tid=78](http://www.ostalk.org/showthread.php?tid=78)

[http://www.ostalk.org/showthread.php?tid=79](http://www.ostalk.org/showthread.php?tid=79)

[http://www.ostalk.org/showthread.php?tid=428](http://www.ostalk.org/showthread.php?tid=428)

These are just handy helpers, so to speak: :)

[http://www.ostalk.org/showthread.php?tid=390](http://www.ostalk.org/showthread.php?tid=390)

[http://www.ostalk.org/showthread.php?tid=376](http://www.ostalk.org/showthread.php?tid=376)


I learned ages ago to just put gn2 in my ignore list, after which I don't have to keep on reading the same arguments coming out of his chauvinistic mind every time there is an Arch thread here in the wonderful Ubuntu forums.

Pollution control is up to us. :)

---

### Post by Pogeymanz on 2009-11-24
> **Arup said:**
> Of course, one is to discuss constructively, other is to blatantly put down the very distro this forum is about, freely spread FUD, curse Ubuntu, make silly comparisons, put down its developers, its policies, belittle its users, thats all fair game for these frustrated other distro users. They got their own forum, let em hang out there. Maybe its a lonely place out there.

Sure. But the same thing is happening against Arch. This is the community cafe and we are free to discuss anything within the rules. I'm not going to copy/paste quotes here because it would take up too much space, but Arch users are constantly belittled and attacked. Not to mention all the FUD spread by people who made it through the installation just to prove a point. Reporting these users does nothing because half the mods are in on it too and are incapable of objectively enforcing the rules.

I thought about leaving the Ubuntu Forums because of this, but then I'd be letting people like gn2 win, so I'll stick around and hopefully people will learn to ignore posts like his and continue an Arch thread as though every other post isn't crap.

gn2, 
I apologize for singling you out, I'm not only upset with you. You just happen to appear in every Arch thread I read, so I assume you wont take it personally that I happened to notice.

---

### Post by snowpine on 2009-11-24
> **Raffles10 said:**
> Arch is community maintained, how many Archers have the testing repo' enabled ? Not many, packages get released with the minimum of testing or without even any at all. It doesn't matter how much you have installed, breakages are inevitable, did you enjoy the recent Xorg update ? Nvidia users had a whale of a time. :p

This is a common misconception. Arch is not randomly pushing unstable "testing" applications onto its users. Most packages in Arch are the current "stable" upstream version.

As an example, just because there are not millions of Arch users testing the latest Firefox, does not mean Firefox is not well tested.

Also for what it's worth, moving from Ubuntu 9.04 to 9.10 broke Xorg for me. Arch does not have a monopoly on Xorg issues. :)

---

### Post by Arup on 2009-11-24
I dont see any Ubuntu users spreading FUD at Arch forum, calling it slow, useless, putting down its users and developers but I see that frequently happening here. Anyone has any issues, right away Arch fanatics come and give advice, use Arch, its better, its faster. 

Its Community Cafe in Ubuntu forum, discuss, yes, don't peddle it, if its good or better or best, people will go there automatically. No need to do it at cost of others.

---

### Post by snowpine on 2009-11-24
> **gn2 said:**
> When there is an Arch forum, why do Arch users feel the need to discuss their chosen distribution here?

The same reason people "feel the need to discuss" their jobs, pets, favorite TV show, or how to count to 200. There is more to life than just Ubuntu.

> **gn2 said:**
> It is the abuse of the Ubuntu Forums by Arch users which bothers me.

Please feel free to report any of my posts in this thread if you feel they are "abusive" of the forum rules; otherwise why don't you leave the moderating to the moderators? (I have not reported your post, as I believe you're entitled to your opinion.)

---

### Post by handy on 2009-11-24
The problems that some people are having here have nothing to do with Arch or Ubuntu.

The problems are due to the human weakness of mind that allows us to so easily be chauvinistic.

Chauvinism continually looks for a venue to express itself.

Just like smoking, drinking, anger, jealousy, lust, ... chauvinism is just another addiction to be overcome.

---

### Post by chucky chuckaluck on 2009-11-24
> **handy said:**
> The problems that some people are having here have nothing to do with Arch or Ubuntu.

The problems are due to the human weakness of mind that allows us to so easily be chauvinistic.

Chauvinism continually looks for a venue to express itself.

Just like smoking, drinking, anger, jealousy, lust, ... chauvinism is just another addiction to be overcome.

ah, chauvinism, the great killer of puppies, kittens and children's laughter...

---

### Post by handy on 2009-11-24
> **chucky chuckaluck said:**
> ah, chauvinism, the great killer of puppies, kittens and children's laughter...

Too serious huh!?

---

### Post by chucky chuckaluck on 2009-11-24
> **handy said:**
> Too serious huh!?

oh no, i was just cautioning the others.

---

### Post by bruno9779 on 2009-11-24
I thought about trying Arch out for a while now, I was just looking for a post like this.

ctrl+D

---

### Post by Grifulkin on 2009-11-24
As far as I'm concerned Arch is superior.  I started with Ubuntu and now almost use Arch exclusively.  The only ubuntu-based distro I use is Crunchbang on my old laptop.  Which by the way has 2 hard drives, the one with crunchbang and the one with Arch.  The one with Arch gets used a lot more.  

I am very thankful for Ubuntu to bring me to linux and I like that I have found a Distro that I really truly enjoy, Arch.  Is that such a terrible thing?  And I still love these forums, I learned a lot here in the support forums.  But now I just hang out in the community cafe although, I don't post a whole lot I am still always around.

And another thing, I will be honest I feel more accomplished setting up Arch on my desktop then I was the first time I dual booted Jaunty and XP.  Now it is Arch and XP and I know more about my computer than I ever did.  If that makes me a snob because I think that Arch is better so be it, I know what I like and if people want to talk about Arch on these forums let them.  The fact of the matter is, you can't have discussions like this on the Arch Forums, that being said I am not even a member on those forums.  These forums are where it's at, so just avoid the Arch threads if you are so bothered by them.

---

### Post by Pasdar on 2009-11-24
Arch seems to be the number one place most Ubuntu users migrate to.

---

### Post by Arup on 2009-11-24
I have absolutely no issues as long as they don't come to a newbie asking for help with an Ubuntu issue and tell that person to use Arch because its superior to Ubuntu,its there I draw a line. Its like I go to Arch forum and every person having an issue there, I tell them use sidux, its far better and quicker which in reality it is and its easier to install as well. Now would that be fair, I don't think so.

I see the Arch word uttered countless times at threads where people are having issues with Ubuntu. Does that seem appropriate, I truly don't think so.

---

### Post by Grifulkin on 2009-11-24
> **Pasdar said:**
> Arch seems to be the number one place most Ubuntu users migrate to.

I have noticed this too.  I do eventually want to give Gentoo a try, or some other distro, like CRUX.  When classes finally end for the semester I will try to install something on my laptop, I am a distro hopper at heart.

---

### Post by mivo on 2009-11-24
> **Arup said:**
> Of course, one is to discuss constructively, other is to blatantly put down the very distro this forum is about, freely spread FUD, [...]

Sounds an awful lot like many of your posts and gn2's. I get it, though, the agenda here is to start a flame war in every Arch thread to get it closed. It is your posts that cause aggression and a negative atmosphere. Unlike posts about other distros, this type of behaviour actually is against the forum rules.

The OP's post was perfectly constructive, as was this thread, until gn2 and you came out of the woodwork, trolling yet another thread. Great community ...

---

### Post by chucky chuckaluck on 2009-11-24
> **Arup said:**
> I have absolutely no issues as long as they don't come to a newbie asking for help with an Ubuntu issue and tell that person to use Arch because its superior to Ubuntu,its there I draw a line. Its like I go to Arch forum and every person having an issue there, I tell them use sidux, its far better and quicker which in reality it is and its easier to install as well. Now would that be fair, I don't think so.

I see the Arch word uttered countless times at threads where people are having issues with Ubuntu. Does that seem appropriate, I truly don't think so.

i pretty much agree with you, here. it's on a par with all the winbloze/window$ nonsense.

---

### Post by earthpigg on 2009-11-24
> **bailout said:**
> Another thread tempting me to spend time trying Arch ;) I keep thinking of trying it on my netbook as iirc there is a comprehensive guide to installing it on my model and a netbook would benefit from a minimal system.

Does the Arch package manager pull in dependencies or does that have to be sorted manually?

have an external keyboard around for the netbook -- you will be doing lots of typing initially.

> To the op, Does the lxpanel allow autohide yet?

im not the OP, but i do use lxde on arch... yes, it has autohide.

---

### Post by gn2 on 2009-11-24
> **mivo said:**
> ~ this type of behaviour actually is against the forum rules. ~

Strange then that I have received no infractions for any posts I have made in connection with Arch.

Feel free to report any/all my posts concerning Arch if you wish. :)

---

### Post by mivo on 2009-11-24
> **gn2 said:**
> Strange then that I have received no infractions for any posts I have made in connection with Arch. Feel free to report any/all my posts concerning Arch if you wish. :)

So you are trolling until you get an infraction? ;) Well, I don't report people for stuff like that. Name-calling, yes, but I limit it to that. I don't moderate these forums and I can handle disagreement without running to mommy.

I have never seen a constructive post by you in any Arch-related thread. It was ironic to see that you claim Arch (Linux) topics are off-topic here, yet you started a poll because you wanted a politics section here. That seemed a tad hypocritical. Don't get me wrong, I don't dislike or disrespect you. I just don't see the point of the snide remarks that you leave in Arch threads. I don't read threads about topics that don't interest and don't concern me.

People discuss Arch, Fedora, SUSE, etc. here because they are part of the community. I doubt I'm the only one who uses Ubuntu and Arch, on different machines. Or more than one distro in general. I don't make Arch threads, or ask support questions here, but I see little harm in the former. A thread like this is more on-topic (in regard to Linux) than most of the threads in the Cáfe.

Is the strong opposition an expression of fear that people may abandon Ubuntu for Arch? That would be unnecessary. If people look for, or switch to, another distro, it is because their current distro lacks something that they feel is desirable to them. Also, trying different distros improves a user's overall Linux knowledge and competence, and I think the community can only benefit from that.

Arch taught me more about Linux than Ubuntu did (but Ubuntu made the Linux entry easier than any other distro would have), which in turn enabled me to help others better with Linux questions. Using Arch didn't make me an expert, I'm far from that, and it certainly doesn't make me a "better" user. What it did is broaden my knowledge and introduce me to additional concepts and more variety. I see no harm in that.

---

### Post by gn2 on 2009-11-24
> **mivo said:**
> ~ It was ironic to see that you claim Arch (Linux) topics are off-topic here, yet you started a poll because you wanted a politics section here. That seemed a tad hypocritical. ~

If you look at how I voted in my poll and the reply I made to a post in the thread, your view may change about why I created the poll.

The problem I have with Arch users posting about Arch here is that it seems to me to be contrary to what was intended in the announcement made when the other OS talk area was closed.

It's just my opinion and I am thus far free to express it, however I feel my point has been made and undertake as of now never again to enter into any discourse on the topic of Arch Linux in the Ubuntu forums.

---

### Post by chucky chuckaluck on 2009-11-24
> **gn2 said:**
> The problem I have with Arch users posting about Arch here is that it seems to me to be contrary to what was intended in the announcement made when the other OS talk area was closed.

the reason stated was that the other OS talk forum was taking up too much space and required moderation. something had to go, and as uf is a forum for ubuntu and there are forums for other distros, it made sense to ditch it. uf didn't suddenly become the psychotic girlfriend who can't tolerate her little users even mentioning another distro. i always thought it was one of the bigger positives that uf had a forum especially for talk of other distros. i was sorry to see it go, but i understood their reasoning. as you can see from reading many of the threads here, talk of other distros is not at all discouraged, even that of the raving zealot variety (something which is not peculiar to arch).

---

### Post by SuperSonic4 on 2009-11-24
> **chucky chuckaluck said:**
> the reason stated was that the other OS talk forum was taking up too much space and required moderation. something had to go, and as uf is a forum for ubuntu and there are forums for other distros, it made sense to ditch it. uf didn't suddenly become the psychotic girlfriend who can't tolerate her little users even mentioning another distro. i always thought it was one of the bigger positives that uf had a forum especially for talk of other distros. i was sorry to see it go, but i understood their reasoning. as you can see from reading many of the threads here, talk of other distros is not at all discouraged, even that of the raving zealot variety (something which is not peculiar to arch).

+1 that's what I recall it being too.

I've been using arch since about March now and there have been a few problems but I keep coming back to it mainly because it's rolling release and pacman. I don't enable [testing] because this is my production machine and arch has been very stable for me. Compared to Kubuntu I've found it requires less maintenance. A periodic pacman -Syu every now and again and the system is up to date. It doesn't matter if I reinstall from 2009-02 or 2009-08.

Plus arch trusts me with the root account by default, sudo gets very annoying if you want to do lots of things as root

---

### Post by BenAshton24 on 2009-11-24
My arch install went great, everything is set up and working. I'm going to stay with Ubuntu for now, but I think that I'll be switching to arch when Lucid is released :D

(No I'm not posting this to make a jab at Ubuntu, I think that it is a fantastic distribution and has worked brilliantly for me, for years. I'm simply replying to offer thanks to the OP for inspiring me to try Arch).

---

### Post by handy on 2009-11-25
> **mivo said:**
> Sounds an awful lot like many of your posts and gn2's. I get it, though, the agenda here is to start a flame war in every Arch thread to get it closed. It is your posts that cause aggression and a negative atmosphere. Unlike posts about other distros, this type of behaviour actually is against the forum rules.

The OP's post was perfectly constructive, as was this thread, until gn2 and you came out of the woodwork, trolling yet another thread. Great community ...

The easy way to eliminate the repetitious negative input of people in this forum, is to add them to your "ignore list", which you will find in your user control panel.

I have only done it to 2 people in 4 years; gn2 being one of them.

He is the only Arch hound I have stopped.  Arup hasn't quite crossed the same threshold as far as I am personally concerned, but if he or anyone else does, then I will just add them to my ignore list, then I don't have to read the same things that they have to say over & over again.  

Easy! :)

---

### Post by handy on 2009-11-25
[quote=gn2]
Strange then that I have received no infractions for any posts I have made in connection with Arch. Feel free to report any/all my posts concerning Arch if you wish. [/quote]

It would seem that WE, the Arch users are far more tolerant of those particular holes that were made just before the b-holes, such as you.  

We aren't complaining about your consistent, repetitious, groundless, small minded & miserable moaning, regarding the Ubuntu/Arch people who have the hide to not just actually mention another distro on the Ubuntu forums, but to discuss it, as they see fit. (Oh! My god, freedom of speech, here?  That's outlandish, quick! Squash it? Now!?)

Some of us ignore you literally (like myself, using the User CP) others just ignore you & laugh at or curse you; some actually engage you...?  

They are usually the ones that haven't seen your posts enough yet, to just naturally find a way to ignore you.

If gn2, you can't find a way to get the Ubuntu forum administrators to ban talk about Arch, then I suggest you ignore us altogether, just as more & more of the Ubuntu/Arch users are learning to ignore you.

It may be as close as we can get to a win win situation.

---

### Post by Tibuda on 2009-11-25
So this is the discussion about discussions we were [discussing in the other discussion]("http://ubuntuforums.org/showthread.php?t=1335672")?

---

### Post by bruno9779 on 2009-11-25
> **Pasdar said:**
> Arch seems to be the number one place most Ubuntu users migrate to.

I have also thought of Gentoo as my next step in linux, but Arch just seems better.

---

### Post by Flag on 2009-11-25
Running Arch and Ubuntu 9.10. Arch took me a bit longer the first time I installed it as it was new to me. The second time it was much quicker, not that I needed to re-install, but just to get the hang of it. If you know what you need, the installation of anything is absolutely no problem. It' stable, updates are as stable as Ubuntu's updates, if something goes wrong it's fixed within a couple of days, which I can't say of Ubuntu ( rember PA forced on us ?):D

---

### Post by handy on 2009-11-25
> **bruno9779 said:**
> I have also thought of Gentoo as my next step in linux, but Arch just seems better.

Arch is easier; it will take you less time to install, & to come to grips with than Gentoo.  

Though that doesn't mean that Arch is better.  

It does in my opinion mean that Arch is probably the best next step on your way to being a Gentoo user, if that is where you are heading.

There is a tip or two on the topic here if you are interested:

[http://www.ostalk.org/showthread.php?tid=81](http://www.ostalk.org/showthread.php?tid=81)

---

### Post by Arup on 2009-11-25
> **mivo said:**
> Sounds an awful lot like many of your posts and gn2's. I get it, though, the agenda here is to start a flame war in every Arch thread to get it closed. It is your posts that cause aggression and a negative atmosphere. Unlike posts about other distros, this type of behaviour actually is against the forum rules.

The OP's post was perfectly constructive, as was this thread, until gn2 and you came out of the woodwork, trolling yet another thread. Great community ...

And so do you, bashing Ubuntu every chance you get, be it the Cafe or any other thread where anyone seems to be having some or other issue with Ubuntu in general. Don't go suggesting Arch to a Ubuntu user unless and until he or she specifically asks for an option. Last time I checked, this is still an Ubuntu forum and therefore peddling your favorite distro, bashing Ubuntu, bad mouthing the developers are all against the rules as well and you seem to be a champion of it. There won't be any flames if your don't mention Arch to a Ubuntu user, plain and simple. Cafe is fine. You are the biggest closeted example of a troll as you frequent Ubuntu forum just to bad mouth the distro and then pick an issue if anyone opposes you. If you so hate Ubuntu, they do you hang out here, this is prime example of a diabolical hypocrite. You are on my ignore list and have been reported as well.

---

### Post by Arup on 2009-11-25
> **chucky chuckaluck said:**
> i pretty much agree with you, here. it's on a par with all the winbloze/window$ nonsense.

Thank you.

---

### Post by Arup on 2009-11-25
> **handy said:**
>   Arup hasn't quite crossed the same threshold as far as I am personally concerned, but if he or anyone else does, then I will just add them to my ignore list, then I don't have to read the same things that they have to say over & over again.  

Easy! :)

Thank you, and in the same breath, I will do the same if you cross the threshold of becoming a Arch fanatic nuisance going over to each and every Ubuntu post and calling it slow and recommending Arch install for speed. ;)

---

### Post by RiceMonster on 2009-11-25
> **Arup said:**
> Thank you, and in the same breath, I will do the same if you cross the threshold of becoming a Arch fanatic nuisance going over to each and every Ubuntu post and calling it slow and recommending Arch install for speed. ;)

I'm going to honest, I get annoyed when people who use Arch or Gentoo or something call anything that uses >500 KB ram slow and bloated. Actually, I don't like the term bloated at all, because people throw it around so much.

That's a whole 'nother story though.

---

### Post by Arup on 2009-11-25
In this day of Quad and Octo Cores, 8-16GB RAM, bloated is but a misnomer. If my PC can't run HD vids, its useless for me. Even laptops are sporting quad cores now with 4GB RAM and for those who are on older machines, some real decent offerings like DSL, Puppy and to an extent Xubuntu is there. Recommending Arch, Gentoo, Slackware and even sidux, however good they maybe to a Linux newbie would surely doom desktop Linux forever.

---

### Post by mivo on 2009-11-25
> **Arup said:**
> If you so hate Ubuntu, they do you hang out here, this is prime example of a diabolical hypocrite. You are on my ignore list and have been reported as well.

I guess I hit a sensitive spot. You have been trolling various threads, and never muss a chance to call people, who find any other distro to be faster, victims of a placebo effect. You have been turning on many people who reported about problems, and frequently ridiculed them, denying and excusing any sort of issues.

I use Ubuntu on one of my machines, and have done so for years, so the claim that I "so hate Ubuntu" is quite nonsensical, as I wouldn't spend time here if I didn't use the distro. I also would not have bought Ubuntu merchandise or continue to do so. This doesn't stop me from voicing criticism where it is appropriate, and that has nothing to do with what other distros or OSes I use. I call people on FUD, as I value factual and intelligent discussion, not zealotry. The latter has been a problem in some parts of the Linux community, and for a while now in the Ubuntu community as well. It damages Linux's reputation much more than you may think.

Do have fun reporting everyone who disagrees with your opinion. The mods here are, thankfully, more open-minded. What a boring world it would be if everyone shared the same opinion. I would say "what a sad world it would be if everyone tried to silence those of different opinion", but this unfortunately does happen frequently. Plenty of examples.

---

### Post by chucky chuckaluck on 2009-11-25
> **handy said:**
> We aren't complaining about your consistent, repetitious, groundless, small minded & miserable moaning, 

haha! too bad there's no money in poetry. this line alone could make you rich.

---

### Post by Arup on 2009-11-25
> **mivo said:**
> I guess I hit a sensitive spot. You have been trolling various threads, and never muss a chance to call people, who find any other distro to be faster, victims of a placebo effect. You have been turning on many people who reported about problems, and frequently ridiculed them, denying and excusing any sort of issues.

I use Ubuntu on one of my machines, and have done so for years, so the claim that I "so hate Ubuntu" is quite nonsensical, as I wouldn't spend time here if I didn't use the distro. I also would not have bought Ubuntu merchandise or continue to do so. This doesn't stop me from voicing criticism where it is appropriate, and that has nothing to do with what other distros or OSes I use. I call people on FUD, as I value factual and intelligent discussion, not zealotry. The latter has been a problem in some parts of the Linux community, and for a while now in the Ubuntu community as well. It damages Linux's reputation much more than you may think.

Do have fun reporting everyone who disagrees with your opinion. The mods here are, thankfully, more open-minded. What a boring world it would be if everyone shared the same opinion. I would say "what a sad world it would be if everyone tried to silence those of different opinion", but this unfortunately does happen frequently. Plenty of examples.

Nope I just exposed you for the troll that you are, you use your alleged install of Ubuntu as an excuse to bash it every opportunity you get, plain and simple. You don't criticize, you spread FUD based on your placebo experience of the so called faster distros, plain and simple. You know what, its fine as this forum tolerates that sort of nonsense. Go and try peddling your OS in a Win7 or Mac OS forum and see how the egg hits your face. You bash Ubuntu in each and every post, as long as they are using any other distro but Ubuntu, you are fine. Just don't mention the U word and accolades like bloated, slow etc. flow freely like venom from your mouth. What you do is total dis-service, not only to Ubuntu users but to general potential LINUX desktop users as well. When anyone comes across with an issue, what do you and your types do? You steer them to another distro which is so hard to install and equally harder to run that it will forever turn off a potential Linux user for good. Do all of us a favor, stop lying that you use Ubuntu just to justify your presence here at the forum, if you were a true user, it would be constructive criticism and lets not talk about speed, in every tests done, the so called bloated Ubuntu has matched or come close and even bettered the so called faster distros, Spare the nonsense and FUD for a change.

Intellectual and zealotry, you are an anathema to the first and a perfect example of the later. All you do is spread confusion and nothing else. You are actually doing Windows a huge favor and maybe go on the payroll of MS, I am sure they will be interested in your covert tactics.

---

### Post by mivo on 2009-11-25
> **Arup said:**
> ... emotional attacks and baseless accusations here ...

More insults and more personal attacks. Perhaps you should step away from the computer for a bit and chill. You seem rather irrational right now. You said you "ignored and reported" me. I'm sure you did the latter, but apparently not the former since you keep talking to me. Well, not talking, but rather exposing me to attacks and what starts to look like harassment.

It isn't unusual for trolls and zealots to call those who have other opinions "trolls". You have done this before and to others, and yet you jump into threads about Arch and Gentoo, insult people, accuse them of being dishonest or somehow confused about their experiences, and attack any sort of criticism.

I think I fed you enough attention, though, and it seems to encourage you to get worse. Go ahead and have the final word.

Edit: I see you edited your post and removed some of the attacks and insults. Plenty left, though.

---

### Post by Arup on 2009-11-25
You know, go back and check your posts, the world 'troll' was coined by you and now when the medicine is administered back to you in full dose, you don't like it. Take a chil pill yourself.

Of course when relevant benchmarks are pointed out, its accusation. So I expose the so called myths and FUD as well as placebos concerning the so called speedy distro, thats a bad thing to do I guess as then it shows their theories in poor light.

I didn't remove anything in the post, rather I added it. You should truly and honestly stop trolling here at Ubuntu forums and don't fake yourself as a Ubuntu user, most of us can clearly see through your facade.

Now for all them try my speedo distro ubuntu is bloated posters. Here is something interesting. For every nonsense threads you will post about your arch(aic) distro or ricer distro being superior, here is what I will do. I will counter peddle it with the real true speedy distro which sadly gets little or no attention. That distro is the true champion called sidux based on debian sid. This is a fine example of a real true hardcore distro which isn't hard to install and is friendlier than so called speedy distros and yet beats them in terms of all out performance. Ironically one never sees the sidux users trolling around in Ubuntu forums telling people to use sidux instead. Maybe they are the ones who are truly enjoying their superior and faster distro. 

Not only that, I will go to Arch and Gentoo forums and just like the Arch and Gentoo trolls here, will tell everyone having issues there, try sidux or Ubuntu and make your life better than using these two mediocre, unfriendly and real abjured distros that takes us back to the dark early days of desktop Linux.

---

### Post by KiwiNZ on 2009-11-25
@ mivo and arup take it elsewhare

Thread closed for cool off

---

