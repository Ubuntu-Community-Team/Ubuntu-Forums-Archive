---
title: "ubuntu minimal install vs arch"
date: 2010-02-11
forum: Recurring Discussions
---

### Post by bobin on 2010-02-11
1.I was wondering WHY arch is so fast?
2.Can the minimal install + Xorg + Some other useful stuff be as fast as arch?
3.If yes please tell me the light weight equivalents to what Iam using right now.
4.I ONLY have a wireless connection. Is it likely to be a problem? (In jaunty it works out-of-the-box)

---

### Post by bobin on 2010-02-11
I have 1gb of ram + a basic 512mb GPU. I know i don't need a very light weight system but its just fun. Besides compiz and emerald is a must.

---

### Post by falconindy on 2010-02-11
> 1.I was wondering WHY arch is so fast?
2.Can the minimal install + Xorg + Some other useful stuff be as fast as arch?
Arch is only as fast or slow as the user makes it. I don't know what's included on the minimal install, but Ubuntu would likely be similar in speed if you used the minimal install disc and cherry picked your packages (skipping meta pkgs like ubuntu-desktop).

> 3.If yes please tell me the light weight equivalents to what Iam using right now.
Not if you don't tell us what you're using.

> 4.I ONLY have a wireless connection. Is it likely to be a problem? (In jaunty it works out-of-the-box)
Since by definition you build Arch up from a terminal with only a few dozen packages installed, it's not really possible to say it works 'out of the box'. If you run WPA encryption (rather than WEP), you'll need the wpa_supplicant package, and you'll likely want a daemon sucd as netcfg or wicd to handle connecting. Arch won't set it up for you, though. It will never hold your hand.

---

### Post by bobin on 2010-02-11
equivalents for nautilus, firefox, gnome, all the defaults in ubuntu. 
P.s is compiz going to run with XDfce or something similar?

---

### Post by jason.blier on 2010-02-11
To help answer your questions:

I run both ubuntu and arch

1. The base install (no gui, no services, etc) of arch and ubuntu are very similar in terms of size and speed.  Similarly, if you loaded up an arch system with the same packages and services as a stock ubuntu installation, arch would be just as "slow" as ubuntu.

2. In short, yes - but it is the goal of arch to be modular by design - right down to the selection of packages.  On ubuntu, apt does not (to my knowledge) let you choose packages interactively from a meta-group.  So, on arch, if you tell pacmam to install "gnome", it will then ask you if you would like to install the entire group or select individual packages from the group.  I have not found this feature on apt - if you tell apt to install "gnome-core", you are getting ALL of gnome-core.

3. What apps are you using?  If you look at the archwiki and search for "lightweight applications", they have a good list of programs that you could use.  You could then search for these programs in the ubuntu/debian repos with apt/aptitude and install on your ubuntu system.

4. I think that your wireless connection should be handled by the ubuntu installer - if I remember correctly, you can choose to enable the proper installer modules and firmware for wireless cards - but I have not used a wireless card in awhile, so you may want to double check that.


Having said all that, it is my opinion that building a minimal system with ubuntu is pointless.  I have ubuntu installed on my machine along with arch - but I just remove the high-level apps that I dont need in ubuntu - I dont bother going "under the hood" because when *I* look at, I see a big mess.  Arch, by design, is simple under the hood.  The package manager allows a great deal of control. config files are easy to understand and use.  Building a custom system from a base install is what arch was built for and you can accomplish that goal much faster and easier than you can in ubuntu.

Don't get me wrong - I like ubuntu and use the distro to check out cool stuff like notify-osd, pulseaudio, upstart, etc.  I also like to see the progress in the patches that may be in arch once the upstream developers adopt them.

Hope this helps/helped you in some way :)

-J

This is all my opinion and may be based on erronious information.  IF there is a way to interactively use apt from the command line to select individual packages from a meta-group on the fly, someon feel free to correct me.

---

### Post by jason.blier on 2010-02-11
> **bobin said:**
> equivalents for nautilus, firefox, gnome, all the defaults in ubuntu. 
P.s is compiz going to run with XDfce or something similar?

