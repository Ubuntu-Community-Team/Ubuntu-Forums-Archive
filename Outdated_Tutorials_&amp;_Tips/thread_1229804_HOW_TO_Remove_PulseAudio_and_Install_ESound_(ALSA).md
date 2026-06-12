---
title: "HOW TO: Remove PulseAudio and Install ESound (ALSA)"
date: 2009-08-02
forum: Outdated Tutorials &amp; Tips
---

### Post by coldReactive on 2009-08-02
[size="5"]DO NOT USE THIS TUTORIAL ON X/K/ubuntu 9.10![/size]

This is quite a simple tutorial, it only takes a few steps, and will have your sound system/manager not be listed in the processes list under top/etc. Before we begin, make sure that you BACK-UP **/etc/X11/Xsession.d/70pulseaudio** just in case this does not work. I can't stress this enough, as I will be UNABLE to provide support for this tutorial.

**Step One**: Open Terminal
[list]
[*]Applications > Accessories > Terminal
[/list]

**Step Two**: Run The Commands Through Terminal
[list]
[*]killall pulseaudio
[*]sudo apt-get remove pulseaudio
[*]sudo apt-get install esound
[*]sudo rm /etc/X11/Xsession.d/70pulseaudio
[*]sudo apt-get purge pulseaudio
[/list]

**Step Three**: Reboot The System

After rebooting, login and see if sound actually works. Depending on your Ubuntu version, the login/startup sound will not play with ESound. ESound will work for DVD Playback.

**Warning:** ESound will/may not show up in the sound configurations, they will display as automatic, like below.

[img]http://i32.tinypic.com/ru43g7.png[/img]

---

### Post by simplyw00x on 2009-08-06
What exactly is the benefit of uninstalling Pulseaudio? It works fine for me, and you haven't mentioned either what benefits you think it will give or what features you will definitely lose.

---

### Post by coldReactive on 2009-08-06
> **simplyw00x said:**
> What exactly is the benefit of uninstalling Pulseaudio? It works fine for me, and you haven't mentioned either what benefits you think it will give or what features you will definitely lose.

ESound doesn't take up as much processing power (if any at all) as pulseaudio does. Not to mention, it's only about 200-400 KB in size, and only one package rather than a few.

---

### Post by Keranu on 2009-08-15
I tried doing it, but I don't see Esound listed anywhere in my Sound Preferences window and PulseAudio is still listed. Here is my terminal log if it's of any help:

