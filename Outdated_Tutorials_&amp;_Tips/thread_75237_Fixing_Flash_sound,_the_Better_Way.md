---
title: "Fixing Flash sound, the Better Way"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by NeoChaosX on 2005-10-13
I've noticed that a common sound problem a lot of users have is when they're browsing the web, there's no sound from Flash animations. For some, this is a blessing, but for people who do browse sites that use the stuff (Homestar Runner immediately comes to mind), sound is necessity. So I cooked up this quick guide on how to fix it.

First, off, I'll say that one common solution I've seen thrown around is
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```
This usually works in getting Flash sound to work. However, in some configs, this causes Flash sound to go out of sync. If this happens, delete /usr/lib/libesd.so.1 and follow these steps...

1) Set up your system to use ALSA dmix mixing and AOSS emulation according to [this thread](http://ubuntuforums.org/showthread.php?t=44753).

2) Install the alsa-oss package.
```
sudo apt-get install alsa-oss
```

3) Open up **/etc/mozilla-firefox/mozilla-firefoxrc** in gedit or whatever your text editor of choice is. Then, modify this line
```
FIREFOX_DSP="auto"
```
to
```
FIREFOX_DSP="aoss"
```

What this does it let Flash run through ALSA's OSS emulation. So Flash sound will not only be in sync (because it isn't forced through another layer of sound like ESD), but it will also play even if you have other apps that use sound running in the background.

Hope this helps.

---

### Post by Gandalf on 2005-10-13
I just want to add that i had problems back in preview using FIREFOX_DSP="aoss" , firefox used to hang when i try to quit the page with the animation...

---

### Post by jarrett.wold on 2005-10-13
I just tried this method, and if I attempt to pause any audio output et al with AOSS as the sink, it locks the browser.  So back to Auto for me.

---

### Post by NeoChaosX on 2005-10-13
I've never had this problem. jarrett.world, did you try the ESD symlink as well?

---

### Post by John.Michael.Kane on 2005-10-14
Does this file need to be reove libesd-alsa0?
Also do you select oss as the output in put or alsa for both

---

### Post by NeoChaosX on 2005-10-14
libesd-alsa0 is necessary for the AOSS output to work.

---

### Post by John.Michael.Kane on 2005-10-14
thanks

---

### Post by jarrett.wold on 2005-10-16
I didn't actually, I just tried your method, the symlink seemed like a bit of a hack to me :)

[QUOTE=NeoChaosX]I've never had this problem. jarrett.world, did you try the ESD symlink as well?[/QUOTE]

---

### Post by pizzach on 2005-10-16
NeoChaosX, if I was 100% sure you weren't a guy, I would kiss you!  But I'm not.  So um...I won't.  But I'm still really happy.  I'm on a 100% alsa setup now.  Now there are no sound lags in flash.  And also, mplayer sync way better now.  It was okay before, but now it SYNCS.  Happiness has arrived!  And is ensuing.  Also, I believe sound quality is higher.

[QUOTE=NeoChaosX]I've noticed that a common sound problem a lot of users have is when they're browsing the web, there's no sound from Flash animations. For some, this is a blessing, but for people who do browse sites that use the stuff (Homestar Runner immediately comes to mind), sound is necessity. So I cooked up this quick guide on how to fix it.

First, off, I'll say that one common solution I've seen thrown around is
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```
This usually works in getting Flash sound to work. However, in some configs, this causes Flash sound to go out of sync. If this happens, delete /usr/lib/libesd.so.1 and follow these steps...

1) Set up your system to use ALSA dmix mixing and AOSS emulation according to [this thread](http://ubuntuforums.org/showthread.php?t=44753).

2) Install the alsa-oss package.
```
sudo apt-get install alsa-oss
```

3) Open up **/etc/mozilla-firefox/mozilla-firefoxrc** in gedit or whatever your text editor of choice is. Then, modify this line
```
FIREFOX_DSP="auto"
```
to
```
FIREFOX_DSP="aoss"
```

What this does it let Flash run through ALSA's OSS emulation. So Flash sound will not only be in sync (because it isn't forced through another layer of sound like ESD), but it will also play even if you have other apps that use sound running in the background.

Hope this helps.[/QUOTE]

---

### Post by kwaanens on 2005-10-17
This did not resolve sound in flash for me. The only change was that Firefox freezes when shut down with aoss enabled. :(

- Ketil

---

### Post by Staesys on 2005-10-22
My Flash sound worked fine, but changing the line in the FireFox file fixed the syncronization problem a treat. Thanks!

---

### Post by spider-man on 2005-10-23
Hi guys,
   The above instructions almost work for me. I have two sound cards. My speakers are plugged into the second sound card, and I have sound using GNOME programs (muine, gaim, ubuntu startup sounds, totem). But I don't have sound in Doom or using flash. On a hunch I plugged my speakers into my first sound card and the sound worked in both Doom and flash. So my question is how do I get flash and Doom (I'm guessing they both use ALSA OSS) to use my second sound card like the rest of my programs?

Thanks for your help.

---

