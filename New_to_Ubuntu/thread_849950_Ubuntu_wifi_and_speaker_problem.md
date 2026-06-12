---
title: "Ubuntu wifi and speaker problem"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by valthyx on 2008-07-05
```
 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

These are the hardwares not working in my linux. I was using windows xp previously and curently, dual-booting with linux. The problem is there is no sound even though i turned the sound volume to the maximnum, i tried to do hardware test, but no sound too(sound test failed). I tried to connect to the internet(wifi), but cant. While in windows, i could do all those thing without any problems.

 Thanks in advanced.

---

### Post by ChameleonDave on 2008-07-05
That's two totally separate problems, but oh well...

You might want to do a search for "wifi" in Synaptic to see if there are any useful packages.  I can see "kwifimanager" and "mintwifi".

You might also want to search for "wifi" and "no sound" on these fora to see if anyone else has had luck solving a similar problem.

[This page]("http://intellinuxwireless.org/") seems to have info on your network controller.

[This page]("http://hardware4linux.info/component/21335/") seems to have info on your sound controller.

---

### Post by valthyx on 2008-07-05
Ok, about the sound driver, i am using acer aspire2920  [http://hardware4linux.info/component/33153/]("http://hardware4linux.info/component/33153/"). But i dont know how to download the driver, where to click?

---

### Post by ChameleonDave on 2008-07-05
[I have found a page]("https://bugs.launchpad.net/ubuntu/+bug/122560") with info on your hardware working with some versions of the Linux kernels and not with others.

Please go to the command line and enter these commands.  Paste the output here:

```

uname -a
cat /etc/lsb-release

```

---

### Post by Papa-san on 2008-07-05
I have a Dell 1525 with the same ```
*-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: eth1
                version: 02
                serial: 00:1c:bf:c9:92:1d
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.56 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g

```and ```
 *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```This worked right out of the box with 7.10. I haven't upgraded to 8.04, and I doubt I will for a while. If you keep having trouble, go ahead and get the older release... Greased lightning!

---

### Post by valthyx on 2008-07-06
> **ChameleonDave said:**
> [I have found a page]("https://bugs.launchpad.net/ubuntu/+bug/122560") with info on your hardware working with some versions of the Linux kernels and not with others.

Please go to the command line and enter these commands.  Paste the output here:

```

uname -a
cat /etc/lsb-release

```




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

---

### Post by ChameleonDave on 2008-07-06
> **valthyx said:**
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

OK, great, you did the second command.  You are on Hardy.

What about the first command though?

---

### Post by valthyx on 2008-07-08
Linux MyCom-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

---

### Post by ChameleonDave on 2008-07-08
> **valthyx said:**
> Linux MyCom-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

Try this:

```

sudo apt-get install linux-ubuntu-modules-2.6.24-19-generic  linux-generic

```

See also [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).

---

### Post by valthyx on 2008-07-09
It says that my ubuntu is uptodate. What should i do? I have followed the link's instruction, but my device is not compatible. When i checked in the device manager, most of my hardwares are not detected(there were question marks), maybe it doesnt detect my drivers? is there any drivers around for linux?

---

