---
title: "[SOLVED] no audio in hardy heron"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by ma3zooz on 2008-09-13
hi im running a dual OS of windows XP and ubuntu hardy heron (8.04). just got it started the other day and im completely clueless. already finished installing the 236 updates..
the problem is ive got no audio. nothin at all. not even from the sound tests.. ive tried changing the devices and ive got alsa but nothing works.
anyones help would be greatly appreciated.
ive read some and i think ull be needing this result from lspci | grep -i audio:

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

---

### Post by Crafty Kisses on 2008-09-13
Well since it recognizes the sound card, I don't think it is a kernel issue, but it possibly could be.

Try the following in the Terminal:
```
find /lib/modules/`uname -r` | grep snd
```
If it does not return any results, then your upgrade/dist-upgrade missed the** linux-ubuntu-modules package**, you need to install it and reboot: 
```
sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
```
After that, you may want to remove this package:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```
Then try reinstalling them:
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```
See if that springs your sound card to life. :)

---

### Post by ma3zooz on 2008-09-13
wow that was quick...
ok tried the first command.. but i got that /lib/modules/uname -r : no such file or directory
so i tried the aptitude thing.. and i got 
Couldn't find any package whose name or description matched "linux-ubuntu-modules-uname -r"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-uname -r"
so i tried the same thing with a space after modules-(space)'uname -r'
but it couldnt find that either.. it gave me a list of packages with ubuntu modules in their name
any ideas?

---

### Post by Crafty Kisses on 2008-09-13
For the first command, did you put **"find"** in the beginning.

So it should be like this:
```
find /lib/modules/`uname -r` | grep snd
```

---

### Post by ma3zooz on 2008-09-13
yes yes.. im not that new to ubuntu.. but i am new enough to try it with and without spaces.. both gave unfavorable answers.. :)

---

### Post by ma3zooz on 2008-09-13
ok ok.. im on to something.. i used quotation marks earlier.. but just figured out it must be ` not '..
so i tried it again.. and i got some long output.. do you want me to post it?

---

### Post by Crafty Kisses on 2008-09-13
Yes please post the results, and usually when someone gives you a command to try, just copy and paste, it's a lot more accurate.

---

### Post by ma3zooz on 2008-09-13
alright sorry for that...
heres the result
ma3zooz@ma3zooz-laptop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.24-19-generic/ubuntu/snd-bt-sco.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-virmidi.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-device.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-dummy.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-page-alloc.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-rtctimer.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-rawmidi.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/usb/snd-usb-audio.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/usb/snd-usb-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/soc/snd-soc-core.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-atiixp-modem.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-bt87x.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-intel8x0.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-via82xx.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-ens1371.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-sonicvibes.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-ad1889.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-als300.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-intel8x0m.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/nm256/snd-nm256.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-es1968.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-via82xx-modem.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-cs5530.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/trident/snd-trident.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-sis7019.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-azt3328.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/pdplus/snd-pdplus.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-rme96.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-als4000.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-fm801.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-atiixp.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-cs4281.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-ens1370.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-rme32.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/mixart/snd-mixart.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-es1938.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/riptide/snd-riptide.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-cmipci.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-maestro3.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/vx222/snd-vx222.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sbawe.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-es968.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb8.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb16.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb-common.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-opl3sa2.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-als100.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4231-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-sscape.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/es1688/snd-es1688.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-sc6000.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-cmi8330.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-es18xx.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-azt2320.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-sgalaxy.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-dt019x.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/msnd
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/gus/snd-interwave.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/gus/snd-gusmax.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/snd-adlib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/i2c/snd-cs8427.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/i2c/snd-i2c.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4114.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/i2c/other/snd-pt2258.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4117.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/i2c/snd-tea6330t.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/snd-portman2x4.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/snd-mtpav.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/snd-mts64.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/snd-serial-u16550.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/snd-dummy.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/snd-aloop.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/snd-virmidi.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/synth/snd-util-mem.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pcmcia/pdaudiocf/snd-pdaudiocf.ko

---

### Post by Crafty Kisses on 2008-09-13
Don't be sorry, just trying to help you out. :) Since it gave you an ouput, that's good.

Try installing this package:
```
sudo apt-get install alsa-oss
```

Then open it through the Terminal, and check your volumes.

---

### Post by ma3zooz on 2008-09-13
got:
alsa-oss is already the newest version
how do i open it from the terminal?

---

### Post by Crafty Kisses on 2008-09-13
Try running this in Terminal:
```
alsa-oss
```

---

### Post by ma3zooz on 2008-09-13
bash: alsa-oss: command not found

---

### Post by ma3zooz on 2008-09-13
may i ask you an unrelated question...
how did you learn linux/ubuntu
books or just by using it a lot?
i'm wondering if i'll be able to understand it fully one day just by using it..

---

### Post by ma3zooz on 2008-09-13
tried and got the following.. might help:
ma3zooz@ma3zooz-laptop:~$ /sbin/alsa reload
/sbin/alsa: Warning: Processes using sound devices: 5838(mixer_applet2). 
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).

---

### Post by Crafty Kisses on 2008-09-13
Sorry about the last command, I'm a little tired, but the way you can learn Linux is doing some research and using it for a bit yourself. The way I learned it is using it myself and doing some reading, and you'll learn yourself along the way.

Try this command to change your volumes:
```
alsamixer
```
You should get something like this:
```
 Card: ***                                                            &#9474;
&#9474; Chip: ***                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00]                                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;MM&#9474;               &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     100             100<>100 100<>100   0<>0      0<>0     0<>0       0      &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Front Mi Surround  Center    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

---

### Post by ma3zooz on 2008-09-13
something similar
```
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: C-Media CMI9880                                                        &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: PCM [dB gain=0.00, 0.00]                                               &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;                                                    &#9484;&#9472;&#9472;&#9488;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;                                                    &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;MM&#9474;      &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;      &#9474;MM&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;  100<>100                                                100<>100            &#9474;
&#9474; <  PCM   >Surround   Center    LFE      Side     IEC958  PC Speak Caller I  
```

---

### Post by Crafty Kisses on 2008-09-13
Try changing some of the volumes, and get back to me.

---

### Post by ma3zooz on 2008-09-13
ok tried playing with the volumes a little bit.. increased some.. then decreased others.. the ones with MM under them i cant change at all..
and i tried testing the sound.. still nothing..

---

### Post by Crafty Kisses on 2008-09-13
Post the results of this command, sorry for all the commands:
```
lspci | grep Audio
```

---

### Post by nightmarestreet on 2008-09-14
He already did, his is: 00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

I'm closely following this thread because I believe I have the same problem. My output is very similar: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by ma3zooz on 2008-09-14
yup already did that..
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

i dont mind the commands.. im learning i guess...

---

### Post by ma3zooz on 2008-09-14
ok so issue has been solved..
i went back to alsamixer.. tried to unmute the things that were muted.. and tried to change the volume (i couldnt by the way)... so i remuted them..
then i tried
sudo apt-get install gnome-alsamixer
played around with the volumes there.. opened system>preferences>sound
and guess what!! the tests worked.. and i heard SOMETHING!!
i can finally watch bleach :D
thank you ubuntu community..

---

### Post by anemptygun on 2008-11-11
I was having similar issues and when I installed the gnome-alsamixer package and messed with the settings it work! awesome!

---