### Post by NeoChaosX on 2005-10-24
It's slightly off-topic, but I'll help out. There is an option to choose your default sound card in System > Preferences > Sound. See if changing that setting works.

---

### Post by spider-man on 2005-10-24
[QUOTE=spider-man]Hi guys,
   The above instructions almost work for me. I have two sound cards. My speakers are plugged into the second sound card, and I have sound using GNOME programs (muine, gaim, ubuntu startup sounds, totem). But I don't have sound in Doom or using flash. On a hunch I plugged my speakers into my first sound card and the sound worked in both Doom and flash. So my question is how do I get flash and Doom (I'm guessing they both use ALSA OSS) to use my second sound card like the rest of my programs?

Thanks for your help.[/QUOTE]

I "solved" the problem adding the driver module of the first sound card to /etc/hotplug/blacklist. Thanks for the great Howto.

---

### Post by ember on 2005-10-24
I tried this method, too and also had freezes when closing the tab/page. So I switched back to the symlink method, which works.

---

### Post by schizoid_embolism on 2005-10-28
Hi,

Thought I would tell of my experiences with this issue.  I have had many problems with sound and tried many different methods to fix it.  I can relate to all of you who say that this howto made Firefox freeze when any website would try to play sound.  I assumed that this howto would simply not work for me.  But I finally got everything working perfectly, and here is how I did it.  I followed NeoChaosX's instructions exactly, EXCEPT for step one, which has you follow some instructions on a separate thread.  When I had done that before, my sound issue was so bad, I couldn't reverse it no matter what I tried, so I reinstalled Ubuntu, and did the instructions again without that step one.  I don't know why this worked for me nor do I know if this will work for others.

Jeremy

---