Ok, I'm confused - Are you looking to run ubuntu minimal and build a system or are you looking to move from ubuntu to arch??

---

### Post by bobin on 2010-02-11
I am not looking to move to arch (Mainly because I don't think I'll be able to set it up correctly). default ubuntu comes with a LOT of stuff I don't ever use like Xsane, bluetooth, games,  Fspot, totem, etc. Ok I could remove it from the default install, but I think (correct me if i am wrong) not having something is better than having it and then removing it. Then again I feel nautilus is also rather bulky.

---

### Post by snowpine on 2010-02-11
You could try one of the lightweight Ubuntu remixes. (CrunchBang is my favorite.) That would save you a lot of time over a minimal install at this stage in your Linux career.

---

### Post by bobin on 2010-02-11
> **jason.blier said:**
> 
Having said all that, it is my opinion that building a minimal system with ubuntu is pointless.  I have ubuntu installed on my machine along with arch - but I just remove the high-level apps that I dont need in ubuntu - I dont bother going "under the hood" because when *I* look at, I see a big mess.  Arch, by design, is simple under the hood.  The package manager allows a great deal of control. config files are easy to understand and use.  Building a custom system from a base install is what arch was built for and you can accomplish that goal much faster and easier than you can in ubuntu.



You think I'll be able to handle Arch ? I am a somewhat lay user with absolutely no knowledge of config files and limited experiance with the terminal.

---

### Post by bobin on 2010-02-11
> **snowpine said:**
> You could try one of the lightweight Ubuntu remixes. (CrunchBang is my favorite.) That would save you a lot of time over a minimal install at this stage in your Linux career.

"CrunchBang Linux is not recommended for anyone needing a stable system or anyone who is not comfortable running into occasional, even frequent breakage. CrunchBang Linux could possibly make your computer go CRUNCH! BANG!"

How serious is this? Also I have heard PCmanfm is rather unstable???

---

### Post by snowpine on 2010-02-11
> **bobin said:**
> You think I'll be able to handle Arch ? I am a somewhat lay user with absolutely no knowledge of config files and limited experiance with the terminal.

Arch and Ubuntu Minimal are of equal difficulty (in my opinion). The question is, are you willing to learn? Either option requires researching and troubleshooting config files and terminal commands. If you don't want to learn all that stuff, go for one of the Ubuntu remixes; basically these are someone else's minimal install that they decided to share with the world.

And yes, you should expect your first few attempts to go CRUNCH! BANG!! Don't install Arch/Ubuntu Minimal as your only operating system on your only computer two days before finals. ;) Consider using VirtualBox, a spare computer, and/or a dual boot until you are comfortable with the results.

ps pcmanfm works okay for me, but of course nothing is stopping you from using the file manager of your choice. :)

---

### Post by mörgæs on 2010-02-11
If you want to play with a minimal Ubuntu:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by jason.blier on 2010-02-11
> **bobin said:**
> You think I'll be able to handle Arch ? I am a somewhat lay user with absolutely no knowledge of config files and limited experiance with the terminal.

Well,

I dont want to discourage you, but at this point, I would start reading the archwiki and learn about:

