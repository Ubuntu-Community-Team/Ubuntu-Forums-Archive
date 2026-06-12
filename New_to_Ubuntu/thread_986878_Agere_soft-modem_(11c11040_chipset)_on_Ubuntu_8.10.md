---
title: "Agere soft-modem (11c11040 chipset) on Ubuntu 8.10"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by krtica on 2008-11-19
I bought HP 550 laptop. It's cheep and Ubuntu works "out of box". Well... Almost "out of box". There is no modem.
Using a "scanModem" from [http://linmodems.org/]("http://linmodems.org/") I found that I have **11c11040** chipset. So with a little effort and searching trough Google I found this**[COLOR="Blue"] ["HOWTO"]("http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html")[/COLOR]**.

**Step 1.** - After [FONT="Courier New"]cat /proc/asound/version[/FONT] command I get this message:
***Advanced Linux Sound Architecture Driver Version 1.0.17.***

In **step 2.** I found first problem: :D
"[I]Patch your sound driver file hda_codec.c for export symbols needed by the drivers:
   1. Use your favourite PLAIN TEXT editor, such as vi or gedit, and with root permission. This file is typically located at /usr/src/linux/sound/pci/hda/hda_codec.c
   2. Add the lines EXPORT_SYMBOL(snd_hda_codec_read); and EXPORT_SYMBOL(snd_hda_codec_write); to the file, after the list of '#include' statements in the beginning.
   3. Save the file.[/I]"
I can't find this file. Nowhere. :shock:
I'm a noob. I have no knowledge to install this modem by myself. I really need modem occasionally, and I really need some help, please.
Thx.

---

### Post by talsemgeest on 2008-11-19
So when you run this command, does it come up with a blank file? ```
gksudo gedit */usr/src/linux/sound/pci/hda/hda_codec.c
```*

---

### Post by krtica on 2008-11-19
Yes.

I also tried to search for *hda_codec.c* trough all filesystem, but there is no such file.

Sound is ok.

---

### Post by krtica on 2008-11-22
Can anyone check in own Ubuntu 8.10 folder:

/usr/src/linux-headers-2.6.27-7-generic/sound/pci/hda

is there any **hda_intel.c** file? :confused:

---

### Post by PriceChild on 2008-11-23
I'm working on this too, and till I manage to get it sorted am just using a 'real' modem on a serial port.

---

### Post by krtica on 2008-11-23
I done this:
```
$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-intrepid.git ubuntu-intrepid
```
and i finally found this hda_codec.c file in the ubuntu-intrepid folder on desktop.
(Probably not smartest thing to do, but couldn't find better way at the moment. I'm only a noob. :D)

Then I copied all files from **/home/*username*/Desktop/ubuntu-intrepid/sound/pci/hda** to **/usr/src/linux-headers-2.6.27-7-generic/sound/pci/hda** folder. I patched hda_codec.c with those two lines:

```
EXPORT_SYMBOL(snd_hda_codec_read);
EXPORT_SYMBOL(snd_hda_codec_write);
```

Then in **/usr/src/linux-headers-2.6.27-7-generic**, I run the following command:
```
$ sudo make oldconfig
scripts/kconfig/conf -o arch/x86/Kconfig
#
# configuration written to .config
#
```

But after I issued make modules command, in same folder, I get this:
```
c$ sudo make modules
scripts/kconfig/conf -s arch/x86/Kconfig
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2
```

??? :confused:

---

### Post by ieee488 on 2008-11-23
In that HOWTO page, there is a link to precompiled driver for Ubuntu 8.04.
Maybe give that a try.

My IBM Thinkpad 600E has a modem using DSP chip. Back in the days I was still on dial-up, I found it much easier to just buy a PMCIA modem. The 3Com 3CXM756 or 3CXM556 work (I have both) and can usually be found used on eBay for $15-20 including shipping.

---

### Post by krtica on 2008-11-23
I tried. It doesn't work. :(

I need modem in rare occasions, but those occasions can be really important. And I can't predict it, so I would like to use modem which is already on laptop.

Can someone tell me - when I'm building those modules - are headers enough or I need **linux-source**?

---

### Post by krtica on 2008-11-30
Ok, I'm back to this problem.

I downloaded linux-source-2.7.27.
Done
```
$ make modules
```
But!

When I finished with making modules, first thing I noticed is that size of old "snd-hda-intel.ko" file in "**/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda**" folder was 494.8 KB (506716 bytes).
Size of new file in "**/usr/src/linux-source-2.6.27/sound/pci/hda**" folder was 2.1 MB (2249480 bytes).
I'm not quite familiar with Linux and compiling, but I think that it is to big difference for just two lines of code:
```
EXPORT_SYMBOL(snd_hda_codec_read);
EXPORT_SYMBOL(snd_hda_codec_write);
```
in hda_codec.c file.
:confused:
After that I copied new file into the "/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda" folder, and I rebooted computer.
**[COLOR="Red"]Sound didn't work.[/COLOR]**

Also, I found in "Makefile", which was in "/usr/src/linux-source-2.6.27/sound/pci/hda", next content:

```
snd-hda-intel-y := hda_intel.o
# since snd-hda-intel is the only driver using hda-codec,
# merge it into a single module although it was originally
# designed to be individual modules
snd-hda-intel-y += hda_codec.o
snd-hda-intel-$(CONFIG_PROC_FS) += hda_proc.o
snd-hda-intel-$(CONFIG_SND_HDA_HWDEP) += hda_hwdep.o
snd-hda-intel-$(CONFIG_SND_HDA_GENERIC) += hda_generic.o
snd-hda-intel-$(CONFIG_SND_HDA_CODEC_REALTEK) += patch_realtek.o
snd-hda-intel-$(CONFIG_SND_HDA_CODEC_CMEDIA) += patch_cmedia.o
snd-hda-intel-$(CONFIG_SND_HDA_CODEC_ANALOG) += patch_analog.o
snd-hda-intel-$(CONFIG_SND_HDA_CODEC_SIGMATEL) += patch_sigmatel.o
snd-hda-intel-$(CONFIG_SND_HDA_CODEC_SI3054) += patch_si3054.o
snd-hda-intel-$(CONFIG_SND_HDA_CODEC_ATIHDMI) += patch_atihdmi.o
snd-hda-intel-$(CONFIG_SND_HDA_CODEC_CONEXANT) += patch_conexant.o
snd-hda-intel-$(CONFIG_SND_HDA_CODEC_VIA) += patch_via.o

obj-$(CONFIG_SND_HDA_INTEL) += snd-hda-intel.o

```
**[COLOR="DarkRed"]Does it all have to be in it?[/COLOR]**
I have been told:
> Your audio chipset is  AD198x Analog. So among the set you could probably delete all except snd-hda-intel-$(CONFIG_SND_HDA_CODEC_ANALOG) += patch_analog.o
I get this for my card:
> NAME="Audio device: Intel Corporation 82801H "
> sound: Intel 82801H (ICH8 Family) HD Audio Controller
**[COLOR="DarkRed"]Does anyone know for sure?[/COLOR]**
*(becouse I didn't remove any of lines during making modules)*

Also, during compiling of drivers, (which were just fine compiled on 8.04), there are messages:
> /usr/src/modules/agrsm-20080808$ make module
make -C /usr/src/linux-source-2.6.27/
SUBDIRS=/usr/src/modules/agrsm-20080808 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.27'
 CC [M]  /usr/src/modules/agrsm-20080808/agrsoftmodem.o
/usr/src/modules/agrsm-20080808/agrsoftmodem.c: In function 'kill_proc_wrap':
/usr/src/modules/agrsm-20080808/agrsoftmodem.c:319: error: implicit
declaration of function 'kill_proc'
/usr/src/modules/agrsm-20080808/agrsoftmodem.c: In function 'x_task_queue_init':
/usr/src/modules/agrsm-20080808/agrsoftmodem.c:450: warning:
assignment from incompatible pointer type
/usr/src/modules/agrsm-20080808/agrsoftmodem.c: In function
'x_task_queue_init_usb':
/usr/src/modules/agrsm-20080808/agrsoftmodem.c:462: warning:
assignment from incompatible pointer type
/usr/src/modules/agrsm-20080808/agrsoftmodem.c: At top level:
/usr/src/modules/agrsm-20080808/agrsoftmodem.c:489: warning: function
declaration isn't a prototype
/usr/src/modules/agrsm-20080808/agrsoftmodem.c:515: warning: function
declaration isn't a prototype
/usr/src/modules/agrsm-20080808/agrsoftmodem.c:525: warning: function
declaration isn't a prototype
/usr/src/modules/agrsm-20080808/agrsoftmodem.c:532: warning: function
declaration isn't a prototype
make[2]: *** [/usr/src/modules/agrsm-20080808/agrsoftmodem.o] Error 1
make[1]: *** [_module_/usr/src/modules/agrsm-20080808] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
make: *** [module] Error 2
And next thing I found is this:
> 8.10 came with a new gcc compiler version. This is a version that breaks things and adds some rather non-conservative warnings (like warnings for not reading a return value for a function). The addition of a new libtool has its own set of problems (like not being able to compile new KDevelop projects).
**Can it be connected?**
I don't know... I'm just a beginner...
So, if anyone have some idea what to do next, **_please_**, tell me.

---

### Post by Nick Zhuravlev on 2009-04-14
I have a stock kernel (2.6.27-rc9), not exactly the one from 8.10 but close
enough. I successfully compiled the driver on Toshiba
Satellite L40 by following the manual found at
[http://linmodems.technion.ac.il/packages/ltmodem/11c11040](http://linmodems.technion.ac.il/packages/ltmodem/11c11040)

Once you patch the hda_codec.c file as suggested at that manual,
you can run:

$ sudo make modules_install

to make sure the module goes to the right place, in my case it is
/lib/modules/2.6.27-rc9/kernel/sound/pci/hda/snd-hda-intel.ko
In Ubuntu it could be different, something like this:
/lib/modules/2.6.22-15-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

My ALSA is 1.0.17, so I used the agrsm-HDA-20080721.tar.bz2 version of
the driver. I did have to patch it, but very lightly. Please see the
attached file. Basically, you have to nuke the deprecated kill_proc() call
and change "tty" to "port.tty" because a corresponding data structure
has changed in the recent kernels.

After the modules are compiled, installed, and loaded, this is what I
get with 'minicom -s':

-----------------------------------
Welcome to minicom 2.3-rc1

OPTIONS: I18n
Compiled on Dec 10 2007, 10:36:19.
Port /dev/ttyAGS3

                 Press CTRL-A Z for help on special keys

AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
OK
ATDT 3432152
NO DIALTONE
ath
OK
-----------------------------------

So, looks like the modem is Ok. I don't have a phone line at home, so
cannot test it any further.

---

