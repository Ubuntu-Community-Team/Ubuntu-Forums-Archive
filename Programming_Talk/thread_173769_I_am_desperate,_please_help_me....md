---
title: "I am desperate, please help me..."
date: 2006-05-10
forum: Programming Talk
---

### Post by hotcha3 on 2006-05-10
Hi, it's the first time i post, im a linux newbie, i really need some help with an issue:

I bought an AvertTV dvb-t USB 2.0 and i've been trying to make system recognize it for like a week but i can't. I've found a nice guide here:  [http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto](http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto)

which has helped me alot, but i have a problem after the cvs checkout when i start to compile: when i press: :~/dvb-kernel/build-2.6$ make 
                 
                 i keep getting :  Makefile:13: /lib/modules/2.6.15-22-386/source/.config:     FIle or directory doesen't exist
make: *** there's no rule to build the objective `/lib/modules/2.6.15-22-386/source/.config'.  Alto.


I really don't know anything about compiling but it's the only way i've found to make my dapper (i tried unluckily with breezy)  recognize it. I would really appreciate if someone could help me. Thanx

---

### Post by Dr. Nick on 2006-05-11
Make sure you have kernel-tree and kernel-source packages installed for your kernel, aswell as build-essential package.

Also programming talk may not be the best forum for this, may miss alot of people who can help.

---

### Post by hotcha3 on 2006-05-11
Thanks for the answer, where should i post about it ? I tried on hardware talk but nobody answered...

Could you please tell me how do i install all these? The tree,source and essential packages? Im really sorry, but im a very newbie. 
My kernel is 2.6.15-22-386

Thanks in advance.

---

### Post by hotcha3 on 2006-05-11
I put : sudo apt-get install kernel-tree-2.6.15-22-386 or sudo apt-get install linux-tree-2.6.15-22-386  and it says it can't find this package. That's how i did to isntall the headers...waiting for ur help xD Thanks in advance

---

### Post by Dr. Nick on 2006-05-11
Oops, they switched naming schemes and I keep forgetting

Install linux-source using ```
sudo apt-get install linux-source
``` and you may also need ```
sudo apt-get install build-essential
``` 
If these dont help you may ask it to be moved to just desktop support

---

### Post by hotcha3 on 2006-05-11
Ok, i'll try it. Thnks for the help mate.

---

### Post by hotcha3 on 2006-05-11
Im sorry for bothering you again, but it still says the same: 

