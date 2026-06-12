---
title: "cannot get my xonar soundcard to work"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-11-15
I am trying to get my xonar dx sound card to work but I get no sound, I do see it in the mixer along with a few other things.
this is the output of this command cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf1000000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf0010000 irq 17
 2 [Webcam         ]: USB-Audio - Dynex 1.3MP Webcam
                      Dynex Dynex 1.3MP Webcam at usb-0000:00:1a.7-3, high speed
 3 [DX             ]: AV200 - Xonar DX
                      Asus Virtuoso 100 (rev 2) at 0xa000, irq 17
and the out put of this command modinfo soundcore
filename:       /lib/modules/2.6.27-7-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:
vermagic:       2.6.27-7-generic SMP mod_unload modversions

---

