---
title: "HOWTO: Enable prelink"
date: 2004-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2004-10-24
Prelink is in universe. I use it on my Ubuntu system without issues, but do google about Prelink and do your research before trying it out.

**How to enable prelink:**

1. Activate Ubuntu universe sources. The procedure is well-documented by Ubuntu.
2. use apt-get or synaptic to install **prelink**.
3. Open /etc/default/prelink with your favorite editor, as sudo/root.
4. Change PRELINKING=unknown from unknown to yes.
5. Adjust the other options if you know what the heck you're doing. Defaults work well.
6. To start the first prelink (the longest one!), run **sudo /etc/cron.daily/prelink**

In the future, prelink performs a quick prelink (a less-than-1-minute procedure on most systems) daily, usually at midnight. Every 14 days, or whatever you changed it to be, a full prelink will run.

If you just did a major apt-get upgrade that changed systemwide libraries (i.e. libc6, glibc, major gnome/X libs, etc etc etc) and experience cryptic errors about libs, rerun step 6.

To undo prelink, change step 4 from yes to no, then rerun step 6.


**WARNING:**
An amd64 users in another thread ([http://ubuntuforums.org/showpost.php?p=134433&postcount=16](http://ubuntuforums.org/showpost.php?p=134433&postcount=16)) reports having experienced trouble with AMD64 prelinking. I have NOT tried prelinking on anything other than an i386!

---

### Post by wallijonn on 2005-01-16
Man, I was looking for this link the longest. Good stuff.

---

### Post by Tichondrius on 2005-01-18
Cool, that seems to work, a few executables and libraries seem to have been updated. But how much of a performance boost is this, and how can it be measured ?

---

### Post by Technoviking on 2005-01-18
Great how-to.
Thanks

---

### Post by Rene_S on 2005-03-10
Cool, I learn something new everyday.  Thanks for the Howto.

---

### Post by bored2k on 2005-03-10
[QUOTE=Rene_S]Cool, I learn something new everyday.  Thanks for the Howto.[/QUOTE]
 How many hours would prelinking last on a 15gb drive?40gb?
Can I use my PC on this period?

---

### Post by Xian on 2005-03-10
[QUOTE=bored2k]How many hours would prelinking last on a 15gb drive?40gb?
Can I use my PC on this period?[/QUOTE]
- It took me under 5 min on a 15GB partition with my AthonXP 3200.
- You can easily still use your computer.

---

### Post by bored2k on 2005-03-11
[QUOTE=Xian]- It took me under 5 min on a 15GB partition with my AthonXP 3200.
- You can easily still use your computer.[/QUOTE]
 thanks, I was a little scared as I basically eat off it  and my communication with the world outside my parking lot lies on Noir -thats her name...pretty sexy.

---

### Post by Xian on 2005-03-14
[QUOTE=jdong]To start the first prelink (the longest one!), run **sudo /etc/cron.daily/prelink**[/QUOTE]
What it the difference between running this and issuing the command?: 

# sudo nice -15 prelink -Rmvaf

---

### Post by jdong on 2005-03-15
the cron scripted prelink is more Debian oriented. At heart, it certainly calls the command you mentioned. However, it redirects output to a logfile in /var/log, allows incremental prelinking, and performs more "civilized" goodies.

---

### Post by Fintan on 2005-03-23
Thanks for the howto.
I'm newbe with ubuntu. So this may seem a stupid question:
After install prlink and setting everything in the /etc/defaults/prelink
and running: sudo /etc/cron.daily/prelink
the terminal daes not schow me any status as in "prelink successfull" or anything like that.
And the apps run just as slow as before.
Am i doing something wrong?

Sys:
PII 450 Mhz
296 Ram
392 Swap
Ubuntu 5.04 Pre

Any help would be appreciated.
Fintan

---

### Post by CowPie on 2005-03-25
[QUOTE=Fintan]Thanks for the howto.
I'm newbe with ubuntu. So this may seem a stupid question:
After install prlink and setting everything in the /etc/defaults/prelink
and running: sudo /etc/cron.daily/prelink
the terminal daes not schow me any status as in "prelink successfull" or anything like that.
And the apps run just as slow as before.
Am i doing something wrong?

Sys:
PII 450 Mhz
296 Ram
392 Swap
Ubuntu 5.04 Pre

Any help would be appreciated.
Fintan[/QUOTE]
the terminal daes not schow me any status as in "prelink successfull" or anything like that.

Same thing happened here...
with hoary

---

### Post by kagou on 2005-04-10
I'v tested

Before:
boot->gdm 112s
gdm->gnome: 22s
openoffice writer:15s
firefox:5s

After:
boot->gdm 109s
gdm->gnome: 22s
openoffice writer:12s
firefox:5s

AMD64 3400+ hoary (32bits)

---

### Post by underworld on 2005-04-10
[QUOTE=Fintan]
And the apps run just as slow as before.
[/QUOTE]

Prelink does only speed up the load process of an application.

---

### Post by Buffalo Soldier on 2005-04-10
Are there any drawbacks in enabling prelink? If yes, what are they?

---

### Post by Leif on 2005-04-10
I realize that this is just my system, and it works fine for everyone else, but prelinking crashes my system (then again, it seems a bit temperamental today, which is weird). The first time I tried it it crashed, but I decided not to be deterred. So I went again. It crashed again, taking dbus-launch with it. Nothing a reinstall of the relevant app didn't fix, but for some reason prelinking and my system don't like eachother, so I guess I'll just have to live with the slower startups.

---

### Post by jdong on 2005-04-10
[QUOTE=Buffalo Soldier]Are there any drawbacks in enabling prelink? If yes, what are they?[/QUOTE]

After major system updates, like library updates, you must remember to start a prelink. Else, you might get quirky/unstable behavior.

---

### Post by kuleali on 2005-04-12
Thank you,  it worked without problem

---

### Post by 23meg on 2005-04-12
does this howto apply exactly to Hoary?  

when i type sudo /etc/cron.daily/prelink at the terminal the hd spins wildly for about 10 minutes (first prelink; subsequent ones were shorter) and then the bash prompt reappears, but the drive keeps working for a few more minutes. is this normal?

---

### Post by mrbass on 2005-04-13
[QUOTE=Leif]I realize that this is just my system, and it works fine for everyone else, but prelinking crashes my system [/QUOTE]

I've had various problems doing a universal prelink in other distros. I wouldn't recommend it prelinking your whole system.  Even though Yoper does it if you examine it it has special ld_library paths or whatever, etc.  I'd say about 75% of apps in mac os x are 'prebinded'. 

I do, however, recommend prelinking **Openoffice** as it'll cut down the load times in half.  Instead of 15 seconds to load OpenWriter, for instance, it'll only take 7 seconds. Sure you can have that openoffice thing load on start but that'll waste memory resources if you don't use it all the time.

[b]sudo apt-get install prelink
sudo /usr/sbin/oooprelink -f[/b]

---

### Post by LokiAs2 on 2005-04-14
I wonder if it works for me. I haven't noticed any boost. Please check my log.

---

### Post by snop on 2005-04-14
[QUOTE=mrbass]
I do, however, recommend prelinking **Openoffice** as it'll cut down the load times in half.  
[b]sudo apt-get install prelink
sudo /usr/sbin/oooprelink -f[/b][/QUOTE]

I've tried to prelink openoffice and I don't get any startup time improvement (sorry, no measures). Perhaps it's because of my slow hd (I'm running ubuntu on a laptop).

SnOp

---

### Post by kiwibird on 2005-04-18
I'm trying the prelink stuff now..but I've got some questions though:

* Does the openoffice prelink have to be run in addition to the /etc/cron.daily/prelink one, or is it included in it?

* If my computer crashes or something during a prelink session, will Bad Stuff happen?

* If I want to uninstall it later, can I just use synaptic or is there something else that needs to be done first, to "unprelink"?

---

### Post by jdong on 2005-04-18
[QUOTE=kiwibird]I'm trying the prelink stuff now..but I've got some questions though:

* Does the openoffice prelink have to be run in addition to the /etc/cron.daily/prelink one, or is it included in it?

* If my computer crashes or something during a prelink session, will Bad Stuff happen?

* If I want to uninstall it later, can I just use synaptic or is there something else that needs to be done first, to "unprelink"?[/QUOTE]

1. No --  oooprelink just prelinks Openoffice (quicker than full prelink). Full prelink prelinks EVERYTHING, including OOo.

2. Nothing bad will happen. Prelink writes its files in a "libname.#PRELINK" format temp file before overwriting the original. Assuming you have an atomic or journaling filesystem (Ext3, XFS, JFS, ReiserFS, Reiser4, etc etc etc), a file will  either be prelinked or not, with no semi-prelinked stage in between ;)

