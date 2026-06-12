---
title: "HOWTO: easy mplayer for warty."
date: 2005-03-06
forum: Outdated Tutorials &amp; Tips
---

### Post by RastaMahata on 2005-03-06
Here's a little and easy howto for warty. I got a lot of help from this post: [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) and from [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) ;)

I think this is the best way to get mplayer running easily and fast. The only downside: xmms. I dont know why the hell you must have it, and I hope this gets fixed for hoary. Well, here we go.

> 
First of all, we're gonna update our whole ubuntu system. We should follow the following steps (Taken from [www.ubuntuguide.org](www.ubuntuguide.org)):

First, update your /etc/apt/sources.list:```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
$ sudo gedit /etc/apt/sources.list
```Delete the whole thing, and copy-paste this:```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe
```Now, we follow these steps:```
$sudo apt-get update
$sudo apt-get upgrade
```Now we are able to install the codecs, mplayer and the plugins. ;)

Open up a console and do this:```
sudo apt-get install manpages-dev autoconf automake libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev libgtk2.0-dev libdirectfb-0.9-20 libfaad2-0 libggi2 liblame0 libpostproc0 libsvga1 libxvidcore4 xmms gstreamer0.8-plugins w32codecs
```Then we get our hands dirty  :) .

Let's create a "work" folder in our home folder so we dont get our folders all messy:```
mkdir ~/work
```Now we change into that folder and download the corresponding version of mplayer for our CPU.

If you use warty, get mplayer from here:```
http://sh.nu/~crimsun/mplayer/
```For example, if you have a pentium 4, get the 686 version. For Athlon (XP), get k6 (as k7 is just a dummy package).

Download it to the recently created "work" folder.

Next, we will install it:```
cd ~/work
sudo dpkg -i mplayer-*
```Now we have mplayer. You can run the following command to run it:```
gmplayer
```Dont worry if it doesnt appear in your Multimedia menu, it will when you reboot your x server (by pressing ctrl+alt+backspace if you dont want to reboot your pc).

Now that we have mplayer running, close it :P, we will have to get the plugins. Unfortunately, the mplayer plugins for mozilla that ubuntu has just suck. So we will make our own (dont worry, it too easy).

First, get these files, and download them to your work directory!:```
http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.6/gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz
http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-2.70.tar.gz?download
```Now open a console and do this:```
cd ~/work
tar -xzvf gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz
tar -xzvf mplayerplug-in-2.70.tar.gz
cd mplayerplug-in
./configure --with-gecko-sdk=~/work/gecko-sdk
make
```Now, if you have firefox, do this:```
sudo cp ~/work/mplayerplug-in/mplayerplug-in.so /usr/lib/mozilla-firefox/plugins
sudo cp ~/work/mplayerplug-in/mplayerplug-in.xpt /usr/lib/mozilla-firefox/components
```And for the mozilla suite, do this:```
sudo cp ~/work/mplayerplug-in/mplayerplug-in.so /usr/lib/mozilla/plugins
sudo cp ~/work/mplayerplug-in/mplayerplug-in.xpt /usr/lib/mozilla/components
```Now close all your firefox/mozilla windows and open a new one. To test the plugin, go here:```
http://www.apple.com/trailers/
```And watch a trailer. Have fun! ;)

---

### Post by Phosphoros on 2005-03-07
Thanks for the mplayer tutorial.  I had some problmes though. 

When I got to the **make** command after grabbing the goodies for the plugins.  I had srolling errors out the wazoo.
Here is just a few I grabbed (there where so many I can't get them all).  This is just the tail end.  Have I neglected in getting something important to make them?

```
Source/plugin.cpp:1865: error: `embed_height' undeclared (first use this
   function)
Source/plugin.cpp:1866: error: `embed_width' undeclared (first use this
   function)
Source/plugin.cpp:1868: error: `window_height' undeclared (first use this
   function)
Source/plugin.cpp:1869: error: `window_width' undeclared (first use this
   function)
Source/plugin.cpp:1965: error: `NP_FULL' undeclared (first use this function)
Source/plugin.cpp:1978: error: `movie_height' undeclared (first use this
   function)
Source/plugin.cpp:1978: error: `movie_width' undeclared (first use this
   function)
Source/plugin.cpp: At global scope:
Source/plugin.cpp:2191: error: `PRBool' was not declared in this scope
Source/plugin.cpp:2191: error: `_retval' was not declared in this scope
Source/plugin.cpp:2192: error: variable or field `GetShowlogo' declared void
Source/plugin.cpp:2192: error: `int nsPluginInstance::GetShowlogo' is not a
   static member of `class nsPluginInstance'
