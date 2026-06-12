---
title: "Unable to install alsa driver for Realtek ALC1150"
date: 2015-09-26
forum: New to Ubuntu
---

### Post by blackegg13 on 2015-09-26
Hi everyone

I'm new to ubuntu and linux. I'm facing problem with no sound from my on-board sound card ALC1150. Before doing anything I had ATI HDMI sound output from graphic card.

I have downloaded drivers from realtek website (3.0) and followed included install manual. After installation, the output list only have 'dummy output' option and ATI HDMI is now gone, so I have no sound at all.
I tried few help tutorials over the web but nothing worked ([this]("http://askubuntu.com/questions/457619/sound-not-working-in-ubuntu-14-04")). Aplay shows: device_list:268: no soundcards found... 

Can anyone help me with this problem please.

---

### Post by cariboo on 2015-09-26
The first thing I'd do is remove the driver, and bring your system back to the way it was before you installed the driver. Hopefully this will allow the audop hardware to be detected. Then in a terminal open alsamixer, and make sure all the levels are turned up. Once you are happy with the way things work, press Esc, then at the prompt type:

```
sudo alsactl store
```

---

### Post by grahammechanical on 2015-09-26
On my system with an onboard Intel HD audio controller and an Nvidia graphic card I found that once I started using an HDMI connection from the graphic adapter to the digital TV that I am using as a monitor that Sound Settings gives me an option to use the graphic adapter HDMI Audio Controller and no other option until I connect an audio cable to the motherboard audio line-out port or the headphone port. Then I am given options to switch the audio output source to the motherboard audio controller. 

Regards.

---

### Post by blackegg13 on 2015-09-27
How can I uninstall that driver? Thanks

---

### Post by blackegg13 on 2015-09-27
Never mind I managed to sort it out using [this]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS") wiki page. I have downloaded vivd package and followed instructions. Thanks for help :)

---

