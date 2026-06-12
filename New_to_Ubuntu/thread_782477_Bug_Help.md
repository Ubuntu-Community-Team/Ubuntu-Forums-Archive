---
title: "Bug Help?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by skylinedna on 2008-05-05
I dont know where to report bugs but when i open update manager i get this

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--21:05:16--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'


And when i try sudo update
skylinedna@MISKNK:~$ sudo apt-get upgrade
E: Type '--21:05:16--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
skylinedna@MISKNK:~$ sudo apt-get update
E: Type '--21:05:16--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list


Can anyone help?

---

### Post by SunnyRabbiera on 2008-05-05
Well yes this is a good place to report a bug.
Did you follow the instructions on getting medibuntu?
did you get any issues before this?

---

### Post by Monicker on 2008-05-05
You have bad information in your medibuntu.list file.  It looks like somehow you got a timestamp from a download in the file itself.  I seem to recall someone else on the forum ran into that issue not long ago.

How did you retrieve medibuntu.list?

---

### Post by skylinedna on 2008-05-05
i dont know what medibuntu i was trying to get some issues with my dvds not playin properly. and then i gave up and since then this is whats happening

---

### Post by skylinedna on 2008-05-05
nstall this:
Quote:
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
Quote:
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
Quote:
sudo apt-get install w32codecs
Quote:
wget -c [http://packages.medibuntu.org/pool/f...untu4_i386.deb](http://packages.medibuntu.org/pool/f...untu4_i386.deb)
Quote:
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
Quote:
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
Quote:
sudo /usr/share/doc/libdvdread3/install-css.sh
Backup Dvds (in Add/Remove All Available Application)i:
Quote:
DVD::RIP and K9copy
EDIT: I think you have problem with video driver:

Quote:
In Mplayer Preferences> video> available drivers: x11
Restart player.
In Vlc Preferences> video> output module> x11



These where the instructions i was following when it stuffed up. i only got to number two and couldnt get any further cause it was saying invalid gpg format or something i cant recall sorry

---

### Post by SunnyRabbiera on 2008-05-05
ah, well the gpg key is important you know, always make sure to follow instructions on adding repositories to the letter.

---

### Post by Monicker on 2008-05-05
> **skylinedna said:**
> i dont know what medibuntu i was trying to get some issues with my dvds not playin properly. and then i gave up and since then this is whats happening

medibuntu is an external repository, which offers some packages which can't be included in Ubuntu repositories.  It would have to have been added manually.


The quick fix would be the following, from a terminal session:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list,
sudo apt-get update
```


After that the update manager should run normally.

If you really want to use the medibuntu packages, then follow the documentation carefully:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Sparkalo on 2008-05-05
Well, I concur with Moicker, it looks like a timestamp somehow got into the first line of your list.  Could you post the contents of your "/etc/apt/sources.list.d/medibuntu.list"?  It might be as simple as deleting the offending timestamp...but we won't know until we see it : P

---

### Post by skylinedna on 2008-05-05
oh k thank you update is working fine now. but im still having problems with getting dvds to play they get picked up by programms but the play all stuffed up should i try follow those medibuntu instructions again?

---

### Post by SunnyRabbiera on 2008-05-05
well the mediabuntu repositories wont immediately install things for you, so if you need DVD playback you have to go up to system then to administration and click on "synaptic package manager"
and make sure you hit that "refresh" button.
from there search for libdvdcss and install it, that should eliminate your DVD issues.

here is a good guide to get you started:
[here]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by skylinedna on 2008-05-05
i clicked reload and searched and nothing came up except libdvdread3 (installed) and ogle?

---

### Post by SunnyRabbiera on 2008-05-05
hmm, well also in synaptic go up to "settings" and to "repositories"
and make sure everything in the first tab is checked off except the source code button, and in the second tab also make sure things are checked off except for the source code repositories.
again hit refresh just in case...
and just in case search for "dvd" too and see if you can find the package, if you properly have the medibuntu repository added you should be able to see it.

---

### Post by skylinedna on 2008-05-05
i still cant find out how to do it i installed alot of gstreamer bits but still dvds not working and i tried what you said and still cant see libdvdcss

---

### Post by SunnyRabbiera on 2008-05-05
hmm, well open a terminal and put in this command: sudo apt-get update

---

### Post by skylinedna on 2008-05-05
I updated like you said  tryied to open totem to play a dvd and it cam up with this error 

Please install the necessary plugins and restart Totem to be able to play this media.

And the plugins in the totem menu are all installed but they are only infared remote and always on top plugin so yeah im at a loss to what to do now. i can play it through mplayer but only sound and its real broken   when i try rip using thoggen it just has a blue screen and does nothing.  but then some dvds will work but most dont

---

### Post by fbuchele on 2008-05-06
This is a completely different issue than the original one. Ubuntu, by default is not set up to allow you to play DVDs, for copyright reasons. 

Taken lovingly from [http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux:](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux:)

> DVD are usually encrypted and therefore, due to legal reasons, Ubuntu Linux does not ship the package which decrypt DVD.

However, Ubuntu offers an easy way to get this package install. This tutorial will show which packages have to be installed in order to get most multimedia applications to run under Ubuntu.

The default movie player on Ubuntu is Totem, a Gnome movie player based on GStreamer or xine. As GStreamer is the default library used with Totem, this tutorial will be focused on GStreamer backend.

To get started with the codecs, we are going to install all the GStreamer library packages available on the repository:

$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

From now on, you should be able to play any divx, non encrypted DVD and music.

In order to be able to play encrypted DVDs, we need to install libdvdcss2 package. As I said earlier, this package is not provided by Ubuntu for legal reasons. However, a script is supplied in order to easily install this package. This script is provided by libdvdread3 package.

Let's go back to the command line and, for people using Ubuntu Feisty 7.04 or Ubuntu Edgy 6.10, type:

$ sudo /usr/share/doc/libdvdread3/install-css.sh

People using releases prior to Edgy Eft, such as Ubuntu Dapper 6.04 will type:

$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh

People using Debian based distribution might have to use:

$ wget [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
$ sudo dpkg -i libdvdcss2_1.2.5-1_i386.deb

Now, libdvdcss2 is installed and that's it :), insert a DVD in your player, Totem should open up and the DVD start playing.

For the ultranoobs (i don't suggest doing this, read the above and get some knowledge): put this in the terminal: 

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Then it should work. However, I would suggest using ogle, 
```
sudo apt-get install ogle
```

Just because it automounts dvds and lets you use the menus. My player of choice.

---