```
keranu@humphrey:~$ sudo killall pulseaudio 
[sudo] password for keranu: 
keranu@humphrey:~$ sudo apt-get remove pulseaudio 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages will be REMOVED: 
  pulseaudio ubuntu-desktop 
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded. 
After this operation, 1880kB disk space will be freed. 
Do you want to continue [Y/n]? y 
(Reading database ... 157424 files and directories currently installed.) 
Removing ubuntu-desktop ... 
Removing pulseaudio ... 
 * PulseAudio configured for per-user sessions 
Processing triggers for man-db ... 
keranu@humphrey:~$ sudo apt-get install esound 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages will be REMOVED: 
  pulseaudio-esound-compat 
The following NEW packages will be installed: 
  esound 
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded. 
Need to get 0B/28.1kB of archives. 
After this operation, 90.1kB disk space will be freed. 
Do you want to continue [Y/n]? y 
(Reading database ... 157334 files and directories currently installed.) 
Removing pulseaudio-esound-compat ... 
Processing triggers for man-db ... 
Selecting previously deselected package esound. 
(Reading database ... 157322 files and directories currently installed.) 
Unpacking esound (from .../esound_0.2.40-0ubuntu3_i386.deb) ... 
Processing triggers for man-db ... 
Setting up esound (0.2.40-0ubuntu3) ... 
keranu@humphrey:~$ sudo rm /etc/X11/Xsession.d/70pulseaudio 
rm: cannot remove `/etc/X11/Xsession.d/70pulseaudio': No such file or directory 
keranu@humphrey:~$ sudo rm /etc/X11/Xsession.d/70pulseaudio.back 
keranu@humphrey:~$ sudo apt-get purge pulseaudio 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package pulseaudio is not installed, so not removed 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
keranu@humphrey:~$ 
```

---

### Post by coldReactive on 2009-08-15
ESound will not show itself in sound configs. It will show as automatic.

---

### Post by colorprint on 2009-08-15
Can't use keyboard volume and mute keys after this :(

---

### Post by coldReactive on 2009-08-15
> **colorprint said:**
> Can't use keyboard volume and mute keys after this :(

I can use them with an iHome keyboard. Maybe it's keyboard specific.

---

### Post by colorprint on 2009-08-15
It worked with pulseaudio...
Also with esound the gnome taskbar mixer/volume applet not works, and gnome-volume-control not works too :(

---

### Post by coldReactive on 2009-08-15
type in terminal
```
esd --help
```

and tell me what it says for **Possible devices are:**

---

### Post by colorprint on 2009-08-15
Possible devices are:  hw:0  (HDA NVidia)

---

### Post by coldReactive on 2009-08-15
> **colorprint said:**
> Possible devices are:  hw:0  (HDA NVidia)

[Download and save this page as **alsa-info.sh**](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)

Right-Click alsa-info.sh > Properties > Permissions Tab; make sure that **Allow executing file as program** is checked.

In terminal, cd to where alsa-info.sh is located, and run it by typing in **./alsa-info.sh**

When it prompts you to upload the data to the alsa server, tell it no.

After it completes, go to tmp in your / (filesystem) and paste your alsa-info.txt between CODE BBCode tags, or upload it

---

### Post by colorprint on 2009-08-15
I have attached it

---

### Post by colorprint on 2009-08-15
gnome-alsamixer  works for example...
but gnome-volume-control and gnome-volume-control-applet not works, and I think keyboard volume keys not works because of gnome-volume-control-applet too...

---

### Post by coldReactive on 2009-08-15
> **colorprint said:**
> gnome-alsamixer  works for example...
but gnome-volume-control and gnome-volume-control-applet not works, and I think keyboard volume keys not works because of gnome-volume-control-applet too...

ALT+F2 and type in esd. Then hit Run. A sound effect should play. Then, try it again. If it works after that...

Make sure that your mixer (System > Preferences > Sound) looks like this:

[img]http://i32.tinypic.com/ru43g7.png[/img]

Reboot the machine after hitting OK. See if this helps. ESound isn't running according to your alsa-info.

---

### Post by colorprint on 2009-08-15
> **coldReactive said:**
> ALT+F2 and type in esd. Then hit Run. A sound effect should play. Then, try it again. If it works after that...

no any sounds :(
> 
Make sure that your mixer (System > Preferences > Sound) looks like this:

It is the gnome-volume-control , not works as I write before...
It only shows a small window about "waiting for response from sound subsystem"


> 
Reboot the machine after hitting OK. See if this helps. ESound isn't running according to your alsa-info.
Rebooted twice, still no any progress :(

---

### Post by coldReactive on 2009-08-15
> **colorprint said:**
> Rebooted twice, still no any progress :(

Try **esd -d hw:0**

---

### Post by colorprint on 2009-08-15
```
root@Anton-HP:/tmp# esd -d hw:0
- using device hw:0
root@Anton-HP:/tmp# ps ax | grep esd
13362 pts/1    S+     0:00 grep esd
root@Anton-HP:/tmp# 

```

---

### Post by colorprint on 2009-08-15
if running just "esd" I see it in ps output:
```
root@Anton-HP:/tmp# ps ax | grep esd
 4009 ?        SL     0:00 esd
 4387 pts/1    S+     0:00 grep esd

```
and alsa-info.sh reports after this:
```
ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - Yes

