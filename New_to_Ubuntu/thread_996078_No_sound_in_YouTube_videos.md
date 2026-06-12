---
title: "No sound in YouTube videos"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by graceful1 on 2008-11-28
I have recently installed Ubuntu 8.04 on my desktop machine. While system sounds (like the startup sound) work just fine, and sound works when playing movies with Totem, I cannot get any audio when playing videos on YouTube (using the FlashPlayer 9 plugin). My sound card is Ensonique AudioPCI.

I should also mention, that when I boot into Windows XP on the same machine, I *am* able to hear sound in YouTube videos.

Thanks for your help.

---

### Post by gandaran on 2008-11-28
install flash 10, get the .deb package here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/), remove flash 9 first, this should fix the sound problem

---

### Post by herteljt on 2008-11-28
This link might be helpful.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by ged5 on 2008-11-28
I had a similar problem in 8.1 , you have to install some proprietary codecs , I followed this guide and got it working.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=firefox3+no+sound](http://ubuntuforums.org/showthread.php?t=766683&highlight=firefox3+no+sound)


Ged

---

### Post by graceful1 on 2008-11-28
> **gandaran said:**
> install flash 10, get the .deb package here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/), remove flash 9 first, this should fix the sound problem

I have installed Flash 10, but unfortunately, there's still no sound in YouTube. :(  Thanks, anyway.

---

### Post by graceful1 on 2008-11-28
I tried following these instructions that were on the guide you pointed me to:

----
If you're running an earlier version of Ubuntu and Firefox (pre-Hardy and Firefox 2x), and you don't have any sound in Flash videos, or you notice strange random behaviour by Firefox, you should try this next solution. Make sure you have the package "alsa-oss" from Part 1 and then paste this command into the terminal:

gksudo gedit /etc/firefox/firefoxrc

Edit the line "FIREFOX_DSP=”none”" and change "none" to "aoss". Then close and save the file. Restart Firefox.
---

Unfortunately, it didn't work. Of course that's probably because I *am* using Hardy Heron, but I am getting desperate.

Thanks.

---

### Post by residualbit on 2008-11-28
Go to the Add/remove menu, make sure "all available applications" is selected and install the "Ubuntu Restricted Extras" package. That should fix it.

---

### Post by smo0th on 2008-11-28
[this]("http://ubuntuforums.org/showthread.php?t=766683") thread is great for all your flash/audio/video needs:

:)

---

### Post by gandaran on 2008-11-28
> **graceful1 said:**
> I have installed Flash 10, but unfortunately, there's still no sound in YouTube. :(  Thanks, anyway.
did you remove the flash 9 first?
okay if flash 10 still doesn't fix the problem then this is the guide to follow [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) but undo anything you have done so far or you mite mess up the system

---

### Post by graceful1 on 2008-11-28
> **nkirk1 said:**
> Go to the Add/remove menu, make sure "all available applications" is selected and install the "Ubuntu Restricted Extras" package. That should fix it.


Thanks, but I already had that package installed. Can you think of anything else?

---

### Post by graceful1 on 2008-11-28
> **gandaran said:**
> did you remove the flash 9 first?
okay if flash 10 still doesn't fix the problem then this is the guide to follow [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) but undo anything you have done so far or you mite mess up the system

I am not sure what you mean by undoing what I have done.
Do you mean I need to uninstall Adobe Flash Player 10?

---

### Post by graceful1 on 2008-11-28
> **gandaran said:**
> did you remove the flash 9 first?
okay if flash 10 still doesn't fix the problem then this is the guide to follow [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) but undo anything you have done so far or you mite mess up the system

I ran into a problem when I started following the directions:

grace@cunctator:~$ sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package padevchooser is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package padevchooser has no installation candidate

---

### Post by gandaran on 2008-11-29
> **graceful1 said:**
> I ran into a problem when I started following the directions:

grace@cunctator:~$ sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package padevchooser is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package padevchooser has no installation candidate
check if all repositories are enabled, system » administration » software sources, in ubuntu software enable the first 4 channels then run **sudo apt-get update**
now if you have read the guide carefully you'll have found out by now this is to fix the flash 9 sound problem, it's better you remove flash 10!   
I still find it hard to believe flash 10 didn't work as you didn't have any other sound problem, just in flash, are you 100% sure you still don't have any other flash installed? remember the ubuntu-restricted-extras installs flash 9!

edit:
just to check what flash you have installed, post the output of **locate libflash**
and also the output of typing this code in firefox url bar **about: plugins** (without spaces)

---

### Post by sadalmelik57 on 2009-01-01
I struggled with this for weeks and finally discovered I needed to "move stream" in the pulse audio volume control.  

To do this have Firefox opened to a You Tube video that is playing.

[LIST]
[*]Open the Pulse Audio Device Chooser from Applications/Sound and Video.
[*]Click on the Pulse Audio icon and choose Volume Control. 
[*]Choose the playback tab and you should see the sound card listed there.  
[*]Click the down arrow button on the right side and you get a menu that includes Move Stream.
[*]Choose the radial button for your sound card.
[*]Go to Output Devices and use the same down arrow button to make your sound card the Default.
[*]Go to Input Devices and also choose your sound card as the default device.
[/LIST]

In my case, it appears to be trying to use the motherboard's built in sound card, instead of the installed Audigy Sound Blaster.

I hope this helps someone else!

---

