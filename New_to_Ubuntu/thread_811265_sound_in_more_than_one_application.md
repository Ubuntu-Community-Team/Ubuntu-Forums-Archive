---
title: "sound in more than one application"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-29
How do i fix the problem where sound only plays in one application at a time?

---

### Post by llama320 on 2008-05-29
First off, I'm assuming you're using Hardy, otherwise everything below probably doesn't apply. anyways...

I had the same problem..here's what I did:

Go to System > Preferences > Sound: change all "Sound Playback" options to PulseAudio

Now, if you want to get flash working (i.e. youtube, etc)..this is a problem with pulseaudio and flash not playing nice. After you've changed everything to pulseaudio

```

sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

Now restart and it will (hopefully) work

if this doesn't work, you may want to set your audio settings on your audio player to pulseaudio (I did this with amarok..not sure if other audio players have this option)

Good Luck

---

### Post by wolfen69 on 2008-05-29
[THIS]("http://ubuntuforums.org/showthread.php?t=776739") worked for me.

---

### Post by balaknair on 2008-05-29
A little more detail on what version of Ubuntu you're using would be helpful. Sound for only one app at a time sounds like you're using OSS, which is an older sound codec for Linux.


If you're using **Ubuntu 8.04**, it comes with Pulse Audio, which as far I know supports sound on multiple applications with most Sound cards. You might have to enable it in sound preferences(System Menu> Preferences> Sound---> Set the devices to Pulse Audio and then test sound. If it works, then in the next tab(Sounds) enable Software Sound Mixing. Try using two different apps for sound.
If this doesn't work you might need to modify or update ALSA codecs/ configuration, for which we need to know what sound cards you have installed.


**For older versions of Ubuntu**, to install and configure pulseaudio use this guide
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

If you still have problems, please reply in this thread and state what issues remain.
If your problem is fixed, please tell us what steps worked for you, and mark this thread as solved.

---

### Post by Kelen.Chang on 2009-04-25
found this thread by Google. and help me solved my issue.

---

