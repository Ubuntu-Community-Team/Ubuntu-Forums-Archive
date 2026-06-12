---
title: "Make Lubuntu even slimmer, more lightwear"
date: 2015-06-13
forum: New to Ubuntu
---

### Post by Xpdin on 2015-06-13
I am a beginner in Linux


I hope I am allowed to ask all these questions in one Topic. Please replay to me to the next 3 questions: I will number them to be easier for you to answer...


Which are the ways to make Lubuntu even faster, slimmer, more lightwear, to make it to has only exactly the options I need from it.


Are there any default pre installed programs from Lubuntu which are not safe to uninstall?


Which one is the most lightware and only with the option for downloading subtitles(would be better to search on more subtitles websites) application for Lubuntu to watch movies. I think I don't need any other more other options then the two above ones than GNOME MPlayer has.


Thank you.

---

### Post by cariboo on 2015-06-13
Instead of using Lubuntu, I'd suggest using the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), and only install what you want/need.

---

### Post by mörgæs on 2015-06-13
Yes, a minimal ISO is a good beginning. After that you could add the core packages as described [here]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install.2C_minimal_install_or_core_install.3F").

---

### Post by deadflowr on 2015-06-13
I forget but isn't there a lubuntu-minimal option in mini.iso?
Which is, as expected, a very trimmed down lubuntu desktop.

---

### Post by sudodus on 2015-06-13
Lubuntu Core has the same desktop environment as standard Lubuntu, but very few installed program packages, so the users can select and install their own favourites. Both Lubuntu and Lubuntu Core can run an Openbox session with only the window manager, and not the whole desktop environment. That way less RAM and CPU power is used, so there will be more available for the application programs.

---

### Post by v3.xx on 2015-06-13
Here's the package list

