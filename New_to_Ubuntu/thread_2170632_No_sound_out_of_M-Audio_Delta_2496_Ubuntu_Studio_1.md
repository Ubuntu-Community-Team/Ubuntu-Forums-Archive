---
title: "No sound out of M-Audio Delta 2496 Ubuntu Studio 12.04"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by louh2 on 2013-08-27
New install, I'm a total newb.  Need help badly, AM GETTING SUPER FRUSTRATED!!!!!! Pulse audio shows no cards installed, only dummy ins/outs.  Can't Figure out how to install a driver for my sound card.  Jack won't run, Mudita24 doesn't do anything at all when clicked on.  Clicking on mp3's shows bars like it's playing but no output.  STUCK!  Please help me, I'm going out of my fricking mind!

---

### Post by UltimateCat on 2013-08-27
Hi: louh2-

Welcome to the Ubuntu Forums!;)

I'm not a sound expert but I'll help you as best I can-

Open your terminal and run this command:
```
lspci | grep -i audio

```

When you do you'll see something like this: (Just an example)

```
 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)


```

Once you know what sound card you have you should be able to find a driver in the Ubuntu repo-
Try using Google and type something like "(name of your card) driver linux

Aside from that you can also test the sound using the terminal but if you have alsa and pause audio both at the same time that can cause conflict.
Try opening the terminal and type: "alsamixer"

When you do you will see the columns for 'Master' and PCM or something similar. With your mouse or arrow keys raise up the volume all the way.
Exit alsa and close the terminal than see if you have sound.
The speakers should be plugged into the green output plug (if this is a Desktop) 

Hope that helps

---

### Post by UltimateCat on 2013-08-27
This sound Troubleshooting may help you too--;)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Picture of Alsa Mixer here:
[http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

---

### Post by louh2 on 2013-08-27
The command to show what audio device is installed gave me "03:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

" which is the M-Audio Audiophile 2496 sound card I have so I know it's there but am unsure if a driver for it is installed since it's not being picked up by pulse audio mixer.

alsamixer only spits back "no such file or directory" which I take means that alsa mixer is not installed?  I have read that pulse audio can cause problems but I can't seem to find a way to completely remove it and I also do not know how to completely install software using the command line.  Is there another way to install software until I can understand how to do it with a command?

UPDATE:
I had another post about my install and a reinstall of the os fixed probably all of the current problems I was experiencing so thanks for the help.

---

### Post by UltimateCat on 2013-08-27
> **louh2 said:**
> The command to show what audio device is installed gave me "03:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

" which is the M-Audio Audiophile 2496 sound card I have so I know it's there but am unsure if a driver for it is installed since it's not being picked up by pulse audio mixer.

alsamixer only spits back "no such file or directory" which I take means that alsa mixer is not installed?  I have read that pulse audio can cause problems but I can't seem to find a way to completely remove it and I also do not know how to completely install software using the command line.  Is there another way to install software until I can understand how to do it with a command?

UPDATE:
I had another post about my install and a reinstall of the os fixed probably all of the current problems I was experiencing so thanks for the help.

The Ubuntu Software Center will install any application that you want so this is the other way to install software till you understand cmdline--
When you open the Ubuntu Software Center look up at the top right hand corner and you'll see where you type in the name of whatever application you'd like to install.;)

But to manually install a driver or application that is not in the Ubuntu repo's or not in the Ubuntu Software Center than you will have to use the terminal to install a driver.
Some drivers are in the form of a ".run" file or script-
In order to install that type of driver you can either use the terminal to install it or you can just double click on the .run file.
To manually install a package you would have to use "dpkg -i"
To learn more about that just open the terminal and type man dpkg:-

When you have time look up Ubuntu and package management and that should help you.

Here are 2 threads were members here had a similar situation as you.
[http://ubuntuforums.org/showthread.php?t=1360685](http://ubuntuforums.org/showthread.php?t=1360685)
[http://ubuntuforums.org/showthread.php?t=1921413](http://ubuntuforums.org/showthread.php?t=1921413)

This mentions under Alsa
[http://wiki.hydrogenaudio.org/index.php?title=M-Audio_Audiophile_24/96](http://wiki.hydrogenaudio.org/index.php?title=M-Audio_Audiophile_24/96)

Pulseaudio may be creating conflict. You could disable it if you suspect that it's creating conflict with Alsa.
I would have to ask another member to help you because I am not in the habit of going into configuration files and disabling arguments w/o help--

---

