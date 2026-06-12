---
title: "[SOLVED] Asus K8V-MX, 8.04, No Sound"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by chackoge on 2008-09-14
Hi- I'm running 8.04 on an an Asus K8V-MX motherboard with an AMD Sempron 2800+. I've never managed to get  sound other than system beeps out of this set up even when running earlier versions of Ubuntu. The motherboard has an integrated SoundMax card. I've looked at related threads and tried all the fixes suggested on various forums with no luck. The speakers and microphone work when plugged into Windows or OS X boxes. 

Current setup:

System -> Preferences -> Sound

ALSA selected on all. Clicking on Test seems to have no effect. Selecting any of the other choices: Autodetect, OSS, VIA8237, Pulseaudio also doesn't work for playback. None of the sliders in the Volume control are set to Mute. 

Any help is much appreciated. Thanks.

---

### Post by k33bz on 2008-09-14
here you go, here is a sound driver for your mother board that is compatible with linux

[http://www.driverstock.com/ASUS-K8V-MX-driver-download/6-9-10118/index.html]("http://www.driverstock.com/ASUS-K8V-MX-driver-download/6-9-10118/index.html")

matter a fact, it has all the drivers for your motherboard that is compatible with Linux

---

### Post by chackoge on 2008-09-14
Thanks. In fact, I did follow that link earlier and install the driver but that didn't solve the problem. GC

---

### Post by k33bz on 2008-09-14
> **chackoge said:**
> Thanks. In fact, I did follow that link earlier and install the driver but that didn't solve the problem. GC

oh, then, I dont know, Im not that good on trouble shooting for sound, and I dont have that paticular Asus motherboard. I have a different one, that worked out the box.

---

### Post by bobnutfield on 2008-09-14
Have you checked to see if all the sound modules were loaded?

> sudo lsmod | grep snd

---

### Post by chackoge on 2008-09-14
Here's the output from lsmod | grep snd

snd_via82xx            33448  3 
gameport               17936  1 snd_via82xx
snd_mpu401_uart        11264  1 snd_via82xx
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_via82xx_modem      18572  0 
snd_ac97_codec        123224  2 snd_via82xx,snd_via82xx_modem
ac97_bus                3840  1 snd_ac97_codec
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                92168  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              27912  2 snd_seq,snd_pcm
snd_page_alloc         13200  3 snd_via82xx,snd_via82xx_modem,snd_pcm
snd                    70856  19 snd_via82xx,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              10400  1 snd

---

### Post by bobnutfield on 2008-09-14
Well, the Via module is correct for that soundcard and it appears to be loaded.  Open a terminal and type:

> ps aux >/dev/dsp

Do you get a scratchy rough sound?

---

### Post by chackoge on 2008-09-14
sudo ps aux > /dev/dsp

No sound at all. GC

---

### Post by bobnutfield on 2008-09-14
OK, now try just to make sure the card is recognized:

> asoundconf list

---

### Post by chackoge on 2008-09-14
~$ asoundconf list
Names of available sound cards:
V8237

---

### Post by bobnutfield on 2008-09-14
Hmmm....if you have Alsa in the selection box in System>Pref>Sound, then something must be wrong with Alsa.  I have seen others with similar problems correct it by installing ALSA from source.  But two things first.  Try uninstalling and then reinstalling ALSA.  Go to Synaptic Package Manager and select Alsa-base for reinstallation.  Try that before trying to install from source.  The is system is doing all it is supposed to with regard to your card, so, unless someone else chimes in and suggests something different, it appears that something is out of whack with ALSA.  Also, study the following:

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

It does not appear to be hardware since they work in Win and Mac.

---

### Post by chackoge on 2008-09-14
Hmm! I removed and reinstalled all the ALSA modules with Synaptic instead of just Alsa-base. That didn't go down too well.. the machine crashed and won't come up in GUI mode so I;m trying to get it back up. My fault for not reading your suggestion carefully.GC

---

### Post by bobnutfield on 2008-09-14
Not sure what you removed, but if you can get into a terminal login with networking just reinstall the gnome-desktop.

> sudo apt-get install gnome-desktop

You may have inadvertently removed some desktop components when you removed the mdoule.  I had only intended that you reinstall alsa-base.

---

### Post by chackoge on 2008-09-15
I had to reinstall but that gave me the opportunity to make a clean start. I worked my way through the troubleshooting guide with no luck so I reported this is a possible bug. It's interesting, Aplay and lspci show that the via 8237 is recognized. I also went back and looked at the BIOS and sound isn't disabled there. I also noticed that I could get one channel from the earphone jack on the front panel. So I disconnected the front panel audio but I still get nothing out of the rear panel audio jacks. GC

---

### Post by chackoge on 2008-09-16
After working my way through the very helpful link that Bob provided, I thought some more and pulled the cover off the box. Turns out that the FP-audio 10-1 connector should have jumpers on pins 5-6 and 9-10. Else sound doesn't go to the ports on the back. I scrounged a couple from a local repair store and I have sound now. The front panel audio connector doesn't work but I don't care. Thanks for the help. I learnt a lot in solving this problem. GC

---

### Post by vdubbus77 on 2008-09-28
chackoge, omg THANK YOU!!!!!!!!!!!!! I have tried everything to get this sound to work. This was my exact problem. I pulled an old asus board and put it in my HTPC case never thinking the old front panel sound was jumpered in the harness. Thanks again!

---

### Post by chackoge on 2008-09-29
Well, thanks are really due to Bob Nutfield for helping me systematically walk through the software issues which forced me to rethink the problem and discover that it was really about hardware configuration. I'm glad the thread was helpful though. Regards. GC

---

### Post by nickpj on 2010-07-16
Very helpful thread! Had the same problem on an old Asus K8V-MX motherboard, assumed it was a software problem in MythBuntu 10.04, tried various things in software for hours, but adding those 2 jumpers got sound working on the rear connectors, so it was a hardware problem all along. Thank you so much for posting the solution!

---

