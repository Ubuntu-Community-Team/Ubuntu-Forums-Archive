---
title: "Get Me Familiar with Kubuntu"
date: 2015-04-16
forum: New to Ubuntu
---

### Post by janolcja5 on 2015-04-16
Hi!

I'm a new Linux user. I love Linux. 

Can you someone tell me the meaning of "apt-get" which is used in 'Konsole'? and where can I find the rest of the commands? I want to be adept at doing commands.


[LIST]
[*]I'm trying to download Deluge, and I don't know what to next with this [page]("http://dev.deluge-torrent.org/wiki/Download"). I'm using _Kubuntu_. Which 1 do I download? Ubuntu, Debian, Fedora, or which? 
[*]How do I know the version of my Kubuntu? 
[*]How can I uninstall a software? 
[/LIST]

---

### Post by kc1di on 2015-04-16
First place to start understanding apt-get is[ here.]("https://help.ubuntu.com/community/AptGet/Howto")
You'll also want to be familiar with the dpkg command . Start [here. ]("http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php")
Synaptic and muon are graphical front ends for dpkg and apt.  Happy learning. 

to find out the version of kubuntu your running type the following comand in a terminal```
cat /etc/*release
```
you get a display that looks similar to this:

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
NAME="Ubuntu"
VERSION="14.04.2 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.2 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

as you can see I'm running ubuntu 14.04.2 LTS

you can uninstall programs /packages in several ways - you learn as you learn the above commands.
Welcome to Linux /kubuntu and ubuntu :)

---

### Post by mastablasta on 2015-04-16
you can use
```
man *command*
``` to see what command does. man command displays a manual page for the command.

I believe Deluge is using GTK (Gnome). if you are downloading from web (not necessary) you download file made for Ubuntu.
KDE torrent is Ktorrent.

[LIST]
[*]you can install both by opening muon software manager (it's called Muon discover or something like that in newer version) and installing them. if oyu can't find it press alt+F2 and start typing muon... it will offer it.
[/LIST]
 

[LIST]
[*]the version is in system information. I am on windows now but ksysguard probably also has it. in Konsole you do it by typing ```
uname -a
```
[/LIST]
 

[LIST]
[*]you uninstall software by opning Muon Software manager / Discover, selecting the software you want to remove and then click uninstall.
[/LIST]

of course there are other option such as CLI option or package manager etc. etc..

to start you off with command line check the free e-book at linuxcommand.org

---

### Post by SeijiSensei on 2015-04-16
Unless you have a strong commitment to Deluge, I'd suggest using either KTorrent or Transmission.  I use the latter on my Kubuntu system since it seems a bit more "lightweight" than KTorrent.

If you want to download Deluge, either find it in the Software Center (main menu > System > Software Center) or open an instance of Konsole from the menu, then type "sudo apt-get install deluge".  Enter your password when prompted.  For Transmission, use "sudo apt-get install transmission".

Transmission is a "GTK" application that uses different methods to display objects on the screen than Kubuntu with KDE does.  KDE has special settings that govern the appearance of GTK apps.  If the default appearance of Transmission looks unattractive, take a look at System Settings > Application Appearance > GTK.

---

### Post by kc1di on 2015-04-16
Ktorrent should already be installed in kubuntu, but transmission works well with it also. Deluge should be in the repository also so there would be no need to download it from the web.

Go to moun and do a search for it.  moun is a frontend for apt and you can install it from there. 

it's always better to install from the official repository than down load a program from the web.  but if you wanted to anyway you would download the ubuntu or debian file.  it should have a .deb extension.  you can install it by right clicking on the downloaded .deb file and selecting install with QApt. 

You may also want to join the kubuntu forums found [here.]("https://www.kubuntuforums.net/forum.php") There are a lot of kind folks there that have more specific kubuntu knowledge.  Enjoy as you learn :)

---

### Post by SeijiSensei on 2015-04-17
> **kc1di said:**
> Go to moun and do a search for it.  moun is a frontend for apt and you can install it from there.
It's "muon" actually, and you can find it from Main Menu > Applications > System > Software Center.

---

### Post by Lars Noodén on 2015-04-17
> **janolcja5 said:**
> Can you someone tell me the meaning of "apt-get" which is used in 'Konsole'? and where can I find the rest of the commands? I want to be adept at doing commands.

Welcome.  As mentioned, the place to start would be the manual pages and then from there follow to the web for guides and howtos or ask here.  Each program has a manual page but they can and do vary in quality.   See *man ls* for all the details of the program *ls*.  As for the rest of the programs (aka commands) you can find them in /bin, /sbin, /usr/bin, /usr/sbin and sometimes also /usr/local/bin and /usr/local/sbin

One of the coolest, IMHO, and useful capabilities is to chain program output together and even make scripts.  As an example of what it can do, I'll leave this gordian knot for you:

```

for i in /bin/*; 
do \
  man $(basename $i) 2>/dev/null \
  | head -n 6 \
  | grep -m 1 ' - ' \
  | sed 's/^  *//' ; 
done  | sort -u |  less

```

It uses man, basename, head, grep, sed, sort and less.  The backslash \ means continued on the next line.  The semicolon ; means end of a statement.  

There are some good tutorials out there for shell scripting, both bash and the other shells.  For shell scripting, Bash in particular, these are useful:

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by uxbal on 2015-04-18
+ I wouldn't recommend Deluge as much as I would QBittorrent, since you seem to run KDE. That one's unbeatable!

---