### Post by stoffe on 2005-11-04
Thanks! That worked perfectly. Now, if someone could help me getting the vmware player to do the same... (simply starting it with aoss or esddsp doesn't work) :)

---

### Post by [HUN]Levente on 2005-11-15
This works great for me, too, but the sound is terrible(it's like the volume is too high) in flash. Other sound(BMP, videos) are OK. What could be the problem?

---

### Post by migo on 2005-11-18
I tried apt-get alsa-oss and got the following error, any other way to get around it?

Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alsa-oss has no installation candidate

---

### Post by NeoChaosX on 2005-11-18
Do you have universe enabled in your /etc/apt/sources.list?

---

### Post by migo on 2005-11-19
I didn't, enabling it gave me a slightly different error.

Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package alsa-oss has no installation candidate

---

### Post by djclue917 on 2005-12-04
You might want to try installing the package libesd-asla0 if you are using ALSA (for Ubuntu and Kubuntu).

sudo apt-get install libesd-alsa0

---

### Post by Zooropa on 2005-12-07
This has worked an absolute treat to get sound working!

I was viewing the video here:
[http://www.thehansofoundation.org/dharma.html](http://www.thehansofoundation.org/dharma.html)

It's slightly out of sync, with the audio being a bit ahead of the video.

Now I need to get poly-audio working...I saw a guide somewhere, but it's too early in the morning to be tinkering.

---

### Post by Zooropa on 2005-12-07
Arrrghhh, I ran through the poly-audio thread here:
[http://ubuntuforums.org/showthread.php?t=32063&highlight=audio+flash](http://ubuntuforums.org/showthread.php?t=32063&highlight=audio+flash)

And now I can't get audio in Flash, even though I ran through the steps here again.

I can play movies in VLC, and get sound, while the same time playing mp3s in XMMS though :S

---

### Post by yaztromo on 2005-12-11
My fix:

For me this worked with Firefox 1.0.7 and 1.5

Check if you have a /dev/dsp. I didn't have one, even though sound in other programs was working fine.

If not create one by typing

cd /dev
sudo ./MAKEDEV audio

Restart firefox and sound should be working.

---

### Post by monkeyface on 2005-12-11
[QUOTE=yaztromo]My fix:

For me this worked with Firefox 1.0.7 and 1.5

Check if you have a /dev/dsp. I didn't have one, even though sound in other programs was working fine.

If not create one by typing

cd /dev
sudo ./MAKEDEV audio

Restart firefox and sound should be working.[/QUOTE]
OMG!!! You're a genius man!! :D
I've tried LOTS of methods, nothing has worked.. but this does :)
OSS sound in Cedega even works now :D

---

### Post by yaztromo on 2005-12-12
Glad to be of help :D 

I've noticed that you have to do this everytime you reboot.

I'm not sure how to put it into a script that runs at boot time. Can anyone help?

EDIT:

Solved it.

Add the following lines to the end of /etc/init.d/bootmisc.sh

#
#       Create /dev/dsp
#
cd /dev
./MAKEDEV audio

---

### Post by pizzach on 2005-12-15
I posted some instructions for enabling flash sound using aoss in firefox 1.5.
[http://www.ubuntuforums.org/showthread.php?t=101438](http://www.ubuntuforums.org/showthread.php?t=101438)

The only problem is that I'm good at forgetting things.  So any testers would be appreciated.  ;)  Esd does not work well with flash with me.  I can't stand the lag it gives on my machine.

---

### Post by akurashy on 2005-12-15
this worked PERFECTLY :)

---

### Post by Jormundgand on 2005-12-15
When following the instructions in the thread linked by the OP and the instructions in the OP itself, I am left with the following:

When playing a Flash movie in Firefox it plays a small amount of the movie and then freezes - if I close Firefox without doing anything I have to kill three stopped instances of "firefox-bin", but it freezes totally and has to be force-quitted if I try to navigate anywhere via hyperlinks. Additionally, as I describe in [this thread](http://www.ubuntuforums.org/showthread.php?t=104062) (which might possibly benefit from being merged into this one?) I cannot change my default sound device in the Sound preferences window as I could before following the instructions given. I have not symlinked libesd.so.0 to libesd.so.1 and doing so has no effect, so far as I could tell.

Can anyone assist me? I got this to work on a previous installation and cannot recall what I did.

---

### Post by chessforce on 2005-12-30
Thanks NeoChaosX for the instructions!  It worked perfectly with Firefox 1.5.

---

### Post by Stroganoff on 2006-01-04
[QUOTE=Jormundgand]When following the instructions in the thread linked by the OP and the instructions in the OP itself, I am left with the following:

When playing a Flash movie in Firefox it plays a small amount of the movie and then freezes - if I close Firefox without doing anything I have to kill three stopped instances of "firefox-bin", but it freezes totally and has to be force-quitted if I try to navigate anywhere via hyperlinks.[/QUOTE]

I second that. Kubuntu 5.10, mozilla.com Firefox 1.5
But it happens only if I'm starting Firefox with ```
aoss /opt/firefox/firefox "$@"
```.
Editing my ~/.mozilla/firefox/rc to ```
FIREFOX_DSP="aoss"
``` does not seem to have any effect at all.

(When starting Firefox with artsdsp from Terminal, it crashes to desktop when I try to open a soundflash.)

I absolutely need flash and xmms together. I'm setting up a single public computer for a local pub with Streamtuner@KMenu and FunnyFlashsites@Bookmarks. It won't be good publicity for Linux if had to explain that they have to stop xmms & RESTART Firefox in order to hear the sound in flashs.

It's such a sad crap. :((

---

### Post by danish_demon on 2006-01-31
[QUOTE=yaztromo]My fix:

For me this worked with Firefox 1.0.7 and 1.5

Check if you have a /dev/dsp. I didn't have one, even though sound in other programs was working fine.

If not create one by typing

cd /dev
sudo ./MAKEDEV audio

Restart firefox and sound should be working.[/QUOTE]

thank you for this (and the helpful tip to get it done at boot).  finally i have sound in flash!  did you follow the instructions at the beginning of this thread as well, or just do this?

---

### Post by yaztromo on 2006-01-31
I found changing firefox_dsp from auto to aoss worked for firefox 1.0.7 but it did not work for 1.5.

I happened upon this fix after trying to play a game that required a /dev/dsp. Some forum searching for this eventually got me to the MAKEDEV command.

---

### Post by Mozzer on 2006-02-07
[QUOTE=yaztromo]My fix:

For me this worked with Firefox 1.0.7 and 1.5

Check if you have a /dev/dsp. I didn't have one, even though sound in other programs was working fine.

If not create one by typing

cd /dev
sudo ./MAKEDEV audio

Restart firefox and sound should be working.[/QUOTE]
This doesn't seem to work for me... :( I already have a dsp.

---

### Post by happyponcho42 on 2006-02-11
[QUOTE=Mozzer]This doesn't seem to work for me... :( I already have a dsp.[/QUOTE]

This method seemed to have worked for me, however, whenever i switch between tabs/browser windows, there's a little skip in the sound.  Is there any way to fix that?

---

### Post by BrokenArrows on 2006-08-11
Sorry to be dragging this post up from the depths of the arcives but i have used this solution to to fix my flash sound problem but only to create another problem.

I cannot play mp3 sound files on my computer.

When i try and play an mp3 using Rhythmbox or any other music application i get the following error;

"Could not open the resource for writing"

When i try and play a file with Totem i get the same error as above and this is the output from the console:

```
(totem:7659): GLib-GObject-WARNING **: gsignal.c:1716: signal `got-redirect' is invalid for instance `0x8319cc8'
- using device default
- using device default
ALSA lib conf.c:1566:(snd_config_load1) _toplevel_:34:0:Unexpected char
ALSA lib conf.c:2811:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2672:(snd_config_hooks_call) function snd_config_hook_load returned error: Unknown error
ALSA lib conf.c:3040:(snd_config_update_r) hooks failed, removing configuration

```

If anyone could help that would be great.

---

### Post by drycellbattery on 2006-08-17
I have an /etc/firefox/firefoxrc and an /etc/mozilla-firefox/mozilla-firefoxrc

changing the former makes changes while the latter does not.
Changing from "auto" to "aoss" solves the sound issue but creates the freezing issue for me.

le sigh

---

