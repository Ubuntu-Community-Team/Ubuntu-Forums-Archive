---
title: "uninstall sound drivers"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by ty74 on 2012-06-19
I have ubuntu 12.04 and have no sound so I am following the guide found on: [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/). which states: "Upgrading your sound drivers may fix the nosound issue, you will need to make sure to uninstall the previous override before trying a new one." I do not know how to uninstall the previous override sound driver

---

### Post by jmfal on 2012-06-19
Open a terminal and run
```
 alsamixer  
```

Make sure all of your master volumes are not muted.
you have to use the arrow keys to navigate , and try selecting another sound card (F6>ENTER)
No sound yet. Try
```
 aplay -l   
```

And post the results.

---

### Post by ty74 on 2012-06-21
Thank for answering. I already tried the alsamixer. I unmuted the master volumes, But I could not switch the drivers. I think I only have 1 how do I find the right driver for my sound card.

---

### Post by jmfal on 2012-06-21
In the Multimedia and Video section of the forum  there are two stickies at the top, try those.

All I'm doing is taking from those,  so it will be a lot easier for you to go through them yourself at your own pace.

If you have a question  you can post back in this thread or post in the stickies thread.

---

### Post by ty74 on 2012-06-27
I did the first command on the sound trouble shooting procedure by mark rijckenberg. the command: **sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`** ruined my light spark and gnash combo. I re installed gnash and updated light spark. No it plays the video but I cannot pause it and I still have no sound. Can you tell me what the command did and how I can reverse it. I would greatly appreciate it.

---

### Post by jmfal on 2012-06-27
HI TY74'
 It looks like the command added a ppa and the alsa soundbase and all that other code, I'm not sure of yet.

Did you follow the rest of the howto??
You need to. Just running that command won't fix it, you need to follow it through at least to step 7. 
Post back if you have any problems.

---

### Post by ty74 on 2012-06-29
I am stuck after step 3 when it says" **After upgrading ALSA and rebooting the computer make sure that the ALSA driver version, library version and utilities version are all exactly the same version number. **"

The Terminal output after running the ALSA information script should contain something like this:

# ALSA Version

# Driver version: 1.0.25

# Library version: 1.0.25

# Utilities version: 1.0.25

My driver version is 1.024 all the rest are the same. How do I update ALSA driver version?

---

### Post by jmfal on 2012-06-29
Try updating/upgrade again then reboot and and check that list . 

Sometimes you need to reboot for changes to take effect.

---

### Post by jmfal on 2012-06-29
If the "# ALSA version"  won't update to the newer version , open the Update manager >>
click on settings >> click on other software tab >> and put a check in the two boxes for the ppa that was installed in the first command of the how-to..

---

### Post by ty74 on 2012-07-02
I had the speaker plug in the wrong slot. I did not know I had to move the speaker to a different slot. I thought if it work on windows it should work for ubuntu. thanks for your help jmfal.:p

---