[http://packages.ubuntu.com/trusty/lubuntu-core](http://packages.ubuntu.com/trusty/lubuntu-core)

The red dots are the necessary packages and the green dots are recommended packages.  You can install just the red dot packages or all.

To compare a full desktop install of lubuntu

[http://packages.ubuntu.com/trusty/lubuntu-desktop](http://packages.ubuntu.com/trusty/lubuntu-desktop)

---

### Post by Xpdin on 2015-06-13
Thank you for your replies,

Tell me please where could I find the iso of the Lubuntu core, so I could use it with the mini.iso?

Here I couldn't find it...

[http://packages.ubuntu.com/trusty/lubuntu-core](http://packages.ubuntu.com/trusty/lubuntu-core)

Here [http://packages.ubuntu.com/trusty/i386/lubuntu-core/download](http://packages.ubuntu.com/trusty/i386/lubuntu-core/download) is the .deb file, but could I use it with mini.iso ?

Excuse me but I can't find the downloadable direct link for mini.iso too...

Kind regards.

---

### Post by sudodus on 2015-06-13
You won't find an iso file for it. You install it from the Ubuntu mini.iso by selecting to install the lubuntu-core package.

- either from the menu system inside the mini.iso installer

- or in the installed bare-bone text mode system with the command

```
sudo apt-get install lubuntu-core
```

---

### Post by Xpdin on 2015-06-13
Thank you sudodus...

First, tell me please how can I see if now I am using Lubuntu Core/Desktop?

Second, tell me please I am interested to install it from a USB Stick... it could work with the command from the terminal?

Thank you.

---

### Post by sudodus on 2015-06-13
1. If you try to install it again, it will tell you that it is already installed.

2. At the login screen you can select between several 'sessions' which means desktop environments or window managers (if you have more than one available).

---

### Post by Xpdin on 2015-06-13
I downloaded this [http://packages.ubuntu.com/trusty/i386/lubuntu-core/download](http://packages.ubuntu.com/trusty/i386/lubuntu-core/download) and after that open the downlaoded .deb file and it opens a Window - Status: Same version is already installed" with 3 buttons on the right side "Reinstall Package" "Download Package" "Remove Package" That's means that I am using Lubuntu Core, not Lubuntu Desktop ?

Thanks...

```
dpkg -l | grep lubuntu-core

ii  lubuntu-core                                0.55                                    i386         Lubuntu Desktop environment - minimal installation

```
This means I am using Lubuntu Core, isn't it?

Thank you..

---

### Post by deadflowr on 2015-06-13
lubuntu-desktop needs lubuntu-core in order work, so it makes sense you would already be using it, or have it.

---

### Post by Xpdin on 2015-06-13
Ups :) 

So, I still could have Lubuntu Desktop installed, using it now?

Thnaks.. :)

---

### Post by v3.xx on 2015-06-13
A quick way to see if the core or the whole package is installed:
```
aptitude
```
A core install will show something like 7 to 800 packages installed.
A full install will be about double the packages.

---

### Post by Xpdin on 2015-06-13
Thank you @v3.xx

```
aptitude
--- Installed Packages (1279)
--- Not installed Packages (44436)
--- Virtual Packages (5049)
--- Tasks (24509)

These packages are currently installed on your computer

This group contains 1279 packages.

```

A great Sunday to all ! :)

---

### Post by vasa1 on 2015-06-14
I've been going through [your posts]("http://askubuntu.com/users/413624/xpdin") in Ask Ubuntu. Do you have more than one machine or more than one operating system on the same machine?

Could you tell people a little about the hardware specs of the computer on which you have Lubuntu?

There maybe quite a few applications in a full Lubuntu install that you can remove without breaking things. When I want to remove something, I look at what else will be removed by *simulating* the removal:```
apt-get purge **-s** package_name
``` This is a totally harmless exercise and doesn't even need **sudo**.

---

### Post by Xpdin on 2015-06-14
Many appreciations for your interest vasa1

I have only one machine - [HP 6820s]("http://www.cnet.com/products/hp-compaq-6820s-17-core-2-duo-t5870-vista-business-xp-pro-downgrade-2-gb-ram-250-gb-hdd/specs/") (maybe the hardware configuration could support more than Lubuntu, but for now I am interested in as simple as possible for a beginner :) )

I use only one operating system - Lubuntu

Thank you for your advice, but for the moment I think I would be more interested to take from scrap with a new clean fresh installation of Lubuntu Core, if I don't have it already installed.

If it helps someone to say if I use Lubuntu Desktop/Core, at the beginning, on the taskbar, on the left side was a Icon from which I could change from Desktop 1 to Desktop 2.

Warm regards.

> **v3.xx said:**
> A quick way to see if the core or the whole package is installed:
```
aptitude
```
A core install will show something like 7 to 800 packages installed.
A full install will be about double the packages.

> **Xpdin said:**
> Thank you @v3.xx

```
aptitude
--- Installed Packages (1279)
--- Not installed Packages (44436)
--- Virtual Packages (5049)
--- Tasks (24509)

These packages are currently installed on your computer

This group contains 1279 packages.

```

A great Sunday to all ! :)


So, it seems that I have Lubuntu Core installed in this moment, is this correct please?

Thanks.

---

### Post by Bucky Ball on 2015-06-14
As mentioned, do a minimal install, DON'T load a machine profile, i.e. Lubuntu-desktop or core, after reboot you will be in a CLI. Login and:

```
sudo apt-get install lxde synaptic
```

Away you go. Install what you want. You now have the kernel, the Lubuntu desktop environment ONLY, and a package manager.

---

### Post by v3.xx on 2015-06-14
> So, it seems that I have Lubuntu Core installed in this moment, is this correct please?
I think you have a full desktop install.  Another way to check:
```
apt-cache policy lubuntu-desktop
```

---

### Post by Xpdin on 2015-06-14
```
apt-cache policy lubuntu-desktop
lubuntu-desktop:
  Installed: 0.55
  Candidate: 0.55
  Version table:
 *** 0.55 0
        500 http://dk.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status

```

Now is 100% sure that I use Lubuntu Desktop, is it right?

Thousands of thanks.

---

### Post by v3.xx on 2015-06-14
> Now is 100% sure that I use Lubuntu Desktop, is it right?
You are 100% correct :)

---

### Post by Xpdin on 2015-07-11
Hi again,

Tell me please it could be possible after I used:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

to change the system from Lubuntu-core (Minimal installation) to Lubuntu-Desktop ?

After ```
sudo apt-get dist-upgrade
``` for a few minutes it installed something about generic...

My actual system:

   ```
apt-cache policy lubuntu-desktop
lubuntu-desktop:
  Installed: (none)
  Candidate: 0.55
  Version table:
     0.55 0
        500 http://dk.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages

```


