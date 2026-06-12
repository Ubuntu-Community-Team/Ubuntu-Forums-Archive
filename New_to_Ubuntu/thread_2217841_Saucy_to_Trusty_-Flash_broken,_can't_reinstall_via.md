---
title: "Saucy to Trusty -Flash broken, can't reinstall via Ubuntu Software Center"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-04-18
Upgrade to Trusty seems to have gone well except for broken flash.  The normal ubuntu flash downloader seems to consistently fail.  What is the method in terminal via apt to purge and force reinstall?   Thanks much.

---

### Post by bapoumba on 2014-04-18
Please enable the multiverse repositories and install pepperflashplugin-nonfree, then run
```
sudo update-pepperflashplugin-nonfree --install
```

---

### Post by monkeybrain20122 on 2014-04-18
> **bapoumba said:**
> Please enable the multiverse repositories and install pepperflashplugin-nonfree, then run
```
sudo update-pepperflashplugin-nonfree --install
```

This only works for Chromium. OP doesn't say he/she uses chromium.

@Op

Just purge and reinstall flashplugin-installer

---

### Post by bapoumba on 2014-04-18
> **monkeybrain20122 said:**
> This only works for Chromium. OP doesn't say he/she uses chromium.

@Op

Just purge and reinstall flashplugin-installer

/o\
Still had my terminal open with the last commands I ran and copied them over before I closed it.. Pretty sorry :)

---

### Post by JeQhdMD on 2014-04-18
Just tried again - - this time using the terminal to "sudo apt-get install flashplugin-installer" still won't install completely as YouTube promptly advises I need flash plugin.  I will install Chrome, but prefer to run Firefox.   Never had an extended problem like this in several years of running ubuntu and other distros.   Have used Synaptic and Ubuntu Software Center to completely remove and reinstall.  No joy.  

Any other things I can check?   

I do get the ubuntu app that advises the installer couldn't fetch all the files and finish install - but, clicking on "do this action now" doesn't solve the issue (a brief error windows pops up but disappears before I can read it).

---

### Post by moster on 2014-04-19
Try searching for repositories for "pepper", it will find pepper flash, install it from there. Terminal command did not work for me. I am on Trusty x64.

---

### Post by oscarivera9 on 2014-04-21
> **JeQhdMD said:**
> Just tried again - - this time using the terminal to "sudo apt-get install flashplugin-installer" still won't install completely as YouTube promptly advises I need flash plugin.  I will install Chrome, but prefer to run Firefox.   Never had an extended problem like this in several years of running ubuntu and other distros.   Have used Synaptic and Ubuntu Software Center to completely remove and reinstall.  No joy.  

Any other things I can check?   

I do get the ubuntu app that advises the installer couldn't fetch all the files and finish install - but, clicking on "do this action now" doesn't solve the issue (a brief error windows pops up but disappears before I can read it).

I get the same message when trying to use the youtube app, but when I actually click on any other video or when I'm using youtube through Firefox, everything works fine.  I think that message is there from some sort of advertisement; if it's the same thing that I'm looking at.  In other words, does youtube tell you that you need the new flash? or can you actually NOT watch any videos?

---

### Post by JeQhdMD on 2014-04-22
To clarify, I can watch all Youtube videos without problem when using Google's "Chrome" browser.   Further, if I'm using "Chromium", I cannot view Youtube videos that require flash, but I can hear the audio.  

Regarding pepper, it doesn't show up in a search using Synaptic or USC - - is there a PPA that needs to be setup?   I have the standard repos enabled.

But, I'm really more concerned about the failure on my 14.04 install (which was an upgrade vs clean install) - - in that I can't view any videos requiring flash while using Firefox (my preferred browser) .  Some videos will play using html5 but most media still requires flash.   It seems (even in other distros like Kubuntu) that flash updates are shaky at best.  Apparently, Canonical is aware of this and a couple 2-3 years ago, added a mechanism to fetch the codecs from Adobe if the normal update tool didn't succeed.  A separate window would pop up and advise the user to run a process to get the flash update code.   This is what's failing.   The fetch process is no longer working as there may be a file permission problem and the proper folder can't be unlocked.

At this point, since I did an upgrade versus clean install, I'm just going to create a Live-DVD and Live-USB Stick and do a clean install (that seems like my best bet).   I normally don't do upgrades, but this time I wanted to try it again and see if the result was good.   Well, it seems 95% good, but I'm consistently getting boot-up "system-error" messages advising me to send a report - - perhaps that's related to the flash plugin update install failures.

---

### Post by JeQhdMD on 2014-04-23
Ubuntu's Flash Update process cannot open & write latest codecs on my Acer 4830T laptop.  But on my Lenovo H410 desktop, the process works fine and I have access to the codec file (libflashplayer.so).  The location is owned by root (/usr/lib/flashplugin-installer/libflashplayer.so).   I want to copy the file to the Acer 4830T laptop, at the same location.   I plan to use a usb flash-stick as the mechanism.

