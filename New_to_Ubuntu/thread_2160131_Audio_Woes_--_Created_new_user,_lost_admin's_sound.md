---
title: "Audio Woes -- Created new user, lost admin's sound -- Ubuntu 13.04"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by Gnawnsense on 2013-07-05
Greetings everyone!

In an effort to shorten my usually TL;DR help requests, here's my "short" version: this is the second time I've had this happen on an Ubuntu 13.04 install. Oh, and let me preface with this I'm a terribly horrible Linux noob. The first time was an issue with settings being switched between HDMI and Audio for some reason. I initially checked that this time, but my previous solution did not work by just going into sound settings. Alright, now onto the actual issue itself this time around:

Everything on my Ubuntu 13.04 installation has been working wonderfully, even my AMD HD 6800. Needless to say, I've began getting a bit more comfortable with Ubuntu in general and I recently decided to set up a secondary user account on the computer, under standard access for my daughter. Everything went well, logged into the account and had a look around, then logged out immediately, changing no settings. 

I logged back in to my primary account on the computer to the surprise that I have no sound. Immediately, I thought I must of broke something, so I logged out of the account and was greeted with the Ubuntu drum-roll when I got to the login screen with the list of user accounts. Feeling a bit better because of the drum-roll, I logged into my newly created account for my daughter and voila, sound was working. 

Convinced the issue just required a log out and back in, I switched back over to my primary account only to find the sound isn't working on this account still. I'm completely lost, because audio and everything was working directly before creating the user account and it stopped directly after creating it, with no other settings being modified.

This is the second time this has happened. The first time, tho, I had been playing with display drivers, as well, so I chalked it up to me borking some important things along the way. This time, tho, was a bit more controlled in the environment and what was going on at the time the user account was created. 

I have searched through the forums and other issues, but haven't found someone experiencing my issue, and I also did review [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) thoroughly, unless I overlooked something.

Any assistance would be greatly appreciated!

---

### Post by Gnawnsense on 2013-07-05
Some additional information:

It does appear that my soundcard is being recognized by the system while on my primary account (the one lacking the sound) as can be seen here:

[IMG]http://screencloud.net//img/screenshots/965e276962b7167f6c31f92b076fda1a.png[/IMG]

When I check to see if sound modules are installed (which they should of been, obviously, as sound was working before) with the [COLOR=#800080]*find /lib/modules/`uname -r` | grep snd *[/COLOR]command, this is the list I get, which indicates they're installed, I believe:

```
/lib/modules/3.8.0-26-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko/lib/modules/3.8.0-26-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.8.0-26-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm0010.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-dfbmcs320.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8995.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-88pm860x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wl1273.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8782.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-sta529.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-jz4740-codec.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm5100.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-isabelle.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ak4641.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-da9055.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ml26124.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-cs42l73.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-spdif-tx.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-max98095.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-da732x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm5102.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-adav80x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8983.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-lm4857.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-cx20442.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ab8500-codec.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-arizona.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm5110.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-max9768.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-max98090.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-cs42l52.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-spdif-rx.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm-adsp.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-twl4030.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8991.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm1250-ev1.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm2200.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-mc13783.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-alc5632.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8996.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-twl6040.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-lm49453.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-adau1373.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-max9850.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/3.8.0-26-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.8.0-26-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.8.0-26-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.8.0-26-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.8.0-26-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.8.0-26-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.8.0-26-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.8.0-26-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.8.0-26-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.8.0-26-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.8.0-26-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.8.0-26-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.8.0-26-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/snd-compress.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.8.0-26-generic/kernel/sound/core/snd.ko
/lib/modules/3.8.0-26-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.8.0-26-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.8.0-26-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.8.0-26-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.8.0-26-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.8.0-26-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.8.0-26-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/3.8.0-26-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.8.0-26-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.8.0-26-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.8.0-26-generic/kernel/sound/pci/riptide/snd-riptide.ko
```

And, just to make sure no funny business could be happening, I checked if the card was installed properly and being recognized by my hardware properly with the [COLOR=#800080]*lspci -v | grep -A7 -i "audio"*[/COLOR] command, just because I found a Wiki page suggesting it during troubleshooting. This is what I got:

[IMG]http://screencloud.net//img/screenshots/bd6ebb0e5ecc620fb9df81a8d4927884.png[/IMG]

---

