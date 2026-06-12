---
title: "HOWTO:  TI SD Card Reader *FEISTY SUPPORTED*"
date: 2007-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by macogw on 2007-04-23
**[COLOR="Red"]There are no drivers for Sony MS, Sony MS Pro, and xD.  They have yet to be written.  This will only get SD & MMC cards working.[/COLOR]**

Copied from my blog:

**Dapper**: sorry, no support in this kernel. Upgrade to Edgy or Feisty, or try using the Feisty method (let me know if it works).  If the Feisty way doesn't work, maybe I'll download the 2.6.15 sources and see if I can find out what's missing to make it work on Dapper, but I don't have a Dapper box to test with

**Edgy**: The modules for the card reader aren't loading. 
```
gksudo gedit /etc/modules
```
 Add to that file:
> tifm_sd
tifm_7xx1
tifm_core
Save it, and on next reboot it will work fine. To get it working right now: 
```
sudo modprobe tifm_7xx1
sudo modprobe tifm_core
sudo modprobe tirm_sd
```

**Feisty**: The 2.6.20-15 kernel is lacking proper TI modules (version 0.7) and a few header files are messed up / missing. This will correct the headers and install version 0.8.
**jdong says I should mention that I don't know yet how this will effect (if it does at all) kernel updates.  I don't believe full kernel updates will be affected at all since the files are only in the current kernel, *however* if tifm is updated through the update manager (without a kernel update), I don't know what will happen.  If you see a tifm update on the update manager, you should probably run the uninstall script before updating**
**[color="red"]If your Feisty is up to date and using 2.6.20-16 (use "uname -r" to check), this script won't help.  It just adds v 0.8 of the drivers, and that is in the 2.6.20-16 build.  A fresh install of Feisty has 2.6.20-15 though, and that needed the script.[/color]**

If you haven't compiled anything before: 
```
sudo aptitude install build-essential linux-headers-`uname -r`
```
You will need to download [my TIFM installer](http://geocities.com/dollzrgr8/tifm_install.tar.gz). Save that installer file somewhere (Desktop works) and extract it or use the "Archive Manager" to extract it immediately. There's a readme, but I'll tell you what to do anyway (note, I'm sure the terminal way works, I didn't test the GUI way, so if it doesn't ask for your password or it doesn't do anything after asking for your password, try the terminal way).

*GUI way*: Right click on install.sh. 
Go to properties > permissions and check off "execute". 
Double click on install.sh. 
Choose "run in terminal."

*Terminal way*: If you saved and extracted to your Desktop (if not, cd to wherever you saved it), ```
cd ~/Desktop
sudo chmod +x install.sh
sh install.sh
```

It should now run, copy files, compile, etc. At the end of that, you should have a working card reader. Please let me know if this doesn't work for you so I can modify it. Ubuntu did not include some of the necessary files by default in the kernel (part of what the script does is fix that), and I doubt that kernel updates will include those files either. As such, you will probably need to run this script after each kernel update.

---

### Post by ghimli on 2007-04-24
First, thank you for your tuto.
I had some issues with your method, but in the end, I got my TI card reader "Feisty supported" with your path. :popcorn: 

First, your install.sh has some errors : some spaces which would not be there at the lines 11, 13 and 15 :
```
sudo mv /lib/modules/`uname -r`/kernel/drivers/misc/tifm_core.ko /lib/module**s    /`u**name -r`/kernel/drivers/misc/tifm_core.ko-old
sudo mv /lib/modules/`uname -r`/kernel/drivers/misc/tifm_7xx1.ko /lib/module**s    /`u**name -r`/kernel/drivers/misc/tifm_7xx1.ko-old
sudo mv /lib/modules/`uname -r`/kernel/drivers/mmc/tifm_sd.ko /lib/modules/**`u    n**ame -r`/kernel/drivers/mmc/tifm_sd.ko-old
```

This breaks your backup system :) 

But I had one more mistake : on my computer, the module tifm_sd is in fact located in ```
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc**/host**
```
Which implies two more problems :
[LIST]
[*]first, the line 15 is wrong again : miss "/host/" :
```
sudo mv /lib/modules/`uname -r`/kernel/drivers/mmc**/host/**tifm_sd.ko /lib/modules/`uname -r`/kernel/drivers/mmc**/host/**tifm_sd.ko-old
```
[*]and then, your script seems to install the new driver tifm_sd in the wrong path : 
```
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc
```
instead of :
```
/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/host/
```
[/LIST]

So, I put the script install.sh which I assume right :
```
#!/bin/bash
touch install.log
cd mmc
sudo cp protocol.h /usr/src/linux-headers-`uname -r`/include/linux/mmc/protocol.h
echo "New protocol.h added" >> ../install.log
sudo mv /usr/src/linux-headers-`uname -r`/include/linux/mmc/host.h /usr/src/linux-headers-`uname -r`/include/linux/mmc/host.h.old
echo "Old host.h file backed up" >> ../install.log
sudo cp host.h /usr/src/linux-headers-`uname -r`/include/linux/mmc/host.h
echo "New host.h file copied in" >> ../install.log
cd ../tifm
sudo mv /lib/modules/`uname -r`/kernel/drivers/misc/tifm_core.ko /lib/modules/`uname -r`/kernel/drivers/misc/tifm_core.ko-old
echo "Backed up tifm_core.ko (named tifm_core.ko-old)" >> ../install.log
sudo mv /lib/modules/`uname -r`/kernel/drivers/misc/tifm_7xx1.ko /lib/modules/`uname -r`/kernel/drivers/misc/tifm_7xx1.ko-old
echo "Backed up tifm_7xx1.ko (named tifm_7xx1.ko-old)" >> ../install.log
sudo mv /lib/modules/`uname -r`/kernel/drivers/mmc/host/tifm_sd.ko /lib/modules/`uname -r`/kernel/drivers/mmc/host/tifm_sd.ko-old
echo "Backed up tifm_sd.ko (named tifm_sd.ko-old)" >> ../install.log
sudo make
sudo make install
echo "Ran tifm's Makefile" >> ../install.log
sudo make clean
echo "Cleaned tifm directory" >> ../install.log
```

And then, I needed to run some commands after this script, to correct the mistake of wrong path :
[LIST]
[*]Backuping the old module :
```
sudo mv /lib/modules/`uname -r`/kernel/drivers/mmc/host/tifm_sd.ko /lib/modules/`uname -r`/kernel/drivers/mmc/host/tifm_sd.ko-old
```
[*]Installing the new one, which is wrong-located :
```
sudo mv /lib/modules/`uname -r`/kernel/drivers/mmc/tifm_sd.ko /lib/modules/`uname -r`/kernel/drivers/mmc/host/
```
[/LIST]

After this, I restarted some modules (there, I can't say if there are some too many, surely yes :) ) :
```
sudo rmmod tifm_sd
sudo rmmod mmc_block
sudo rmmod sdhci
sudo rmmod tifm_7xx1
sudo rmmod tifm_core
sudo modprobe tifm_sd
sudo modprobe tifm_7xx1 
sudo modprobe tifm_core
sudo modprobe mmc_core
sudo modprobe mmc_block
sudo modprobe sdhci
```

Finally I inserted my card and whoooooo, it works !! :guitar: 

To finish, maybe you should look to your uninstall.sh script too to modify this mistakes.
And maybe we need to put tifm_sd in /etc/modules ?
Thanks a lot again

Ghimli

---

### Post by ghimli on 2007-04-24
The second mistake is in fact due to an error in the makefile in your tifm_sd folder.

---

### Post by macogw on 2007-04-25
The Makefile is from the original devs.  With the new tifm_sd.ko in that location, it works fine, but I'll modify it to use Ubuntu's locations.  

I updated the package since you downloaded it to get rid of the whitespace and remove the line that messes with tifm_sd.ko.

I already tested about /etc/modules, and it doesn't have to be added to that file like it did in Edgy.  /etc/modules can be blank and have it work.  

I've just uploaded a new version which uses Ubuntu's placement for the tifm_sd.ko and which automatically unloads and reloads the modules.

Hopefully that clears up all the bugs.

---

### Post by ghimli on 2007-04-25
Thank you again !

I checked for the new archive and everything looks fine. :)
Except one thing : maybe unprobing mmc_core should not work directly, because of its dependances (sdhci & mmc_block) are still probed ?

edit : I always forget : I'm running Feisty Fawn 32 on a HP Pavilion dv 5142eu, just for information .

---

### Post by Nonsenseproteine on 2007-04-25
Hi Maco,

I tried your install skript and it worked well. But afterwards nothing changed. dmesg is still saying that " ms card is detected in socket 0" but nothing else happens.
I tried the rmmod and modprobe commands which ghimli suggested nad got following dmesg output

> [ 6521.012000] tifm0 : demand removing card from socket 0:0
[ 6522.688000] tifm_core: MemoryStick card detected in socket 0:0
[ 6522.696000] tifm_sd: disagrees about version of symbol tifm_eject
[ 6522.696000] tifm_sd: Unknown symbol tifm_eject
[ 6522.696000] tifm_sd: disagrees about version of symbol tifm_register_driver
[ 6522.696000] tifm_sd: Unknown symbol tifm_register_driver
[ 6522.696000] tifm_sd: disagrees about version of symbol tifm_unmap_sg
[ 6522.696000] tifm_sd: Unknown symbol tifm_unmap_sg
[ 6522.696000] tifm_sd: disagrees about version of symbol tifm_map_sg
[ 6522.696000] tifm_sd: Unknown symbol tifm_map_sg
[ 6522.696000] tifm_sd: disagrees about version of symbol tifm_unregister_driver
[ 6522.696000] tifm_sd: Unknown symbol tifm_unregister_driver