```
But System > Preferences > Sound (gnome-volume-control) and gnome mixer applet (gnome-volume-control-applet ) not works anyway...

---

### Post by coldReactive on 2009-08-15
You might want to create a new topic about the issue, I'm sorry.

---

### Post by colorprint on 2009-08-15
ok thanks for help anyway

---

### Post by Katalog on 2009-08-15
> **simplyw00x said:**
> What exactly is the benefit of uninstalling Pulseaudio? It works fine for me, and you haven't mentioned either what benefits you think it will give or what features you will definitely lose.

> **coldReactive said:**
> ESound doesn't take up as much processing power (if any at all) as pulseaudio does. Not to mention, it's only about 200-400 KB in size, and only one package rather than a few.

My opinion (and that's all it is - my opinion, so keep that in mind while you read this post) is that unless you have extremely limited resources or some kind of old or incompatible hardware that your system would actually benefit from purging PulseAudio from your system, that you're probably better off learning how to set up PulseAudio correctly (which is almost as easy as geting rid of it) and becoming familiar with it, because it is not going away. This is the future my friends, and there may come a day in the not so distant future when you may not have the option, or they will at least make it more difficult, to fall back on ESound any more. Yes, Pulse uses more resources and it does take more packages, but it also supports a wider range of devices. Pulse is indeed broken and only halfway installed in Ubuntu 9.04, but it is possible to install the missing packages and get it running correctly on Hardy, Intrepid and Jaunty:
[URL="http://ubuntuforums.org/showthread.php?t=789578"]
**HOWTO: PulseAudio Fixes & System-Wide Equalizer Support**[/URL]

I too was opposed to PulseAudio in the beginning because I saw no need for yet another Linux sound architecture, but now that I have it set up and working like it's supposed to, I actually quite like it. And I'm running it on an Eee PC 1000HA netbook with a puny little 1.6GHz N270 Atom processor, and the performance hit has not been as dreadful as I expected, and will only get better as the developers continue to improve it.

Like I said, this is just my opinion. Take it for what it's worth. I'm not trying to start a debate, I just wanted to present a logical reason for adopting it rather than getting rid of it. Just my two cents on the subject, that's all.

---

### Post by Yellow Pasque on 2009-08-15
Esound? Esound? No!
Esound is useful for those running Hardy, who want to get rid of PulseAudio and still have system/event sounds. Other than that, run as far away from esound as you can. There is a reason that it has been replaced by libcanberra.

---

### Post by coldReactive on 2009-08-15
> **Temüjin said:**
> Esound? Esound? No!
Esound is useful for those running Hardy, who want to get rid of PulseAudio and still have system/event sounds. Other than that, run as far away from esound as you can. There is a reason that it has been replaced by libcanberra.

I don't like seeing pulseaudio in any system monitoring software.

---

### Post by Yellow Pasque on 2009-08-15
> **coldReactive said:**
> I don't like seeing pulseaudio in any system monitoring software.
Removing pulseaudio is okay for now, but GNOME is becoming increasingly dependent on Pulseaudio. In Ubuntu 9.10, it's a real challenge to go without PulseAudio (I run an  Ubuntu 9.10 with OSS4 and the volume control and sound settings dialogs don't run without it.)

---

### Post by colorprint on 2009-08-16
> **Temüjin said:**
> (I run an  Ubuntu 9.10 with OSS4 and the volume control and sound settings dialogs don't run without it.)
Yes, I have the same problem on 9.10 with Esound :(

---

### Post by coldReactive on 2009-08-16
> **colorprint said:**
> Yes, I have the same problem on [SIZE="7"]9.10[/SIZE] with Esound :(

That's your problem then.

---

### Post by Jose Catre-Vandis on 2009-09-12
This worked fine for me. I had followed the "Howto Setup up Pulse Audio tut" but this killed esound from Audacious, VLC, Totem. So removing pulseaudio fixed it for me :)

---

### Post by edwinluischm on 2009-10-24
I like remove pulseaudio because don't work with the microphone on VirtualBox 3.

---

### Post by Yellow Pasque on 2009-12-03
Ok, for those running GNOME in Karmic without PulseAudio, who want their volume control and media-keys back: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by woodmaster on 2010-01-01
I'm a bit of an Ubuntu noob, but...I can't find this screen...how do I get there?
 
 
 
 
[IMG]http://i32.tinypic.com/ru43g7.png[/IMG]

---

### Post by Yellow Pasque on 2010-01-02
woodmaster: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973/comments/11](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973/comments/11)
Ignore what it says about the mixing. Just grab the gnome packages from the PPA I linked to in the last post, and the classic GNOME volume control/mixer will be available on the next boot (you may have to re-add the 'volume control applet' to your panel).

---

### Post by skyraven on 2010-03-05
Hello there guys,


I have a small question..don't shoot me for it..I read the big title but still this is the only relevant thread:)
I'm using the NxServer - NxClient combination...that forwards display, sound, etc from the server to the "terminal" which can run on Linux/Windows/etc.

The bad part..is that NxServer requires ESD installed (it's running it's own ESD process from which it forwards sound) and if it doesn't receive anything there it won't get me any sound.

Does anyone have any good tutorial on replacing Pulse with ESD on Ubuntu 9.10 ?
I've done so far removing, purging pulseaudio, configuring gstreamer-properties, placing the packages from [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa) (but with partial luck..I only got the volume control to appear).
With all these..totem player the default player for example still goes with something other then ESD and no sound can be heard.
Also I can't configure the distribution sound theme as I'm having no more menu for that.

Can I ask for some kind and patient help ? :) other than a RTFM as I'm already banging my head against the wall.

---

### Post by junn0suk3 on 2010-03-14
> **Temüjin said:**
> Ok, for those running GNOME in Karmic without PulseAudio, who want their volume control and media-keys back: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)
At last! I had an issue with skype in pulseaudio (the sound was horrendously buggy and the external mic on my Acer Aspire 1 did not work) which made me just remove the whole thing (pulseaudio, I really need my skype); thanks for the help to get my volume controls via hotkeys back.

---

### Post by aeon.flux on 2010-04-25
> **simplyw00x said:**
> What exactly is the benefit of uninstalling Pulseaudio? It works fine for me, and you haven't mentioned either what benefits you think it will give or what features you will definitely lose.

i've just found this thread useful, because i play "warsow" (first person shooting game) and when i listen music (in any player using pulseaudio) and playing that game, the sounds in game often stops and i there's a problem to turn off that game (i have to pres Ctrl+Alt+F4 , type killall warsow_bin) so this is very useful :)))

---

### Post by ESDEEM on 2011-04-10
Contented with this thread...Now I use ALSA over pulseaudio....smoother than the latter...no loop stucks...!:razz:

---

