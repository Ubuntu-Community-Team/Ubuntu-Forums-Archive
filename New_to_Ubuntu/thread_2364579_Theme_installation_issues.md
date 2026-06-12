---
title: "Theme installation issues"
date: 2017-06-24
forum: New to Ubuntu
---

### Post by 1jarwolf on 2017-06-24
Hello, I am somewhat new to Ubuntu. I can't seem to install themes correctly. I attempted to install macbook theme onto Ubuntu. Everything works except that side panel to the left. It still looks like the default clean side panel as when you first installed Ubuntu. I can't seem to get it to work. Any suggestions on how to install themes, as well as themes that make the GUI look better, and easier to get around, other than having to search programs up by the name in order to open it? Also, as a side note, any programs to automatically install tar, bz2 files and whatnot? 

Thanks!:confused::confused:

---

### Post by howefield on 2017-06-25
> **1jarwolf said:**
> I can't seem to install themes correctly. I attempted to install macbook theme onto Ubuntu. Everything works except that side panel to the left.

What tutorial are you trying to follow ? 

> Also, as a side note, any programs to automatically install tar, bz2 files and whatnot? 

A tar file is just a bundle of files, not necessarily installable. If you mean to ask for an application that would extract those types of files then Archive Manager which is included in the default Ubuntu installation should do it.

---

### Post by 1jarwolf on 2017-06-25
I thank you for your response, as I am certainly happy that I can get support! The tutorial I was watching on how to install a theme is this youtube video. Also, the side panel, I could not get working, I guess what I mean is, if you watch the video, that whole bar to he left of his screen is what I can't seem to change, no matter what theme I install.  [URL="https://www.youtube.com/watch?v=inZ9uYYILXU"]https://www.youtube.com/watch?v=inZ9uYYILXU 

[/URL] Okay, I thank you so much for te tar files. I was trying to install a program called "keepassx-2.0.3" , however I do not know how to install it once extracted to the system.

EDIT: I have both Ubuntu Tweak, and Tweak Tool and I tried both programs, and still no success.

---

### Post by howefield on 2017-06-25
> **1jarwolf said:**
> I thank you for your response, as I am certainly happy that I can get support! The tutorial I was watching on how to install a theme is this youtube video. Also, the side panel, I could not get working, I guess what I mean is, if you watch the video, that whole bar to he left of his screen is what I can't seem to change, no matter what theme I install.  [URL="https://www.youtube.com/watch?v=inZ9uYYILXU"]https://www.youtube.com/watch?v=inZ9uYYILXU 

OK, someone might watch the video and work it out.

> I was trying to install a program called "keepassx-2.0.3" , however I do not know how to install it once extracted to the system.

What version of Ubuntu are you using ?

Xenial (16.04) has keepassx version 2.0.2 and Zesty (17.04) has keepassx version 2.0.3 already in the repositories, so is very easy to install without the need for external sources. If you are using Ubuntu 14.04 then it might be a different story as keepassx is only version 0.4.3.

---

### Post by again? on 2017-06-25
Do you just want to change the colour of the unity launcher or change the layout of the panels?
The unity launcher by default is transparent, so it's colour is determined by the desktop wallpaper which is what I see in the video.
You can change the unity launcher's colour and transparency with compizconfig-settings-manager(ccsm).

If it's a different panel layout you want you could install another desktop environment.
[**top-linux-desktop-environments-compared**]("http://www.pcworld.com/article/2951829/operating-systems/freedom-of-choice-7-top-linux-desktop-environments-compared.html")

---

### Post by 1jarwolf on 2017-06-25
> **guber2 said:**
> Do you just want to change the colour of the unity launcher or change the layout of the panels?
The unity launcher by default is transparent, so it's colour is determined by the desktop wallpaper which is what I see in the video.
You can change the unity launcher's colour and transparency with compizconfig-settings-manager(ccsm).

If it's a different panel layout you want you could install another desktop environment.
[**top-linux-desktop-environments-compared**]("http://www.pcworld.com/article/2951829/operating-systems/freedom-of-choice-7-top-linux-desktop-environments-compared.html")

AHA! Thank you so much! Yes! That is what I meant. The layout of the panels. I looked at that link you provided and I am gearing towards the "Linux Mint with the Cinnamon desktop." 

