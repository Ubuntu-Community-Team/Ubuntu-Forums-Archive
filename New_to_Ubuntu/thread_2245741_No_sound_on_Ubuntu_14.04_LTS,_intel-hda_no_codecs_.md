---
title: "No sound on Ubuntu 14.04 LTS, intel-hda no codecs found"
date: 2014-09-25
forum: New to Ubuntu
---

### Post by SugoiDesu on 2014-09-25
Hi.
I've just installed a copy of Ubuntu 14.04 LTS, and there doesn't seem to be any sound.
I'm already absolutely hopeless :mad:
Weren't able to find any solutions online, not anything that could help me fix this problem, anyways.
Could really use your help. Please ><

Some information that might be useful:

sugoi@sugoidesu:~$ dmesg | egrep "hda|00:14.2"
[    6.279205] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    6.349681] hda-intel 0000:00:1b.0: no codecs found!
[    7.881784] hda_intel: Disabling MSI
[    7.881789] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    7.881829] hda-intel 0000:01:00.1: Disabling 64bit DMA
[    7.885668] hda-intel 0000:01:00.1: Enable delay in RIRB handling


sugoi@sugoidesu:~$ lsmod | grep snd
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_intel          52355  1 
snd_hda_codec         192906  1 snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  11 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd


sugoi@sugoidesu:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)


sugoi@sugoidesu:~$ grep -i codec /proc/asound/card*/codec*
Codec: Nvidia ID 42

---

### Post by dreamer2 on 2014-10-06
Ditto on 10.04.  What few hairs I had left are packing for the coast.
00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
It's dual boot w/ 8.1. Well, not really windows keeps "repairing" the MBR. So, booting to 10.04 from isolinux on disc.  Strange though, Knoppix on a stick has sound.  I don't know. I've got a new CAELinux 2013 coming w/ 12.04.  We're deep in the woods and pay through the nose for broadband, 10bucks/Gb. Hey it's fast though.  No sound hardware showing, unclaimed hardware, even when it looks like it might work, it don't.  Every thing else is working except the grub problem.

sudo lshw -C "sound"
  *-multimedia UNCLAIMED  
       description: Audio device
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d30000-f7d33fff

Will let you know if a solution is found.

gdp

---

### Post by mastablasta on 2014-10-07
there was a thread that talked about installing interl drivers manually for sound chip. I cant' find it and if someone has the time to do it I would also be glad. I just know I read it once but now...
I have a similar issue. only in my case sound is sometimes found and recognised other times it's acting like there is no sound card/chip installed.

---

### Post by _az_ on 2015-01-15
I had a freshly installed Ubuntu Studio 14.04 and after a couple of days i also had no sound with pulse, jack seemed to work though.

In my case vga switcheroo disabled the hda intel audio device, and searching for that, i stumbled upon this thread.

Maybe this will help:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1310260/comments/21](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1310260/comments/21)

If i understand this correctly, you first get a list of your available sound devices and then disable the one, which uses HDMI.

---

### Post by Sally_Joshua on 2015-01-15
i am new to linux, i wonder why they dont just package linux installed with all the necessary drivers from networking, sound e.t.c the creators of these OS can see that people are suffering from the lack of drivers, just install them for us or give us an easy way to install. seems the open source bandwagon has no customer service, oh wait its because its free.

---

### Post by JeQhdMD on 2015-01-15
Sally, . . . for better than 95% of linux installs (40 million and counting) . . . . . there are no sound issues.   Lenovo, Dell and HP _**standard sound hardware chip-sets** are_ _well supported_ (and they constitute the vast majority of PC sales).   I've installed linux at least 60-70 times over 12 years.   Had 2 sound configuration issues back around 2004/2006 and none since.  Plus the two issues were fixed by doing some googling (with solutions saved if needed for future reference).

Re customer service, where else can you find hundreds of volunteers that devote _many hours 24/7 to help new users_ . . . (in spite of many user "caused" issues . . . e.g., not willing to read, learn, put forth the effort etc. etc.).   And further, being an IT Consultant at a company with over 50,000 pc users, I can relate a thing or two about the quality of "paid" help.

---

### Post by mastablasta on 2015-01-16
> **Sally_Joshua said:**
> i am new to linux, i wonder why they dont just package linux installed with all the necessary drivers from networking, sound e.t.c the creators of these OS can see that people are suffering from the lack of drivers, just install them for us or give us an easy way to install. 

They are installed. they are integrated with the so so much that they are part of the core (kernel) of the OS. however the issue is sometimes they don't do so well when they are recognising the chip.
> 
seems the open source bandwagon has no customer service, oh wait its because its free.
feel free to purchase professional support from Cannonical. more here: [http://www.ubuntu.com/management](http://www.ubuntu.com/management)

> **JeQhdMD said:**
> Sally, . . . for better than 95% of linux installs (40 million and counting) . . . . . there are no sound issues.   Lenovo, Dell and HP _**standard sound hardware chip-sets** are_ _well supported_ (and they constitute the vast majority of PC sales).   I've installed linux at least 60-70 times over 12 years.   Had 2 sound configuration issues back around 2004/2006 and none since.  Plus the two issues were fixed by doing some googling (with solutions saved if needed for future reference).
.
I have intel sound chip. something you might call "standard". yet it keeps getting recognised differently on different boots. the chip is supposed to have digital surround sound and all. I only need stereo. and sometimes it is recoginsed as digital output, analog input, sometimes ad digital output /digital input (this produces no sound) sometime it is called dummy, sometimes it is analog stereo with analog input. all these sometimes produce sound form speakers, other times everything is quiet. sometimes I can solve it by reloading Alsa modules, other times I need to turn off PC completely take out the power cable and then boot again for the chip to get recognised.

I was already thinking about getting a cheap "sound blaster card" that is Linux compatible, but somehow I think it would still recognise the on board chip and make it primary and stuff like that. I tried saving the session, saving the sound config, yet it keeps trying and sometimes failing to find the correct sound chip. funny though it worked perfectly for about 2 months when I installed 14.04. one of the updates made it go crazy again.

---

