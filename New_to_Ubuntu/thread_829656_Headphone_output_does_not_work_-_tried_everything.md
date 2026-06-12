---
title: "Headphone output does not work - tried everything"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by willis575 on 2008-06-15
I have a Sony Vaio FZ320 with Intel HDA. The audio plays fine through the built in speakers, but does not play through the headphone jack. There are a ton of threads about this issue and I have spent all day trying them all... to no avail. Am I missing something here?

---

### Post by Fingel on 2008-06-15
make sure the headphones work :P

---

### Post by powerpleb on 2008-06-15
You could try opening a terminal and typing in 'alsamixer' and making sure the headphone jack volume is turned up.

---

### Post by willis575 on 2008-06-15
> **powerpleb said:**
> You could try opening a terminal and typing in 'alsamixer' and making sure the headphone jack volume is turned up.


Yep, volume is all the way up.

---

### Post by willis575 on 2008-06-15
> **Fingel said:**
> make sure the headphones work :P

lol... yes, they work =)


the sound plays out of the built in speakers, and simply continues to play out of the speakers when i plug headphones in.

---

### Post by roscal on 2008-06-15
You have to adjust your mixer.
I've been playing with this same issue all night :-)
Open your mixer (whatever you are using, probably click the volume control and click on mixer, eh)
Turn the volume right down on the stand alone speakers, and adjust your settings with the headphones on.
Pay particular attention to the VIA DXS slider (turn it up).
:guitar:
cheers, hope this might help you.

---

### Post by Nepherte on 2008-06-15
Add the following to the end of /etc/modprobe.d/alsa-base if it's not already there:
```
options snd-hda-intel model=vaio
```
and restart your computer.

---

### Post by willis575 on 2008-06-15
> **Nepherte said:**
> Add the following to the end of /etc/modprobe.d/alsa-base if it's not already there:
```
options snd-hda-intel model=vaio
```
and restart your computer.

thanks for your response but i've already tried that. if it helps ive tried EVERY thread here

[http://ubuntuforums.org/search.php?searchid=43048927](http://ubuntuforums.org/search.php?searchid=43048927)

The strange thing is, I have 8.04 running on another partition and the headphone jack works fine. All I had to do is install alsa from synaptic. The modprobe.d files on both partitions are identical. The only difference seems to be that on the working version, when I double click the sound icon and go to edit -> preferences, there is an option for microphone, and it is checked. On the non working partition I only have options for master and pcm. ='(

---

### Post by willis575 on 2008-06-15
bump

---

### Post by lswest on 2008-06-15
try this: ```
sudo modprobe snd_hda_intel
``` and try plugging the headphones in.  Also, what version of Ubuntu/Linux Distro are you using?  Pulseaudio in 8.04 got my headphone jacks working, and it works fine in ALSA or Pulseaudio on my ArchLinux install, using the module above.

---

### Post by willis575 on 2008-06-15
> **lswest said:**
> try this: ```
sudo modprobe snd_hda_intel
``` and try plugging the headphones in.  Also, what version of Ubuntu/Linux Distro are you using?  Pulseaudio in 8.04 got my headphone jacks working, and it works fine in ALSA or Pulseaudio on my ArchLinux install, using the module above.

AH! I tried reinstalling all the alsa stuff from synaptic and now I have NO sound! 

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

and when i ran what you asked, i got pages of errors

---

### Post by lswest on 2008-06-15
hmm, have you rebooted since re-installing alsa? and have you started the daemon with ```
sudo /etc/init.d/alsa start
```  Also, what does alsamixer tell you?  Oh, and have you installed the gstreamer plugins again (if they were uninstalled with alsa)?

---

### Post by willis575 on 2008-06-15
> **lswest said:**
> hmm, have you rebooted since re-installing alsa? and have you started the daemon with ```
sudo /etc/init.d/alsa start
```  Also, what does alsamixer tell you?  Oh, and have you installed the gstreamer plugins again (if they were uninstalled with alsa)?


ok, i restarted again and the sound is back, but still no headphones. this is what alsamixer tells me

```
Card: HDA Intel                                                              &#9474;
&#9474; Chip: SigmaTel STAC9872AK                                                    &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-18.75, -18.75]      
```

---

### Post by lswest on 2008-06-15
Is this Ubuntu 7.10, or some other distro/version?  And what does ```
lshw -C audio
``` tell you? (It should print out info corresponding to your sound card, but I could be wrong, don't have access to lshw from Arch these days).

---

### Post by willis575 on 2008-06-15
> **lswest said:**
> Is this Ubuntu 7.10, or some other distro/version?  And what does ```
lshw -C audio
``` tell you? (It should print out info corresponding to your sound card, but I could be wrong, don't have access to lshw from Arch these days).

I am running Ubuntu 8.04 x86 32 bit. It's a fresh install, all updates applied. 


the lshw -C audio command just flashes a bunch of stuff to fast to read.

---

### Post by willis575 on 2008-06-15
ha! it works! i followed this thread AGAIN and now the headphones work as they should. thanks to everyone who tried to help!

[http://ubuntuforums.org/showthread.php?t=677331](http://ubuntuforums.org/showthread.php?t=677331)

---

### Post by lswest on 2008-06-15
> **willis575 said:**
> ha! it works! i followed this thread AGAIN and now the headphones work as they should. thanks to everyone who tried to help!

[http://ubuntuforums.org/showthread.php?t=677331](http://ubuntuforums.org/showthread.php?t=677331)

great, glad it works!  And about the lshw command, you can do it like this: ```
lshw -C audio|less
``` to be able to scroll through the output.  Anyways, glad it works.

---

