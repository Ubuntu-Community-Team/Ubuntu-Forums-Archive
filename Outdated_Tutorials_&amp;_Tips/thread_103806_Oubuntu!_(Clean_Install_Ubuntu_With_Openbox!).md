---
title: "Oubuntu! (Clean Install Ubuntu With Openbox!)"
date: 2005-12-14
forum: Outdated Tutorials &amp; Tips
---

### Post by ecto on 2005-12-14
Note: I am not sure if this method of install would work with Fluxbox... This is my first HOW-TO.
Introduction: After using linux for about three months now I have learned a great deal in thanks to the patient people in the ubuntu and ubuntuforums chatroom (and the ubuntu forum itself). While Gnome is fine and dandy, and KDE is more than useful, both still use a fair amount resources. Xfce seems like a logical choice with it's KDE chic and its lightweight but it still doesn't feel fast enough. If you feel this way why not use a WM? My WM of choice, of course, is Openbox. Most people suggest to install Gnome/KDE first, then sudo apt-get install openbox obconf, and finally exit into the GDM and select openbox. This is a good method however the only problem is you still have the bulk of Gnome or KDE on your HD. So then why not just delete Gnome/KDE? The answer to this my friends is that many of the apps you already (might) have depends on Gnome/KDE libraries. Therefore, the best solution is to clean/server/base install and apt-get openbox! So with no further a due the HOW-TO.
Step 1: The easy part.
a.)I will assume you have backed up all your data and no longer (or never had) a fear of command line. Ok... Now pop that beautiful ubuntu/kubuntu cd into your cdrom drive. When you are prompted on what kind of install you want to do type "server" and then press enter.
b.)Proceed with the installation (I.E. Set up the language, hostname, username, etc.)
c.)Log into CLI.
Step 2: The other easy part with a pinch of difficult.
a.)Before we go messing with the sources.list lets take precaution by backing it up shall we? Type sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup.
b.)Now we mess with the sources.list. Using your favorite CLI text editor (nano seems to be a popular choice i prefer VI) sudo vi /etc/apt/sources.list
c.)Uncomment: deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
                          deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
in order to activate repos.
d.)Type sudo apt-get update
e.)Type sudo apt-get upgrade
f.)Type sudo apt-get install irssi-text (you can use this to get help!)
g.)Type sudo apt-get install elinks (a very helpful text browser) (this is optional you can use w3m if you wish).
Step 3: The hard part.
a.)sudo apt-get install x-window-system-core
b.)sudo apt-get install xbase-clients
c.)sudo apt-get install xserver-xorg
d.)sudo apt-get install openbox obconf
e.)You can make a choice here. If you want you may choose any of the various terminals supplied to you. Therefore, you can have gnome-terminal, kterminal, xfce4-terminal, or xterm. I chose xfce4-terminal because its easier to read, customizable, and lighter than gnome-terminal and kterminal. So sudo apt-get install (one of the above terminals)
f.)You may get any web browser you so choose. If you want to sudo apt-get install mozilla you may. However, If you want to have the newest version of Firefox (which is the great part of a clean install) with this fresh install you can simply get it from the Firefox website using w3m or elinks! If you choose to do this make sure you decompress and untar Firefox before proceeding to the next step.
g.)Now run updatedb
h.)Type Locate menu.xml and cd to the location.
i.)Using your favorite editor open menu.xml (sudo vi/nano menu.xml)
j.)Now for where it says: 
 <item label="Terminal">
<action name="Execute"><execute>x-terminal-emulator</execute></action>
 </item>
replace x-terminal-emulator with the emulator you apt-get installed in step 3 part e. For example, since i chose xfce4-terminal this is how my xml coding looks like
  <item label="Terminal">
    <action name="Execute"><execute>xfce4-terminal</execute></action>
  </item>
k.)To set up the browser button find where it says 
<item label="Web browser">
    <action name="Execute"><execute>x-webrowser</execute></action>
 </item>
and where it says x-webrowser type the browser you chose in step 3 part f. If you got the newest version of firefox it is pertinent you put the whole string, meaning the directory and such. For example,
<item label="Web browser">
    <action name="Execute"><execute>/home/n0dl/firefox/firefox/./firefox</execute></action>
  </item>
Step 4: Moment of truth!
a.) Type startx 
God speed!
If you have problems you should check your .xsession-error. Its a log that tells you what went wrong. To access it type sudo vi (or nano) /home/username/.xsession-errors and scroll down... The newest problem is at the very bottom... Most likely you edited your xml script wrong
Well the background is an unfriendly shade of gray and the cursors are a tad different. But I will leave the cutomization to you. Here are some links to help you out to customizing your new openbox!
[https://wiki.ubuntu.com/Openbox](https://wiki.ubuntu.com/Openbox) (official wiki)
[http://ubuntuforums.org/showthread.php?t=75471](http://ubuntuforums.org/showthread.php?t=75471) (fun with alt-tab!)
[http://www.boxwhore.org/modules/news/](http://www.boxwhore.org/modules/news/) (disregard the name... Its a themes site)
Here are some screenshots of my openbox! (I am using the bluish theme)

---

### Post by iced-tux on 2005-12-15
Hi,
nice HowTo ;)
Myself I am also using OpenBox and I love it. It's fast, it's highly configurable *well ok a bit behind fluxbox but ....* and it's lightweighted.


For your HowTo, why not using the firefox packages available?
As for to further speed up your system:
1) An alternative to thunderbird *nice* is sylpheed. It has an gtk1/2 frontend , is easy to configure and very, very fast.
2) rxvt-unicode is a nice and very good terminal :) or xterm ;)
3) A nice run-dialog like we have it in Gnome: gmrun
 - Use a keybinding like A-F2 to execute gmrun ;)
