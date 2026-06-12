---
title: "Firefox/Amarok audio problem"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by bete on 2008-09-17
Hi, i switched to linux a few days ago and so far so good. But i have some issues regarding audio on this system.

I have amarok audio player up and running, no problems.
But if i try to watch a flash video (youtube etc) while listening to music, the flash video will pause after a few seconds and totally freeze up amarok.

So i kill the amarok player and firefox, and restart amarok and press play - No go! The app freezes again.

So after this happens, audio is messed up all over, so i have to relog.

This also happens if i start WoW with amarok on, then the audio in wow gets disabled. If i do it the other way around, start amarok after i have already started wow, amarok freezes up..

Meh im tired of this :(.
Sounds like a problem for the Linux pro's.. Help me out :P

---

### Post by cozmicharlie on 2008-09-17
Welcome to Ubuntu - sorry to hear you are having problems.  FYI - Ubuntu just recently changed to "Pulse Audio" which in the long run is much better than the previous audio system but is now suffering from a few bugs that need to be fixed (and will be) in susequent releases of Ubuntu.  I realize that really doesn't matter since most people just want sound to work.  Luckily the Ubuntu community has a fix already and this should work for you.  The fix for this is found here [http://www.ubuntugeek.com/pulseaudio-fixes-system-wide-equalizer-support-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/pulseaudio-fixes-system-wide-equalizer-support-in-ubuntu-804-hardy-heron.html).  However, being new I will walk you through this so you don't have any problems.

First read the caveats - make sure this describes your situation.  I will assume you have Hardy installed on a 32 bit system - if not then follow the 64 bit instructions.  Below are the instructions for the 32 bit/1386 users only.  For the commands, simply open a terminal and cut and paste the commands - add your password when it asks:

Remove the obsolete nspluginwrapper package:
```
sudo aptitude remove nspluginwrapper
```
Remove obsolete packages and configuration files:
```
sudo aptitude remove libflashsupport
```
```
sudo rm ~/.pulse/* ~/.asoundrc* /etc/asound.conf

```

Step1:- Procedure to follow

Ensure you have the necessary packages installed
```
sudo aptitude install padevchooser libao-pulse libasound2-plugins libsdl1.2debian-pulseaudio
```

Add PPA to your sources.list - this adds a repository to Synaptic.  You can also do this using a GUI method.  In the menu got to System>administration>software sources.  Click add and cut and paste the two deb lines below one at a time then close. Or, use the command line:
```
gksudo gedit /etc/apt/sources.list
```

Add the following lines to the end,save and exit
> # PulseAudio Fixes
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main

Update your repository lists, then upgrade your system (answer yes to install packages that cannot be validated)
```
sudo aptitude update
```
```
sudo aptitude upgrade

```
Set PulseAudio as the default ALSA device and enable the correct driver for libao applications
```
asoundconf set-pulseaudio
```
```
echo &#8220;default_driver=pulse&#8221; >~/.libao
```

Now you need to Go to System/Preferences/Sound. Ensure all the &#8220;Sound Playback&#8221; entries are set to their default setting of &#8220;Autodetect&#8221;, otherwise you may experience difficulties.

After logging out and back in, everything should work correctly! These packages will install PulseAudio complete with tweaks to reduce stuttering/CPU usage, and Flash 10 (release candidate). Finally, Flash & PulseAudio work correctly without crashes

---

### Post by markbuntu on 2008-09-17
In Amarok go to Settings/Configure Amarok/Engine and change the Output plugin to pulseaudio. You can also read my guide to getting multiple sound applications to play together nicely:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by bete on 2008-10-08
You guyes rock :)
Thanks cozmicharlie worked perfectly

---

### Post by hiko2 on 2008-10-28
Hi, I had the same problem and did your tutorial, and amarok sound works fine but i can't hear the audio of youtube, the video is there but just no audio, already tried reboot, but no use. If you know this problem or have heard of it any help will be greatly appreciated. Thanks.

---

### Post by wolfen69 on 2008-10-28
try ```
sudo apt-get install libflashsupport
``` then restart firefox if open.

---

### Post by hiko2 on 2008-10-29
Thanks very much, man it worked perfectly, flawless. :).

---

### Post by Maheriano on 2008-10-29
Not so much.....I was able to hear audio from Audacious but not Firefox and now I have no audio. I followed all the steps posted above and the problem is I don't really know what they do....please help! How can I fix it? I'm (was) using SPDIF out on my motherboard to play audio.

---

### Post by salingova on 2008-11-06
> **wolfen69 said:**
> try ```
sudo apt-get install libflashsupport
``` then restart firefox if open.
I had the same problem, and this really fixed it. THX

---

### Post by Eye of Storm on 2008-12-30
> salingova  	
Re: Firefox/Amarok audio problem
Quote:
Originally Posted by wolfen69 View Post
try
Code:

sudo apt-get install libflashsupport

then restart firefox if open.
I had the same problem, and this really fixed it. THX


Me too ... but when I entered ... install libflashsupport .. it said
> Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
[B]However the following packages replace it:
  flashplugin-nonfree-extrasound[/B]
E: Package libflashsupport has no installation candidate

So I closed Firefox and typed into console ...
> sudo apt-get install flashplugin-nonfree-extrasound
and WHAMMO! it downloaded and installed what I wanted. Then, when I started up Firefox flash videos like YouTube worked again. :D

Thanks ya'll!

---