Source/plugin.cpp:2192: error: syntax error before `{' token
Source/plugin.cpp:2197: error: parse error before `)' token
Source/plugin.cpp:2219: error: syntax error before `::' token
Source/plugin.cpp:2237: error: syntax error before `*' token
Source/plugin.cpp:2240: error: parse error before `*' token
Source/plugin.cpp: In member function `nsScriptablePeer*
   nsPluginInstance::getScriptablePeer()':
Source/plugin.cpp:2265: error: `NS_ADDREF' undeclared (first use this function)
Source/plugin.cpp: In member function `nsControlsScriptablePeer*
   nsPluginInstance::getControlsScriptablePeer()':
Source/plugin.cpp:2279: error: `NS_ADDREF' undeclared (first use this function)
make: *** [plugin.o] Error 1

```

Also, probably as a result of the error in **make** I'm getting these errors when I run....
```
sudo cp ~/work/mplayerplug-in/mplayerplug-in.so /usr/lib/mozilla-firefox/plugins
```
Here is the resulting error.....
```
cp: cannot stat `/home/tristan/work/mplayerplug-in/mplayerplug-in.so': No such file or directory
```

When I run....
```
sudo cp ~/work/mplayerplug-in/mplayerplug-in.xpt /usr/lib/mozilla-firefox/components
```
The result is.....
```
cp: cannot stat `/home/tristan/work/mplayerplug-in/mplayerplug-in.xpt': No such file or directory
```

I have obviously done something wrong or I don't have something important.
Any ideas?

Thanks

---

### Post by Dethread on 2005-03-07
The following worked for me to compile the firefox plugin:
```

cd ~/work
tar -xzvf gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz
tar -xzvf mplayerplug-in-2.70.tar.gz
sudo chown -R username *
cd mplayerplug-in
./configure --with-gecko-sdk=/home/username/work/gecko-sdk
make

```

Note that I first made myself the owner of all the extracted files (replace "username" with your username) and also specified the complete path to gecko.

---

### Post by Phosphoros on 2005-03-07
Yay!  Thank you Dethread!  That worked like a charm.
 :mrgreen:

---

### Post by A-star on 2005-03-17
[QUOTE=Phosphoros]Yay!  Thank you Dethread!  That worked like a charm.
 :mrgreen:[/QUOTE]
 Thanks for the guide, 
Mplayer works fine now in warty.

---

### Post by ldoria on 2005-03-21
Hi, as all newby in linux after many years as windows user I´ve had been some difficult to install some programs. In this moment the program in question is mplayer k7 for semprom2200. I found in some foruns here some explanations what about how to download and install it, but honestely I´ve try nut I couldn´t. Can some one give a step by step help???
Tks a lot

---

### Post by RastaMahata on 2005-03-22
[QUOTE=ldoria]Hi, as all newby in linux after many years as windows user I´ve had been some difficult to install some programs. In this moment the program in question is mplayer k7 for semprom2200. I found in some foruns here some explanations what about how to download and install it, but honestely I´ve try nut I couldn´t. Can some one give a step by step help???
Tks a lot[/QUOTE]
 well, you have the guide there.. and seeing you have a sempron, you should download the k6 version. (as the k7 version is a dummy one),

---

### Post by bored2k on 2005-03-22
[QUOTE=RastaMahata]well, you have the guide there.. and seeing you have a sempron, you should download the k6 version. (as the k7 version is a dummy one),[/QUOTE]
 I just reinstalled warty ... I just added marillat's repositories and got mplayer. What is wrong with this method ?

---

### Post by RastaMahata on 2005-03-23
[QUOTE=bored2k]I just reinstalled warty ... I just added marillat's repositories and got mplayer. What is wrong with this method ?[/QUOTE]
 err, as far as I know, marillat's mplayer gives you several problems with warty (dependancy problems, non existant packages in warty). I'll do a apt-get update/upgrade and see how it goes :S

edit:
It asks for:
libarts (>= 4:2.2.2-1) or libarts-alsa (>= 4:2.2.2-1), libdvdread2 and libvorbis0 (>= 1.0rc3-1), all are non-existant in warty.

---

### Post by sam.holland on 2005-03-24
[QUOTE=RastaMahata]Here's a little and easy howto for warty. I got a lot of help from this post: [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) and from [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) ;)

I think this is the best way to get mplayer running easily and fast. The only downside: xmms. I dont know why the hell you must have it, and I hope this gets fixed for hoary. Well, here we go.[/QUOTE]
 Thanks for the great tutorial.

