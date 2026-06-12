---
title: "32 bit, 64 bit, etc."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Roasted on 2008-07-08
I'm told that nobody officially supports 64 bit drivers and whatnot for Ubuntu. My question is, eventually, won't they have to? Isn't it true that 32 bit processors only recognize like 3.3gb of RAM, so eventually everybody will be making the switch to 64 bit platforms... will 32 bit drivers work for 64 bit, or will 64 bit specific drivers start to surface?

---

### Post by tamoneya on 2008-07-08
you are right: the end of 32 bit is very soon approaching.  Some drivers do exist for 64 bit systems.  A good example is graphics cards.  They have a lot of 64 bit drivers for graphics cards.

---

### Post by tjwoosta on 2008-07-08
i have 64bit Ubuntu and have yet to run into any issues whatsoever

i have two 64 bit machines (everything went without issues)

rtl8187b wireless and rtl8185 wireless  (both with native linux drivers)

intel GM956  and ati radion (both work fine, although i cheated on the intel and copied my xorg.conf from a previous gutsy install, but that issue is with both 32bit and 64bit)

synaptics touchpad (works perfectly after installing the driver from synaptic package manager)

i hear of people saying that flash and java dont work, but mine have both worked perfectly since i installed them

the only thing that i dont like about 64bit is that i cant get mupen64 to work (so far its for 32bit only)

---

### Post by Sef on 2008-07-08
> I'm told that nobody officially supports 64 bit drivers and whatnot for Ubuntu. My question is, eventually, won't they have to? Isn't it true that 32 bit processors only recognize like 3.3gb of RAM, so eventually everybody will be making the switch to 64 bit platforms... will 32 bit drivers work for 64 bit, or will 64 bit specific drivers start to surface?

The only two major apps without 64-bit are flash, which can be installed easily with Kliz's Script, and java, which is being resolved.  For more information on both, read those [stickies in the 64-bit forum]("http://ubuntuforums.org/forumdisplay.php?f=343").

---

### Post by bodhi.zazen on 2008-07-08
> **Roasted said:**
> Isn't it true that 32 bit processors only recognize like 3.3gb of RAM

No that is NOT TRUE. People keep spreading that mis-information. It depends on your motherboard.

> For **32-bit systems[b] the Server Edition is configured to use [b]PAE which allows addressing up to 64GB of memory** while the Desktop Edition is configured for 4GB.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

You can either run the server kernel on your desktop installation or re-compile your kernel with PAE support.

---

### Post by Roasted on 2008-07-08
But, nonetheless, the same holds true that 64 bit platforms (both hardware and all software) are in the future, despite how much they can stretch out 32 bit platforms with this additional support. Am I right on that one at least?

---

### Post by sawjew on 2008-07-08
I have been using 64 bit ubuntu for about 2 years now and have had no issues whatsover.  The only hardware I have had any issue with is my internal dial-up modem and since I went to broadband I haven't worried about it.  Dial-up modem support is patchy in linux generally but is even more so for 64 bit systems.  

Apart from this everything that is available for 32 bit is available for 64 bit. 

Flash has been in the repositories for the last two releases of ubuntu and will give you the option of installing automatically the first time you go to a flash enabled web site.

As of Hardy, the latest release there is a 64 bit java plugin available also.

In short, I don't know why anyone stays with 32 bit as basically everything available for 32 bit is available for 64 bit also.  For the rare applications which are only available in 32 bit versions you can run 32 bit apps on 64 bit ubuntu, just install the ia32 libs.

If you need any help on 64 bit ubuntu just go the 64 bit forums and there are plenty of willing people to help out.

Have fun with a great 64 bit OS.

---

### Post by bodhi.zazen on 2008-07-08
> **Roasted said:**
> But, nonetheless, the same holds true that 64 bit platforms (both hardware and all software) are in the future, despite how much they can stretch out 32 bit platforms with this additional support. Am I right on that one at least?

The future is mulitcore 64 bit and beyond.

Xeon dual quad core = 8 cpu

very fast, check out the xeon kernel

---

### Post by k3lt01 on 2008-07-08
> **sawjew said:**
> 
In short, I don't know why anyone stays with 32 bit as basically everything available for 32 bit is available for 64 bit also.  For the rare applications which are only available in 32 bit versions you can run 32 bit apps on 64 bit ubuntu, just install the ia32 libs.For the simple fact that running a 64 bit OS on old architectures that are not 64 bit is not going to achieve anything, if indeed it would even install.

