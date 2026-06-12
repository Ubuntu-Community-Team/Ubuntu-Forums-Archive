---
title: "[SOLVED] Banshee codec issue"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by MinderBinderNW on 2008-08-05
So this is my first time using Linux and I got it up and running.  I've been using the apt to get some things done and its worked well.  But then I ran into a problem with banshee.  It didnt have any codecs.  So I downloaded all of them, but then I got some license agreement for Java in the terminal and I couldn't figure out how to click ok.  So eventually I just tried to do it in the add/remove section of third party applications, but it said 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

And when I entered it in the terminal it said I must be a super user.  I am the only account on this computer.  And I am at a loss.  The version is 7.04.

Thanks.

---

### Post by northern lights on 2008-08-05
> **MinderBinderNW said:**
> And when I entered it in the terminal it said I must be a super user.
Well, run it as such using```
sudo dpkg --configure -a
```followed by your regular password.

As far as codecs are concerned:
If you're talking about banshee, you most likely wanted to play .mp3 files, right?
mp3 support is gained via the package 'ubuntu-restricted-extras'.
For wma/wmv you have to enable '[medibuntu]("https://help.ubuntu.com/community/Medibuntu")'

---

### Post by LowSky on 2008-08-05
sudo dpkg --configure -a

sudo apt-get install ubuntu-restricted-extras

and medibuntu for anything else

---

### Post by MinderBinderNW on 2008-08-05
yeah.  that was a hit myself over the head moment.  i managed to figure it out just after i posted.

but now it says this.

ryan@ryan-laptop:~$ sudo dpkg --configure -a
Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...
 
and then it goes back to the regular command line.  codecs still dont work.  but yeah mp3s mostly.  some aac.

thanks

---

### Post by MinderBinderNW on 2008-08-05
low sky.  this is what came up when i put the get ubuntu thing
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-00-2ubuntu2) but it is not going to be installed
  ubuntu-restricted-extras: Depends: gstreamer0.10-plugins-ugly but it is not going to be installed
                            Depends: gstreamer0.10-plugins-ugly-multiverse but it is not going to be installed
                            Depends: msttcorefonts but it is not going to be installed
                            Depends: flashplugin-nonfree but it is not going to be installed
                            Depends: sun-java6-plugin but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by LowSky on 2008-08-05
I would run what it says
sudo apt-get -f install

also what happens if you try to install these packages from Add/Remove or Synaptic?

---

### Post by northern lights on 2008-08-05
Okay.

dpkg was never meant to fix the codec issue. It configured all unpacked packages but unconfigured packages.
It unpack the configuration files, back-ups the old configuration files and runs a postinst script, if provided by the package.

As for the codes:

Navigate to "System > Administration > Software Sources". Enable all repositories but 'proposed' and 'backports'.

Adding medibuntu:```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Update (synchronize index files w/ sources), install public keyring, update again```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

For DVD playback, run
```
sudo apt-get install libdvdcss2
```

For wma/wmv support, which is now possible with medibuntu enabled, run```
sudo apt-get install w32codecs
```

For mp3 support, run```
sudo apt-get install ubuntu-restricted-extras
```

For video/flash web content run```
sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer flashplugin-nonfree
```

[EDIT]
Latest persisting problem came up while posting.
Obviously, unmet dependencies need to be resolved first.
[/EDIT]

---

### Post by MinderBinderNW on 2008-08-05
good call.  i guess i mistyped that one the first time.  Add/Remove said to run the dpkg thing in apt.  but now Im back to square one where I got into this whole mess.  Im looking at the license agreement in apt, and i cant figure out how to get past it.  ive scrolled up and down.  hit enter. typed yes.  any ideas?

---

### Post by LowSky on 2008-08-05
just type y hit enter

---

### Post by MinderBinderNW on 2008-08-05
tried that.  it just has the agreement and  <ok>  I cant type anything anywhere.

---

### Post by northern lights on 2008-08-05
For that issue purge everything first```
sudo apt-get purge un-java6-bin sun-java6-jre ubuntu-restricted-extras gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse msttcorefonts flashplugin-nonfree sun-java6-pl
```

---

### Post by LowSky on 2008-08-05
do me a favor with that window open hit the PrintScreen button on your keyboard and then take the file it creates and post it here

---

### Post by MinderBinderNW on 2008-08-05
i attached an image of it.

---

### Post by LowSky on 2008-08-05
LOL... hit the TAB key it should highlight it

---

### Post by MinderBinderNW on 2008-08-05
yeah.  i knew it had to be something simple.  it was pretty infuriating.  thanks

---

### Post by LowSky on 2008-08-05
Your welcome... and it Happens to the best of us.. dont forget to mark the tread as solved (under thread tools at the top of the page)

---

