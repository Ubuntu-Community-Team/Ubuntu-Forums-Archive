---
title: "[SOLVED] Sound is MESSED UP!  PLEASE HELP!!!"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Archie69 on 2008-08-10
Hi again,

I posted here a day ago cause I'm having a little difficulty with the set up of ubuntu an my Acer Aspire 5920.  I seem to have everything installed properly however there seems to be a problem with the sound card.

The card is an "Audio (Intel High Definition Audio (HDA))"

The most info I found on its problems were: 
"Sound works but plugging a headphone does not mute front speakers, no solution for Virtual SurroundSound 

Internal microphone outputs to speakers but capture does not work"

Is there anything I can do to resolve this issue because I am goin out of my mind, or is this sound card just a lemon on ubuntu?

Thanks

---

### Post by Locutus_of_Borg on 2008-08-10
your problem is that plugging in head phones does not mute the speakers?

---

### Post by Archie69 on 2008-08-10
There are a host of problems, however this is the most information I have found regarding this specific model.  As of now sound is not functioning period.

I'm also looking at this link:

[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920G](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920G)

I appreciate the help.

---

### Post by Locutus_of_Borg on 2008-08-10
Try the following:

```
sudo -i
alsaconf
alsamixer
modprobe snd_hda_intel
usermod -a -G audio YOUR_USER_NAME
```

See if any of that helps

---

### Post by Archie69 on 2008-08-10
YOU ARE AWESOME PAL.

Sound works great.
Thanks a lot.

---

### Post by Locutus_of_Borg on 2008-08-10
okay good, now to make sure it works after a reboot, do this:

```
sudo echo "snd_hda_intel" >> /etc/modules
sudo alsactl store
```

this will make sure your volume settings get saved, and the correct module for your soundcard get loaded at boot.  I am not positive that the alsactl is even needed, but it can't hurt to be safe

---

### Post by fenT1 on 2008-08-10
> **Locutus_of_Borg said:**
> Try the following:

```
sudo -i
alsaconf
alsamixer
modprobe snd_hda_intel
usermod -a -G audio YOUR_USER_NAME
```

See if any of that helps

ok im in the dark the whole code ina single line?

---

### Post by Locutus_of_Borg on 2008-08-10
> **fenT1 said:**
> ok im in the dark the whole code ina single line?

each line seperately

sudo -i opens a root shell

alsaconf configures alsa and your soundcard, it will create a menu where you basically just press yes for everything

alsamixer lets you change volume, just make everything as high as it can go

modprobe snd_hda_intel loads the module for the intel soundcard

usermod adds a user to a group, in this case the audio group

---

### Post by Archie69 on 2008-08-11
Wow, I spoke too soon.

Alright... Basically... this was done

In volume control make sure that in File -> Change device the "HDA Intel (alsa mixer)" is selected.
Go to Edit -> Preferences and select all tracks in the list.
Unmute and increase volume on "PCM", "Surround", "Center", "Side" and "LFE". Sound should work nicely now. Optionally mute the micophone sliders.\

to resolve the "no sound" issue but now I cant get sound from the working speakers.

---

### Post by Archie69 on 2008-08-11
That didn't make much sense now hat i read it. Basically, sound comes from the speakers from the notebook but nothing happens when I plug in external ones.  What could cause that?

---

### Post by Vaedrah on 2009-01-11
Hi Loctus_Of_Borg et al

I have a similar audio problem with an acer aspire 5920 in that the internal speakers no longer work. I tried your commands in the terminal box;

sudo -i
alsaconf
alsamixer
modprobe snd_hda_intel
usermod -a -G audio YOUR_USER_NAME 

but alsaconf refused to acknowledge any file. Also alsamixer bought up a graphical display but the sliders don't respond.

The headphone works with external speakers.

The notebook used to run Vista but then I managed somehow to loose its hard drive. This had 2 main partitions and two knobby end ones. I suspect one of these lost its contents. After than I couldn't reinstall windows but Ubuntu 8.04 seems to work. However the internal speakers didn't work.

I've also tried Sun VirtualBox on top of Ubuntu but that also didn't work (I has problems seeing the DVD drive). I am quite "green" with s/w so I appreciate any suggestions.

Thank in advance!

---

