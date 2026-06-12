---
title: "Sound not working"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by Webgazer on 2012-07-25
I bought a new computer and installed Ubuntu on it about a month and half ago, and my sound started having problems about two weeks after the OS was installed, intermittently not working.

For the last two weeks or so though, the sound has stopped working altogether. This command:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

 found [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"), used to sometimes fix it, but now after every reboot, the sound doesn't work.

Can any one guide me in fixing it?

---

### Post by sid0972 on 2012-07-25
go to terminal and type

killall pulseaudio

---

### Post by Webgazer on 2012-07-25
Do I need to reboot afterward or should it work immediately after the command?

Edit: because I tried it now and the sound still doesn't work.

---

### Post by sid0972 on 2012-07-27
no you were not supposed to reboot, it should work at the moment itself
but you would have figured out that by now
and i am a noob in this, maybe some experienced member can help you

---

### Post by sandyd on 2012-07-27
> **Webgazer said:**
> I bought a new computer and installed Ubuntu on it about a month and half ago, and my sound started having problems about two weeks after the OS was installed, intermittently not working.

For the last two weeks or so though, the sound has stopped working altogether. This command:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

 found [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"), used to sometimes fix it, but now after every reboot, the sound doesn't work.

Can any one guide me in fixing it?
post output of
```

aplay -l
lspci

```

---

### Post by dadinck on 2012-07-31
I had many instances where I could not use the sound with Ubuntu 12.04. I lost the sound control in the tool bar. I then tried to run the pavucontrol only to find out it wasn't installed.

Once I installed the pavucontrol, I found out that the HDMI was selected, even though nothing was plugged in there. I just wanted to built-in speakers on the laptop to be the output. I turned off the HDMI output and then I was able to hear sound once again.

---

### Post by Webgazer on 2012-08-12
> post output of
Code:
aplay -l
lspci

I got this:

card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

