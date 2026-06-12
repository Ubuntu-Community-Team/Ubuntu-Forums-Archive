---
title: "[SOLVED] turning off onboard sound or setting priority"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by jasontu on 2008-06-04
I had gotten everything to work just as I wanted it... then I restarted and Ubuntu decided that my onboard sound took priority over my sound card.  I noticed that in the device selection menu for volume settings my Intel HDA was now 0 and my sound card was now 1.

How do I switch them back or turn off Intel HDA entirely?

Thank you!

---

### Post by iaculallad on 2008-06-04
Post the output of your **lsmod | grep snd**, so we know how we could change your audio priority.

```
lsmod | grep snd
```

---

### Post by jasontu on 2008-06-04
snd_cmipci             38528  3 
gameport               16008  1 snd_cmipci
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_cmipci,snd_hda_intel,snd_pcm_oss
snd_opl3_lib           12928  1 snd_cmipci
snd_mpu401_uart         9728  1 snd_cmipci
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  2 snd_hda_intel,snd_opl3_lib
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  24 snd_cmipci,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_mpu401_uart,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

---

### Post by jasontu on 2008-06-04
I also noticed that when I run alsamixer it only gives me control over the Intel sound.

I can hear through the sound card through my music playing application though... strange.

---

### Post by hexanol on 2008-06-04
If you have a sound card installed in your PC and also has onboard sound capabilities, I personnaly would suggest you to disable the onboard sound via your computer's BIOS. The only problem is that it may be complicated to do this depending on your knowledge of "computers". But that way, you'll never have to worry again about your onboard sound (your PC might also consume a little bit less of power that way, but something ridiculously low, like less than 1 watts).

---

### Post by iaculallad on 2008-06-04
Add the following lines below to the bottom of your /etc/modprobe.d/alsa-base file and then reboot (Changing Priority): 

#-------------------------------------
# Force soundcard priority number
options snd_cmipci index=0
options snd_hda_intel index=1
#-------------------------------------

Or you can disable your On-board audio by:

-Open your /etc/modprobe.d/blacklist for editing
```
sudo gedit /etc/modprobe.d/blacklist
```
-Append (the line of code below) to the bottom of your /etc/modprobe.d/blacklist file and do a reboot.
**blacklist snd_hda_intel**

---

### Post by jasontu on 2008-06-04
Bingo!

That worked and it was pretty painless!
... now if I can just keep my GPU fan from ramping up to "deafening" mode everything would be perfect.  I'll keep patrolling the forums.

Many many thanks!

---

### Post by iaculallad on 2008-06-04
Im glad to know that it worked :) Enjoy the sound..

---

