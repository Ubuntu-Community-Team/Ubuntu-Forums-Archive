---
title: "Sound not working"
date: 2015-03-31
forum: New to Ubuntu
---

### Post by brandon27 on 2015-03-31
hi, im not very good with computers and i havent had ubuntu that long but i cant seem to get my sound to work?
its picking up my sound card but its not playing sound any help is highly appreciated.

Thankyou in advance

---

### Post by sandyd on 2015-04-01
*Moved to New to Ubuntu*

---

### Post by newb85 on 2015-04-01
Please give us more detailed info about your sound card.  The output of the following would be helpful
```
sudo lshw -C sound
```

All the command does is "list hardware" with detailed information.  The "-C" narrows it to a category--in this case, sound.

It will ask for a password.  It wants your user password (set up when you installed Ubuntu).  It won't give you any visual feedback as you type the password.

---

### Post by dino99 on 2015-04-01
to be able to access the internal pulseaudio settings, you need to install 'paman'

sudo apt-get install paman

then from the Sound menu, select 'pulseaudio volume control' you have two tabs: 'output devices' & 'configuration' where you need to test/find the good settings for your hardware. This should be automatically done, but it is badly done and known/met by many users (including myself with the latest upgrade). Hopes this will be fixed soon.

---

### Post by brandon27 on 2015-04-01
newb85 i typed in your command and it said this
       description: Audio device
       product: NM10/ICH7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:44 memory:fdff8000-fdffbfff
i now have no idea of what to do XD

i also downloaded what 9d9 said to download and again have no idea what to do.
sorry i really am bad with techy stuff like this
thankyou for the help though

---

### Post by Geoffrey_Arndt on 2015-04-02
And we can assume you checked the "systems settings>sound config." and muted is not selected?  ALso, the "play sound through" . . . speakers (built in audio) are highlighted (selected)?

---

### Post by newb85 on 2015-04-04
Okay, let's try this.


We need to add a kernel module to a blacklist, and the easiest way to tell you to do that is using gedit (a graphical text editor utility). To do that, you'll need to use gksudo, which isn't installed by default, so:
```
sudo apt install gksu
```


We want to add the following line to the file /etc/modprobe.d/alsa-base-blacklist.conf.
```
blacklist i82975x_edac
```


To open that file with gedit:
```
gksudo gedit /etc/modprobe.d/alsa-base-blacklist.conf
```


Copy that line (the one starting with blacklist) to the end of the open file (on a new line if the file isn't empty). You should be able to simply highlight and drag-and-drop it from your internet browser. Once that's done, save and close.


Finally,
```
sudo modprobe -r i82975x_edac
sudo alsa force-reload
```

---