I'm very new to Linux, and I'm having some dependency problems that are making me feel particularly clueless. I got this:

dpkg: dependency problems prevent configuration of mplayer-586:
 mplayer-586 depends on libdirectfb-0.9-20; however:
  Package libdirectfb-0.9-20 is not installed.
 mplayer-586 depends on libfaad2-0 (>= 2.0.0-0.1); however:
  Package libfaad2-0 is not installed.
 mplayer-586 depends on libggi2 (>= 1:2.0.4); however:
  Package libggi2 is not installed.
 mplayer-586 depends on liblame0 (>= 3.96.1-1); however:
  Package liblame0 is not installed.
 mplayer-586 depends on libpostproc0 (>= 0.90rc4); however:
  Package libpostproc0 is not installed.
 mplayer-586 depends on libxvidcore4 (>= 1:1.0.0-rc4-0.0); however:
  Package libxvidcore4 is not installed.
dpkg: error processing mplayer-586 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-686:
 mplayer-686 depends on mplayer-586; however:
  Package mplayer-586 is not configured yet.
dpkg: error processing mplayer-686 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mplayer-586

I followed every step to the letter. Any idea on what could be wrong?

Thanks!

---

### Post by TheEHMan on 2005-04-03
**When I run the upgrade, I get the following:**

$ sudo apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mplayer-586: Depends: libartsc0 (>= 1.3.2) but 1.2.3-1 is installed
               Depends: libasound2 (> 1.0.8) but 1.0.5-woody0.1 is installed
               Depends: libgcc1 (>= 1:4.0-0pre6ubuntu4) but 1:3.4.2-2ubuntu1 is installed
               Depends: libggi2 (>= 1:2.0.5) but 1:2.0.4-3 is installed
               Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is installed
               Depends: libogg0 (>= 1.1.2) but 1.1.0-1 is installed
               Depends: libpng12-0 (>= 1.2.8rel) but 1.2.5.0-7ubuntu1 is installed
               Depends: libsdl1.2debian (> 1.2.7+1.2.8) but 1.2.7-7 is installed               Depends: libungif4g (>= 4.1.3) but 4.1.0b1-6 is installed
               Depends: libxinerama1 but it is not installable
               Depends: libxxf86dga1 but it is not installable
               Depends: libxxf86vm1 but it is not installable
E: Unmet dependencies. Try using -f.

[B]
When I run upgrade again using -f, I get this:[/B]

Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  mplayer-586
The following packages have been kept back:
  hotplug mencoder-586
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7688kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 69850 files and directories currently installed.)
Removing mplayer-586 ...

After that, nothing.  I just can't seem to get mplayer installed.  I'm a newbie.  What am I doing wrong?

---

### Post by palsyboy on 2005-04-04
I'm getting errors similar to sam.holland's:

```

root@mrc:# sudo dpkg -i mplayer-686_1.0-pre6a-0.0_i386.deb
Selecting previously deselected package mplayer-686.
(Reading database ... 61195 files and directories currently installed.)
Unpacking mplayer-686 (from mplayer-686_1.0-pre6a-0.0_i386.deb) ...
dpkg: dependency problems prevent configuration of mplayer-686:
 mplayer-686 depends on mplayer-586; however:
  Package mplayer-586 is not installed.
dpkg: error processing mplayer-686 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mplayer-686

```
I'm fairly experienced with Gentoo and SuSE, but I don't yet understand Debian-based stuff.  What do I need to do to resolve the dependency?  Should I install mplayer-586, or could that break something?

---

### Post by RastaMahata on 2005-04-10
[QUOTE=palsyboy]I'm getting errors similar to sam.holland's:

```

root@mrc:# sudo dpkg -i mplayer-686_1.0-pre6a-0.0_i386.deb
Selecting previously deselected package mplayer-686.
(Reading database ... 61195 files and directories currently installed.)
Unpacking mplayer-686 (from mplayer-686_1.0-pre6a-0.0_i386.deb) ...
dpkg: dependency problems prevent configuration of mplayer-686:
 mplayer-686 depends on mplayer-586; however:
  Package mplayer-586 is not installed.
dpkg: error processing mplayer-686 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mplayer-686

```
I'm fairly experienced with Gentoo and SuSE, but I don't yet understand Debian-based stuff.  What do I need to do to resolve the dependency?  Should I install mplayer-586, or could that break something?[/QUOTE]
 sadly enough, seems that the author of the package updated it. there's nothing I can do about it now. Sorry for the delay :(

You could try hoary now, and instead of using gmplayer, give totem-xine a try (although you'll have to wait a bit for an official firefox plugin)

---

