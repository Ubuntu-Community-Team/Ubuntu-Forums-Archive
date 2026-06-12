---
title: "No Sound, OSS installed but not loading"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by buttonpusher7 on 2008-05-03
Hi all,

I am using a Razer sound card that uses a CMedia 8788 chip. Ihave installed the oss driver for the card.When I do a osstest, I can hear the test sounds play, but the sound control is crossed out.This is on gutsy 7.10..

Here is the result of osstest,
 
*** Scanning sound adapter #-1 ***
/dev/oss/cmi87880/pcm0 (audio engine 0): CMedia CMI8788 (MultiChannel)
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 48009.00 Hz (0.02%)> 
/dev/oss/cmi87880/pcm1 (audio engine 2): CMedia CMI8788 (SPDIF)
- Performing audio playback test... 
  <left> OK <right> OK <stereo> 

Here is the ossmix:

Selected mixer 0/CMedia CMI8788
Known controls are:
pcm <both/leftvol>[:<rightvol>] (currently 75:75)
rear <both/leftvol>[:<rightvol>] (currently 94:94)
center <both/leftvol>[:<rightvol>] (currently 75:75)
side <both/leftvol>[:<rightvol>] (currently 75:75)
ext.monitor.multichannel ON|OFF (currently ON)
ext.monitor.frontpanel ON|OFF (currently OFF)
ext.monitor.spdif ON|OFF (currently OFF)
ext.routing.speaker-spread ON|OFF (currently ON)
ext.routing.spdif-loopback ON|OFF (currently OFF)
spdif-out.enable ON|OFF (currently OFF)
spdif-out.adc/dac ON|OFF (currently OFF)
spdif-out.pro <Consumer|Professional> (currently Consumer)
spdif-out.audio <Audio|Data> (currently Audio)
spdif-out.copy ON|OFF (currently OFF)
spdif-out.pre-emph ON|OFF (currently OFF)
spdif-out.rate <44.1KHz|48KHz|32KHz|88.2KHz|96KHz|64KHz|176.4KHz|192KHz> (currently 48KHz)
spdif-out.vbit ON|OFF (currently OFF)

Thanks,BP

---