4) For your background image use something like feh
5) To have some EyeCandy you can use adesklet *personally I like the gdesklets more, though there are some Gnome dependencies on them* So it's possibly to have some icons on your "desktop" and a starter bar etc.
6) A nice tool to show yout system status: conky
7) Don't forget to grab your xscreensaver

Here my Openbox starter:

```

#!/bin/sh
# Openbox startet mit einigen kleinen Anwendungen. F&#252;r alle Benutzer startbar
# /usr/bin/myopenbox
##
# Daemon fuer Terminal
exec urxvtd &
# ein buntes Bild
exec feh --bg-scale /home/i0109/.config/openbox/backgrounds/sleeper_1280x1024.jp
g &
#Bildschirmschoner
exec xscreensaver -no-splash &
# Conky
exec conky &
# gDesklets
exec gdesklets &
# und hier unser Fenstermanager
exec /usr/bin/openbox

```

iced-tux

---

### Post by ecto on 2005-12-17
How do you make a openbox starter? I was reading the openbox wiki before i made this How-to but could never find the "xsession." thingie which shows the sartup processes of xserver/xorg.? Is there a way to make a startup script that starts apps up on different desktops I.E. Web browser opens at start up on desktop 1, 4 terminals start up on Desktop 2, etc?

---

### Post by Juippisi on 2005-12-20
Good howto indeed and Openbox seems very beatiful. But still, I prefer PekWM more ;-).

---

### Post by daschl on 2005-12-20
[QUOTE=ecto]How do you make a openbox starter? I was reading the openbox wiki before i made this How-to but could never find the "xsession." thingie which shows the sartup processes of xserver/xorg.? Is there a way to make a startup script that starts apps up on different desktops I.E. Web browser opens at start up on desktop 1, 4 terminals start up on Desktop 2, etc?[/QUOTE]

its really easy.

```

$ nano ~/.xinitrc

```

and add these lines

```

openbox &
**optional**

```

replace **optional** with the programs you like. important is the "&" at the end, so if you want to use a taskbar you may apt-get fbpanel and if you want to set a wallpaper you can use feh for example.

so in the end your config file maybe looks like this

```

openbox &
fbpanel &
feh --bg-scale ~/images/wallpapers/mywallpaper.png &
firefox

```

good luck

---

### Post by Juippisi on 2005-12-20
[QUOTE=daschl]its really easy.

```

$ nano ~/.xinitrc

```

and add these lines

```

openbox &
**optional**

```

replace **optional** with the programs you like. important is the "&" at the end, so if you want to use a taskbar you may apt-get fbpanel and if you want to set a wallpaper you can use feh for example.

so in the end your config file maybe looks like this

```

openbox &
fbpanel &
feh --bg-scale ~/images/wallpapers/mywallpaper.png &
firefox

```

good luck[/QUOTE]


Hmm? I've always thought that first the apps you want to start and then the WM.

---

### Post by Juippisi on 2005-12-20
[http://forums.gentoo.org/viewtopic-t-406741-highlight-xinitrc.html](http://forums.gentoo.org/viewtopic-t-406741-highlight-xinitrc.html)

"As far as I know, it doesn't matter what order your ~/.xinitrc things are in, as long as the WM/DE script is the last thing on the list."
Like that.

But
"I load the wm first otherwise fbpanel gets confused"

and 
"I don't believe it does, because the amperstands at the end of each line background those process instantly... "

So, I really don't know. Maybe it doesn't matter then ;-).

---

### Post by ecto on 2005-12-20
I tried the to sudo vi ~/.xinitrc and make a new xinitrc script but x kept on crashing on me. I tried to locate to see if there are any other "xinitrc" scripts around and i found one besides the one I newly created
> n0dl@ubuntu:~$ locate xinitrc
/etc/X11/xinit/xinitrc

I peeked into this file with vi and i found this:
> #!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

So what do i do? Do i simply edit this initrc file? Or do i some how make it execute my script?
Also btw. For some reason my keybinds dont work. I used to be able to switch desktops by simply using ALT-1 or ALT-2. I edited my rc.xml script but it still doesnt work. Thanks your help is much appreciated.

---

### Post by ecto on 2005-12-20
Well i figured what happened with my xinitrc file
apperently you dont simply state
> openbox &
actually its
> exec openbox
at the end of the file.
That and i needed to add #!/usr/bin/env/bash
to the beginning.
but still my keybinds dont work... still need help with that
thanx