3. You should read the man page for Prelink, specifically the "Undo" option ;)

---

### Post by iNs4ne on 2005-05-12
Prelinking Openoffice worked great, much faster loading now! (about 2x  :grin: )

Cheers

---

### Post by equilibrium on 2005-05-27
nice :)

I had used prelink in gentoo and it made load times a lot faster. Nice how-to.

I edited the  /etc/default/prelink file and changed

PRELINK_OPTS=-mR
to
PRELINK_OPTS=-avmfR

then ran "prelink -avmfR"

---

### Post by nlogax on 2005-06-03
I prelinked OOo on my system about a month or two ago.  Recently I started seeing errors like the ones I've quoted at the foot of this post when running the Ubuntu update application - I guess this was because the updater had installed a newer version of OpenOffice.org-bin and I hadn't forced prelink to run again before the next update to OpenOffice.org-bin.

Here are the steps I went through to fix it:

1) reinstalled OpenOffice using Synaptic
2) disabled all prelinking in Ubuntu (prelink state was 'Unknown' in /etc/default/prelink, so I changed it to no and ran 'sudo prelink -ua' to effect the change)
3) another OOo reinstall - still broken
4) disabled OOo prelinking using 'sudo /usr/sbin/oooprelink -f'
5) another OOo reinstall - still broken
6) someone's web suggested uninstall first and then reinstall of OOo - this also didn't fix it
7) read through some files and found reference to a file '/var/state/openoffice/ooo_is_prelinked' and deleted it
8) reinstalled OOo successfully!