When i tried to load tifm_sd an error occured:
> FATAL: Error inserting tifm_sd (/lib/modules/2.6.20-15-generic/kernel/drivers/mmc/host/tifm_sd.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I tried to get a clue of the content in [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/53923](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/53923)
but I not sure if i did.
Maybe you can give me a hint.

---

### Post by Metacarpal on 2007-04-25
I had to
```
sudo modprobe -r sdhci
```
and
```
sudo modprobe -r mmc_core
```
to do it, but this worked like a charm.

I love you.

---

### Post by macogw on 2007-04-25
> **Nonsenseproteine said:**
> Hi Maco,

I tried your install skript and it worked well. But afterwards nothing changed. dmesg is still saying that " ms card is detected in socket 0" but nothing else happens.
I tried the rmmod and modprobe commands which ghimli suggested nad got following dmesg output


When i tried to load tifm_sd an error occured:


I tried to get a clue of the content in [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/53923](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/53923)
but I not sure if i did.
Maybe you can give me a hint.
In the folder that resulted from unzipping, look inside the tifm folder.  There should be a Module.symvers text file.  What does it say?

---

### Post by tonywhelan on 2007-04-25
> **Nonsenseproteine said:**
> Hi Maco,

I tried your install script and it worked well. But afterwards nothing changed. dmesg is still saying that " ms card is detected in socket 0" but nothing else happens.
I tried the rmmod and modprobe commands which ghimli suggested nad got following dmesg output


I ran the TIFM script OK, but SD card still not mounting, Then I rebooted and inserted my SD card and all was well. So maybe a reboot (or at least some modprobes)  is needed to get it all going. Rebooting seemed easier!

[COLOR="Magenta"]
MACOGW: thank you very much for the work you've done on this![/COLOR]

---

### Post by Nonsenseproteine on 2007-04-26
Hi Macow,

First of all thanks for your help. 

The Module.symvers file has following content:
> 0x7625ea0d	tifm_alloc_device	drivers/misc/tifm_core	EXPORT_SYMBOL
0xb1deb2e3	tifm_map_sg	drivers/misc/tifm_core	EXPORT_SYMBOL
0x39f86aa1	tifm_queue_work	/home/moritz/Desktop/tifm_install/tifm/tifm_core	EXPORT_SYMBOL
0xd98bbe7e	tifm_alloc_adapter	drivers/misc/tifm_core	EXPORT_SYMBOL
0x257b1daf	tifm_add_adapter	drivers/misc/tifm_core	EXPORT_SYMBOL
0xee5a18c5	tifm_unregister_driver	drivers/misc/tifm_core	EXPORT_SYMBOL
0xdf91b1db	tifm_free_adapter	drivers/misc/tifm_core	EXPORT_SYMBOL
0x5104a1b3	tifm_eject	drivers/misc/tifm_core	EXPORT_SYMBOL
0x56d708ec	tifm_free_device	drivers/misc/tifm_core	EXPORT_SYMBOL
0x83b47cf3	tifm_unmap_sg	drivers/misc/tifm_core	EXPORT_SYMBOL
0x645f016b	tifm_register_driver	drivers/misc/tifm_core	EXPORT_SYMBOL
0xe47f7293	tifm_remove_adapter	drivers/misc/tifm_core	EXPORT_SYMBOL

I tried a reboot and all the modprobe's with tifm7xx1, tifm_core, mmc_core, mmc_block and tifm_sd. Last one didn't work.

> moritz@Mumpitz:~$ lsmod | grep tifm
tifm_7xx1               8960  0
tifm_core              11396  1 tifm_7xx1
moritz@Mumpitz:~$ lsmod | grep mmc
mmc_core               26756  0

These modules are autoloaded on boot. I have no entry in the modprobe.conf. I'm loading the  modules manually.

I'm trying to mount an Sony ms card form my mobile phone. I have no SD card to try, 

Following devices from TI are listet:

> 08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


I'm using the 2.6.20-15-generic Kernel from the repositories

br

M.

---

### Post by macogw on 2007-04-27
There are no drivers for Sony's MS and MS Pro or for xD.  MMC & SD are the only ones for which drivers exist.  Sorry I didn't read closely enough when you put up the dmesg error the first time.

---

### Post by shawnrgr on 2007-04-28
Ran your script cause i desperately need my sd card working. seemed like everything worked fine, no errors when I ran the script. But nothing happens! When I plug the SD card in (mini sd in SD converter card) nothing even posts in the logs. Here is some info on my system. 

Ubuntu Feisty Fawn
Kernal: 2.6.20-15-generic (#2 SMP Sun Apr 15 07:36:31 UTC 2007)
AMD Athlon(tm) 64 Processor 3700+

Texas Instruments
TSB43AB21 IEEE-1394a-2000
PCI1620 PC Card Controller

Module.symvers:
```
0x7625ea0d	tifm_alloc_device	drivers/misc/tifm_core	EXPORT_SYMBOL
0xb1deb2e3	tifm_map_sg	drivers/misc/tifm_core	EXPORT_SYMBOL
0x39f86aa1	tifm_queue_work	/home/maco/Desktop/tifm_install/tifm/tifm_core	EXPORT_SYMBOL
0xd98bbe7e	tifm_alloc_adapter	drivers/misc/tifm_core	EXPORT_SYMBOL
0x257b1daf	tifm_add_adapter	drivers/misc/tifm_core	EXPORT_SYMBOL
0xee5a18c5	tifm_unregister_driver	drivers/misc/tifm_core	EXPORT_SYMBOL
0xdf91b1db	tifm_free_adapter	drivers/misc/tifm_core	EXPORT_SYMBOL
0x5104a1b3	tifm_eject	drivers/misc/tifm_core	EXPORT_SYMBOL
0x56d708ec	tifm_free_device	drivers/misc/tifm_core	EXPORT_SYMBOL
0x83b47cf3	tifm_unmap_sg	drivers/misc/tifm_core	EXPORT_SYMBOL
0x645f016b	tifm_register_driver	drivers/misc/tifm_core	EXPORT_SYMBOL
0xe47f7293	tifm_remove_adapter	drivers/misc/tifm_core	EXPORT_SYMBOL
```

Please Help!!!!

---

### Post by macogw on 2007-04-29
Did you try rebooting so that the new modules are loaded?

---

### Post by shawnrgr on 2007-04-29
Yes I have rebooted many times since then. Still nothing.

---

### Post by macogw on 2007-04-30
lsmod | grep sd
and see if the tifm_sd is loaded, if it's not modprobe it and add it to /etc/modules

If that doesn't work, I guess you could try the setpci hack.  I've heard it doesn't work with really new models, and it shouldn't be necessary with the native drivers, but since v 1.0 of the drivers isn't out, maybe not all models are supported just yet.  To do that:

setpci -s $BUSID 4c.b=0x22
modprobe sdhci

$BUSID is the 04:09.2 in
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
so replace it with whatever number yours is

I've never seen it called PC Card.  Usually it's either like mine or says FlashMedia.  PC Card usually refers to PCMCIA (the wide slot where you can put a wireless card).  Are you sure your card reader is Texas Instruments?

---

### Post by BigBob on 2007-04-30
Hi macogw,

Since I'm in same situation than all others, I have read this thead.

However, there is a thing I don't understand :

- Feisty reach the release date with this bug.

Why, since the release, they don't released a new modules package with this bug correction ?

A++

PS: Anyhow, good job !!!

---

### Post by tcabeen on 2007-05-01
macogw:  Thank you for this post.  I found this forum while googling around for a solution to this issue, and this was simple as pie.  I've got one of the Toshibas with the TI reader, and finally made the switch to linux over the weekend (read: I have no idea what I'm doing here...)  I ran the script the easy way (didn't even need to change the permissions).  It asked for my password, and that was that.  Nothing worked right away, of course, but as soon as I rebooted, we were good to go.

I tested with a 128MB card first, then a 2GB card.  Both worked flawlessly.

Trackpad and wireless still work as well, so it didn't screw anything up in the process.

Thanks again!

---

### Post by brazzmonkey on 2007-05-01
this helped me too. thx !

---

### Post by pjssilva on 2007-05-01
Unfortunately the script didn'work for me. I present the deatils below.

I have a new U205 S5067 laptop. This is a relatively new version of the U200 Satellite series from Toshiba.

The relevant part of my lscpi is:

03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

I have downloaded the script. It compiled cleanly and installed the new modules. However, after reboot the sd didn't work. At that moment I had the following modules loaded:

mmc_core
sdhci
tifm_core
tifm_7xx1

Note that tifm_sd and mmc_block are not loaded.

After that I tried the following variations:

1) The modules above + tifm_sd
2) The modules aboce + tifm_sd and mmc_block
3) The modules above - sdhci + tifm_sd
4) The modules above -sdhci + tifm_sd and mmc_block
5) The setpci hack:

 sudo setpci -s 03:0b.2 4c.b=0x22

+ sdhci

I also tried:

sudo setpci -s 03:0b.3 4c.b=0x22

+ sdhci.

In all cases the sd didn't work. The file /var/log/messages print messages like:

When loading sdhci:
May  1 22:22:33 trinity kernel: [  742.232000] sdhci: Secure Digital Host Contro
ller Interface driver
May  1 22:22:33 trinity kernel: [  742.232000] sdhci: Copyright(c) Pierre Ossman
May  1 22:22:33 trinity kernel: [  742.232000] sdhci: SDHCI controller found at 
0000:03:0b.3 [104c:803c] (rev 0)
May  1 22:22:33 trinity kernel: [  742.232000] ACPI: PCI Interrupt 0000:03:0b.3[
D] -> GSI 23 (level, low) -> IRQ 19
May  1 22:22:33 trinity kernel: [  742.232000] mmc0: SDHCI at 0xff9ff700 irq 19 
DMA

When loading tifm_7xx1:
May  1 22:24:41 trinity kernel: [  870.132000] ACPI: PCI Interrupt 0000:03:0b.2[D] -> GSI 23 (level, low) -> IRQ 19