---

### Post by daschl on 2005-12-21
> **Juippisi][http://forums.gentoo.org/viewtopic-t-406741-highlight-xinitrc.html](http://forums.gentoo.org/viewtopic-t-406741-highlight-xinitrc.html)

"As far as I know, it doesn't matter what order your ~/.xinitrc things are in, as long as the WM/DE script is the last thing on the list."
Like that.

But
"I load the wm first otherwise fbpanel gets confused"

and 
"I don't believe it does, because the amperstands at the end of each line background those process instantly... "

So, I really don't know. Maybe it doesn't matter then  said:**
> 

well i dont think that its really a problem

just try, but "my" method works fine for me (openbox was the first windowmanager i used with slackware, so i read a tutorial about it a year ago and the author did it "my" way)

[QUOTE=ecto]Well i figured what happened with my xinitrc file
apperently you dont simply state

actually its

at the end of the file.
That and i needed to add #!/usr/bin/env/bash
to the beginning.
but still my keybinds dont work... still need help with that
thanx
can you post your .xinitrc here?

for your info: the xinitrc in the X11 directory is for global settings which affect all users. as the majority of the config files the dotfile in your homedirectory overwrites the settings which were set in the global file. so it doesnt matter what variables are set in the global config file, as long you override them in your personal dotfile.

---

### Post by karma 23 on 2005-12-23
If using only a WM instead of a complete DE, are we still able to do the basics like networking, multimedia, and the such?  How would we access files and would Samba run?  I like the idea of having as little as possible, but would it affect everyday "normal" usage?

---

### Post by Juippisi on 2005-12-23
Of course you can get everything up n' running. I suggest you to put "exec gnome-settings-daemon &" to your .xinitrc -file. It really makes your life easier ;-) (applies Gnome's settings to programs under Openbox, but you need some Gnome-stuff installed)

---

### Post by karma 23 on 2005-12-23
Thanks Juippisi!  I will give that a try.

---

### Post by daschl on 2005-12-26
for gnome users, this is the easy way :)

```

$ sudo apt-get install openbox
$ sudo apt-get install obconf

```

and then follow this guide:

[http://icculus.org/openbox/docs.php?page=build.html#install-gnome](http://icculus.org/openbox/docs.php?page=build.html#install-gnome)

for kde users:

[http://icculus.org/openbox/docs.php?page=build.html#install-kde](http://icculus.org/openbox/docs.php?page=build.html#install-kde)

well, another way is to boot in an other runlevel and then edit you xinitrc (used by startx) this may be useful if you are running a server

---

### Post by iced-tux on 2005-12-29
If you use .xinitrc or .xsession or an external script depends also heavily which login manager you use.
On my homebox I use wdm and if you start the default session, it listens to .xsession.
There I have put in things like:
exec conky & 
and some stuff.
Last line is exec /usr/bin/openbox.

For GDM you have to edit the openbox.desktop file. There you find a link to the executable that GDM uses. Set it to your liking e.g. /usr/local/bin/myopenbox and put into that your apps you want to have started with openbox.

---

### Post by karma 23 on 2006-01-03
I can't seem to install Samba under a fresh install with only OpenBox.  How would I go about doing it?  Or are there any other easier ways to network computers with only a WM?  I'm trying to hop on a Windows network at the office.

---

### Post by oss_monkey on 2006-07-24
DISCLAIMER: I have limited experience with these things. :)

> **karma 23 said:**
> I can't seem to install Samba under a fresh install with only OpenBox.  How would I go about doing it?  Or are there any other easier ways to network computers with only a WM?  I'm trying to hop on a Windows network at the office.

The easiest way I found to access network items was to use nautilus. Yes, it probably has GNOME dependencies, but if you're willing to install them to make life easier, why not?

The clean OpenBox desktop won't be ruined as long as you run
> nautilus --no-desktop

but again, YMMV.

---

### Post by amgeex on 2006-10-13
I want my GTK applications to look as good as if they were running under gnome. How do I do that?

Do I need to install gnome? I hope not, because that'd defeat the purpose of having a minimal system. Also, how do one installs gnome's volume manager so CD's and usb drives get automounted?

Thanks! :D

---

### Post by rogerdean on 2008-09-10
Hello all
Many thanks to the OP for this post so many years ago! Now, does anyone have an update for Hardy? I'd like to give openbox a whirl but doubtless much has changed since 2005...
Cheers
Roger

---

### Post by urukrama on 2008-09-10
Have a look at my guide (link in signature). It doesn't cover installing Ubuntu, but you can use [Aysiu's guide]("http://psychocats.net/ubuntu/minimal") for that. If you want to do without a session manager, such as GDM, have a look at [this page]("https://wiki.ubuntu.com/CustomXSession") on the Ubuntu Wiki.

---

### Post by rogerdean on 2008-09-10
wow, lots of info there - will take a while to digest. thanks very much!

---

### Post by MooPi on 2009-07-29
Use Pcmanfm , it is a great file manager that will handle your usb sticks , external drives etc etc.....

---

