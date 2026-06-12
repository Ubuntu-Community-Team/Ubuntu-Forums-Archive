---
title: "HOWTO: CMI8378, Alsa, software mixing and 5.1 sound in xmms"
date: 2005-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by BeeRockxs on 2005-05-04
This will get you software mixing (multiple sounds at the same time), and lets you play MP3s in xmms on your surround boxes, not just on your front left and right boxes.

First, create a .asoundrc file in your home directory, and put this into it:

```
pcm.dmix51 {
  type dmix
  ipc_key 1024
  slave {
    pcm "hw:0,1"
    rate 48000
    channels 6
    period_time 0
    period_size 1024
    buffer_time 0
    buffer_size 4096
  }
}
pcm.stereo {
  type plug
  slave.pcm "dmix51"
  ttable.0.0 1
  ttable.1.1 1
}
pcm.!default {
  type plug
  slave.pcm "stereo"
}
pcm.duplicate {
  type plug
  slave.pcm "dmix51"
  slave.channels 6
  route_policy duplicate
}
```

Then, change the output plugin in xmms to the alsa plugin (press CTRL-P), and then click configure. Set the output device to "duplicate".
If you also want software mixing in xine, set the alsa_surround51_device in the xine configuration to "dmix51".
With this setting, for all applications that use the default output get outpont on front left and front right speakers. All that have 5.1 sound should use the dmix51 device.

---

### Post by jazzorist on 2005-05-05
Thank you! :)

---

### Post by BeeRockxs on 2005-05-05
I'm glad I could help, I've been fighting ALSA quite some time to get this working :-)

---

### Post by freelovemat on 2005-05-08
Finally the centerbox works. Thanks a lot...  \\:D/

---

### Post by sukker on 2005-05-23
Have some problems with getting 5.1 too. Is there any kind of script that would fix this while I'm using an usb-audio-device (Terratec Aureon 5.1 USB MKII)?
I only get sound on the right and left front box, neither on subwoofer, center or rear and all those tips posted in several forums didn't work for me.
So I hope there is another useful script ;) THX

---

### Post by Mataanin on 2005-08-15
Hello, 

I have some problem with the script
I have followed your instructions with few exceps: I didn't find 'Output device' (in the xmms, Ctrl+P, Alsa plugin, Configure). In the Audio device section I have 'default'.
Then I try to play smth. XMMS Says "Coundn't open audio" and outputs:

"ALSA lib pcm_dmix.c:868: (snd_pcm_dmix_open) unable to open slave"

Do you have any ideas? ](*,)

---

### Post by MrJack on 2005-09-03
How could you ? Why me ? 
I just paid 30 bucks for a sound blaster and now i got my old card to work full 5.1. Bastard!




kidding :D.(well i did buy a new card , but who cares :D)
Cheers man , i owe you a beer ! :smile:
(you can't eaven imagine how long i've tryed to make this work !You'r just pure genius :D)

...dose anyone know why xmms stops when i "pause" it ? (it's like i pressed stop , and resume dose not work)

---

### Post by Tschaeck on 2005-10-07
[QUOTE=sukker]Have some problems with getting 5.1 too. Is there any kind of script that would fix this while I'm using an usb-audio-device (Terratec Aureon 5.1 USB MKII)?
I only get sound on the right and left front box, neither on subwoofer, center or rear and all those tips posted in several forums didn't work for me.
So I hope there is another useful script ;) THX[/QUOTE]
using that asoundrc as it is doesn't work for my terratec aureon 5.1 usb mkII. i had to change hw:0,1 to hw:1,0. now i hear sound on all 6 channels, but it is distorted and always overlaid by a sharp buzzing.
any ideas on how to get this fixed?

---

### Post by Tschaeck on 2005-10-09
search arround in the www and finally put together this asoundrc file:

```
pcm.dmix51 {
	type dmix
	ipc_key 1024
	ipc_key_add_uid false
	ipc_perm 0666 
	slave {
		pcm "hw:1,0"
		channels 6
		period_time 0
		period_size 1024
		buffer_size 8192
		rate 44100
	}
}

ctl.dmix51 {
	type hw
	card 1
}

pcm.stereo {
	type plug
	slave.pcm "dmix51"
	ttable.0.0 1
	ttable.1.1 1
}

pcm.!default {
	type route
	slave.pcm "dmix51"
	slave.channels 6
	ttable.0.0 1
	ttable.1.1 1
	ttable.0.2 1
	ttable.1.3 1
	ttable.0.4 1
	ttable.1.4 1
	ttable.0.5 1
	ttable.1.5 1
}

pcm.duplicate {
	type plug
	slave.pcm "dmix51"
	slave.channels 6
	route_policy duplicate
}
```

it is working excellent with my terratec aureon 5.1 usb mkII.

---

### Post by Vlammetje on 2005-10-20
Well I do have 6 channels. but unfortunately it's added enormous static to my sound as well... to the point where all you hear is static. :(

Any suggestions?

---

### Post by george_apan on 2006-01-27
I just wanted to say thanks for this. I just bought a Terratec Aureon 5.1 USB MkII sound card and using the script provided by Tschaeck I get sound from all speakers in xmms. The only difference following BeeRockxs' instructions was that  I selected the "default" Audio Output in Alsa configuration in xmms, since there was no "duplicate" one. So thanks again everyone! :)

---

### Post by eug2k on 2006-02-22
This did not work at all for me. I have an sb live 24bit (no hardware mixing).  All this did was change my output from front to rear speakers and make it very choopy as well.  I think I will try arts.

---

### Post by hobs0n on 2007-06-17
It seems this work with my Terratec Aureon 5.1 USB MK.2, before I added the .asoundrc file it didnt play at all, now it plays but I dont get any sound, I am connecting it by a Optical to my stereo. Anyone got an idea?

---

### Post by bugg_tb on 2008-09-06
I realise this is an old thread, but I've tried about a million different configurations and I can't get more than front left and front right out of my speakers using the spdif output on my Terratec Aureon. Can anyone shed any light on this?

Cheers

Tom

---

### Post by Jo21 on 2008-11-21
i have the same problem

i get front right from left (green and blue ports)

but not rear right/rear left (pink)

on the test i do, but not on the media players.

---