If I insert the sd card there isn't any messages in /var/log/messages, /var/log/dmesg and /var/log/kern.log

---

### Post by macogw on 2007-05-02
> **BigBob said:**
> Hi macogw,

Since I'm in same situation than all others, I have read this thead.

However, there is a thing I don't understand :

- Feisty reach the release date with this bug.

Why, since the release, they don't released a new modules package with this bug correction ?

A++

PS: Anyhow, good job !!!

Left hand didn't know what the right one was doing.  One dev upgraded to the working drivers.  Another didn't know they were at 0.8 and thought they were still 0.6 so he "upgraded" them to 0.7 which are broken, but it was really a downgrade since while he thought it was 0.6 it was really 0.8.  The dev who did the downgrade has been notified and said he'll try to get a patch released through updates.

---

### Post by macogw on 2007-05-02
> **pjssilva said:**
> Unfortunately the script didn'work for me. I present the deatils below.

I have a new U205 S5067 laptop. This is a relatively new version of the U200 Satellite series from Toshiba.

The relevant part of my lscpi is:

03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

I have downloaded the script. It compiled cleanly and installed the new modules. However, after reboot the sd didn't work. At that moment I had the following modules loaded:

mmc_core
sdhci
tifm_core
tifm_7xx1

Note that tifm_sd and mmc_block are not loaded.

After that I tried the following variations:

1) The modules above + tifm_sd
2) The modules aboce + tifm_sd and mmc_block
3) The modules above - sdhci + tifm_sd
4) The modules above -sdhci + tifm_sd and mmc_block
5) The setpci hack:

 sudo setpci -s 03:0b.2 4c.b=0x22

+ sdhci

I also tried:

sudo setpci -s 03:0b.3 4c.b=0x22

+ sdhci.

In all cases the sd didn't work. The file /var/log/messages print messages like:

When loading sdhci:
May  1 22:22:33 trinity kernel: [  742.232000] sdhci: Secure Digital Host Contro
ller Interface driver
May  1 22:22:33 trinity kernel: [  742.232000] sdhci: Copyright(c) Pierre Ossman
May  1 22:22:33 trinity kernel: [  742.232000] sdhci: SDHCI controller found at 
0000:03:0b.3 [104c:803c] (rev 0)
May  1 22:22:33 trinity kernel: [  742.232000] ACPI: PCI Interrupt 0000:03:0b.3[
D] -> GSI 23 (level, low) -> IRQ 19
May  1 22:22:33 trinity kernel: [  742.232000] mmc0: SDHCI at 0xff9ff700 irq 19 
DMA

When loading tifm_7xx1:
May  1 22:24:41 trinity kernel: [  870.132000] ACPI: PCI Interrupt 0000:03:0b.2[D] -> GSI 23 (level, low) -> IRQ 19

If I insert the sd card there isn't any messages in /var/log/messages, /var/log/dmesg and /var/log/kern.log
What the end part is saying (that trinity kernel stuff) is that it's using SDHCI.  If it's a new model of TI card reader to go with your new model of laptop, SDHCI probably won't work, and the TIFM ones are the only working ones.  Try 
sudo rmmod sdhci
and then modprobe the tifm_sd and mmc_block ones.  If it's trying to use sdhci when it can't for that model, that'd be a problem.  If that doesn't help, try asking in bug 53923 since they're the ones that actually figured out the problem.  I just made a script to implement what they said would fix it, and it's worked for at least some of us.  Variation between models can always cause unexpected results, of course.

---

### Post by pandasonic on 2007-05-03
Try this:

1. Enter this at the terminal:
```
lspci
```

You'll get something like this:
> 02:09.0 CardBus bridge: Texas Instruments PCI6411,6421,6611,6621,7411,7421,7611,7621 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments PCI7411,7421,7611,7621 Firewire Controller
**02:09.3** Unknown mass storage controller: Texas Instruments PCI6411,6421,6611,6621,7411,7421,7611,7621 Flash Media Controller
02:09.4 Class 0805: Texas Instruments PCI6411,6421,6611,6621,7411,7421,7611,7621 SD Host Controller

2. Now enter this:
```
setpci -s **02:09.3** 4c
```
Note: Make sure you enter the right value depending on your result from entering: lspci


It works on my HP dv1000. Good luck.

---

### Post by macogw on 2007-05-03
> **pandasonic said:**
> Try this:

1. Enter this at the terminal:
```
lspci
```

You'll get something like this:


2. Now enter this:
```
setpci -s **02:09.3** 4c
```
Note: Make sure you enter the right value depending on your result from entering: lspci


It works on my HP dv1000. Good luck.

Yeah, that's the setpci hack.  It's supposed to be unnecessary with the tifm modules, and it's also supposed to not work at all on very new models of card readers.

---

### Post by Sawert on 2007-05-08
Thanks! This helped me a lot!

Both my external hard drive and my iPod was mounted automatically without having to do anything else. My card reader and my cellphone did not, and this has been so annoying! I didn't get it since all devices are plugged in via USB but now I realize what I was missing. Just followed your first steps and boom, when I plug in a devices it pops up on my desktop and the "what to do" message shows up! Thanks!

---

### Post by nepenthes on 2007-05-08
Script worked like a charm on my Compaq Presario v2000 with Feisty AMD64.

I love you :mrgreen:

---

### Post by novice_pdg on 2007-05-11
Hi there, I'm very new to all things Linux, Ubuntu, etc and have been progressively re-building my Toshiba laptop and its peripherals.  While I have has some success with most devices I am really struggling with getting the mmc host working.  I have followed the instruction posted below and all seemed to be going well with the install until I struck this message:

cannot stat `/lib/modules/2.6.15-28-386/kernel/drivers/misc/tifm_core.ko': No such file or directory

I have no idea what this message means not having a developer background, etc.  Can anyone assist?

regards  pdg

---

### Post by derekguy on 2007-05-14
Brilliant! Worked a treat for me. i had to reboot before it recognised the card.

I am using a Compaq Presario B1800 with an integrated TI card reader.

One thing: The MMC card shows up on my desktop and is named "NO_NAME" is there a way to change it to say MMC or SD?

Thanks a bunch for the How To.

---

### Post by ianw1974 on 2007-05-21
I find none of this works for me or my card reader.  It has worked previously in Edgy, as well as Mandriva 2007 and Debian Etch/Sid.

I only needed to use mmc_core, mmc_block and sdhci.  Now I find with Feisty that nothing works, no matter what I try.

I rebooted once with the card in and it worked, but it hasn't since.

---

### Post by glennric on 2007-05-21
I have been trying to get the card reader in my laptop to work for a long time now.  The laptop is a Toshiba Satellite Pro 6000.  The card shows up with lspci as

```
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
```

The information about the device from lshw is
```
*-system UNCLAIMED
             description: System peripheral
             product: SD TypA Controller
             vendor: Toshiba America Info Systems
             physical id: 12
             bus info: pci@00:12.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:38104000-381041ff irq:255
```

The only pertinent information from /var/log/messages or dmesg is
```
May 21 08:47:09 lappy kernel: [  708.904000] sdhci: Secure Digital Host Controller Interface driver
May 21 08:47:09 lappy kernel: [  708.904000] sdhci: Copyright(c) Pierre Ossman

```

I have tried everything I have read to get this card to work but get absolutely nothing.  I haven't even seen the led come on for the card reader.  Does anyone have any ideas how to get this to work?

---

### Post by gamerteck on 2007-05-22
This worked worked for me on my HP nc6230.  Kudos!:guitar:

---

### Post by treesurf on 2007-05-23
This worked perfectly for me on a Gateway NX570X.  Thank you!

Incidentally, the script never asked me for a password.  I just double clicked on the install icon and away it went.

---

### Post by Zio Bobo on 2007-05-24
**SD Card reader working under Ubuntustudio 7.04**

Macogw's procedure (see first post) to get SD card readers to work...worked wonders also with Ubuntustudio 7.04 (on a HP Pavillion dv1589EA)!

THANKS!!!

---

### Post by elatre on 2007-05-26
Thank you, it works for me (HP nx6325).
But: it doesn't work anymore after a standby. Any solutions?

---

### Post by macogw on 2007-05-28
> **elatre said:**
> Thank you, it works for me (HP nx6325).
But: it doesn't work anymore after a standby. Any solutions?
You could try putting the modules into the blacklist for suspend (somewhere in /etc/).  You'll have to Google for the proper directory though, sorry.  I don't play with init too much.

---

### Post by macogw on 2007-05-28
> **glennric said:**
> I have been trying to get the card reader in my laptop to work for a long time now.  The laptop is a Toshiba Satellite Pro 6000.  The card shows up with lspci as

```
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
```

The information about the device from lshw is
```
*-system UNCLAIMED
             description: System peripheral
             product: SD TypA Controller
             vendor: Toshiba America Info Systems
             physical id: 12
             bus info: pci@00:12.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:38104000-381041ff irq:255
```

The only pertinent information from /var/log/messages or dmesg is
```
May 21 08:47:09 lappy kernel: [  708.904000] sdhci: Secure Digital Host Controller Interface driver
May 21 08:47:09 lappy kernel: [  708.904000] sdhci: Copyright(c) Pierre Ossman

```

I have tried everything I have read to get this card to work but get absolutely nothing.  I haven't even seen the led come on for the card reader.  Does anyone have any ideas how to get this to work?
Better off posting a thread in the laptops or beginners forum.  This thread is just for Texas Instruments.

---

### Post by macogw on 2007-05-28
> **novice_pdg said:**
> Hi there, I'm very new to all things Linux, Ubuntu, etc and have been progressively re-building my Toshiba laptop and its peripherals.  While I have has some success with most devices I am really struggling with getting the mmc host working.  I have followed the instruction posted below and all seemed to be going well with the install until I struck this message:

cannot stat `/lib/modules/2.6.15-28-386/kernel/drivers/misc/tifm_core.ko': No such file or directory

