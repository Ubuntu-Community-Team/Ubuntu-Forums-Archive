---
title: "Sound stopped working suddenly"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by vijayanand_sodadasi on 2008-11-28
Hi there,

All of a sudden the sound stopped working.  I have a dual boot with Windows XP (wubi) and sound works fine in XP.  I can't hear the start up sound as well.  I don't remember what changes I did to the system.  I installed Skype and Cheese for video capture recently.  I searched the forums a lot and tried all the options available on the System->Preferences->Sound. I am using Ubuntu 8.04.

> vijay@vijay-laptop:~$ lspci|egrep -i audio
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)

vijay@vijay-laptop:~$ cat /proc/asound/devices 
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer

vijay@vijay-laptop:~$ cat /proc/asound/cards
 0 [A5451          ]: ALI5451 - ALI 5451
                      ALI 5451 at 0x1000, irq 11

Can somebody suggest me something please?

Thanks,
Vj.

---

### Post by a0u on 2008-11-28
I would look through [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) first.

---

### Post by vijayanand_sodadasi on 2008-11-28
> **a0u said:**
> I would look through [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) first.
Thanks, I will go through that and will post the results.

I followed the steps in the above guide and everything seems to be set up properly.  As a last resort, I reinstalled the drivers as mentioned in the document:

> sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

Still no sound.  I'm thinking about reinstalling Ubuntu.

---