pacman - how it works, how to use it (it is pretty easy once you learn the commands.

arch beginners guide - very good info in here, read it many times over

maybe check the forums and search for installation issued with wireless cards - almost EVERYTHING that could go wrong has been posted on the forums and/or included in the wiki.

get used to using a command line editor such as vi, vim, joe, or nano (I prefer nano - it is pretty easy for first time users and is well rounded)  your ubuntu installation should have this installed - read the nano man pages.

do some reading on the basics of using the terminal (how to kill a process, background a command, using su or sudo, etc.

Then, once you are relitavley comfortable with the command line, you can give it a shot and I am sure that you will do fine.

For the time being,

*Crunchbang is a good choice if you want a slimmer ubuntu install.
Arch has a few derivatives that you may want to try:
*Archbang is a crunchbang "clone" "basically arch with openbox and a few tools and apps installed.
*Chakra is a KDE environment based on arch with a giu frontend for pacman and a few giu tools for configuration - it is still in alpha stage and may be buggy.
*larch is an arch live cd with a gui and some apps installed.

if you go to the arch website, you can search for these in the wiki and forums and find links to download the iso files.

The nice thing is that you could use larch and fart around with it to get you comfortable before you decide to take the plunge.

A word of warning about the arch forums - make sure that you search both the archwiki and forums before posting a question or problem - chances are that it has been discussed already and ,while the forums are very helpful, most *common* problems have been covered over and over and you may get the "Use the search" or "This is in the Wiki" response if you fail to try and find the solution on your own first.

Just so you feel better - even when I was starting out with arch, I NEVER had to post a question to the forums - everything was in the wiki or had been previously covered.

Hopefully my verbal torrent is useful for you :)

---

### Post by snowpine on 2010-02-11
Whether it's Arch or Ubuntu Minimal, this easy 3-step process has never failed me:

1. MAKE A LIST of what I need on my finished installation
2. RESEARCH AND UNDERSTAND how to achieve every item on the list. Print out (or bookmark on a second computer) detailed instructions.
3. EXECUTE the plan! using the resource materials collected in step 2

YOU CAN DO IT! if you set aside a weekend for the project and patiently follow the instructions step by step.

[http://wiki.archlinux.org/index.php/Beginners%27_Guide](http://wiki.archlinux.org/index.php/Beginners%27_Guide)

---

### Post by jason.blier on 2010-02-11
> **snowpine said:**
> Whether it's Arch or Ubuntu Minimal, this easy 3-step process has never failed me:

1. MAKE A LIST of what I need on my finished installation
2. RESEARCH AND UNDERSTAND how to achieve every item on the list. Print out (or bookmark on a second computer) detailed instructions.
3. EXECUTE the plan! using the resource materials collected in step 2

YOU CAN DO IT! if you set aside a weekend for the project and patiently follow the instructions step by step.

[http://wiki.archlinux.org/index.php/Beginners%27_Guide](http://wiki.archlinux.org/index.php/Beginners%27_Guide)

^ Can't say it any better than that!  Best advice right there.

---

### Post by jason.blier on 2010-02-11
> **bobin said:**
> You think I'll be able to handle Arch ? I am a somewhat lay user with absolutely no knowledge of config files and limited experiance with the terminal.

Tell you what,

If/when you decide to try arch, feel free to email me anytime with any questions or problems.  I will do my best to point you in the right direction or help walk you through things if you are completely lost.

[email]jason.blier@gmail.com[/email]

---

### Post by MisfitI38 on 2010-02-11
Good luck with whatever you choose. I'd be interested to hear your conclusions.
Have fun.

---

### Post by k3lt01 on 2010-02-11
> **mörgæs said:**
> If you want to play with a minimal Ubuntu:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)+1 to both of these links. The thread started by the shiv is updated regular by community members and Psychocats tutorial gives you a complete step by step to get Ubuntu to an absolute minimum usable stage. From there you choose in Synaptic what programs you want.

---

### Post by Tibuda on 2010-02-11
You don't get the main ArchLinux advantage with Minibuntu: the rolling-release updates.

---

### Post by k3lt01 on 2010-02-11
> **danielrmt said:**
> You don't get the main ArchLinux advantage with Minibuntu: the rolling-release updates.Um of course you wont get Arch updates if you use a minimum Ubuntu but you will get Ubuntu updates.

---

### Post by Tibuda on 2010-02-11
> **k3lt01 said:**
> Um of course you wont get Arch updates if you use a minimum Ubuntu but you will get Ubuntu updates.

Missed the point.

---

### Post by k3lt01 on 2010-02-11
> **danielrmt said:**
> Missed the point. There is no Arch advantage in this regard you still get Ubuntu updates with a minimum Ubuntu install and choosing the right applications.

---

### Post by MisfitI38 on 2010-02-11
> **k3lt01 said:**
> There is no Arch advantage in this regard you still get Ubuntu updates with a minimum Ubuntu install and choosing the right applications.

No, you really are missing the point.

---

### Post by k3lt01 on 2010-02-11
> **MisfitI38 said:**
> No, you really are missing the point.Well why don't you teach an old dog som new tricks and lets see.

---

### Post by ~sHyLoCk~ on 2010-02-11
> **k3lt01 said:**
> Um of course you wont get Arch updates if you use a minimum Ubuntu but you will get Ubuntu updates.

rolling release oooboontoo updates? :O

---

### Post by k3lt01 on 2010-02-11
> **~sHyLoCk~ said:**
> rolling release oooboontoo updates? :OBackports and Proposed repositories. I would consider those 2 options rolling releases as they are capable of keeping a system at the same level of the next release.

---

### Post by falconindy on 2010-02-11
No. Backports are proposed repos are **not** the same as a rolling release distro. While you **could** go and hunt down the latest and greatest on your own via PPAs, it's a royal pain in the butt compared to getting the same releases (with QA included) through your official update pipeline. 

Karmic won't officially get kernel 2.6.32 (soon to be .33), KDE 4.4, OpenOffice 3.2, Firefox 3.6, udev 150+, libpng14, libjpeg8... The list goes on. Arch already has all these.

---

### Post by bobin on 2010-02-12
OP speaks: So finally made a decision . Ubuntu minimal + lubuntu desktop - lxpanel + gnome-panel + autologin + jockey + nvidia-drivers + compiz + wine + OOo
What do you think ?


Is audacious good? Or will i have to hunt for something else? Mplayer vs Vlc ? Which is lighter and/or better


> **k3lt01 said:**
> Backports and Proposed repositories. I would consider those 2 options rolling releases as they are capable of keeping a system at the same level of the next release.

How stable is this going to be?

---

### Post by ~sHyLoCk~ on 2010-02-12
bobin

Audacious is good, but why not go super light? MPD+ncmpcpp ?My favorite :D

I use smplayer, but that's not light, pulls in qt and a few kde stuffs, so does vlc I believe. Maybe totem with all the codecs?

---

### Post by k3lt01 on 2010-02-12
> **bobin said:**
> How stable is this going to be?If you want stable go for an LTS release. Something like 8.04-4 (the latest version of) Hardy Heron. Then when April comes you could update to 10.04 Lucid Lynx which is the nest LTS.

If you want apps at the level of the next release then certainly use Backports, I wouldn't do it though as you may as well use the next release. If you want to use Proposed then it is something you use at your own risk.

---

### Post by mörgæs on 2010-02-12
10.04 (alpha) is available now. The regular installation is at
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

and the minimal is at 
[http://cdimages.ubuntu.com/netboot/lucid/](http://cdimages.ubuntu.com/netboot/lucid/)

---

### Post by k3lt01 on 2010-02-12
> **mörgæs said:**
> 10.04 (alpha) is available now. The regular installation is at
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

and the minimal is at 
[http://cdimages.ubuntu.com/netboot/lucid/](http://cdimages.ubuntu.com/netboot/lucid/)Not sure I'd be attempting to use an Alpha release if I was just considering a mini install. I have used both and while Lucid is unusually stable for an alpha its mini install doesn't seem to work the same way previous minis did.

---

### Post by Tibuda on 2010-02-12
> **k3lt01 said:**
> Backports and Proposed repositories. I would consider those 2 options rolling releases as they are capable of keeping a system at the same level of the next release.

No, they are not at the same level. In theory they are, but not in practice.

It is possible to be "rolling release" on ubuntu only if you upgrade to the next alpha release when it is available. I did it on the past.

---

### Post by snowpine on 2010-02-12
Rolling release is dandy and all for the right user, but I'm not sure it is the OP's goal... Bobin, I would stick with 9.10 (the current stable release) if I were you, **without** any proposed, experimental, or 3rd party repositories (unless you absolutely need something, for example, you can't do your job without the latest OpenOffice).

---

### Post by nothingspecial on 2010-02-12
> **bobin said:**
> OP speaks: So finally made a decision . Ubuntu minimal + lubuntu desktop - lxpanel + gnome-panel + autologin + jockey + nvidia-drivers + compiz + wine + OOo


If you install lubuntu-desktop your going to get a whole bunch of stuff you may or may not want```


Dependencies: 
0.7.1 - abiword (0 (null)) alsa-base (0 (null)) alsa-utils (0 (null)) anacron (0 (null)) aqualung (0 (null)) bluetooth (0 (null)) cheese (0 (null)) cron (0 (null)) dbus-x11 (0 (null)) desktop-file-utils (0 (null)) evince (0 (null)) firefox (0 (null)) galculator (0 (null)) gdm (0 (null)) gksu (0 (null)) gnash (0 (null)) gnome-bluetooth (0 (null)) gnome-power-manager (0 (null)) gnome-system-tools (0 (null)) gnumeric (0 (null)) gpicview (0 (null)) gstreamer0.10-plugins-base (0 (null)) gstreamer0.10-plugins-good (0 (null)) gstreamer0.10-pulseaudio (0 (null)) gstreamer0.10-x (0 (null)) language-pack-en (0 (null)) leafpad (0 (null)) logrotate (0 (null)) lxappearance (0 (null)) lxde-core (0 (null)) lxde-icon-theme (0 (null)) lxinput (0 (null)) lxrandr (0 (null)) lxsession-edit (0 (null)) lxshortcut (0 (null)) lxterminal (0 (null)) mtpaint (0 (null)) obconf (0 (null)) pidgin (0 (null)) ppp (0 (null)) pyneighborhood (0 (null)) sylpheed (0 (null)) synaptic (0 (null)) transmission (0 (null)) wicd (0 (null)) wireless-tools (0 (null)) wpasupplicant (0 (null)) wvdial (0 (null)) x11-utils (0 (null)) xarchiver (0 (null)) xchat (0 (null)) xfburn (0 (null)) xorg (0 (null)) xscreensaver (0 (null)) xserver-xorg-input-all (0 (null)) xserver-xorg-input-evtouch (0 (null)) mplayer (0 (null)) powernowd (0 (null)) smplayer (0 (null))
```

If you truly want to build this from the ground up don`t install meta-packages.

Make sure you install the wireless stuff in the installer or it won`t work if you don`t have a wired connection.

To start with I always install xinit wicd ncurses-bin ncurses-base.

How light do you want to go, gui light or command line light?

---

### Post by nothingspecial on 2010-02-12
Ps

I understand why this thread has been placed here but it might be better off in desktop environments as the op want help installing a minimal system.

But your probably right, the title is asking for trouble :)

---

### Post by k3lt01 on 2010-02-12
> **nothingspecial said:**
> If you install lubuntu-desktop your going to get a whole bunch of stuff you may or may not want

If you truly want to build this from the ground up don`t install meta-packages.I agree that's why I and others pointed him to a couple of other places to read up on. This is a timely reminder.

> **nothingspecial said:**
> Make sure you install the wireless stuff in the installer or it won`t work if you don`t have a wired connection.

To start with I always install xinit wicd ncurses-bin ncurses-base.I'm not saying he shouldn't install Wicd but personally I think its a mistake. To often I help people who have removed NM and installed Wicd only to be even more disappointed cause they can't get NM back again after working out Wicd is worse for them and have to do a complete reinstall.

---

### Post by nothingspecial on 2010-02-12
> **k3lt01 said:**
> 

I'm not saying he shouldn't install Wicd but personally I think its a mistake. .

As long as he has a fairly normal wireless card wicd is preferable because it is run as a daemon and starts on boot.

You can config it very simply without X by using wicd-curses (hence installing ncurses) in a gui like way (think cmus or other curses based console apps)

That or a crash course in editing /etc/network/interfaces

Don`t forget, if he goes minimal he won`t even have X and it might be nice to have wireless working while he get`s his system right, especially with a gui like curses wireless config.

---

### Post by k3lt01 on 2010-02-12
> **nothingspecial said:**
> Don`t forget, if he goes minimal he won`t even have X and it might be nice to have wireless working while he get`s his system right, especially with a gui like curses wireless config.In my case I just used a wired setup until I got my wireless working. If he, like I do, sets up his system via a mini install following Psychocats he will have synaptic very early one and then installing NM is a straight forward process. This is just my preferred method.

---

### Post by RedSquirrel on 2010-02-12
> **k3lt01 said:**
> Not sure I'd be attempting to use an Alpha release if I was just considering a mini install. I have used both and while Lucid is unusually stable for an alpha its mini install doesn't seem to work the same way previous minis did.
Can you elaborate? How does it differ from previous mini install CDs?

---

### Post by k3lt01 on 2010-02-12
Previous mini install cds just setup a CLI system that I then apt-get"ed" only the software I wanted. The Lucid mini cd setup a cli system and then downloaded 670 odd mb of Ubuntu Desktop and installed it.

---

### Post by chucky chuckaluck on 2010-02-12
i tried the ubuntu mini.iso recently and found myself pretty lost (where's the documentation? i couldn't find it). 
aren't there underlying differences in structure that could still account for a difference in speed ( not too mention a variety of more important considerations)?

---

### Post by RedSquirrel on 2010-02-12
> **k3lt01 said:**
> Previous mini install cds just setup a CLI system that I then apt-get"ed" only the software I wanted. The Lucid mini cd setup a cli system and then downloaded 670 odd mb of Ubuntu Desktop and installed it.

Thanks for the info. There was a similar bug with Karmic's mini CD. The installer pulled in openoffice.org. :rolleyes:


@chucky:

Basic info here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This tutorial provides one way to set things up:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by chucky chuckaluck on 2010-02-12
thanks, red. i'll probably give that a whirl the next time i get stuck in arch (every once in a while, i hit something i can't solve and come screaming back to baboontu).

---

### Post by RedSquirrel on 2010-02-12
> **chucky chuckaluck said:**
> thanks, red. i'll probably give that a whirl the next time i get stuck in arch (every once in a while, i hit something i can't solve and come screaming back to baboontu).

baboontu?! Just what we need -- yet another Ubuntu derivative. :P

---

### Post by k3lt01 on 2010-02-13
> **RedSquirrel said:**
> Thanks for the info. There was a similar bug with Karmic's mini CD. The installer pulled in openoffice.org. :rolleyes:
 I had no problem with Karmic's mini.iso for me it worked as it should have. I might do a little searching about that now to see what I can find out. Thanks for the tip.

---

### Post by RedSquirrel on 2010-02-13
> **k3lt01 said:**
> I had no problem with Karmic's mini.iso for me it worked as it should have. I might do a little searching about that now to see what I can find out. Thanks for the tip.

Here's the bug report for the Karmic issue:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/443167](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/443167)

(I haven't tried Karmic's mini installer since October. Back then, it was pulling in openoffice.org.)


I had a quick look on launchpad last night for a report regarding the issue you mentioned but I didn't see anything. My search was somewhat superficial, however. I might try the Lucid mini install today to see if the issue still exists.

---

### Post by k3lt01 on 2010-02-13
Interesting, the bug seems to be a bit bigger now. I just wonder if they tested the mini.iso before they released it.

---

### Post by Dj Melik on 2010-02-14
> **bobin said:**
> You think I'll be able to handle Arch ? I am a somewhat lay user with absolutely no knowledge of config files and limited experiance with the terminal.
You're going to need a great deal of bash experience for Arch. 

Although, I suppose if you're good at following instructions; take a look at the Arch Wiki and follow the instructions. Do NOT skip steps, follow exactly.

Theres probably nothing lighter than my Arch; 
[http://omploader.org/vM2pyag](http://omploader.org/vM2pyag)

125 megabytes of RAM with Xorg/Pidgin/Firefox/Thunar running :)

---

### Post by docus on 2010-02-14
> **Dj Melik said:**
> You're going to need a great deal of bash experience for Arch. <SNIP>

I hope you don't feel I'm taking your words out of context, but I don't have "a great deal of bash experience" and I managed to get Arch up and running by following the AMAZING beginners' guide.  True, it took a while but I learnt a lot from it and now I have a light and fast Arch/Openbox system with everything I need and nothing I don't.

I'm not being an Arch fanboy, I'm just trying to demystify it a little.

---

### Post by nothingspecial on 2010-02-14
There`s not alot of difference really.

---

### Post by Dj Melik on 2010-02-14
> **docus said:**
> I hope you don't feel I'm taking your words out of context, but I don't have "a great deal of bash experience" and I managed to get Arch up and running by following the AMAZING beginners' guide.  True, it took a while but I learnt a lot from it and now I have a light and fast Arch/Openbox system with everything I need and nothing I don't.

I'm not being an Arch fanboy, I'm just trying to demystify it a little.
Well I covered that in the rest of my post.

And compared to many other distros, you're going to need a lot 'great deal' of bash experience. To get most of it up and running, you're going to need to edit lots of config files, and run many commands, the package manager doesn't come up with a GUI tool by default.

But like I said, if one is able to follow instructions accordingly; they should be fine.

---

### Post by juancarlospaco on 2010-02-14
***Whats the Oficial Arch Security Bulletin (Webpage and RSS), just like U.S.N. ???***

:)

---

### Post by docus on 2010-02-15
> **Dj Melik said:**
> Well I covered that in the rest of my post.

And compared to many other distros, you're going to need a lot 'great deal' of bash experience. To get most of it up and running, you're going to need to edit lots of config files, and run many commands, the package manager doesn't come up with a GUI tool by default.

But like I said, if one is able to follow instructions accordingly; they should be fine.

You're absolutely right.  I looked more closely at your original post, and I can see you were saying that all along.  Sorry for the confusion.  

I do feel that anyone interested in trying Arch should not be scared to give it a go, as the beginners' guide is so good (as you already said).

---

### Post by k3lt01 on 2010-02-16
> **RedSquirrel said:**
> I might try the Lucid mini install today to see if the issue still exists.@ RedSquirrel, did you try the Lucid mini.iso? If yes, did it work properly? I was thinking of trying it just after Alpha 3 is released but don't want to get stuck with a lot of download that I don't want.

---

### Post by RedSquirrel on 2010-02-16
> **k3lt01 said:**
> @ RedSquirrel, did you try the Lucid mini.iso? If yes, did it work properly? I was thinking of trying it just after Alpha 3 is released but don't want to get stuck with a lot of download that I don't want.

No, I haven't tried it yet. I thought I might try it sometime this week (and provide the results :)), but I must admit my enthusiasm is waning.

By the way, I tested Karmic again. Its mini installer still pulled in openoffice.org when I used it. :evil:

---

### Post by k3lt01 on 2010-02-16
Ah so they still haven't fix Karmic. Well I suppose I shouldn't wait with baited breath for them to fix Lucid then, I value my life to much lol.

---

### Post by swoll1980 on 2010-02-17
> **bobin said:**
> 1.I was wondering WHY arch is so fast?
2.Can the minimal install + Xorg + Some other useful stuff be as fast as arch?
3.If yes please tell me the light weight equivalents to what Iam using right now.
4.I ONLY have a wireless connection. Is it likely to be a problem? (In jaunty it works out-of-the-box)

I didn't know Arch was fast. I've tried about every distro in distrowatch's top fifty, and other than the default themes, and package manager there wasn't any kind of notable difference. The only thing that made Arch stand out from the rest for me, was the pain in the butt installation process. The only distro that really felt different was free bsd. It had a similar pain in the butt installation, but did feel a little bit snappier. The bsd distros aren't as far along as far as support goes, so that adventure was short lived.

---

### Post by nothingspecial on 2010-02-17
> **RedSquirrel said:**
> 
By the way, I tested Karmic again. Its mini installer still pulled in openoffice.org when I used it. :evil:

I didn`t even notice. I only realised I had openoffice when I removed apt and it removed it aswell.

---

### Post by TeamRocket1233c on 2012-05-01
> **snowpine said:**
> You could try one of the lightweight Ubuntu remixes. (CrunchBang is my favorite.) That would save you a lot of time over a minimal install at this stage in your Linux career.


Crunchbang saves more time, but Ubuntu minimal allows for more headroom as far as customization goes, allows you to learn Linux a little better, and can be pretty fun, and is not that tough.

Arch is great if you have the brains, the time, and the stones.

---

### Post by nothingspecial on 2012-05-01
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

