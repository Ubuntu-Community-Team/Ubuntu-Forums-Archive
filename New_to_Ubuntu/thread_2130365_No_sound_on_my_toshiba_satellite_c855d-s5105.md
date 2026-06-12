---
title: "No sound on my toshiba satellite c855d-s5105"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by Reina on 2013-03-29
Hello everyone, I recently got a toshiba satellite c855d-s5105, and while after turning off UEFI and secureboot worked and Lubuntu installed  I've found that there is no sound. I believe the built in sound card is a realtek ALC2269VB. Are there any fixes that could get the sound to work? Sorry, and thanks in advance.

---

### Post by JLeon85 on 2013-03-29
There's a common problem on Lubuntu where the volume keys on your keyboard will not un-mute the sound. You can make sure by clicking on your volume indicator and seeing that the mute box is unchecked. Otherwise, you can make sure your sound card is recognized under the system profile, and if it is perhaps go into Synaptics and do a search for any realtek drivers that might work once installed.

---

### Post by Reina on 2013-03-29
Hm... when I open up my system profile I get a blank message:

[http://i.imgur.com/BmKAZFy.png](http://i.imgur.com/BmKAZFy.png)

When I hit x, a another blank box pops up, and when I hit it another one pops up, and after about 3 times the system profile shows up, and when I click on certain parts I get more blank messages. But all in all it looks like it didn't recognize my soundcard:

[http://i.imgur.com/jfFIjmz.png](http://i.imgur.com/jfFIjmz.png)

Or... maybe it did?

[http://i.imgur.com/1li1upK.png](http://i.imgur.com/1li1upK.png)

If that's the case, what is this realtek thing GNOME ALSA mixer finds (Lubuntu doesn't show any volume controls on the side and I couldn't remember the program name)

[http://i.imgur.com/G4SggjN.png](http://i.imgur.com/G4SggjN.png)

The ati thing is blank when I click it also. If that's the case, where is that other audio driver my system recognized?

---

### Post by JLeon85 on 2013-03-29
What does it show in "additional drivers" in the "software & updates" settings? It may list a bunch of alternate drivers that you can try. Also, I noticed you have no volume control on the taskbar. Is that something you deleted, or did it never show up there? I don't know how you ended up with the Gnome Alsa Mixer because that is not part of the default software, and I would probably remove it. The default Lubuntu volume software is called "PulseAudio Volume Control" so I would make sure that's installed in the software center.

---

### Post by amjjawad on 2013-03-29
> **Reina said:**
> Hm... when I open up my system profile I get a blank message:

[http://i.imgur.com/BmKAZFy.png](http://i.imgur.com/BmKAZFy.png)



Hi,

This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/hardinfo/+bug/1029212](https://bugs.launchpad.net/ubuntu/+source/hardinfo/+bug/1029212)

---

### Post by amjjawad on 2013-03-29
It looks to me you do have the driver for your Audio Card.

From LXTerminal:

```
sudo lshw -C multimedia 

```

Post the result please to double check your driver. Please, wrap up the result with CODE Tags.

---

### Post by Reina on 2013-03-30
> **JLeon85 said:**
> What does it show in "additional drivers" in the "software & updates" settings? It may list a bunch of alternate drivers that you can try. Also, I noticed you have no volume control on the taskbar. Is that something you deleted, or did it never show up there? I don't know how you ended up with the Gnome Alsa Mixer because that is not part of the default software, and I would probably remove it. The default Lubuntu volume software is called "PulseAudio Volume Control" so I would make sure that's installed in the software center.

Oddly enough installing Pulse has fixed my problem. I say this because on my other Lubuntu setup, there is no pulseaudio either and it used something called alsa-mixer to control the volume. Now that I got a closer look at my soundcard info (which are both AMD things), the first time I booted up Lubuntu on this machine, it gave me an AMD error which I thought might be related to the processor, and ever since I've never seen the error when I boot up my computer. Perhaps that had something to do with my problem, as the volume control was missing from the very start. I couldn't run alsa-mixer from terminal (wrong command maybe?) so I installed GNOME Alsa Mixer to see if I couldn't control the volume from there.


> **amjjawad said:**
> It looks to me you do have the driver for your Audio Card.

From LXTerminal:

```
sudo lshw -C multimedia 

```

Post the result please to double check your driver. Please, wrap up the result with CODE Tags.

Alright for future reference in case anyone else has this problem (If this even helps at all):
```

  *-multimedia:0          
       description: Audio device
       product: Wrestler HDMI Audio [Radeon HD 6250/6310]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:42 memory:f0344000-f0347fff
  *-multimedia:1
       description: Audio device
       product: Hudson Azalia Controller
       vendor: Advanced Micro Devices [AMD]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:43 memory:f0340000-f0343fff

```

---

