---
title: "Howto RhythmBox 0.95 Album Art &amp; Daap (share songs)"
date: 2006-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by amoore on 2006-06-21
[B][COLOR="Red"]This how to is out dated if you are using the current version of Ubunutu!!!
Edgy or newer
[/COLOR][/B]


RhythmBox is quickly chaching up to iTunes!!!! In the latest version, from source you can complie some of the new cool features that RhythmBox has.

These new features are:

1. Displays Album Art
2. DAAP song sharing (what iTunes uses to share) 

lets get started:

1. Download latest source code from [http://ftp.gnome.org/pub/GNOME/sources/rhythmbox](http://ftp.gnome.org/pub/GNOME/sources/rhythmbox). 
Get the .tar.gz version, and put it on the desktop.  Make sure you get the version .95 

Right click on the .tar.gz file on the desktop, and select "Extract Here".

2. If you don't already have build-essential and checkinstall, go to a terminal and type

[PHP]sudo apt-get install build-essential checkinstall
[/PHP]

3. Rhythmbox relies on the presence of a bunch of dev packages to compile with all the features. The following will do the trick (on a virgin Dapper-i386 install, this totals 77 packages including dependencies, taking 59 MB):
Code:

[PHP]sudo apt-get install libxml-parser-perl libgtk2.0-dev libgnomevfs2-dev libgnomeui-dev libtotem-plparser-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libnautilus-burn-dev libmusicbrainz4-dev libnotify-dev python2.4-dev python-gtk2-dev libsoup2.2-dev libgpod-dev check[/PHP]


4. Then, to compile and install, do this at the terminal 

During the sudo checkinstall just answer the questions asked or press enter if your unsure.

[PHP]cd ~/Desktop/rhythmbox-0.9.5 
./configure --enable-python --with-daap
make 
sudo checkinstall[/PHP]

5. Install avahi

[PHP]sudo apt-get install avahi-daemon[/PHP]

6. Run RhythmBox and set up Sharing

From the Applications menu

[I]Aplications> Sound and Video> RhythmBox  
[/I]
In RhythmBox 

From the Edit menu choose Preferences

*Edit> Preferences *

Click the Sharing tab

Mark Share my muisc

From the Edit menu choose Plugins

*Edit> Plugins *

mark Art Display

Your done!!!!! you can now see album art and share songs with RhythmBox!!!!

Credit of this how to should go to zeus77

---

### Post by PhrankDaChickenGeek on 2006-06-25
Thanks for the How-To! Everything works great!

---

### Post by mlind on 2006-06-25
I already made a HOWTO about this earlier which upgrades using official Debian
RB package and includes Launchpad integration

[http://www.ubuntuforums.org/showthread.php?t=200762](http://www.ubuntuforums.org/showthread.php?t=200762)

Looks good though.

---

### Post by oskvaz on 2006-07-10
Thanks!!! Works perfect.

---

