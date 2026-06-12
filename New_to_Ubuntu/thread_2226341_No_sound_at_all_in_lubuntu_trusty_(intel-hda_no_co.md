---
title: "No sound at all in lubuntu trusty (intel-hda no codecs found)"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by justin111 on 2014-05-26
So after installing Lubuntu trusty on my laptop with no issues I decided to recomission a friends old toshiba satellite for them. Its an older turion dual core with integrated radeon hd 4200 and 4gbs of ram. the problem is when i boot up the first text i see is "intel-hda no codecs found" I get no volume slider on startup. When i run alsamixer the only device that shows up is card: HDA ATI HDMI Chip: ATI RS690/780 HDMI. using a graphical mixer program yeilds no devices and no volume sliders. It would be awesome to get sound on this laptop it runs great and is pretty snappy with lubuntu installed. another clue might be that youtube video plays really fast and in alsamixer the only thing that shows up on the bottom is S/PDIF

---

### Post by matt_symes on 2014-05-26
Hi

To get the ball rolling, post the output of thse commands from the termimal

lsmod | grep snd
lspci | grep -i audio
grep -i codec /proc/asound/card*/codec*

Kind regards

---

### Post by justin111 on 2014-05-26
here you go!

snd_hda_codec_hdmi     46207  1 
snd_hda_intel          52355  1 
snd_hda_codec         192906  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  12 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
deanna@deannatoshiba:~$ lspci | grep -i audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]

---

### Post by matt_symes on 2014-05-27
Hi

Still looking at this. Can you post the exact make and model of the laptop.

Can you also post

```
lspci -nnk | grep -iA2 azalia
```

That's a capital A above.

For another piece of the jigsaw please post the output of

```
dmesg | grep hda
```

Run that last command after a reboot.

That may give more info as to why it`s not finding the codec

And one final question: is the laptop a toshiba satellite M300 ?

Kind regards

---

### Post by justin111 on 2014-05-28
sure!
its a Toshiba satellite L505D-LS5025

 lspci -nnk | grep -iA2 azalia
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]

im going to reboot and run the final command

---

### Post by justin111 on 2014-05-28
dmesg | grep hda
[   12.052929] hda-intel 0000:00:14.2: Using LPIB position fix
[   12.163711] hda-intel 0000:00:14.2: azx_reset: controller not ready!
[   12.163720] hda-intel 0000:00:14.2: no codecs found!
[   13.218336] hda-intel 0000:01:05.1: Using LPIB position fix
[   13.241022] hda-intel 0000:01:05.1: Enable sync_write for stable communication

---

### Post by monkeybrain20122 on 2014-05-28
Check the volume button on the lower right corner of the panel. Lubuntu sometimes (often?) mutes sound on reboot, no idea why.

---

### Post by Charlotte18 on 2014-05-28
If you have no luck with alsa, maybe installing pulseaudio instead will get you sound.

---

### Post by justin111 on 2014-05-28
> **monkeybrain20122 said:**
> Check the volume button on the lower right corner of the panel. Lubuntu sometimes (often?) mutes sound on reboot, no idea why.

Unfortunately there is no volume slider at all for me to manipulate/unmute

---

### Post by monkeybrain20122 on 2014-05-28
> **justin111 said:**
> Unfortunately there is no volume slider at all for me to manipulate/unmute


It is odd.There has to be a sound setting somewhere. Having installed Lubuntu on a few old machines I am fairly sure that your problem is caused by sound being muted. Unfortunately I don't have any lubuntu, so can't show you a screenshot or test other stuffs.

---

### Post by justin111 on 2014-05-28
> **Charlotte18 said:**
> If you have no luck with alsa, maybe installing pulseaudio instead will get you sound.

Just tried this. installed pulseaudio and removed alsa-base. this gave me a volume slider but still nothing.

---

### Post by monkeybrain20122 on 2014-05-28
BTW, does sound work if you boot from a live usb or CD? If yes then it is your settings. If no then maybe hardware or lubuntu.

---

### Post by justin111 on 2014-05-28
no it doesn't.
the first message i get when i boot relates to the sound codec not being found so the device isn't being initialized.

---

### Post by matt_symes on 2014-05-29
Hi

```
**snd_hda_codec_hdmi** 46207 1
snd_hda_intel 52355 1
snd_hda_codec 192906 2 **snd_hda_codec_hdmi**,snd_hda_intel
snd_hwdep 13602 1 snd_hda_codec
snd_pcm 102099 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
```

```
[ 12.052929] hda-intel 0000:00:14.2: Using LPIB position fix
[ 12.163711] hda-intel 0000:00:14.2: [B]azx_reset: controller not ready!
[ 12.163720] hda-intel [COLOR=#ff0000]0000:00:14.2[/COLOR]: no codecs found![/B]
[ 13.218336] hda-intel 0000:01:05.1: Using LPIB position fix
[ 13.241022] hda-intel 0000:01:05.1: Enable sync_write for stable communication
```

```
**[COLOR=#ff0000]0000:00:14.2[/COLOR] **00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
```

> **justin111 said:**
> no it doesn't.
the first message i get when i boot relates to the sound codec not being found so the device isn't being initialized.

Exactly what i think is happening. It's finding the hda controller but only finding the HDMI codec from the controller.

I suspect you may have sound if you plug it into a TV using and HDMI connection as, when it discovers the hardware codec, it's able to load the driver (snd_intel_codec_hdmi). Can you try this just as a test and report back ?

Anyway, I suspect this may be due to a buggy BIOS not reporting the correct location of the codec in the PCI space to the snd_hda_intel driver. That may or may not be the issue.

Could you post the output of

 ```
dmesg | egrep  "hda|00:014.2"
```

First thing i would do is raise a bug report.

```
ubuntu-bug audio
```

Second: have you checked for a BIOS update ?

Third:  I think the kernel documentation may be a little out of date, but it does seem to suggest you can probe all the codec slots avaliable. I assume you can still do this and i'm trying to find more up-to-date information on that.

Have a crack at the first two and then we can play with the third later.

Please post the link to the bug report in this thread. I want to subscribe to it as well.

EDIT: I've just noticed the model number as well so i'll take a look and see of that throws up any useful information.

Try reloading snd_hda_intel using

```
model=auto
```

Kind regards

---

### Post by Charlotte18 on 2014-06-03
Also, besides running a Bios update, you might try entering the Bios and disabling the HDMI output if possible. Then boot into Lubuntu and see if the sound is working after you take HDMI out of the equation. This might let you know whether matt_symes's hunch about the HDMI output is right.

---