I have no idea what this message means not having a developer background, etc.  Can anyone assist?

regards  pdg

That script is just for Feisty, 2.6.20.  You're using Dapper.  Without the part at the beginning of the script that removes old modules, it *might* work.  That error you posted is it responding to the script telling it to remove the old non-working modules in Feisty.  Try opening up the install file with Gedit or Kate, and get rid of these lines:

sudo mv /lib/modules/`uname -r`/kernel/drivers/misc/tifm_core.ko /lib/modules/`uname -r`/kernel/drivers/misc/tifm_core.ko-old &&
sudo mv /lib/modules/`uname -r`/kernel/drivers/misc/tifm_7xx1.ko /lib/modules/`uname -r`/kernel/drivers/misc/tifm_7xx1.ko-old &&
sudo mv /lib/modules/`uname -r`/kernel/drivers/mmc/host/tifm_sd.ko /lib/modules/`uname -r`/kernel/drivers/mmc/host/tifm_sd.ko-old &&

then save it and run it.

---

### Post by elatre on 2007-05-28
> **macogw said:**
> You could try putting the modules into the blacklist for suspend (somewhere in /etc/).  You'll have to Google for the proper directory though, sorry.  I don't play with init too much.
After standby there are three modules loaded: tifm_7xx1, tifm_core and mmc_core. So it doesn't work. If I manually load the other three modules (tifm_sd, mmc_block, sdhci) it still doesn't work.

---

### Post by hotshot23t on 2007-05-31
Hi I'm trying to get my card reader to work with no avail.  I have a compaq v2000 running 7.04 32bit.  I ran your script and it did not work.  I am using a MicroSD card put into a SD card adapter if that makes a difference.  On my dmesg, I get the following output, over and over again, maybe 20 times.

[  248.964000] mmcblk0: error 2 transferring data
[  248.964000] end_request: I/O error, dev mmcblk0, sector 0

Thanks for any help.

---

### Post by macogw on 2007-05-31
Updated Feisty's don't need the script now.  The v 0.8 drivers are in 2.6.20-16 which came through some time in the last few days.  2.6.20-15, the kernel from the install disk, needs it, so if you're up to date, the script won't help any and it's either a bug with the driver or some other problem.

---

### Post by ThrobbingBrain66 on 2007-06-25
Macogw-

I added a link to this thread at the top of my Edgy card reader thread.  Thanks for the hard work.

---

### Post by oobe on 2007-06-26
hi, just installed Ubuntu on my friends satellite laptop ...

plugged in his sandisk brand "memory stick Pro duo" , no desktop icon arrived ..

checked dmesg, shows a card being plugged in and out and mentions "tfim0" and "tfim_core" etc ..

I read some cards arent included in the first post of this thread, is this one of them?

---

### Post by ThrobbingBrain66 on 2007-06-26
[quote=oobe]hi, just installed Ubuntu on my friends satellite laptop ...

plugged in his sandisk brand "memory stick Pro duo" , no desktop icon arrived ..

checked dmesg, shows a card being plugged in and out and mentions "tfim0" and "tfim_core" etc ..

I read some cards arent included in the first post of this thread, is this one of them?[/quote]

Only SD and MMC cards are currently supported

---

### Post by vicnov on 2007-07-05
After upgrading from Edgy to Feisty (kernel 2.6.20-16-generic), my TI card reader continues working - I tested with SD cards.

What I have done in Edgy is written in the first post:
[http://ubuntuforums.org/showpost.php?p=2520594&postcount=1](http://ubuntuforums.org/showpost.php?p=2520594&postcount=1)
(that is I have added tifm_7xx1, tifm_core, tifm_sd modules to /etc/modules).

---

### Post by jcrow on 2007-07-11
Your script worked for me with SD cards. I did have to restart after the installation. I am using the default kernel that comes with Fiesty. The newer kernel screws everything up from sound to wireless to XGL. I am running a gateway MX 6448 which has a turion 64X2, an ATI 1150 express and a broadcom wireless adapter. I sure picked a great machine to work with Ubuntu. I had no problems with installing fiesty with beryl on my 5 year old machine. Go figure. 



Just say no to Vista!

---

### Post by fishyf on 2007-07-14
My SD card reader still doesn't work. It seems that if the card is 03.0b.02 (output from lspci) then it won't work.

My card reader won't detect an SD card on insertion (no message in dmesg), but it will detect insertion of an XD card. It looks like the driver is failing to recognise insertion of an SD card.

---

### Post by smiley1962 on 2007-07-22
Here is the result of my lspci, i'm trying to get my sdcard reader to work, but the firmware loading bit that is bothering me, anybody know how to get it to work?

00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[COLOR="Red"]02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)[/COLOR]
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

Smiley:(

---

### Post by raphoun on 2007-07-23
> **smiley1962 said:**
> Here is the result of my lspci, i'm trying to get my sdcard reader to work, but the firmware loading bit that is bothering me, anybody know how to get it to work?

00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[COLOR="Red"]02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)[/COLOR]
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