In the console I typed in [COLOR=#ff0000]sudo apt-get install cinnamon [/COLOR]and I got the following errors.

"[I]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: libcjs0e (>= 3.2.0-20170426020128) but it is not going to be installed
            Depends: cinnamon-screensaver (>= 3.4.0) but it is not going to be installed
            Depends: libcjs0-libmozjs-24-0
            Recommends: cinnamon-bluetooth but it is not installable
E: Unable to correct problems, you have held broken packages.[/I]"

From the error above, from what I am getting from it, is that I have to go and install a better version of libcjs0e and cinnamon-screensave

> **howefield said:**
> OK, someone might watch the video and work it out.



What version of Ubuntu are you using ?

Xenial (16.04) has keepassx version 2.0.2 and Zesty (17.04) has keepassx version 2.0.3 already in the repositories, so is very easy to install without the need for external sources. If you are using Ubuntu 14.04 then it might be a different story as keepassx is only version 0.4.3.

That is odd. I have Ubuntu 16.04 LTS. I searched my computer and put in keepppassx and nothing showed up for it.

---

### Post by howefield on 2017-06-25
> **1jarwolf said:**
> That is odd. I have Ubuntu 16.04 LTS. I searched my computer and put in keepppassx and nothing showed up for it.

It isn't keepppassx... try opening a terminal and post the output of 

```
apt-cache policy keepassx
```

The output should be something like (but not the same as)..

```
apt-cache policy keepassx
keepassx:
  Installed: 2.0.3-1
  Candidate: 2.0.3-1
  Version table:
 *** 2.0.3-1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) artful/universe amd64 Packages
        100 /var/lib/dpkg/status
```

Should give you the version available to you and to install it you can use..

```
sudo apt install keepassx
```

---

### Post by oldos2er on 2017-06-25
```
sudo apt-get update; sudo apt-get keepassx
``` should get you keepassx (note spelling).

Ninja'ed!

---

### Post by again? on 2017-06-25
I don't do a lot of distro hopping nowadays but I believe mint uses the cinnamon desktop which you can install in Ubuntu/unity.
You can install other desktop environments (DE) but sometimes they don't play together nicely and you will also get duplicate file managers, text editors etc.
[https://wiki.archlinux.org/index.php/desktop_environment](https://wiki.archlinux.org/index.php/desktop_environment)
You can select your installed DE at the greeter.
[ATTACH=CONFIG]275768[/ATTACH]

Best thing to do is install and test some different DE's and when you find one you like 
do a clean install of a distro that uses that DE.
eg
Kubuntu uses kde
Xubuntu uses xfce4
Lubuntu uses lxde
Ubuntu Gnome uses Gnome
Linux Mint uses cinnamon

To install a DE you usually install a package ending in "-desktop.
eg
[LIST]
[*]kubuntu-desktop
[*]Xubuntu-desktop
[*]lubuntu-desktop
[/LIST]

These will pull in all the applications needed for that DE.

Have a look in synaptic.(software centre is crap) You will need to install synaptic.
```
sudo apt install synaptic
```
[ATTACH=CONFIG]275769[/ATTACH]

---

### Post by again? on 2017-06-25
> **1jarwolf said:**
> AHA! Thank you so much! Yes! That is what I meant. The layout of the panels. I looked at that link you provided and I am gearing towards the "Linux Mint with the Cinnamon desktop." 

In the console I typed in [COLOR=#ff0000]sudo apt-get install cinnamon [/COLOR]and I got the following errors.

"[I]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: libcjs0e (>= 3.2.0-20170426020128) but it is not going to be installed
            Depends: cinnamon-screensaver (>= 3.4.0) but it is not going to be installed
            Depends: libcjs0-libmozjs-24-0
            Recommends: cinnamon-bluetooth but it is not installable
E: Unable to correct problems, you have held broken packages.[/I]"

From the error above, from what I am getting from it, is that I have to go and install a better version of libcjs0e and cinnamon-screensave

I don't get the error here in 16.04.
Did you add a cinnamon ppa?
Some packages may require removal which can be performed using **dist-upgrade**.

Run 
```
sudo apt install -f
sudo apt update
sudo apt dist-upgrade
```

---

### Post by 1jarwolf on 2017-06-25
[SIZE=5][COLOR=#00ff00][U][I][B]SOLVED.

[/B][/I][/U][/COLOR][/SIZE]&#8203;Thank you guys so much for fixing my problems! Much appreciated, really, THANK YOU! <3[SIZE=5][COLOR=#00ff00][/COLOR][/SIZE]

---

### Post by again? on 2017-06-26
****Good. \\:D/
FYI from the manual page of apt:
> **apt**
provides a high-level commandline interface for the package management system. It is intended as an end user interface and enables some options better suited for interactive usage by default compared to more specialized APT tools like apt-get(8) and apt-cache(8).
Much like apt itself, its manpage is intended as an end user interface and as such only mentions the most used commands and options partly to not duplicate information in multiple places and partly to avoid overwhelming readers with a cornucopia of options and details.

[INDENT]**update** (apt-get(8))
update is used to download package information from all configured sources. Other commands operate on this data to e.g. perform package upgrades or search in and display details about all packages available for installation.

**upgrade** (apt-get(8))
upgrade is used to install available upgrades of all packages currently installed on the system from the sources configured via sources.list(5). New packages will be installed if required to satisfy dependencies, but existing packages will never be removed. [COLOR="#FF0000"]If an upgrade for a package requires the remove of an installed package the upgrade for this package isn't performed.[/COLOR]

**full-upgrade** (apt-get(8))
full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.[/INDENT]

The command **apt**, generally can replace **apt-get** with more user friendly options. apt combines some of the functions of apt-get and apt-cache.
**apt full-upgrade** can be used instead of *[COLOR="#696969"]apt dist-upgrade[/COLOR]* or *[COLOR="#696969"]apt-get dist-upgrade[/COLOR]*
**apt policy** can be used instead of *[COLOR="#696969"]apt-cache policy[/COLOR]*


*P.S you can mark the thread as solved in "Thread Tools" at the top right.

---

### Post by vasa1 on 2017-06-26
See why you should mark your thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

