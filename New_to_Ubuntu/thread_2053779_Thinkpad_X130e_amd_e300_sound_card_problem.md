---
title: "Thinkpad X130e amd e300 sound card problem"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by zerobinary on 2012-09-06
```
[sudo] password for mr-fool: 
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
```
1 sink(s) available.
  * index: 1
	name: <alsa_output.pci-0000_00_01.1.hdmi-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: RUNNING
	suspend cause: 
	priority: 9950
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 89.78 ms
	max request: 15 KiB
	max rewind: 64 KiB
	monitor source: 1
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 1
	linked by: 1
	configured latency: 90.00 ms; range is 0.50 .. 371.52 ms
	card: 0 <alsa_card.pci-0000_00_01.1>
	module: 21
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "HDMI 0"
		alsa.id = "HDMI 0"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "3"
		alsa.card = "0"
		alsa.card_name = "HD-Audio Generic"
		alsa.long_card_name = "HD-Audio Generic at 0xf0344000 irq 43"
		device.bus_path = "pci-0000:00:01.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.1/sound/card0"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices [AMD] nee ATI"
		device.product.name = "Wrestler HDMI Audio [Radeon HD 6250/6310]"
		device.form_factor = "internal"
		device.string = "hdmi:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "hdmi-stereo"
		device.profile.description = "Digital Stereo (HDMI)"
		device.description = "Built-in Audio Digital Stereo (HDMI)"
		alsa.mixer_name = "ATI R6xx HDMI"
		alsa.components = "HDA:1002aa01,00aa0100,00100200"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900, available: no)
			properties:
				
	active port: <hdmi-output-0>
>>> 

```
```
mr-fool@mrfool-ThinkPad-X130e:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.2.0-30-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/snd.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/3.2.0-30-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.2.0-30-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.2.0-30-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.2.0-30-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.2.0-30-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/3.2.0-30-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.2.0-30-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.2.0-30-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.2.0-30-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-88pm860x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-max9850.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8995.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8782.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm5100.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8983.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wl1273.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-max98095.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8996.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8991.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ak4641.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-adau1373.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-jz4740-codec.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-adav80x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-dfbmcs320.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-lm4857.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-wm1250-ev1.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-cx20442.ko
/lib/modules/3.2.0-30-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/3.2.0-30-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.2.0-30-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.2.0-30-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.2.0-30-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.2.0-30-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.2.0-30-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.2.0-30-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.2.0-30-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.2.0-30-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.2.0-30-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.2.0-30-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.2.0-30-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.2.0-30-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.2.0-30-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.2.0-30-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.2.0-30-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-analog.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-ca0132.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-cmedia.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-hdmi.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-idt.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-realtek.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-si3054.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-ca0110.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-via.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-conexant.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-codec-cirrus.ko
/lib/modules/3.2.0-30-generic/updates/dkms/snd-hda-intel.ko

```
```
mr-fool@mrfool-ThinkPad-X130e:~$ sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
[sudo] password for mr-fool: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-3.2.0-30-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.2.0-30-generic'
mr-fool@mrfool-ThinkPad-X130e:~$ uname -v
#48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012
mr-fool@mrfool-ThinkPad-X130e:~$ uname -r
3.2.0-30-generic

```
```
mr-fool@mrfool-ThinkPad-X130e:~$ lspci -v | grep -A7 -i "audio"
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
	Subsystem: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0344000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port (prog-if 00 [Normal decode])
--
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Lenovo Device 21ec
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

mr-fool@mrfool-ThinkPad-X130e:~$ 

```

---

### Post by zerobinary on 2012-09-06
Shameless bump

---

### Post by zerobinary on 2012-09-06
help please

---

### Post by zerobinary on 2012-09-06
shameless bump

---

### Post by zerobinary on 2012-09-06
shameless bump

---

### Post by zerobinary on 2012-09-08
shameless bump

---

### Post by mips on 2012-09-09
lspci -v ?

Also run alsamixer in a terminal and post a screenshot here (stretch the window to fit the content)

---

