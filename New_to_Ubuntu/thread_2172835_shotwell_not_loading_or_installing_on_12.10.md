---
title: "shotwell not loading or installing on 12.10"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by shaikh-m on 2013-09-06
Hello, I have been using Ubuntu 12.10 and only recently noticed that shotwell doesnt appear to run.

I uninstalled it via the "Ubuntu Software Centre", however, since then, I am unable to reinstall via UBC or using terminal and receive the errors below

1. Via Ubuntu Software Centre


[IMG]http://i.imgur.com/Mf2nivn.png[/IMG]

[IMG]http://i.imgur.com/W0OJl41.png[/IMG]


[IMG]http://i.imgur.com/kadZP6W.png[/IMG]

[IMG]http://i.imgur.com/yUqql0i.png[/IMG]

[IMG]http://i.imgur.com/yY1IdgA.png[/IMG]

[IMG]http://i.imgur.com/LKeevrT.png[/IMG]

2. Via Terminal

```
[COLOR=#555555][FONT=monospace]sudo add-apt-repository ppa:yorba/ppa[/FONT][/COLOR]
[COLOR=#555555][FONT=monospace]sudo apt-get update[/FONT][/COLOR]
[COLOR=#555555][FONT=monospace]sudo apt-get install shotwell[/FONT][/COLOR]
```

receiving the following output

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 shotwell : Depends: libgee-0.8-2 (>= 0.8.3) but 0.8.0-0ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I have also tried the following but no joy.

```
sudo apt-get -f install
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

that didnt work so tried the following


```
sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```
but none of the above worked.. :(

any ideas please? (apologies if i've missed any details, or posted in the wrong section - please do let me know)

thank you!

---

### Post by newb85 on 2013-09-06
Hmm...seems to be a problem with the dependencies listed for the shotwell package in the yorba ppa.  Shotwell in the repos for Raring is also 0.14.1, but it depends on libgee2 instead of libgee 0.8 (which is in the Raring repos, but not the yorba PPA).

---

### Post by shaikh-m on 2013-09-06
Thanks for the prompt response newb85! umm.. does this mean, it is an issue with yorba ppa rather than my current install of 12.10? or should i perhaps look to install an alternate ppa to allow a complete install or just upgrade to 13.04? (sorry, i'm still rather green and just about getting my head around understanding linux/ubuntu) or maybe a different approach? :?

thanks!

---

### Post by newb85 on 2013-09-06
I guess my first question is whether you specifically need Shotwell 0.14.1, or if the one in the repos for Quantal is sufficient.  I would first remove the yorba ppa and try installing shotwell from the repositories.

Upgrading to Raring isn't a bad idea, but it's probably overkill.  Moreover, 13.04 hits End-of-Life January 2014, while 12.10 doesn't hit EOL until April 2014.  (Ubuntu shortened the non-LTS life cycle from eighteen to nine months with 13.04.)  It's not a huge difference time wise, but 12.10 will last until 14.04 (LTS) is released, and 13.04 won't.

---

### Post by shaikh-m on 2013-09-07
well, I was after a simple photo manager with some editing options; looking around, shotwell seems to have received the better feedback (GIMP is a bit overkill for my use) and look easy on the eye!

Currently, i use Geary which uses yorba ppa, so unsure if i remove the yorba PPA, will i still be able to install via the repositories via Ubuntu Software Centre, as at present shotwell wont even install via software centre (unless you mean another method perhaps?)

Completely agree about the upgrade; I have been putting off upgrading until 14:04, as 12.10 has been solid for me.

---

### Post by newb85 on 2013-09-07
If you still have the yorba PPA set up on your system, Software Center will try to install Shotwell (and Geary) from there, as it's a newer version than in the Quantal Repos.

Note: if you open SC and click the little down arrow next to the "All Software" button, you can filter the software by source to see what's going on.

Geary and Shotwell are both in the repos, so I would try doing without the yorba PPA.

---

### Post by shaikh-m on 2013-09-07
i've tried that now, deleted the yorba ppa via SC - Geary re-installed fine. Shotwell also installed, but will not launch. It seems to be bit little bit further than i was! 

should i try an alternate method to remove the ppa, not sure is that would help (i did this via SC)

---

### Post by newb85 on 2013-09-07
Have you tried launching shotwell from the terminal to see if there are any error messages?

---

### Post by shaikh-m on 2013-09-07
launching from terminal i receive the below

```

