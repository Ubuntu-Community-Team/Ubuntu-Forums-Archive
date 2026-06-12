---
title: "have no sound with any application"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Norman Thom on 2008-12-02
I just installed Ubuntu 8.10 in a dual boot situation with my MS XP SP3
I seem to be getting no sound via my applications. sp VLC, audacious, Tuna pie, Rhythmbox etc.  When I tried to reconfigure ALSA I was told that ALSA was not installed, even though ALSA has been selected in my synaptic package manager.  When I access System > Preferences > Sounds I can get a test sound result if I select certqain SB Live Values.  I don't know off hand what my sound card is ( though I would like to find out, does Linus have the equivilant of a device manager?).  

Can anybody help me regain my sound

Ellysium

---

### Post by Michael.Godawski on 2008-12-02
To check if Ubuntu recognizes your sound card type into the terminal:
```
aplay -l
```
and post the result here.

To check if the sound modules are installed:
```
find /lib/modules/`uname -r` | grep snd
```
You should see a bunch of files...

Also post the result of 
```
lspci 
```
here please.

---

### Post by markbuntu on 2008-12-02
Here is a little quick start guide for getting Intrepid sound working properly:


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by Norman Thom on 2008-12-02
Thank you very much Michael:

Te responses I got were as follows:

for aplay l:
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Live [SBLive! Value [CT4830]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 3: Live [SBLive! Value [CT4830]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 3: Live [SBLive! Value [CT4830]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

for grep snd:

/lib/modules/2.6.27-10-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-10-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-10-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.27-10-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.27-10-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.27-10-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-10-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-10-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-10-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-10-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-10-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-10-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-10-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.27-10-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-10-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-10-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.27-10-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-10-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/cs423x/snd-cs4231-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.27-10-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-10-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.27-10-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
/lib/udev/devices/sndstat
find: `modules/ellysium': No such file or directory
find: `-': No such file or directory
find: `r': No such file or directory


for command lspci:

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
00:0b.0 Communication controller: Conexant Systems, Inc. Device 2f01 (rev 01)
00:0c.0 Ethernet controller: Belkin Device 700f (rev 20)
00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)


Hope this is helpful

---