All of the above MAY have been unnecessary if I'd just re-pre-linked OOo; I'm not sure.  Anyway, it looks as if for some reason, the scripts which manage and check the state of '/var/state/openoffice/ooo_is_prelinked' aren't always doing their thing.

As an aside, does anyone know how much (if any) prelinking is configured after a standard Ubuntu install?  From some comments on this thread it would seem there is none, but I want to be sure.

Here are the errors I was seeing:
[quote=Synaptic Errors]E: openoffice.org-bin:  subprocess post-installation script returned error exit status 1
E: openoffice.org-gtk-gnome:  dependency problems - leaving unconfigured
E: openoffice.org:  dependency problems - leaving unconfigured

Setting up openoffice.org-bin (1.1.3-8ubuntu2.3) ...
Undoing prelinking of OpenOffice.org binaries... run-parts: /usr/share/openoffice.org-debian-files/hooks/postinst.d/prelink exited with return code 1
dpkg: error processing openoffice.org-bin (--configure):
 subprocess post-installation script returned error exit status 1[/quote]

---

### Post by mohaham on 2005-06-18
awesome.... Thanks for this HOWTO.

---

### Post by Rinnan on 2005-07-08
Note that this has a far more profound impact on KDE than on Gnome, as I remember from my Gentoo days.

EDIT:  Okay just put it in for the first time in Ubuntu.  It is every bit as effective as as it was on Gentoo.  It makes a HUGE difference on my machine.  I think it makes a bigger difference on slower machines (such as mine).

Konqueoror takes about one fifth of a second to start up after it's already in the cache, whereas before it took two full seconds even after being in the cache.

---

### Post by Xian on 2005-08-01
Is there a way to edit the /etc/default/prelink file to include a nice setting.
It seems to run at a default NI level of 19 and I'd like to knock that down some.

Seems like it would go in the PRELINK_OPTS but I'm not sure of the format.

---

### Post by PhilippWollermann on 2005-08-01
Hi!

Have a look at /etc/cron.daily/prelink. There is a line right at the beginning which says:
> renice +19 -p $$ >/dev/null 2>&1
You can change the "+19" into anything you like, I guess.

I found that file using