shotwell: error while loading shared libraries: libgexiv2.so.1: cannot open shared object file: No such file or directory 

```

however geary launches fine via both terminal and shortcut (geary version is older as expected 0.2.1)

slightly baffled, as shotwell now appears on unity but just will not launch

---

### Post by newb85 on 2013-09-07
Try this:
```
sudo apt-get remove shotwell
sudo apt-get purge libgexiv2-0
sudo apt-get install shotwell
shotwell
```

---

### Post by shaikh-m on 2013-09-08
ok, just tried it,

appears to uninstall ok,
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  shotwell
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 6,726 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 217344 files and directories currently installed.)
Removing shotwell ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for libglib2.0-0:i386 ...



```

however on purge

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libgexiv2-0' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

install seems fine

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  shotwell
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/2,304 kB of archives.
After this operation, 6,726 kB of additional disk space will be used.
Selecting previously unselected package shotwell.
(Reading database ... 217181 files and directories currently installed.)
Unpacking shotwell (from .../shotwell_0.13.1-0ubuntu1_amd64.deb) ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Setting up shotwell (0.13.1-0ubuntu1) ...

```



after i try launch via terminal, receive the below

```
shotwell: error while loading shared libraries: libgexiv2.so.1: cannot open shared object file: No such file or directory



```

---

### Post by newb85 on 2013-09-08
Oops, sorry, my source was apparently outdated.  Let's try again.
```
sudo apt-get remove shotwell
sudo apt-get purge libgexiv2-0 libgexiv2-1 libgexiv2-2
sudo apt-get install shotwell
shotwell
```

---

### Post by shaikh-m on 2013-09-08
ok, this is output 

```

sudo apt-get purge libgexiv2-0 libgexiv2-1 libgexiv2-2


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libgexiv2-0' is not installed, so not removed
E: Unable to locate package libgexiv2-2

```

and on the run

```
shotwell: error while loading shared libraries: libgexiv2.so.1: cannot open shared object file: No such file or directory

```

---

### Post by newb85 on 2013-09-08
Is shotwell automatically installing libgexiv2-1?

```
sudo dpkg --status libgexiv2-1
```

---

### Post by shaikh-m on 2013-09-08
well not sure really, output

```

Package: libgexiv2-1
Status: install ok installed
Priority: extra
Section: libs
Installed-Size: 151
Maintainer: Jim Nelson <jim@yorba.org>
Architecture: amd64
Source: gexiv2
Version: 0.6.1+109~quantal1
Replaces: libgexiv2-0
Depends: libc6 (>= 2.14), libexiv2-12, libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.24.0), libstdc++6 (>= 4.6)
Conflicts: libgexiv2-0
Description: GObject-based wrapper around the Exiv2 library
 gexiv2 is a GObject-based wrapper around the Exiv2 library. It makes the basic
 features of Exiv2 available to GNOME applications.
Homepage: http://redmine.yorba.org/projects/gexiv2/wiki

```

---

### Post by newb85 on 2013-09-09
> **shaikh-m said:**
> 
```

Status: install ok installed

```

Yes, it's installed.  I'm at a loss as to why that file was not created on installation.

---

### Post by shaikh-m on 2013-09-10
thanks for your patience newb85, I really appreciate your help.

I think i'll leave it for now, and will give pinta or fspot a try!

For the benefit of any others that may be experiencing similar issue, whilst googling about, I came across two bugs reported on yorba, [http://redmine.yorba.org/issues/6618](http://redmine.yorba.org/issues/6618) and [http://redmine.yorba.org/issues/5965](http://redmine.yorba.org/issues/5965) (I did attempt the workarounds but hasn't worked me, so hope it brings others some joy...)

---