```
aptitude

--- New Packages (40)
--- Installed Packages (1174)
--- Not installed Packages (44533)
--- Virtual Packages (5048)
--- Tasks (24509)

```

From what I can remember a few weeks ago when I made a new fresh install of Lubuntu-core (Minimal Installation), after: ```
aptitude
``` I had less Installed Packages(sorry, I can't remember exactly how many), and now, as you can see in my actual aptitude, it seems that I have Lubuntu-Desktop again, as in the previous posts from this topic...

Please answer to the next 3 questions
I will number them to be easier for you to answer

1. Tell me please, am I using now Lubuntu Desktop?

2. If the question from the first point is "Yes", tell me please how is this possible if it didn't happen after using the first 3 commands from the beginning of this post.

3. If now I am using Lubuntu Desktop, is there any way to go back to Lubutu-core?

Kind regards.

---

### Post by Bucky Ball on 2015-07-11
To install Lubuntu-desktop:

```
sudo apt-get install lubuntu-desktop
```

Be aware that this is exactly the same as installing Lubuntu in the first place so there was no point in installing Lubuntu-core, so to do this is contradictory to the title of your thread. You will be making Lubuntu-core less lightweight. Just throwing that in so you are completely aware of what you are about to do. Good luck. :)

PS: I am presuming this:

```
sudo apt-get updatesudo apt-get upgrade
sudo apt-get dist-upgrade
```

... is a typo. It should be three commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Xpdin on 2015-07-11
Sorry, it was a typing mistake...

I used:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Excuse me, for my previous mistakes from questions 1 and 2(I have just edited them).

Now I am interested to come back or still using Lubuntu-core, if somebody can say if now I have already been using it.

Thanks.

---

### Post by Bucky Ball on 2015-07-11
You could try:

```
lsb_release -a
```

... and see what that shows. Depending on what you've added to lubuntu-core, if that's what you installed in the first place and not Lubuntu, remove what you've added.

Best guarantee is to install lubuntu-core from scratch. If all you've done so far is installed and done no setting up, that's what I'd do, if that's where you want to be.

---

### Post by Xpdin on 2015-07-11
tasksel Thanks Bucky Ball

```
 lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

```

It seems that is Lubuntu Desktop?

I will try to tell what I can remember as much and as correct as possible

Around two weeks ago I downloaded [PC (Intel x86) alternate install image]("http://cdimages.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-alternate-i386.iso") from here [Lubuntu 14.04.2 LTS (Trusty Tahr) ]("http://cdimages.ubuntu.com/lubuntu/releases/trusty/release/") 

With UNetbootin I put the above downloaded iso on a USB Stick and installed it. After the installation finished, it boots only directly in a console something tty1 or tty2. In the console I typed:

```
tasksel
```

and after that:

```
sudo apt-get install lubuntu-core

```

Everything should be ok with these steps for a correct installation of Lubuntu-core?

---

