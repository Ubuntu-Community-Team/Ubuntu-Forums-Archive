---
title: "Easiest way to Install Real Player"
date: 2005-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Brutal Ben on 2005-04-06
1) Download the version of RealPlayer thats prepackaged for Xandros Linux. Its a .deb package that works under Hoary.

[https://helixcommunity.org/download.php/949/RealPlayer-10.0.3-rc1-xandros3.i586.deb.tar.bz2](https://helixcommunity.org/download.php/949/RealPlayer-10.0.3-rc1-xandros3.i586.deb.tar.bz2) 

2) Uncompress the .tar.zp2 file to get realplay_10.0.2-1_i386.deb

3) Open a command line shell and cd into the directory that you saved the deb file, (default is ~/Desktop

4) Use Sudo to install the file: sudo dpkg -i realplay_10.0.2-1_i386.deb

Unfortunately as of this writing, Real Player conflicts with Enlightened Sound Daemon. You'll need to use gconf and set /desktop/gnome/sound/enable_esd to false (uncheck its box) to disable it. Reboot, and you should be all set.

If you disable ESD you can still use gstreamer by: setting/system/gstreamer/0.8/default/audiosink=alsasink

Hopefully in the near future ESD will not interfere with OSS applications, or gnome switches completely to ALSA which is mult-threading now.

---

### Post by Jad on 2005-04-06
Thank you
Helix can be installed but cant play .rm files

---

### Post by tanari on 2005-04-06
Why not use RealPlayer10?
[www.real.com](www.real.com)
download and launch .bin file (with sudo), very simple.

---

### Post by bored2k on 2005-04-06
[QUOTE=tanari]Why not use RealPlayer10?
[www.real.com](www.real.com)
download and launch .bin file (with sudo), very simple.[/QUOTE]
 Because sometimes the Player will just not open.

Xandros's RealPlayer is 10.0.2 [at least your link is], RP is on 10.0.3 now. And for anyone getting the anoying "it just won't open", disable the sound server and retry.

---

### Post by Brutal Ben on 2005-04-09
Note for Kubuntu users!
K
The package I mentioned doesn't seem to get along with Kubuntu (specifically kdelibs-data). My error log is:


dpkg -i realplay_10.0.2-1_i386.deb
Selecting previously deselected package realplay.
(Reading database ... 101551 files and directories currently installed.)
Unpacking realplay (from realplay_10.0.2-1_i386.deb) ...
dpkg: error processing realplay_10.0.2-1_i386.deb (--install):
 trying to overwrite `/usr/share/mimelnk/application/vnd.rn-realmedia.desktop', which is also in package kdelibs-data
Errors were encountered while processing:
 realplay_10.0.2-1_i386.deb

Real Player seems to be an odd sticking point for Ubuntu. I hope the hylix community can get Real player to support Esound and Alsa again!!  :-?

---

### Post by mesocool on 2005-04-09
[QUOTE=bored2k]Because sometimes the Player will just not open.

Xandros's RealPlayer is 10.0.2 [at least your link is], RP is on 10.0.3 now. And for anyone getting the anoying "it just won't open", disable the sound server and retry.[/QUOTE]

Yes, my realplay cannot open but I see it in the system monitor with sleeping status.. Why it's that? ](*,)

---

### Post by Jad on 2005-04-09
I think Hoary wont let realplayer run because it try to take the sound system for itself, and wont allow other application to use it at the same time.

---

### Post by fsman on 2005-04-09
My hoary system is uptodate and installing realplayer was simple just follow this

[http://www.elyps.de/guide.html#realplayer](http://www.elyps.de/guide.html#realplayer)

the important part is in english, so don't mind the .de

---

### Post by Gianni Exile on 2005-04-09
[QUOTE=fsman]My hoary system is uptodate and installing realplayer was simple just follow this

[http://www.elyps.de/guide.html#realplayer](http://www.elyps.de/guide.html#realplayer)

the important part is in english, so don't mind the .de[/QUOTE]
This work perfectly. thank you.

---

### Post by Brutal Ben on 2005-04-10
[QUOTE=mesocool]Yes, my realplay cannot open but I see it in the system monitor with sleeping status.. Why it's that? ](*,)[/QUOTE]

The source code to Hylix (and Real Player) does support ALSA, Esound, and Art. According to the developers the support for these 3 are too buggy, so they disabled the three during compiling. Any adventurest linux programmer with a nack for sound should sign up to help debug Helix. Make a .deb for us Ubuntu folks.  :wink:

---

### Post by iansealy on 2005-04-10
[QUOTE=Brutal Ben]Unfortunately as of this writing, Real Player conflicts with Enlightened Sound Daemon. You'll need to use gconf and set /desktop/gnome/sound/enable_esd to false (uncheck its box) to disable it. Reboot, and you should be all set.

If you disable ESD you can still use gstreamer by: setting/system/gstreamer/0.8/default/audiosink=alsasink

Hopefully in the near future ESD will not interfere with OSS applications, or gnome switches completely to ALSA which is mult-threading now.[/QUOTE]

Is there any way of getting RealPlayer and Music Player (AKA rhythmbox) to both work? I've followed the above instructions, but now Music Player gives the following error:

[CENTER]Internal GStreamer error: pad problem. File a bug.[/CENTER]

---

### Post by whatever on 2005-04-10
[QUOTE=tanari]Why not use RealPlayer10?
[www.real.com](www.real.com)
download and launch .bin file (with sudo), very simple.[/QUOTE]
alternative: get the rpm from real.com and convert it to .deb with alien

btw: to solve most sound problems setup alsa dmix for alsa:default device (read [here](http://alsa.opensrc.org/index.php?page=DmixPlugin)) and set everything's output to alsa - either directly or via aoss.
esd settings are in /etc/esound/esd.conf and don't forget to install "libesd-alsa0"; gstreamer settings can be changed in system->settings->multimedia-system

---

### Post by titus1950 on 2005-04-10
I have installed Real player finely............but it doesn't work.....,,,so 
somehow,this fixed it: Is like asking for a hamburger in a hardware store but it did the trick.......
System.....Preferences........Sound.......General.....(Uncheck....Enable sound server startup) 
Now maybe and only maybe some of us will enjoy some MULTIMEDIA


Good Luck.

---

### Post by dejitarob on 2005-04-10
[QUOTE=bored2k]Because sometimes the Player will just not open.[/QUOTE]Hm, I use RealPlayer10 to watch [www.democracynow.org]("http://www.democracynow.org") everyday on both of my boxes and have never experienced a problem. Could this be hardware-dependent or does it just happen in kubuntu?

---

### Post by iansealy on 2005-04-11
[QUOTE=dejitarob]Hm, I use RealPlayer10 to watch [www.democracynow.org]("http://www.democracynow.org") everyday on both of my boxes and have never experienced a problem. Could this be hardware-dependent or does it just happen in kubuntu?[/QUOTE]

I'm having problems with Ubuntu, not Kubuntu. Also, RealPlayer worked fine under Warty. I'm only having problems since upgrading to Hoary.

---

### Post by RastaMahata on 2005-04-11
well.. yeah, this .deb adds menu entries and stuff, but it doesnt integrate to firefox, and it creates a menu with broken links (besides broken icons).

I'll install the .bin now, I think :( I wish there was an ubuntu deb

---

### Post by Robban59 on 2005-04-14
Hi everybody,

being a newbie I also jumped in and installed the bin file downloaded from Real.com; the only thing is that I didn't change the directory when prompted, so it ended up installed in my /home/downloads directory.
Now I would like ti deinstall it and reinstall it in a proper directory, but how do I install it ? do I just delete the directory created during install under /home/downloads ? ....in Synaptic there is no trace of it of course...

Thanks in advance for helping a newbie like me...

---

### Post by dabang on 2005-04-15
I had no problems installing Realplayer from real.com. Just get the package from [here](http://www.real.com/linux/?rppr=rnwk&src=040104freeplayer), make it executable und go! If you say "no" to the question concerning the symbolic links (which I always do), I'd create a symbolic to the "realplay" executable in /usr/bin afterwards manually. If you do so, the shortcut in the KDE menu will work, too.
For example, if you installed RealPlayer in /usr/lib:
cd /usr/bin
sudo ln -s /usr/lib/RealPlayer/realplay

If you don't like the place where you installed it, it should be OK if you just delete the directory and have another try.

---

### Post by rsw on 2005-04-17
[QUOTE=Brutal Ben]1) Download the version of RealPlayer thats prepackaged for Xandros Linux. Its a .deb package that works under Hoary.

[https://helixcommunity.org/download.php/949/RealPlayer-10.0.3-rc1-xandros3.i586.deb.tar.bz2](https://helixcommunity.org/download.php/949/RealPlayer-10.0.3-rc1-xandros3.i586.deb.tar.bz2) 

2) Uncompress the .tar.zp2 file to get realplay_10.0.2-1_i386.deb

3) Open a command line shell and cd into the directory that you saved the deb file, (default is ~/Desktop

4) Use Sudo to install the file: sudo dpkg -i realplay_10.0.2-1_i386.deb
[/QUOTE]


If you have the "kdelibs-data" installed, step 4 will fail due to conflicting files. Whether you want to do this or not, here's a quick workaround which might break things (though judging by the file that is in conflict between both packages, i would say it wont break anything):

4b) sudo dpkg -i --force-overwrite realplay_10.0.2-1_i386.deb

It should install just fine :) Works for me with hoary, no other modifications or steps necessary. Just run it (from a terminal, the command is: realplay) and enjoy.

---

### Post by Gianni Exile on 2005-04-27
[QUOTE=titus1950]I have installed Real player finely............but it doesn't work.....,,,so 
somehow,this fixed it: Is like asking for a hamburger in a hardware store but it did the trick.......
System.....Preferences........Sound.......General.....(Uncheck....Enable sound server startup) 
Now maybe and only maybe some of us will enjoy some MULTIMEDIA


Good Luck.[/QUOTE]

To avoid conflicts, add to /etc/esound/esd.conf
```
default_options=-nobeeps -as 3
```

Which tells ESD to release to soundcard after 3 seconds of inactivity.

Here's my whole file 

~$ cat /etc/esound/esd.conf 
```
[esd]
auto_spawn=0   # don't autospawn - causes conflicts
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100