But I fairly new to Ubuntu and _nautilus doesn't seem to offer a "open terminal here" option_ . . . so, could someone advise the proper command to copy the file from the desktop PC, write it to the flash-stick, and then copy from the flash-stick to the same location on the Acer laptop?  

A second file of 791 bytes also exists in the folders of each PC (install-plugin).   Could this file on the laptop be corrupt and thereby be causing the failure of the normal ubuntu update process?  Should I also copy this file along with the codec file? Or should I look at each file and see if any differences and editing if needed?

This is my plan to try and fix the issue listed in this thread:  [http://ubuntuforums.org/showthread.php?t=2217841](http://ubuntuforums.org/showthread.php?t=2217841)

---

### Post by bapoumba on 2014-04-23
> **JeQhdMD said:**
> To clarify, I can watch all Youtube videos without problem when using Google's "Chrome" browser.   Further, if I'm using "Chromium", I cannot view Youtube videos that require flash, but I can hear the audio.  

Regarding pepper, it doesn't show up in a search using Synaptic or USC - - is there a PPA that needs to be setup?   I have the standard repos enabled.


You have to enable the multiverse repositories for the pepperflash plugin.

---

### Post by bapoumba on 2014-04-23
There is one thing that I've been looking around for but cannot find a satisfying answer to : will it work ? I mean, copy the libflashplayer.so from one machine to the other ?
From this older (and for another purpose) post I think it can work, but I'm not sure : [http://ubuntuforums.org/showthread.php?t=1839293&p=11523048#post11523048](http://ubuntuforums.org/showthread.php?t=1839293&p=11523048#post11523048)

If so,
You'll need to go to a terminal and run, from the Lenovo where the .so file is
```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /path_to_your_removable_media/
```
Rename the old .so on the Acer
```
sudo mv /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.so_old
```
Then with the removable media plugged into the Acer
```
sudo cp /path_to_your_removable_media/libflashplayer.so /usr/lib/flashplugin-installer/
```

And make sure the permissions are correct
```
cd /usr/lib/flashplugin-installer/
ls -la
```
Here is what I have
```
-rwxr-xr-x   1 root root      791 avril  8 22:41 install_plugin
-rw-r--r--   1 root root 17422820 avril 10 20:45 libflashplayer.so
```

Other than that, does the install fail on the Acer ? Any error to work with ?
The install_plugin file can be opened with any simple word editor (gedit for ex), so you can compare the two.

---

### Post by JeQhdMD on 2014-04-23
I have all the standard repo server sources enabled including multiverse.  In synaptic, a search for "Pepper" reveals:   "pepper 0.3.2-2 . . Source code repository statistics and report tool" . . . note that this machine is running Ubuntu 13.10 Saucy Salamander versus Ubuntu 14.04 Trusty Tahr.  Anyway, thanks for the tips, I'll be doing a fresh install from DVD and thereby replacing Saucy on 3 PC's today.  After that, if the flash update process is still as unreliable as it has been for the past 2-3 years, I'll just change my default browser to Chrome as everything works very well and seamlessly.  I just prefer a fully open application to one that's proprietary only - but I think I have a last resort manual method anyway to install the flashplayer by dropping in to /usr/lib/flashplugin-installer/libflashplayer.so (the actual codecs for enabling flash).

Thanks again.

---

### Post by JeQhdMD on 2014-04-23
Thanks much Bapoumba!   I've also updated the other related thread on this topic, . . . if the mods could combine that would be best.  I added this thread as this possible solution took a different angle on the issue - - that is, will it work and what's the terminal method as Nautilus doesn't seem as flexible as Dolphin file manager (although I seem to recall something about starting Nautilus via gksu nautilus . . ).

Again, thanks for the useful info above, I'll save it to my knowledge db (using CherryTree v0.32).

By the way . . . the Acer Timeline laptop never did have the codecs file in that folder - the updater apparently could not open the folder and write to it (so nothing to rename) ?? . . .

Greg

---

### Post by bapoumba on 2014-04-23
Well, yes, I can merge the two threads. The conversation may look a little awkward as posts will be presented by timestamps. But for now, did it work ?
Edit: threads merged.

---

### Post by JeQhdMD on 2014-04-23
Yes - it works well enough, (I should have just appended the orig. )   Anyway, wish me luck on my reinstall.  I'll still have a couple backup OS's (win7 & Kubuntu 12.04 on their own partitions).

---

### Post by bapoumba on 2014-04-23
Thanks :)
Wishing you all the best of luck. Please do your backups, and mark your thread as solved (in Thread Tools).
See you around!

---