### Post by Bucky Ball on 2015-07-11
Tasksel may do the same job, but I would install like this. Install the [minimal .iso]("https://help.ubuntu.com/community/Installation/MinimalCD") (which could equate to the Lubuntu alternative .iso, I don't know), once installed, reboot and you will arrive at the login prompt. Login then:

```
sudo -i
apt-get install lubuntu-core
apt-get dist-upgrade
apt-get autoclean
rm /var/cache/apt/archives/*.deb
reboot
```

You have Lubuntu-core on reboot.

---

### Post by deadflowr on 2015-07-11
```
echo $DESKTOP_SESSION
```
should tell you what desktop session you are now running.

I do not know whether that will show anything helpful though.
Another command to see might be
```
printenv
```
might as well post the whole output.
As it usually contains something help, or interesting about the current desktop session...

---

### Post by Xpdin on 2015-07-11
Before installing Lubuntu-core like on the previous post, I tried to install it from mini.iso, but at the boot instead of sending me a tty console like my actual Lubuntu-core, it stopped on a black screen.

From what I can remember, after pressing ctrl+alt+f1 in that black screen it sended me in a tty, but there I think it didn't work sudo commands, I am not very sure about it, maybe I will try that way too.

But tell me please even with the way I've followed, now I should been using Lubuntu-core is it right? 

How is that possible now to have Lubuntu Desktop installed ?

If It could be from...

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` 

I shouldn't use ```
upgrade/dist-upgrade
``` them even If I will install Lubuntu-core with mini.iso?

```
echo $DESKTOP_SESSION
Lubuntu
```

```
printenvXDG_VTNR=7
XDG_SESSION_ID=c2
CLUTTER_IM_MODULE=xim
XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/xpdin
SELINUX_INIT=YES
SAL_USE_VCLPLUGIN=gtk
SESSION=Lubuntu
GPG_AGENT_INFO=/run/user/1000/keyring-bK5K7n/gpg:0:1
TERM=xterm
SHELL=/bin/bash
XDG_MENU_PREFIX=lxde-
WINDOWID=29360164
UPSTART_SESSION=unix:abstract=/com/ubuntu/upstart-session/1000/1369
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-bK5K7n
XTERM_SHELL=/bin/bash
USER=xpdin
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK=/run/user/1000/keyring-bK5K7n/ssh
DEFAULTS_PATH=/usr/share/gconf/Lubuntu.default.path
XDG_CONFIG_DIRS=/etc/xdg/lubuntu:/etc/xdg/xdg-Lubuntu:/usr/share/upstart/xdg:/etc/xdg
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
DESKTOP_SESSION=Lubuntu
QT_IM_MODULE=ibus
JOB=dbus
PWD=/home/xpdin
XMODIFIERS=@im=ibus
LANG=en_US.UTF-8
GNOME_KEYRING_PID=1367
GDM_LANG=en_US
MANDATORY_PATH=/usr/share/gconf/Lubuntu.mandatory.path
IM_CONFIG_PHASE=1
GDMSESSION=Lubuntu
XTERM_LOCALE=en_US.UTF-8
XTERM_VERSION=XTerm(297)
_LXSESSION_PID=1499
SESSIONTYPE=lxsession
HOME=/home/xpdin
SHLVL=1
XDG_SEAT=seat0
XDG_CONFIG_HOME=/home/xpdin/.config
LANGUAGE=en_US
UPSTART_INSTANCE=
UPSTART_EVENTS=started xsession
LOGNAME=xpdin
XDG_DATA_DIRS=/etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/usr/share/Lubuntu:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-WKjCC3J3YQ
QT4_IM_MODULE=xim
LESSOPEN=| /usr/bin/lesspipe %s
UPSTART_JOB=lxsession
INSTANCE=
TEXTDOMAIN=im-config
DISPLAY=:0
XDG_RUNTIME_DIR=/run/user/1000
XDG_CURRENT_DESKTOP=LXDE
GTK_IM_MODULE=ibus
LESSCLOSE=/usr/bin/lesspipe %s %s
TEXTDOMAINDIR=/usr/share/locale/
XAUTHORITY=/home/xpdin/.Xauthority
_=/usr/bin/printenv





```

---

### Post by Bucky Ball on 2015-07-11
The desktop Lubuntu uses is lxde. If you have any Lubuntu installed, you are already using it. Run the command deadflowr provided earlier. 

echo $DESKTOP_SESSION

Does it say 'lxde'? If so, you're already using the same desktop environment as Lubuntu does.

---

### Post by sudodus on 2015-07-11
The difference between Lubuntu Core and Lubuntu is that Lubuntu (lubuntu-desktop) contains several 'extra' application programs (for example firefox, abiword, gnumeric, lxterminal, leafpad), plus some settings.

If you install lubuntu-desktop you will arrive at (almost) the same result as if you install Lubuntu directly, and all the effort to get a slimmer version will be wasted.

Lubuntu Core and Lubuntu (lubuntu-desktop) are actually meta-packages (packages of packages) that will give you a specified set of programs and settings. If you want something really light-weight, you should listen to Bucky Ball's advice, start from the Ubuntu mini.iso and install only the packages that you want. Avoid meta-packages, which will install a lot of packages, some of which you want, but also several packages, that you do not want. Maybe it is enough with a window-manager (openbox, fluxbox, jwm ...) instead of a full desktop environment (lxde, xfce, mate, gnome3, kde, unity ...).

It is much harder to remove packages and dependencies than to install them, so it is better to start in the small end and avoid installing things that you don't need. If you use the option 

```
--no-install-recommends
```

so
```
sudo apt-get --no-install-recommends install package-name
```

the installation will be leaner. See ```
man apt-get
```

---

### Post by Xpdin on 2015-07-25
I appreciate all your replays,

I have 5 questions please:
I will numerate them to be easier for you to answer.

> **sudodus said:**
> 
you should listen to Bucky Ball's advice, start from the Ubuntu mini.iso and install only the packages that you want. 

1. Tell me please, should I fallow all the normal or any other advanced steps when installing from mini.iso, until one of the last steps were it asks what Ubuntu distribution  I would like to install, and there I will chose Ubuntu or Lubuntu Minimal Installation ? 

> **sudodus said:**
> 
It is much harder to remove packages and dependencies than to install  them, so it is better to start in the small end and avoid installing  things that you don't need. If you use the option 

```
--no-install-recommends
```

so
```
sudo apt-get --no-install-recommends install package-name
```

2. When should I enter the above 2 commands please? After the installation from mini.iso completed -> restart -> ctrl+alt+f1 -> in that console I should write only those 2 commands? Or should I write any other commands above or beyond those 2?

3. Are there any mandatory packages which I should install with the second command, or they will automatically be installed, so the system can function properly?

 > **sudodus said:**
> 
Maybe it is enough with a window-manager (openbox, fluxbox, jwm ...)  instead of a full desktop environment (lxde, xfce, mate, gnome3, kde,  unity ...).


4. I will have to install openbox with the second command from question nr. 2?

5.More than lighter, tell me please which are the other most important advantages/disadvantages  between using openbox instead of a full desktop environment?

a)For a beginner could I meet many difficulties in using openbox instead of a full desktop environment? 
b) Is it possible to use themes in openbox? (not for me)
c) Is it possible to switch between openbox and the full desktop environment, without restart?
d) Are there any stability or safety differences between using openbox and a full desktop environment?

If you have more differences to add between using openbox instead of a full desktop environment, would be a big favor.

Warm regards.

---

### Post by sudodus on 2015-07-25
> **Xpdin said:**
> I appreciate all your replays,

I have 5 questions please:
I will numerate them to be easier for you to answer.

1. Tell me please, should I fallow all the normal or any other advanced steps when installing from mini.iso, until one of the last steps were it asks what Ubuntu distribution  I would like to install, and there I will chose Ubuntu or Lubuntu Minimal Installation ? 

Follow all the normal steps. I suggest that you select ***no*** package to install, when offered by the menu wizard. Do the rest of the tweaking after booting into the installed system.
> 
2. When should I enter the above 2 commands please? After the installation from mini.iso completed -> restart -> ctrl+alt+f1 -> in that console I should write only those 2 commands? Or should I write any other commands above or beyond those 2?
Those are only an illustration. You should install packages (with real package names), for example as a minimum:

```
sudo apt-get update
sudo apt-get dist-upgrade

sudo apt-get install fluxbox xinit xterm
# or
sudo apt-get install openbox xinit xterm
```
> 

3. Are there any mandatory packages which I should install with the second command, or they will automatically be installed, so the system can function properly?

See the reply above. But I think you want a web browser and a file browser too, and probably a graphical text editor, a picture viewer and a pdf viewer.> 
4. I will have to install openbox with the second command from question nr. 2?
There are alternatives, for example fluxbox and jwm> 
5.More than lighter, tell me please which are the other most important advantages/disadvantages  between using openbox instead of a full desktop environment?

a)For a beginner could I meet many difficulties in using openbox instead of a full desktop environment? 
Yes, the desktop environment is like a quick start guide or manual. Without experience it is hard to run a plain window manager.> 
b) Is it possible to use themes in openbox? (not for me)
You already replied to this question. I can add: Not now, but maybe later ;-)> 
c) Is it possible to switch between openbox and the full desktop environment, without restart?
Yes, via the log in screen> 
d) Are there any stability or safety differences between using openbox and a full desktop environment?
In a simpler system there are fewer things that can go wrong.> 
If you have more differences to add between using openbox instead of a full desktop environment, would be a big favor.

Warm regards.

Since you don't know, I think you should choose Lubuntu Core or maybe even the full Lubuntu (and switch between standard Lubuntu, Lubuntu-netbook and Openbox sessions.

```
sudo apt-get install lubuntu-core
```

And in case you select Lubuntu, of course you install it easier from a Lubuntu desktop or alternate iso file.

---

