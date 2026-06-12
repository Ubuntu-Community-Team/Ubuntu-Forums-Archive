---
title: "No sound - Audiocard [ID 236 Analog]"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by alg2 on 2016-03-06
Hi everybody,

It's my first time with Linux and Ubuntu 14.04 (I'm using Pinguy specifically).  My laptop is a Lenovo Ideapad 500S

I managed to get Wifi working after a few days and here is my new problem.  No sound on internal speakers or headset.  I've been all over the ALSA settings, mute, etc

[B]
Output of      aplay -l: [/B]

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ID 236 Analog [ID 236 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



From what I can tell, ID236 is not on the list of driver options in snd-hda-intel
based on some other suggestions, I've adjusted the following settings

[B]/etc/modprobe.d  
      [/B]options snd-hda-intel probe_mask=1
      options snd-hda-intel model=ideapad

for model, I've also tried "thinkpad" "lenovo" and "laptop"


Any other suggestions?  Thanks in advance!

---

### Post by trag on 2016-03-07
Install Pulseaudio Volume Control from the Software Centre,this should do the trick

---

### Post by alg2 on 2016-03-11
Pulse Audio is on, when I play music, the bar flashes showing output.  I just can't hear anything.  I'll try re-installing it

---

### Post by alg2 on 2016-03-11
Within Alsa I have 2 soundcard options:
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Sound Card &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; 
&#9474;-   (default)           
&#9474;0   HDA Intel PCH       
&#9474;29  ThinkPad Console Audio Control

It doesn't help to change to 29,  still no sound (and no mixer bars in ALSA)
Since      "ThinkPad Console Audio Control" isn't showing up on aplay, is it possible that is the issue?

---

### Post by alg2 on 2016-03-19
Hi folks, Is this thread still open?  To follow-up on this:

These are the commands I used to remove and then re-install pulseaudio. 

sudo rm -r ~/.config/pulse; pulseaudio -k
sudo dpkg --configure -a
sudo apt-get install pulseaudio

pavucontrol         - launches pulseaudio

My test speakers both make no sound.

---