## default options are used in spawned and non-spawned mode
# don't beep on startup, release device after 3 secs
default_options=-nobeeps -as 3  

```

---

### Post by NeoChaosX on 2005-04-27
I made a how-to on [forcing RealPlayer to use ALSA](http://ubuntuforums.org/showthread.php?t=29586), for anyone interested.

---

### Post by N'Jal on 2005-04-28
Yeah after following that and all the links it points to i now have realplayer working ^_^ i can now watch all the Dr Who trailors from the BBC website now

---

### Post by pjkramer on 2007-02-12
sudo apt-get install realplayer

That is the easiest way by a long shot and it's now version 10.

---

### Post by MattParkins on 2007-06-12
> **pjkramer said:**
> sudo apt-get install realplayer

That is the easiest way by a long shot and it's now version 10.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


Any ideas?   If I download the linux version from realplayer and try to run it (having set it to execute obviously)

sh RealPlayer10GOLD.bin 
RealPlayer10GOLD.bin: 1: Syntax error: "(" unexpected

Any ideas on either?  I have some rmvbs I'd like to watch some day...

---

### Post by Bostonian on 2007-06-17
I have a post in the begginner area, but I have the same problem/different error. Thought it might help.

$ ls R*
RealPlayer10GOLD.bin
$ chmod a+x RealPlayer10GOLD.bin 
$ ./RealPlayer10GOLD.bin 
bash: ./RealPlayer10GOLD.bin: No such file or directory

---

### Post by mhg on 2007-07-15
I am using vmware + browser appliance.
Everything works great.

I tried first to install realplayer through the .deb but it didn't configure properly.

After that I downloaded and installed RealPlayer10GOLD.bin
chmod +x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin
choose everything default and everything is fine. 

I still cannot listen to some sites but that is the site problem.

---

### Post by linux4begin on 2007-11-23
Same error i m getting with  7.10

root@ashishbarot:/home/barot/Desktop# dpkg -i realplay_10.0.3-1_i386.deb 
Selecting previously deselected package realplay.
(Reading database ... 101830 files and directories currently installed.)
Unpacking realplay (from realplay_10.0.3-1_i386.deb) ...
dpkg: error processing realplay_10.0.3-1_i386.deb (--install):
 trying to overwrite `/usr/share/mimelnk/application/vnd.rn-realmedia.desktop', which is also in package kdelibs-data
Errors were encountered while processing:
 realplay_10.0.3-1_i386.deb
root@ashishbarot:/home/barot/Desktop

Can anyone help me for this?

Thanks.
With Regards,
Ashish Barot.

[www.linux4beginners.info](www.linux4beginners.info)

---

### Post by kevinmoire on 2008-05-05
> **Brutal Ben said:**
> The source code to Hylix (and Real Player) does support ALSA, Esound, and Art. According to the developers the support for these 3 are too buggy, so they disabled the three during compiling. Any adventurest linux programmer with a nack for sound should sign up to help debug Helix. Make a .deb for us Ubuntu folks.  :wink:

SUPPORT!@!@

---

### Post by r41d3r on 2008-07-14
Thanx.

---