---

### Post by wg5o on 2008-08-08
> **tjwoosta said:**
> i have 64bit Ubuntu and have yet to run into any issues whatsoever

i have two 64 bit machines (everything went without issues)

rtl8187b wireless and rtl8185 wireless  (both with native linux drivers)

intel GM956  and ati radion (both work fine, although i cheated on the intel and copied my xorg.conf from a previous gutsy install, but that issue is with both 32bit and 64bit)

synaptics touchpad (works perfectly after installing the driver from synaptic package manager)

i hear of people saying that flash and java dont work, but mine have both worked perfectly since i installed them

the only thing that i dont like about 64bit is that i cant get mupen64 to work (so far its for 32bit only)

The part about wireless hit a nerve.  I have been trying all summer to get wireless working on 64-bit 8.04.  I have two PCI cards, in both cases, ndiswrapper refused to load a 32-bit driver on a 64-bit OS.  I found a 64 bit driver for the currently installed card, but it hangs up at "sudo modprobe ndiswrapper." See my post, about two weeks ago in the Wireless form (8.04 Encore ENLWI-G2 WiFi Adapter 64 Bit Driver).

The other card has the rtl8185 chip set.  I tried to compile the "native driver" and got a directory, "rtl8185_linux_26.1010.0531.2006," but have no idea of what to do next.  If I can make that work, I'll happily reinstall the card.

Any help will be appreciated.

---

### Post by tjwoosta on 2008-08-08
> 
The part about wireless hit a nerve. I have been trying all summer to get wireless working on 64-bit 8.04. I have two PCI cards, in both cases, ndiswrapper refused to load a 32-bit driver on a 64-bit OS. I found a 64 bit driver for the currently installed card, but it hangs up at "sudo modprobe ndiswrapper." See my post, about two weeks ago in the Wireless form (8.04 Encore ENLWI-G2 WiFi Adapter 64 Bit Driver).

The other card has the rtl8185 chip set. I tried to compile the "native driver" and got a directory, "rtl8185_linux_26.1010.0531.2006," but have no idea of what to do next. If I can make that work, I'll happily reinstall the card.

Any help will be appreciated.

this was my origial "need help" thread for the rtl-8185 (it is solved and the link to the working driver for 64bit is in the very last post )
[http://ubuntuforums.org/showthread.php?t=846249&highlight=rtl8185&page=3]("http://ubuntuforums.org/showthread.php?t=846249&highlight=rtl8185&page=3")

this was my "need help" thread for the rtl-8187b (also solved and the working driver for 64bit is the one from pjasons mentioned on the first two pages)
[http://ubuntuforums.org/showthread.php?t=765671]("http://ubuntuforums.org/showthread.php?t=765671")

---

### Post by rcharles84 on 2008-10-07
I have a problem don't
root@chafarleston-desktop:~# sudo ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 
root@chafarleston-desktop:~# dmesg | grep ndiswrapper
[   39.874486] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.943303] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   39.943313] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   39.943326] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   39.943336] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   39.943341] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   39.943347] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   39.943367] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   39.943373] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   39.943379] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   39.943385] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   39.943391] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   39.943396] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   39.943402] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   39.943408] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   39.943413] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   39.943419] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   39.943448] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   39.943458] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   39.943476] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   39.943481] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   39.943487] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   39.943492] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   39.943498] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   39.943504] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   39.943509] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   39.943515] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   39.943521] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   39.943526] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   39.943532] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   39.943538] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   39.943543] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   39.943549] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   39.943555] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   39.943561] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   39.943566] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8185'
[   39.944021] ndiswrapper (load_wrap_driver:112): couldn't load driver net8185; check system log for messages from 'loadndisdriver'
[   39.944082] usbcore: registered new interface driver ndiswrapper
root@chafarleston-desktop:~# 

how I do Please helpme couldn't load driver net8185

---

### Post by tuxxy on 2008-10-07
The only thing I can think of is that 32-bit flash plugin we must use, it runs fine for me though.  Heres a link to the [64-bit user group]("http://ubuntuforums.org/group.php?groupid=258") if you got any more questions :)

---