Makefile:13: /lib/modules/2.6.15-22-386/source/.config: No existe el fichero o el directorio
make: *** No hay ninguna regla para construir el objetivo `/lib/modules/2.6.15-22-386/source/.config'.  Alto.

Which means, the file or directory doesen't exist and there's no rule to build the objective...

I've installed everything u just said: headers,source and build essential. I'm really desperate...i don't know what to do.

---

### Post by Dr. Nick on 2006-05-11
This is just a guess but worth a shot
open a terminal and go ```
cd /usr/src/linux
``` then run 
```
make menuconfig
```then exit and save config.

That may generate the .config file its looking for, If that doesnt work the copy the file called /boot/config-2.6.15-22-386 to the directory its lookijng for .config in. After that use the rename command from the terminal from the directory to rename config-2.6.15-22-386 to .config should be something like 
rename config-2.6.15-22-386 .config

I am not sure what would cause this, I Havent had to build divers in a long time
Good Luck

---

### Post by hotcha3 on 2006-05-11
Well, the first steps didn't work, it gave me a wierd error. 
So then i tried to copy the config-2.6.15-22-386 to /lib/modules/2.6.15-22-386/source, but the problem is that "source" directory doesen't exist...should i copy it directly in /lib/modules/2.6.15-22-386 ??

---

### Post by Dr. Nick on 2006-05-11
You could try that but it may not work, what you might try is making a source direcotry under the modules/2.6/15-22-386 folder then copying it, It still may not compile but it may get you a bit further.

Would be something like
sudo mkdir /lib/modules/2.6.15-22-386/source

I am really not sure what would fix it exactly since Ive never done that particular driver  before

---

### Post by hotcha3 on 2006-05-11
Well someone told me another way and it worked, and i got the source directory with the makefile. then i started compiling, and everything went fine till the end when i got an error:

> [ -L saa7146_video.c ] || ./getlinks
getting links from kernel-cvs driver
make[1]: se ingresa al directorio `/home/sunil/dvb-kernel/build-2.6'
rm -f *.o *.ko .*.o.cmd .*.ko.cmd *.mod.c .*.o.d fdump av7110_firm.h video-buf.crm -rf .tmp_versions
find . -type l | xargs -r rm
make[1]: se sale del directorio `/home/sunil/dvb-kernel/build-2.6'
crea el enlace simbólico `av7110.c' a `../linux/drivers/media/dvb/ttpci/av7110.c'
crea el enlace simbólico `av7110.h' a `../linux/drivers/media/dvb/ttpci/av7110.h'
crea el enlace simbólico `av7110_av.c' a `../linux/drivers/media/dvb/ttpci/av7110_av.c'
crea el enlace simbólico `av7110_av.h' a `../linux/drivers/media/dvb/ttpci/av7110_av.h'
crea el enlace simbólico `av7110_ca.c' a `../linux/drivers/media/dvb/ttpci/av7110_ca.c'
crea el enlace simbólico `av7110_ca.h' a `../linux/drivers/media/dvb/ttpci/av7110_ca.h'
crea el enlace simbólico `av7110_hw.c' a `../linux/drivers/media/dvb/ttpci/av7110_hw.c'
crea el enlace simbólico `av7110_hw.h' a `../linux/drivers/media/dvb/ttpci/av7110_hw.h'
crea el enlace simbólico `av7110_ipack.c' a `../linux/drivers/media/dvb/ttpci/av7110_ipack.c'
crea el enlace simbólico `av7110_ipack.h' a `../linux/drivers/media/dvb/ttpci/av7110_ipack.h'
crea el enlace simbólico `av7110_ir.c' a `../linux/drivers/media/dvb/ttpci/av7110_ir.c'
crea el enlace simbólico `av7110_v4l.c' a `../linux/drivers/media/dvb/ttpci/av7110_v4l.c'
crea el enlace simbólico `budget-av.c' a `../linux/drivers/media/dvb/ttpci/budget-av.c'
crea el enlace simbólico `budget-ci.c' a `../linux/drivers/media/dvb/ttpci/budget-ci.c'
crea el enlace simbólico `budget-core.c' a `../linux/drivers/media/dvb/ttpci/budget-core.c'
crea el enlace simbólico `budget-patch.c' a `../linux/drivers/media/dvb/ttpci/budget-patch.c'
crea el enlace simbólico `budget.c' a `../linux/drivers/media/dvb/ttpci/budget.c'
crea el enlace simbólico `budget.h' a `../linux/drivers/media/dvb/ttpci/budget.h'
crea el enlace simbólico `fdump.c' a `../linux/drivers/media/dvb/ttpci/fdump.c'
crea el enlace simbólico `ttpci-eeprom.c' a `../linux/drivers/media/dvb/ttpci/ttpci-eeprom.c'
crea el enlace simbólico `ttpci-eeprom.h' a `../linux/drivers/media/dvb/ttpci/ttpci-eeprom.h'
crea el enlace simbólico `dvb-ttusb-budget.c' a `../linux/drivers/media/dvb/ttusb-budget/dvb-ttusb-budget.c'
crea el enlace simbólico `dvb-ttusb-dspbootcode.h' a `../linux/drivers/media/dvb/ttusb-budget/dvb-ttusb-dspbootcode.h'
crea el enlace simbólico `ttusb_dec.c' a `../linux/drivers/media/dvb/ttusb-dec/ttusb_dec.c'
crea el enlace simbólico `ttusbdecfe.c' a `../linux/drivers/media/dvb/ttusb-dec/ttusbdecfe.c'
crea el enlace simbólico `ttusbdecfe.h' a `../linux/drivers/media/dvb/ttusb-dec/ttusbdecfe.h'
crea el enlace simbólico `dibusb-mb.c' a `../linux/drivers/media/dvb/dvb-usb/dibusb-mb.c'
crea el enlace simbólico `a800.c' a `../linux/drivers/media/dvb/dvb-usb/a800.c'
crea el enlace simbólico `cxusb.c' a `../linux/drivers/media/dvb/dvb-usb/cxusb.c'
crea el enlace simbólico `cxusb.h' a `../linux/drivers/media/dvb/dvb-usb/cxusb.h'
crea el enlace simbólico `dibusb-common.c' a `../linux/drivers/media/dvb/dvb-usb/dibusb-common.c'
crea el enlace simbólico `dibusb-mc.c' a `../linux/drivers/media/dvb/dvb-usb/dibusb-mc.c'
crea el enlace simbólico `dibusb.h' a `../linux/drivers/media/dvb/dvb-usb/dibusb.h'
crea el enlace simbólico `digitv.c' a `../linux/drivers/media/dvb/dvb-usb/digitv.c'
crea el enlace simbólico `digitv.h' a `../linux/drivers/media/dvb/dvb-usb/digitv.h'
crea el enlace simbólico `dtt200u-fe.c' a `../linux/drivers/media/dvb/dvb-usb/dtt200u-fe.c'
crea el enlace simbólico `dtt200u.c' a `../linux/drivers/media/dvb/dvb-usb/dtt200u.c'
crea el enlace simbólico `dtt200u.h' a `../linux/drivers/media/dvb/dvb-usb/dtt200u.h'
crea el enlace simbólico `dvb-usb-common.h' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-common.h'
crea el enlace simbólico `dvb-usb-dvb.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-dvb.c'
crea el enlace simbólico `dvb-usb-firmware.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-firmware.c'
crea el enlace simbólico `dvb-usb-i2c.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-i2c.c'
crea el enlace simbólico `dvb-usb-ids.h' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h'
crea el enlace simbólico `dvb-usb-init.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-init.c'
crea el enlace simbólico `dvb-usb-remote.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-remote.c'
crea el enlace simbólico `dvb-usb-urb.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-urb.c'
crea el enlace simbólico `dvb-usb.h' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb.h'
crea el enlace simbólico `nova-t-usb2.c' a `../linux/drivers/media/dvb/dvb-usb/nova-t-usb2.c'
crea el enlace simbólico `umt-010.c' a `../linux/drivers/media/dvb/dvb-usb/umt-010.c'
crea el enlace simbólico `vp702x-fe.c' a `../linux/drivers/media/dvb/dvb-usb/vp702x-fe.c'
crea el enlace simbólico `vp702x.c' a `../linux/drivers/media/dvb/dvb-usb/vp702x.c'
crea el enlace simbólico `vp702x.h' a `../linux/drivers/media/dvb/dvb-usb/vp702x.h'
crea el enlace simbólico `vp7045-fe.c' a `../linux/drivers/media/dvb/dvb-usb/vp7045-fe.c'
crea el enlace simbólico `vp7045.c' a `../linux/drivers/media/dvb/dvb-usb/vp7045.c'
crea el enlace simbólico `vp7045.h' a `../linux/drivers/media/dvb/dvb-usb/vp7045.h'
crea el enlace simbólico `dst_ca.c' a `../linux/drivers/media/dvb/bt8xx/dst_ca.c'
crea el enlace simbólico `bt878.c' a `../linux/drivers/media/dvb/bt8xx/bt878.c'
crea el enlace simbólico `bt878.h' a `../linux/drivers/media/dvb/bt8xx/bt878.h'
crea el enlace simbólico `dst.c' a `../linux/drivers/media/dvb/bt8xx/dst.c'
crea el enlace simbólico `dst_ca.h' a `../linux/drivers/media/dvb/bt8xx/dst_ca.h'
crea el enlace simbólico `dst_common.h' a `../linux/drivers/media/dvb/bt8xx/dst_common.h'
crea el enlace simbólico `dst_priv.h' a `../linux/drivers/media/dvb/bt8xx/dst_priv.h'
crea el enlace simbólico `dvb-bt8xx.c' a `../linux/drivers/media/dvb/bt8xx/dvb-bt8xx.c'
crea el enlace simbólico `dvb-bt8xx.h' a `../linux/drivers/media/dvb/bt8xx/dvb-bt8xx.h'
crea el enlace simbólico `flexcop-common.h' a `../linux/drivers/media/dvb/b2c2/flexcop-common.h'
crea el enlace simbólico `flexcop-dma.c' a `../linux/drivers/media/dvb/b2c2/flexcop-dma.c'
crea el enlace simbólico `flexcop-eeprom.c' a `../linux/drivers/media/dvb/b2c2/flexcop-eeprom.c'
crea el enlace simbólico `flexcop-fe-tuner.c' a `../linux/drivers/media/dvb/b2c2/flexcop-fe-tuner.c'
crea el enlace simbólico `flexcop-hw-filter.c' a `../linux/drivers/media/dvb/b2c2/flexcop-hw-filter.c'
crea el enlace simbólico `flexcop-i2c.c' a `../linux/drivers/media/dvb/b2c2/flexcop-i2c.c'
crea el enlace simbólico `flexcop-misc.c' a `../linux/drivers/media/dvb/b2c2/flexcop-misc.c'
crea el enlace simbólico `flexcop-pci.c' a `../linux/drivers/media/dvb/b2c2/flexcop-pci.c'
crea el enlace simbólico `flexcop-reg.h' a `../linux/drivers/media/dvb/b2c2/flexcop-reg.h'
crea el enlace simbólico `flexcop-sram.c' a `../linux/drivers/media/dvb/b2c2/flexcop-sram.c'
crea el enlace simbólico `flexcop-usb.c' a `../linux/drivers/media/dvb/b2c2/flexcop-usb.c'
crea el enlace simbólico `flexcop-usb.h' a `../linux/drivers/media/dvb/b2c2/flexcop-usb.h'
crea el enlace simbólico `flexcop.c' a `../linux/drivers/media/dvb/b2c2/flexcop.c'
crea el enlace simbólico `flexcop.h' a `../linux/drivers/media/dvb/b2c2/flexcop.h'
crea el enlace simbólico `flexcop_ibi_value_be.h' a `../linux/drivers/media/dvb/b2c2/flexcop_ibi_value_be.h'
crea el enlace simbólico `flexcop_ibi_value_le.h' a `../linux/drivers/media/dvb/b2c2/flexcop_ibi_value_le.h'
crea el enlace simbólico `stv0297_cs2.c' a `../linux/drivers/media/dvb/b2c2/stv0297_cs2.c'
crea el enlace simbólico `stv0297_cs2.h' a `../linux/drivers/media/dvb/b2c2/stv0297_cs2.h'
crea el enlace simbólico `stv0297_priv.h' a `../linux/drivers/media/dvb/b2c2/stv0297_priv.h'
crea el enlace simbólico `cinergyT2.c' a `../linux/drivers/media/dvb/cinergyT2/cinergyT2.c'
crea el enlace simbólico `dmxdev.c' a `../linux/drivers/media/dvb/dvb-core/dmxdev.c'
crea el enlace simbólico `demux.h' a `../linux/drivers/media/dvb/dvb-core/demux.h'
crea el enlace simbólico `dmxdev.h' a `../linux/drivers/media/dvb/dvb-core/dmxdev.h'
crea el enlace simbólico `dvb_ca_en50221.c' a `../linux/drivers/media/dvb/dvb-core/dvb_ca_en50221.c'
crea el enlace simbólico `dvb_ca_en50221.h' a `../linux/drivers/media/dvb/dvb-core/dvb_ca_en50221.h'
crea el enlace simbólico `dvb_demux.c' a `../linux/drivers/media/dvb/dvb-core/dvb_demux.c'
crea el enlace simbólico `dvb_demux.h' a `../linux/drivers/media/dvb/dvb-core/dvb_demux.h'
crea el enlace simbólico `dvb_filter.c' a `../linux/drivers/media/dvb/dvb-core/dvb_filter.c'
crea el enlace simbólico `dvb_filter.h' a `../linux/drivers/media/dvb/dvb-core/dvb_filter.h'
crea el enlace simbólico `dvb_frontend.c' a `../linux/drivers/media/dvb/dvb-core/dvb_frontend.c'
crea el enlace simbólico `dvb_frontend.h' a `../linux/drivers/media/dvb/dvb-core/dvb_frontend.h'
crea el enlace simbólico `dvb_net.c' a `../linux/drivers/media/dvb/dvb-core/dvb_net.c'
crea el enlace simbólico `dvb_net.h' a `../linux/drivers/media/dvb/dvb-core/dvb_net.h'
crea el enlace simbólico `dvb_ringbuffer.c' a `../linux/drivers/media/dvb/dvb-core/dvb_ringbuffer.c'
crea el enlace simbólico `dvb_ringbuffer.h' a `../linux/drivers/media/dvb/dvb-core/dvb_ringbuffer.h'
crea el enlace simbólico `dvbdev.c' a `../linux/drivers/media/dvb/dvb-core/dvbdev.c'
crea el enlace simbólico `dvbdev.h' a `../linux/drivers/media/dvb/dvb-core/dvbdev.h'
crea el enlace simbólico `at76c651.c' a `../linux/drivers/media/dvb/frontends/at76c651.c'
crea el enlace simbólico `at76c651.h' a `../linux/drivers/media/dvb/frontends/at76c651.h'
crea el enlace simbólico `bcm3510.c' a `../linux/drivers/media/dvb/frontends/bcm3510.c'
crea el enlace simbólico `bcm3510.h' a `../linux/drivers/media/dvb/frontends/bcm3510.h'
crea el enlace simbólico `bcm3510_priv.h' a `../linux/drivers/media/dvb/frontends/bcm3510_priv.h'
crea el enlace simbólico `cx22700.c' a `../linux/drivers/media/dvb/frontends/cx22700.c'
crea el enlace simbólico `cx22700.h' a `../linux/drivers/media/dvb/frontends/cx22700.h'
crea el enlace simbólico `cx22702.c' a `../linux/drivers/media/dvb/frontends/cx22702.c'
crea el enlace simbólico `cx22702.h' a `../linux/drivers/media/dvb/frontends/cx22702.h'
crea el enlace simbólico `cx24110.c' a `../linux/drivers/media/dvb/frontends/cx24110.c'
crea el enlace simbólico `cx24110.h' a `../linux/drivers/media/dvb/frontends/cx24110.h'
crea el enlace simbólico `cx24123.c' a `../linux/drivers/media/dvb/frontends/cx24123.c'
crea el enlace simbólico `cx24123.h' a `../linux/drivers/media/dvb/frontends/cx24123.h'
crea el enlace simbólico `dib3000-common.c' a `../linux/drivers/media/dvb/frontends/dib3000-common.c'
crea el enlace simbólico `dib3000-common.h' a `../linux/drivers/media/dvb/frontends/dib3000-common.h'
crea el enlace simbólico `dib3000.h' a `../linux/drivers/media/dvb/frontends/dib3000.h'
crea el enlace simbólico `dib3000mb.c' a `../linux/drivers/media/dvb/frontends/dib3000mb.c'
crea el enlace simbólico `dib3000mb_priv.h' a `../linux/drivers/media/dvb/frontends/dib3000mb_priv.h'
crea el enlace simbólico `dib3000mc.c' a `../linux/drivers/media/dvb/frontends/dib3000mc.c'
crea el enlace simbólico `dib3000mc_priv.h' a `../linux/drivers/media/dvb/frontends/dib3000mc_priv.h'
crea el enlace simbólico `dvb-pll.c' a `../linux/drivers/media/dvb/frontends/dvb-pll.c'
crea el enlace simbólico `dvb-pll.h' a `../linux/drivers/media/dvb/frontends/dvb-pll.h'
crea el enlace simbólico `dvb_dummy_fe.c' a `../linux/drivers/media/dvb/frontends/dvb_dummy_fe.c'
crea el enlace simbólico `dvb_dummy_fe.h' a `../linux/drivers/media/dvb/frontends/dvb_dummy_fe.h'
crea el enlace simbólico `l64781.c' a `../linux/drivers/media/dvb/frontends/l64781.c'
crea el enlace simbólico `l64781.h' a `../linux/drivers/media/dvb/frontends/l64781.h'
crea el enlace simbólico `lgdt330x.c' a `../linux/drivers/media/dvb/frontends/lgdt330x.c'
crea el enlace simbólico `lgdt330x.h' a `../linux/drivers/media/dvb/frontends/lgdt330x.h'
crea el enlace simbólico `lgdt330x_priv.h' a `../linux/drivers/media/dvb/frontends/lgdt330x_priv.h'
crea el enlace simbólico `mt312.c' a `../linux/drivers/media/dvb/frontends/mt312.c'
crea el enlace simbólico `mt312.h' a `../linux/drivers/media/dvb/frontends/mt312.h'
crea el enlace simbólico `mt312_priv.h' a `../linux/drivers/media/dvb/frontends/mt312_priv.h'
crea el enlace simbólico `mt352.c' a `../linux/drivers/media/dvb/frontends/mt352.c'
crea el enlace simbólico `mt352.h' a `../linux/drivers/media/dvb/frontends/mt352.h'
crea el enlace simbólico `mt352_priv.h' a `../linux/drivers/media/dvb/frontends/mt352_priv.h'
crea el enlace simbólico `nxt2002.c' a `../linux/drivers/media/dvb/frontends/nxt2002.c'
crea el enlace simbólico `nxt2002.h' a `../linux/drivers/media/dvb/frontends/nxt2002.h'
crea el enlace simbólico `nxt200x.c' a `../linux/drivers/media/dvb/frontends/nxt200x.c'
crea el enlace simbólico `nxt200x.h' a `../linux/drivers/media/dvb/frontends/nxt200x.h'
crea el enlace simbólico `nxt6000.c' a `../linux/drivers/media/dvb/frontends/nxt6000.c'
crea el enlace simbólico `nxt6000.h' a `../linux/drivers/media/dvb/frontends/nxt6000.h'
crea el enlace simbólico `nxt6000_priv.h' a `../linux/drivers/media/dvb/frontends/nxt6000_priv.h'
crea el enlace simbólico `or51132.c' a `../linux/drivers/media/dvb/frontends/or51132.c'
crea el enlace simbólico `or51132.h' a `../linux/drivers/media/dvb/frontends/or51132.h'
crea el enlace simbólico `or51211.c' a `../linux/drivers/media/dvb/frontends/or51211.c'
crea el enlace simbólico `or51211.h' a `../linux/drivers/media/dvb/frontends/or51211.h'
crea el enlace simbólico `s5h1420.c' a `../linux/drivers/media/dvb/frontends/s5h1420.c'
crea el enlace simbólico `s5h1420.h' a `../linux/drivers/media/dvb/frontends/s5h1420.h'
crea el enlace simbólico `sp8870.c' a `../linux/drivers/media/dvb/frontends/sp8870.c'
crea el enlace simbólico `sp8870.h' a `../linux/drivers/media/dvb/frontends/sp8870.h'
crea el enlace simbólico `sp887x.c' a `../linux/drivers/media/dvb/frontends/sp887x.c'
crea el enlace simbólico `sp887x.h' a `../linux/drivers/media/dvb/frontends/sp887x.h'
crea el enlace simbólico `stv0297.c' a `../linux/drivers/media/dvb/frontends/stv0297.c'
crea el enlace simbólico `stv0297.h' a `../linux/drivers/media/dvb/frontends/stv0297.h'
crea el enlace simbólico `stv0299.c' a `../linux/drivers/media/dvb/frontends/stv0299.c'
crea el enlace simbólico `stv0299.h' a `../linux/drivers/media/dvb/frontends/stv0299.h'
crea el enlace simbólico `tda10021.c' a `../linux/drivers/media/dvb/frontends/tda10021.c'
crea el enlace simbólico `tda10021.h' a `../linux/drivers/media/dvb/frontends/tda10021.h'
crea el enlace simbólico `tda1004x.c' a `../linux/drivers/media/dvb/frontends/tda1004x.c'
crea el enlace simbólico `tda1004x.h' a `../linux/drivers/media/dvb/frontends/tda1004x.h'
crea el enlace simbólico `tda8083.c' a `../linux/drivers/media/dvb/frontends/tda8083.c'
crea el enlace simbólico `tda8083.h' a `../linux/drivers/media/dvb/frontends/tda8083.h'
crea el enlace simbólico `tda80xx.c' a `../linux/drivers/media/dvb/frontends/tda80xx.c'
crea el enlace simbólico `tda80xx.h' a `../linux/drivers/media/dvb/frontends/tda80xx.h'
crea el enlace simbólico `ves1820.c' a `../linux/drivers/media/dvb/frontends/ves1820.c'
crea el enlace simbólico `ves1820.h' a `../linux/drivers/media/dvb/frontends/ves1820.h'
crea el enlace simbólico `ves1x93.c' a `../linux/drivers/media/dvb/frontends/ves1x93.c'
crea el enlace simbólico `ves1x93.h' a `../linux/drivers/media/dvb/frontends/ves1x93.h'
crea el enlace simbólico `saa7146_core.c' a `../linux/drivers/media/common/saa7146_core.c'
crea el enlace simbólico `saa7146_fops.c' a `../linux/drivers/media/common/saa7146_fops.c'
crea el enlace simbólico `saa7146_hlp.c' a `../linux/drivers/media/common/saa7146_hlp.c'
crea el enlace simbólico `saa7146_i2c.c' a `../linux/drivers/media/common/saa7146_i2c.c'
crea el enlace simbólico `saa7146_vbi.c' a `../linux/drivers/media/common/saa7146_vbi.c'
crea el enlace simbólico `saa7146_video.c' a `../linux/drivers/media/common/saa7146_video.c'
crea el enlace simbólico `saa7146_vv_ksyms.c' a `../linux/drivers/media/common/saa7146_vv_ksyms.c'
crea el enlace simbólico `pluto2.c' a `../linux/drivers/media/dvb/pluto2/pluto2.c'
rm -rf video-buf.c
ln -s /lib/modules/2.6.15-22-386/source/drivers/media/video/video-buf.c video-buf.c
make -C /lib/modules/2.6.15-22-386/source  SUBDIRS=/home/sunil/dvb-kernel/build-2.6 AV7110_FIRMWARE= AV7110_OSD=y
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.15-22'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-22/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      /home/sunil/dvb-kernel/build-2.6/built-in.o
  CC [M]  /home/sunil/dvb-kernel/build-2.6/version_check.o
  CC [M]  /home/sunil/dvb-kernel/build-2.6/flexcop-pci.o
En el fichero incluído de /home/sunil/dvb-kernel/build-2.6/dvbdev.h:32,
                 de /home/sunil/dvb-kernel/build-2.6/dmxdev.h:37,
                 de /home/sunil/dvb-kernel/build-2.6/flexcop-common.h:16,
                 de /home/sunil/dvb-kernel/build-2.6/flexcop-pci.c:10:
/home/sunil/dvb-kernel/build-2.6/compat.h:7:18: error: bttv.h: No existe el fichero o el directorio
make[2]: *** [/home/sunil/dvb-kernel/build-2.6/flexcop-pci.o] Error 1
make[1]: *** [_module_/home/sunil/dvb-kernel/build-2.6] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.15-22'
make: *** [all] Error 2


---

### Post by Dr. Nick on 2006-05-11
Well glad to see you got a little further, Hope you can get it straightned out.

---