> grep -I -r prelink /etc/* 2>/dev/null

The "-I" tells grep not to search in binary files and I redirect stderr to /dev/null, because I don't want to look at all those "file not found" messages. :)

Philipp

---

### Post by Xian on 2005-08-01
Nice call. I'll try making that edit and watch the result.

---

### Post by sb73542 on 2005-08-10
Could someone who has noticed huge performance improvements on older systems, especially with KDE, please post your prelink.conf file, and tell exactly which prelink command switches you used?  Did you also disable the KDE prelinker so that kdeinit is not used?  Thanks!

---

### Post by bored2k on 2005-08-10
[QUOTE=sb73542]Could someone who has noticed huge performance improvements on older systems, especially with KDE, please post your prelink.conf file, and tell exactly which prelink command switches you used?  Did you also disable the KDE prelinker so that kdeinit is not used?  Thanks![/QUOTE]
 At least with Gnome the performance increase is awsome. Nautilus used to open in about 3 seconds (or more, depending on how hungry Azureus is) and now is close to instantly at the max. Firefox too, et al.

---

### Post by sb73542 on 2005-08-10
OK, I prelinked and I have set the environment variable: 

export KDE_IS_PRELINKED="true"

But about 5 instances of kdeinit still get loaded as soon as I start a KDE app.  Any idea what's going on?  Thanks!

---

### Post by cutterjohn on 2005-08-12
prelinking on ibook2 G3/500 Hoary 5.10/GNOME borked oOo with a no suitable window manager(if run from CLI), no message if run from menu just busy icon then nothing.

removal of prelinking -au & reboot restored oOo functionality.

The few other programs that I tried, nautilus, etc. all worked fine.

Side note: I noted that some of the oOo support programs/files gave warnings about missing dependencies or similar, but I don't have a copy of the log as it was apparently removed when I removed the prelink package...  Some other applications also had similar errors, so I'm wondering whether or not those would have been borked as well.

IMNHO: prelinking seems to work best/completely(from reports) ONLY on x86/32bit, if you're not running on x86/32 I'd just stay far away from prelinking for now...

---

### Post by brentroos on 2005-10-10
*

---

### Post by poofyhairguy on 2005-10-10
[QUOTE=brentroos]Can you prelink just one program, or must it be all? I'm trying to understand the concept of this procedure better. 

I run a little bit slower computer:

AMD Duron 950, 192 RAM, 2.6.10-5-k7.

Also I'm running Kubuntu (KDE) version, and I'm wondering if there is a way to increase the loadup time of Firefox, specifically.

I am not really interested in prelinking any other applications. Mozilla Firefox is by far, my most commonly used application, so having a faster load time would be great. Currently, is takes just about 10 seconds, which isn't horrible, but I'd like it to be quicker, similar to how FF loads in XP if possible.

Thanks in advance to any replies to this. Once again, I am only interested in a technique to have Firefox load faster, in KDE.

Thanks.[/QUOTE]


There is a way....but I don't think its easy. If you want to just prelink one, isntall it and use this command:

sudo prelink -amvR

---

### Post by jdong on 2005-10-10
take a look at prelink.bin -- be careful -- sometimes there are such things as *prelink dependencies* :). Pass it a filename and theoretically it should be happy (firefox.bin in your case)

---

### Post by HighPlainsDrifter on 2005-10-11
Prelinking went fine. I noticed some small performance enhancements. The only issue that has come to my attention is when I run Gnome Terminal, 

```
bash: /usr/bin/dircolors: cannot execute binary file
```

is displayed before the prompt.

Any ideas?

---

### Post by soonindallas on 2005-10-12
the performance gains do not seem to outweigh the bloat and risk

---

### Post by jdong on 2005-10-12
Bloat, I've seen insignificant amounts. If you're *that* tight on space, prelinking's probably not right for you!

As far as risk, I don't see much. If prelinking is stale, you'll get an angry error and then reverse back to un-prelinked behavior. It's very rare to corrupt actual binaries (like what happened above), except in cases of filesystem data corruption (not *any* particular application's fault).


For the person above, please try ```
sudo apt-get install --reinstall coreutils
```. This will re-create the files corrupted.

---

### Post by HighPlainsDrifter on 2005-10-17
Thank you. This worked like a charm! :)

---

### Post by HighPlainsDrifter on 2005-10-17
[QUOTE=jdong]It's very rare to corrupt actual binaries (like what happened above), except in cases of filesystem data corruption (not *any* particular application's fault).


For the person above, please try ```
sudo apt-get install --reinstall coreutils
```. This will re-create the files corrupted.[/QUOTE]

I ran in to an additional problem with gzip becoming corrupted. After forcing a reinstall of gzip, I was then able to reinstall coreutils. I wonder if something is going on with my hard drive. :???:

---

### Post by CHUCKYCHUCK on 2005-10-26
i have a question about undoing prelink, in the 1st it's said that do undo prelink, i have to modify the option from "yes" to "no" in the /etc/default/prelink, and then execute /etc/cron ...
but i did some search, and i found that prelink can also be undone by the 'undo' option of prelink, ( prelink -u i remembered )
which method should i use ??

 ( i have no problems with prelink, just to know :) | except after the install of acroread, when prelinking took 45 minutes ............  for the others packages installations it just takes a few secondes but with acroread ... strange isn't it ?? )

---

### Post by ekravche on 2005-12-04
interesting, how safe is this app? I don't want to screw up my i686 5.10 breezy  install

---

### Post by punda on 2005-12-12
Just a little addendum: (and a suggestion to developers :-)

to check if kde is running on a prelinked system we may just add in /usr/bin/startkde:

```
# prelinking check starts here.
if test -f /etc/default/prelink; then
. /etc/default/prelink
  if test "$PRELINKING" = "yes" ; then
     KDE_IS_PRELINKED="true"
     export KDE_IS_PRELINKED
  else
     unset KDE_IS_PRELINKED
  fi
fi
# prelinking check end.
```

my 2 euro cents,

--
Punda

---

### Post by MichaelZ on 2006-04-30
[quote=jdong]
6. To start the first prelink (the longest one!), run **sudo /etc/cron.daily/prelink**
[/quote] 
Hello,

I did as suggested, but when I give the command:

sudo /etc/cron.daily/prelink

the harddisk begin to run, but after some minutes I does not hear any noise more. The system monitor shows CPU at 100%:confused:. Moreover, the terminal does not return. I have the cursor blinking, but nothing else.

My desktop is PIII 500MHz with 500MB RAM.

What could be the problem?

Thank you very much.

Best wishes,
Michael

---

### Post by MichaelZ on 2006-04-30
[quote=MichaelZ]Hello,

I did as suggested, but when I give the command:

sudo /etc/cron.daily/prelink

the harddisk begin to run, but after some minutes I does not hear any noise more. The system monitor shows CPU at 100%:confused:. Moreover, the terminal does not return. I have the cursor blinking, but nothing else.

My desktop is PIII 500MHz with 500MB RAM.

What could be the problem?

Thank you very much.

Best wishes,
Michael[/quote] 
It seems that the problem has gone.

I have first restarted my computer, then:

> 
sudo prelink -avmR 
and finally:

> 
sudo /etc/cron.daily/prelink  
Best wishes,
Michael

---

### Post by nalmeth on 2006-05-16
I've been using prelink happily for a while, but am facing a possible problem.

I ran an update for dapper yesterday, which included a new kernel, and replacing completely xubuntu, and gstreamer + mplayer.

The problem, is that it started prelinking yesterday at 4:00 PM. It is still running, at 8:18 AM...

What gives.

I don't want to interupt it, as i've heard it can cause problems, but I can't just leave it sitting like this. I should point out, the CPU light isn't going at all, and I'm in the failsafe terminal.

Is it safe to interupt a prelink?

---

### Post by nalmeth on 2006-05-16
It's almost 11:00 AM, and prelink is still running. :(

This is not right. I almost just stopped it, but then CPU light started blinking.

Can anyone reassure that it would be safe to stop? Or warn me against doing this?

---

### Post by nalmeth on 2006-05-16
OK!!!

It is 2:15pm right now. I looked at the screen right as it finally finished prelinking:

>>**_22 HOURS AFTER IT STARTED_**<<

>>*_**HOLY MOLEY**_*<<

I can't believe the time it took to do that. My first prelink (when I installed prelink) didn't take that long.

What is it that caused this to take all this time?

 ```
The following packages will be upgraded:
  amarok amarok-xine app-install-data dbus dbus-1-utils debconf
debconf-i18n
  debconf-utils desktop-file-utils digikam dmsetup eject
gnome-app-install
  gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver
  gnome-session gstreamer0.10-alsa gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
gstreamer0.10-x
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1
  libavahi-qt3-1 libdbus-1-2 libdbus-1-cil libdbus-glib-1-2
libdbus-qt-1-1c2
  libexo-0.3-0 libgstreamer-plugins-base0.10-0 libpanel-applet2-0
libsexy2
  libthunar-vfs-1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfcegui4-4
  linux-image-386 linux-kernel-headers linux-restricted-modules-386
locales
  lvm2 mousepad mplayer orage python2.4-dbus thunar ubuntu-artwork
xchat-gnome
xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-fsguard-plugin xfce4-mailwatch-plugin
  xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa
  xfce4-mount-plugin xfce4-netload-plugin xfce4-panel
  xfce4-quicklauncher-plugin xfce4-session xfce4-systemload-plugin
  xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin
  xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfmedia xfprint4
xfwm4
  xubuntu-default-settings 
```

---

### Post by Dutch on 2006-06-03
Upgrading on my Celeron 500Mhz went  ok till he began with running prelink.

He is already busy with running prelink from 11:00 hrs this morning till now ( 21:45).
The processor use is constantly 100% ( almost 11 hours already)
Is it possible to stop this (with an other terminal) ore have I just sit it out ?

---

### Post by Peepsalot on 2006-10-12
Nice how-to.  I just set up prelink on my computer.  I have a question though: Is there any possible way to have synaptic/apt-get/aptitude know that rpelink is installed, and to automatically run it after an upgrade to avoid any problems?
Is there a script that can be edited to have this command run after an upgrade?  I have a feeling I'll forget one of these days.

---

### Post by Peepsalot on 2006-10-13
anyone?

---

### Post by musicinmybrain on 2006-10-28
> **Peepsalot said:**
> Nice how-to.  I just set up prelink on my computer.  I have a question though: Is there any possible way to have synaptic/apt-get/aptitude know that rpelink is installed, and to automatically run it after an upgrade to avoid any problems?
Is there a script that can be edited to have this command run after an upgrade?  I have a feeling I'll forget one of these days.

[Here's how.]("http://ubuntuforums.org/showthread.php?t=45810")

Summary: Put ```
DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}
``` in /etc/apt/apt.conf, which probably doesn't exist until you create it.

---

### Post by VCSkier on 2006-12-08
How would this effect battery life on a laptop?

---

### Post by Johan! on 2006-12-08
There's a problem on my system:
```
sudo /etc/cron.daily/prelink
/etc/cron.daily/prelink: line 53:  3097 Aborted                 (core dumped) /usr/sbin/prelink -a $PRELINK_OPTS >>/var/log/prelink.log 2>&1
```

Last lines of /var/log/prelink.log:
```
prelink.bin: ../../src/dso.c:1465: recompute_nonalloc_offsets: Assertion `dso->shdr[i - 1].sh_offset < dso->ehdr.e_shoff' failed.
Prelink failed with return value 134
```

What does this error message mean, and how can I solve this error?

---

### Post by jdong on 2006-12-08
> **VCSkier said:**
> How would this effect battery life on a laptop?

This would have a negligible or no effect on battery life, unless the prelink happens to run while you're on battery power, which would decrease your battery life by loading your CPU for 5 minutes.


The good news is starting from Feisty, all this prelink thing will just be a story you can tell your grandkids.... With the introduction of DT_GNU_HASH, binaries will have precomputed hash values at compile-time, no need for nightly prelink runs :)

---

### Post by bodhi.zazen on 2006-12-12
Nice How-to

This thread has been added to the UDSF wiki.

[Prelink](http://doc.gwos.org/index.php/Prelink)

---

### Post by Nevermore on 2007-01-15
hi everyone
i have a problem
there is no prelink in etc/chron.d
what can i do???
thanks

---

### Post by noob12345 on 2007-05-08
how can I tell if prelink is working or not?

---

### Post by goodtimetribe on 2007-05-11
> **mrbass said:**
> I've had various problems doing a universal prelink in other distros. I wouldn't recommend it prelinking your whole system.  Even though Yoper does it if you examine it it has special ld_library paths or whatever, etc.  I'd say about 75% of apps in mac os x are 'prebinded'. 

I do, however, recommend prelinking **Openoffice** as it'll cut down the load times in half.  Instead of 15 seconds to load OpenWriter, for instance, it'll only take 7 seconds. Sure you can have that openoffice thing load on start but that'll waste memory resources if you don't use it all the time.

[b]sudo apt-get install prelink
sudo /usr/sbin/oooprelink -f[/b]

I definitely noticed some improvement from this.

thanks.

---

### Post by ajmc on 2011-03-01
I wonder if prelink has still errors on amd64?  Does anybody know?  I want to try it out. :)

---