Smiley:(



Same trouble on a compaq R3000 :(:(

---

### Post by redefender on 2007-08-01
My SD card worked fine in Edgy and I have followed the instructions in this thread and all seems fine, but when I put the SD card in the reader, nothing happens.

"dmesg" says:

> [  111.860000] tifm_core: MMC/SD card detected in socket 0:3


"lsmod|grep sd" says:

> tifm_sd                12808  0 
sdhci                  18700  0 
mmc_core               26756  2 tifm_sd,sdhci
tifm_core              11396  2 tifm_sd,tifm_7xx1
tsdev                   8768  0 
sd_mod                 23428  8 
scsi_mod              142348  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata


Any ideas?

---

### Post by vikram sai balaji on 2007-08-11
> **gamerteck said:**
> This worked worked for me on my HP nc6230.  Kudos!:guitar:

i tried the same thing can you provide more information? i have a HP nc6230

---

### Post by phenest on 2007-10-06
I have a HP TC1100 tablet PC with a TI 1620 PCMCIA and an SD card reader.

lspci output:
```
02:06.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:06.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:06.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```

I have tried your method but to no avail.

---

### Post by thingswelostinthefire on 2007-10-08
> **smiley1962 said:**
> 

[COLOR="Red"]02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)[/COLOR]


I have exactly the same **lspci** (HP Pavillion zv5000 series, zv5362EA the exact model)... and with **Feisty** it's not working... can anyone help us? :)

this is the result of **lsmod | grep tifm**:

tifm_7xx1               8704  0 
tifm_sd                12552  0 
mmc_core               26756  1 tifm_sd
tifm_core              11140  2 tifm_7xx1,tifm_sd

it seems correct to me... Thanks in advance!

---

### Post by kekojeep on 2007-10-10
> **thingswelostinthefire said:**
> I have exactly the same **lspci** (HP Pavillion zv5000 series, zv5362EA the exact model)... and with **Feisty** it's not working... can anyone help us? :)

this is the result of **lsmod | grep tifm**:

tifm_7xx1               8704  0 
tifm_sd                12552  0 
mmc_core               26756  1 tifm_sd
tifm_core              11140  2 tifm_7xx1,tifm_sd

it seems correct to me... Thanks in advance!

Same here.. HP zv5466, TI 1620 card reader..

[ ]'s

---

### Post by phenest on 2007-11-17
> **phenest said:**
> I have a HP TC1100 tablet PC with a TI 1620 PCMCIA and an SD card reader.

lspci output:
```
02:06.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:06.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:06.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```

I have tried your method but to no avail.

I'm using Gutsy now and someone told me the PCMCIA slot works as they have tried it. If the card reader is part of the same chipset, then can I assume there is a driver for it? If so, why doesn't it work? If I have the Windows driver, can I use that somehow?

---

### Post by rreynolds on 2007-11-20
I may have found an answer for the PCI1620 problem [here]("http://gentoo-wiki.com/HARDWARE_Texas_Instruments_PCI1620_Cardbus_Controller_with_a_4_in_1_memory_card_reader") but I'm getting errors when I go to make the driver in fiesty.  Maybe someone with more knowledge of C could fix the code.  Maybe I need to upgrade to get it compiling. I don't really know.

---

### Post by phenest on 2007-11-20
> **rreynolds said:**
> I may have found an answer for the PCI1620 problem [here]("http://gentoo-wiki.com/HARDWARE_Texas_Instruments_PCI1620_Cardbus_Controller_with_a_4_in_1_memory_card_reader") but I'm getting errors when I go to make the driver in fiesty.  Maybe someone with more knowledge of C could fix the code.  Maybe I need to upgrade to get it compiling. I don't really know.

I have looked at this code but also cannot compile it. What errors do you get? I'm an experienced C programmer but have never done anything in Linux to know what to do next. I might be getting different errors to you. Maybe we can put our heads together and see what we can come up with.

---

### Post by rreynolds on 2007-11-20
It seems that the firmware loader compiles correctly but the pata_pci1620 gives:
```
/home/rich/Drivers/TI_PCI1620/modules/pata_pci1620.c:143: error: ‘ata_sff_port_start’ undeclared here (not in a function)
/home/rich/Drivers/TI_PCI1620/modules/pata_pci1620.c: In function ‘pcmcia_init_one’:
/home/rich/Drivers/TI_PCI1620/modules/pata_pci1620.c:305: warning: implicit declaration of function ‘ata_host_alloc’
/home/rich/Drivers/TI_PCI1620/modules/pata_pci1620.c:305: warning: assignment makes pointer from integer without a cast
/home/rich/Drivers/TI_PCI1620/modules/pata_pci1620.c:319: warning: implicit declaration of function ‘ata_host_activate’
make[2]: *** [/home/rich/Drivers/TI_PCI1620/modules/pata_pci1620.o] Error 1
make[1]: *** [_module_/home/rich/Drivers/TI_PCI1620/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```
I looked up the lines in the .c file, but it wasn't obvious to me where the declarations should occur.  This is supposed to be a modified version of the pata_pcmcia.c source.  My next step was to look at the two sources side by side and see how quickly I can learn C.
Are these the errors you're getting?

---

### Post by phenest on 2007-11-21
I'm not getting anywhere as far as you. Any chance you can send me what you got, either on this thread or PM me. Cheers.

---

### Post by rreynolds on 2007-11-21
Here's what I've gotten so far.   This doesn't include the pci1620.bin file that I got from the XP share (key was 0xFF if that helps) .   Hopefully this helps some.  I doubt I'll be working on it again until next week (I'm with family for the holidays).  Thanks.

---

### Post by rreynolds on 2007-11-21
Quick update.  

I figured out the call to ata_sff_port_start is only for kernel 2.6.22; for feisty it needs to be changed to ata_port_start.

I was able to get everything compiled - the pata_pci1620 module still had warnings and wouldn't load.  If I load only the tiumfwl.ko then insert an SD card my system freezes.  So, I guess that's progress- at least something is happening...

---

### Post by 00ber n00b on 2007-11-21
got mine working in gutsy, using the first tuto.  Also be sure that you do not have your SD card locked, :lolflag:

---

### Post by phenest on 2007-11-22
> **00ber n00b said:**
> got mine working in gutsy, using the first tuto.  Also be sure that you do not have your SD card locked, :lolflag:

I'm running Gutsy and my system freezes. How did you do it?

---

### Post by phenest on 2007-11-22
After examining the bin file, I don't think it xor'ed.

---

### Post by phenest on 2007-11-22
Got it! But nothing happens.
```
steve@tc1100:~$ dmesg | tail
[ 1307.752000] pccard: PCMCIA card inserted into slot 1
[ 1307.768000] pcmcia: registering new device pcmcia1.0
[ 1307.864000] scsi4 : pata_pci1620
[ 1307.864000] ata4: PATA max PIO0 cmd 0x00013100 ctl 0x0001310e bmdma 0x00000000 irq 3
[ 1308.116000] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[ 1308.872000] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[ 1308.872000] ata4.00: limiting speed to UDMA7:PIO5
[ 1309.628000] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)

```

---

### Post by cross157 on 2007-11-23
I've try just about everything I've seen in this thread and elsewhere to get my SD card reader working and nothing works.

I've tried the first tutorial in this thread, the setpci hack, and even followed [[COLOR="Red"]this page[/COLOR]]("http://gentoo-wiki.com/HARDWARE_Texas_Instruments_PCI1620_Cardbus_Controller_with_a_4_in_1_memory_card_reader"), like others in this thread.

```
$lspci
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
```

```
$dmesg | tail:
[  163.240391] pccard: PCMCIA card inserted into slot 1
[  163.257095] pcmcia: registering new device pcmcia1.0
[  163.359842] scsi3 : pata_pcmcia
[  163.360338] ata2: PATA max PIO0 cmd 0x0001a100 ctl 0x0001a10e bmdma 0x00000000 irq 3
[  163.623913] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  164.390834] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  164.390851] ata2.00: limiting speed to UDMA7:PIO5
[  165.165734] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x2)
```


I'm new much of a noob to completely understand what's going on here, please help.

---

### Post by rreynolds on 2007-11-24
It's progress.  It's slow frustrating progress, but progress none the less.  What size SD card did you use?  In XP I'm limited to 1GB cards; I assume that there is something about the addressing in cards >1GB that confuses the firmware.

00ber n00b,  Does your output from lspci have:
```
02:06.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:06.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:06.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
```
in it?  If so, please, let us know more about how you got the SD working.

---

### Post by cross157 on 2007-11-25
Could this problem:

```

$dmesg
[  376.913028] pccard: PCMCIA card inserted into slot 1
[  376.913041] cs: memory probe 0xd0200000-0xd02fffff: excluding 0xd0200000-0xd020ffff
[  377.443530] pcmcia: registering new device pcmcia1.0
[  377.607910] scsi2 : pata_pcmcia
[  377.608286] ata1: PATA max PIO0 cmd 0x0001a100 ctl 0x0001a10e bmdma 0x00000000 irq 3
[  377.867169] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  378.630851] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  378.630861] ata1.00: limiting speed to UDMA7:PIO5
[  379.394540] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)

```

be solved by editing the config.opts file in usr/lib/pcmciautils?

```
#
# Local PCMCIA Configuration File
#
#----------------------------------------------------------------------
#
# System resources available for PCMCIA cards
#
# NOTE: these settings have no effect on resources assigned to a
# CardBus bridge device itself; this file only affects resources
# assigned to cards.  Also, interrupt settings here will only affect
# ISA bus interrupts assigned to 16-bit cards.  PCI interrupts
# generally can't be reconfigured.
#
# With the kernel PCMCIA subsystem, these settings also have no effect
# at all on resources used for 32-bit CardBus cards.  Those are set by
# the PCI hotplug subsystem.
#

include port 0x100-0x3af
include port 0x3e0-0x4ff
include port 0x820-0x8ff
include port 0xc00-0xcf7

include memory 0xc0000-0xfffff
include memory 0xa0000000-0xa0ffffff
include memory 0x60000000-0x60ffffff


# These may hurt on FSC.
# include port 0x3c0-0x3d2
# Exclude 0x3d3 as Radeon IGP MCE's if you touch these ports
# include port 0x3d4-0x3df

# High port numbers do not always work...
# include port 0x1000-0x17ff

# Extra port range for IBM Token Ring
include port 0xa00-0xaff
```

I don't know enough about port and memory ranges to figure it out. Anyone know?

---

### Post by giruzz on 2008-01-29
Is there a way to have the reader working with an xD card?

thank you

g.

---

### Post by talishte on 2008-03-10
If you are using Linux Mint with Gutsy Gibbon you just need to install [this]("http://geocities.com/dollzrgr8/tifm_install.tar.gz") software.

And :guitar: play

For me works fine wit the kernel 2.6.22.12

---

### Post by Terralthra on 2008-08-22
I am trying to use the script on the first page on my TC1100, running Ubuntu 8.04. I get the following when I try to run it:

```

terralthra@Case:~/Desktop/tifm_install$ ./install.sh
echo /home/terralthra/Desktop/tifm_install/tifm
/home/terralthra/Desktop/tifm_install/tifm
make -C /lib/modules/2.6.24-19-generic/build M=/home/terralthra/Desktop/tifm_install/tifm
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/terralthra/Desktop/tifm_install/tifm/tifm_7xx1.o
/home/terralthra/Desktop/tifm_install/tifm/tifm_7xx1.c: In function ‘tifm_7xx1_probe’:
/home/terralthra/Desktop/tifm_install/tifm/tifm_7xx1.c:344: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/terralthra/Desktop/tifm_install/tifm/tifm_7xx1.c:344: error: (Each undeclared identifier is reported only once
/home/terralthra/Desktop/tifm_install/tifm/tifm_7xx1.c:344: error: for each function it appears in.)
make[2]: *** [/home/terralthra/Desktop/tifm_install/tifm/tifm_7xx1.o] Error 1
make[1]: *** [_module_/home/terralthra/Desktop/tifm_install/tifm] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2
terralthra@Case:~/Desktop/tifm_install$ 

```

Any ideas?

---

### Post by vkov_tinsky on 2008-09-12
> ```
'[...] tifm/tifm_7xx1.c:344: error: &#8216;SA_SHIRQ&#8217; undeclared [...]
```
That's because this macro has been deprecated in more recent kernel versions. You're best off trying a slightly newer version, as follows.

***** NOTE: Compilation only tested with Ubuntu 8.04 & kernel v2.6.24-21** (might also with with 2.6.24-19)

Get the revision which matches kernel v2.6.24-21 the closest (that's the most up to date Ubuntu 8.04 one):
```
svn co -r157 http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/
```
Download the attached patch into the directory you ran the above command in and then do the following:
```

unzip -d driver ubuntu_2.6.24-21_tifm_ms.patch.zip 
cd driver
patch -p1 < ubuntu_2.6.24-21_tifm_ms.patch
make

```

Assuming you get no errors (with v2.6.24-21 you won't) you can the install the module (like described in this thread)... along the lines of:
```
sudo make install
```

Regards,
VT

PS: Haven't been able to test this since I don't have a TI card reader

---

### Post by macvr on 2008-09-13
> **vkov_tinsky said:**
> That's because this macro has been deprecated in more recent kernel versions. You're best off trying a slightly newer version, as follows.

***** NOTE: Compilation only tested with Ubuntu 8.04 & kernel v2.6.24-21** (might also with with 2.6.24-19)

Get the revision which matches kernel v2.6.24-21 the closest (that's the most up to date Ubuntu 8.04 one):
```
svn co -r157 http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/
```
Download the attached patch into the directory you ran the above command in and then do the following:
```

unzip -d driver ubuntu_2.6.24-21_tifm_ms.patch.zip 
cd driver
patch -p1 < ubuntu_2.6.24-21_tifm_ms.patch
make

```

Assuming you get no errors (with v2.6.24-21 you won't) you can the install the module (like described in this thread)... along the lines of:
```
sudo make install
```

Regards,
VT

PS: Haven't been able to test this since I don't have a TI card reader

ok.. i tired this in v2.6.24-19 and get the following errors
```
echo /home/oo/driver
/home/oo/driver
make -C /lib/modules/2.6.24-19-generic/build M=/home/oo/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /home/oo/driver/built-in.o
  CC [M]  /home/oo/driver/tifm_core.o
  CC [M]  /home/oo/driver/tifm_7xx1.o
  CC [M]  /home/oo/driver/tifm_sd.o
/home/oo/driver/tifm_sd.c: In function &#8216;tifm_sd_probe&#8217;:
/home/oo/driver/tifm_sd.c:972: error: &#8216;MMC_VDD_32_33&#8217; undeclared (first use in this function)
/home/oo/driver/tifm_sd.c:972: error: (Each undeclared identifier is reported only once
/home/oo/driver/tifm_sd.c:972: error: for each function it appears in.)
/home/oo/driver/tifm_sd.c:972: error: &#8216;MMC_VDD_33_34&#8217; undeclared (first use in this function)
/home/oo/driver/tifm_sd.c:982: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:983: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:985: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_size&#8217;
/home/oo/driver/tifm_sd.c:986: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:986: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_size&#8217;
/home/oo/driver/tifm_sd.c:987: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_req_size&#8217;
make[2]: *** [/home/oo/driver/tifm_sd.o] Error 1
make[1]: *** [_module_/home/oo/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

```

will try again after updating to 2.6.24-21

[COLOR="Red"]how safe is 2.6.24-21? i'm a noob so dont want to try experimental headers:([/COLOR]

---

### Post by Terralthra on 2008-09-13
I got it to build under 2.6.24-19, but when I build the firmware loader from the gentoo-wiki walkthrough, once I insmod it, dmesg | grep tiumfw shows this:

```

[51253.795256] tiumfwl.c: v1.10 (June 7, 2006) Texas Instruments UltraMedia firmware loader
[51253.795303] PCI: Unable to reserve I/O region #1:40@4000 for device 0000:02:06.2
[51253.795310] tiumfwl: Cannot obtain PCI resources, aborting.
[51253.795327] tiumfwl: probe of 0000:02:06.2 failed with error -16

```

Ideas?

---

### Post by vkov_tinsky on 2008-09-13
> **Terralthra said:**
> ```
[51253.795256]**[COLOR="Red"]tiumfwl[/COLOR]**.c: v1.10 (June 7, 2006) Texas Instruments UltraMedia firmware loader
```
That looks like a different driver: The compiled one should show up starting with **tifm**. Not quite sure why you're looking for tiumfwl (is that TI's own?). What's this walkthrough you're talking about?

[quote="macvr"]how safe is 2.6.24-21? [...] dont want to try experimental headers[/quote] It's stable. Don't obviously just install the headers. I'm not sure but if you've got "Proposed updates" ticked under "Software Sources"->Updates then the newer kernel should be available in the "Updage Manager". 2.6.24-21 should be the latest available version for the *linux-generic* and *linux-headers-generic packages*. Have you not updated your kernel because you've got more custom compiled modules? Why don't you simply run *sudo apt-get install upgrade* ?

Regards,
VT

---

### Post by Terralthra on 2008-09-13
> **vkov_tinsky said:**
> That looks like a different driver: The compiled one should show up starting with **tifm**. Not quite sure why you're looking for tiumfwl (is that TI's own?). What's this walkthrough you're talking about?

The walkthrough I'm referencing is [here](http://gentoo-wiki.com/Texas_Instruments_PCI1620_Cardbus_Controller_with_memory_card_reader).

tiumfwl is the manually created module to load the TI 1620's firmware into the reader so it can be used.

"dmesg | grep tifm" returns nothing.

---

### Post by vkov_tinsky on 2008-09-13
[quote="Terralthra"]```
[51253.795310] tiumfwl: Cannot obtain PCI resources, aborting.
```[/quote]
Is it maybe because you loaded the tifm modules before the firmware loading one? If that's the case rmmod these first: tifm_core.ko tifm_7xx1.ko and tifm_sd.ko, then load tiumfwl followed by make install for tifm).

If not I don't know, sorry.

Regards,
VT

---

### Post by vkov_tinsky on 2008-09-13
> **macvr said:**
> ```
[...]
/home/oo/driver/tifm_sd.c: In function &#8216;tifm_sd_probe&#8217;:
/home/oo/driver/tifm_sd.c:972: error: &#8216;MMC_VDD_32_33&#8217; undeclared (first use in this function)
[...]

```


Ok, figured it out. The reason it can't find the defines is because you've used macogw's tifm installer (which replaces some headers with older ones, as far as I can tell). Run the uninstall.sh script (as sudo of course) from macogw's files, that should return the headers back to what they were before. After that my instructions should work fine even for kernel v2.6.24-19, no need to upgrade after all.

Regards,
VT

---

### Post by macvr on 2008-09-14
> **vkov_tinsky said:**
> Ok, figured it out. The reason it can't find the defines is because you've used macogw's tifm installer (which replaces some headers with older ones, as far as I can tell). Run the uninstall.sh script (as sudo of course) from macogw's files, that should return the headers back to what they were before. After that my instructions should work fine even for kernel v2.6.24-19, no need to upgrade after all.

Regards,
VT
i tried to repeat after removing  macogw's files[doubly removed using GUI and also terminal]... 

but get the same exact error i got previously...
> $ make
echo /home/oo/driver
/home/oo/driver
make -C /lib/modules/2.6.24-19-generic/build M=/home/oo/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /home/oo/driver/built-in.o
  CC [M]  /home/oo/driver/tifm_core.o
  CC [M]  /home/oo/driver/tifm_7xx1.o
  CC [M]  /home/oo/driver/tifm_sd.o
/home/oo/driver/tifm_sd.c: In function &#8216;tifm_sd_probe&#8217;:
/home/oo/driver/tifm_sd.c:972: error: &#8216;MMC_VDD_32_33&#8217; undeclared (first use in this function)
/home/oo/driver/tifm_sd.c:972: error: (Each undeclared identifier is reported only once
/home/oo/driver/tifm_sd.c:972: error: for each function it appears in.)
/home/oo/driver/tifm_sd.c:972: error: &#8216;MMC_VDD_33_34&#8217; undeclared (first use in this function)
/home/oo/driver/tifm_sd.c:982: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:983: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:985: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_size&#8217;
/home/oo/driver/tifm_sd.c:986: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:986: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_size&#8217;
/home/oo/driver/tifm_sd.c:987: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_req_size&#8217;
make[2]: *** [/home/oo/driver/tifm_sd.o] Error 1
make[1]: *** [_module_/home/oo/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2


i think the main error might be corrected if i correct this>
```
~$ dmesg | grep tifm
[COLOR="Red"][18617.825108] tifm_sd: Unknown symbol tifm_eject
[18617.825206] tifm_sd: Unknown symbol tifm_register_driver
[18617.825519] tifm_sd: Unknown symbol tifm_unmap_sg
[18617.825616] tifm_sd: Unknown symbol tifm_map_sg
[18617.825721] tifm_sd: Unknown symbol tifm_unregister_driver[/COLOR]

```
previously <~$ dmesg | grep tifm> used to return no result...
i think that removing the above and starting from first again might correct the errors

so i tired>
```
[COLOR="Silver"]~$ sudo rmmod tifm_7xx1; sudo rmmod tifm_core; sudo rmmod tifm_sd[/COLOR]
ERROR: Module tifm_7xx1 does not exist in /proc/modules
ERROR: Module tifm_core does not exist in /proc/modules
ERROR: Module tifm_sd does not exist in /proc/modules

```

any ideas?

---

### Post by vkov_tinsky on 2008-09-14
[quote="macvr"]i tried to repeat after removing macogw's files[/quote] No, that's not enough because his installation script also put some files in /usr/src/linux-headers-2.6.24-19-generic (your kernel source dir). Did you run the uninstall.sh script from his file first? If yes, and you still get these particular compile errors re-install the kernel headers like so:
```
sudo apt-get --reinstall install linux-headers-`uname -r`
```Then it should definitely compile.

[quote="macvr"]i think the main error might be corrected if i correct this[/quote] No, you first need to get the module to compile properly before it can be loaded. Then you can do *make install*.

Regards,
VT

---

### Post by macvr on 2008-09-14
> **vkov_tinsky said:**
> No, that's not enough because his installation script also put some files in /usr/src/linux-headers-2.6.24-19-generic (your kernel source dir). Did you run the uninstall.sh script from his file first? If yes, and you still get these particular compile errors re-install the kernel headers like so:
```
sudo apt-get --reinstall install linux-headers-`uname -r`
```Then it should definitely compile.

 No, you first need to get the module to compile properly before it can be loaded. Then you can do *make install*.

Regards,
VT
s,i had removed her files by running uninstall.sh [as root both from GUI& terminal]
so i reinstalled the linux headers 
and now dmesg has changed to:
```
[COLOR="DimGray"]~$ dmesg | grep tifm[/COLOR]
[   31.107951] tifm_sd: Unknown symbol tifm_eject
[   31.108005] tifm_sd: Unknown symbol tifm_register_driver
[   31.108204] tifm_sd: Unknown symbol tifm_unmap_sg
[   31.108259] tifm_sd: Unknown symbol tifm_map_sg
[   31.108318] tifm_sd: Unknown symbol tifm_unregister_driver

```
but still get the same error as before while compiling
```
[COLOR="DimGray"]~/driver$ make[/COLOR]
echo /home/oo/driver
/home/oo/driver
make -C /lib/modules/2.6.24-19-generic/build M=/home/oo/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /home/oo/driver/built-in.o
  CC [M]  /home/oo/driver/tifm_core.o
  CC [M]  /home/oo/driver/tifm_7xx1.o
  CC [M]  /home/oo/driver/tifm_sd.o
/home/oo/driver/tifm_sd.c: In function &#8216;tifm_sd_probe&#8217;:
/home/oo/driver/tifm_sd.c:972: error: &#8216;MMC_VDD_32_33&#8217; undeclared (first use in this function)
/home/oo/driver/tifm_sd.c:972: error: (Each undeclared identifier is reported only once
/home/oo/driver/tifm_sd.c:972: error: for each function it appears in.)
/home/oo/driver/tifm_sd.c:972: error: &#8216;MMC_VDD_33_34&#8217; undeclared (first use in this function)
/home/oo/driver/tifm_sd.c:982: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:983: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:985: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_size&#8217;
/home/oo/driver/tifm_sd.c:986: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_count&#8217;
/home/oo/driver/tifm_sd.c:986: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_blk_size&#8217;
/home/oo/driver/tifm_sd.c:987: error: &#8216;struct mmc_host&#8217; has no member named &#8216;max_req_size&#8217;
make[2]: *** [/home/oo/driver/tifm_sd.o] Error 1
make[1]: *** [_module_/home/oo/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

```

---

### Post by vkov_tinsky on 2008-09-15
[quote="macvr"]```
/home/oo/driver/tifm_sd.c:972: error: &#8216;MMC_VDD_32_33&#8217; undeclared
```[/quote]

All these errors point to defines which should all be specified in the following file: /usr/src/linux-headers-2.6.24-19/include/linux/mmc/host.h
Does it contain a line starting with *#define MMC_VDD_32_33*? If not you've **still** got the old version (which was put there by macogw's script). You can try this, but I assume it won't work since you say you already ran uninstall.sh:
```
sudo cp /usr/src/linux-headers-`uname -r`/include/linux/mmc/host.h.old /usr/src/linux-headers-`uname -r`/include/linux/mmc/host.h
```
If it doesn't work put the attached (original) host.h in /usr/src/linux-headers-2.6.24-19/include/linux/mmc/

Regards,
VT

---

### Post by macvr on 2008-09-15
> **vkov_tinsky said:**
> All these errors point to defines which should all be specified in the following file: /usr/src/linux-headers-2.6.24-19/include/linux/mmc/host.h
Does it contain a line starting with *#define MMC_VDD_32_33*? If not you've **still** got the old version (which was put there by macogw's script). You can try this, but I assume it won't work since you say you already ran uninstall.sh:
```
sudo cp /usr/src/linux-headers-`uname -r`/include/linux/mmc/host.h.old /usr/src/linux-headers-`uname -r`/include/linux/mmc/host.h
```
If it doesn't work put the attached (original) host.h in /usr/src/linux-headers-2.6.24-19/include/linux/mmc/

Regards,
VT
my host.h doesnt have the lines u mentioned, nor did the command work[dont have a host.h.old file!]

so i backed up mine n replaced the original host.h file u had attached...

ran the procedure u have given in this post>[http://ubuntuforums.org/showpost.php?p=5778068&postcount=70]("http://ubuntuforums.org/showpost.php?p=5778068&postcount=70")

this is the output, there are a lot of warnings...```

[COLOR="SlateGray"]~/driver$ make[/COLOR]
echo /home/oo/driver
/home/oo/driver
make -C /lib/modules/2.6.24-19-generic/build M=/home/oo/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /home/oo/driver/built-in.o
  CC [M]  /home/oo/driver/tifm_core.o
  CC [M]  /home/oo/driver/tifm_7xx1.o
  CC [M]  /home/oo/driver/tifm_sd.o
  CC [M]  /home/oo/driver/memstick.o
  CC [M]  /home/oo/driver/mspro_block.o
  CC [M]  /home/oo/driver/tifm_ms.o
/home/oo/driver/tifm_ms.c: In function &#8216;tifm_ms_transfer_data&#8217;:
/home/oo/driver/tifm_ms.c:184: warning: &#8216;p_off&#8217; may be used uninitialized in this function
  CC [M]  /home/oo/driver/jmb38x_ms.o
/home/oo/driver/jmb38x_ms.c: In function &#8216;jmb38x_ms_transfer_data&#8217;:
/home/oo/driver/jmb38x_ms.c:295: warning: &#8216;p_off&#8217; may be used uninitialized in this function
  CC [M]  /home/oo/driver/xd_card_blk.o
/home/oo/driver/xd_card_blk.c: In function &#8216;xd_card_process_request&#8217;:
/home/oo/driver/xd_card_blk.c:1862: warning: format &#8216;%lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;sector_t&#8217;
/home/oo/driver/xd_card_blk.c:1869: warning: format &#8216;%lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;sector_t&#8217;
  CC [M]  /home/oo/driver/xd_card_ecc.o
  LD [M]  /home/oo/driver/xd_card.o
  CC [M]  /home/oo/driver/jmb38x_xd.o
/home/oo/driver/jmb38x_xd.c: In function &#8216;jmb38x_xd_issue_cmd&#8217;:
/home/oo/driver/jmb38x_xd.c:161: warning: format &#8216;%llx&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 4 has type &#8216;dma_addr_t&#8217;
/home/oo/driver/jmb38x_xd.c: In function &#8216;jmb38x_xd_isr&#8217;:
/home/oo/driver/jmb38x_xd.c:353: warning: format &#8216;%llx&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 4 has type &#8216;dma_addr_t&#8217;
  CC [M]  /home/oo/driver/flash_bd.o
  Building modules, stage 2.
  MODPOST 10 modules
  CC      /home/oo/driver/flash_bd.mod.o
  LD [M]  /home/oo/driver/flash_bd.ko
  CC      /home/oo/driver/jmb38x_ms.mod.o
  LD [M]  /home/oo/driver/jmb38x_ms.ko
  CC      /home/oo/driver/jmb38x_xd.mod.o
  LD [M]  /home/oo/driver/jmb38x_xd.ko
  CC      /home/oo/driver/memstick.mod.o
  LD [M]  /home/oo/driver/memstick.ko
  CC      /home/oo/driver/mspro_block.mod.o
  LD [M]  /home/oo/driver/mspro_block.ko
  CC      /home/oo/driver/tifm_7xx1.mod.o
  LD [M]  /home/oo/driver/tifm_7xx1.ko
  CC      /home/oo/driver/tifm_core.mod.o
  LD [M]  /home/oo/driver/tifm_core.ko
  CC      /home/oo/driver/tifm_ms.mod.o
  LD [M]  /home/oo/driver/tifm_ms.ko
  CC      /home/oo/driver/tifm_sd.mod.o
  LD [M]  /home/oo/driver/tifm_sd.ko
  CC      /home/oo/driver/xd_card.mod.o
  LD [M]  /home/oo/driver/xd_card.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

```

```
[COLOR="SlateGray"]~/driver$ sudo make install[/COLOR]
mkdir -p /lib/modules/2.6.24-19-generic
rm -f /lib/modules/2.6.24-19-generic/kernel/drivers/misc/tifm_core.ko
rm -f /lib/modules/2.6.24-19-generic/kernel/drivers/misc/tifm_7xx1.ko
rm -f /lib/modules/2.6.24-19-generic/kernel/drivers/mmc/tifm_sd.ko
install -c -m 644 tifm_core.ko tifm_7xx1.ko /lib/modules/2.6.24-19-generic/kernel/drivers/misc/
install -c -m 644 tifm_sd.ko /lib/modules/2.6.24-19-generic/kernel/drivers/mmc/
/sbin/depmod -ae

```
has it installed properly?

 [COLOR="SlateGray"]~$ dmesg | grep tifm[/COLOR] 
[COLOR="Red"]now gives NO OUTPUT[/COLOR]? nor is my device recognized by virtualBox

---

### Post by vkov_tinsky on 2008-09-15
No errors (only warnings, which I get too of course) means it compiled and installed fine.

[quote="macvr"]now gives NO OUTPUT?[/quote]
The output you got previously got, e.g.```
[   31.107951] tifm_sd: Unknown symbol tifm_eject
[...]
``` indicated the module couldn't be loaded, i.e. all the output from *dmesg | grep tifm* that you've shown up to now only highlighted it wasn't working.

I assume after a reboot *dmesg | grep tifm* might show some output (when the module is loaded). Do *tail -f /var/log/messages* in a terminal (this will show you the last lines of the kernel log and update it with new entries when they're added) and then plug in e.g. an SD card (i.e. type of media which this driver is known to support). You should see output in the terminal window indicating whether the driver is working or not.

[quote="macvr"]nor is my device recognized by virtualBox[/quote]
The only devices VirtualBox can "forward" straight to the guest operating system are USB, parallel/serial ports, CD drive and disk partitions, i.e. VirtualBox won't help you in this case. So if the tifm driver still doesn't to xD then you'll have to wait (as I said in the VirtualBox forums).


*** **Update** ***

I was blind. See the list of modules built in your *make* output:
```

  LD [M]  /home/oo/driver/flash_bd.ko
  LD [M]  /home/oo/driver/jmb38x_ms.ko
  LD [M]  /home/oo/driver/jmb38x_xd.ko
  LD [M]  /home/oo/driver/memstick.ko
  LD [M]  /home/oo/driver/mspro_block.ko
  LD [M]  /home/oo/driver/tifm_7xx1.ko
  LD [M]  /home/oo/driver/tifm_core.ko
  LD [M]  /home/oo/driver/tifm_ms.ko
  LD [M]  /home/oo/driver/tifm_sd.ko
  LD [M]  /home/oo/driver/xd_card.ko
```

But it only installs three of them (so only SD card support by default) since the other ones are still in the alpha/beta stages:
```

install -c -m 644 **tifm_core.ko tifm_7xx1.ko** /lib/modules/2.6.24-19-generic/kernel/drivers/misc/
install -c -m 644 **tifm_sd.ko** /lib/modules/2.6.24-19-generic/kernel/drivers/mmc/
```

If you already got it to recognise an SD card fine you could try to install the xd related modules manually (and reboot). 
```
sudo install -c -m 644 **xd_card.ko** **jmb38x_xd.ko** /lib/modules/`uname -r`-generic/kernel/drivers/mmc/
``` As it says on the tifm driver website don't try it with an xD the contents of which you haven't backed up.

If it doesn't work you'll be able to try out the very latest version of the driver with Ubuntu 8.10 (since there won't be kernel incompatibilities forcing you to use an older version as far as I can see).

Regards,
VT

---

### Post by macvr on 2008-09-16
> **vkov_tinsky said:**
> 
If you already got it to recognise an SD card fine you could try to install the xd related modules manually (and reboot). 
```
sudo install -c -m 644 **xd_card.ko** **jmb38x_xd.ko** /lib/modules/`uname -r`-generic/kernel/drivers/mmc/
``` As it says on the tifm driver website don't try it with an xD the contents of which you haven't backed up.

If it doesn't work you'll be able to try out the very latest version of the driver with Ubuntu 8.10 (since there won't be kernel incompatibilities forcing you to use an older version as far as I can see).

Regards,
VT
i dont have an sd card to test the sd driver
i'v installed the xD driver...

```
:~$ dmesg | grep tifm
[ 1608.933291] tifm_7xx1 0000:0a:09.2: checking media set 1
[ 1608.945642] tifm_core: SmartMedia/xD card detected in socket 0:0
[ 1643.707732] tifm_7xx1 0000:0a:09.2: checking media set 1
[ 1643.707742] tifm0 : demand removing card from socket 0:0
[ 1645.909033] tifm_7xx1 0000:0a:09.2: checking media set 1
[ 1645.914474] tifm_core: SmartMedia/xD card detected in socket 0:0
[ 1653.449710] tifm_7xx1 0000:0a:09.2: checking media set 1
[ 1653.449720] tifm0 : demand removing card from socket 0:0

```
tail -f /var/log/messages
```
Sep 16 13:00:30 UBUNTU-laptop kernel: [ 1608.945642] tifm_core: SmartMedia/xD card detected in socket 0:0
Sep 16 13:02:42 UBUNTU-laptop kernel: [ 1643.707742] tifm0 : demand removing card from socket 0:0
Sep 16 13:02:52 UBUNTU-laptop kernel: [ 1645.914474] tifm_core: SmartMedia/xD card detected in socket 0:0

```

so i guess it is detecting the card!!!... 

so how do i access it? any ideas? :(

did i miss something?/am i supposed to mount it?/was i supposed to have run sudo modprobe?

or how could i make it accessible in virtualBox[serial port?]

---

### Post by vkov_tinsky on 2008-09-16
From the logs it looks like it's all installed properly.

[quote="macvr"]
tail -f /var/log/messages
```
sep 16 13:00:30 ubuntu-laptop kernel: [ 1608.945642] tifm_core: Smartmedia/xd card detected in socket 0:0
```
[/quote]
Is that all it says in /var/log/messages? I mean, does it not indicate where it's attached the card to (e.g. something like /dev/sd*)?

If not indicates that the author of **tifm** has not finished implementing the xD driver part (as he states on [_the website_](http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver): "*[...] The development of xD card support is pending.*"). In the most recent version of the driver available (via SVN) there seem to have been quite a few changes made to the xD parts but you can't try it just like that because it won't compile with the latest Ubuntu 8.04 (Hardy) kernel. It will though with Ubuntu 8.10, as I already said (which is only a month or so away). In fact the version of tifm which comes with 8.10 might be recent enough to support xD.

If you really really don't want to wait that long you can manually try to compile a 2.6.25 or later kernel, but I can't help you with that. If you search in these forums you'll find plenty of information on this like [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835) and [http://ubuntuforums.org/showthread.php?t=43065](http://ubuntuforums.org/showthread.php?t=43065). I advise you to wait until the release of 8.10 though.

Regards,
VT

---

### Post by macvr on 2008-09-16
> **vkov_tinsky said:**
> From the logs it looks like it's all installed properly.



[COLOR="Blue"]hei, THANK u so much for taking time in trying to help resolve this issue...[/COLOR]

well i was trying desperately to see if the **_card slot_** was detected , it might be used in VirtualBox atleast... so that i could delete my XP[:mad:] partition FOREVER...[guess i have to keep the stupid XP for some more time!:mad:]

if i really get more pissed off with XP i might give a shot at the headers:)

i have [COLOR="Red"]a few final doubts...[/COLOR]

1-is the folder /home/oo/driver/ and its contents just a temporary folder created for the driver installation? if so, could i delete it?

2-do i need to remove the ms_patch[_by the way,where did u get if from?_i'm not able to google it]

3-do i need to remove the driver files which were installed now,if i'm to install the new headers?[if so, how?]

---

### Post by vkov_tinsky on 2008-09-17
> **macvr said:**
> 
1-is the folder /home/oo/driver/ and its contents just a temporary folder created for the driver installation? if so, could i delete it?
Yep, you can delete all that.

> **macvr said:**
> 
2-do i need to remove the ms_patch[_by the way,where did u get if from?_i'm not able to google it
I made it myself, i.e. I figured out why it (the version newer than 0.8 which comes with Ubutnu 8.04) wasn't compiling on kernel v.2.6.24-* so I thought I'd share what I found.

> **macvr said:**
> 
3-do i need to remove the driver files which were installed now
Simply delete the modules which were installed, i.e **tifm_core.ko** and **tifm_7xx1.ko** from */lib/modules/2.6.24-19-generic/kernel/drivers/misc/* and **tifm_sd.ko**, **xd_card.ko** and **jmb38x_xd.ko** from /lib/modules/2.6.24-19-generic/kernel/drivers/mmc/

> **macvr said:**
> 
[...] ,if i'm to install the new headers? if so, how?
You do realise that kernel headers are for a specific kernel version, so if you're planning to try v2.6.25.* or something you'll need both the kernel and the headers.

Regards,
VT

---

### Post by macvr on 2008-09-17
> **vkov_tinsky said:**
> 
I made it myself, i.e. I figured out why it (the version newer than 0.8 which comes with Ubutnu 8.04) wasn't compiling on kernel v.2.6.24-* so I thought I'd share what I found.
pretty cool...[i know ur patch is for the older kernel,but if u send it to the author , _it might_ help him with his work]
> **vkov_tinsky said:**
> You do realise that kernel headers are for a specific kernel version, so if you're planning to try v2.6.25.* or something you'll need both the kernel and the headers.

i was talking about removing the drivers, which u have explained[asking how? to remove the drivers if i needed to install the new kernels, not for installing the headers]...

i'm a noob though... will take a look at the guides u have linked if 8.10 doesnt recognize the card...

thanx for the help..

---

### Post by vkov_tinsky on 2008-09-17
> **macvr said:**
> [i know ur patch is for the older kernel,but if u send it to the author , _it might_ help him with his work]

The reason the newer version didn't work with the older kernel (of Ubuntu 8.04) is because the author of tifm had moved to developing on the newest available kernel. So this is a "fix" to allow the newer code to run on an older kernel (same reason why this whole thread was started in the first place)

> **macvr said:**
> will take a look at the guides u have linked if 8.10 doesnt recognize the card...
You might want to contact the author of tifm and ask what state xD support is actually in? (After all there won't be any point in trying it if he says - I'm still working on it - give me approximately 3 months).

Regards,
VT

---

### Post by ccl4 on 2008-09-21
i have 8.04 and my card reader does not work, please help
**lspci -v**
> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: dc700000-dc7fffff
	Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dc800000-dcffffff
	Prefetchable memory behind bridge: 00000000be000000-00000000bfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: dd000000-dfefffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at dc6be000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at dc6bfc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at c800 [size=8]
	I/O ports at c480 [size=4]
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=16]
	Memory at dc6bd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
	Memory behind bridge: dff00000-dfffffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1339
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at dc6b8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1385
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at dc6bc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at bc00 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Atheros Communications Inc. AR5006EG 802.11bg NIC (2.4GHz, PCI Express)
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at dc7f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1322
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at dd000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at dfee0000 [disabled] [size=128K]
	Capabilities: <access denied>

05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at dfffe800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: medium devsel, IRQ 17
	Memory at dffff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

05:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: medium devsel, IRQ 10
	Memory at dffff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

05:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: medium devsel, IRQ 10
	Memory at dffffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>



**lusb**
> Bus 002 Device 004: ID 046d:c045 Logitech, Inc. 
Bus 002 Device 005: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 05e1:0501 Syntek Semiconductor Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

---

### Post by macvr on 2008-09-21
> **ccl4 said:**
> i have 8.04 and my card reader does not work, please help

what do u mean exactly?
doesnt it work for all cards/ what card are u trying to use?

---

### Post by ccl4 on 2008-09-21
i have 4 in 1 built in card reader, it recognizes nothing at all.

---

### Post by vbhide on 2008-09-23
Compaq Presario V2000

Just had to reboot and it worked.

I love you.

---

### Post by benste on 2008-12-02
For those who want to use the MS and MS Duo too,
please subscribe to the following bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285039]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285039")

---

### Post by macvr on 2008-12-02
Any info on the xD card support?

---

### Post by acreech on 2008-12-03
> **macvr said:**
> Any info on the xD card support?

Bump

I am trying to figure out how to get my card reader to recognize xD too. It recognizes  SD out of the box. 

I am using Intrepid on an Acer Aspire 7520-5185 laptop

---

### Post by acreech on 2008-12-03
There is a bug report on this at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490")

---

### Post by macvr on 2008-12-03
> **acreech said:**
> There is a bug report on this at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490")

that bug is for the Ricoh Co Ltd card reader , not the texas instruments card reader...

maybe the solution could be the same???

---

### Post by acreech on 2008-12-03
> **macvr said:**
> that bug is for the Ricoh Co Ltd card reader , not the texas instruments card reader...

maybe the solution could be the same???

Sorry about that. I did not mean to post on the TI thread. I think the answer is the same. As I have been googling the problem it appears that xD does not have any support in Liunx. It seems that SD works and xD only works with a USB Card reader.

---

### Post by Skumpic on 2008-12-14
Hi anyone was able to compile this source on ubuntu intrepid ?? (kernel 2.6.27)

I'm interested in the beta moudules for xd cards (jmb38x_xd and xd_card)

Thanks in advance

---

