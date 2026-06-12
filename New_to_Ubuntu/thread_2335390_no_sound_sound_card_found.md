---
title: "no sound sound card found"
date: 2016-08-28
forum: New to Ubuntu
---

### Post by adamdarbyshire on 2016-08-28
**Product name** 

 [TABLE="class: table table-bordered table-steps"]
[TR]
[TD="align: left"][/TD]
[TD="align: left"] HP Pavilion x2 - 10-n156na (ENERGY STAR)

 [/TD]
 [/TR]
 [TR]
 [TD="align: left"]  **Microprocessor** 
 [/TD]
[TD="align: left"] Intel® Atom™ Z8300 with Intel® HD Graphics (1.44 GHz, 2 MB cache, 4 cores)
 [/TD]
 [/TR]
 [TR]
 [TD="align: left"]  **Memory, standard** 
 [/TD]
[TD="align: left"] 2 GB DDR3L SDRAM (onboard)
 [/TD]
 [/TR]
 [TR]
 [TD="align: left"]  **Video Graphics** 
 [/TD]
[TD="align: left"] Intel HD Graphics
 [/TD]
 [/TR]
 [TR]
 [TD="align: left"]  **Hard Drive** 
 [/TD]
[TD="align: left"] 32 GB eMMC
[/TD]
[/TR]
[/TABLE]

 **Audio features       **B&O PLAY with 2 speakers

Audio Driver:               TITLE:  Conexant Audio Driver

VERSION:  1.58.0.50 REV:  A PASS:  11

alsamixergui : alsamixer function snd_ctl_open failed for default: No such file or directory

i have followed this: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

step 4 readout: 
bunnahabhaind@bunnahabhaind-HP-Pavilion-x2-Detachable:~$ sudo aplay -l
[sudo] password for bunnahabhaind: 
aplay: device_list:268: no soundcards found...

step 5 readout:
bunnahabhaind@bunnahabhaind-HP-Pavilion-x2-Detachable:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/4.4.0-34-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-generic.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/4.4.0-34-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/dice/snd-dice.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/fireworks/snd-fireworks.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/oxfw/snd-oxfw.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/bebob/snd-bebob.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/digi00x/snd-firewire-digi00x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/tascam/snd-firewire-tascam.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/snd-compress.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/snd.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/snd-pcm-dmaengine.ko
/lib/modules/4.4.0-34-generic/kernel/sound/core/snd-timer.ko
/lib/modules/4.4.0-34-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tfa9879.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42xx8.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-es8328.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8804-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-rt5645.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-dmic.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-sta350.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs4349.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tas5086.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tas2552.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8804-spi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic31xx.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4554.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-rl6231.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-pcm512x-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs35l32.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-rt286.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23-spi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-pcm512x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs4265.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-pcm1792a-codec.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ssm4567.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42l73.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-rt5670.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42xx8-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-pcm1681.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs4271-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ssm2602-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak5386.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42l56.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-adau1701.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-gtm601.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42l52.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs42l51-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-spdif-rx.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ac97.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ssm2602-spi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-max98090.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-sti-sas.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-spdif-tx.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ts3a227e.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-rt5640.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs4271-spi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-rl6347a.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-tas571x.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ak4613.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-pcm512x-spi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/xtensa/snd-soc-xtfpga-i2s.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/skylake/snd-soc-skl.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/skylake/snd-soc-skl-ipc.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-skl_rt286.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bytcr-rt5640.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-max98090_ti.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-sst-byt-rt5640-mach.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5645.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-sst-byt-max98090-mach.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5672.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-sst-haswell.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/boards/snd-soc-sst-broadwell.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/atom/sst/snd-intel-sst-core.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/atom/sst/snd-intel-sst-acpi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/atom/snd-soc-sst-mfld-platform.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/baytrail/snd-soc-sst-baytrail-pcm.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/common/snd-soc-sst-ipc.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/common/snd-soc-sst-acpi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/common/snd-soc-sst-dsp.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/intel/haswell/snd-soc-sst-haswell-pcm.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/fsl/snd-soc-fsl-sai.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/fsl/snd-soc-fsl-ssi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/fsl/snd-soc-fsl-asrc.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/fsl/snd-soc-imx-audmux.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/fsl/snd-soc-fsl-esai.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/fsl/snd-soc-fsl-spdif.ko
/lib/modules/4.4.0-34-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/line6/snd-usb-variax.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/line6/snd-usb-toneport.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/line6/snd-usb-line6.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/line6/snd-usb-pod.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/line6/snd-usb-podhd.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/bcd2000/snd-bcd2000.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/4.4.0-34-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/4.4.0-34-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/4.4.0-34-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/4.4.0-34-generic/kernel/sound/hda/ext/snd-hda-ext-core.ko
/lib/modules/4.4.0-34-generic/kernel/sound/hda/snd-hda-core.ko
/lib/modules/4.4.0-34-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/4.4.0-34-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/4.4.0-34-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/4.4.0-34-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/4.4.0-34-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/4.4.0-34-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/4.4.0-34-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/4.4.0-34-generic/kernel/sound/drivers/snd-aloop.ko

The snd is highlighted red.

then;

sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-4.4.0-34-generic
E: Couldn't find any package by glob 'linux-restricted-modules-4.4.0-34-generic'
E: Couldn't find any package by regex 'linux-restricted-modules-4.4.0-34-generic'

step 6 readout:
bunnahabhaind@bunnahabhaind-HP-Pavilion-x2-Detachable:~$ lspci -v | grep -A7 -i "audio"
bunnahabhaind@bunnahabhaind-HP-Pavilion-x2-Detachable:~$

I'm new to lubuntu and was wondering what I can do about this?

I've tried updating the BIOS, audio driver and chipset ([http://support.hp.com/us-en/drivers/selfservice/hp-pavilion-10-n100-x2-detachable-pc/8499312/model/9014689](http://support.hp.com/us-en/drivers/selfservice/hp-pavilion-10-n100-x2-detachable-pc/8499312/model/9014689)) but these are .exe files which i have tried to run with wine tool [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) but to no avail.

i had previously installed Ubuntu 16.04.1 LTS and had the same issue.

really would like to get this fixed and would appreciate any help offered!

thank you so much in advance!

---

