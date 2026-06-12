---
title: "Howto: Simple upgrade to Hardy's developing kernel - 2.6.24"
date: 2007-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by walkerk on 2007-12-21
[CENTER]**[SIZE=4][COLOR=DarkOrange]Simple kernel upgrade to 2.6.24[/COLOR][/SIZE]**
*This has been tested using Gutsy. Other versions please let me know...*
[/CENTER]

[COLOR=Red]**Disclaimer:**[/COLOR] This is how I successfully upgraded my kernel without having to compile it myself. A couple of users have had issues with this method so be aware that problems can arise. At this point removing the new kernel using the instructions at the end of the post should do the trick, but if it doesn't I take no responsibility. I will monitor this thread to try to help out anyone thats had issues. [COLOR=Red]Do not upgrade any packages while you have the Hardy repository open.[/COLOR][COLOR=Green]*** With that being said, it worked fine for me. Also, this will not remove your current kernels.***[/COLOR]

[SIZE=3]**Current kernel version:**  *2.6.24-10*[/SIZE]
[SIZE=2][COLOR=DarkOrange]**After you've upgraded please reply with your machine Model and specs so that others can benefit :)**[/COLOR][/SIZE]


[SIZE=4]**[COLOR="DarkOrange"]Option #1:[/COLOR] You can download the script I've attached and do the following:**[/SIZE]
> ***hardy.py** will upgrade to the current kernel using meta packages, meaning if you run this every week or so it will upgrade your kernel if a new version has been released.*

1. Download hardy.py from the end of this post.

2. Move to the directory in which you downloaded the script.. for example:
```
cd /path/to/file/
```3. Make the script executable:
```
chmod +x hardy.py
```4. Run it:
```
sudo python hardy.py
```This installed the new kernel. Reboot and enjoy :)



[SIZE=4]**[COLOR="DarkOrange"]Option #2:[/COLOR] Do it manually without the script.**[/SIZE]

1. First you need to add the Hardy repository (this is only temporary to pull the new kernel):
```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy main restricted' | sudo tee /etc/apt/sources.list.d/hardy.list
```2. Now that you've added the repository you need to update:
```
sudo apt-get update
```3. Next you need to install the new kernel:
```
sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
```4. Now that you've pulled the kernel you need to remove the Hardy repository: 
```
sudo rm /etc/apt/sources.list.d/hardy.list
```5. Once again you need to update so that you'll stop pulling updates from the Hardy repository:
```
sudo apt-get update
```6. Alright. If you've done all of the above without errors, you've successfully installed 2.6.24-10-generic. Now you need to reboot into the new kernel:
```
sudo reboot
```Enjoy :)


[SIZE=5][COLOR=DarkOrange]Miscellaneous fixes [/COLOR][/SIZE]
> **[COLOR="DarkOrange"]1.[/COLOR] B43 Wireless driver**: (Replaces bcm43xx) Get the new firmware [[COLOR=DarkOrange]here[/COLOR]]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware").
```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy universe' | sudo tee /etc/apt/sources.list.d/fwcutter.list

sudo apt-get update

sudo apt-get install b43-fwcutter

sudo rm /etc/apt/sources.list.d/fwcutter.list

sudo apt-get update
```

Now blacklist bcm43xx:[COLOR="Red"] (If you are still using 2.6.22 you shouldn't do this as it won't conflict with 2.6.24 and b43)[/COLOR]
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

> **[COLOR="DarkOrange"]2.[/COLOR] WLAN Interface naming.** Fix *wlan0_rename, wmaster0_rename, etc...*
**> [COLOR="Green"]I had to do this to get my wireless NIC to function correctly.** (*wlan0* doesn't work. It'll still end up *wlan0_rename*)[/COLOR]
>> Should be a temp fix as I'd assume the kernel devs will address this bug (already on launchpad)

Replace instances of **<driver>** with your wireless driver. (b43, iwl3945, madwifi, etc)

1. Alter the the NICs persistent interface name:
```
gksu gedit /etc/udev/rules.d/70-persistent-net.rules
```

2. Now remove any interfaces already listed with your WLAN NIC's MAC address.

3. Add the following and then save and exit: (Replace **00:00:00:00:00:00** with your WLAN NIC's MAC address.)
```
# PCI device 0x14e4:0x4311 (**<driver>**)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:00:00:00:00", NAME="eth1"
```

4. Now create an alias for eth1 and your driver, in my case b43: (b43, iwl3955, madwifi, etc...)
```
echo 'alias eth1 **<driver>'** | sudo tee /etc/modprobe.d/**<driver>**
```

5. Reboot


> **[COLOR="DarkOrange"]3.[/COLOR]  GCC** upgrade.
> For anyone that is having issues compiling against the new kernel, which uses a newer version of gcc, you can update:

1. Add the Hardy repository:
```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy main' | sudo tee /etc/apt/sources.list.d/gcc.list
```

2. Update:
```
sudo apt-get update
```

3. Install the gcc version available with Hardy:
```
sudo apt-get install gcc++ g++
```

4. Remove the repository:
```
sudo rm /etc/apt/sources.list.d/gcc.list
```

5. Update:
```
sudo apt-get update
```

> **[COLOR="DarkOrange"]4.[/COLOR]** **nVidia** Video cards. (Thanks **lemurian**) [COLOR="Green"]*Automated w/ the script*[/COLOR]
> Please see [this post]("http://ubuntuforums.org/showpost.php?p=4066411&postcount=87") to update to Ubuntu supported nVidia drivers.
> To use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") you'll need to re-install (**recommended**)

> **[COLOR="DarkOrange"]5.[/COLOR]** **lsusb**  ([Thanks lemurian]("http://ubuntuforums.org/showpost.php?p=4162057&postcount=189"))
> If lsusb isn't listing your USB devices, an upgrade of the udev package should do the trick...

1. Add the repository:
```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy main' | sudo tee /etc/apt/sources.list.d/udev.list
```

2. Update:
```
sudo apt-get update
```

3. Install udev:
```
sudo apt-get install udev
```

4. Remove the repository:
```
sudo rm /etc/apt/sources.list.d/udev.list
```

5. Update:
```
sudo apt-get update
```

> **[COLOR="DarkOrange"]5. [/COLOR]** **Encrypted Hard drives**
> If you are going to be booting from an encrypted hard drive see the link below:
> [http://ubuntuforums.org/showpost.php?p=4398688&postcount=456]("http://ubuntuforums.org/showpost.php?p=4398688&postcount=456")



**Check for fixes from my last thread:**
[[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=511974[/COLOR]]("http://ubuntuforums.org/showthread.php?t=511974")


[COLOR="DarkOrange"]
[SIZE=3]**Ok.. Did it hose your box? Too easy.**[/SIZE][/COLOR]

Reboot your computer and at Grub press esc to boot into your last kernel.

Remove the installed kernel and then upgrade. 
```
sudo apt-get remove linux-image-2.6.24-10-generic linux-headers-2.6.24-10-generic linux-headers-2.6.24-10 linux-restricted-modules-2.6.24-10-generic linux-ubuntu-modules-2.6.24-10-generic
``````
sudo apt-get upgrade
```**Updates**
1/4/2008: *The script will now determine if nVidia drivers are necessary...*

---

### Post by Trueno22 on 2007-12-25
Worked great for me using the script.

Specs:
e6600 Core 2 Duo
Gigabyte P35-DS3R MOBO
Geil 4-4-4-12 DDR2 900Mhz RAM
Nvidia Geforce 7600GT
Belkin Wireless G Desktop Card (atheros chipset)


Question since it is  2.6.24 is CFS included in this kernel???

---

### Post by exploder on 2007-12-25
Worked just fine for me. Thanks!

---

### Post by walkerk on 2007-12-25
> **Trueno22 said:**
> Worked great for me using the script.

Specs:
e6600 Core 2 Duo
Gigabyte P35-DS3R MOBO
Geil 4-4-4-12 DDR2 900Mhz RAM
Nvidia Geforce 7600GT
Belkin Wireless G Desktop Card (atheros chipset)


Question since it is  2.6.24 is CFS included in this kernel???

> **exploder said:**
> Worked just fine for me. Thanks!

Great to hear it guys :) Happy Holidays!

---

### Post by walkerk on 2007-12-25
> **Trueno22 said:**
> Worked great for me using the script.

Specs:
e6600 Core 2 Duo
Gigabyte P35-DS3R MOBO
Geil 4-4-4-12 DDR2 900Mhz RAM
Nvidia Geforce 7600GT
Belkin Wireless G Desktop Card (atheros chipset)


Question since it is  2.6.24 is CFS included in this kernel???

I would believe so... as long as the Ubuntu devs compiled CFS with the kernel...

---

### Post by exploder on 2007-12-25
One question, what is the path to the linux-ubuntu-modules? When I removed the old kernel the linux-ubuntu-modules 2.6.22.14 will mot completely un-install and I would like to manually remove them.

---

### Post by walkerk on 2007-12-25
> **exploder said:**
> One question, what is the path to the linux-ubuntu-modules? When I removed the old kernel the linux-ubuntu-modules 2.6.22.14 will mot completely un-install and I would like to manually remove them.

I would suggest leaving a fall-back kernel just in case... but the ubuntu modules are located here:

```
/lib/modules/**[COLOR="Red"]2.6.22-14-generic[/COLOR]**/ubuntu
```

where **[COLOR="Red"]2.6.22-14-generic[/COLOR]** is the kernel you are removing...

Hope this helps. :)

---

### Post by gfg on 2007-12-25
I am testing this now, will report results later.

Edit: Fantastic, it worked great, no problems! And as I'd hoped it fixed suspending! That was the only thing I missed after switching from Vista. Now everything's perfect. Thank you very much sir for a great script!

---

### Post by walkerk on 2007-12-25
> **gfg said:**
> I am testing this now, will report results later.

Edit: Fantastic, it worked great, no problems! And as I'd hoped it fixed suspending! That was the only thing I missed after switching from Vista. Now everything's perfect. Thank you very much sir for a great script!

Glad to help :)

---

### Post by exploder on 2007-12-25
E: linux-ubuntu-modules-2.6.22-14-generic: subprocess post-removal script returned error exit status 1

That is what I get when I try and remove the residual config files. I looked at the path listed above but linux-ubuntu-modules from the old config are not there.

Any ideas?

---

### Post by exploder on 2007-12-25
Got it solved! The new kernel works great!

Hardware Spece

Biostar mainboard
Athlon XP 1800+
VIA Rhine Onboard Network Card
VIA Vinal AC97 Onboard Sound
ATI Radeon 7200 AGP Graphics Card
Maxtor 120 GB ATA HD
Phillips 2400 CDRW
Combo Drive CDRW?DVDRW Pulled from a damaged HP 
1 GB DDR RAM

Thanks again for this thread and the help!

Merry Christmas!

---

### Post by walkerk on 2007-12-26
> **exploder said:**
> Got it solved! The new kernel works great!

Hardware Spece

Biostar mainboard
Athlon XP 1800+
VIA Rhine Onboard Network Card
VIA Vinal AC97 Onboard Sound
ATI Radeon 7200 AGP Graphics Card
Maxtor 120 GB ATA HD
Phillips 2400 CDRW
Combo Drive CDRW?DVDRW Pulled from a damaged HP 
1 GB DDR RAM

Thanks again for this thread and the help!

Merry Christmas!

Glad to hear it :) Happy New Years!

---

### Post by fjf on 2007-12-26
Well, I did it and it works.  Unfortunately, I needed it to make lmsensors work using the abutguru3 module (I have an abit ip35 pro motherboard), supposedly working since 2.6.23, but this module is not in this kernel.  Damn!!.  Bad luck.

---

### Post by Muscar on 2007-12-26
Hmm, maybe ill try this, how stable is it?

---

### Post by walkerk on 2007-12-26
Worked flawlessly for me... everyone else as well..

You can take a look at my last [thread]("http://ubuntuforums.org/showthread.php?t=511974") (same deal but from Feisty to Gutsy kernel, 2.6.22)

---

### Post by shifty2 on 2007-12-26
Installed and having issues with desktop effects. Just as I had them working on gutsy...

---

### Post by walkerk on 2007-12-26
> **shifty2 said:**
> Installed and having issues with desktop effects. Just as I had them working on gutsy...

What kind of graphics card do you have?

Also, you can still press esc at Grub 1.5 at boot and load an old kernel (Desktop effects will work there.)

If you have an nVidia card or ATI you might look at the link from my last kernel upgrade thread... [click here]("http://ubuntuforums.org/showthread.php?t=511974") and look at miscellaneous fixes.

---

### Post by shifty2 on 2007-12-26
cheers. I am using my previous kernel atm, Have an ATI card so will keep browsing to see if i can find any fixes  around.

---

### Post by loopeando on 2007-12-26
When I try to upgrade using the script I'm getting this

 The following packages will be upgraded:
  libc6 libc6-dev libc6-i686 libncurses5 libncurses5-dev linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-common
  linux-restricted-modules-generic tzdata util-linux

Is it ok to upgrade those packages?

Edit: Yes, It's.

It works great on a Lenovo 3000 N100 and it finally solves de Intel HDA Audio Jack sense problem. The only thing that doesn't work is the Wi-Fi light on the laptop but it isn't really that useful.

Thx!

---

### Post by BC7333 on 2007-12-27
Finally 3945abg wireless connecting as it should with USR 9106 adsl router.

Only negative is that the wireless status/indicator light is not working.

Sleep/suspend to disk also works now.

Thanks!

---

### Post by walkerk on 2007-12-27
> **loopeando said:**
> When I try to upgrade using the script I'm getting this

 The following packages will be upgraded:
  libc6 libc6-dev libc6-i686 libncurses5 libncurses5-dev linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-common
  linux-restricted-modules-generic tzdata util-linux

Is it ok to upgrade those packages?

Edit: Yes, It's.

It works great on a Lenovo 3000 N100 and it finally solves de Intel HDA Audio Jack sense problem. The only thing that doesn't work is the Wi-Fi light on the laptop but it isn't really that useful.

Thx!

> **BC7333 said:**
> Finally 3945abg wireless connecting as it should with USR 9106 adsl router.

Only negative is that the wireless status/indicator light is not working.

Sleep/suspend to disk also works now.

Thanks!

The Wifi light is strange. It works fine with my BCM94311... loopeando, by chance do you have a 3945?

Also BC7333, which driver are you using? ipw3945 or iwl3945?
```
sudo lshw -C network
```

**edit: **Looking at a config online all I see is the iwl3945 driver which is good. I'll take a look at the kernel config when I get home to ensure this is how its setup:
```
CONFIG_IWL3945=m
CONFIG_IWL3945_QOS=y
CONFIG_IWL3945_SPECTRUM_MEASUREMENT=y
CONFIG_IWL3945_LED=y
```

---

### Post by BC7333 on 2007-12-27
> **walkerk said:**
> The Wifi light is strange. It works fine with my BCM94311... loopeando, by chance do you have a 3945?

Also BC7333, which driver are you using? ipw3945 or iwl3945?
```
sudo lshw -C network
```

**edit: **Looking at a config online all I see is the iwl3945 driver which is good. I'll take a look at the kernel config when I get home to ensure this is how its setup:
```
CONFIG_IWL3945=m
CONFIG_IWL3945_QOS=y
CONFIG_IWL3945_SPECTRUM_MEASUREMENT=y
CONFIG_IWL3945_LED=y
```

Here it is:

```
brian@brian-laptop:~$ sudo lshw -C network
[sudo] password for brian:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:09:5d:15:60:23
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0_rename
       version: 02
       serial: 00:19:d2:bb:50:59
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.3 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
brian@brian-laptop:~
```$

---

### Post by walkerk on 2007-12-27
> **BC7333 said:**
> Here it is:

```
brian@brian-laptop:~$ sudo lshw -C network
[sudo] password for brian:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:09:5d:15:60:23
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0_rename
       version: 02
       serial: 00:19:d2:bb:50:59
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.3 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
brian@brian-laptop:~
```$

Yea you're using the iwl3945 driver.

I see your wireless interface is **wmaster0_rename**. Are you having any issues with this? Mine was switching back and forth between that and **wlan0_rename**.
 I suggest you try naming the interface [COLOR="Green"]**eth1**[/COLOR]. The instructions are in my OP under Miscalleanous Fixes.

---

### Post by BC7333 on 2007-12-27
Here is the config file eth1 already present, guessing for the cabled nic.  Should I just rename it to eth0 ad then wireless to eth1?

Thanks!

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
#SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:09:5d:15:60:23", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x8086:0x4222 (ipw3945)
#SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:bb:50:59", NAME="wlan0"

# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:bb:50:59", NAME="wlan0"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:09:5d:15:60:23", NAME="eth1"
```

---

### Post by walkerk on 2007-12-27
> **BC7333 said:**
> Here is the config file eth1 already present, guessing for the cabled nic.  Should I just rename it to eth0 ad then wireless to eth1?

Thanks!

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
#SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:09:5d:15:60:23", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x8086:0x4222 (ipw3945)
#SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:bb:50:59", NAME="wlan0"

# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:bb:50:59", NAME="wlan0"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:09:5d:15:60:23", NAME="eth1"
```

Yes. Alter the file to just include the following: (I just edited your file)
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:09:5d:15:60:23", NAME="eth1"

# PCI device 0x8086:0x4222 (ipw3945) *** Changed from wlan0 to fix the rename issue
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:bb:50:59", NAME="eth1"
```

Now create an alias for it:
```
echo 'alias eth1 iwl3945' | sudo tee /etc/modprobe.d/iwl3945
```

Now reboot :)

Let me know...

---

### Post by BC7333 on 2007-12-27
> 
Now reboot :)

Let me know...

Done.. wireless comes up within a couple seconds now.. before was taking 15 to 30 seconds..

awe..  :popcorn:

Did not affect the wlan status light though. still completely off. Not bad though.. guess it will save battery power :)

---

### Post by walkerk on 2007-12-27
> **BC7333 said:**
> Done.. wireless comes up within a couple seconds now.. before was taking 15 to 30 seconds..

awe..  :popcorn:

Did not affect the wlan status light though. still completely off. Not bad though.. guess it will save battery power :)

LOL. Glad it did something. At least this way your interface will always stay the same instead of swapping back and forth from wlan0_ren, wlan0_rename, wmaster0, and wmaster0_rename (I saw them all and it drove me nuts changing my interface in WICD)

---

### Post by BC7333 on 2007-12-27
> **walkerk said:**
> LOL. Glad it did something. At least this way your interface will always stay the same instead of swapping back and forth from wlan0_ren, wlan0_rename, wmaster0, and wmaster0_rename (I saw them all and it drove me nuts changing my interface in WICD)

Well.. this was with a warm boot.. did a cold boot and something different happened..

Could not connect, checked network manager and it showed two eth1 interfaces and an eth1_rename in the gui all as wired.

reverted back to wlan0 in persistent net rules and got wireless back so all still ok.

Another thing I noticed when booting, (right after upgrading the kernel) is a message that flashes when booting:

AppArmor: unable to register AppArmor

never saw this one with the last kernel and really don't have a clue what AppArmor is.

---

### Post by Gigamo on 2007-12-27
Not working here. When I boot in the new kernel it doesn't find my graphic/screen drivers and I get an option to configure it, to quit or to continue into an empty X desktop. I now did the things described in the "did it hose your system" section, but I now realise that this isn't fixing the new kernel, but simply removing it again and living with the old one? :D

Is there a way to use the new kernel? Or to fix the X not recognising my video card or screen anymore?

---

### Post by walkerk on 2007-12-27
> **BC7333 said:**
> Well.. this was with a warm boot.. did a cold boot and something different happened..

Could not connect, checked network manager and it showed two eth1 interfaces and an eth1_rename in the gui all as wired.

reverted back to wlan0 in persistent net rules and got wireless back so all still ok.

Another thing I noticed when booting, (right after upgrading the kernel) is a message that flashes when booting:

AppArmor: unable to register AppArmor

never saw this one with the last kernel and really don't have a clue what AppArmor is.

Strange. :/ I can't re-create this :/ 

I get the same AppArmor error though I'm not sure why... looking into it../

---

### Post by walkerk on 2007-12-27
> **Gigamo said:**
> Not working here. When I boot in the new kernel it doesn't find my graphic/screen drivers and I get an option to configure it, to quit or to continue into an empty X desktop. I now did the things described in the "did it hose your system" section, but I now realise that this isn't fixing the new kernel, but simply removing it again and living with the old one? :D

Is there a way to use the new kernel?

What kind of graphics card do you have?
```
lspci | grep Display
```

you could try booting into 2.6.24 recovery mode and try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by BC7333 on 2007-12-27
> **walkerk said:**
> Strange. :/ I can't re-create this :/ 



I've probably fiddled enough before to create some 'unique' network environment here.

In any case is a lot better than before!  This is the third time I've used your kernel uprade scripts and it just keeps getting better.. and better.

---

### Post by walkerk on 2007-12-27
> **BC7333 said:**
> Another thing I noticed when booting, (right after upgrading the kernel) is a message that flashes when booting:

AppArmor: unable to register AppArmor

never saw this one with the last kernel and really don't have a clue what AppArmor is.

[https://lists.ubuntu.com/archives/hardy-changes/2007-December/003113.html](https://lists.ubuntu.com/archives/hardy-changes/2007-December/003113.html)

I think the kernel team is removing AppArmor...

---

### Post by Gigamo on 2007-12-27
Thanks for all your help btw walkerk :)

My graphics card is a 8600M GT 512MB DDR2.

Will sudo dpkg-reconfigure -phigh xserver-xorg make any changes to the .22-14 kernel if ran in the .24 kernel?

I might add that I installed nvidia drivers using Envy on this kernel. I'm stumped here, anyone with any advice or solutions on how to migrate the driver to the new kernel?

---

### Post by Gigamo on 2007-12-27
Ooookaaaay, now I got another weird bug:

Here's my story; I installed the kernel as described in this post. I booted with it but my video settings were messed up. I booted back into the old kernel and removed this one again. Now I did some research how to go into vesa mode and then reinstall the nvidia driver in the new kernel, so I ran the hardy.py script again. It finished way faster than the first time I ran it, and asked for a reboot. I rebooted, but here's my problem: The new kernel isn't installed, or at least it's not in the boot list :D

Help!

---

### Post by atlas95 on 2007-12-27
Hello,
lsusb report me nothing while I run this kernel, could you help me? 
Thanks

---

### Post by walkerk on 2007-12-27
> **Gigamo said:**
> Ooookaaaay, now I got another weird bug:

Here's my story; I installed the kernel as described in this post. I booted with it but my video settings were messed up. I booted back into the old kernel and removed this one again. Now I did some research how to go into vesa mode and then reinstall the nvidia driver in the new kernel, so I ran the hardy.py script again. It finished way faster than the first time I ran it, and asked for a reboot. I rebooted, but here's my problem: The new kernel isn't installed, or at least it's not in the boot list :D

Help!

Yea, you'll need to re-run the Envy script for the new kernel. I'm guessing something didn't download completely. Ensure you are using the VESA driver and re-run the script. If the script runs completely you will reboot into the new driver. 

Let me know...

---

### Post by walkerk on 2007-12-27
> **atlas95 said:**
> Hello,
lsusb report me nothing while I run this kernel, could you help me? 
Thanks

What is the output of:
```
lspci | grep USB
```

---

### Post by loopeando on 2007-12-27
> **walkerk said:**
> Yes. Alter the file to just include the following: (I just edited your file)
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:09:5d:15:60:23", NAME="eth1"

# PCI device 0x8086:0x4222 (ipw3945) *** Changed from wlan0 to fix the rename issue
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:bb:50:59", NAME="eth1"
```

Now create an alias for it:
```
echo 'alias eth1 iwl3945' | sudo tee /etc/modprobe.d/iwl3945
```

Now reboot :)

Let me know...

Light is still off but it doesn't bother me.

The only thing that does is that I have to mount via console two partitions on my home server which are at fstab and should automount.

These partitions are mounted through smbfs from a Windows XP computer.

Any idea?

---

### Post by walkerk on 2007-12-27
> **loopeando said:**
> Light is still off but it doesn't bother me.

The only thing that does is that I have to mount via console two partitions on my home server which are at fstab and should automount.

These partitions are mounted through smbfs from a Windows XP computer.

Any idea?

Are the partitions still listed in /etc/fstab?

---

### Post by nowshining on 2007-12-27
i use the vanilla kernel, seems like others are not having many probs, hmmm I may as well compile 2.6.24 - the rc versions...unless Ubuntu patched it to death to fix issues...

---

### Post by Gigamo on 2007-12-28
Okay, I now succesfully upgraded to the new kernel and reran envy. Video and stuff is working fine now, but Wicd no longer finds my wireless home network :O. How does this come/is there a fix for it?
Searched the other thread but none of the fixes work for me. I went to restricted drivers manager and Enabled the wireless driver there, rebooted, but when I go look in there now it says "Enabled" but "Not in use". How to fix this?

My other issue: Boot time is way slower on the new kernel!

---

### Post by loopeando on 2007-12-28
> **walkerk said:**
> Are the partitions still listed in /etc/fstab?

Yes, they're still there

---

### Post by walkerk on 2007-12-28
> **Gigamo said:**
> Okay, I now succesfully upgraded to the new kernel and reran envy. Video and stuff is working fine now, but Wicd no longer finds my wireless home network :O. How does this come/is there a fix for it?
Searched the other thread but none of the fixes work for me. I went to restricted drivers manager and Enabled the wireless driver there, rebooted, but when I go look in there now it says "Enabled" but "Not in use". How to fix this?

My other issue: Boot time is way slower on the new kernel!

post the results of 
```
dmesg
```

and I am experiencing the longer boot time as well... I'm investigating... both the Ubuntu develop version of 2.6.24 and my custom compiled version for kernel.org are doing this... +2 minutes to boot

---

### Post by Gigamo on 2007-12-28
Okay, sorry it took so long, here it is:

```
gigamo@GIGAMO2:~$ dmesg
[    0.000000] Linux version 2.6.24-2-generic (buildd@rothera) (gcc version 4.2.3 20071210 (prerelease) (Ubuntu 4.2.2-4ubuntu2)) #1 SMP Thu Dec 20 17:36:12 GMT 2007 (Ubuntu 2.6.24-2.4-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7bc0
[    0.000000] Entering add_active_range(0, 0, 523984) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523984
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523984
[    0.000000] On node 0 totalpages: 523984
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292307 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7B40 checksum 0
[    0.000000] ACPI: RSDP 000F7B40, 0024 (r2 Compal)
[    0.000000] ACPI: XSDT 7FED7D8C, 0094 (r1 Compal CRESTLNE  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEDFBD2, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FED9B9F, 5FBF (r2 Compal CRESTLNE  6040000 INTL 20061109)
[    0.000000] ACPI: FACS 7FEE2FC0, 0040
[    0.000000] ACPI: APIC 7FEDFCC6, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7FEDFD2E, 0038 (r1 Compal CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FEDFD66, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7FEDFDA2, 0032 (r1 Intel  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TMOR 7FEDFDD4, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC 7FEDFDFA, 0176 (r1 Compal CRESTLNE  6040000 TBD         1)
[    0.000000] ACPI: APIC 7FEDFF70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FEDFFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FED9550, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED8EBE, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED83AC, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED8306, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED7E20, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519891
[    0.000000] Kernel command line: root=UUID=c57c9fe1-c5e6-4039-8afb-4f40a12cd922 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2394.068 MHz processor.
[   17.124683] Console: colour VGA+ 80x25
[   17.124686] console [tty0] enabled
[   17.124972] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.125219] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.186199] Memory: 2066164k/2095936k available (2118k kernel code, 28524k reserved, 985k data, 364k init, 1178432k highmem)
[   17.186205] virtual kernel memory layout:
[   17.186205]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.186206]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.186207]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.186207]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.186208]       .init : 0xc040d000 - 0xc0468000   ( 364 kB)
[   17.186209]       .data : 0xc031182d - 0xc0407d64   ( 985 kB)
[   17.186210]       .text : 0xc0100000 - 0xc031182d   (2118 kB)
[   17.186212] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.186244] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   17.186352] hpet clockevent registered
[   17.266221] Calibrating delay using timer specific routine.. 4792.71 BogoMIPS (lpj=9585422)
[   17.266238] Security Framework initialized
[   17.266243] SELinux:  Disabled at boot.
[   17.266246] Capability LSM initialized
[   17.266254] Mount-cache hash table entries: 512
[   17.266356] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[   17.266363] monitor/mwait feature present.
[   17.266364] using mwait in idle threads.
[   17.266366] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.266368] CPU: L2 cache: 4096K
[   17.266370] CPU: Physical Processor ID: 0
[   17.266371] CPU: Processor Core ID: 0
[   17.266372] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[   17.266380] Compat vDSO mapped to ffffe000.
[   17.266389] Checking 'hlt' instruction... OK.
[   17.282468] SMP alternatives: switching to UP code
[   17.283607] Early unpacking initramfs... done
[   17.502245] ACPI: Core revision 20070126
[   17.502279] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.509103] CPU0: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz stepping 0a
[   17.509115] SMP alternatives: switching to SMP code
[   17.509601] Booting processor 1/1 eip 3000
[   17.519961] Initializing CPU#1
[   17.597643] Calibrating delay using timer specific routine.. 4788.00 BogoMIPS (lpj=9576002)
[   17.597648] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[   17.597652] monitor/mwait feature present.
[   17.597654] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.597655] CPU: L2 cache: 4096K
[   17.597657] CPU: Physical Processor ID: 0
[   17.597658] CPU: Processor Core ID: 1
[   17.597659] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[   17.598314] CPU1: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz stepping 0a
[   17.598334] Total of 2 processors activated (9580.71 BogoMIPS).
[   17.598508] ENABLING IO-APIC IRQs
[   17.598691] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.745471] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   17.765448] Brought up 2 CPUs
[   17.765468] CPU0 attaching sched-domain:
[   17.765470]  domain 0: span 03
[   17.765471]   groups: 01 02
[   17.765473] CPU1 attaching sched-domain:
[   17.765474]  domain 0: span 03
[   17.765475]   groups: 02 01
[   17.765629] net_namespace: 64 bytes
[   17.765635] Booting paravirtualized kernel on bare hardware
[   17.765988] Time: 20:11:10  Date: 12/28/07
[   17.766025] NET: Registered protocol family 16
[   17.766150] EISA bus registered
[   17.766154] ACPI: bus type pci registered
[   17.766511] PCI: PCI BIOS revision 2.10 entry at 0xfdde1, last bus=14
[   17.766512] PCI: Using configuration type 1
[   17.766514] Setting up standard PCI resources
[   17.768332] ACPI: EC: Look up EC in DSDT
[   17.772842] ACPI: System BIOS is requesting _OSI(Linux)
[   17.772844] ACPI: If "acpi_osi=Linux" works better,
[   17.772845] Please send dmidecode to linux-acpi@vger.kernel.org
[   17.773242] ACPI: Interpreter enabled
[   17.773245] ACPI: (supports S0 S3 S4 S5)
[   17.773256] ACPI: Using IOAPIC for interrupt routing
[   17.817898] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   17.817900] ACPI: EC: driver started in poll mode
[   17.818012] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.821105] PCI: Transparent bridge - 0000:00:1e.0
[   17.821234] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.821491] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   17.821586] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   17.821676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   17.821766] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   17.821856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   17.821945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[   17.822034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[   17.822134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   17.825669] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   17.825743] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   17.825816] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   17.825887] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   17.825959] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   17.826030] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   17.826101] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   17.826173] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   17.826277] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.826297] pnp: PnP ACPI init
[   17.826302] ACPI: bus type pnp registered
[   17.845485] pnp: PnP ACPI: found 11 devices
[   17.845487] ACPI: ACPI bus type pnp unregistered
[   17.845489] PnPBIOS: Disabled by ACPI PNP
[   17.845614] PCI: Using ACPI for IRQ routing
[   17.845617] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.976992] NET: Registered protocol family 8
[   17.976994] NET: Registered protocol family 20
[   17.977016] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.977019] hpet0: 3 64-bit timers, 14318180 Hz
[   17.980981] Time: tsc clocksource has been installed.
[   17.980986] Switched to high resolution mode on CPU 0
[   17.981069] Switched to high resolution mode on CPU 1
[   17.992943] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   17.992946] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   17.992948] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   17.992950] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   17.992952] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   17.992954] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   17.992956] system 00:01: iomem range 0x0-0x0 could not be reserved
[   17.992958] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   17.992963] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   17.992968] system 00:06: ioport range 0x680-0x69f has been reserved
[   17.992970] system 00:06: ioport range 0x800-0x80f has been reserved
[   17.992972] system 00:06: ioport range 0x1000-0x107f has been reserved
[   17.992973] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   17.992975] system 00:06: ioport range 0x1640-0x164f has been reserved
[   17.992977] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[   17.992979] system 00:06: ioport range 0xff00-0xff7f has been reserved
[   18.023247] PCI: Failed to allocate mem resource #6:20000@c7000000 for 0000:01:00.0
[   18.023363] PCI: Bridge: 0000:00:01.0
[   18.023365]   IO window: 2000-2fff
[   18.023367]   MEM window: c4000000-c6ffffff
[   18.023370]   PREFETCH window: d0000000-dfffffff
[   18.023372] PCI: Bridge: 0000:00:1c.0
[   18.023375]   IO window: 3000-3fff
[   18.023380]   MEM window: bc000000-bfffffff
[   18.023384]   PREFETCH window: cc000000-cdffffff
[   18.023389] PCI: Bridge: 0000:00:1c.1
[   18.023392]   IO window: 4000-4fff
[   18.023397]   MEM window: f0000000-f3ffffff
[   18.023401]   PREFETCH window: fa000000-fbffffff
[   18.023406] PCI: Bridge: 0000:00:1c.2
[   18.023409]   IO window: 5000-5fff
[   18.023414]   MEM window: f4000000-f7ffffff
[   18.023418]   PREFETCH window: fc000000-fdffffff
[   18.023423] PCI: Bridge: 0000:00:1c.3
[   18.023426]   IO window: 6000-6fff
[   18.023431]   MEM window: b4000000-b7ffffff
[   18.023435]   PREFETCH window: c8000000-c9ffffff
[   18.023441] PCI: Bridge: 0000:00:1c.4
[   18.023443]   IO window: 7000-7fff
[   18.023449]   MEM window: f8100000-f81fffff
[   18.023452]   PREFETCH window: disabled.
[   18.023458] PCI: Bridge: 0000:00:1c.5
[   18.023459]   IO window: disabled.
[   18.023464]   MEM window: f8000000-f80fffff
[   18.023468]   PREFETCH window: disabled.
[   18.023474] PCI: Bridge: 0000:00:1e.0
[   18.023475]   IO window: disabled.
[   18.023480]   MEM window: f8200000-f82fffff
[   18.023484]   PREFETCH window: disabled.
[   18.023498] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.023502] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.023525] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.023529] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.023552] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   18.023556] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.023579] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   18.023584] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.023607] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   18.023612] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   18.023634] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   18.023639] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   18.023662] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   18.023667] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   18.023680] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.023687] NET: Registered protocol family 2
[   18.060845] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.061002] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.061307] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.061459] TCP: Hash tables configured (established 131072 bind 65536)
[   18.061461] TCP reno registered
[   18.072870] checking if image is initramfs...<6>ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.295958]  it is
[   18.538518] Freeing initrd memory: 7230k freed
[   18.538653] Simple Boot Flag at 0x38 set to 0x1
[   18.539087] audit: initializing netlink socket (disabled)
[   18.539099] audit(1198872670.224:1): initialized
[   18.539269] highmem bounce pool size: 64 pages
[   18.540585] VFS: Disk quotas dquot_6.5.1
[   18.540636] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.540747] AppArmor: Unable to register AppArmor
[   18.540882] io scheduler noop registered
[   18.540884] io scheduler anticipatory registered
[   18.540885] io scheduler deadline registered
[   18.540892] io scheduler cfq registered (default)
[   18.541028] Boot video device is 0000:01:00.0
[   18.541114] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.541145] assign_interrupt_mode Found MSI capability
[   18.541171] Allocate Port Service[0000:00:01.0:pcie00]
[   18.541196] Allocate Port Service[0000:00:01.0:pcie02]
[   18.541259] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.541323] assign_interrupt_mode Found MSI capability
[   18.541376] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.541400] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.541505] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.541570] assign_interrupt_mode Found MSI capability
[   18.541631] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.541652] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.541747] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.541808] assign_interrupt_mode Found MSI capability
[   18.541869] Allocate Port Service[0000:00:1c.2:pcie00]
[   18.541890] Allocate Port Service[0000:00:1c.2:pcie02]
[   18.541994] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   18.542062] assign_interrupt_mode Found MSI capability
[   18.542125] Allocate Port Service[0000:00:1c.3:pcie00]
[   18.542146] Allocate Port Service[0000:00:1c.3:pcie02]
[   18.542246] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   18.542321] assign_interrupt_mode Found MSI capability
[   18.542376] Allocate Port Service[0000:00:1c.4:pcie00]
[   18.542398] Allocate Port Service[0000:00:1c.4:pcie02]
[   18.542509] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   18.542572] assign_interrupt_mode Found MSI capability
[   18.542624] Allocate Port Service[0000:00:1c.5:pcie00]
[   18.542648] Allocate Port Service[0000:00:1c.5:pcie02]
[   18.542802] isapnp: Scanning for PnP cards...
[   18.900334] isapnp: No Plug & Play device found
[   18.917088] Real Time Clock Driver v1.12ac
[   18.917245] hpet_resources: 0xfed00000 is busy
[   18.917268] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.918091] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.918139] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.918204] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.960983] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.960987] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.991247] mice: PS/2 mouse device common for all mice
[   18.991319] EISA: Probing bus 0 at eisa.0
[   18.991326] Cannot allocate resource for EISA slot 1
[   18.991328] Cannot allocate resource for EISA slot 2
[   18.991329] Cannot allocate resource for EISA slot 3
[   18.991331] Cannot allocate resource for EISA slot 4
[   18.991332] Cannot allocate resource for EISA slot 5
[   18.991334] Cannot allocate resource for EISA slot 6
[   18.991335] Cannot allocate resource for EISA slot 7
[   18.991342] EISA: Detected 0 cards.
[   18.991344] cpuidle: using governor ladder
[   18.991345] cpuidle: using governor menu
[   18.991398] TCP cubic registered
[   18.991404] NET: Registered protocol family 1
[   18.991424] Using IPI No-Shortcut mode
[   18.991529]   Magic number: 3:879:195
[   18.991541]   hash matches device ttys7
[   18.991544]   hash matches device ttypa
[   18.991744] Freeing unused kernel memory: 364k freed
[   19.018762] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.144477] fuse init (API version 7.9)
[   20.153960] ACPI: SSDT 7FED8B3A, 02BC (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   20.154118] ACPI: SSDT 7FED860B, 04AA (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   20.155649] Monitor-Mwait will be used to enter C-1 state
[   20.155652] Monitor-Mwait will be used to enter C-2 state
[   20.155653] Monitor-Mwait will be used to enter C-3 state
[   20.155740] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.155744] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.158236] ACPI: SSDT 7FED8DF6, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   20.158383] ACPI: SSDT 7FED8AB5, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   20.163750] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   20.163754] ACPI: Processor [CPU1] (supports 8 throttling states)
[   20.275664] usbcore: registered new interface driver usbfs
[   20.275681] usbcore: registered new interface driver hub
[   20.275786] usbcore: registered new device driver usb
[   20.276559] USB Universal Host Controller Interface driver v3.0
[   20.276600] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.276613] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   20.276618] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   20.276773] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   20.276810] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[   20.276910] usb usb1: configuration #1 chosen from 1 choice
[   20.276926] hub 1-0:1.0: USB hub found
[   20.276929] hub 1-0:1.0: 2 ports detected
[   20.376876] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[   20.376887] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   20.376893] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   20.376910] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   20.376947] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00001820
[   20.377034] usb usb2: configuration #1 chosen from 1 choice
[   20.377054] hub 2-0:1.0: USB hub found
[   20.377058] hub 2-0:1.0: 2 ports detected
[   20.403960] SCSI subsystem initialized
[   20.410395] libata version 3.00 loaded.
[   20.480685] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[   20.480697] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.480703] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.480722] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   20.480764] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00001840
[   20.480841] usb usb3: configuration #1 chosen from 1 choice
[   20.480856] hub 3-0:1.0: USB hub found
[   20.480859] hub 3-0:1.0: 2 ports detected
[   20.584520] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   20.584530] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.584536] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.584552] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   20.584587] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[   20.584669] usb usb4: configuration #1 chosen from 1 choice
[   20.584685] hub 4-0:1.0: USB hub found
[   20.584688] hub 4-0:1.0: 2 ports detected
[   20.688355] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.688365] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.688368] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.688387] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   20.688418] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[   20.688504] usb usb5: configuration #1 chosen from 1 choice
[   20.688520] hub 5-0:1.0: USB hub found
[   20.688524] hub 5-0:1.0: 2 ports detected
[   20.792228] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   20.792246] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   20.792253] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   20.792283] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   20.796190] ehci_hcd 0000:00:1a.7: debug port 1
[   20.796201] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   20.796205] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8504000
[   20.808022] Clocksource tsc unstable (delta = -1783173230 ns)
[   20.812012] Time: hpet clocksource has been installed.
[   20.813051] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.813144] usb usb6: configuration #1 chosen from 1 choice
[   20.813370] hub 6-0:1.0: USB hub found
[   20.813374] hub 6-0:1.0: 4 ports detected
[   20.828864] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[   20.828883] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.828890] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.828920] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   20.832849] ehci_hcd 0000:00:1d.7: debug port 1
[   20.832855] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.832859] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xf8504400
[   20.838823] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.838964] usb usb7: configuration #1 chosen from 1 choice
[   20.838996] hub 7-0:1.0: USB hub found
[   20.839002] hub 7-0:1.0: 6 ports detected
[   20.848005] tg3.c:v3.86 (November 9, 2007)
[   20.848091] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.848106] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   20.885971] usb 6-2: new high speed USB device using ehci_hcd and address 2
[   21.014553] usb 6-2: configuration #1 chosen from 1 choice
[   21.060096] eth0: Tigon3 [partno(none) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:38:2b:e9:2c
[   21.060100] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   21.060102] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   21.060181] ACPI: PCI Interrupt 0000:0e:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[   21.112810] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8200000-f82007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   21.116930] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   21.116968] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.116983] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   21.117006] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   21.117029] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.117040] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   21.120915] ata_piix 0000:00:1f.1: version 2.12
[   21.120930] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   21.120964] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.121346] scsi0 : ata_piix
[   21.121682] scsi1 : ata_piix
[   21.121725] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[   21.121727] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[   21.152192] ata1.00: ATAPI: Slimtype DVDRW SSM-8515S, GS09, max UDMA/33
[   21.161302] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   21.170073] ata1.00: configured for UDMA/33
[   21.183543] usb 2-1: configuration #1 chosen from 1 choice
[   21.218828] scsi 0:0:0:0: CD-ROM            Slimtype DVDRW SSM-8515S  GS09 PQ: 0 ANSI: 5
[   21.218916] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   21.232015] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   21.232060] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.232184] scsi2 : ata_piix
[   21.232349] scsi3 : ata_piix
[   21.232417] ata3: SATA max UDMA/133 cmd 0x18f8 ctl 0x18cc bmdma 0x18e0 irq 19
[   21.232419] ata4: SATA max UDMA/133 cmd 0x18f0 ctl 0x18c8 bmdma 0x18e8 irq 19
[   21.234960] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   21.247792] ata3.00: ATA-8: SAMSUNG HM250JI, HS100-08, max UDMA7
[   21.247794] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   21.252148] ata3.00: configured for UDMA/133
[   21.256007] usb 2-2: configuration #1 chosen from 1 choice
[   21.287202] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HM250JI  HS10 PQ: 0 ANSI: 5
[   21.292893] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   21.292902] sd 2:0:0:0: [sda] Write Protect is off
[   21.292904] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.292916] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.292954] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   21.292962] sd 2:0:0:0: [sda] Write Protect is off
[   21.292963] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.292975] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.292977]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.299734] Uniform CD-ROM driver Revision: 3.20
[   21.299793] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   21.396580] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f78b2402261]
[   21.657288] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   21.839167] usb 5-1: configuration #1 chosen from 1 choice
[   21.849891] usbcore: registered new interface driver hiddev
[   21.852560]  sda1 sda2 <<6>input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.2/usb5/5-1/5-1:1.0/input/input2
[   21.864929]  sda5 > sda3 sda4
[   21.880923] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-1
[   21.880940] usbcore: registered new interface driver usbhid
[   21.880944] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   21.881583] sd 2:0:0:0: [sda] Attached SCSI disk
[   21.884532] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   21.884546] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   22.174680] Attempting manual resume
[   22.174683] swsusp: Resume From Partition 8:3
[   22.174684] PM: Checking swsusp image.
[   22.174922] PM: Resume from disk failed.
[   22.210316] kjournald starting.  Commit interval 5 seconds
[   22.210353] EXT3-fs: mounted filesystem with ordered data mode.
[   28.091482] Linux agpgart interface v0.102
[   28.280736] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.320146] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.447902] iTCO_vendor_support: vendor-support=0
[   28.548266] tpm_inf_pnp 00:08: Found TPM with ID IFX0102
[   28.548325] tpm_inf_pnp 00:08: TPM found: config base 0x4e, data base 0x1670, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   28.611660] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   28.635606] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.653054] input: Power Button (FF) as /devices/virtual/input/input4
[   28.730383] ACPI: Power Button (FF) [PWRF]
[   28.730435] input: Lid Switch as /devices/virtual/input/input5
[   28.762388] ACPI: Lid Switch [LID0]
[   28.762433] input: Power Button (CM) as /devices/virtual/input/input6
[   28.810241] ACPI: Power Button (CM) [PWRB]
[   29.341557] nvidia: module license 'NVIDIA' taints kernel.
[   29.596032] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.596046] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   29.596338] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.07  Thu Dec 13 18:42:56 PST 2007
[   29.619902] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input7
[   29.676557] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.680820] ACPI: AC Adapter [ACAD] (on-line)
[   29.687890] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   29.696937] ACPI: Battery Slot [BAT1] (battery present)
[   29.699025] Linux video capture interface: v2.00
[   29.744567] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   29.782665] Bluetooth: Core ver 2.11
[   29.782703] NET: Registered protocol family 31
[   29.782704] Bluetooth: HCI device and connection manager initialized
[   29.782707] Bluetooth: HCI socket layer initialized
[   29.807216] Bluetooth: HCI USB driver ver 2.9
[   29.808618] usbcore: registered new interface driver hci_usb
[   29.829661] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.1.17kds
[   29.829664] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.829749] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   29.829763] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   29.829781] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   29.832744] sdhci: Secure Digital Host Controller Interface driver
[   29.832746] sdhci: Copyright(c) Pierre Ossman
[   29.898846] sdhci: SDHCI controller found at 0000:0e:06.1 [1180:0822] (rev 22)
[   29.898871] ACPI: PCI Interrupt 0000:0e:06.1[B] -> GSI 23 (level, low) -> IRQ 21
[   29.898887] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   29.898923] mmc0: SDHCI at 0xf8200800 irq 21 DMA
[   29.960188] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b018)
[   29.963516] usbcore: registered new interface driver uvcvideo
[   29.963519] USB Video Class driver (v0.1.0)
[   30.002570] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   30.002870] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   30.161394] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 23
[   30.161414] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   30.262002] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input9
[   30.268482] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   30.268527] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.002975] lp: driver loaded but no devices found
[   32.074914] Adding 498004k swap on /dev/sda3.  Priority:-1 extents:1 across:498004k
[   32.705546] EXT3 FS on sda4, internal journal
[   34.102982] No dock devices found.
[   34.127425] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   35.156823] ppdev: user-space parallel port driver
[   37.397309] Bluetooth: L2CAP ver 2.9
[   37.397313] Bluetooth: L2CAP socket layer initialized
[   37.461888] Bluetooth: RFCOMM socket layer initialized
[   37.461902] Bluetooth: RFCOMM TTY layer initialized
[   37.461910] Bluetooth: RFCOMM ver 1.8
[   53.969912] UDF-fs: No VRS found
[   54.019678] ISO 9660 Extensions: Microsoft Joliet Level 1
[   54.070393] ISOFS: changing to secondary root

```

---

### Post by walkerk on 2007-12-28
Ok... your driver (iwl3945) is loading correctly. Post the results of the following
```
sudo lshw -C network
```
```
lspci | grep Network
```

```
ifconfig
```
```
iwconfig
```
```
iwlist scanning
```

---

### Post by Gigamo on 2007-12-28
Done,

```
gigamo@GIGAMO2:~$ sudo lshw -C network
[sudo] password for gigamo:
  *-network DISABLED      
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:2b:e9:2c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=half latency=0 link=yes module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:2e:6b:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g




gigamo@GIGAMO2:~$ lspci | grep Network
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)




gigamo@GIGAMO2:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)







gigamo@GIGAMO2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0







gigamo@GIGAMO2:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0_rename  No scan results

```

---

### Post by walkerk on 2007-12-28
> **Gigamo said:**
> Done,

```
gigamo@GIGAMO2:~$ sudo lshw -C network
[sudo] password for gigamo:
  *-network DISABLED      
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:2b:e9:2c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=half latency=0 link=yes module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:2e:6b:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g




gigamo@GIGAMO2:~$ lspci | grep Network
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)




gigamo@GIGAMO2:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)







gigamo@GIGAMO2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0







gigamo@GIGAMO2:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0_rename  No scan results

```

Try following my Interface rename fix in the OP under miscellaneous fixes. For **<driver>** you would use **iwl3945** 

Let me know :) I had the same issue with my Broadcom wireless..

---

### Post by Gigamo on 2007-12-28
I have tried that, but is it normal that the 'echo' command takes ages to finish? It just stops showing a '>' and nothing happens. So i just exit that terminal then. Should I let it run?

---

### Post by walkerk on 2007-12-28
> **Gigamo said:**
> I have tried that, but is it normal that the 'echo' command takes ages to finish? It just stops showing a '>' and nothing happens. So i just exit that terminal then. Should I let it run?

Nice catch buddy! I fixed it. Try it again now :)

---

### Post by Gigamo on 2007-12-28
Well, this was easy. I just went into wicd preferences and changed eth1 to wlan0_rename, and it finds my network/I have internetz now. The echo alias thingy didn't work apparently, everything was still the same after the reboot :(

---

### Post by walkerk on 2007-12-28
> **Gigamo said:**
> Well, this was easy. I just went into wicd preferences and changed eth1 to wlan0_rename, and it finds my network/I have internetz now. The echo alias thingy didn't work apparently, everything was still the same after the reboot :(

Different wireless drivers... Glad its working though :D

---

### Post by Gigamo on 2007-12-28
Yeah I'm glad too. This kernel seems faster at least. Also the firefox lag when combined with compiz is gone.

Thanks alot for this and the help :)

---

### Post by walkerk on 2007-12-28
> **Gigamo said:**
> Yeah I'm glad too. This kernel seems faster at least. Also the firefox lag when combined with compiz is gone.

Thanks alot for this and the help :)

No problem :)

---

### Post by olmari on 2007-12-29
Hmm shouldn't you include updating of GCC also so it would match the version kernel was compiled with? Without that half of stuff goes wrong (vmware modules for example).

As the vmware config says > Your kernel was built with "gcc" version "4.2.3", while you are trying to use "/usr/bin/gcc" version "4.1.3

---

### Post by walkerk on 2007-12-30
> **olmari said:**
> Hmm shouldn't you include updating of GCC also so it would match the version kernel was compiled with? Without that half of stuff goes wrong (vmware modules for example).

As the vmware config says

You could. People had this same issue with VMWare with my last thread (2.6.20 > 2.6.22)... I use VirtualBox without issues...

You could give it a try...

---

### Post by BC7333 on 2007-12-30
Regarding iwl3945 and non op led found this:

[http://bughost.org/bugzilla/show_bug.cgi?id=1209](http://bughost.org/bugzilla/show_bug.cgi?id=1209)

haven't a clue how to proceed though..

Also regarding eth1 vs wlan0 I *think* after revewing some iwl documentation the driver somehow 'likes' wlan0 best.

Holiday cheers to all!

---

### Post by olmari on 2007-12-30
> **walkerk said:**
> You could. People had this same issue with VMWare with my last thread (2.6.20 > 2.6.22)... I use VirtualBox without issues...

You could give it a try...

Yes, well, VMWare isn't only thing suffering from same issue... I know I can hunt correct GCC manually, but all peoples can't :)

---

### Post by walkerk on 2007-12-30
> **olmari said:**
> Yes, well, VMWare isn't only thing suffering from same issue... I know I can hunt correct GCC manually, but all peoples can't :)

Its as easy as re-adding the Hardy repos and
```
sudo apt-get install gcc++
```


But I haven't experienced any issues other than with VMWare... What issues have you experienced other than gcc?

---

### Post by olmari on 2007-12-30
> **walkerk said:**
> Its as easy as re-adding the Hardy repos and
```
sudo apt-get install gcc++
```


But I haven't experienced any issues other than with VMWare... What issues have you experienced other than gcc?

Building some IBM Thinkpad related kernel modules failed... Or not the building itself, but they didn't work until correct GCC was used.

---

### Post by walkerk on 2007-12-30
> **olmari said:**
> Building some IBM Thinkpad related kernel modules failed... Or not the building itself, but they didn't work until correct GCC was used.

Ahh... yea, that makes sense. I'll add the gcc bit to the OP. :)

---

### Post by MeanderingCode on 2007-12-31
Most seems well on my Thinkpad T40p:
1 Gb RAM
Processor Pentium M 1.6 GHz
Atheros chipset wireless
ATI Radeon Mobility FireGL 9000

I was hoping this update would fix my ehci_hcd kernel module problem with usb storage devices loosing connection and not holding hardware addresses (my only solution was to rmmod ehci_hcd and run at usb 1.1 speeds)

No such luck...still having problems.  The following is true for me (though i don't know whatever happened to atlas95:

> > **atlas95 said:**
> Hello,
lsusb report me nothing while I run this kernel, could you help me? 
Thanks

> **walkerk said:**
> What is the output of:
```
lspci | grep USB
```

```
myself@kioskfreedom:~$ lspci|grep -i usb
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

```

I would love for this to work.  Any help?

Also, un(sort of)related question:

I'm running VirtualBox OSE on my box here and during boot with 2.6.24-2-generic that the vboxdrv module failed to load and i can't start my VMs.  The kernel module installed (by checking what's installed via apt) is kernel-specific...i can manually go get the ..24 specific module, but i would be making educated guesses as to how to put it into the system so the correct module is loaded per the kernel booting...

Also, is this related to my usb problems?  Did i not get the updated modules that might stop this plague affecting so many dealing with their usb storage devices?



All in all, though: Many thanks, walkerk!

---

### Post by ST.x on 2008-01-01
Working well here so far. On reboot, the vesa driver was enabled (had 169.07 using envy before) so I continued to login and reran envy and rebooted and its okay now. Thanks!
edit: I haven't had problems with compiling my C programs yet so im sticking to the default gcc for now.

---

### Post by walkerk on 2008-01-01
> **MeanderingCode said:**
> 
I would love for this to work.  Any help?

Also, un(sort of)related question:

I'm running VirtualBox OSE on my box here and during boot with 2.6.24-2-generic that the vboxdrv module failed to load and i can't start my VMs.  The kernel module installed (by checking what's installed via apt) is kernel-specific...i can manually go get the ..24 specific module, but i would be making educated guesses as to how to put it into the system so the correct module is loaded per the kernel booting...

Also, is this related to my usb problems?  Did i not get the updated modules that might stop this plague affecting so many dealing with their usb storage devices?



All in all, though: Many thanks, walkerk!

As for the USB issue, I am looking into it. I've been pretty busy with the Holidays :)

To load the VBox modules for 2.6.24 you can re-add the Hardy repositories and install them: ([source]("http://ubuntuforums.org/showthread.php?t=653102"))
```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy main universe' | sudo tee /etc/apt/sources.list.d/vbox.list
```
```
sudo apt-get update
```
```
sudo apt-get install virtualbox-modules-`uname -r`
```
```
sudo rm /etc/apt/sources.list.d/vbox.list
```
```
sudo apt-get update
```

I hope this works... I haven't tested it as I am not using VBox :)

---

### Post by walkerk on 2008-01-01
> **ST.x said:**
> Working well here so far. On reboot, the vesa driver was enabled (had 169.07 using envy before) so I continued to login and reran envy and rebooted and its okay now. Thanks!
edit: I haven't had problems with compiling my C programs yet so im sticking to the default gcc for now.

I haven't had any issues either, though some people might not like the warnings they get about compiling with a different version of gcc.

---

### Post by ST.x on 2008-01-01
> **walkerk said:**
> I haven't had any issues either, though some people might not like the warnings they get about compiling with a different version of gcc.
hmm I just upgraded to it anyway lol, btw in the OP on updating gcc, theres a typo, the first part should be:
```
 echo 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main'|sudo tee /etc/apt/sources.list.d/gcc.list
```

---

### Post by walkerk on 2008-01-01
> **ST.x said:**
> hmm I just upgraded to it anyway lol, btw in the OP on updating gcc, theres a typo, the first part should be:
```
 echo 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main'|sudo tee /etc/apt/sources.list.d/gcc.list
```

Ahh... good catch :) Thanks

---

### Post by snakeeyes on 2008-01-01
Hi, thanks for the how to, but can u please help me with virtual box cause ur method doesn't work or can u tell me some other free virtual machine software.

---

### Post by walkerk on 2008-01-01
> **snakeeyes said:**
> Hi, thanks for the how to, but can u please help me with virtual box cause ur method doesn't work or can u tell me some other free virtual machine software.

In the past when I  trie to load VBox with a new kernel, it gave me an error and told me a command to run in terminal... Does it not still do this?

I can't remember the command...

---

### Post by snakeeyes on 2008-01-01
Thanks for the reply, but no that doesn't work anymore. I think virtual box developers may not have built modules for this kernel yet or something cause its really new.

---

### Post by walkerk on 2008-01-01
> **snakeeyes said:**
> Thanks for the reply, but no that doesn't work anymore. I think virtual box developers may not have built modules for this kernel yet or something cause its really new.

Please try this:
```

/etc/init.d/vboxdrv setup
```

Let me know :)

---

### Post by snakeeyes on 2008-01-01
doesn't work virtual box can't make a module for this kernel I tried that.

---

### Post by walkerk on 2008-01-02
> **snakeeyes said:**
> doesn't work virtual box can't make a module for this kernel I tried that.

Have you tried compiling the latest SVN from Virtualbox.org? From what I've read it supports 2.6.24... [Download here.]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by snakeeyes on 2008-01-02
Hey thanks, I will try this when I get home.

---

### Post by snakeeyes on 2008-01-02
Hi again I was just searching some Hardy packages in Ubuntu website and I noticed virtualbox for Hardy is in the repos so if u know which repo contains virtualbox then we can just install it from Hardy's repos. Sorry I really don't know which repo contains virtualbox myself.

---

### Post by walkerk on 2008-01-02
> **snakeeyes said:**
> Hi again I was just searching some Hardy packages in Ubuntu website and I noticed virtualbox for Hardy is in the repos so if u know which repo contains virtualbox then we can just install it from Hardy's repos. Sorry I really don't know which repo contains virtualbox myself.

No problem
```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy main universe' | sudo tee /etc/apt/sources.list.d/vbox.list
```
```
sudo apt-get update
```
```
sudo apt-get install virtualbox
```
```
sudo rm /etc/apt/sources.list.d/vbox.list
```
```
sudo apt-get update
```
It still only shows modules for 2.6.22 as the 2.6.24 kernel is in its early stages of testing by the Ubuntu devs...

I've actually tested this and it doesn't work because the virtualbox-ose-modules-2.6.24 haven't been released yet... Your best bet until they are is to compile the latest SVN trunk...

---

### Post by snakeeyes on 2008-01-02
Yeah u were right, the correct modules r not showing up, so I will find the link for downloading seperate packages again and tell u.

---

### Post by snakeeyes on 2008-01-02
Ok yeah u were right there r no modules for kernel 2.6.24-2 right now. Its ok I wasn't using virtualbox these days anyway. The new kernel works great cause on my machine the latest updates to kernel 2.6.22-14 stopped my system from booting and I couldn't suspend and hibernate either so I had to use Gutsy beta kernel 2.6.22-12 for hibernate support and to be able to boot into Kubuntu atleast. Anyway this kernel is perfect so far. Thanks for the help.

Oh yeah one more thing, how do u know which repos contain what packages?

---

### Post by stefanst on 2008-01-02
The script worked like a charm! 

Unfortunately the kernel does not. I upgraded because it is supposed to support my TV Tuner (KWorld ATSC 115) right out of the box, which it seems to do, according to my dmesg output, however, when I tune an analog channel I can see it for approx. 2 seconds before the screen goes blank. I can't tune any digital (ATSC) channels at all.
You can see details in this thread, if interested:

[http://ubuntuforums.org/showthread.php?p=4058971]("http://ubuntuforums.org/showthread.php?p=4058971")

Great work though!

---

### Post by walkerk on 2008-01-02
> **stefanst said:**
> The script worked like a charm! 

Unfortunately the kernel does not. I upgraded because it is supposed to support my TV Tuner (KWorld ATSC 115) right out of the box, which it seems to do, according to my dmesg output, however, when I tune an analog channel I can see it for approx. 2 seconds before the screen goes blank. I can't tune any digital (ATSC) channels at all.
You can see details in this thread, if interested:

[http://ubuntuforums.org/showthread.php?p=4058971]("http://ubuntuforums.org/showthread.php?p=4058971")

Great work though!

I have no experience with TV Tuners so I wouldn't know where to begin... A couple questions: 

1. What module in 2.6.24 allows compatibility?
2. How did you get it working with 2.6.22? Work-around, etc...

---

### Post by sciencewhiz on 2008-01-03
Has anyone had any problems with hard freezes under heavy network usage with the Hardy kernel? I'm using the iwl3945 driver on a dell e1405 laptop. I've had it happen twice when using sftp (in gftp) and once in update-manager.

I updated to Hardy A2, so I'm not sure if it is the new kernel or something else at this moment. I'm currently trying to reproduce it on the gutsy kernel in hardy.

my wifi light doesn't work either, but that isn't a big issue to me.

---

### Post by walkerk on 2008-01-03
> **sciencewhiz said:**
> Has anyone had any problems with hard freezes under heavy network usage with the Hardy kernel? I'm using the iwl3945 driver on a dell e1405 laptop. I've had it happen twice when using sftp (in gftp) and once in update-manager.

I updated to Hardy A2, so I'm not sure if it is the new kernel or something else at this moment. I'm currently trying to reproduce it on the gutsy kernel in hardy.

my wifi light doesn't work either, but that isn't a big issue to me.

Hardy is a totally different machine... A lot of things going on during the Alpha stage of Hardy... What I'd be more interested in is whether anyone using Gutsy with 2.6.24 is having this issue (none have been reported and a few are using iwl3945)...

---

### Post by loopeando on 2008-01-03
I'm experiencing similar issues with my iwl3945 using Gutsy with 2.6.24.

When playing a movie mouted via smbfs it takes ages to load and after a few minutes of playback it freezes.

It's strange since with Gutsy default kernel iwl3945 performance was flawless, at least for me.

---

### Post by lemurian on 2008-01-03
First, thanks to walkerk for developing and testing the procedure and script.

I upgraded to 2.6.24-2 a few minutes ago.  My machine is a Sager NP2090 (aka Compal IFL90).  See here for the full story on my setup:

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/)

Here's the uname after upgrade:

```

$ uname -a
Linux bodhi 2.6.24-2-generic #1 SMP Thu Dec 20 17:36:12 GMT 2007 i686 GNU/Linux

```

A few things to note:

1. I have not encountered the problem with wireless naming.  My wireless interface was wlan0 and is still wlan0.

2. People who are using nVidia's closed source driver also need to upgrade nvidia-glx-new while upgrading the kernel.  People can easily edit the hardy.py file and add nvidia-glx-new to the list of packages to upgrade... just like I did.

3. There used to be a noticeable delay when switching tabs in terminal and firefox while using emerald to decorate windows.  After upgrade, this delay is no longer present.

---

### Post by snakeeyes on 2008-01-03
> **lemurian said:**
> First, thanks to walkerk for developing and testing the procedure and script.

I upgraded to 2.6.24-2 a few minutes ago.  My machine is a Sager NP2090 (aka Compal IFL90).  See here for the full story on my setup:

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/)

Here's the uname after upgrade:

```

$ uname -a
Linux bodhi 2.6.24-2-generic #1 SMP Thu Dec 20 17:36:12 GMT 2007 i686 GNU/Linux

```

A few things to note:

1. I have not encountered the problem with wireless naming.  My wireless interface was wlan0 and is still wlan0.

2. People who are using nVidia's closed source driver also need to upgrade nvidia-glx-new while upgrading the kernel.  People can easily edit the hardy.py file and add nvidia-glx-new to the list of packages to upgrade... just like I did.

3. There used to be a noticeable delay when switching tabs in terminal and firefox while using emerald to decorate windows.  After upgrade, this delay is no longer present.
Hey how r the latest drivers working, I didn't upgrade to them, I will right now. Is suspend and hibernate all right? Please reply quickly I really don't want to loose suspend and hibernate.

---

### Post by lemurian on 2008-01-03
I've just noticed something...

My /proc/bus/usb is empty and lsusb does not report any information about any device.  However, all of my usb devices are working properly and /sys/bus/usb is populated.  Anyone else having this problem?

---

### Post by walkerk on 2008-01-03
> **lemurian said:**
> First, thanks to walkerk for developing and testing the procedure and script.

I upgraded to 2.6.24-2 a few minutes ago.  My machine is a Sager NP2090 (aka Compal IFL90).  See here for the full story on my setup:

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/)

Here's the uname after upgrade:

```

$ uname -a
Linux bodhi 2.6.24-2-generic #1 SMP Thu Dec 20 17:36:12 GMT 2007 i686 GNU/Linux

```

A few things to note:

1. I have not encountered the problem with wireless naming.  My wireless interface was wlan0 and is still wlan0.

2. People who are using nVidia's closed source driver also need to upgrade nvidia-glx-new while upgrading the kernel.  People can easily edit the hardy.py file and add nvidia-glx-new to the list of packages to upgrade... just like I did.

3. There used to be a noticeable delay when switching tabs in terminal and firefox while using emerald to decorate windows.  After upgrade, this delay is no longer present.

Thanks lemurian... added to OP :)

nVidia users.. You can alter the script or do the following afterwards: add the nvidia-glx-new or legacy (if your not using Envy).. add the Hardy repository** again and do the following:

```
sudo apt-get install nvidia-glx-new
```
I doubt you have a legacy card but if the above doesn't work try:
```
sudo apt-get install nvidia-glx-legacy
```
Now be sure to remove the Hardy repository** and run update..

** - Refer to the original post for instructions.

---

### Post by snakeeyes on 2008-01-03
hey when I installed the nvidia-glx-new package it also installed kernel 2.6.24-2-386 and I also have 2.6.24-2-generic. Which one should I use? The default kernel was 2.6.22-14-generic.

---

### Post by walkerk on 2008-01-03
> **snakeeyes said:**
> hey when I installed the nvidia-glx-new package it also installed kernel 2.6.24-2-386 and I also have 2.6.24-2-generic. Which one should I use? The default kernel was 2.6.22-14-generic.

What kind of processor do you have? 32bit Dual core processors run with genenic... 32 bit legacy runs with 386...

---

### Post by snakeeyes on 2008-01-03
This computer has Pentium 4 2.8 ghz processor.

---

### Post by crazyness003 on 2008-01-03
Hi, n00b here. I tried the python script once, and while it was running I saw something about i386 in there. I originally have kernel 2.6.22-14-rt
installed on 64 bit system. It's the Ubuntu Studio 7.10 x86_64 release. 

Is this "Hardy" Kernel a 64 bit one, or a x86?

anyway, as I was pondering on that question, the upgrade was complete and I restarted. 
When it booted back up, it told me my X server was not configured right and X windows couldnt load. I attribute this to the nvidia drivers for my display, but could it be something else?
And it its not, how to I install the nvidia drivers in that kernel?

My machine is an HP Pavilion tx1000 series (tx1308nr) tablet pc. 
It's got a Broadcom BCM94311MCG wlan wi-fi card (that I **can not** get working in 2.6.22)
and I was also wondering if the tablet screen will fully work
(In 2.6.22 I can only use it s a left mouse click, no biggie), WebCam and (most importantly sound.
lspci tells me i have an nVidia Corporation MCP51 High Definition Audio (rev a2).

Sorry about lack of organization, but it is what it is.

Any help is welcome, even telling to go ***** is also understandable.

edit: one more thing, how do I add the nvidia driver install command to the python script?

---

### Post by Gigamo on 2008-01-03
The kernel works fine for me on 64bit. For the nvidia drivers, I don't know how you installed them, but I just ran Envy again in the new kernel and rebooted, then everything was fine.

---

### Post by crazyness003 on 2008-01-03
hey, I just did some fiddling around and got the 2.6.24 kernel running. 
I modified the python file, i dont know if im allowed, but if it hellps:
 I added
```

nvidia-glx-new

```
at the end of packages =  "linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic" 
```

packages =  "linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic **nvidia-glx-new**"

```
When i ran the script again, everything worked perfectly
I only had to add the boot param "noapic" to the kernel entry in GRUB. For some reason no linux distro likes my laptop's apic. No biggie.

Now that im in the new kernel, i have out-of-the-box audio.
Haven't tried the new bc43 driver for wifi

I'll update if anythign new happens.

Now, for the stupid part. Since i updated this, am I still technically running a 64 bit OS?

---

### Post by Kyran on 2008-01-03
Used the script adding nvidia-glx-new to the packages. Works fine as far as I can tell.

Computer: Freeman
CPU: 2ghz AMD64 X2
Ram: 2Gib
Video: NVIDIA GeForce 7800GTX

> For some reason no linux distro likes my laptop's apic.
What model is it?

> Now, for the stupid part. Since i updated this, am I still technically running a 64 bit OS?
Yep.

---

### Post by walkerk on 2008-01-04
> **walkerk said:**
> What kind of processor do you have? 32bit Dual core processors run with genenic... 32 bit legacy runs with 386...

You should be using the generic kernel. I'm not certain why it installed 386 as well...

---

### Post by walkerk on 2008-01-04
Would someone with an nVidia graphics card please post the results of the following:
```
lspci | grep Display
```
```
lshw -C video
```

I'm altering the script to automatically determine if the user needs the nVidia drivers... If so it will prompt you tp install them or not (Envy)...

Thanks

---

### Post by Gigamo on 2008-01-04
> **walkerk said:**
> Would someone with an nVidia graphics card please post the results of the following:
```
lspci | grep Display
```
```
lshw -C video
```

I'm altering the script to automatically determine if the user needs the nVidia drivers... If so it will prompt you tp install them or not (Envy)...

Thanks

Ok, here goes:

```

gigamo@GIGAMO2:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GeForce 8600M GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

lspci | grep Display does nothing for me.

---

### Post by snakeeyes on 2008-01-04
Yeah I just found out that if it installs the 386 kernel then don't use it cause no restricted modules or anything is installed for it. I booted into the generic kernel cause I noticed I couldn't use my webcam or anything else with the 386 kernel.

---

### Post by walkerk on 2008-01-04
> **Gigamo said:**
> Ok, here goes:

```

gigamo@GIGAMO2:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GeForce 8600M GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

lspci | grep Display does nothing for me.

Thanks :)

---

### Post by walkerk on 2008-01-04
Alright... I've uploaded the new script that **should** determine if nVidia drivers are needed... Would someone give it a try? You can always press Ctrl-C to abort the installation...

---

### Post by Vinno on 2008-01-04
Anyone else getting this:

Jan  4 22:00:42 Home kernel: [  386.426757] hdc: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan  4 22:00:42 Home kernel: [  386.426760] hdc: status error: error=0x00 { }
Jan  4 22:00:42 Home kernel: [  386.426762] ide: failed opcode was: unknown
Jan  4 22:00:42 Home kernel: [  386.426763] hdc: drive not ready for command
Jan  4 22:00:44 Home kernel: [  388.422848] hdc: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan  4 22:00:44 Home kernel: [  388.422857] hdc: status error: error=0x00 { }
Jan  4 22:00:44 Home kernel: [  388.422859] ide: failed opcode was: unknown
Jan  4 22:00:44 Home kernel: [  388.422862] hdc: drive not ready for command
Jan  4 22:00:44 Home kernel: [  388.422889] hdc: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan  4 22:00:44 Home kernel: [  388.422893] hdc: status error: error=0x00 { }
Jan  4 22:00:44 Home kernel: [  388.422895] ide: failed opcode was: unknown
Jan  4 22:00:44 Home kernel: [  388.422897] hdc: drive not ready for command
Jan  4 22:00:44 Home kernel: [  388.422919] hdc: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan  4 22:00:44 Home kernel: [  388.422923] hdc: status error: error=0x00 { }
Jan  4 22:00:44 Home kernel: [  388.422924] ide: failed opcode was: unknown
Jan  4 22:00:44 Home kernel: [  388.422926] hdc: drive not ready for command
Jan  4 22:00:44 Home kernel: [  388.422966] hdc: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan  4 22:00:44 Home kernel: [  388.422970] hdc: status error: error=0x00 { }
Jan  4 22:00:44 Home kernel: [  388.422971] ide: failed opcode was: unknown
Jan  4 22:00:44 Home kernel: [  388.422973] hdc: drive not ready for command

---

### Post by wolfear on 2008-01-04
Anyone have any idea if this will stop the random freezes some of us are having under Gutsy?
I'm at the point of desperation.

---

### Post by lemurian on 2008-01-04
> **Vinno said:**
> Anyone else getting this:

Jan  4 22:00:42 Home kernel: [  386.426757] hdc: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan  4 22:00:42 Home kernel: [  386.426760] hdc: status error: error=0x00 { }


I am not experiencing this problem.

But I am amending my earlier observation.  The tabbing lag in firefox and the terminal while using emerald as the window decorator still happens.  Maybe it is more subtle or maybe it requires that the machine be more loaded to manifest itself but it is still there.  :-?

Another amendment: my comments about nvidia-glx-new presuppose that one is using the restricted drivers manager rather than Envy to get the closed-source driver from nVidia.  If you use Envy, you probably don't want to just upgrade nvidia-glx-new from the Hardy repository.  (Now that the restricted drivers manager exists, what's the point of using Envy??)

I noted earlier that lsusb is no longer working under the new kernel and asked whether anyone experienced this but I have seen no reply to that query.  Is lsusb under the new kernel working fine for anyone else???

---

### Post by ST.x on 2008-01-04
> **wolfear said:**
> Anyone have any idea if this will stop the random freezes some of us are having under Gutsy?
I'm at the point of desperation.
I haven't had any full crashes of the OS since updating to this kernel, also I haven't noticed any slowdowns in boot times as was mentioned earlier in the thread : )

> **lemurian said:**
> 
I noted earlier that lsusb is no longer working under the new kernel and asked whether anyone experienced this but I have seen no reply to that query. Is lsusb under the new kernel working fine for anyone else???

nope, lsusb isn't returning anything here either.

---

### Post by snakeeyes on 2008-01-04
> **wolfear said:**
> Anyone have any idea if this will stop the random freezes some of us are having under Gutsy?
I'm at the point of desperation.
This kernel is more stable, upgrade to this kernel as soon as u can.

---

### Post by walkerk on 2008-01-04
Could an nVidia user please post the result of:
```
lspci
```

Thanks

---

### Post by ST.x on 2008-01-04
> **walkerk said:**
> Could an nVidia user please post the result of:
```
lspci
```

Thanks
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

```

---

### Post by walkerk on 2008-01-04
> **ST.x said:**
> ```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

```

Thanks... that will work in the script. :)

---

### Post by RaZoR1394 on 2008-01-04
Ok so I upgraded to this kernel on Gutsy amd64 but now it seems I'm screwed. The nVidia drivers don't work anymore. I have tried installing the nvidia-glx-new (both from hardy and gutsy reps) and also nvidia-glx-legacy (both from hardy and gutsy reps) and it doesn't help me a bit. It doesn't matter if I boot the old kernel or the new one it still doesn't work. I'm now booting into some kind of low reduced graphics mode. I've checked my config and it looks right. I looked into the /var/log/Xorg.0.log and it seems i'm getting some kind of "no matching device" so I commented out the PCI line in the xorg.conf but it doesn't help either. And yes I've tried Envy but it doesn't work at all as it errors out. Another thing I've tried as a last resort is nvidia-xconfig.

---

### Post by walkerk on 2008-01-04
> **RaZoR1394 said:**
> Ok so I upgraded to this kernel on Gutsy amd64 but now it seems I'm screwed. The nVidia drivers don't work anymore. I have tried installing the nvidia-glx-new (both from hardy and gutsy reps) and also nvidia-glx-legacy (both from hardy and gutsy reps) and it doesn't help me a bit. It doesn't matter if I boot the old kernel or the new one it still doesn't work. I'm now booting into some kind of low reduced graphics mode. I've checked my config and it looks right. I looked into the /var/log/Xorg.0.log and it seems i'm getting some kind of "no matching device" so I commented out the PCI line in the xorg.conf but it doesn't help either. And yes I've tried Envy but it doesn't work at all as it errors out. Another thing I've tried as a last resort is nvidia-xconfig.

Make a backup copy of xorg.conf and then boot into recovery mode (Press ESC at boot) and then execute the following:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
```
sudo reboot
```

?

---

### Post by gindyo on 2008-01-04
> **walkerk said:**
> Could an nVidia user please post the result of:
```
lspci
```

Thanks

Hi walkerk,
thanks for your effort, I upgraded to 2.6.24 kernel and everything seams to be working fine,  I could not get the ndiswrapper to  work in the beginning, but after few restarts it somehow started working. and the best  of all is that after upgrading to the new kernel my  laptop suspends and comes back on without a problem.

here is my lspci output


[B]dimitar@dimitar-laptop:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
dimitar@dimitar-laptop:~/Desktop$ 
[/B]

thanks again, and I hope this helps.

---

### Post by walkerk on 2008-01-04
> **gindyo said:**
> Hi walkerk,
thanks for your effort, I upgraded to 2.6.24 kernel and everything seams to be working fine,  I could not get the ndiswrapper to  work in the beginning, but after few restarts it somehow started working. and the best  of all is that after upgrading to the new kernel my  laptop suspends and comes back on without a problem.

here is my lspci output


[B]dimitar@dimitar-laptop:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
dimitar@dimitar-laptop:~/Desktop$ 
[/B]

thanks again, and I hope this helps.

Glad it worked :) One suggestion though...

2.6.24 comes with a new and improved Broadcom wireless driver: **b43** (replaces bcm43xx). **b43** is now capable of 54 Mb/s... bcm43xx was only capable of 11 which is why all of us BCM94311 users preferred to use ndiswrapper.

If you are interested you can look at the OP at Miscellaneous  Fixes...

---

### Post by gindyo on 2008-01-04
> **walkerk said:**
> Glad it worked :) One suggestion though...

2.6.24 comes with a new and improved Broadcom wireless driver: **b43** (replaces bcm43xx). **b43** is now capable of 54 Mb/s... bcm43xx was only capable of 11 which is why all of us BCM94311 users preferred to use ndiswrapper.

If you are interested you can look at the OP at Miscellaneous  Fixes...

thanks for the suggestion, and yes i am interested, but could you please clarify what is "OP at Miscellaneous  Fixes" and where can I find this  animal :)

Edit: sorry for the stupid question I found it

---

### Post by walkerk on 2008-01-04
> **gindyo said:**
> thanks for the suggestion, and yes i am interested, but could you please clarify what is "OP at Miscellaneous  Fixes" and where can I find this  animal :)

One the first post where the script is... there is a section called "Miscellaneous Fixes".. the b43 driver is the first fix. :)

---

### Post by MeanderingCode on 2008-01-04
> **snakeeyes said:**
> This kernel is more stable, upgrade to this kernel as soon as u can.

Is this praise or empirical "fact"?  Why is this, if it is?

Anyway, we're all still having problems with lsusb.  Any leads?

I am still disappointed about the ehci_hcd module problem persisting into this kernel.  I need to unload it every time (i know i could blacklist it...seems like admitting defeat :)) i use usb storage devices and run at 1.1 speed.  Can anyone point me to where i can figure out how to fix this?  It worked on this machine previous to Gutsy!!

Also...i noticed that the machine won't enter suspend under the new kernel, then when i "wake" it from it's screen being blank and locked (not suspended), shuting down the machine via gui just logs me out to gdm's login screen and cmdline 'poweroff' freezes the machine.

Haven't dug into diagnosing the hangup, yet.

---

### Post by lemurian on 2008-01-04
> **MeanderingCode said:**
> 
Anyway, we're all still having problems with lsusb.  Any leads?


Nobody has yet said whether they also see the same problem I do or not.  Note however that USB devices are working fine.  Note also that it is fixable.  Let me quote [my Ubuntu on a Compal IFL90 page](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/):

> 
lsusb no longer works after upgrade. However, USB devices do work. The problem with lsusb is fixable but I have not yet developed an elegant solution for it. If one issues:

```

            $ sudo mount -t usbfs procbususb /proc/bus/usb

```

then the problem is temporarily solved. This would have to be done automatically at boot time but rather than knee-jerkily add the command to the booting scripts, I’d rather investigate more to find whether there is a better fix.


> **MeanderingCode said:**
> 
I am still disappointed about the ehci_hcd module problem persisting into this kernel.  I need to unload it every time (i know i could blacklist it...seems like admitting defeat :)) i use usb storage devices and run at 1.1 speed.  Can anyone point me to where i can figure out how to fix this?  It worked on this machine previous to Gutsy!!

Also...i noticed that the machine won't enter suspend under the new kernel, then when i "wake" it from it's screen being blank and locked (not suspended), shuting down the machine via gui just logs me out to gdm's login screen and cmdline 'poweroff' freezes the machine.

Haven't dug into diagnosing the hangup, yet.

Yikes!  I can't help with those.

---

### Post by RaZoR1394 on 2008-01-04
> **walkerk said:**
> Make a backup copy of xorg.conf and then boot into recovery mode (Press ESC at boot) and then execute the following:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
```
sudo reboot
```

?

Thanks but it seems I'm stuck with the "nv" driver. With your help I got this driver to work but as soon as I switch over to nvidia it won't work.

I've attached the logfile from Xorg (it seems that the "no matching device" was just a warning, the error is different).

Here's a snippet:

> 
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.


---

### Post by walkerk on 2008-01-04
> **RaZoR1394 said:**
> Thanks but it seems I'm stuck with the "nv" driver. With your help I got this driver to work but as soon as I switch over to nvidia it won't work.

I've attached the logfile from Xorg (it seems that the "no matching device" was just a warning, the error is different).

Here's a snippet:

Unfortunately I don't have an nVidia card so I don't have experience with it. I would suggest using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install nVidia drivers... perhaps this will have a better outcome. Of course after running the Envy script you'll need to reboot...

You can think of a module like a driver... If its not loaded correctly your hardware will not be recognized...

---

### Post by lemurian on 2008-01-04
> **RaZoR1394 said:**
> Thanks but it seems I'm stuck with the "nv" driver. With your help I got this driver to work but as soon as I switch over to nvidia it won't work.


Here are a couple questions that may help circumscribe the problem:

1. How did you install the nVidia closed-source driver before?  Using Envy?  Using the Restricted Driver Manager bundled with Ubuntu?

2. What is the output of:

```

$ dpkg -l nvidia-glx-new

```

---

### Post by snakeeyes on 2008-01-04
I think I should be able to help out Nvidia users.

Ok make sure u have set GRUB to boot from the first default kernel. 

If u r using the nvidia-glx-new package from the Gutsy repos then leave it that way. If u used Envy to install the nvidia drivers then uninstall them right now and reconfigure xsever to use the vesa drivers instead. If u can't boot using vesa then use the nv drivers.

I suggest that u don't use the script to update to the latest kernel cause while installing the nvidia drivers it also installs another, I don't know why, it could be a bug but I noticed without that 386 kernel the nvidia drivers won't work.

In terminal type:
sudo nano /etc/apt/sources.list

Add this repository at the end:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

sudo apt-get update

Now install the new kernel first:

sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic

Now reboot into the new kernel, GRUB should be automatically configured to boot from it if u never made changes to GRUB otherwise just make sure that the default boot kernel is "0" which is 2.6.24-2-generic.

After u boot into the new kernel then people who had previously removed the nvidia drivers using envy should boot up with vesa and one using nvidia-glx-new should boot up with those without problems. In case u do have problems then reconfigure xserver to use vesa instead.

Now envy users can again use envy to install the nvidia drivers and configure xserver to use them and they r ready. Just make sure to manually remove Hardy's sources from ur sources.list.

Those who want to update to the latest nvidia drivers using Hardy's repository should now type in the terminal:

sudo apt-get install nvidia-glx-new

This is where I noticed that it will install the 2.6.24-2-386 kernel with the drivers. Anyway continue with installation and now reboot using the default kernel the nvidia drivers downloaded with it so u should be booting up into kernel 2.6.24-2-386.

Check if everything works fine. It should work ok. Now change ur GRUB configuration file to boot from kernel 2.6.24-2-generic which is the kernel u actually installed. It was the 3rd in my GRUB list so I set the default value from 0 to 2. Remember GRUB starts counting from 0.

Now when I rebooted, here is where the problem began, kernel 2.6.24-2-generic would boot ok, but xserver would never load and there was a continuous blinking line on the left side of my screen.

I presses alt+ctrl+del ad rebooted the machine and gave it another try and the same thing happened. I rebooted again and tried to boot into my previous 2 kernels which were kernel 2.6.22-14 and 2.6.22-12. They wouldn't boot either though I could perfectly boot into the 386 kernel nvidia drivers installed. I tried booting into the generic kernel again for the 3rd time and it started working. I haven't had any problem since so I think the nvidia drivers still have some bugs in them. You just have to try 3 or 4 times to boot into this kernel if u encounter this problem though its not important that u will face it, so don't worry.

The new kernel is excellent and solved most of previous power management issues, freezes, and also a bug where my hard disk would start screaming or something making really loud noises was also fixed in this kernel.

It is a lot more stable.

Hope this helps u nvidia users.

:)

---

### Post by ST.x on 2008-01-04
> **lemurian said:**
> Nobody has yet said whether they also see the same problem I do or not.  Note however that USB devices are working fine.  Note also that it is fixable.  Let me quote [my Ubuntu on a Compal IFL90 page]("http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/"):

Yes, same here usb devices are working but not the lsusb command.

---

### Post by lemurian on 2008-01-04
> **ST.x said:**
> Yes, same here usb devices are working but not the lsusb command.
Ok, so it's not just me.  Judging by the kernel activity in launchpad, I think they are about to release a new hardy kernel so I'm going to wait for that release.  If the bug remains, I'll package a deb that can be installed to provide a temporary solution.

---

### Post by crazyness003 on 2008-01-05
**Multi-info post!**
**#1**> **Kyran said:**
> 
What model is it?


Hey, just wanted to let you know.

Its an HP Pavilion tx1308nr tablet laptop.
AMD Turion64 x2
nVidia Geforce 6150 Go
Broadcom BCM94311MCG wlan mini-PCI BCM

It originaly shipped with 'doze Vista. **Immediately** got rid of that.
Then installed XP... it got boring, so here I am.
So far I can't get my Wi-Fi, Webcam and Touch Screen to work.

when i do ```
sudo lshw -C cpu
``` for capabilities i get
```
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 **apic** sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq

```

Apic is right in there but idk. As long as I get added performance, this thing is on fire when it comes to speed, esp now with gnu/linux

**#2** I modded the script and installed the new kernel, might have been one of those once-in-a-lifetime bug where it actually helped. hopee it helpes others.

**#3** Can anyone help me with my Broadcom Wireless card. I cant even seem to turn it on anymore. Before at leased I would get the thing on for about a min or two using the bcm43xx in gutsy. But now It wont come on.
Also, the driver for non-legacy cards on the [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) website is busted. 
The file from [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2) wont extract and the b43-fwcutter wont deal with it either.
On their website it sais to extract the firmware like so:
```

sudo b43-fwcutter -w /lib/firmware wl_apsta.o

```
But *wl_apasta.o* is no where to be found.
I used the legacy one, but it no work.

Any help is useful

on a side note: its interesting how different conversations are happening at once. pretty cool.

Anyway, thanks for everything. The new kernel did get my sound running. Thats a double+ for me. And I thank you guys for that.

---

### Post by walkerk on 2008-01-05
> **crazyness003 said:**
> **Multi-info post!**
**#1**

Hey, just wanted to let you know.

Its an HP Pavilion tx1308nr tablet laptop.
AMD Turion64 x2
nVidia Geforce 6150 Go
Broadcom BCM94311MCG wlan mini-PCI BCM

It originaly shipped with 'doze Vista. **Immediately** got rid of that.
Then installed XP... it got boring, so here I am.
So far I can't get my Wi-Fi, Webcam and Touch Screen to work.

when i do ```
sudo lshw -C cpu
``` for capabilities i get
```
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 **apic** sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq

```

Apic is right in there but idk. As long as I get added performance, this thing is on fire when it comes to speed, esp now with gnu/linux

**#2** I modded the script and installed the new kernel, might have been one of those once-in-a-lifetime bug where it actually helped. hopee it helpes others.

**#3** Can anyone help me with my Broadcom Wireless card. I cant even seem to turn it on anymore. Before at leased I would get the thing on for about a min or two using the bcm43xx in gutsy. But now It wont come on.
Also, the driver for non-legacy cards on the [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) website is busted. 
The file from [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2) wont extract and the b43-fwcutter wont deal with it either.
On their website it sais to extract the firmware like so:
```

sudo b43-fwcutter -w /lib/firmware wl_apsta.o

```
But *wl_apasta.o* is no where to be found.
I used the legacy one, but it no work.

Any help is useful

on a side note: its interesting how different conversations are happening at once. pretty cool.

Anyway, thanks for everything. The new kernel did get my sound running. Thats a double+ for me. And I thank you guys for that.

Which Broadcom driver are you needing? 4311, 09? 
```
lspci | grep Network
```
```
lshw -C network
```

Im sure you are not using a legacy chip so you'll definitely need straight b43 and the correct firmware (I can point you in the right direction with some info)

---

### Post by BC7333 on 2008-01-05
Regarding strange shutdowns, I also have this problem from time to time.

Although quite 'fuzzy', it seems to happen **only** when the laptop is charging.  Also noticed frequently was using the right shift key.

A bit inconvenient, but all in all happy with the new kernel.

Still haven't figured out the wireless light issue.  Anyone try [http://bughost.org/bugzilla/show_bug.cgi?id=1209](http://bughost.org/bugzilla/show_bug.cgi?id=1209) ?

---

### Post by snakeeyes on 2008-01-05
Hey can anyone give me the link where the bug report about "lsusb" not giving any output has been filed. Thanks!

---

### Post by lemurian on 2008-01-05
> **snakeeyes said:**
> Hey can anyone give me the link where the bug report about "lsusb" not giving any output has been filed. Thanks!
No bug report about lsusb and /proc/bus/usb should be filled.

The Ubuntu developers do not want bugs reported against bizarro installations.  Running a Hardy kernel in Gutsy is not something they support.  For all we know, the problem may be absent for somebody running whatever alpha version of Hardy is available.   That is, maybe upgrading the initscripts package or the usbutils package to the current version of those packages available in Hardy would fix the bug.

I'm going to mount /proc/bus/usb manually for now and wait for the next kernel release (which, judging from launchpad activity, looks like it will happen really soon).  If the next kernel release still shows the bug, I will inquire among the developers whether /proc/bus/usb is deprecated or something.

---

### Post by snakeeyes on 2008-01-05
thanks, but there is no danger right cause all my devices work though so do u think I should be worried?

---

### Post by walkerk on 2008-01-05
> **snakeeyes said:**
> thanks, but there is no danger right cause all my devices work though so do u think I should be worried?

As long as your USB devices are working properly you need not worry about lsusb not reporting any devices... lsusb is a tool to list devices, it doesn't actually handle the devices...

---

### Post by snakeeyes on 2008-01-05
ok thanks

---

### Post by crazyness003 on 2008-01-06
> **walkerk said:**
> Which Broadcom driver are you needing? 4311, 09? 
```
lspci | grep Network
```
```
lshw -C network
```

Im sure you are not using a legacy chip so you'll definitely need straight b43 and the correct firmware (I can point you in the right direction with some info)

Hello, sorry took so long.
```
lspci | grep Network:
03:00.0 Network controller: Broadcom Corporation BCM9**4311**MCG wlan mini-PCI (rev 02)

```

and

```
lshw -C network:
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: **BCM94311MCG wlan mini-PCI**
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: **driver=b43-pci-bridge** latency=0 module=ssb

```

I need the  straight b43 driver, but i was testing my luck with the legacy. I just cant find a working driver file. I guess its supposed to end with ** xx.xx.o **
I downloaded **broadcom-wl-4.80.53.0.o** from the linuxwireless.org site bbut I think I need one that looks like this:
**wl_apsta.o**

Any help is roxor

btw: I installed Wicd and I have to manualy connect to my hardwire everytime i log in. And the little icon in the tray is just blank. It wont even run the program when i click it, or show any infor when I hover over it. 
Is that bad?
Also, ever so often the program auto launches its-self. Mayby its remembering all the clicks i made earlier in the session. Its no big prob. if all else fails i'll go back to Network Manager.

---

### Post by walkerk on 2008-01-06
> **crazyness003 said:**
> Hello, sorry took so long.
```
lspci | grep Network:
03:00.0 Network controller: Broadcom Corporation BCM9**4311**MCG wlan mini-PCI (rev 02)

```

and

```
lshw -C network:
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: **BCM94311MCG wlan mini-PCI**
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: **driver=b43-pci-bridge** latency=0 module=ssb

```

I need the  straight b43 driver, but i was testing my luck with the legacy. I just cant find a working driver file. I guess its supposed to end with ** xx.xx.o **
I downloaded **broadcom-wl-4.80.53.0.o** from the linuxwireless.org site bbut I think I need one that looks like this:
**wl_apsta.o**

Any help is roxor

btw: I installed Wicd and I have to manualy connect to my hardwire everytime i log in. And the little icon in the tray is just blank. It wont even run the program when i click it, or show any infor when I hover over it. 
Is that bad?
Also, ever so often the program auto launches its-self. Mayby its remembering all the clicks i made earlier in the session. Its no big prob. if all else fails i'll go back to Network Manager.

1. Ensure you have the b43-fwcutter
```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy universe' | sudo tee /etc/apt/sources.list.d/fwcutter.list

sudo apt-get update

sudo apt-get install b43-fwcutter

sudo rm /etc/apt/sources.list.d/fwcutter.list

sudo apt-get update
```

2. Download the firmware
```
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
```

3. Unzip it...
```
tar -xvjf broadcom-wl-4.80.53.0.tar.bz2
```

4. Go there...
```
cd broadcom-wl-4.80.53.0
```

5. Now install the firmware
```
For b43: 'sudo b43-fwcutter -w /lib/firmware wl_apsta.o'
```

---

### Post by crazyness003 on 2008-01-06
> **walkerk said:**
> 1. Ensure you have the b43-fwcutter

2. Download the firmware

3. Unzip it...

4. Go there...

5. Now install the firmware

1.done
2.done twice
3.done twice
4.done than double checked to make sure they're in the right place

Tried it all. The fwcutter is the latest, finnaly got the .tar.bz2 file to extract. Had some probs at first. The file wouldnt extract. then the wl_apsta.o file was in another folder. It extracted it in a sub-folder called kmod. I did manage to get the .fw files copied to /lib/firmware/b43, but its still not working. 
I did changed the alias for my wireless mac address to wlan0, maybe thats the problem.
Also, should I have the broadcom firmware in the restricted drivers "in use" or "not in use". Right now they're not in use, maybe i gotta turn thems on?
::Too much to go wrong::
Sorry to such a downer, but nothing seems to be working. I bet i'm missing a semi-colon somewhere ;) Thats why its not working.
Thanks again

---

### Post by RaZoR1394 on 2008-01-07
I upgraded fully to Hardy itself and now my nVidia issues are gone. Wireless also works better than ever. Forget ndiswrapper. :popcorn:

---

### Post by cRoW2k on 2008-01-08
As your's past Guide (from Feisty2Gutsy), it works perfectly on my ASUS X53Sa (with ATI HD 2600)

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9581
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
08:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Wlan, Audio, ATI (driver reinstalled with ENVY) works all

---

### Post by walkerk on 2008-01-08
> **cRoW2k said:**
> As your's past Guide (from Feisty2Gutsy), it works perfectly on my ASUS X53Sa (with ATI HD 2600)

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9581
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
08:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Wlan, Audio, ATI (driver reinstalled with ENVY) works all

Glad to hear it :)

---

### Post by wolfear on 2008-01-08
I did the kernel upgrade, then went ahead with a full dist upgrade(on top of a clean Gutsy installation) and so far, just about everything seems to be working fine.

This even fixed the system lockups I was having under Gutsy (whoohoo!).

---

### Post by Xan63 on 2008-01-09
Hi everybody,

I successfully upgraded to the new kernel, but I'm experiencing the wireless interface renaming bug. But my wireless network is working.

I have tried the Miscellaneous Fixes for my eth1 wireless, without effect.
The ipw3945 is in the "Closed driver manager", but signaled as "Not used"

Here is the results of iwconfig 

> xan@Vitty:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0_rename  no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:"wlan-etudiants"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0B:86:2B:2B:14   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=90/100  Signal level=-41 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig results:

> xan@Vitty:~$ ifconfig
eth1      Lien encap:Ethernet  HWaddr 00:16:D4:DD:E0:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:17 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)

wlan0_ren Lien encap:Ethernet  HWaddr 00:1B:77:3D:56:85  
          inet adr:10.41.4.174  Bcast:10.41.255.255  Masque:255.255.0.0
          adr inet6: fe80::21b:77ff:fe3d:5685/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:23593 erreurs:0 :0 overruns:0 frame:0
          TX packets:5276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:8685238 (8.2 MB) Octets transmis:1473335 (1.4 MB)

wmaster0_ Lien encap:UNSPEC  HWaddr 00-1B-77-3D-56-85-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)



I'd like to know if there any possibility to use the ipw3945 driver, because it seems that Monitor mode is not working with the new driver...

thank you a lot!

Cheers

---

### Post by lemurian on 2008-01-09
I ran the script again this morning and I'm now at:

```
Linux bodhi 2.6.24-3-generic #1 SMP Thu Jan 3 23:30:29 UTC 2008 i686 GNU/Linux
```

The problem with /proc/bus/usb not being mounted is still present so I will try to get better information about what the deal is with that.

---

### Post by walkerk on 2008-01-09
> **Xan63 said:**
> Hi everybody,

I successfully upgraded to the new kernel, but I'm experiencing the wireless interface renaming bug. But my wireless network is working.

I have tried the Miscellaneous Fixes for my eth1 wireless, without effect.
The ipw3945 is in the "Closed driver manager", but signaled as "Not used"

Here is the results of iwconfig 



ifconfig results:



I'd like to know if there any possibility to use the ipw3945 driver, because it seems that Monitor mode is not working with the new driver...

thank you a lot!

Cheers

Try this...

1. Backup 
```
sudo cp /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.back
```

2. Delete it. At boot this file will be recreated without the remains from the kernel upgrade and iftab
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

3. Reboot

This will keep mac80211 from using wlan0 thus forcing your actual NIC from being renamed wlan0_rename. *It does work*

For some crazy reason you need to recover just replace the backed up file.

---

### Post by Syron Nightshade on 2008-01-09
I also updated successfully to the new hardy kernel. :cool:

Everything seems stable and faster. The important thing for me is that my wacom tablet seems more responsive and precise to pressure than before and Gimp doesn't  lag anymore when using the tablet :-D

So, thank you walkerk for your excellent guide :D

---

### Post by walkerk on 2008-01-10
No problem :)

---

### Post by Gigamo on 2008-01-10
Just reporting in that upgrading from 24-2 to 24-3 with the same script worked flawlessly. I just had to run envy again. No wireless issues this time :)

---

### Post by crazyness003 on 2008-01-10
I have a simple question:
In order to do a **full** hardy upgrade, do i need to download the latest daily build ISO from the website and reinstall? Or does running the script do this automatically?

Just wondering what a full upgrade means.

---

### Post by RaZoR1394 on 2008-01-11
> **crazyness003 said:**
> I have a simple question:
In order to do a **full** hardy upgrade, do i need to download the latest daily build ISO from the website and reinstall? Or does running the script do this automatically?

Just wondering what a full upgrade means.

There's no need to use the disc. It's cleaner to do a full format as always but I didn't find it necessary.

Please check the sticky in the Hardy forum.

[http://ubuntuforums.org/showthread.php?t=600644](http://ubuntuforums.org/showthread.php?t=600644)

I just opened /etc/apt/sources.list with gedit and used the replace feature to replace all "gutsy" entries with "hardy".

edit:

Remember Hardy seems to have some problems. I can't create a user normally for ex. I have to use the command line. The wired NIC is not working in our A6T laptop. The proprietary driver for my touchscreen driver also doesn't work. But the almost perfect b43 module for broadcom NIC's and the ability to shut down cleanly is enough for me to switch. Even ndiswrapper crashes (or maybe It's the Windows driver).

---

### Post by lemurian on 2008-01-11
Ok, somebody running an alpha of Hardy told me that for him.

1. lsusb works normally.

2. ls -l /proc/bus/usb returns nothing

3. mount | grep usb returns nothing

This suggests that the procbususb filesystem is being phased out.  I'll seek further confirmation from the Hardy release of usbutils and ask the people packaging the kernel.  

I mentioned before that the solution is as simple as issuing:

```

$ sudo mount -t usbfs procbususb /proc/bus/usb/

```

but for my own needs I will want to make a installable package out of this.  For traceability, robustness and documentation purposes I prefer that to just shoving the mount into some pre-existing booting script.

---

### Post by jdc on 2008-01-11
I just tried running the script on my Macbook Pro using the nvidia-glx-new drivers, and when I tried to reboot into the new kernel, it stopped while starting sshd. I switched to a new virtual terminal and logged in as root, and several commands (e.g. iwconfig and ifconfig) froze and couldn't be killed.  I killed the S16ssh init script, and the boot process continued to the next item, cups, and that one froze too.

Any suggestions for how to work around this?  I'm guessing it is network related, but I'm not sure.  I use ndiswrapper as the madwifi driver has problems with my Atheros AR5418 card.  ndiswrapper did complain in dmesg about ath0 already being taken, something it doesn't complain about with the gutsy kernel.

Thanks for any help,

Dan

---

### Post by lemurian on 2008-01-11
As I suspected the usb issue is not a bug.  The fact is that /proc/bus/usb will be phased out in Hardy.  It will be replaced by /dev/bus/usb.  The reason lsusb is failing is that in Hardy udev is responsible for managing /dev/bus/usb but the udev which ships with Gutsy is too old.

If someone wants to test installing Hardy's udev in Gutsy and check whether the resulting system works well or not, go for it.  I'm a bit reluctant to do it myself as I don't want other things to start failing mysteriously.

---

### Post by ThrasherSC2K2 on 2008-01-11
First of all, thx for thie really great how to, helps a lot.

I just noted that VMWare still refused to compile, even after installing the g++ package. Afterwards ich checked gcc --version and g++ --version and noted that g++ still had the old Version.

So I just reenabled the Hary Repo and installed g++ as well, as it hasnt been done before.

Finaly I compiled Vmware and afterwards used the anyany15a Patch (dont know if the official unofficial anyany15 will work as well).

Hope I wasnt the only one with this Problem. :)

---

### Post by dcstar on 2008-01-11
Installing the Hardy kernel was a major problem for me, it changed all my PATA IDE hard drive designations from /dev/hd to /dev/sd because it uses the newer SCSI emulation driver setting in the kernel configuration - therefore things were majorly mucked up in everything that used the old designations.

Various hdparm commands also no longer work with this setup, so that was an additional problem.

Changing them to /dev/sd was not an option, as it meant the dual booting to the current Gutsy kernel would then have the same problems.

---

### Post by walkerk on 2008-01-12
> **dcstar said:**
> Installing the Hardy kernel was a major problem for me, it changed all my PATA IDE hard drive designations from /dev/hd to /dev/sd because it uses the newer SCSI emulation driver setting in the kernel configuration - therefore things were majorly mucked up in everything that used the old designations.

Various hdparm commands also no longer work with this setup, so that was an additional problem.

Changing them to /dev/sd was not an option, as it meant the dual booting to the current Gutsy kernel would then have the same problems.

Sorry to hear it...

Try removing the kernel and then re-installing 2.6.22-14 through synaptic. I would think this would fix the problem until you can figure out a fix...

---

### Post by Leno. on 2008-01-12
Great guide, it helped me alot with my network card not working with WPA, but there are some problems; mainly that I am not able to launch openoffie in a proper manner.

I can not click an ODT-file and expect it to open, neither can i click it in the menu. However, if i run it in the terminal _without any parameters_ i can make it run.

Error:
> Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'

This is making me insane, can somebody give some more information about this issue?

---

### Post by lemurian on 2008-01-12
> **Leno. said:**
> Great guide, it helped me alot with my network card not working with WPA, but there are some problems; mainly that I am not able to launch openoffie in a proper manner.

I can not click an ODT-file and expect it to open, neither can i click it in the menu. However, if i run it in the terminal _without any parameters_ i can make it run.

Error:


This is making me insane, can somebody give some more information about this issue?
This is quite perplexing.  I run Gutsy.  I upgraded to the Hardy kernel with the help of walkek's script and I run openoffice w/o any problem.  To see whether we can come up with a solution, tell us:

1. What is it exactly you type in the terminal to start openoffice?

2. What is the output of:

```

$ ls -l /usr/lib/openoffice/program/soffice

```

---

### Post by Leno. on 2008-01-12
1. > openoffice --writer (doesn't work)
openoffice (works)

2.> -rwxr-xr-x 1 root root 9226 2007-11-28 05:11 /usr/lib/openoffice/program/soffice

---

### Post by RaZoR1394 on 2008-01-12
> **dcstar said:**
> Installing the Hardy kernel was a major problem for me, it changed all my PATA IDE hard drive designations from /dev/hd to /dev/sd because it uses the newer SCSI emulation driver setting in the kernel configuration - therefore things were majorly mucked up in everything that used the old designations.

Various hdparm commands also no longer work with this setup, so that was an additional problem.

Changing them to /dev/sd was not an option, as it meant the dual booting to the current Gutsy kernel would then have the same problems.

Have you tried UUID instead of for ex /dev/sda?

---

### Post by lemurian on 2008-01-12
Leno, the date on your soffice file is different than mine.  I do not know right off the bat whether this is indicative of a problem or not.  (For instance, if the postrm scripts touch soffice after installation, then it is not a problem.)  What is the output of the following commands?

1. 

```

$ dpkg-query -W openoffice.org-common

```

2.

```

$ md5sum /usr/lib/openoffice/program/soffice

```

3.

```

$ dpkg-query -W openoffice.org-writer

```

---

### Post by Leno. on 2008-01-13
1.> openoffice.org-common   1:2.3.0-1ubuntu5.3

2.> 27503ff99693184e58d9d119b8b0f0e0  /usr/lib/openoffice/program/soffice
3.> openoffice.org-writer   1:2.3.0-1ubuntu5.3
:-)

---

### Post by MozartlovesUbun2 on 2008-01-13
HI ya
thank you for this guide i will try it and post the results here.

please if someone can answer this

One question: I put put on the Alpha 2 version on Hardy on a laptop for testing, so how do i update it? (as wireless is not working),  i am downloading the Alpha 3 right now on to a different PC, so can i update directly from the new cd or do i have to do fresh reinstalls of each alpha release every time?

so which is it, will Hardy keep updating itself normally through all the stages up until the final stable release, or do I have to download each and every alpha and do fresh reinstalls?

thanks

---

### Post by ST.x on 2008-01-13
> **MozartlovesUbun2 said:**
> HI ya
thank you for this guide i will try it and post the results here.

please if someone can answer this

One question: I put put on the Alpha 2 version on Hardy on a laptop for testing, so how do i update it? (as wireless is not working),  i am downloading the Alpha 3 right now on to a different PC, so can i update directly from the new cd or do i have to do fresh reinstalls of each alpha release every time?

so which is it, will Hardy keep updating itself normally through all the stages up until the final stable release, or do I have to download each and every alpha and do fresh reinstalls?

thanks
Im pretty sure if you installed from the releases then they should update like normal releases. I think the alpha 3 has a newer kernel than what we have using this script at the moment.

---

### Post by Hero of Time on 2008-01-13
I also updated the kernel, but am having troubles with my ati graphic driver. When I follow the binaryhowto/ati I get errors. I am currently stuck at CLI. Wlan also doesn't work as I have the damn rename error, while I renamed the first name of my ifaces. It was eth1 for wireless, changed that to wlan but now its wlan0_rename. I will try the removal of the 70-persistent-net.rules file. It's not my first concern, I still have a working lan device. My priority is my video driver.

What I did to update is the manual method. I checked of the packages that I had installed that needed the hardy version. That ended up on only the kernel-header, kernel-image and kernel-restricted-modules (along with normal modules, just in case). I had X running with graphical support, but now not anymore. I changed something yesterday and am now screwed.
I follow the driver howto, bash ./atidriver.run, dpkg -i fglxr-kernel-source, dpkg -i xorg-driver, all fine till then. Then when I need the M-A things, it's when it goes wrong. With m-a prepare,update it finishes successfully. But m-a build,install fglrx-kernel, I get the following error:
```
The source tarball could not be found!
Package fglrx-kernel-source not installed? (strange, since it got just installed)
Running "m-a -f get fglrx-kernel-source" may help. (doesn't do anything)
Target package file /urs/src/fglrx-kernel-2.6.24-4-generic......deb already exists, not rebuilding!
(however, you could use the -f switch to ignore it) (how do I use -f and -i in dpkg together, I get errors on that about invalid switches)
I: Direct installation failed, trying to post-install the dependencies

Default stuff about apt things, but then the following:
The following packages will be REMOVED:
fglrx-kernel-2.6.24-4-generic (this one needs to be installed, then why remove it?)
Do you want to continue [Y/n]?
```

When I hit enter or type Y to remove it, it sasy this:
```
Removing fglrx-kernel-2.6.24-4-generic ...
And puts me back at the prompt. Apt-get remove the package says it's not installed. When I run the m-a build,install again, the same question comes over and over. I do get other errors in the middle.
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.24....:
fglrx-kernel-2.6.24.... depends on xorg-driver-fglrx (= 8.433-1); however
Version of xorg-driver-fglrx on system is 8.443.1-1.
dpkg: error processing fglrx-kernel-2.6.24-4-generic (--install):
dependency problems - leaving unconfigured
Error were encountered while processing:
fglrx-kernel-2.6.24-4-generic
```

Now that I think about it, 433 is 7.11 ati driver, but I want the 7.12. Any idea on how to get it running on the propretary ati driver? Or is the xorg driver in the repo the ati one?

Edit:
Ok, I removed the 70-persistent-net.rules file, got my wireless just fine back again. But with an additional interface, wmaster0, which isn't seen in the rules file. I just hope everything will still work in the gutsy kernel. After the reboot, X also worked again. I'm no trying the 7.11 driver which I kept just in case. Will report again.

edit2:
Driver installed fine, but running on Mesa. Aticonfig --initial gives 'Found fglrx primary device section. Nothing to do, terminating.'
Wifi does show up, does associate but doesn't work with WPA. On boot, I got an error about padlock-aes.ko not found or something. That would indicate that the WPA module isn't loaded. Also PowerNowd gave some errors too not able to load or find files. I guess the whole file location is different in Hardy.

Edit 3:
Found the padlock_aes error, need the aes_generic module. However, I now have another problem. Somehow, my wpa_supplicant doesn't work anymore. I get the error:
```
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - 
```
Now what? How to solve this?

But first, I have to check if the Gutsy kernel still works.

---

### Post by Gigamo on 2008-01-13
So is 24-4 out?

---

### Post by lemurian on 2008-01-13
Leno, the results you post are all as expected.  What is the output of:

```

$ dpkg-query -W openoffice.org-core

```

I'm starting to think you have a setup which triggers some sort of obscure memory management problem.  I have for evidence this post:

[http://www.mail-archive.com/debian-openoffice@lists.debian.org/msg15514.html](http://www.mail-archive.com/debian-openoffice@lists.debian.org/msg15514.html)

The situation described there is different than yours.  The poster is saying that if MALLOC_PERTURB_ is at all set then **openoffice does not run at all.**  He's also saying that the problem he uncovered is good evidence that openoffice does not manage its memory properly.  You might have stumbled onto a different but related problem.  Memory management problems are notoriously hard to debug so you might want to return to a vanilla Gutsy installation and wait for Hardy to be officially released.

If you want to continue pursuing this issue, what I would do next is create a new user for testing purposes.  Then I would log into my system as that user and see whether I can run openoffice normally as that user.  Doing this allows to determine whether the problem is user-specific or system-wide.

---

### Post by Hero of Time on 2008-01-13
> **Gigamo said:**
> So is 24-4 out?
Yes, 24-4 is out. When I was working in that kernel, I somehow screwed up my 22-14 kernel. No wifi, no ntfs for normal user rights, mouse wasn't working at the start. All kinds of crazy stuff. Bridge was also gone.
Another thing, I think my sound didn't work in 24-4. Anyone got the stuff working I'm having problems with? I have the Fujitsu-Siemens Amilo Pi 1536, intel pro wireless 3945, ati x1400.

Also, when I tried to install the 7.12 driver for my 22-14 kernel, I got the same errors as with the 24-4.

Edit:
Got most stuff working again in my 22-14 kernel. Only thing left is the video driver, that stays at mesa.

---

### Post by AvitarX on 2008-01-13
I'm having the same problem as Leno with the same results.

I have not found a chance, but wanted to let those interested know thatthere is someone else, and also hope for a solution.

I do have uninstallable updates to OO.o waiting for version 2.3.1, but the openoffice-core package for that version is un-available.


----editing ten minutes after post----

I would like to add if I run the command openoffice, I can then double click (after assigning the file types) on a .odt file and it will open.

---

### Post by lemurian on 2008-01-13
> **AvitarX said:**
> I'm having the same problem as Leno with the same results.

I have not found a chance, but wanted to let those interested know thatthere is someone else, and also hope for a solution.

I do have uninstallable updates to OO.o waiting for version 2.3.1, but the openoffice-core package for that version is un-available.


----editing ten minutes after post----

I would like to add if I run the command openoffice, I can then double click (after assigning the file types) on a .odt file and it will open.
If OO.o 2.3.1 is a candidate for installation on your machine there is definitely something wrong because 2.3.1 is available only for Hardy.  See this page:

[https://launchpad.net/ubuntu/+source/openoffice.org](https://launchpad.net/ubuntu/+source/openoffice.org)

The script developed by walkerk temporarily adds the Hardy repository to your apt configuration, upgrades your kernel (and associated files) and then removes the Hardy repository from your apt configuration.  If you do it manually instead of using his script, the idea is the same.  After everything is done, no Hardy-specific packages should be available for installation so you should not get OO.o 2.3.1 as an installation candidate.

One way to check the version of all OO.o packages on your system is to run:

```

$ dpkg-query -W "openoffice.org*" | gawk '$2 { print;}'

```

On my system, I get:

```

openoffice.org  1:2.3.0-1ubuntu5.3
openoffice.org-base     1:2.3.0-1ubuntu5.3
openoffice.org-calc     1:2.3.0-1ubuntu5.3
openoffice.org-common   1:2.3.0-1ubuntu5.3
openoffice.org-core     1:2.3.0-1ubuntu5.3
openoffice.org-dev      1:2.3.0-1ubuntu5.3
openoffice.org-draw     1:2.3.0-1ubuntu5.3
openoffice.org-evolution        1:2.3.0-1ubuntu5.3
openoffice.org-filter-mobiledev 1:2.3.0-1ubuntu5
openoffice.org-gnome    1:2.3.0-1ubuntu5.3
openoffice.org-gtk      1:2.3.0-1ubuntu5.3
openoffice.org-help-en-gb       1:2.3.0-1ubuntu2
openoffice.org-help-en-us       1:2.3.0-1ubuntu2
openoffice.org-help-fr  1:2.3.0-1ubuntu2
openoffice.org-help-hi-in       1:2.3.0-1ubuntu2
openoffice.org-help-zh-cn       1:2.3.0-1ubuntu2
openoffice.org-help-zh-tw       1:2.3.0-1ubuntu2
openoffice.org-hyphenation      0.2
openoffice.org-impress  1:2.3.0-1ubuntu5.3
openoffice.org-java-common      1:2.3.0-1ubuntu5.3
openoffice.org-l10n-common      1:2.3.0-1ubuntu2
openoffice.org-l10n-en-gb       1:2.3.0-1ubuntu2
openoffice.org-l10n-en-us       1:2.3.0-1ubuntu5.3
openoffice.org-l10n-en-za       1:2.3.0-1ubuntu2
openoffice.org-l10n-fr  1:2.3.0-1ubuntu2
openoffice.org-l10n-hi-in       1:2.3.0-1ubuntu2
openoffice.org-l10n-zh-cn       1:2.3.0-1ubuntu2
openoffice.org-l10n-zh-tw       1:2.3.0-1ubuntu2
openoffice.org-math     1:2.3.0-1ubuntu5.3
openoffice.org-style-andromeda  1:2.3.0-1ubuntu5.3
openoffice.org-style-crystal    1:2.3.0-1ubuntu5.3
openoffice.org-style-default    1:2.3.0-1ubuntu5.3
openoffice.org-style-human      1:2.3.0-1ubuntu5.3
openoffice.org-style-industrial 1:2.3.0-1ubuntu5.3
openoffice.org-style-tango      1:2.3.0-1ubuntu5.3
openoffice.org-thesaurus-en-us  1:2.2.0-2ubuntu1
openoffice.org-writer   1:2.3.0-1ubuntu5.3

```

Some packages are optional and won't appear on your system but my system is up to date with regard to OO.o as published for Gutsy so your versions should correspond to mine if your system is up to date but should not be higher.

---

### Post by HeWhoE on 2008-01-13
I upgraded with no serious detriment.  Here are some of the issues I've noticed, so far.

-- When the kernel is loading, it complains about AppArmor.

-- The Master sound volume control still doesn't work (hasn't worked since I upgraded to Gutsy).  

-- When I open gnome-volume-control, the volume slider won't slide where I want it to go.  

Here are my system specs:

**Compaq Presario C300**
Celeron M CPU: 430 @ 1.73 GHz
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Audio controller: Intel 82801G (ICH7 Family)

---

### Post by jdc on 2008-01-14
> **jdc said:**
> I just tried running the script on my Macbook Pro using the nvidia-glx-new drivers, and when I tried to reboot into the new kernel, it stopped while starting sshd. I switched to a new virtual terminal and logged in as root, and several commands (e.g. iwconfig and ifconfig) froze and couldn't be killed.  I killed the S16ssh init script, and the boot process continued to the next item, cups, and that one froze too.

Any suggestions for how to work around this?  I'm guessing it is network related, but I'm not sure.  I use ndiswrapper as the madwifi driver has problems with my Atheros AR5418 card.  ndiswrapper did complain in dmesg about ath0 already being taken, something it doesn't complain about with the gutsy kernel.


I just tried 24-4, and the machine boots fine and the wireless network is also working fine.  Suspend to ram seems more reliable, and for the first time I have a working microphone (had to check the Rec box below one of the "capture" slides in gnome-alsamixer).  I still can't use hibernate/suspend to disk.

This is on a Macbook Pro C2D Santa Rosa.

Dan

---

### Post by ST.x on 2008-01-14
hmm when I run the script it doesnt say there is an update to 24-4.

---

### Post by Hero of Time on 2008-01-14
Check the repo with Synaptic.

I have a question. Since I kinda screwed things up, I removed the kernel and gone back to how things were. But since Hardy doesn't use the ipw3945 module anymore and switched to iwl3945, I can't use wpa_supplicant anymore. I changed to iwl3945 module on my gutsy kernel too, so I want to get this fixed before I go check the Hardy kernel again. See my post on the previous page about the error from wpa_supplicant. It has something to do with using WEXT as driver for wpa_supplicant. My SSID is hidden btw.

---

### Post by jdc on 2008-01-14
> **ST.x said:**
> hmm when I run the script it doesnt say there is an update to 24-4.

I installed the 24-4 kernel packages manually.

---

### Post by stefanst on 2008-01-14
I upgraded from Gutsy to the Hardy Kernel and am VERY happy with it. One small problem seems to exist with the SCSI emulation though.

I have two HDDs and one DVD installed:
- One old 40GB IDE drive that I boot from and that contains the root tree. This is the master on the IDE) interface0
. One DVD-R/W that is the master on IDE1
- One 500GB SATA that is hooked up to SATA0

Now every time I boot the two HDDs seem to be switching designations. First boot: the IDE drive is SDA and the SATA is SDB. Next boot the roles are reversed. Of course this is bad for auto-mounting of partitions....

Any ideas?

Thanks

---

### Post by evets on 2008-01-14
What's the effective difference between this method and a clean install? Do you know?

Thanks

---

### Post by evets on 2008-01-14
Oh, I think I answered my own (dumb) question. It's a kernel upgrade, not an OS upgrade.  
 LOL

---

### Post by ajay003 on 2008-01-14
Could anyone post their acpi-support file? I have the hardy kernel installed but for me suspend doesn't work. It suspends but doesn't wake up. May be caz i was playing with some of the settings in acpi-support?:(

---

### Post by lemurian on 2008-01-14
> **ajay003 said:**
> Could anyone post their acpi-support file? I have the hardy kernel installed but for me suspend doesn't work. It suspends but doesn't wake up. May be caz i was playing with some of the settings in acpi-support?:(
Proper acpi configuration is very much tied to the specific hardware you are using.  Anyway, here's my acpi-support file.  Knock yourself out!  You will notice that I have "kvm kvm_intel" in the list of modules to unload.  If you don't use kvm, then you don't need to worry about that.

---

### Post by bhaverkamp on 2008-01-15
I tried this. The procedure worked fine. However the system took much longer to boot afterwards and seems sluggish while running. I ran into some problems with VMware workstation. All the USB ports seemed to disappear for VMs. I think it has to do with a change in compilers between the two kernels. I have since reverted back for now.

---

### Post by gpmartinson on 2008-01-15
One small thing that I noticed is that it rebuilds the grub to point to (hd0,0) (at least in my experience).  I had to boot by hand and rewrite the grub.lst so that the hard drives pointed to by grub in my existing file get restored.  For me, the linux partition is hd0,1...so I had to fix that (after ruling out a ton of things).  Any chance that the script could search for this line and renew that in grub at the end?  I know, i didn't write anything to help you with this, but I thought I would pass along my experiences.  

Thanks for the script.  wireless worked great and the new kernel seems responsive.

---

### Post by Hero of Time on 2008-01-16
> **gpmartinson said:**
> One small thing that I noticed is that it rebuilds the grub to point to (hd0,0) (at least in my experience).  I had to boot by hand and rewrite the grub.lst so that the hard drives pointed to by grub in my existing file get restored.  For me, the linux partition is hd0,1...so I had to fix that (after ruling out a ton of things).  Any chance that the script could search for this line and renew that in grub at the end?  I know, i didn't write anything to help you with this, but I thought I would pass along my experiences.  

Thanks for the script.  wireless worked great and the new kernel seems responsive.

The script only does things that you can do by hand. If you had upgraded the kernel by hand, this might also have happened. After I upgraded, I changed my menu.lst to disable the quiet and splash options. I like to see what my system is doing during boot. It also shows if an interface can't be configured or a hard drive can't be mounted.

---

### Post by walkerk on 2008-01-16
> **gpmartinson said:**
> One small thing that I noticed is that it rebuilds the grub to point to (hd0,0) (at least in my experience).  I had to boot by hand and rewrite the grub.lst so that the hard drives pointed to by grub in my existing file get restored.  For me, the linux partition is hd0,1...so I had to fix that (after ruling out a ton of things).  Any chance that the script could search for this line and renew that in grub at the end?  I know, i didn't write anything to help you with this, but I thought I would pass along my experiences.  

Thanks for the script.  wireless worked great and the new kernel seems responsive.

I could add this function, though its a simple fix... I'll give it a look this weekend when I have some spare time.

---

### Post by Zack McCool on 2008-01-16
> **stefanst said:**
>  Of course this is bad for auto-mounting of partitions....

Any ideas?

Thanks

While I don't have the answer to your issues, your automounting will be fixed by switching to UUID's instead of old style drive designations...

Works well, but takes a little time to get all set up...

---

### Post by MarkieB on 2008-01-17
no longer participating in ubuntuforums.org

---

### Post by ST.x on 2008-01-17
Just updated to **2.6.24-4** using the script.

---

### Post by Gigamo on 2008-01-17
Same as above, just upgraded and everything still working fine.

---

### Post by walkerk on 2008-01-17
> **MarkieB said:**
> Just to say I upgraded from Feisty - with 2.6.22-14 - to try to resolve a sata access error 
```
res 51/84:00:67:5e:85/84:01:01:00:00/e1 Emask 0x30 (host bus error)

```that persisted after (warm) reboot, S.M.A.R.T reporting to the Bios the name of the hard drive "BzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBz"[-(, then giving error 18 loading grub/ stage 1.5 read error - presumably hardware buffer trouble

searches seem to indicate that the host bus error is connected to suspend weaknesses in older kernels, so the fact that the new kernel addresses those should be a good sign

so far, so good..

thanks walkerk!

> **ST.x said:**
> Just updated to **2.6.24-4** using the script.

> **Gigamo said:**
> Same as above, just upgraded and everything still working fine.

Glad to hear it guys :)

---

### Post by accepttheownage on 2008-01-17
Tried installing this kernel several times using the script, and several parts confuse me. First off, from a clean Ubuntu install to HD, after I update the kernel upon reboot I am asked to install close to 300 or so updates. Is this NORMAL and am I suppose to accept? I have found no mention of this in the guide at all, so I am wondering whether or not this is normal. Also, after adding Hardy repository and doing apt-get install build-essential and apt-get install gcc and removing the repository I still cannot get Envy to install Nvidia drivers, it gives me an error about a dependency. This error disappears when I add the Hardy repository again but upon reboot I get a bunch of graphical glitches, such as my whole terminal being WHITE when I open one. No text, no borders, nothing. I am also asked to install roughly 500 updates with the Hardy repository and after installing those (and waiting a while) my system becomes even more unstable and runs like crap, still with the white screen bug. Has anyone experienced anything similar, and am I supposed to install all of those updates after the kernel upgrade, and am I supposed to install the updates from Hardy repository?!?

If not, how am I supposed to get Envy to install my Nvidia drivers? I am willing to reinstall the kernel again, but only if I KNOW for sure it will work okay. I am running Ubuntu on my laptop with a 8600M GT. Thanks for the help :)

---

### Post by Hero of Time on 2008-01-17
When you do a clean install of Gutsy, it is possible to have about 300 packages to update to a newer version. Best is to update Gutsy to the latest version and install your nVidia driver on it. Then reboot, check if everything is still OK and add the hardy repo to install the hardy kernel. After you install the kernel, remove the repo and boot to the hardy kernel. Try to install the nVidia driver again for this current kernel. It should work if the driver has support for the kernel. Keep in mind that we are running on a kernel that is still under development in alpha stage. Things might not work as planned on your system.

---

### Post by goldsniper on 2008-01-17
Got the script and upgrade! Everything is working just as usual and working fine. 

I notice my laptop sound (ALSA) is much much more louder than before. 

My laptop specs:

HP Compaq Presario V3000 series (V3210TU)

Processors: Intel Core Duo T2250 (2 x 1.73 GHz, 2MB L2 cache, 533MHz FSB). 
Memory: 2GB DDR2. 
Hardisk: 80GB HDD SATA. 
Display/LCD Screen: Intel® Graphics Media Accelerator 950 share 64MB
Sound: HDA Intel 
LAN : Nic 10/100, 
Modem : Modem 56K, 
Ports: IEEE 1394,Card Reader 5in1, Bluetooth. 
Ext.Drive : DVD±RW, 
Wi-Fi: Intel Pro Wireless  802.11a/b/g.

***** I just found a problem... my vmware wont power-up my windows xp. I think this is only config prolem in vmware. I'll check with vmware forum afterwards and post back here the result.

---

### Post by Hero of Time on 2008-01-18
You have the Intel Pro Wireless a/b/g card. Is it the 3945 by chance? Does it work for you? Can you connect to access points without problems? I'm asking because I have major problems with the driver it loads, the iwl3945.

---

### Post by lemurian on 2008-01-18
Well, I've upgraded udev to Hardy's 117-3.

That took care of the problem with lsusb.

---

### Post by dcdashone on 2008-01-18
6910p no issues with 2.6.24-4-generic. The eye candy is working.
Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
4 gig mem
160g hd sata
Mobility Radeon X2300

---

### Post by walkerk on 2008-01-19
> **lemurian said:**
> Well, I've upgraded udev to Hardy's 117-3.

That took care of the problem with lsusb.

Good to know...

---

### Post by goldsniper on 2008-01-19
Hero Of Time,

I did 

*sudo lspci -v*

and i got 

05:00.0 Network controller: **Intel Corporation PRO/Wireless 3945ABG Network** Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 135b
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

Yes, it is 3945 and it is working great! But it doen not uses iwl3945 driver. It uses ipw3945 instead. I hope this answer your question :)

*** About the vmware. i had to uninstall and reinstall the vmware server and everything is back to okay now.

---

### Post by Hero of Time on 2008-01-19
Goldsniper, how did you manage to use the ipw driver in the Hardy kernel? That driver isn't even supplied with that kernel, only the iwlwifi driver. When I try to modprobe it, I get the error 'module not found'.

---

### Post by gpmartinson on 2008-01-19
> **walkerk said:**
> I could add this function, though its a simple fix... I'll give it a look this weekend when I have some spare time.

Twould be great.  Thanks!

---

### Post by Hitchhiker427 on 2008-01-19
> **lemurian said:**
> Well, I've upgraded udev to Hardy's 117-3.

That took care of the problem with lsusb.

Thanks!  This fixed a problem I was having with my MTP media player.

---

### Post by woaiwojia on 2008-01-19
It's great

---

### Post by TransitMan on 2008-01-21
Just took the plunge, seems to have taken.

Dell Dimension 8400
Intel 3.2ghz HT processor
ATI X300 vid card
3x80gb HDD
DVD-ROM
DVD-RW+/-
3 USB external drives

---

### Post by goldsniper on 2008-01-21
> **Hero of Time said:**
> Goldsniper, how did you manage to use the ipw driver in the Hardy kernel? That driver isn't even supplied with that kernel, only the iwlwifi driver. When I try to modprobe it, I get the error 'module not found'.

Hero of time, im not a linux expert, i just an end user. The wireless just happened to be working fine and i do not know why it should not? :lolflag:

But for sharing sake, lets trace what happened. :popcorn:

I installed ubuntu 7.10 gutsy with my installation cd i downloaded from ubuntu. 

On the first installation menu, i choose installation for OEM ( i tried normal installation before and my sound card was not working - curiously OEM seems to overcome that problem easily. what did happened actually? OEM detects better?). After that, I did  an updating session just after the installation.

Then i upgraded to Hardy's kernel. Nothing went wrong and my wifi is working.  :guitar:

You could read [http://ipw3945.sourceforge.net/]("http://ipw3945.sourceforge.net/") and [http://intellinuxwireless.org/]("http://intellinuxwireless.org/")
 Anyway, anybody got the same Intel wifi problems?

---

### Post by lemurian on 2008-01-21
> **Hero of Time said:**
> Goldsniper, how did you manage to use the ipw driver in the Hardy kernel? That driver isn't even supplied with that kernel, only the iwlwifi driver. When I try to modprobe it, I get the error 'module not found'.
Hmm... I don't use that card or that driver so please excuse me if the following is not what you want but:

```

$ locate ipw3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
$ dpkg -S /lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
linux-ubuntu-modules-2.6.22-14-generic: /lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
$ dpkg-query -W linux-ubuntu-modules-2.6.22-14-generic
linux-ubuntu-modules-2.6.22-14-generic  2.6.22-14.37

```

I would guess that installing the latest linux-ubuntu-modules-2.6.22-14-generic provided for Hardy, which is at version 2.6.22-14.37 by my reckoning, should do the trick.

---

### Post by gupta_sumesh63 on 2008-01-21
Thanks,
worked like a charm.
Intel 3.66GHz P4
Intel Video card (Onboard)
1.5 GB DDR2 RAM
Intel Sound card with Realtek Chip set
Realtek ethernet card.
Thanks again.:guitar:

---

### Post by stefanst on 2008-01-21
> **walkerk said:**
> I have no experience with TV Tuners so I wouldn't know where to begin... A couple questions: 

1. What module in 2.6.24 allows compatibility?
2. How did you get it working with 2.6.22? Work-around, etc...

The problem is that the tuner picks up the QAM channels and locks but then kicks out stating that it can't find a "table". Don't really know what that means. This occurs running "dvbscan" as well as using MythTV.

I dug a little deeper and found out one more astonishing fact:
The TV Card (KWorld ATSC 115) works without problem on the I386 kernel v 2.6.24. Running the AMD64 2.6.24 kernel creates the problem. The 2.6.22 works fine for both: I386 and AMD64 kernels. 

To answer your question how to get the card to work in 2.6.22:

1) copy the firmware (dvb-fe-nxt2004.fw) into the firmware directory. This is also needed for the 2.6.24 kernel.

2) Add the following lines to /etc/modprobe.conf (only 2.6.22 kernel)
   alias char-major-81 videodev
   alias char-major-81-0 saa7134
   options saa7134 card=90 disable_ir=1

3) Load the modules: (only 2.6.22 kernel)
    modprobe saa7134-dvb
    modprobe saa7134-alsa

And it works. Note that the module with the problem is the "dvb" module. I haven't had any luck getting ALSA working no matter which kernel I use.

Since the firmware works when using the 2.6.22 kernel, I would look in the module- but then I'm clueless when it comes to programming, so over to you.

ST

---

### Post by Hero of Time on 2008-01-21
> **lemurian said:**
> Hmm... I don't use that card or that driver so please excuse me if the following is not what you want but:

```

$ locate ipw3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
$ dpkg -S /lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
linux-ubuntu-modules-2.6.22-14-generic: /lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
$ dpkg-query -W linux-ubuntu-modules-2.6.22-14-generic
linux-ubuntu-modules-2.6.22-14-generic  2.6.22-14.37

```

I would guess that installing the latest linux-ubuntu-modules-2.6.22-14-generic provided for Hardy, which is at version 2.6.22-14.37 by my reckoning, should do the trick.
That could work, I got my wireless back again in the Gutsy kernel with the ipw driver, but I still wonder why the iwlwifi won't work for me. When I do get it to work my wifi won't connect using wpa_supplicant. It's wining about wext incompatible or something. If things still don't go how I like it, I either remove the Hardy kernel until hardy is at it's final stage (or late beta) or compile the ipw driver myself. I had wifi on Saturday, lost it on Sunday and today I found out that I was missing the ipw3945d.ko file for the daemon to run. Got that file, renamed to the one Ubuntu needed and it works again. With compiling, that will be much easier, but I rather use iwlwifi, which I can't compile whatsoever or get WEXT errors with wpa_supplicant.

---

### Post by gryzzly on 2008-01-21
after i made all things with installing new kernel i had my card reader working, but sleep mode (because of which i started all upgrading) didn't fix - after it goes to sleep, when i wake it up it makes horrible noise from speakers (like one that you hear when putting microphone close to speakers, you know) - and login form comes and i can never login, i put in my password and it just doesn't take it. After reboot i can login easily. Also my virtual box dead, which i need very much, since i am web-developer, and i test stuff under win... Also wi-fi doesn't work (i have tried fixes from miscellaneous, but nothing worked :( in my  Grub i don't have old kernel, i think i have deleted it somehow :( sorry 
anyway, can i anyhow come back, or should i just make reinstall of all system? thanks a lot! (really, your tuts are straight forward and cool)

---

### Post by Hero of Time on 2008-01-21
> **gryzzly said:**
> after i made all things with installing new kernel i had my card reader working, but sleep mode (because of which i started all upgrading) didn't fix - after it goes to sleep, when i wake it up it makes horrible noise from speakers (like one that you hear when putting microphone close to speakers, you know) - and login form comes and i can never login, i put in my password and it just doesn't take it. After reboot i can login easily. Also my virtual box dead, which i need very much, since i am web-developer, and i test stuff under win... Also wi-fi doesn't work (i have tried fixes from miscellaneous, but nothing worked :( in my  Grub i don't have old kernel, i think i have deleted it somehow :( sorry 
anyway, can i anyhow come back, or should i just make reinstall of all system? thanks a lot! (really, your tuts are straight forward and cool)
If you lan interface still works, connect trough that to internet, then install the Gutsy kernel again. That should work. You also mention that VBox no longer works, did you type 'sudo /etc/init.d/vboxdrv setup' in a terminal? You need to do that after every kernel update.

---

### Post by gryzzly on 2008-01-21
> **Hero of Time said:**
> If you lan interface still works, connect trough that to internet, then install the Gutsy kernel again. That should work. You also mention that VBox no longer works, did you type 'sudo /etc/init.d/vboxdrv setup' in a terminal? You need to do that after every kernel update.

Thing is, that i probably deleted somehow package of virtual machine, anyway, i have a lan connection to internet, but i dont know how to install old kernel now, i tried to make ```
sudo apt-get linux install (but with gutsy version of linux and linux-generic)
``` but it didn't work at all. It sayed "you have already newest kernel version, or something like that ..

---

### Post by lemurian on 2008-01-21
> **gryzzly said:**
> Thing is, that i probably deleted somehow package of virtual machine, anyway, i have a lan connection to internet, but i dont know how to install old kernel now, i tried to make ```
sudo apt-get linux install (but with gutsy version of linux and linux-generic)
``` but it didn't work at all. It sayed "you have already newest kernel version, or something like that ..
Did you try:

```

$ sudo apt-get install linux=2.6.22.14.21

```

Using the "=<version>" tells apt-get you want to downgrade.  But to revert to the system exactly as it was you probably also need to downgrade libc6 and maybe other things...

It would actually be possible to write a script that issues a set of apt-get commands to downgrade everything to the latest version of what is available in the repository **currently** available in the apt configuration.  That would take care of reverting the actions of the hardy.py script when the **** hits the fan.

Edit: Oh, goodie!  The forum software automatically censors posts!  I meant to say "when the excrement hits the fan"... let's see whether that gets censored.

---

### Post by Hero of Time on 2008-01-21
> **gryzzly said:**
> Thing is, that i probably deleted somehow package of virtual machine, anyway, i have a lan connection to internet, but i dont know how to install old kernel now, i tried to make ```
sudo apt-get linux install (but with gutsy version of linux and linux-generic)
``` but it didn't work at all. It sayed "you have already newest kernel version, or something like that ..

Why didn't you use Synaptic? I removed my Gutsy kernel once when on Hardy kernel to get my ipw driver back, worked just fine for downgrading back to the Gutsy kernel.

---

### Post by gryzzly on 2008-01-22
Hey guys, thanks for response. I've downgraded everything i needed, so now it's ok :)

---

### Post by MianoSM on 2008-01-23
I wasn't able to catch it if it was already said but,

Is this kernel running at 100hz or 1000hz by default?

Thanks.

---

### Post by TransitMan on 2008-01-23
Just treid the command to mount the usb and it failed.
I cannot access my USB drives, even though they are seen on boot-up and the icons populate the desktop.

Solutions, anyone?

---

### Post by lemurian on 2008-01-23
> **TransitMan said:**
> Just treid the command to mount the usb and it failed.
I cannot access my USB drives, even though they are seen on boot-up and the icons populate the desktop.

Solutions, anyone?
Can you cut and paste the command you were using and the error message you got?

Unless you upgrade your udev to Hardy's udev, lsusb and things which depend on /proc/bus/usb being a mountpoint for usbfs won't work.  

However, even if you don't upgrade your udev, all USB devices should be recognized by the kernel, mounting USB drives should not be a problem and accessing USB drives should work.  I'm talking from experience.   (Check my previous posts in this thread for details.)

---

### Post by TransitMan on 2008-01-23
> **lemurian said:**
> 
```

$ sudo mount -t usbfs procbususb /proc/bus/usb/

```

> **lemurian said:**
> Can you cut and paste the command you were using and the error message you got?

Unless you upgrade your udev to Hardy's udev, lsusb and things which depend on /proc/bus/usb being a mountpoint for usbfs won't work.  

However, even if you don't upgrade your udev, all USB devices should be recognized by the kernel, mounting USB drives should not be a problem and accessing USB drives should work.  I'm talking from experience.   (Check my previous posts in this thread for details.)

See the code above from your post.
No error messages given.
USB drives are all NTFS except for one partition being FAT32 and I can read an access it normally.

---

### Post by lemurian on 2008-01-23
> **TransitMan said:**
> See the code above from your post.
No error messages given.
USB drives are all NTFS except for one partition being FAT32 and I can read an access it normally.
Mounts typically don't fail without an error message.  You can also check /var/log/syslog for suspicious messages in there.  Also if you do this:

```

$ sudo mount -t usbfs procbususb /proc/bus/usb/; echo $?

```

The echo command will output the exit status of the mount command (it is transmitted as-is by sudo).  If you see "0", then all is peachy.  If you see another number, something went wrong somewhere.  Also, if lsusb works after you preform that mount and if you get a list of files from:

```

$ ls /proc/bus/usb/

```

Then it means the mount worked.  That mount command only populates /proc/bus/usb/.  That's helpful to get lsusb to work and to get things which depend on /proc/bus/usb to work but it does nothing more.

---

### Post by TransitMan on 2008-01-23
Ended up installing pysdm and made the changes I need from there.
I now have r/w access to all the USB drives.

---

### Post by MianoSM on 2008-01-24
> **MianoSM said:**
> I wasn't able to catch it if it was already said but: Is this kernel running at 100hz or 1000hz by default?
Thanks.

Anyone?

---

### Post by lamborghiniwang on 2008-01-25
This script works well on my T61p+Gutsy X86-64. Because I had manually installed the Nvidia 169.09 driver before, I had to reinstall the driver after the new kernel is installed, but other than that everything works perfectly. :D

---

### Post by Kokesh on 2008-01-25
Works like a charm, except one thing for me: I still have few NTFS partitions, which I was lazy to convert to ext3 and it don't mount them.

---

### Post by Hero of Time on 2008-01-25
Strange, I have an NTFS partition that mounts just fine. Do you use the build-in NTFS module, or NTFS-3G? I use the latter. What does your fstab say about the NTFS partition?

---

### Post by gfg on 2008-01-25
Does anyone get a huge amount of kernel interrupt with the latest kernel, 2.6.24-5-generic? Powertop reports:  42.6% (392.0)      <kernel IPI> : Rescheduling interrupts . Seems to be an effect of the new kernel, as this  did not happen on 2.6.24-4-generic. Any help would be appreciated.

---

### Post by Kokesh on 2008-01-25
It says during boot procedure (about all my NTFS partitions)
> /dev/hda5: The superblock could not be read or does not describe a correct ext2 filesystem. ............
fsck died with exit status 8

Than it is waiting for my root password to continue.
If I try than as root mount -a, it says: > The device '/dev/sda/1' doesn't have a valid NTFS. Maybe you selected wrong device?.....

If I boot into 2.6.22-14 kernel, all is OK.

Here is example from my fstab:
> /dev/sda1                                  /media/c                ntfs-3g      defaults,locale=en_US.UTF-8      0  0  


---

### Post by Roland S on 2008-01-25
I just wanted to thank you. I was able to update my kernel and can now use my ne wacom bamboo pad. This was amazingly simple. There was only one little problem which was easy to fix. Thank You Again

---

### Post by lemurian on 2008-01-25
> **gfg said:**
> Does anyone get a huge amount of kernel interrupt with the latest kernel, 2.6.24-5-generic? Powertop reports:  42.6% (392.0)      <kernel IPI> : Rescheduling interrupts . Seems to be an effect of the new kernel, as this  did not happen on 2.6.24-4-generic. Any help would be appreciated.
No.  I've just upgraded to 2.6.24-5 and have no problem at all.

BTW, those who use the nVidia closed-source driver provided by the restricted drivers manager get an upgrade to 169.09 when they upgrade their kernel to 2.6.24-5.

---

### Post by portach king on 2008-01-25
Erk. I'm geting a slow bootup, followed by a black screen. Laptop backlight seems to turn on and off three times before settling as on, though still just a black screen. 
Any suggestions?
I'm back using my 2.6.22 kernel again to post this. Thanks in advance, I really hope this helps me get my broadcom working properly. :)

---

### Post by wnelson on 2008-01-26
I notice right off that on initial load and completed load of Gnome before 2.22.xx it took 99M and now 88M of memory consumed. Boots into Gnome in 11 seconds. Before application of first load were cached and took more time to load. Now loads instantly (~2 seconds) firefox before (~4 seconds).


Pentium 4 2.8 Northwood
MSI 865PE
512M 
160 HD / ext3
CDRW
Nvidia Geforce4 440 agp 8x
Epson CX3810 printer/scanner

Walt
Tacoma, WA

---

### Post by lemurian on 2008-01-26
> **portach king said:**
> Erk. I'm geting a slow bootup, followed by a black screen. Laptop backlight seems to turn on and off three times before settling as on, though still just a black screen. 
Any suggestions?
I'm back using my 2.6.22 kernel again to post this. Thanks in advance, I really hope this helps me get my broadcom working properly. :)
The symptoms you describe sound like XWindows is trying to start but is not able to.  Are you using the nVidia closed-source driver by any chance?  Or any kind of unusual setup for XWindows?

---

### Post by portach king on 2008-01-26
It's an ATI card. Simply using the restricted drivers.
I did have to alter the Usplash to speed up by boot time with Gutsy earlier (It was taking 3 minutes to boot with no splash scren), so I followed this guide which solved my problem: [http://ubuntuforums.org/showthread.php?t=579568&highlight=gutsy+boots+slow&page=2](http://ubuntuforums.org/showthread.php?t=579568&highlight=gutsy+boots+slow&page=2)
Any chance that might be to blame, and/or if I can reverse it easily?

---

### Post by lemurian on 2008-01-26
> **portach king said:**
> It's an ATI card. Simply using the restricted drivers.
I did have to alter the Usplash to speed up by boot time with Gutsy earlier (It was taking 3 minutes to boot with no splash scren), so I followed this guide which solved my problem: [http://ubuntuforums.org/showthread.php?t=579568&highlight=gutsy+boots+slow&page=2](http://ubuntuforums.org/showthread.php?t=579568&highlight=gutsy+boots+slow&page=2)
Any chance that might be to blame, and/or if I can reverse it easily?
Here's what comes to mind:

1. I doubt usplash has any effect on whether XWindows can start or not.

2. I think the problem is XWindows but I could be wrong.  Normally, when X cannot start, you at least get a screen that tells you it cannot start.  If things are somewhat ok for X, it will go into "safe mode" and show you a dialog box in the middle of a black screen asking whether you want to configure it, etc.  If things are so bad that X cannot grab the display at all, then you should get a text dialog which tells you X cannot start.  But you did not mention either of those in your initial description so maybe I'm wrong.  The way to check what is going on with X would be to hit Ctrl-Alt-F1 after the machine has booted to get into a console, log in and check for errors in /var/log/Xorg.0.log

I have an nVidia card so I know nothing of the caveats that ATI card owners must keep in mind when upgrading kernels.

I think that's about all I can say.

---

### Post by elkanguro on 2008-01-26
Is this method upgrade to last realesed stable 2.6.24 kernel? Make it sense to go through it, when I am Newbie and have never done such operations? Will every application and driver work after upgrade or I will have to install it again? I use Ubuntu 7.04 with 2.6.20-16-generic kernel. What benefits I get after upgrade? Please advise me.

---

### Post by hugo_koopmans on 2008-01-26
HI, The script worked very good thank you !

Sony Vaio laptop VGN SZ61

hugo

---

### Post by portach king on 2008-01-26
Hi,
Well my problem stil perists. Can anyone help?
I tried loading into Recovery Mode which before loading up the terminal command screen read
```
profile /etc/apparmor.d/usr.sbin.cupsd failed to load
```

I'm not sure if that sheds any light. I'd really appreciate any help, as I mentioned I'm having a very difficult time with my broadcom card. Thank you

---

### Post by jasnix on 2008-01-27
Hello,
First I would like to thank you for the great howto.  I updated to the latest kernel and everything seemed to work until I tried to use my nVidia driver. I have tried using Envy, nvidia-glx-new (installed by your script) and also tried installing manually from nvidia's site.  Each time I do this my computer boots and then when it gets to the login screen all I get is a white screen with a black line down the middle.  

Looking in /var/log/Xorg.0.log doesn't appear to have any useful information. 

The video card I have is an 8600m GT.

Any help would be much appreciated!

---

### Post by nDrewPJ on 2008-01-27
> **jasnix said:**
> Hello,
First I would like to thank you for the great howto.  I updated to the latest kernel and everything seemed to work until I tried to use my nVidia driver. I have tried using Envy, nvidia-glx-new (installed by your script) and also tried installing manually from nvidia's site.  Each time I do this my computer boots and then when it gets to the login screen all I get is a white screen with a black line down the middle.  

Looking in /var/log/Xorg.0.log doesn't appear to have any useful information. 

The video card I have is an 8600m GT.

Any help would be much appreciated!

Get the latest envy: envy_0.9.10-0ubuntu2_all.deb. Uninstall the legacy version, install the new one. Then write:

sudo envy --uninstall-all

followed by:

sudo envy -t   
...and select '6' >> Install the new driver

---

### Post by Meyithi on 2008-01-27
Script worked perfectly for me, Athlon 64 x2 3800 (x86).  Did a manual install of the nVidia drivers afterwards with Envy.

Many thanks for the script!  Great work!

---

### Post by portach king on 2008-01-27
I'm going to ask for help once more. As I mentioned on page 23, the system wont boot in .24. The splash screen loads slowly and ultimately finishes in a black screen with nothing happening. 
I'd really appreciate any help.

---

### Post by snakeeyes on 2008-01-27
> **portach king said:**
> I'm going to ask for help once more. As I mentioned on page 23, the system wont boot in .24. The splash screen loads slowly and ultimately finishes in a black screen with nothing happening. 
I'd really appreciate any help.
This happens because u probably didn't upgrade your drivers or u didn't set up the system to use the new drivers. If u haven't upgraded your drivers yet then reconfigure xserver to use vesa or nv for now to boot into the new kernel atleast.

---

### Post by walkerk on 2008-01-27
> **portach king said:**
> I'm going to ask for help once more. As I mentioned on page 23, the system wont boot in .24. The splash screen loads slowly and ultimately finishes in a black screen with nothing happening. 
I'd really appreciate any help.

run this in recovery mode...
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

once you're back on the vesa driver you should re-install the nVidia driver...

---

### Post by portach king on 2008-01-27
Thank you both Walkerk and Snakeeyes.
I'll try that now, I should note though, that  am using an ATI card. Proceeding with 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
is stil the right thing to do, yes?
Sorry if that's a silly question. I'm learning :)

---

### Post by snakeeyes on 2008-01-27
Hi again well I usuall type in:

sudo dpkg-reconfigure xserver-xorg

This command I typed usually reconfigures the entire xsever but I think the command u typed in is only for the display and u should try that first.

---

### Post by portach king on 2008-01-27
Will do! Thanks again for your patience and help.

---

### Post by portach king on 2008-01-27
Hello! Posting from 24 Kernel now! Thank you so much! The new b43 driver works really well on my BCM4318! I can finally connect without having to sit right beside my router. (Though I can't get the wireless light to come on) I'm delighted.
Two issue though remain though.
1. Booting is still rather slow. It seems to hang for 30-40 seconds about a quarter of the way into the splash screen.
2. How do i get my ATI card working again. I tried installing the restricted drivers, but it brought me back to the black screen issue again.

Thanks for your help so far guys. you are truly amazing.

---

### Post by standards on 2008-01-27
The script seemed to work more or less perfectly [thanks!] but now I'm having an issue with importing photos from my camera. 

When I plug it in it is detected and the dialog pops up, but I get this message:

```
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
```

I *did* install hardy's udev package (as well as update libgphoto2-2, but that was after i was having problems. it didn't help). reboots have not helped. 

i think i have read/write access, here's an ls-l of /mnt/proc

robert@smain:/proc/bus$ ls -l
total 0
dr-xr-xr-x 2 root root 0 2008-01-27 14:46 input
dr-xr-xr-x 5 root root 0 2008-01-27 14:29 pci
dr-xr-xr-x 2 root root 0 2008-01-27 14:46 usb

anyone? playing with the modules is a bit beyond my grasp.

---

### Post by lemurian on 2008-01-27
> **standards said:**
> The script seemed to work more or less perfectly [thanks!] but now I'm having an issue with importing photos from my camera. 

When I plug it in it is detected and the dialog pops up, but I get this message:

```
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
```

I *did* install hardy's udev package (as well as update libgphoto2-2, but that was after i was having problems. it didn't help). reboots have not helped. 

i think i have read/write access, here's an ls-l of /mnt/proc

robert@smain:/proc/bus$ ls -l
total 0
dr-xr-xr-x 2 root root 0 2008-01-27 14:46 input
dr-xr-xr-x 5 root root 0 2008-01-27 14:29 pci
dr-xr-xr-x 2 root root 0 2008-01-27 14:46 usb

anyone? playing with the modules is a bit beyond my grasp.
The way to check whether it is a permission problem is this:

1. Run:

```

$ lsusb

```

You will get output of the form:

```

Bus 007 Device 008: ID 046d:c225 Logitech, Inc. 
Bus 007 Device 007: ID 046d:c521 Logitech, Inc. 
Bus 007 Device 006: ID 046d:c221 Logitech, Inc. 
Bus 007 Device 005: ID 046d:c223 Logitech, Inc. 
Bus 007 Device 004: ID 05a9:2641 OmniVision Technologies, Inc. 
...

```

2. Identify the device that interests you in the list and note the Bus and Device number.  For instance, if I care about the "Omnivision Technologies" device above, the bus number is 007 and device is 004.  Issue the following command:

```

$ ls -l /dev/bus/usb/BUS/DEVICE

```

where you replace BUS and DEVICE by the numbers you found.  With the example of the omnivision device:

```

$ ls -l /dev/bus/usb/007/004
crw-rw-r-- 1 root root 189, 771 2008-01-27 10:33 /dev/bus/usb/007/004

```

You want check that the permissions (the first thing which appears on the line, "crw-rw-r--" in the example above) are set to allow you to use the device.

If the permissions are not set for you to use the device, then you need to fix the permissions.   There's a guide here:

[http://gphoto.sourceforge.net/doc/manual/permissions-usb.html](http://gphoto.sourceforge.net/doc/manual/permissions-usb.html)

You want to check this section: "4.3.3. USB ports on Linux using udev" because Ubuntu uses udev.

---

### Post by standards on 2008-01-27
hi, thanks for the concise reply. here's what mine looks like:

```

robert@smain:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:30f2 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
robert@smain:~$ ls -l /dev/bus/usb/001/003
crw-rw-r-- 1 root root 189, 2 2008-01-27 15:32 /dev/bus/usb/001/003

```

is there something amiss here? i think i can follow the directions on the link you supplied, but i'm not sure if it's supposed to have any additional permissions.

---

### Post by motion parallax on 2008-01-27
Sorry if this seems like such a base question, but what are the benefits to upgrading to the Hardy kernel?  My understanding of Linux is meager, but I'm always interested in improvements, especially if it addresses the suspend/hibernate issue.

---

### Post by snakeeyes on 2008-01-27
> **portach king said:**
> Hello! Posting from 24 Kernel now! Thank you so much! The new b43 driver works really well on my BCM4318! I can finally connect without having to sit right beside my router. (Though I can't get the wireless light to come on) I'm delighted.
Two issue though remain though.
1. Booting is still rather slow. It seems to hang for 30-40 seconds about a quarter of the way into the splash screen.
2. How do i get my ATI card working again. I tried installing the restricted drivers, but it brought me back to the black screen issue again.

Thanks for your help so far guys. you are truly amazing.
I don't have any real experience with ATI cards, but I think u should remove all current ATI drivers. Then use Envy to install the driver, Envy may ask for this repo to be added though.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main

Good Luck!

---

### Post by portach king on 2008-01-27
Thanks, I installed envy and it worked, though the performance (ie. the framerate while running compiz) has dropped dramatically from fglrx provided with the Restricted Drivers. It's very choppy.
Anyone else with an ATI card? 
Thought I might as well ask these questions as I'm sure that I am/will not be alone with these problems.       : )

---

### Post by lemurian on 2008-01-27
> **standards said:**
> hi, thanks for the concise reply. here's what mine looks like:

```

robert@smain:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:30f2 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
robert@smain:~$ ls -l /dev/bus/usb/001/003
crw-rw-r-- 1 root root 189, 2 2008-01-27 15:32 /dev/bus/usb/001/003

```

is there something amiss here? i think i can follow the directions on the link you supplied, but i'm not sure if it's supposed to have any additional permissions.
No, those permissions are no good.

Ok, I got my wife's camera and plugged it in.  I ran into the same problem you have.  The way I fixed it is as follows:

1. Execute:

```

$ sudo nano /etc/udev/rules.d/45-libgphoto2.rules 

```

2. Change the line which reads:

```

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

```

so that instead of "usb_device" it reads "usb".  The way I did it on my system was that I replaced the line above with the following:

```

# LDD: modified the original line:
# SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
# to the following
SUBSYSTEM!="usb", GOTO="libgphoto2_rules_end"

```

So that I have some documentation of what I did.  (LDD are my initials.)  After doing that, I can import photos.

Note that you must be part of the plugdev group but if you were able to import pictures before, you should already be in that group.

I'm afraid that one problem with the udev upgrade is that some of the ways to specify USB devices in the rule files has changed.  I had to do a similar thing as the above change to get my scanner working. :-\

---

### Post by gdselzer on 2008-01-28
The script seems to have worked and suspend WORKS now!  But in a move of one step forward, two steps back, my wireless card does not work at all now.  I had it working in Gutsy with ndiswrapper, but now I get nothing.

I have the bcm94311mcg rev 2 card:

```
$ lspci |grep BCM
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
```

I installed the firmware using b43-fwcutter and it seems to have gone into /lib/firmware/b43 without a problem.

When I do:
```

$ sudo modprobe b43
```

nothing happens.  No messages in dmesg.  No new interfaces.  Nothing.

I assume the module is loaded, because:

```
$ lsmod | grep b43
b43                   126120  0 
rfkill                 10128  1 b43
mac80211              192664  1 b43
led_class               7176  1 b43
input_polldev           6928  1 b43
ssb                    37252  2 b43,ohci_hc
```d

I don't even know how to trouble shoot this.  Can anyone help?

---

### Post by snakeeyes on 2008-01-28
> **portach king said:**
> Thanks, I installed envy and it worked, though the performance (ie. the framerate while running compiz) has dropped dramatically from fglrx provided with the Restricted Drivers. It's very choppy.
Anyone else with an ATI card? 
Thought I might as well ask these questions as I'm sure that I am/will not be alone with these problems.       : )
I really suggest u use envy for the drivers and do u have xgl running?

---

### Post by Hero of Time on 2008-01-28
> **portach king said:**
> Thanks, I installed envy and it worked, though the performance (ie. the framerate while running compiz) has dropped dramatically from fglrx provided with the Restricted Drivers. It's very choppy.
Anyone else with an ATI card? 
Thought I might as well ask these questions as I'm sure that I am/will not be alone with these problems.       : )
I don't know what card you have, but I have an x1400 mobile and with the closed source ati driver, I do get it working, only with fglrxinfo I get mesa. I blame the dkms system that causes these problems, as I have the same issues now on my Gutsy kernel.

---

### Post by hopelessone on 2008-01-28
Hi,

Nice script..!!

1. It changed my Fstab around a bit but was easy to fix HDD's..

2. Couldnt get auto install Nvdia drivers to work (1) so installed envy after that and i think i got it...[COLOR="Red"]did i have to uninstall anything before i installed ENVY??[/COLOR]

I had only 640x480 so i set (Screens and Graphics) from (generic) to LCD panel 1024x768...

I get a resolution of 50mHz (Screens and Graphics) but in Nvdia settings it says TGM TGL SM150 (CRT-0) 75mHz... Weird?
[COLOR="Red"]How do i fix???[/COLOR]

the only error i get in my logs  is this:
[COLOR="Red"]Jan 28 20:55:12 box-desktop kernel: [  138.322332] python[5619]: segfault at aaaaaaac eip b793a339 esp bff3e280 error 4[/COLOR]

anyway is was worth it...

p4 1.7ghz
756mb memory
Nvdia NV11 [GeForce2 MX/MX 400]


thanks..

---

### Post by snakeeyes on 2008-01-28
Has anyone else had this bug with the new nvidia drivers that the title bar sometimes becomes transparent?

---

### Post by lemurian on 2008-01-28
> **snakeeyes said:**
> Has anyone else had this bug with the new nvidia drivers that the title bar sometimes becomes transparent?
Are you sure your window decorator is not crashing?

I've had gtk-window-decorator crash a few times.  The symptom is that all title bars and all windows decorations disappear.  I then have to go to a terminal and restart it.  It has not happened in a while and I'm not sure what changed that made the problem go away.

If you use compiz, your windows decorator should be emerald.  I think gtk-window-decorator is used if compiz is turned off or if you mess with your settings like I do.  Check which of emerald or gtk-window-decorator is running when you have title bars, then when they disappear, check again to see whether your decorator is still running.  If not, you can restart the decorator by going to a terminal and typing:

```

$ emerald &

```

or gtk-window-decorator as needed.

---

### Post by snakeeyes on 2008-01-28
No, not a crash, what happens is with a few programs only such as openoffice writer, if I go near the close, max buttons they r not drawn completely but still there.

---

### Post by portach king on 2008-01-28
Are you using Emerald? Perhaps you have it using the incorrect Frame engine?
Try reloading a theme again if you are.

---

### Post by snakeeyes on 2008-01-28
> **portach king said:**
> Are you using Emerald? Perhaps you have it using the incorrect Frame engine?
Try reloading a theme again if you are.
Nope I am using gtk window decorator.

---

### Post by Nepherte on 2008-01-28
> **snakeeyes said:**
> Has anyone else had this bug with the new nvidia drivers that the title bar sometimes becomes transparent?
I have the same problem with the Nvidia drivers 169.07 in combination with a Nvidia 7800GT

---

### Post by lemurian on 2008-01-28
> **Nepherte said:**
> I have the same problem with the Nvidia drivers 169.07 in combination with a Nvidia 7800GT
Argh!  I've never had that problem or heard about it.  The crash hypothesis was my best guess.

---

### Post by Meyithi on 2008-01-28
I've had this forever with Firefox and OpenOffice, a slight flicker over maximized windows minimize, maximize and close buttons and then the whole toolbar will go transparent until I mouseover it.

---

### Post by snakeeyes on 2008-01-28
This is a known bug with the Ubuntu human theme but with these new drivers it happens with all the themes whether I use emerald or gtk while using openoffice or firefox mostly, its very annoying cause the title bar changes to some weird looking colors.

Has some one tested Hardy? Does it happen on that? Also it happens whether I use envy to install nvidia or the repo so I think its a bug in the kernel.

---

### Post by BC7333 on 2008-01-28
Up to 2.6.24-5 now using the script.  seems a bit snappier but wireless light/indicator still not working.

thumbs up!

[edit]

Sudden hangs while charging did not disappear though.. maybe next time.

---

### Post by caveneri on 2008-01-28
Work for me!! Thanks.... I use the script Option #1 (hardy.py).

* Pentium 4 HT 2.4c 800Mhz.
* 1Gb ddr 400mhz (512mb 400mhz Samsumg - 512mb 400mhz kingston) - Dual Channeling.
*Sound Blaster Audigy Se 24bit
*Speaker Logitech 5.1 (Work all Speaker)
*Ati Radeon x1650 256Mb
*Monitor Samsung SyncMaster 793s

Bye :lolflag:

---

### Post by schmolch on 2008-01-28
How do i get the wacom pen of my tablet-pc working with 2.6.24?

I just did a fresh gutsy install and updated the kernel, but now the wacom device is not found anymore.

---

### Post by jimbojones on 2008-01-29
Dell XPS1210, Nvidia GeForceGo 7400

Updated to the new kernel manually, all went well.  Updated GCC & performed the lsusb fix.  Everything is working fine.  I did not reinstall the nvidia driver and my video appears to be using the 169.09 driver still without needing to reinstall (at least nvidia-settings says so)

---

### Post by ssc351 on 2008-01-30
Dell Inspiron 640m
Intel 945 graphics
1.66 core duo
Atheros 5006x wireless card


Used the option #1, everything seems to work BUT...it seems like every 3rd or 4th reboot after I am fully logged in, the hard drive grinds away like crazy!!!  It doesn't really stop, or at least I haven't been patient enough to wait for it to stop, then when I go to reboot/shutdown it takes a good 10-12 mins to actually shut the thing down.  Its very similar to when you have a ton of malware/viruses/bugs in windows and you can't get anywhere because the hard disk keeps grinding away.  But as I said, if I reboot it, the problem usually goes away.

---

### Post by TD-Linux on 2008-01-30
IBM Thinkpad T61p

This update did no go so well for me. First off, my second core disappeared. Then, my wireless died. I tried the fix, to no avail. I believe it is because of the lack of the ipw3945 driver, and I was unable to set up the iwl3945 driver to work correctly. There should be a way to fix this, but I can't find it.

Finally, this does not fix the problem I was having with bzflag skipping frames randomly and being extremely jerky, though with a high average framerate.

I'll give this one more restart, then switch back if 2.6.24 still fails me. Then, when my Hardy update in a few more months probably breaks everything yet again, I'll switch to Fedora...

BTW where are the eth* interfaces supposed to appear? I've never seen them in /dev, though knetworkmanager seems to work just fine anyways, except with this latest kernel.

---

### Post by rio-paco on 2008-01-31
Sony Vaio SZ61
nVidia GeForce 8400M GS
Intel Corporation PRO/Wireless 3945ABG

Running 'hardy.py' worked fine and I included the new nVidia drivers. I had to upgrade udev to get lsusb working. Some issues that were fixed for me were:

 * Wireless does not drop connection anymore. Previously my wireless card ended up as eth1, now it is wlan0_ren, I don't no if this is anything I should care about.

 * Screen does not flicker when using full compiz graphic effects. Before the screen flickered every 15 seconds or so.

However, my machine boots a lot slower. At least twice as log time to get to the login window. Comparing the output from dmesg shows:

[    0.000000] Detected 2194.601 MHz processor.
[   30.751066] Console: colour VGA+ 80x25

With my old gutsy kernel the time diff there was only 12 secs. Any ideas at what I should look at? I'd really like to have a fast boot. Any feedback that can help me improve it would be appreciated.

Also I get the following errors/warnings in dmesg:

[   31.149164] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   49.693107] sonypi: probe of sonypi failed with error -17

and

[   35.286393] PM: Resume from disk failed.
[   42.290362] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   45.855484] audit(1201767040.713:2): operation="profile_load" info="failed to unpack profile" name="/usr/lib/cups/backend/cups-pdf" pid=4592
[   49.692702] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
[   49.692946] kobject_add failed for sonypi with -EEXIST, don't try to register things with the same name in the same directory.
[   49.693102] sonypi: misc_register failed
[   49.693107] sonypi: probe of sonypi failed with error -17

I thought that the sony-laptop was to replace sonypi.

Thanks for the 'hardy.py' script!

---

### Post by Gigamo on 2008-01-31
Sadly, the long boot time is normal.

---

### Post by mk100 on 2008-01-31
I did it with 2.6.24-5 and udev update and it is working fine on my HP NX 6325 with ATI X1150m and Broadcom 4312 wireless card. The new b43 driver is a great improvement.

---

### Post by snakeeyes on 2008-01-31
Nobody had any problems with their titlebar after this? My title bar keeps on becoming transparent from some sides.

---

### Post by Gigamo on 2008-01-31
Few questions before I do this upgrade again on my fresh install;

- I installed the NVIDIA driver with the manual installer from their site this time (no envy or nvidia-glx-new package). How will this work/what will I have to do in the new kernel?

- I use a program called "btnx" from someone here on the forums to give my MX Revolution mouse better functionality; does anyone know if this works flawlessly in the new kernel still?

Thanks!

---

### Post by Gigamo on 2008-01-31
Well, I upgraded and took the nvidia-glx-new package with me in the script. However, I cannot start X even though it is installed. I can start X when I set the driver to "nv" in xorg.conf; but that's it. Should I run the nvidia manual installer or can I fix this one?

Edit: Fixed it by enabling restricted drivers manager.

Thanks again for this wonderful script, walkerk.

---

### Post by walkerk on 2008-01-31
> **Gigamo said:**
> Well, I upgraded and took the nvidia-glx-new package with me in the script. However, I cannot start X even though it is installed. I can start X when I set the driver to "nv" in xorg.conf; but that's it. Should I run the nvidia manual installer or can I fix this one?

Edit: Fixed it by enabling restricted drivers manager.

Thanks again for this wonderful script, walkerk.

Sorry man.. just checked this thread. I'm glad you got it worked out :)

---

### Post by lemurian on 2008-01-31
> **Gigamo said:**
> Well, I upgraded and took the nvidia-glx-new package with me in the script. However, I cannot start X even though it is installed. I can start X when I set the driver to "nv" in xorg.conf; but that's it. Should I run the nvidia manual installer or can I fix this one?

Edit: Fixed it by enabling restricted drivers manager.

Thanks again for this wonderful script, walkerk.
For future reference.  The way I understand it, whenever you upgrade a kernel on Ubuntu, any kernel modules **you installed manually for the old kernel must be reinstalled for the newer kernel**.  The reason for this is that each kernel look in separate directories for their modules:

```

$ ls -l /lib/modules/
total 16
drwxr-xr-x 9 root root 4096 2007-12-19 08:49 2.6.22-14-generic
drwxr-xr-x 4 root root 4096 2008-01-25 15:43 2.6.24-3-generic
drwxr-xr-x 8 root root 4096 2008-01-17 17:53 2.6.24-4-generic
drwxr-xr-x 7 root root 4096 2008-01-25 18:40 2.6.24-5-generic

```

As you can see each kernel release has its own directory.  I think in theory it would be possible to share modules across releases but that would cause problems that end users would have a hard time diagnosing.

You switched to the driver provided by the restricted drivers manager so that fixed the problem.  The only thing you have to worry about from now on is that the appropriate linux-restricted-modules package must be upgraded whenever you upgrade.  Walkerk's script always does that.  But you must also upgrade nvidia-glx-new to the latest release each time you upgrade.  Walkerk's script asks for that and you must answer that you **want** it to upgrade this package.

---

### Post by lemurian on 2008-01-31
> **Gigamo said:**
> Few questions before I do this upgrade again on my fresh install;

- I installed the NVIDIA driver with the manual installer from their site this time (no envy or nvidia-glx-new package). How will this work/what will I have to do in the new kernel?

- I use a program called "btnx" from someone here on the forums to give my MX Revolution mouse better functionality; does anyone know if this works flawlessly in the new kernel still?

Thanks!
I use btnx.  No problem at all with 2.6.24-5.

---

### Post by Gigamo on 2008-01-31
Yep, working fine here too.

I do have an nvidia driver issue though, or I don't know if it's nvidia related; but my laptop stays in powersaving mode when running a game. That wasn't so in my previous kernel, and as a result, my game runs laggy.

---

### Post by lemurian on 2008-01-31
> **Gigamo said:**
> Yep, working fine here too.

I do have an nvidia driver issue though, or I don't know if it's nvidia related; but my laptop stays in powersaving mode when running a game. That wasn't so in my previous kernel, and as a result, my game runs laggy.
Hmm... I don't play any kind of GPU-intensive game in Linux so I don't know how the laptop should behave under those conditions.

Is it your CPU which is being throttled down or your GPU?  How do you check that the laptop is in powersaving mode?

---

### Post by Gigamo on 2008-01-31
> **lemurian said:**
> Hmm... I don't play any kind of GPU-intensive game in Linux so I don't know how the laptop should behave under those conditions.

Is it your CPU which is being throttled down or your GPU?  How do you check that the laptop is in powersaving mode?

I think it's the CPU. The GPU was running on performance speeds when I checked right after killing the game (Warcraft 3 in cedega in this case). I suspect the CPU because my fans in the laptop don't spin loud at all while playing, usually theyre very loud while playing wc3 (in the old kernel).

---

### Post by lemurian on 2008-01-31
> **Gigamo said:**
> I think it's the CPU. The GPU was running on performance speeds when I checked right after killing the game (Warcraft 3 in cedega in this case). I suspect the CPU because my fans in the laptop don't spin loud at all while playing, usually theyre very loud while playing wc3 (in the old kernel).
What does cpufreq-info tell you when you run it?

---

### Post by Gigamo on 2008-02-01
That tells me what I suspected: My cpu is only running at 1.20Ghz when in WC3, while it should run at 2.4Ghz (what it usually did as well in the normal kernel). Is this something fixable?

---

### Post by lemurian on 2008-02-01
> **Gigamo said:**
> That tells me what I suspected: My cpu is only running at 1.20Ghz when in WC3, while it should run at 2.4Ghz (what it usually did as well in the normal kernel). Is this something fixable?
Can you cut and paste the output of cpufreq-info?  That would provide substantial clues to help figure out what is going on.  It is enough to cut and paste the information for one core.

---

### Post by Gigamo on 2008-02-01
> **lemurian said:**
> Can you cut and paste the output of cpufreq-info?  That would provide substantial clues to help figure out what is going on.  It is enough to cut and paste the information for one core.

Sure;

```
[~] cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 2.40 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within 800 MHz and 2.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 2.40 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within 800 MHz and 2.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

```

---

### Post by lemurian on 2008-02-01
Gigamo, the output looks fine.  "ondemand" is the correct governor to use.  The steps and ranges look fine.  Do you have powernowd or any other frequency scaling daemon?  If you do have those daemons running, can you turn them off and see whether you still have the problem you noted?  There might be interference between the kernel modules and daemons.

---

### Post by Gigamo on 2008-02-01
> **lemurian said:**
> Gigamo, the output looks fine.  "ondemand" is the correct governor to use.  The steps and ranges look fine.  Do you have powernowd or any other frequency scaling daemon?  If you do have those daemons running, can you turn them off and see whether you still have the problem you noted?  There might be interference between the kernel modules and daemons.

Well I turned of the powernowd daemons nog, I'll report how it went.

---

### Post by Gigamo on 2008-02-01
Hmm, well. It was a bit random. At some times the speed would be 2.0GHz, 1.6GHz, etc, but at other times it'd still be only 800MHz. With the previous kernel it stayed at fullspeed the entire duration of the game. This is weird.

---

### Post by lemurian on 2008-02-01
I would expect the ondemand governor to be good enough to keep your CPU at %100 while the game is running but maybe they've changed the logic in the latest kernel or something...  As I said, I don't run CPU or GPU-intensive games in Linux.  Maybe you should manually switch to the performance governor while gaming and return it to ondemand when you are not gaming.  

For a while I used a tool that would do that automatically on my previous laptop (a Dell).  I think it was called cpufreqd.  The tool I was using was configurable to switch governors automatically depending on a series of conditions.  One of those conditions could be which processes are running.  For instance, I had it configured so that it would switch to the performance governor if any movie player was running.

I had to stop using it though because my machine had a problem with CPU throttling.  Sometimes, the kernel would "forget" what frequencies the CPU accepted and would keep the CPU stuck at the lowest frequency! I've never reinstalled it even after I switched computers.

---

### Post by Gigamo on 2008-02-01
How can I manually change the governor? That sounds reasonable to me.

---

### Post by Gigamo on 2008-02-01
Hmm, I installed cpufreqd (which prompte dto uninstall powernowd) and now my cpu frequency is locked to 2GHz, and governor is on "performance", and I have no idea how ot go back to ondemand. Also, perforamcne should be 2.4ghz, no?

Edit: Rebooted and the governor is now back at ondemand, using cpufreqd daemon. Will see later how it acts ingame.

---

### Post by lemurian on 2008-02-01
> **Gigamo said:**
> Hmm, I installed cpufreqd (which prompte dto uninstall powernowd) and now my cpu frequency is locked to 2GHz, and governor is on "performance", and I have no idea how ot go back to ondemand. Also, perforamcne should be 2.4ghz, no?

Edit: Rebooted and the governor is now back at ondemand, using cpufreqd daemon. Will see later how it acts ingame.
Observations:

1. You can only have one running daemon which messes with cpu frequencies so cpufreqd and powernowd cannot run at the same time.  That's normal.

2. As long as you have cpufreqd running, switching your governor will do nothing good because cpufreqd will reset it to whatever it thinks it should be.  In other words, if you change your governor manually while you cpufreqd is running, you're going to end up fighting with cpufreqd for control of the frequency settings.

3. If cpufreqd is installed and you want to change your governor in an ad hoc fasion, you first must turn off cpufreqd:

$sudo /etc/init.d/cpufreqd stop

And then you must use cpufreq-set to switch the governor (use man to see how cpufreq-set works).

4. Regarding the maximum frequency that performance should work with, see the documentation for cpufreq-set.  There is settable maximum and minimum limit that I think *all* governors must respect, even the performance one.

---

### Post by TD-Linux on 2008-02-01
Hmm, well I fixed a lot of problems by realizing I was using 386 kernel and switching to generic. However, I still have a few problems:

kpowersave says I have 3 processors, while I only have 2. The 3rd processor is grayed out and is at 0 MHz.

I successfully switched from ipw3945 to iwl3945, but upon resuming from sleep, wireless dies and requires a restart.

Obviously, the latter is far more important than the former, especially because I usually prefer never to turn my laptop off. I used to suspend/restore my old thinkpad for weeks at a time, but in Ubuntu, something always dies. Not sure whose fault it is though, especially because of the vastly different hardware of the two machines.

---

### Post by BladeMelbourne on 2008-02-02
Hi Everyone,

I loosely followed these instructions to update my PPC G4 mac mini.
I still have my 2.6.22 kernel installed, and have setup yaboot (ppc equivalent of grub) to be able to boot both 2.6.24 and 2.6.22. I also have the Hardy version of udev, which also works on Gutsy 2.6.22.

After selecting the 2.6.24 kernel, it starts detecting/probing hardware and at least a page of text scrolls by. It then stops immediately after displaying the line saying something like "eth0 up full duplex 100 mbps". I can still use the keyboard, but can't do anything except Ctrl-Alt-Delete; which results in a normal restart.

I installed the new b43 fwcutter, which downloaded the new firmware. I also edited 70-persistent_net.rules to refer to b43. Still hung on boot.
I tried commenting-out the wireless adapter out of 70-persistent_net.rules altogether, however the result was the same. I don't use wireless, so I'm fine if it's not working.

/var/log/messages does not contain anything when attempting to boot 2.6.24.

I realise my arch is different from you guys, however does anyone have any tips or suggestions?

I just compiled the latest open ATI driver from GIT, which finally works on my hardware, however the machine hard-locks when I exit/logout of X. I figure it might be a DRI/DRM thing which might be fixed in 2.6.24.

TIA,

Mike

---

### Post by snakeeyes on 2008-02-02
> **BladeMelbourne said:**
> Hi Everyone,

I loosely followed these instructions to update my PPC G4 mac mini.
I still have my 2.6.22 kernel installed, and have setup yaboot (ppc equivalent of grub) to be able to boot both 2.6.24 and 2.6.22. I also have the Hardy version of udev, which also works on Gutsy 2.6.22.

After selecting the 2.6.24 kernel, it starts detecting/probing hardware and at least a page of text scrolls by. It then stops immediately after displaying the line saying something like "eth0 up full duplex 100 mbps". I can still use the keyboard, but can't do anything except Ctrl-Alt-Delete; which results in a normal restart.

I installed the new b43 fwcutter, which downloaded the new firmware. I also edited 70-persistent_net.rules to refer to b43. Still hung on boot.
I tried commenting-out the wireless adapter out of 70-persistent_net.rules altogether, however the result was the same. I don't use wireless, so I'm fine if it's not working.

/var/log/messages does not contain anything when attempting to boot 2.6.24.

I realise my arch is different from you guys, however does anyone have any tips or suggestions?

I just compiled the latest open ATI driver from GIT, which finally works on my hardware, however the machine hard-locks when I exit/logout of X. I figure it might be a DRI/DRM thing which might be fixed in 2.6.24.

TIA,

Mike
Did u try pressing ctrl+alt+f1 and see if that takes u to a console based login screen? If it does then that means u didn't install your vga card drivers. In the console login screen, login as a regular user and reconfigure xserver to use the vesa drivers and install the latest vga card drivers for your card.

sudo dpkg-reconfigure xserver-xorg

---

### Post by BladeMelbourne on 2008-02-02
Hi - quick response!

It's not video driver related (they don't even get a chance to load, nor do any services). Switching to another terminal just shows a blinking "_" in the top left hand corner.

After just booting 2.6.22 - I can see that immediately after the eth0 line is where the kernel starts to look at /dev/hda4 which is my root partition.

So maybe it's not network related, maybe it can't access/mount my root partition. Which would explain why there's nothing inside /var/log/messages - it's too early in the process.

I just have an IDE disk (modprobe ide_core I believe). I noticed in an earlier post that someone's drive designations changed with the 2.6.24 kernel due to new drivers.

Would it be possible that under 2.6.24, my /dev/hda has now become /dev/sda - however my boot configuration (and /etc/fstab) is still pointing to /dev/hdaX? I might test this theory with a Hardy bootable CD tomorrow.

Mike

---

### Post by snakeeyes on 2008-02-02
You can try changing your fstab to sda if u like and then tell us what happens.

---

### Post by _VWV_ on 2008-02-02
Hi!
Sorry if it was discussed before..
I failed to compile some additional modules for the 2.6.24 kernel. I  did:
cd /usr/src/linux-headers-2.6.24-5-generic
sudo make menuconfig (and marked the needed modules there)
sudo make -k && make modules_install
it returned something like that ( sorry, I've got russian-language console in case my translation is totally wrong): 
no rules to build the target `arch/x86/kernel/asm-offsets.c` needed for `arch/x86/kernel/asm-offsets.s'.
and 2-d error [prepare0].
I installed gcc++ fro hardy's repos, but it didn't help. 
What should I do to compile a kernel module for 2.6.24?

---

### Post by Ernie79 on 2008-02-02
Hi,

After upgrading, there are problems with Amarok and Totem.
In particular playing mp3 and DVDs.
The codes which were installed before seem to be gone.
So I've tried to remove to new kernel and go back to 2.6.22-14-generic.
Unfortunately still the same.
The package manager complains about a broken package:
 libwxgtk2.6-0 (>= 2.6.3.2.1.5ubuntu12)

How can this be resolved?

Regards
Eric

---

### Post by paxmark1 on 2008-02-03
Slick, no problems with 2.4 celeron and sis cheap  video onboard.  Not using wlan at present.  I did have to do the lusb, but appreciate getting a newer version of udev.  

Is this some plot to get data for the hardy migration from us who arent't up to alphas.  Or just something for us with an itch to test some boundaries.  Either way, it works well for me.  Thanks

---

### Post by walkerk on 2008-02-03
> **paxmark1 said:**
> Slick, no problems with 2.4 celeron and sis cheap  video onboard.  Not using wlan at present.  I did have to do the lusb, but appreciate getting a newer version of udev.  

Is this some plot to get data for the hardy migration from us who arent't up to alphas.  Or just something for us with an itch to test some boundaries.  Either way, it works well for me.  Thanks

Just for those interested in "testing some boundaries"... :)

---

### Post by Gigamo on 2008-02-03
I've got a question. I'm thinking to do a dist-upgrade to hardy, but will it upgrade the kernel once more or will it keep the kernel since it's the same one? If it would keep it that would be great, that's one less issue that could cause breakage then.

---

### Post by Ernie79 on 2008-02-03
"Testing boundaries?" Not really.
The MP3s are working now.
I suppose the file /etc/apt/sources.list.d/hardy.list kept telling apt that there is a later version of libxine1 than the one compatible with Amarok, name 1.1.7-1 and  1.1.10.
Anyway, the file is gone and libxine1 installed as expected.

DVD/VCD playback is working but somehow the menus are not showing up using totem.

Thanks goes to reassuringlyoffensive's post
> [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by fuoco on 2008-02-04
I am using 2.6.24 kernel on gutsy on a powerpc laptop (iBook) and mostly everything is good. There's one small thing I noticed which is quite annoying and I couldn't understand:
this laptop doesn't work with ondemand governor it has to use a userspace daemon. By default on gutsy and previous versions there's powernowd which works just great. 
The problem is that with 2.6.24 powernowd will not autostart anymore, and then i get no cpufreq. I can still manually run the daemon in a terminal and everything is great. So i thought the problem lies in the init scripts or system - but couldn't find out exactly what's wrong and how could that be related to a kernel change. 
Any ideas anyone?

---

### Post by Hero of Time on 2008-02-04
I updated to the latest hardy kernel, 24-5, and above all expectations, my wireless works. I didn't expect that, though hoped it would. I renamed the 70-persistent-net.rule file to .gutsy so I had a backup of the file in case it wouldn't work, but it does. And best of all, the wifi works in the old kernel too, with the ipw driver instead of the iwl. Also, I managed to get my video back to normal. I followed the guide on cchtml.com and I forgot to blacklist the old modules. Now in the hardy kernel and gutsy kernel, video works as it should. Too bad the booting is still slow, both kernels wait about 15 seconds at the beginning (after about 14 seconds in boot process).

---

### Post by walkerk on 2008-02-04
> **Hero of Time said:**
> I updated to the latest hardy kernel, 24-5, and above all expectations, my wireless works. I didn't expect that, though hoped it would. I renamed the 70-persistent-net.rule file to .gutsy so I had a backup of the file in case it wouldn't work, but it does. And best of all, the wifi works in the old kernel too, with the ipw driver instead of the iwl. Also, I managed to get my video back to normal. I followed the guide on cchtml.com and I forgot to blacklist the old modules. Now in the hardy kernel and gutsy kernel, video works as it should. Too bad the booting is still slow, both kernels wait about 15 seconds at the beginning (after about 14 seconds in boot process).

Good to hear...

---

### Post by Hero of Time on 2008-02-04
I checked what version of the iwl driver it uses, and instead of the 1.1.0 on the previous kernel, it uses a newer version, 1.1.17. Still not the latest version, as that is 1.2.24, but they are getting there ;).

And Hibernate works, with 2 gig of RAM and a swap partition of 1.1 gig (not all RAM in use, only about 400 MB, maybe less, didn't check). Must be the work of the wifi driver.

---

### Post by CazperII on 2008-02-05
I upgraded my kernel to 2.6.24 a while ago and it's working out great (finally sleep/hibernate works) But with the latest software update Ubuntu wants to install the 2.6.22-14 kernel. Is there a way to blacklist the kernel updates, so that for the time being they don't show up in the software update icon?

---

### Post by octopuskevin on 2008-02-05
> **CazperII said:**
> I upgraded my kernel to 2.6.24 a while ago and it's working out great (finally sleep/hibernate works) But with the latest software update Ubuntu wants to install the 2.6.22-14 kernel. Is there a way to blacklist the kernel updates, so that for the time being they don't show up in the software update icon?

yeh i believe if you load up synaptic and under 'package' you can lock the version in place... should stop asking you about an upgrade

---

### Post by sistoviejo on 2008-02-05
Hello,
I did the update with the second method and it worked flawlessly. Thank you.
I have a little doubt though. Update manager is now showing me these 3 updates available:
```
linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-image-2.6.22-14-generic
```
Along with other updates. What should I do?
Thanks again.
BTW this is the output of uname -a ... 
```
Linux silvio-linux 2.6.24-3-generic #1 SMP Thu Jan 3 23:30:29 UTC 2008 i686 GNU/Linux
```

---

### Post by Nunslaughter on 2008-02-06
I used the script to update and it works great! My wireless finally works decent after 9 months!! And my graphics card shows up 7°C cooler then before...

Dell XPS m1710
c2d t7200 @ 2ghz
2gb ddr2 ram
geforce go 7900 gs
intel 4965agn wifi

---

### Post by Hero of Time on 2008-02-06
The reason that the older kernel is shown, is because if you kept the 2.6.22 kernel, there is a new version for it. I had my system up2date on Monday and it didn't show then. I have 2.6.22-14.47 installed, and build 51 is now available. Something to easily see, if you know where to look ;).

sistoviejo, you still have an older kernel. We are now on the 2.6.24-5. Either update manually, or use the script (personally I prefer manually).

---

### Post by nilarimogard on 2008-02-06
I upgraded to 2.6.24-5

Asus A7N8X-X 
AMD Athlon XP 2800+
ATI Radeon 9600

And worked, i guess, but:

-it autodetected my video card as being nvidia, while my card is ati. I manually installed ati and worked
-now my hard disks are sda and sdb not hda and hdb... until now i only needed to fix conky because of that, but i hope there won't be any problems with anything else

---

### Post by sistoviejo on 2008-02-06
> **Hero of Time said:**
> The reason that the older kernel is shown, is because if you kept the 2.6.22 kernel, there is a new version for it. I had my system up2date on Monday and it didn't show then. I have 2.6.22-14.47 installed, and build 51 is now available. Something to easily see, if you know where to look ;).

sistoviejo, you still have an older kernel. We are now on the 2.6.24-5. Either update manually, or use the script (personally I prefer manually).

thanks! 
Is it possible to remove the old kernel and enable autoupdate for the newer kernel?

---

### Post by nilarimogard on 2008-02-06
Yeah i want to delete the old kernel too, and also make it not show up when booting, but i'm not sure what i have to delete.

---

### Post by El_Belgicano on 2008-02-06
> **nilarimogard said:**
> Yeah i want to delete the old kernel too, and also make it not show up when booting, but i'm not sure what i have to delete.

To remove it from the boot up, you have to edit your /boot/grub/menu.lst:
```
sudo (nano/gedit/whatevertexteditor) /boot/grub/menu.lst
```
and remove the line with the old kernel in the list at the end of the file.
remove the old kernel: maybe in the synaptic package manager? only a guess.

---

### Post by Hero of Time on 2008-02-06
Removal of older/unwanted kernels can be done from synaptic or use apt-get remove <full kernel name and version>. Then, after the removal, it is also removed from the grub list.

---

### Post by nilarimogard on 2008-02-06
> **Hero of Time said:**
> Removal of older/unwanted kernels can be done from synaptic or use apt-get remove <full kernel name and version>. Then, after the removal, it is also removed from the grub list.

And that will remove everything from the old kernel? Also, will it change/remove something in the new kernel and system configuration?

Edit: Also do you have any idea what's Ubuntu 7.10 Gutsy default full kernel name and version? :)

---

### Post by Hero of Time on 2008-02-06
> **nilarimogard said:**
> And that will remove everything from the old kernel? Also, will it change/remove something in the new kernel and system configuration?

Edit: Also do you have any idea what's Ubuntu 7.10 Gutsy default full kernel name and version? :)
When removing the old kernel, all settings in that kernel will be removed, but systemwide settings are kept of course. All modules and stuff that resides in the various folders with the kernel name in it will be removed.
For removal of the Gutsy kernel, best to open synaptic and look for every kernel thing with version similar to 2.6.22 (-14-generic is mostly the full name, but other versions might be installed like 386 instead of generic). Kernell .22 is the Gutsy one. You can also boot to the old kernel, then sudo apt-get purge *${uname -r} or similar, don't know the correct uname -r variable use (purge will also remove config files, if any). Synaptic is the safest way.

---

### Post by nilarimogard on 2008-02-06
Thank you. The answer was in the first post, where it said how to remove this new kernel, i just had to change the kernel version to the one you said Gutsy has, so i used this:

sudo apt-get remove linux-image-2.6.22-14-generic linux-headers-2.6.22-14-generic linux-headers-2.6.22-14 linux-restricted-modules-2.6.22-14-generic linux-ubuntu-modules-2.6.22-14-generic

Reboot, and voila! :)

---

### Post by kamleshb on 2008-02-07
I'm having a major problem viewing videos, either.WMV or .MPG, with mplayer, VLC, or Totem.  The minor problem is that the video does not appear on the player window.  If I force it to full screen, then I can see the video, the first time.  The second time or third time I watch a video, either the same one or a different one, a console type screen appears, similar to Ctrl-Alt-F8, displaying my start-up messages.  If I enter any key strokes, such as Ctrl-Alt-F1, the screen goes black, and this text message appears:

fglrx (8.452.1): Already installed on this kernel.

The laptop does not respond.  I need to depress the power button for 10 seconds or so to bring my computer back.

I've tried re-running hardy.py and envy, but I have the same results.

IBM ThinkPad T42
ATI Radeon Mobility 9600 M10

---

### Post by sir4taye on 2008-02-07
I can't get the restricted drivers manager to run b43-fwcutter. It automatically reverts to selecting the previously deselected bcm43XX-fwcutter, which having blacklisted brings me no wireless settings access. The upgrade to 8.04 worked smooth as butter. I could never get my broad chip to run with ubuntu, though I push the os like water by the sea. 

AMD athlonx2 64bit 1gram(64m of which is shared to the nvid 6100 compaq presario f730us with nvid chipset

---

### Post by jimbojones on 2008-02-07
Question on iwl3945
I am trying to update to the latest iwl3945 drivers from [http://intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi)
since I installed the developmental kernal.

I get to the point where I have I untar /iwlwifi-1.2.25.tgz and cd, then MAKE and i return an error **"Kernel Makefile not found at '/lib/modules/2.6.24-5-generic/source'"**
Any hints on where to go from here?  I checked that directory and there is indeed no makefiles in that directory. :confused:

---

### Post by Hero of Time on 2008-02-07
> **jimbojones said:**
> Question on iwl3945
I am trying to update to the latest iwl3945 drivers from [http://intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/index.php?p=iwlwifi&n=howto-iwlwifi)
since I installed the developmental kernal.

I get to the point where I have I untar /iwlwifi-1.2.25.tgz and cd, then MAKE and i return an error **"Kernel Makefile not found at '/lib/modules/2.6.24-5-generic/source'"**
Any hints on where to go from here?  I checked that directory and there is indeed no makefiles in that directory. :confused:
I that that problem too. But why do you want to compile a newer version? Version 1.1.17 is working just fine for me. I did end up with the same error when I tried to compile it though. I really have no idea what file it wants. If you haven't done so already, update to the 24-7 kernel.

Edit:
Don't update to the 24-7 kernel yet, if you don't see the kernel-modules package for it. I installed it, and don't have wireless anymore because of the missing module package. It seems they need to build that one.
Edit2:
Never mind, package is available again. Iwlwifi is at 1.2.0 now, but not working properly for me atm.

---

### Post by Hero of Time on 2008-02-08
If anyone wants to get rid of some boot error messages about Powernowd and AppArmor failing to load, just install the version from the Hardy repo and everything will be ok again.

---

### Post by jimbojones on 2008-02-08
> **Hero of Time said:**
> I that that problem too. But why do you want to compile a newer version? Version 1.1.17 is working just fine for me. I did end up with the same error when I tried to compile it though. I really have no idea what file it wants. If you haven't done so already, update to the 24-7 kernel.

Edit:
Don't update to the 24-7 kernel yet, if you don't see the kernel-modules package for it. I installed it, and don't have wireless anymore because of the missing module package. It seems they need to build that one.

I was trying to update because of some wireless problems with a few programs I run (airmon-ng for example).  What about using the old ipw3945?  could i blacklist the new driver and revert back to the old somehow?

edit.  I also seems to get errors when using make **Makefile:56: 'make SHELL=/bin/bash**

---

### Post by Hero of Time on 2008-02-08
If you want to revert back to the IPW driver, then you need to compile it for the Hardy kernel. You might end up with the same errors.
The error about /bin/bash is only an enviromental setting for make, the default shell isn't set to /bin/bash (perhaps /bin/sh). If you get errors when using shell=/bin/bash, then there might be an error in the bash program on the line mentioned. You can look for a fix, but I don't have it.
Have you searched for errors you get when running the programs you are having problems with? It might not be the driver but the interfaces (as wmaster0 is added).

---

### Post by psychos on 2008-02-08
Here's what I consider a better way to have the Hardy repositories present (and **IMPORTANT DOWNGRADE INFORMATION** at the end of my post, because the current method does not account for dependencies like libc6 that get upgraded along with your kernel):

1. Edit your "/etc/apt/sources.list". Add a line for:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse

2. Edit (or create) "/etc/apt/preferences". Add the following:
Package: *
Pin: release a=hardy
Pin-Priority: 400

3. Run "apt-get update".

4. Install packages with the "-t hardy" option to apt-get. The following will get you a "generic" Hardy kernel (you can replace "generic" with "rt" or whatever):
apt-get -t hardy install linux-image-generic linux-headers-generic linux-restricted-modules-generic

5. To keep up to date, occasionally repeat step 4 with the same packages that you installed. See below for why this cannot be automated.

Using this method pins the Hardy packages below the default target release. So an apt-get upgrade or dist-upgrade will not upgrade to any Hardy packages.

Unfortunately, there isn't a way to pin packages with a wildcard in the name or by maintainer (or one could do "linux-image*" or "Ubuntu Kernel Team*".) Since the kernel packages change names when there's a new version (e.g. "linux-image-2.6.24-7-rt" will change to "linux-image-2.6.24-8-rt"), this means you can't automatically have apt-get upgrade your Hardy kernel images along with the rest of your packages. So you need to issue an "apt-get -t hardy install ..." once in a while to pull the latest Hardy packages.


**IMPORTANT DOWNGRADE INFORMATION:**
Whichever method you use, apt-get WILL NOT automatically downgrade other packages that have been upgraded even if you remove the kernel packages that you manually installed. This means that packages like libc6 and module-init-tools will stay at the Hardy version, even if you remove the kernel packages you have installed.

To downgrade these packages back to your current release:

1. Make sure you don't have the Hardy repositories present in your "/etc/apt/sources.list" (see step 1 of installation.)

2. Edit "/etc/apt/preferences" to contain the following, and delete any references to Hardy:
Package: *
Pin: release v=7.10
Pin-Priority: 1100

Note that the release should be changed for whatever release you are using (eg., 7.04 for feisty, 7.10 as shown for gutsy.) You should specify this by version number and not by name because otherwise you need separate entries for gutsy, gutsy-updates, etc.

3. Run "apt-get dist-upgrade". This will downgrade your packages, and if you have the "linux-image-..." and so on metapackages installed, should also remove the Hardy kernel components if still present.

4. Edit "/etc/apt/preferences" and remove the pin you added in step 2, or just remove the file completely. You should now be back at your current release.

---

### Post by Kyran on 2008-02-08
Updated from 2.6.24-2 to 2.6.24-7 and now it can't see that its connected to a network (so no internet), and the shutdown menu doesn't work. All the other kernels installed also have this problem.

EDIT: Concurrent booting was the problem.

---

### Post by portach king on 2008-02-09
Hey guys, 
I'm constantly running up against this problem.
>  Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. 
Anyone else finding this happening too? Can someone explain why, maybe even help me fix the problem?

I'd also like to point out that I can't figure out how to install the drivers for my ati card. Restricted drivers don't work (as I'm assuming they're designed for 2.6.22), Envy won't install (Build error??) and I can't install Catalyst 8.1 (or any other previous version) because trying to install the dependencies brings up the above message too.
I look forward to hearing back from someone.

---

### Post by Hero of Time on 2008-02-09
> **portach king said:**
> Hey guys, 
I'm constantly running up against this problem.

Anyone else finding this happening too? Can someone explain why, maybe even help me fix the problem?

I'd also like to point out that I can't figure out how to install the drivers for my ati card. Restricted drivers don't work (as I'm assuming they're designed for 2.6.22), Envy won't install (Build error??) and I can't install Catalyst 8.1 (or any other previous version) because trying to install the dependencies brings up the above message too.
I look forward to hearing back from someone.

For installing your ATi driver, check this site: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
It helped me for installing the driver correctly on both gutsy and hardy kernel.

---

### Post by portach king on 2008-02-09
Hey Hero of Time,
Thanks for the link, however it brought me back to my first error (ie. the message I posted above). When I try to install "build-essential" I get the above quoted error and:
```
Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed 
```

Very confusing.

---

### Post by Hero of Time on 2008-02-09
Then install the components. I have them installed. Install them manually. I originally installed the driver on the Gutsy kernel, then when on the Hardy kernel, I only had to make sure DKMS had installed the kernel components correctly. On the first install, it appeared it wasn't, but when I removed the kernel-source package and re-installed it from the packages I got when on the Gutsy kernel, it worked just fine.

---

### Post by portach king on 2008-02-09
> **Hero of Time said:**
> Then install the components. I have them installed. Install them manually. I originally installed the driver on the Gutsy kernel, then when on the Hardy kernel, I only had to make sure DKMS had installed the kernel components correctly. On the first install, it appeared it wasn't, but when I removed the kernel-source package and re-installed it from the packages I got when on the Gutsy kernel, it worked just fine.

Sorry, you're probably going to think Im an idiot but, I don't understand what you mean.

---

### Post by pja1728 on 2008-02-09
I'm way too new at this, so maybe off-topic.

I updated Gutsy to the Hardy kernel to get my wifi working - thanks for the posts - it worked a dream.

Trouble is I now want Wine installed and am running 64-bit Kubuntu. Wine refuses to install because of dependencies which seems to come down to the libc6 package being version 2.7-5ubuntu2 instead of 2.6.1-1ubuntu10

Is that a consequence of the upgraded kernel? If so would forcing the older version wreck the upgrade? My wifi is far more important to me than Wine.

Is there a work around using Hardy dependencies for Wine?

---

### Post by Gigamo on 2008-02-09
> **pja1728 said:**
> I'm way too new at this, so maybe off-topic.

I updated Gutsy to the Hardy kernel to get my wifi working - thanks for the posts - it worked a dream.

Trouble is I now want Wine installed and am running 64-bit Kubuntu. Wine refuses to install because of dependencies which seems to come down to the libc6 package being version 2.7-5ubuntu2 instead of 2.6.1-1ubuntu10

Is that a consequence of the upgraded kernel? If so would forcing the older version wreck the upgrade? My wifi is far more important to me than Wine.

Is there a work around using Hardy dependencies for Wine?

Have you tried compiling from source?

---

### Post by Hero of Time on 2008-02-09
Portach King:
What I mean is install those dependencies manually via synaptic. You can use the Gutsy repo. Usually, when you want to update the kernel, you are also asked to update the libc package, at least, that was in my case.

Pja1728:
There shouldn't be a problem with the kernel upgrade and Wine. I got Wine running just fine when I installed it on Gutsy. Perhaps it's wise to boot to the Gutsy kernel, then install Wine and boot back to Hardy.

---

### Post by pja1728 on 2008-02-09
> **Hero of Time said:**
> 

Pja1728:
There shouldn't be a problem with the kernel upgrade and Wine. I got Wine running just fine when I installed it on Gutsy. Perhaps it's wise to boot to the Gutsy kernel, then install Wine and boot back to Hardy.

Thanks. I reset to Gutsy kernel and had the same problem so I guess that shows it's not the kernel upgrade causing the problem. I'll try a different thread. Meanwhile I'm going back to Hardy to keep the wifi alive.

Gigamo: I haven't tried compiling from source. In theory it's not necessary, but the theory isn't working, so it's got to be worth a try.

---

### Post by portach king on 2008-02-09
Thanks for the clarification Hero of Time. I actually managed to get it installed in the meantime anyway! : )
But now onto the next problem... :(
I can't get any video playback while compiz is running. It's fine in metacity, but as soon as I activate compiz I get a black image where the video should be. I can even hear the audio. Anybody else with this slightly more amusing problem?

---

### Post by Hero of Time on 2008-02-10
I never had this problem, but when compiz-fusion was running, I ended up with only half of the video. It was sliced in half diagonally and would flicker a lot. That was only when I set the output to OpenGL I think. OpenGL gives better video quality, but X11 should work just fine. What video player do you use? Did you also run the aticonfig --overlay=Xv? I don't run compiz anymore, since it wasn't very useful and some Wine apps would crash when starting.

---

### Post by Gigamo on 2008-02-11
How is 2.6.24-7? Safe to upgrade?

---

### Post by Hero of Time on 2008-02-11
If you have the Intel Pro Wireless 3945, no, it's not safe. The driver modules, 1.2.0, does not work correctly. At least for me. Rest it looked fine.

---

### Post by Gigamo on 2008-02-11
> **Hero of Time said:**
> If you have the Intel Pro Wireless 3945, no, it's not safe. The driver modules, 1.2.0, does not work correctly. At least for me. Rest it looked fine.

I do. Thanks for letting me know. XD

---

### Post by lemurian on 2008-02-12
> **Gigamo said:**
> How is 2.6.24-7? Safe to upgrade?

For the benefit of those who don't have the Intel Pro Wireless 3945:  2.6.24-7 works fine for me.

---

### Post by walkerk on 2008-02-12
I've backed away from b43 (native wireless driver).... I'm back with ndiswrapper... just seems a bit quicker and less laggy... :/

---

### Post by Gigamo on 2008-02-12
> **walkerk said:**
> I've backed away from b43 (native wireless driver).... I'm back with ndiswrapper... just seems a bit quicker and less laggy... :/

How do I do this with an ipw3945/does this work with it? Since I'm having some issues with my wireless connection under linux, I think it could be because of that. Also, with then using ndiswrapper instead of the IPW3945 module, will 2.6.24-7 work fine?

---

### Post by Hero of Time on 2008-02-13
I've read in another topic that some have their 4965 working with ndiswrapper, so I guess it can be done with the 3945 too. Every nic should work with ndiswrapper, but some are just too broken or complex for it to work.
What driver did work for you correctly? You might be able to compile that version for the .24 kernel. All I know is that I have no problems whatsoever with this wireless card.

---

### Post by Gigamo on 2008-02-13
> **Hero of Time said:**
> I've read in another topic that some have their 4965 working with ndiswrapper, so I guess it can be done with the 3945 too. Every nic should work with ndiswrapper, but some are just too broken or complex for it to work.
What driver did work for you correctly? You might be able to compile that version for the .24 kernel. All I know is that I have no problems whatsoever with this wireless card.

Well, none of the intel ifw3945/ipw3945 have worked without this bug.

The bug being my speed limit capped at 130kb/s at times, while I have a 20Mbit connection, and on windows (and sometimes on linux, like it should be), I download at 2Mb/s. So when I for example download a file that I'm sure I get max speed at on windows, it will be capped at 120kb/s, and my internet overall feels totally slow and choked (because the download is taking 120 of the 130 max). And at another time, for example if I restart networking/wicd, for a short time my speed will be normal. It's weird.

---

### Post by Hero of Time on 2008-02-13
That is strange. I can download with full speed on my ipw3945. I got a top speed of about 3 MB/s. That was with the ipw3945 driver. I don't know about the iwlwifi driver, but I asume it will be the same. This was with about 3-4 meters from the AP.

---

### Post by walkerk on 2008-02-13
> **Gigamo said:**
> How do I do this with an ipw3945/does this work with it? Since I'm having some issues with my wireless connection under linux, I think it could be because of that. Also, with then using ndiswrapper instead of the IPW3945 module, will 2.6.24-7 work fine?

Yes you can get ndiswrapper to work...

You need to make sure you add the following to /etc/modprobe.d/blacklist (in this order) I actually had to create a script in /etc/init.d/ and modprobe -r them...
```

ohci_hcd
ssb

#and your native driver ipw or iwl
ipw4965

```

once you've done that download and follow the instructions from [ndiswrapper.sourceforge.net]("http://ndiswrapper.sourceforge.net")

**ssb conflicts with ndiswrapper and ohci_hcd depends on ssb...**

---

### Post by lime4x4 on 2008-02-13
okay updated a gutsy box to the hardy kernel using your script. Now it wants to download 230 megs worth of updates and among them is the latest kernel for gutsy which is already installed. How do i prevent it from updating?

---

### Post by Hero of Time on 2008-02-13
> **lime4x4 said:**
> okay updated a gutsy box to the hardy kernel using your script. Now it wants to download 230 megs worth of updates and among them is the latest kernel for gutsy which is already installed. How do i prevent it from updating?

If you read the OP till the end, you would know that you have to disable the Hardy repositories after the kernel update. Also, if you get a kernel update when you just updated, there might have been something going wrong with the first update, or you got an older kernel version (you can install either 2.6.24-5 and 2.6.24-7).

---

### Post by lime4x4 on 2008-02-13
i did that here is a copy of my apt.list

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

#AUTOMATIX REPOS START

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
#AUTOMATIX REPOS END

# WICD repository
#deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras
# WICD repository
#deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extrasdeb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras
#deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras


here is what it wants to perform

pammy@pammy-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  acpi-support amarok amarok-xine amor apt apt-utils aptitude at-spi
  bluez-gnome bluez-utils bogofilter-bdb brltty brltty-x11 bug-buddy
  capplets-data compiz compiz-core compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compiz-plugins cpp cupsys cupsys-bsd
  cupsys-client cupsys-driver-gutenprint debhelper deskbar-applet dpkg
  dpkg-dev ekiga eog evince evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins
  evolution-webcal f-spot fast-user-switch-applet file-roller firefox
  firefox-gnome-support gappletviewer-4.2 gcc gcj-4.2-base gconf-editor gconf2
  gconf2-common gdm gedit gedit-common gettext gij gij-4.2 gimp gimp-data
  gimp-python gksu gnome-app-install gnome-applets gnome-applets-data
  gnome-cards-data gnome-control-center gnome-games gnome-games-data
  gnome-keyring gnome-mag gnome-media gnome-mount gnome-nettool gnome-orca
  gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver
  gnome-session gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-utils gnome-volume-manager gnupg gparted grub
  gstreamer0.10-plugins-good gstreamer0.10-x gthumb gtk2-engines
  gtk2-engines-pixbuf gtkhtml3.14 gucharmap hal hal-cups-utils hal-info hpijs
  hplip hplip-data iproute java-gcj-compat kdelibs4c2a kwin lftp libatspi1.0-0
  libbonoboui2-0 libbonoboui2-common libcairo2 libcamel1.2-10 libcupsimage2
  libcupsys2 libcurl3-gnutls libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2
  libegroupwise1.2-13 libexchange-storage1.2-3 libgail-common
  libgail-gnome-module libgail18 libgcj-bc libgcj8-1 libgcj8-1-awt libgcj8-jar
  libgconf2-4 libgimp2.0 libgksu2-0 libgnome-keyring0 libgnome-speech7
  libgnome-window-settings1 libgnome2-canvas-perl libgnomecanvas2-0
  libgnomecups1.0-1 libgnomekbd-common libgnomeprint2.2-0
  libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnutls13 libgs8 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkhtml2-0 libgtkhtml3.14-19
  libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common
  libgtkspell0 libgucharmap6 libgutenprintui2-1 libhsqldb-java libimlib2
  libk3b2 liblocale-gettext-perl libmetacity0 libmono-sqlite2.0-cil libnss3-0d
  libofa0 libopal-2.2 libpam-modules libpanel-applet2-0 libpango1.0-0
  libperl5.8 libpoppler-glib2 libpq5 libpurple0 librarian0 librsvg2-2
  librsvg2-common libsasl2-2 libsasl2-modules libsdl1.2debian
  libsdl1.2debian-alsa libsmbclient libsoup2.2-8 libtracker-gtk0 libtunepimp5
  libvte-common libvte9 libwnck-common libwnck22 libx11-6 libxine1
  libxine1-console libxine1-misc-plugins libxine1-x metacity metacity-common
  nautilus nautilus-cd-burner nautilus-data nautilus-sendto netcat
  notification-daemon ntfsprogs openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-human openoffice.org-writer perl perl-base perl-modules
  perl-suid pidgin pidgin-data pulseaudio pulseaudio-esound-compat python-apt
  python-cups python-glade2 python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnomecanvas python-gobject python-gtk2
  python-gtkhtml2 python-notify python-uno python-vte python2.5
  python2.5-minimal rhythmbox rpm samba samba-common scim scim-gtk2-immodule
  scim-modules-socket scim-modules-table scim-tables-additional smbclient
  smbfs sound-juicer splix ssh-askpass-gnome synaptic system-tools-backends
  tomboy totem totem-gstreamer totem-mozilla tracker tracker-search-tool
  ttf-gentium ubuntu-artwork ubuntu-desktop ubuntu-standard update-notifier
  vino wvdial xbase-clients xorg xsane xsane-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-amd
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-imstt
  xserver-xorg-video-intel xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xutils yelp zenity
The following packages will be upgraded:
  adduser alien alsa-base alsa-utils app-install-data
  app-install-data-commercial apparmor apparmor-utils apport apport-gtk apturl
  aspell avahi-autoipd avahi-daemon base-files base-passwd bash bc bind9-host
  binutils binutils-static bittorrent bluez-cups bogofilter bogofilter-common
  bsdmainutils bsdutils bsh busybox-initramfs bzip2 cdparanoia cdrdao
  cli-common command-not-found command-not-found-data console-setup
  console-terminus console-tools consolekit coreutils cpio cpp-4.1 cups-pdf
  cupsys-common dash dbus dc dcraw debconf debconf-i18n debianutils defoma
  desktop-file-utils dhcdbd dhcp3-client dhcp3-common dictionaries-common
  discover1 discover1-data dnsutils doc-base docbook-xml dosfstools
  dvd+rw-tools e2fslibs e2fsprogs eject esound-common espeak espeak-data
  ethtool fakeroot file findutils fontconfig fontconfig-config foo2zjs
  foomatic-db foomatic-filters freeglut3 fuse-utils gamin gcalctool gcc-4.1
  gcc-4.1-base gcc-4.2-base gdb gdebi gdebi-core genisoimage gettext-base
  ghostscript ghostscript-x gnome-about gnome-accessibility-themes
  gnome-desktop-data gnome-doc-utils gnome-icon-theme gnome-media-common
  gnome-menus gnome-themes gpgv grep groff-base gsfonts gsfonts-x11
  gstreamer-tools gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-tools guidance-backends gzip hdparm hostname human-icon-theme
  hwdb-client-common hwdb-client-gnome info initramfs-tools initscripts
  iptables iputils-arping iputils-ping iputils-tracepath iso-codes java-common
  kdelibs-data klibc-utils klogd language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common laptop-mode-tools less libaa1 libacl1 libao2
  libarchive-tar-perl libart-2.0-2 libart2.0-cil libarts1-akode libarts1c2a
  libartsc0 libasound2 libasound2-plugins libaspell15 libatk1.0-0 libattr1
  libaudio2 libaudiofile0 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1
  libavahi-qt3-1 libavcodec1d libavformat1d libavutil1d libbcel-java
  libbind9-30 libblkid1 libbluetooth2 libbonobo2-0 libbonobo2-common
  libbz2-1.0 libcaca0 libcairo-perl libcairomm-1.0-1 libcdparanoia0 libcomerr2
  libcompizconfig0 libcompress-raw-zlib-perl libcompress-zlib-perl libconsole
  libcucul0 libdatrie0 libdb4.2 libdbus-1-3 libdc1394-13 libdecoration0
  libdeskbar-tracker libdevmapper1.02.1 libdiscover1 libdjvulibre15 libdns32
  libedit2 libeel2-data libenchant1c2a libesd-alsa0 libespeak1 libexif12
  libexpat1 libflac++6 libflac8 libfontconfig1 libfribidi0 libfuse2 libgamin0
  libgc1c2 libgcc1 libgcj-common libgconf2.0-cil libgcrypt11 libgdl-1-0
  libgdl-1-common libgdl-gnome-1-0 libgl1-mesa-dri libgl1-mesa-glx
  libglade2.0-cil libglew1.4 libglib-perl libglib2.0-0 libglib2.0-cil
  libglibmm-2.4-1c2a libglu1-mesa libgmime-2.0-2 libgmime2.2-cil
  libgnome-desktop-2 libgnome-mag2 libgnome-media0 libgnome-menu2
  libgnome-vfs2.0-cil libgnome2-0 libgnome2-common libgnome2-vfs-perl
  libgnome2.0-cil libgnomecanvas2-common libgnomevfs2-bin libgnomevfs2-common
  libgnomevfs2-extra libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpmg1
  libgsf-1-114 libgsf-1-common libgsm1 libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtk2-perl libgtkhtml2.0-cil libgtop2-7 libgtop2-common
  libgutenprint2 libhal-storage1 libhal1 libhunspell-1.1-0 libice6 libidl0
  libidn11 libieee1284-3 libio-compress-base-perl libio-compress-zlib-perl
  libisc32 libisccc30 libisccfg30 libiw29 libjaxp1.3-java libjline-java
  libkeyutils1 libklibc libkpathsea4 libkrb53 liblcms1 libldap2 liblircclient0
  liblog4j1.2-java libltdl3 liblua50 liblualib50 liblwres30 libmagic1
  libmodplug0c2 libmono-cairo1.0-cil libmono-corlib1.0-cil
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-system-data2.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono0 libmono2.0-cil libmysqlclient15off libnautilus-burn4
  libnautilus-extension1 libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libndesk-dbus1.0-cil libnet-dbus-perl libnewt0.52 libnl1-pre6 libnm-glib0
  libnm-util0 libnspr4-0d libnss-mdns libntfs-3g16 libogg0 libopenal0a
  liborbit2 libpam-gnome-keyring libpam-runtime libpam0g libpango1.0-common
  libpaper-utils libpaper1 libpcap0.8 libpcre3 libpcrecpp0 libpisock9
  libpisync0 libpng12-0 libpoppler2 libpostproc1d libpulse0 libqt3-mt
  libraw1394-8 librecode0 librpc-xml-perl librsvg2.0-cil libruby1.8
  libsamplerate0 libsane libscim8c2a libscrollkeeper0 libsdl-image1.2
  libsensors3 libshout3 libslang2 libslp1 libsnmp-base libsqlite3-0 libss2
  libssl0.9.8 libstdc++6 libsvg1 libswscale1d libtag1c2a libtasn1-3 libtheora0
  libtrackerclient0 libusb-0.1-4 libusplash0 libuuid1 libvisual-0.4-0
  libvolume-id0 libvorbis0a libvorbisenc2 libvorbisfile3 libwpd8c2a
  libwpg-0.1-1 libwps-0.1-1 libwww-perl libx11-data libxalan2-java libxaw7
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxcomposite1 libxcursor1
  libxerces2-java libxfont1 libxi6 libxklavier11 libxml-twig-perl libxml2
  libxml2-utils libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxslt1.1
  libxtst6 libxxf86dga1 linux-headers-2.6.22-14
  linux-headers-2.6.22-14-generic linux-image-2.6.22-14-generic
  linux-sound-base login lsb-base lsb-release lshw lsof ltrace makedev man-db
  manpages mcpp mesa-utils mktemp module-init-tools mono-common mono-gac
  mono-jit mono-runtime mount mysql-common nano ncurses-base ncurses-bin
  ndiswrapper-common ndiswrapper-utils-1.9 net-tools netbase ntfs-3g ntpdate
  openoffice.org-java-common openoffice.org-l10n-common openprinting-ppds
  openssh-client openssh-server openssl passwd pciutils pcmciautils po-debconf
  poppler-utils popularity-contest powermanagement-interface powernowd
  pppoeconf procps psmisc python-apport python-bittorrent python-central
  python-dbus python-gconf python-gdbm python-gmenu python-gst0.10
  python-launchpad-bugs python-libxml2 python-numeric python-problem-report
  python-pyorbit python-software-properties python-support python-xml rdesktop
  readahead rss-glx rsync ruby ruby1.8 screen scrollkeeper sed
  shared-mime-info slocate software-properties-gtk ssh ssl-cert startup-tasks
  strace sudo sysklogd system-services sysv-rc sysvutils tango-icon-theme tar
  tasksel tasksel-data tcpdump toshset tsclient ttf-arabeyes ttf-dejavu
  ttf-dejavu-core ttf-dejavu-extra ttf-mgopen ttf-opensymbol ttf-thai-tlwg
  tzdata ubufox ubuntu-keyring ubuntu-minimal ucf unattended-upgrades
  update-inetd update-manager update-manager-core update-notifier-common
  upstart upstart-compat-sysv upstart-logd usbutils usplash util-linux
  util-linux-locales vbetool vim-common vim-tiny vorbis-tools wamerican
  wbritish whiptail whois wireless-tools wodim x-ttcidfont-conf x11-common
  xauth xdg-user-dirs xdg-user-dirs-gtk xdg-utils xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-encodings xfonts-utils xfsprogs xinit xkb-data
  xscreensaver-data xscreensaver-gl xserver-xorg-video-i810 xsltproc zlib1g
534 upgraded, 0 newly installed, 0 to remove and 326 not upgraded.
Need to get 223MB/223MB of archives.
After unpacking 13.7MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by wnelson on 2008-02-13
lime4x4:The following should fix your problems.

sudo rm /etc/apt/sources.list.d/hardy.list

sudo apt-get update

---

### Post by Geezle on 2008-02-13
I just finished upgrading my kernel using the python script, but now that I've rebooted Ubuntu isn't seeing any of my drives.  They're simply not showing up in my /dev folder.  I haven't read through the entire thread yet...there's quite a lot to it, but I'm working my way though, but has anybody else run into this problem?

---

### Post by lime4x4 on 2008-02-13
john@pammy-desktop:~$ sudo rm /etc/apt/sources.list.d/hardy.list
[sudo] password for john:
rm: cannot remove `/etc/apt/sources.list.d/hardy.list': No such file or directory

---

### Post by wnelson on 2008-02-14
lime4x4: What version of ubuntu did you just install? 7.04? 7.10?

---

### Post by Hero of Time on 2008-02-14
> **Geezle said:**
> I just finished upgrading my kernel using the python script, but now that I've rebooted Ubuntu isn't seeing any of my drives.  They're simply not showing up in my /dev folder.  I haven't read through the entire thread yet...there's quite a lot to it, but I'm working my way though, but has anybody else run into this problem?

Check your /dev/ folder. If you have a SATA drive, perhaps your drive names changed from hdx to sdx. I've read about that here.


lime4x4:
What does 'locate hardy' give for response? Else, open Synaptic and go to Settings > Repositories and then the second tab 'Third Party Software'. Uncheck the Hardy repo or remove the line. Unchecking is advised though, as if you want to update, all you have to do is check it, reload and look for the new packages. Then uncheck again when done.

---

### Post by LonelyTraveler on 2008-02-14
I don't know if I'm having a blond moment, but when I click on the upgrade links at the bottom of the thread it opens a page thats exactly the same as the first one. What am I doing wrong?

---

### Post by lime4x4 on 2008-02-14
john@pammy-desktop:~$ locate hardy
/home/pammy/Desktop/hardy.py
/home/john/Desktop/hardy-desktop-i386.iso
/home/john/Desktop/hardy-alternate-i386.iso
/home/john/Desktop/hardy-alternate-i386.iso.part
/var/log/samba/log.john-hardy
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_Release
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg
john@pammy-desktop:~$

---

### Post by LonelyTraveler on 2008-02-14
> **lime4x4 said:**
> john@pammy-desktop:~$ locate hardy
/home/pammy/Desktop/hardy.py
/home/john/Desktop/hardy-desktop-i386.iso
/home/john/Desktop/hardy-alternate-i386.iso
/home/john/Desktop/hardy-alternate-i386.iso.part
/var/log/samba/log.john-hardy
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_Release
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg
john@pammy-desktop:~$

Was this reply for me? 

I got it installed with the second option. My sound even worked right away! Great!

---

### Post by LonelyTraveler on 2008-02-14
Is this kernel what you call a stock kernel? How do I know what support is in the kernel? I need ppp0 support.

---

### Post by lemurian on 2008-02-14
> **LonelyTraveler said:**
> Is this kernel what you call a stock kernel? How do I know what support is in the kernel? I need ppp0 support.
A "stock" kernel is the kernel which ships with a distribution.  If you upgrade your Gutsy installation to 2.6.24, you are not longer using a "stock" kernel because Gutsy does not ship with 2.6.24.  However, the kernel you get is a "stock" kernel in the sense that it is the kernel which ships with Hardy.

Welcome to the wonderful world of shades of grey where things are neither black nor white.

AFAIK, ppp support is included in all stock kernels shipped by major distributions but I have not used ppp in a while so I could be wrong.

Edit: I checked the config file for 2.6.24-7 and PPP is configured as a module, so yes it is there.

---

### Post by Hero of Time on 2008-02-14
> **lime4x4 said:**
> john@pammy-desktop:~$ locate hardy
/home/pammy/Desktop/hardy.py
/home/john/Desktop/hardy-desktop-i386.iso
/home/john/Desktop/hardy-alternate-i386.iso
/home/john/Desktop/hardy-alternate-i386.iso.part
/var/log/samba/log.john-hardy
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_Release
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg
john@pammy-desktop:~$

Did you do any of the options in the first post, like the gcc and udev update? If so, then remove those files you created. Also, did you run sudo apt-get update after you removed the repo or ran the script?

---

### Post by Milos_SD on 2008-02-14
I installed this and it is working.

Core2Duo E6550 2.33Ghz
2GB RAM
Gigabyte GA-P35-DS3L

But when I installed new udev, my scaner Canon ScanLide25 is not working, and I can not force Gutsy version of udev. :(
Here is the log:
```
Feb 14 23:28:07 c2d-desktop kernel: [  524.229191] ppdev0: registered pardevice
Feb 14 23:28:07 c2d-desktop kernel: [  524.229202] ppdev0: unregistered pardevice
Feb 14 23:28:07 c2d-desktop kernel: [  524.550493] ppdev0: registered pardevice
Feb 14 23:28:07 c2d-desktop xsane: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Feb 14 23:28:07 c2d-desktop kernel: [  524.598156] ppdev0: unregistered pardevice
```

And here is the lsusb:
```
Bus 001 Device 004: ID 04a9:2220 Canon, Inc. 
```

---

### Post by Hero of Time on 2008-02-15
If you can't force that version, then remove it, then install the Gutsy version and lock the version. You can also select older versions and lock that one. Just check the properties or something. I'm not in Linux atm, so I don't know where it is excactly, I only know that it's there somewhere.

---

### Post by lemurian on 2008-02-15
> **Milos_SD said:**
> I installed this and it is working.

Core2Duo E6550 2.33Ghz
2GB RAM
Gigabyte GA-P35-DS3L

But when I installed new udev, my scaner Canon ScanLide25 is not working, and I can not force Gutsy version of udev. :(
Here is the log:
```
Feb 14 23:28:07 c2d-desktop kernel: [  524.229191] ppdev0: registered pardevice
Feb 14 23:28:07 c2d-desktop kernel: [  524.229202] ppdev0: unregistered pardevice
Feb 14 23:28:07 c2d-desktop kernel: [  524.550493] ppdev0: registered pardevice
Feb 14 23:28:07 c2d-desktop xsane: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Feb 14 23:28:07 c2d-desktop kernel: [  524.598156] ppdev0: unregistered pardevice
```

And here is the lsusb:
```
Bus 001 Device 004: ID 04a9:2220 Canon, Inc. 
```

I've had a similar problem with my HP scanner.  The new version of udev has different specs to specify what to do with USB devices.  One thing you can try is see whether you can access your scanner when you run your software as root.  If you can, then the problem is just permissions.

Try adding the rules I'm attaching to this message to /etc/udev/rules.d/  (You must gunzip the file before installing it.)

I created this file by taking the old rules file bundled with libsane and modifying the syntax to the new specs.

Edit: BTW, ldd are my initials.  You can rename the file whichever way you want but you definitely should keep the "45-" at the beginning intact and the ".rules" at the end. I just like to put my initials on files I add to my system configuration or to parts of files I modify.  It's like a wild cat pissing on everything to mark its territory.

---

### Post by Milos_SD on 2008-02-15
Thanks lemurian. It is working now. I didn't had that file in /etc/udev/rules.d/
But, while I was reading this thread, I had that file there, and was thinking to edit it "usb_device" to "usb", but ones I made my mind, I could not find it there. :S

Thanks again lemurian, now it's all working like it should. :D

---

### Post by LonelyTraveler on 2008-02-15
Okay... Here's my predicament.

I'm trying to get my embedded 3G card running under Ubuntu. I was told that support for it came with kernel 2.6.23 and up. So I figured I'll install the latest one. 

How can I configure this kernel to make sure it has built in what it needs? Well... how can I configure it over all? I guess I need the source? Where can i find this?

---

### Post by Hero of Time on 2008-02-15
Did you install the linux-ubuntu-modules package and the restricted-modules package? Your driver might be in one of those packages. Install them and see if you can use it. I think it might be possible to see the device with an 'lshw -C network'.

---

### Post by LonelyTraveler on 2008-02-15
> **Hero of Time said:**
> Did you install the linux-ubuntu-modules package and the restricted-modules package? Your driver might be in one of those packages. Install them and see if you can use it. I think it might be possible to see the device with an 'lshw -C network'.

Nothing with lshw -C network, but I do see it with lsusb. Do I need to add the Hardy repository to install those packages?

---

### Post by Hero of Time on 2008-02-15
Of course, you installed the Hardy kernel, so you also need the Hardy kernel modules. If you installed Kernel 2.6.24-8, the restricted modules are the only one available atm but also very limited. You have to install 2.6.24-7 for all modules, or wait untill the modules are released. I wish they would update the kernel image along with the modules, not seperately like now.

---

### Post by LonelyTraveler on 2008-02-15
> **Hero of Time said:**
> Of course, you installed the Hardy kernel, so you also need the Hardy kernel modules. If you installed Kernel 2.6.24-8, the restricted modules are the only one available atm but also very limited. You have to install 2.6.24-7 for all modules, or wait untill the modules are released. I wish they would update the kernel image along with the modules, not seperately like now.

Is it called linux-ubuntu-modules-2.6.24-7-generic?

---

### Post by Hero of Time on 2008-02-15
If you installed the 2.6.24-7-generic kernel, yes, that is the module package you need.

---

### Post by LonelyTraveler on 2008-02-15
> **Hero of Time said:**
> If you installed the 2.6.24-7-generic kernel, yes, that is the module package you need.

Okay, both the packages you asked about was installed with the kernel I guess. Is there a way of configuring this kernel though? (For future reference)

Also, I can see my embedded 3G card. Do you know what to do next to get it working? I've temporarily been using a external USB 3G modem while I sort the embedded one out and have been using a Vodafone application, but now that I'm running the new kernel, the application doesn't want to open while the modem is plugged in. When its unplugged it starts up. Even tried to plug it in after starting the application, but that doesn't help either. When running the application in terminal, it just says "Failed to start application:" But nothing after the colons. So I'm facing two problems, here. Both related to 3G devices.

---

### Post by Hero of Time on 2008-02-15
I have no idea, as I don't have any 3G devices. Perhaps someone else knows how. I think it's best to open a new topic for this problem.

---

### Post by sdm_cacto on 2008-02-15
Im sorry if this was already posted, im having trouble configuring my wireless card , wich uses the  b43 driver, cause i cant get the firmware.

so i tried to setup ndiswrapper unsuccessfuly, can someone explain me how to do it??

i have a dell 1521 brand new but im tired of using windows vista.

thanks

---

### Post by wnelson on 2008-02-15
2.6.24-8-generic is out in the wild

Walt

---

### Post by Hero of Time on 2008-02-15
> **wnelson said:**
> 2.6.24-8-generic is out in the wild

Walt

It was released a few days ago. But the modules aren't compiled/released yet. So you can update to the new kernel version, but you will have only half the hardware running. No wireless, no video, nothing of the extra things (unless you install the propretary driver that isn't included in Ubuntu).

---

### Post by toasterboy1 on 2008-02-15
Compaq Persario v6133cl
nVidia GeForce GO 6150
AMD Turion 64 X2
Broadcom wireless
Kubuntu 7.10 Gutsy

Loading of kernel went well. Initially would not boot past splash. Tried once with envy option and once with nvidia option. No dice. Had to boot to recovery mode and run envy from command line. Finally booted to GUI.  Wireless did not work attempted fix in first post no luck. Tried ndiswrapper with no luck. Light stayed amber on front. Botted back to original kernel. Still no wireless. Did not even work in Windows so maybe a hardware failure. Went on. After a fresh install of Gutsy, because of issues with wireless tried again. No problems with kernel or booting. Applied gcc and udev fixes. Cannot install wine or envy related to lib6c. Going to resort back to Gutsy until Hardy is final.

---

### Post by sdm_cacto on 2008-02-15
> **[COLOR=DarkOrange]2.[/COLOR] WLAN Interface naming.** Fix *wlan0_rename, wmaster0_rename, etc...*
**> [COLOR=Green]I had to do this to get my wireless NIC to function correctly.[/COLOR]**[COLOR=Green] (*wlan0* doesn't work. It'll still end up *wlan0_rename*)[/COLOR]
>> Should be a temp fix as I'd assume the kernel devs will address this bug (already on launchpad)

Replace instances of **<driver>** with your wireless driver. (b43, iwl3945, madwifi, etc)

1. Alter the the NICs persistent interface name:
 	Code:
 	gksu gedit /etc/udev/rules.d/70-persistent-net.rules 
2. Now remove any interfaces already listed with your WLAN NIC's MAC address.

3. Add the following and then save and exit: (Replace **00:00:00:00:00:00** with your WLAN NIC's MAC address.)
 	Code:
 	# PCI device 0x14e4:0x4311 (**<driver>**)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:00:00:00:00", NAME="eth1" 
4. Now create an alias for eth1 and your driver, in my case b43: (b43, iwl3955, madwifi, etc...)
 	Code:
 	echo 'alias eth1 **<driver>'** | sudo tee /etc/modprobe.d/**<driver>** 
5. Reboot

If someone could explain this to me (in an easier way) it would be fantastic, i cant get b43 driver to work.

thanks

---

### Post by walkerk on 2008-02-16
> **sdm_cacto said:**
> If someone could explain this to me (in an easier way) it would be fantastic, i cant get b43 driver to work.

thanks

Did you install the b43 firmware? Please post the results of the following commands:
```
dmseg | grep b43
```
```
iwconfig
```

If you are trying to use ndiswrapper you will need to blacklist, ohci_hcd, ssb, and then re-mod ndiswrapper... If you have ndiswrapper installed along with bcmwl5.inf do this in the command line:
```

sudo modprobe -r ndiswrapper
sudo modprobe -r ohci_hcd
sudo modprobe -r ssb
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart

```

---

### Post by rupert on 2008-02-16
Hi

I am still having problems with the nvidia drvier (nv or nvidia). When I do a reboot X always starts in the low graphics mode and I have to reconfigure the whole X. in my xorg.conf there is nv as driver selected. 
Can someone maybe help me out?
I have an old Geforce3 Card.

thx

---

### Post by LonelyTraveler on 2008-02-16
This might be a stupid question seeing that this thread is on Ubuntu forums, but what is the latest kernel that is actually supported by Gutsy?

Will I have less problems with a older one?

---

### Post by Hero of Time on 2008-02-16
You can always check [http://packages.ubuntu.com/gutsy/base](http://packages.ubuntu.com/gutsy/base) to see what latest kernel is. Currently, it's stuck on 2.6.22-14.52.

As for less problems with an older one, that depends on what the new kernel will give for fixes or better drivers for your hardware.

---

### Post by LonelyTraveler on 2008-02-16
> **Hero of Time said:**
> You can always check [http://packages.ubuntu.com/gutsy/base](http://packages.ubuntu.com/gutsy/base) to see what latest kernel is. Currently, it's stuck on 2.6.22-14.52.

As for less problems with an older one, that depends on what the new kernel will give for fixes or better drivers for your hardware.

The latest stable kernel on kernel.org is 2.6.24.2. I'm gonna try to get that working again. Last time it didn't want to start up. Kept on getting a kernel panic.

---

### Post by Hero of Time on 2008-02-16
Remember that the Ubuntu crew has a different kernel for each version they release, with it's own patches and tweaks in it. So, the latest kernel you can get from the Gutsy repo is the one I mentioned. If you want to run a newer kernel, then follow the OP to get the latest Hardy kernel.

If you want to run the latest normal kernel, then you also need to compile it and make sure it supports your hardware. If you get a Kernel Panic, then there is something wrong with your kernel code for your hardware. I think you didn't have all the drivers needed for it.

---

### Post by LonelyTraveler on 2008-02-16
> **Hero of Time said:**
> Remember that the Ubuntu crew has a different kernel for each version they release, with it's own patches and tweaks in it. So, the latest kernel you can get from the Gutsy repo is the one I mentioned. If you want to run a newer kernel, then follow the OP to get the latest Hardy kernel.

If you want to run the latest normal kernel, then you also need to compile it and make sure it supports your hardware. If you get a Kernel Panic, then there is something wrong with your kernel code for your hardware. I think you didn't have all the drivers needed for it.

So I guess the best thing will be to use the Hardy kernel and just sort the things out? That way it will be fine by the time Hardy launches.

---

### Post by Hero of Time on 2008-02-16
Yes, you can do that if you want to run the latest kernel. Remember that the Hardy kernel is still under development, even though the 2.6.24 kernel is final. There is a possibility that some things don't work as you think they should.

The modules for the 2.6.24-8 kernel are also available now, so updating to that kernel is now possible for full hardware support (for as far as they have build modules for the hardware ;)).

---

### Post by LonelyTraveler on 2008-02-16
Okay. I know I'm asking a lot of questions here, but I'm so tired of trying to sort this 3G thing out. What is the latest stable release? The 2.6.24.2 one right? I guess I'm gonna have to go back to the kernel panic one then and sort that out.

---

### Post by Hero of Time on 2008-02-16
Why are you still looking for a kernel, when the best option is to look for a driver? It's the same with Windows, it doesn't matter if you install the latest version or not, if it doesn't have the driver for it, the device won't work. Simple as that. Look for the driver, install it and it should work. Do an lspci, google for the 3G result and you probably will get a driver for Linux.

---

### Post by LonelyTraveler on 2008-02-16
I've Googled endlessly for 3G help, but nothing. I was told that kernels 2.6.23 and up has support for the embedded 3G card. Thats whey I need a newer kernel. But I also don't really want to be using a developing kernel.

---

### Post by Hero of Time on 2008-02-16
I think you have no choice. The kernel you compiled keeps returning kernel panic, so you have to run the Hardy development kernel. And as you can read in this topic, there are no serious problems. Some wireless don't work as they should, but it's always better then a kernel panic.

---

### Post by LonelyTraveler on 2008-02-16
> **Hero of Time said:**
> I think you have no choice. The kernel you compiled keeps returning kernel panic, so you have to run the Hardy development kernel. And as you can read in this topic, there are no serious problems. Some wireless don't work as they should, but it's always better then a kernel panic.

Okay, cool. Thanks for the help. I'm running 2.6.24-7 now, but I'm playing around with 2.6.24.2 at the moment. Maybe I can figure something out. I'm just hoping to have this 3G thing sorted out soon and that my system will be the way I want it to be. :)

Have a great weekend.

---

### Post by mavila on 2008-02-16
First off - thanks to WALKERK for the original how-to on this upgrade... very helpful. Also thanks for all the contributions everyone else has made... again these have been extremely helpful.

After sloggin through these I have two minor annoyances (okay, well issues). The first is the inability to "easily" get my USB scanner working. Looks like I have to mount the usb system now, and doing that messes up file permissions so I can only run SANE or gscan2pdf as root now (following some of the thread instructions). Can anyone point me to the documentation or explain how to setup the libusb permission? 

when I initially (before sudo mount -t usbfs procbususb /proc/bus/usb/; echo $? command) issue "cat /proc/bus/usb/devices" Im seeing nothing, but once the usbfs is mounted in the 2.6.24-7 kernel I can see the scanner. Its showing;


T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=04 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0638 ProdID=0a25 Rev= 0.01
S:  Manufacturer=AVISION!)
S:  Product=AV210
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=125us
E:  Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms

... so I know its there. at this point "sane-find-scanner" will actually return something positive (it finds the scanner!);

found USB scanner (vendor=0x0638, product=0x0a25) at libusb:002:008

So launching SANE or gscan2pdf as a user (not root) doesn't find the scanner. I launch either application as root and all works - so I know its permissions. Looking into /proc/bus/usb/002 I can see that the scanner has permissions of;

-rw-r--r-- 1 root root  57 2008-02-15 15:18 008

and changing them to either 664 or 777 seems to have no effect.... so I again know Im doing something wrong. Can someone offer a bit of guidance on this?

Second  issue is gcc (I need to re-compile VMWare modules) but I think Ive got that figured out (someone else posted it somewhere in the thread if memory serves me....)

Thanks again!

---

### Post by LonelyTraveler on 2008-02-16
As there's a lot of "kernel guys" here, i figured this will be the best place to ask this question.

Lets say I install kernel 2.6.24.2 and afterward want to configure it; do I have to uninstall it completely, or can I just go make menuconfig and install from there?

Thanks.

---

### Post by lemurian on 2008-02-16
> **mavila said:**
> After sloggin through these I have two minor annoyances (okay, well issues). The first is the inability to "easily" get my USB scanner working. Looks like I have to mount the usb system now, and doing that messes up file permissions so I can only run SANE or gscan2pdf as root now (following some of the thread instructions). Can anyone point me to the documentation or explain how to setup the libusb permission? 


<...snip...>

Hmm... I think your problem has already been answered in this thread.

1) From Hardy onwards /proc/bus/usb is obsolete. Install the latest udev package from Hardy and you will find your usb devices in /dev/bus/usb.  The usb tools are already able to look there when they don't find /proc/bus/usb.

2) The udev for Hardy has different specs for its rules.  Look back to a previous post of mine in this thread to which I have attached a .rules file.  Follow the instructions in that post.

To find all previous posts on usb that have anything to do with upgrading to a Hardy kernel you can use the search capabilities of this forum to search for "usb" **in this thread only**.

---

### Post by lemurian on 2008-02-16
If you install 2.6.24.2 from kernel.org, you're basically on your own to make sure you don't mess up anything.  That's not something I would recommend unless it is a do or die situation.  This is coming from someone who used to compile kernels on a regular basis.  I have not done that in a while because I see more problems than benefits to compiling my own kernels.

Here's what I would expect: If you install a precompiled kernel and then you decide to customize the sources **for that kernel** and reinstall, you will just overwrite the  kernel you've just installed.  So no, you don't need to uninstall it first.

---

### Post by snakeeyes on 2008-02-16
has anyone got rid of that bug with emerald and new drivers for nvidia for example if u go to openoffice writer and go on to the close minimize button, then they start flickering.

---

### Post by snakeeyes on 2008-02-16
Hi, ok here is the fix to this problem. What happens is when some people use this driver with emerald whenever they go to the close, maximize, minimize buttons in firefox or openoffice then whole titlebar becomes translucent or transparent and starts flickering.

Here is the fix:

1. start emerald theme manager
2. click on the emerald settings tab
3. un check use button fade and use button fade pulse

This will take care of the problem.

Whoever has this problem, tell me how it goes.

---

### Post by EtniesBMX on 2008-02-16
to the OP and anyone who cares:
upgrading this kernel fixed the problem of
 > No volume control GStreamer plugins and/or devices found.
since my motherboard (MSI P6NGM) was so new, the gutsy kernel did not support sound, but the new hardy one works great! thank you!

---

### Post by Hero of Time on 2008-02-17
The driver module in kernel 2.6.24-8 for iwlwifi iwl3945 is not changed compared to 2.6.24-7, so the driver is still broken and not working for me. I will stick to 2.6.24-5 until that is fixed. So for now, all who have the Intel Pro Wireless 3945 should stay at 2.6.24-5, unless they use another driver (either compiled the ipw again, or use ndiswrapper).

---

### Post by BC7333 on 2008-02-17
> **Hero of Time said:**
> The driver module in kernel 2.6.24-8 for iwlwifi iwl3945 is not changed compared to 2.6.24-7, so the driver is still broken and not working for me. I will stick to 2.6.24-5 until that is fixed. So for now, all who have the Intel Pro Wireless 3945 should stay at 2.6.24-5, unless they use another driver (either compiled the ipw again, or use ndiswrapper).

I did not try 24.7, but just now upgraded to 24.8.

3945 seems to be working fine here, except that the wifi indicator led does not do anything.

---

### Post by mavila on 2008-02-17
thanks lemurian... appreciated. What wasn't clear was adding Hardy's udev package. Once I did that all is well. I had the older libsane.rules from the Gutsy install - but went ahead and used yours (thanks again) as I see where its pointing as opposed the old file.

Still plugging away at getting VMWare modules built however.... thats  burning some brain cells! Has anyone figured this one out yet? Ive upgraded cgg and Im still getting;



RegardsConfiguring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Workstation 5.5.2 or 5.5.3.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config0/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-7-generic'
[COLOR="Magenta"]make: *** [vmmon.ko] Error 2[/COLOR]
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by Hero of Time on 2008-02-17
> **BC7333 said:**
> I did not try 24.7, but just now upgraded to 24.8.

3945 seems to be working fine here, except that the wifi indicator led does not do anything.
My wifi led is on when I have the switch on, but it just won't associate correctly. I do get a 'signal' but when I iwconfig my wlan, it just stays at link speed: 0. Also, ping to the router does nothing and my WaveLan panel doesn't say anything about association (no signal).

---

### Post by Hero of Time on 2008-02-18
Now I'm at school and wifi works. The AP I'm connected to is using WEP instead of WPA which I use at home. It is still going though wpa_supplicant, so somehow WPA is not possible, even though wpa_supplicant is used.

---

### Post by Gigamo on 2008-02-18
24-8 safe to upgrade then?

---

### Post by Hero of Time on 2008-02-18
Well, I guess I was wrong about 24-7 too. However, if you use WPA encryption, you might run in some problems not getting a signal or link. I didn't get anything when trying to connect to a WPA connection.

---

### Post by Nunslaughter on 2008-02-18
I have a problem with my Nvidia driver after an update from 2.6.24-5 to 2.6.24-8. The installation went ok I guess, then after a reboot my desktop effects were off. Also the temp of my card doesn't show up anymore in gkrellm. So I went to the restricted driver thing (don't know what's it called in English), and according to that, the Nvidia driver is in use. Also in my xorg.conf the driver is set to "nvidia".

---

### Post by ST.x on 2008-02-18
> **Nunslaughter said:**
> I have a problem with my Nvidia driver after an update from 2.6.24-5 to 2.6.24-8. The installation went ok I guess, then after a reboot my desktop effects were off. Also the temp of my card doesn't show up anymore in gkrellm. So I went to the restricted driver thing (don't know what's it called in English), and according to that, the Nvidia driver is in use. Also in my xorg.conf the driver is set to "nvidia".
you probably need to reinstall the nvidia driver, check the first post.

---

### Post by tekknokrat on 2008-02-18
I had also to update my libc6 incl. -dev headers.

Now i have buil-dep problems when trying to build some packages from source.

Is there some way to upgrade kernel without libc upgrade?

---

### Post by lemurian on 2008-02-18
> **tekknokrat said:**
> I had also to update my libc6 incl. -dev headers.

Now i have buil-dep problems when trying to build some packages from source.

Is there some way to upgrade kernel without libc upgrade?
Probably not.  I'm inferring this from the fact that walkerk's script does not explicitly ask for an upgrade to libc6 and yet it is upgraded.  There's a chain of dependencies that require it.  I can't be 100% sure that there is no way to avoid it but attaining 100% certainty requires too much work to track down what depends on what.  This is the best answer I can give.

---

### Post by perfectska04@hotmail.com on 2008-02-18
There is a problem with the latest restricted modules and NVIDIA in the repos, if glx won't load, go to launchpad and download the .deb files for linux-restricted-modules, linux-restricted-modules-common, and nvidia-glx-new version 2.6.24.9-8.25

The nvidia-settings tool is no longer included with the drivers either, so you have to install the package from the hardy repos as well... I hope this can be of some help.

---

### Post by RDV on 2008-02-18
Works first time using the hardy.py script.

Hardware info:
ASUS mainboard
P5AD2-E Premium P4 3.6GHz
Maxvell 88E8053 PCI Express Onboard Network Card
C-Media CMI9880 7.1 Onboard Sound Card
Nvidia GeForce 8600GTS Graphics Card
(2) Western Digital 111Gb ATA HDs
(3) Westaen Digital 300Gb SATA HDs
Plextor PX-708A CDRW/DVDRW
2 GB DDR RAM
Monitor is a HDTV running at 1920x1080i

Thanks, it was really easy with the hardy.py script. The script even preserved my Nvidia component out settings for the HDTV.
I had hoped that the kernel upgrade would allow me to use my line-in from the onboard sound card. A quick try was unfortunately no-joy. Everything else is working well.

EDIT: This probably does not matter to many, but with this kernel I finally was able to install MS-Reader under WINE. It just would not work with the generic Gutsy kernel.

---

### Post by beharsen on 2008-02-18
It works like a charm (did it the manual way) and now my keyboard is working again... :)

Hardware info:

Compaq Evo D510 SFF
Intel(R) Pentium(R) 4 CPU 2.40GHz
Integrated Intel Extreme graphics
Integrated Intel PRO/100 NIC
Integrated Intel Audio
512 DDR RAM
Samsung SyncMaster 225BW running at 1680x1050 via VGA
Microsoft Natural 4000 (all keys work out of the box!)

Thank you so much!

---

### Post by BC7333 on 2008-02-18
One pleasant surprise is that I have not noted any unexpected shutdowns or blackouts with the 24.8 kernel.

Thanks Walkerk!

---

### Post by ghindo on 2008-02-18
Upgrade worked fine on my Dell Inspiron 1420n, but the sound doesn't work.  I think I'm just going to check back with the kernel when Hardy is release.  Thanks for the tutorial, anyway - it was super-easy to follow and helpful. :)

---

### Post by oeperez on 2008-02-18
Worked the first time on a new 7.10 installation on a Dell PowerEdge 1600SC using SATA PMP (Port Multiplier).

Thank you so much for this awesome script!

---

### Post by Nunslaughter on 2008-02-19
> **perfectska04@hotmail.com said:**
> There is a problem with the latest restricted modules and NVIDIA in the repos, if glx won't load, go to launchpad and download the .deb files for linux-restricted-modules, linux-restricted-modules-common, and nvidia-glx-new version 2.6.24.9-8.25

The nvidia-settings tool is no longer included with the drivers either, so you have to install the package from the hardy repos as well... I hope this can be of some help.

Ok, maybe pretty stupid, but where can I find these packages on Launchpad?

---

### Post by ST.x on 2008-02-19
> **perfectska04@hotmail.com said:**
> There is a problem with the latest restricted modules and NVIDIA in the repos, if glx won't load, go to launchpad and download the .deb files for linux-restricted-modules, linux-restricted-modules-common, and nvidia-glx-new version 2.6.24.9-8.25

The nvidia-settings tool is no longer included with the drivers either, so you have to install the package from the hardy repos as well... I hope this can be of some help.
Why not just reinstall the drivers with envy after the update to 2.6.24.9-8.25 ?

---

### Post by cRoW2k on 2008-02-19
Just compiled new -8 kernel, all works great, but i've a new device (wmaster0  no wireless extensions.) and a dmesg full of: 
[ 6790.439299] wmaster0: CCMP decrypt failed for RX frame from

Internet e wlan0 goes well. What can i do?

---

### Post by Hero of Time on 2008-02-19
wmaster0 is an additional interface that is the result of the wireless driver. Nothing to do about it. I have it too. Just a dummy interface that links to your wifi interface. Check lshw -C network and you will see wmaster0 as logical name for your wifi.

---

### Post by cRoW2k on 2008-02-19
ok, i've seen that it's the same interface. But for the dmesg ? It continuosly get out my upside messagge.

---

### Post by HDave on 2008-02-19
> **mavila said:**
> Still plugging away at getting VMWare modules built however.... thats  burning some brain cells! Has anyone figured this one out yet?

+1 for solving this....

EDIT: Apparently there is some magic any-any patch that allows any version of vmware to compile on any version of the linux kernel.

I found this link that looked hopeful, but the link to the vmware any-any patch was broken:

[http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel]("http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel")

---

### Post by snakeeyes on 2008-02-19
anyone knows when the Linux kernel will support udf 2.50 by default?

---

### Post by mavila on 2008-02-19
I tried the 115 patch and thats not working... cant get to the 116 patch (the group appears down)... and I dont see that anywhere else. You did the gcc upgrade as well?

---

### Post by HDave on 2008-02-19
I upgraded gcc right away as the compile wouldn't even commence without the same version of gcc that was used to compile the kernel.

The Ubuntu VMWare wiki page:

[https://help.ubuntu.com/community/VMware/Workstation]("https://help.ubuntu.com/community/VMware/Workstation")

indicated that the patch could be located here:

[http://knihovny.cvut.cz/ftp/pub/vmware/]("http://knihovny.cvut.cz/ftp/pub/vmware/")

But it is version 115 of the patch.  I tried this patch and is does NOT work. 

Then I found version 116 of the patch here:

[http://www.paldo.org/index-section-packages-page-main-releaseid-101381.html]("http://www.paldo.org/index-section-packages-page-main-releaseid-101381.html")

and it didn't work either complaining:

> make[1]: Entering directory `/usr/src/linux-headers-2.6.24-7-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

I am now out of ideas.

---

### Post by Hero of Time on 2008-02-19
I have an idea. Switch to VirtualBox. It is free, fast and works great on Linux (and can also use VMWare images. Some setup might be a tad different and may take some time, but I have no problems whatsoever. When you upgrade your kernel, all you have to do is 'sudo /etc/init.d/vboxdrv setup' and you're all done with new VBox kernel modules.

This isn't a solution but a workaround, but one that will keep working after a kernel upgrade.

---

### Post by HDave on 2008-02-19
OK -- Apparently the 116 any-any patch DOES work.  My compilation problem was related to the fact that I needed to upgrade the g++ package in addition to gcc++.

I am running the new kernel on Gutsy and the how-to at the beginning of this post say only to upgrade gcc++.  It needs to be updated to reflect that g++ must be obtained too.

Once I got Hardy's g++, the compile went fine with the 116 patch and I am back up and running.

---

### Post by MiataMuc on 2008-02-19
Hi! Thanks, runs perfectly on a Thinkpad R61 (8918-DEG), and helped me enabling the important ones of the FN-key combinations plus - what I really appreciate - made X recognise my alps - touchpad as an touchpad..I can scroll now :)

Thanks a lot,

Flo

---

### Post by mavila on 2008-02-19
HDave - thanks for the tip... I can now build the modules, but something new has crept up... and I still cant launch VMWare. I havent yet looked a the VMWare forums, but will in a few minutes. Im getting the following;

desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
desktop:~$

Any ideas on that issue?

---

### Post by HDave on 2008-02-19
Mavila -- Off hand, I am not sure of the source of this error.  I would check:

a) that I am using the latest gcc ("gcc --version" = 4.2.3) -- that it installed without error
b) that the vmware compile had no errors
c) that I started with a clean install of the latest version of vmware (build 59824)

---

### Post by walkerk on 2008-02-20
> **HDave said:**
> OK -- Apparently the 116 any-any patch DOES work.  My compilation problem was related to the fact that I needed to upgrade the g++ package in addition to gcc++.

I am running the new kernel on Gutsy and the how-to at the beginning of this post say only to upgrade gcc++.  It needs to be updated to reflect that g++ must be obtained too.

Once I got Hardy's g++, the compile went fine with the 116 patch and I am back up and running.

Thanks. I'll update the OP. :)

---

### Post by fooman on 2008-02-21
tried both methods (script and manual) and when i try to boot into the new kernel,  i get an error message that my /home directory cannot be found?  the boot goes fine until i get to the log in screen.  i then type in my user name and password,  and up pops the error message.  it asks if i want to use the root directory as /home.  doesn't matter if i answer yes or no,  it of course will not boot.  i have to reboot to the old kernel again to be able to log in.  everything works fine in the old kernel, and i can remove the new one without a problem...  just would like to be able to boot to the new one.

any suggestions on how to fix?  ...thanks.

---

### Post by czikus on 2008-02-21
Just upgraded to the new kernel, udev, gcc etc. Everything works great (finally my ext3 on truecrypt volume problem is solved)! There is only one small issue. My dmesg is flooded with the following messages:
wmaster0: RX WEP frame with unknown keyidx 0 
About 15 per second! I'm using the iwl3945 driver. Anyone else have seen such problem?

---

### Post by Hero of Time on 2008-02-21
> **czikus said:**
> Just upgraded to the new kernel, udev, gcc etc. Everything works great (finally my ext3 on truecrypt volume problem is solved)! There is only one small issue. My dmesg is flooded with the following messages:
wmaster0: RX WEP frame with unknown keyidx 0 
About 15 per second! I'm using the iwl3945 driver. Anyone else have seen such problem?
I don't have that message in dmesg. I do know that the latest kernel, 2.6.24-7 and -8 use the 1.2.0 driver, which only works with WEP. You could try to install 2.6.24-5 and see if you still have that error. I don't know if that version is still in the repo, but you could try a hold version in synaptic or enter the full name of the package when updating from CLI.

---

### Post by walkerk on 2008-02-21
> **czikus said:**
> Just upgraded to the new kernel, udev, gcc etc. Everything works great (finally my ext3 on truecrypt volume problem is solved)! There is only one small issue. My dmesg is flooded with the following messages:
wmaster0: RX WEP frame with unknown keyidx 0 
About 15 per second! I'm using the iwl3945 driver. Anyone else have seen such problem?

thats strange... is your wireless interface being named wmaster0? are you using WEP?

try what **hero of time** suggests...

```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy main restricted' | sudo tee /etc/apt/sources.list.d/hardy.list
```
```
sudo apt-get update
```

Now use Synaptic to install 2.6.24-5 (search for it)
```
gksu synaptic
```

After installing it make sure to remove the Hardy repository...
```
sudo rm /etc/apt/sources.list.d/hardy.list
```
```
sudo apt-get update
```

Now you can reboot into the kernel... You'll need to press Esc at grub to select the kernel as 2.6.24-8 will be primary...

---

### Post by Hero of Time on 2008-02-21
Walkerk, when you have the IPW3945, the iwlwifi driver will bind the wifi to wmaster0 as logical name, and use wlan0 as wifi name. Something like a symlink (or alias) for the nic. Wmaster0 will have no support for wireless extensions and in the rules file, wlan0 is listed as the interface.

[SIZE="1"]Just some info in case you don't have the ipw3945 (which I think you don't have).[/SIZE]

---

### Post by NEUR0M4NCER on 2008-02-21
Thanks to the OP for this, but there was just too much 'under-the-hood' tinkering needed to get wireless & nvidia working (guess I don't know as much as I thought I did ;)). I'll wait for the release.

Easily removed new kernel etc, back to Gutsy no problems, so thanks again for thinking through your howto.

Regards

---

### Post by clickwir on 2008-02-21
This is a nice idea and great for some people. I must have something else going on with my system as I cannot get the nvidia driver to work.

The closest I've gotten is to using the nvidia installer from nvidia's website, not rebooting after install and trying just a startx. That flashes up the NVIDIA logo, shows the X cursor and then dumps back to a command prompt with some bogus message about font's set to 2 needs to be 1, fixing. No errors about why it wouldn't start though.

I've tried the gutsy nvidia-glx-new and the hardy. I've tried the ENVY script 0.9.10, I don't know how many times. With and without reboots. I'm running the hardy kernel right now, but only using VESA driver.

If I use the nvidia installer, and reboot it doesn't work. Gives me an error about a version mismatch. But if I run the installer again right then, and try startx I get the NVIDIA logo and X cursor. But if I just reboot without doing anything else, I get the version mismatch error. Something is changing something on reboot to be wrong. I can boot with VESA, but that's all. So it's almost there. I don't know. I'm giving up and I'm not reading through 40+ pages (already did 20) of unrelated posts to maybe find something. I'm going to reinstall with Kubuntu Gutsy 64 bit and wait for Hardy beta.

---

### Post by czikus on 2008-02-22
> **Hero of Time said:**
> I don't have that message in dmesg. I do know that the latest kernel, 2.6.24-7 and -8 use the 1.2.0 driver, which only works with WEP. You could try to install 2.6.24-5 and see if you still have that error. I don't know if that version is still in the repo, but you could try a hold version in synaptic or enter the full name of the package when updating from CLI.

Unfortunately can't find the -5 kernel anymore. But, I found a very related bug report [http://bughost.org/bugzilla/show_bug.cgi?id=1566](http://bughost.org/bugzilla/show_bug.cgi?id=1566).
Are you using the -8 kernel and iwl3945? Do you know which version of iwlwifi is used in 2.6.24-8? Any other hints? 

Thanks a lot!

---

### Post by Hero of Time on 2008-02-22
> **czikus said:**
> Unfortunately can't find the -5 kernel anymore. But, I found a very related bug report [http://bughost.org/bugzilla/show_bug.cgi?id=1566](http://bughost.org/bugzilla/show_bug.cgi?id=1566).
Are you using the -8 kernel and iwl3945? Do you know which version of iwlwifi is used in 2.6.24-8? Any other hints? 

Thanks a lot!

I already mentioned the version that is in use in both the -5, -7 and -8 kernel modules. In -5, its 1.1.17, newer modules use 1.2.0. I don't use that version, as only WEP works, and obviously flawed too. You have to wait for a new kernel module that doesn't use 1.2.0. Perhaps you can return to the ipw3945 driver by compiling it. I haven't tried that, as my driver works fine and I can hibernate.

---

### Post by Nunslaughter on 2008-02-22
> **clickwir said:**
> This is a nice idea and great for some people. I must have something else going on with my system as I cannot get the nvidia driver to work.

The closest I've gotten is to using the nvidia installer from nvidia's website, not rebooting after install and trying just a startx. That flashes up the NVIDIA logo, shows the X cursor and then dumps back to a command prompt with some bogus message about font's set to 2 needs to be 1, fixing. No errors about why it wouldn't start though.

I've tried the gutsy nvidia-glx-new and the hardy. I've tried the ENVY script 0.9.10, I don't know how many times. With and without reboots. I'm running the hardy kernel right now, but only using VESA driver.

If I use the nvidia installer, and reboot it doesn't work. Gives me an error about a version mismatch. But if I run the installer again right then, and try startx I get the NVIDIA logo and X cursor. But if I just reboot without doing anything else, I get the version mismatch error. Something is changing something on reboot to be wrong. I can boot with VESA, but that's all. So it's almost there. I don't know. I'm giving up and I'm not reading through 40+ pages (already did 20) of unrelated posts to maybe find something. I'm going to reinstall with Kubuntu Gutsy 64 bit and wait for Hardy beta.

Yeah, correct. I first upgraded to 2.6.24-5 and everything worked fine. Then updated to the -8 and also can't get the Nvidia drivers to work.

---

### Post by lemurian on 2008-02-22
> **clickwir said:**
>  I'm giving up and I'm not reading through 40+ pages (already did 20) of unrelated posts to maybe find something.

Two observations:

1. The number of posts per page is configurable.  The thread is 11 pages long for me.  That does not cut down the number of posts to look at but it does cut down the time spent reading a thread from the start because you don't have to change page so often.

2. This is more important than 1.  You can search **within** a thread for posts that contain a specific keyword.  So you don't have to read all the other stuff.

---

### Post by mavila on 2008-02-22
Clickwir - I had similar issues fooling around between the 2.6.24.and 2.6.22 kernels and the NVIDIA drivers. I tried ENVY and it really hosed things up, so I would suggest to dump it completely.  I ended up following the following to get the Hardy NVIDIA packages installed and working

Once you get into a terminal remove ALL your existing NVIDIA stuff with apt-get remove, then enable the Hardy repository, apt-get install the nvidia-glx-new, remove the hardy repository, (I rebooted here) and then it all came to life. << not sure here, but you may have to go into system/preferences/restricted-drivers and enable the NVIDIA drivers and reboot>> 

I had to reset the screen resolution for the monitors though - only my primary was enabled - but the driver was working and all went well.

At any rate - it sounds like youve got either too many NVIDIA packages and conflicting modules... clean them all out with apt-get remove and start fresh with the HARDY repo open and it should spring to life for you.

---

### Post by Hero of Time on 2008-02-22
Does anyone know how to disable that annoying beep when you can login, run to the beginning/end of a file, and what not? This wasn't in the old kernel. I really hate it, as it was also annoying in Windows to hear a beep when you want to check to see if you can move one more character in any editor. I don't mind it if it sounds when my battery is low, but other than that, I hate it.

Nevermind, found it:
[quote="Yfrwlf"]I thought you just went to Sys > Prefs > Sound > Sys Beep > Enable/Disable Sys Beep. Worked for me.[/quote]
That made me think about volume. Muted my pc speaker and done. As I'm using Xfce, the above mentioned option isn't available for me, only on Gnome (and perhaps also KDE).

---

### Post by tommohawk on 2008-02-23
Just used the guide to upgrade to the Hardy kernel and it worked perfectly.   Went the whole way and updated everything and now my laptop (HP DV8000 series) works like never before.  Even suspend works - that is a first in Linux for me.

---

### Post by Milos_SD on 2008-02-23
Here is how I installed nvidia drivers:

First I did this upgrade to Hardy kernel, then before rebooting changed Driver "nvidia" to Driver "nv" in xorg.conf, then I rebooted in the new kernel.
Then I started envy script and selected Install NVIDIA driver, rebooted and I had nvidia drivers working.

BUT, I still have that bug with dual core CPU and Nvidia driver. :( I was hoping that installing new kernel and restricted modules will help with that bug, but no luck. :(

---

### Post by mavila on 2008-02-23
Not sure about the dual core bug.... Im running a dual core Intel box with 4GB ram (32 bit kernel) and its working fine. Im using Compiz as well  on a dual head system- and it actually seems to respond better than the 7.10 and 7.04 I was running previously. I did not use envy however - while it was pretty good in the 7.10 for getting various NVIDIA drivers installed, Ive taken the manual path... A bit more configuration work, but it does work.

---

### Post by vinpous on 2008-02-23
Upgraded to the kernel as per instructions, everything asides wireless seems to work fine.

Specs(ish)

Asus laptop
Intel Proset 3945ABG
Realtek HDA
Realtek NIC
nVidia GO 7300 (512mb) GFX
1.5gb DDR2
etc etc.

After following the steps to rectify wlan0 problems (and before), network manager sees the network and attempts to connect, sometimes telling me it's succeeded, however, I can't ping the router at all and rather rapidly it drops the connection. Connection Info tells me there's no IP address associated, etc.

ifconfig tells me there's no eth1.

iwconfig tells me there IS an eth1 and it's associated with the ESSID: "omgbbq" (which is correct" and the correct router MAC address.

--

Using manual configuration offers the same results with less pretty graphics telling me I'm connected when I'm not.

-- I also don't have LED activation - no biggie though.

--

The reason I wanted to upgrade is because the wifi connection drops, randomly, under the default 7.10 install and did the same when I was running PCLinuxOS2007. The reason for the change was really just for something different and hopefully working wifi. I'm beginning to think I should just give up on wifi and Linux OR that there's something medically (hyuk) wrong with my wifi card.

Any suggestions?

I can't really run ethernet out to my studio where I use the laptop, so I'm on my desktop inside, using Windows and listening to Cowboy Bebop soundtrack... :)

EDIT: I've also combed this thread looking for ideas, tried deleting the 70-persisten-thingy file (after backing up, of course), so that a new one would be generated. Didn't make a difference...

---

### Post by vinpous on 2008-02-24
Interesting...

My router tells me that the laptop is (at least partially) connected...

MAC 	Signal 	Noise 	SNR
00:18:DE:04:84:2D	-59	-100	41
00:11:50:0D:3B:43	-65	-100	35

The top MAC is the laptop...

Most interesting.

---

### Post by vinpous on 2008-02-24
Final update:

Switched to WPA2 on the router and that worked, but it dropped out and won't reconnect at all. 

Very frustrating.

(On the positive... World of Warcraft gained 20fps from the change in Kernel...)

I think I might have to bite the proverbial bullet and return to Windows on my laptop... I mean, the recording software I prefer is only available on Windows, not to mention Sibelius and the like.

Sigh... if I do that, Ubuntu (and Linux) will be left in the backburner for a long while... again.

---

### Post by prudent14 on 2008-02-24
Hi to all... this is my first post in Ubuntu forum...

I love this stuff

successfully update the kernel

> kushal@kushal-desktop:~$ cat /proc/version
Linux version 2.6.24-8-generic (buildd@rothera) (gcc version 4.2.3 (Ubuntu 4.2.3-1ubuntu2)) #1 SMP Thu Feb 14 20:40:45 UTC 2008

as a noob i just do the following to get nvidia drivers to get work

1. Install hardy.py script as described in first page
2. Restart and Uninstall nvidia driver from Envy
3. Uninstall Envy from Synaptic and restart
4. Install Envy from Synaptic
5. Install nvidia driver and restart

all coming back to the same as before .. thx a lots

everything seems to be run fine on desktop environment but whenever i press CTRL+ALT+F1 to get the command line it just give me a black screen with a blinking cursor... no command accepted except only CTRL+ALT+F7 to get back to desktop GUI... though its not a huge problem for me but i just wonder what happend to the system which destroy my command line.


i can provide any further information if required

by the way i successfully run AWN, Compiz Fusion, Xwinwrap, Envy, Emerald Theme Manager, Screenlets, Kiba-Dock and lots of customization without any problem....

My System:
Q6600 SLACR G0 @ 2.40GHz
MSI 8800GTS 512 OC stock
Intel DG33BU
2GB DDR2 667MHz
250GB Seagate SATA
Tagan TG600-U33 600W PSU
IBM P76 17"

---

### Post by Hero of Time on 2008-02-24
> **vinpous said:**
> Final update:

Switched to WPA2 on the router and that worked, but it dropped out and won't reconnect at all. 

Very frustrating.

(On the positive... World of Warcraft gained 20fps from the change in Kernel...)

I think I might have to bite the proverbial bullet and return to Windows on my laptop... I mean, the recording software I prefer is only available on Windows, not to mention Sibelius and the like.

Sigh... if I do that, Ubuntu (and Linux) will be left in the backburner for a long while... again.
Switch to WEP encryption and it should work a lot better. As you could have read from my posts, since the kernel modules newer then 2.6.24-5, the iwlwifi driver doesn't work as it should. No WPA(2), no IEEE802.1x, nothing except for WEP. Although I have my doubts about that too, as I have all three wifi encryptions on locations I go to (WPA at home, other 2 at school) and WEP stopped after some time. Could also have been a drop in connection, reset from AP, etc. So unless you can compile iwlwifi version 1.1.17, you are better off with Windows. I didn't have any problems with the ipw3945 driver though.

---

### Post by lemurian on 2008-02-24
> **Hero of Time said:**
> Switch to WEP encryption and it should work a lot better. As you could have read from my posts, since the kernel modules newer then 2.6.24-5, the iwlwifi driver doesn't work as it should. No WPA(2), no IEEE802.1x, nothing except for WEP. Although I have my doubts about that too, as I have all three wifi encryptions on locations I go to (WPA at home, other 2 at school) and WEP stopped after some time. Could also have been a drop in connection, reset from AP, etc. So unless you can compile iwlwifi version 1.1.17, you are better off with Windows. I didn't have any problems with the ipw3945 driver though.
I think the comments above about iwlwifi being unstable concern **only** the iwl3945.  

The iwl4965 is also part of the iwlwifi driver and has been working perfectly for me ever since Gutsy Gibbon was released.  It has continued working perfectly with all the Hardy kernels.  I did not have the wireless device renaming problem that people have been discussing.  I use WPA for encryption.

---

### Post by Gigamo on 2008-02-24
I am using iwl3945 with 2.6.24-8 (and Ive been using it since 2.6.24-2 actually), with WPA2 encryption, and I have had no problems at all except for 1Mbit bug.

---

### Post by s0ullight on 2008-02-24
hello i upgraded my kernel with ur script (worked great)
then i followed that guide for the interface renaming thing
didn't help :(
but i extracted the firmware etc. manually so i can connect 
to wireless networks with my wlan0_rename interface
the weird thing is that i still have my old interface name (eth1)
and iwconfig says not a wireless extension
can you help me ? plz 
tnx in advance ;]
i got stuck a long time with the bcm43xx driver so it's a great leap

---

### Post by Hero of Time on 2008-02-24
> **Gigamo said:**
> I am using iwl3945 with 2.6.24-8 (and Ive been using it since 2.6.24-2 actually), with WPA2 encryption, and I have had no problems at all except for 1Mbit bug.
Could you tell me the result of 'modinfo iwl3945'? Does it say 1.2.0 or a different version? 1.2.0 does not work for me.

s0ullight:
Did you remove your eth1 connection from the 70-persistent-net.rules file found in the /etc/udev/rules.d folder? Do a 'sudo mv 70-persistent-net.rules 70-persistent-net.rules.bak' and reboot. Check if the name is wlan0 now. You can also see the logical name of the nic by typing 'lshw -C network'.

---

### Post by Tonohono on 2008-02-24
**Edit:** Installing cryptsetup and dmsetup from the Hardy repo has solved this issue!

Howdy folks,

Today I followed the instructions in this thread to install the Hardy kernel, nvidia drivers, udev, and gcc. The installations went without incident, however I'm running into an issue when I attempt to boot to the Hardy kernel.
First, boot hangs for several seconds at:
```
Uniform CD-ROM driver Revision: 3.20
```

After which the following message and error is displayed:
```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/uNF-root does not exist. Dropping to a shell!
```

Then, surely enough, I am dropped to a shell.

The hard drive is encrypted, and the Hardy kernel boot fails before I am prompted for the passphrase. I imagine because of the encrypted drive, there's an additional step I need to perform after installing the kernel.

Thanks for the help!

---

### Post by vinpous on 2008-02-25
> **Hero of Time said:**
> Switch to WEP encryption and it should work a lot better. As you could have read from my posts, since the kernel modules newer then 2.6.24-5, the iwlwifi driver doesn't work as it should. No WPA(2), no IEEE802.1x, nothing except for WEP. Although I have my doubts about that too, as I have all three wifi encryptions on locations I go to (WPA at home, other 2 at school) and WEP stopped after some time. Could also have been a drop in connection, reset from AP, etc. So unless you can compile iwlwifi version 1.1.17, you are better off with Windows. I didn't have any problems with the ipw3945 driver though.

Thanks for the response. I didn't try WEP at all, but am back on Windows for the time being. I'll be sure to give it a try again down the track, or on my desktop which is simply serving files/playing CDs while I do exercise. :D

---

### Post by Gigamo on 2008-02-25
> **Hero of Time said:**
> Could you tell me the result of 'modinfo iwl3945'? Does it say 1.2.0 or a different version? 1.2.0 does not work for me.

s0ullight:
Did you remove your eth1 connection from the 70-persistent-net.rules file found in the /etc/udev/rules.d folder? Do a 'sudo mv 70-persistent-net.rules 70-persistent-net.rules.bak' and reboot. Check if the name is wlan0 now. You can also see the logical name of the nic by typing 'lshw -C network'.

modinfo says 1.2.0, so it seems it does work here :)

---

### Post by Hero of Time on 2008-02-25
> **Gigamo said:**
> modinfo says 1.2.0, so it seems it does work here :)
Ok, so it works for you. What software do you use to connect to your AP? I use wpa_supplicant (have to because of school network that uses 802.1x) and I'm on Xubuntu (xfce) so I don't have the gnome network manager (which might use wpa_supplicant). I don't feel like installing it, as I've heard others about it that it just plain sucked when connecting to different APs.

---

### Post by Gigamo on 2008-02-25
Well, i take that back. At home, with a WRT54GL Linksys router and WPA2 encryption, its working fine.

Right now I'm somewhere else, with a different linksys router model, the same wpa2 encryption, and here it doesn't work. I had to boot back into 2.6.24-5 to get connected. I guess I'm using wpa_supplicant, not sure, I'm using WICD as a network manager.

---

### Post by Hero of Time on 2008-02-25
> **Gigamo said:**
> Well, i take that back. At home, with a WRT54GL Linksys router and WPA2 encryption, its working fine.

Right now I'm somewhere else, with a different linksys router model, the same wpa2 encryption, and here it doesn't work. I had to boot back into 2.6.24-5 to get connected. I guess I'm using wpa_supplicant, not sure, I'm using WICD as a network manager.
I knew it! :P I have also a Linksys router, the WRT54GLX4. I have WPA/WPA2 both enabled. I don't know if Linux uses WPA or WPA2 (same goes for Windows). I don't want to find out by disabling WPA and force WPA2, as I don't know if I will be able to connect to the router or not after that.

Now all we can do is wait for a better version to be released in the modules. Does anyone have a launchpad account and can report this issue to the Ubuntu developers? They should know that this modules does not work, while the previous one did.

---

### Post by LK_gandalf_ on 2008-02-25
I'm sorry, an easy question.
I should try your kernel update script to solve an issue with my lan card. but I don't have an intertnet connection.

During the update is it required or I can upload the script on a usbdrive and go?

---

### Post by BC7333 on 2008-02-26
Regarding shutdowns I reported with the 7 kernel that disappeared, they have reappeared with 8.

I did see though that the shutdowns are not really hangs, but that the lcd backlight turns off.  The sun was shining and I could faintly see the page I was viewing.

This started happening only after several updates.  I wonder if there is some kind of update that caused this effect.

This happens ONLY when the laptop is charging so am ruling out a defective backlight.. thinking more towards some power saving feature or such.

---

### Post by Hero of Time on 2008-02-26
> **LK_gandalf_ said:**
> I'm sorry, an easy question.
I should try your kernel update script to solve an issue with my lan card. but I don't have an intertnet connection.

During the update is it required or I can upload the script on a usbdrive and go?
The script uses apt-get commands, so no, you have to have internet in order to get the new kernel that way. What you might try is download the packages from [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/) but keep in mind that you need the dependencies too.

---

### Post by SomeGuyDude on 2008-02-26
I've got the script ready to go, but I use WPA enterprise for my university network. Does anyone know if it'll work with the new kernel?

---

### Post by Hero of Time on 2008-02-26
That depends which wifi card you have. If you have the intel pro wireless 3945, then don't update as the iwl3945 module does not work.

---

### Post by SomeGuyDude on 2008-02-26
> **Hero of Time said:**
> That depends which wifi card you have. If you have the intel pro wireless 3945, then don't update as the iwl3945 module does not work.

How do I go about checking that? I know it's an Intel, but I have no idea what number.

EDIT: looked it up by my model number. It's the Intel PRO/Wireless 3945ABG. Guess that means I'm out. Damn.

---

### Post by Hero of Time on 2008-02-26
See the specs of your laptop. Else, use lspci or lshw -C network to see what you have. Nofi, but this is basic stuf, you should know this without asking. Use google if you don't.

---

### Post by SomeGuyDude on 2008-02-26
> **Hero of Time said:**
> See the specs of your laptop. Else, use lspci or lshw -C network to see what you have. Nofi, but this is basic stuf,** you should know this without asking**. Use google if you don't.

At some point in my Linux career I'm going to be asking things. Without pursuing knowledge, I have no idea how I'm supposed to gain it. This "you shouldn't have to ask that" attitude pisses me off because at one point all of us were unaware of these things.

EDIT: Besides, I was speaking specifically about a command to check. Now, I have a restricted driver, apparently, and was having a difficult time looking it up online, so I asked in the hopes that there was a command. I'm wondering how in the world I was supposed to know what command to use to identify hardware without asking at some point.

---

### Post by lemurian on 2008-02-26
> **SomeGuyDude said:**
> This "you shouldn't have to ask that" attitude pisses me off because at one point all of us were unaware of these things.

In general, answering a beginner with RTFM or "you shouldn't have to ask that" is certainly problematic.

But consider the context in which you are asking.  Yes, Walkerk made a script that greatly simplifies upgrading to a Hardy kernel.  However, one should not assume that this is something beginners should attempt.  **This upgrade is not a no-brainer.**  If you don't have enough experience with Linux (and not knowing how to query your hardware shows that you don't), then you should not attempt the upgrade.  Please realize that if you perform the upgrade, you end up with an unsupported system.  There's no telling what kind of problems you might encounter and there are very few people who are going to be able to help you because very few people run Feisty or Gutsy with a Hardy kernel and among those, very few have the exact hardware you have.  If you are not  significantly self-sufficient, you can quickly find yourself up sh*t creek without a paddle.

So I'd say in this context the answer "you shouldn't have to ask that", while perhaps not pleasant for the person receiving it, is quite appropriate.

---

### Post by SomeGuyDude on 2008-02-26
> **lemurian said:**
> In general, answering a beginner with RTFM or "you shouldn't have to ask that" is certainly problematic.

But consider the context in which you are asking.  Yes, Walkerk made a script that greatly simplifies upgrading to a Hardy kernel.  However, one should not assume that this is something beginners should attempt.  **This upgrade is not a no-brainer.**  If you don't have enough experience with Linux (and not knowing how to query your hardware shows that you don't), then you should not attempt the upgrade.  Please realize that if you perform the upgrade, you end up with an unsupported system.  There's no telling what kind of problems you might encounter and there are very few people who are going to be able to help you because very few people run Feisty or Gutsy with a Hardy kernel and among those, very few have the exact hardware you have.  If you are not  significantly self-sufficient, you can quickly find yourself up sh*t creek without a paddle.

So I'd say in this context the answer "you shouldn't have to ask that", while perhaps not pleasant for the person receiving it, is quite appropriate.

Hm, you make a good case.

I hadn't thought of this as the equivalent of a beta test, given that the 2.6.25 kernel is in the works, but if that's how things go then there you have it. I have no problems with breaking everything (I keep a weekly copy of my home folder on an external HD), so I'm not exactly worried that I might find myself up **** creek, my main concern was just discovering if I'm going to be able to get online and look through The Google when I -do- start breaking things. Believe you me I'm willing to spend all the time I need to in searching through documentation to iron things out, I just figured in this case going "hey what's a command for that" was faster.

Ya dig?

---

### Post by 1.PostMan on 2008-02-27
Hello All,

i would today use the Python Script to install the Kernel from Hardy. There is not possible while the Script reports an Error with a Package

```
Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  linux-restricted-modules-generic: Hängt ab: linux-restricted-modules-2.6.24-10-generic ist aber nicht installierbar

```

Is this Problem current known?

---

### Post by Hero of Time on 2008-02-27
> **1.PostMan said:**
> Hello All,

i would today use the Python Script to install the Kernel from Hardy. There is not possible while the Script reports an Error with a Package

```
Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  linux-restricted-modules-generic: Hängt ab: linux-restricted-modules-2.6.24-10-generic ist aber nicht installierbar

```

Is this Problem current known?
That is quite simple. They already build the 2.6.24-10 kernel, but not the modules yet. So you get that error, because the corresponding modules aren't available (yet).

@SomeGuyDude:
I gave the commands you asked for. I was just a bit suprised that you didn't know them, as they are mentioned here a couple of times and in most networking howto's. I believe that some commands, even for beginners, should be common knowledge. It's not wrong to ask, but as Lemurian stated, this isn't an 'Absolute beginners talk'-topic.

---

### Post by 1.PostMan on 2008-02-27
OK, i hope these coming soon

---

### Post by Hero of Time on 2008-02-27
So do I. I hope for new iwl3945 modules that work.

---

### Post by 1.PostMan on 2008-02-27
I´am too, my ThinkPad need this Modul also  :)

---

### Post by Hero of Time on 2008-02-27
I just checked [http://packages.ubuntu.com/hardy/base/](http://packages.ubuntu.com/hardy/base/) and I saw the -10 modules. That means they have uploaded them. Could you see if they have a better version then 1.2.0 of the iwlwifi module? In order to get the wireless working, restricted modules is not needed, as the driver isn't a restricted driver (though it might show up in restricted manager).

Hmm, checking the changelog, the only thing I see is as follows:
> * Enabled iwlwifi LEDS
    - LP: #176090
  * iwlwifi spams syslog
    - LP: #191388
That would indicate that the module is still on 1.2.0.

---

### Post by 1.PostMan on 2008-02-27
I Found in the Kernel Changelog:

```
* iwlwifi3945/4965: fix rate control algo reference leak
```

---

### Post by Hero of Time on 2008-02-27
But would that also fix the issue of associating correctly? I can only associate with my router, as in, iwconfig shows the network name, but there is no link.

---

### Post by STA on 2008-02-28
Worked fine for me on Acer Asprie 9412 laptop with nVidia GeForce 7300 video card.
Thanks for this work !!

---

### Post by BC7333 on 2008-02-28
Upgrade to 10 successful here.

Wireless LED for intel pro 3945 still not working though.  Will see if the backlight shutdown problem resolved.

BTW what is the proper response in the script for:

Would you like to run autoclean to
remove unnecessary files left behind?

what is removed?

---

### Post by BC7333 on 2008-02-28
Noticed a lot more cursor 'drift' today with my stick pointer.

---

### Post by walkerk on 2008-02-28
> **BC7333 said:**
> Upgrade to 10 successful here.

Wireless LED for intel pro 3945 still not working though.  Will see if the backlight shutdown problem resolved.

BTW what is the proper response in the script for:

Would you like to run autoclean to
remove unnecessary files left behind?

what is removed?

Autoclean removes packages that are no longer needed. It is safe to reply "yes". :)

---

### Post by goldsniper on 2008-02-28
Just did a clean manual upgrade; again!. 
Successful. Wireless is detected and running nicely  by default. It report using the iwl3945 driver.
I notice my laptop sound (ALSA) is extremely too loud.

My laptop specs:

HP Compaq Presario V3000 series (V3210TU)

Processors: Intel Core Duo T2250 (2 x 1.73 GHz, 2MB L2 cache, 533MHz FSB).
Memory: 2GB DDR2.
Hardisk: 80GB HDD SATA.
Display/LCD Screen: Intel® Graphics Media Accelerator 950 share 64MB
Sound: HDA Intel
LAN : Nic 10/100,
Modem : Modem 56K,
Ports: IEEE 1394,Card Reader 5in1, Bluetooth.
Ext.Drive : DVD±RW,
Wi-Fi: Intel Pro Wireless 802.11a/b/g.


~$ uname -r


[COLOR="Magenta"]2.6.24-10-generic[/COLOR]


~$ locate iwl3945.ko


[COLOR="Blue"]/lib/modules/2.6.24-10-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko[/COLOR]


~$ lspci -v -t


-[0000:00]-+-00.0  Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
           +-02.0  Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
           +-02.1  Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
           +-1b.0  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
           +-1c.0-[0000:02-03]--
           +-1c.2-[0000:04]--
[COLOR="Red"]           +-1c.3-[0000:05]----00.0  Intel Corporation PRO/Wireless 3945ABG Network Connection[/COLOR]
           +-1d.0  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller
           +-1e.0-[0000:08]--+-08.0  Intel Corporation PRO/100 VE Network Connection
           |                 +-09.0  Ricoh Co Ltd R5C832 IEEE 1394 Controller
           |                 +-09.1  Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
           |                 +-09.2  Ricoh Co Ltd R5C843 MMC Host Controller
           |                 +-09.3  Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter
           |                 \-09.4  Ricoh Co Ltd xD-Picture Card Controller
           +-1f.0  Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801G (ICH7 Family) IDE Controller
           +-1f.2  Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
           \-1f.3  Intel Corporation 82801G (ICH7 Family) SMBus Controller


~$ iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

[COLOR="SeaGreen"]wlan0_rename  IEEE 802.11g  ESSID:"penyu"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:78:CA:1C:DA   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=85/100  Signal level=-49 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR]



~$ lsusb


[COLOR="black"]
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard USB Wireless (Bluetooth + WLAN) Interface [HP Integrated Module]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000[/COLOR]



[COLOR="Red"]~$ sudo modinfo iwl3945


filename:       /lib/modules/2.6.24-10-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.2.0
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     8E95C617988943846696F97
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        iwlwifi_mac80211
vermagic:       2.6.24-10-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
[/COLOR]

---

### Post by Gigamo on 2008-02-28
Here's my issue with -10: I'm not using any login manager, when I start up I get to the VT where I have to enter my username and password (usually) and then start X by typing startx. However, -10 doesnt ask me for my username/password even when the boot sequence is finished, and I cannot issue any commmands, as if it is stuck, and there is also no more harddrive activity.

---

### Post by Hero of Time on 2008-02-29
Goldsniper, first, change the output of lsusb to a different colour, yellow on white is hard to read.
Could you also give the output of 'modinfo iwl3945'?

I tried the -10 yesterday, but removed it shortly after it because my wireless didn't work, which I thought it didn't but I made a mistake in my script, which caused my interface to stop the association process :X.

Also, on my Xfce panel, I have a battery monitor icon that shows how much time I have left in my battery, and when charging how long it would take to reach 100%. Now, it doesn't do that anymore. It does show how long I can run on my battery, but the time refreshes everytime the status is a percent lower, and that isn't good. When charging, it changes the remaining time to charge to remaining time on battery power, that can go up to more then 12 hours, until it's finished charging, then it's back to 00:00. Anyone know how to fix this? There isn't a new version for the battery panel plugin, so updating it is not possible. Perhaps somewhere in ACPI/APM that needs a fix?

---

### Post by goldsniper on 2008-02-29
okay , i'll add it  above

---

### Post by Hero of Time on 2008-02-29
Thanks. It's still the same version as the -7 kernel module, and that one didn't work on my laptop. Still a no go update for me. Anyone else with the latest kernel modules and the ipw3945 card that have WPA running without problems?

Oh, and you might want to remove the eth1 entry in the udev/rules.d/70-persistent-net.rules file, as your wifi will be named wlan0 instead of wlan0_rename after a reboot. Unless you still use the Gutsy kernel too with the ipw driver.

---

### Post by damneddark on 2008-03-01
installed on sony vaio VGN-CR14GN, without a hitch. Used the python script
reinstall the video driver for ATi, that's all you gotta do. Even compiz and AWN working fine.

---

### Post by BC7333 on 2008-03-01
Track stick 'wander' seems to be a bit less after reboot.  Fan however seems to run constantly where before it ran only when watching video. Ergo less battery 'life' with the 10 kernel.

---

### Post by mavila on 2008-03-02
HDave - appreciate the help. Finally got the 116 any-to-any patch installed, but ended up doing a VMWare upgrade from 5.5 to 6.0.... with 27 days left on the eval key. Not sure If I want to pay the upgrade charge though.

Someone suggested VirtualBox - and I did work with that for a week or so. Its a nice project, the downside is unless you use the licensed version there is no USB, I had "difficulty" reading VMWare volumes (it would start, then just hang), and for whatever reason shared folders seems to be flaky - it did work, just not reliably.

While Im sure that most of those issues were mine, VMWare (for better or worse) offers me a compatibility layer across multiple enterprises.... and thats important to me, so IN this case commercial interests win.

Appreciate all the guidance though

---

### Post by megahead13 on 2008-03-02
I 've upgraded to Hardy's kernel. Everything is fine, apart from my HP printer. I 've reinstalled HPLIP, but no use. What can I do to resolve this issue? Thanx in advance...

---

### Post by lemurian on 2008-03-02
> **megahead13 said:**
> I 've upgraded to Hardy's kernel. Everything is fine, apart from my HP printer. I 've reinstalled HPLIP, but no use. What can I do to resolve this issue? Thanx in advance...
If it is connected through usb you might want to search this thread with the keyword "usb" to find all the posts that discuss usb issues.  Otherwise, I don't know.

---

### Post by ccw127 on 2008-03-02
.

---

### Post by megahead13 on 2008-03-02
> **lemurian said:**
> If it is connected through usb you might want to search this thread with the keyword "usb" to find all the posts that discuss usb issues.  Otherwise, I don't know.
But of course. I had to update the udev package as well. Doh! Thanx for pointing the usb :)

---

### Post by BC7333 on 2008-03-03
I believe my problems with backlight turning off while charging are somehow related to ACPI with the 8, 9 and 10 kernels.  All settings I can get to regarding power are set to 'never'.

Is there an alternative to using ACPI?

---

### Post by lemurian on 2008-03-03
> **BC7333 said:**
> I believe my problems with backlight turning off while charging are somehow related to ACPI with the 8, 9 and 10 kernels.  All settings I can get to regarding power are set to 'never'.

Is there an alternative to using ACPI?
There's APM but that is more primitive than ACPI in functionality and might not be available on your specific machine.  AFAIK development efforts are spent more on ACPI than APM.

---

### Post by tlu on 2008-03-03
My experiences were rather mixed. When I upgraded to 2.6.24-8 using the script everything went smoothly. But I had the impression that the boot process took a little bit longer and that overall performance decreased a bit.

I checked my two harddisks with hdparm -i and found that both were running with UDMA2 although their maximum mode is UDMA6 and UDMA5. Transfer rates measured with hdparm -Tt were signifi&#263;antly worse than expected. Then I found hints with dmesg that were identical to the ones mentioned in [Bug #195221]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195221") . Some days later I started hardy.py again and this time 2.6.24.10-generic and 2.6.24.11-386 were installed. Unfortunately, I couldn't boot Ubuntu any more even when I chose one of the older kernels. 

I restored the image of my root partition containing kernel 2.6.22 - and everything's running okay again. And my harddisks are addressed with UDMA6 and UDMA5 again. :)

Bottom line: It seems that kernel 2.6.24 still has some serious bugs.

---

### Post by lemurian on 2008-03-03
> **tlu said:**
> Some days later I started hardy.py again and this time 2.6.24.10-generic and 2.6.24.11-386 were installed.

I ran into the same problem.  That's because when a new kernel is released, the modules for it trickle out to the package repository in bits and pieces rather than all at once.   It can take a few days for all the packages making up a kernel to be present together in the repository.

That was precisely the problem yesterday (I don't know if it's been fixed since).  They had **some** of the modules for 2.6.24-11 released but not all of them.  When I did my upgrade, the nvidia-glx-new in the archive was dependent on the image for 2.6.24-11 so that image was installed besides 2.6.24-10 so I ended up with **most of 2.6.24-10** and **bits of 2.6.24-11**.  Unfortunately, the nvidia driver was for 2.6.24-11 so when I rebooted X did not come up properly.  I had to get back on the network and manually clean up the mess by issuing a bunch of apt-get commands and manually downloading and installing a version of nvidial-glx-new which was no longer available through the repository.

I'm pretty sure there would be a way to code the hardy.py script to check against this kind of scenario but I'm not going to petition for this feature.  If walkerk wants to implement it, great.  If not, I'm going to live with the current script and try to pay attention to possible problems.

---

### Post by tlu on 2008-03-03
> **lemurian said:**
> I ran into the same problem.  That's because when a new kernel is released, the modules for it trickle out to the package repository in bits and pieces rather than all at once.   It can take a few days for all the packages making up a kernel to be present together in the repository.

That was precisely the problem yesterday (I don't know if it's been fixed since).  They had **some** of the modules for 2.6.24-11 released but not all of them.  When I did my upgrade, the nvidia-glx-new in the archive was dependent on the image for 2.6.24-11 so that image was installed besides 2.6.24-10 so I ended up with **most of 2.6.24-10** and **bits of 2.6.24-11**.  

I guess you're right. I might try it again to see if the DMA problem is fixed in the meanwhile. But only with an up-to-date backup of my root partition available!;)

---

### Post by goldsniper on 2008-03-03
Update to new kernal...again!

Everything is working fine... 

uname -r 

2.6.24-11-generic

---

### Post by °Spitfire on 2008-03-03
Hi, i want to ask what problems i can face when upgrading the kernel. After a upgrade, is it still posible to use the programs i get from synaptic, or do i have to change the repos..... .
 
 
Thx, in advance :)

---

### Post by Hero of Time on 2008-03-03
> **°Spitfire said:**
> Hi, i want to ask what problems i can face when upgrading the kernel. After a upgrade, is it still posible to use the programs i get from synaptic, or do i have to change the repos..... .
 
 
Thx, in advance :)
You can still use all the programs you have and install from the repo. Some problems you might encounter is not working hardware (e.g. network). It's best to keep an older kernel version to fall back on in case you mess up.

---

### Post by °Spitfire on 2008-03-03
Thank, you! I will try it, if it doesn't work i still can delete it.

---

### Post by tlu on 2008-03-04
> **goldsniper said:**
> Update to new kernal...again!

Everything is working fine... 

uname -r 

2.6.24-11-generic

Thanks - good to know! Have you already checked if you have the same DMA problems I mentioned above?

---

### Post by goldsniper on 2008-03-04
tlu:
Glad that u mention it, i did some testing :

**hdparm -i /dev/sda**

/dev/sda:

 Model=FUJITSU MHV2080BH PL                    , FwRev=892C    , SerialNo=NW9ZT6C3DYAM        
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

[B]
hdparm -Tt /dev/sda[/B]

/dev/sda:
 Timing cached reads:   2228 MB in  2.00 seconds = 1115.04 MB/sec
 Timing buffered disk reads:  108 MB in  3.01 seconds =  35.84 MB/sec
[B]
hdparm -X68 /dev/sda[/B]

/dev/sda:
 setting xfermode to 68 (UltraDMA mode4)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error

Frankly, i do not know if the problems consist! What do you think?

---

### Post by BC7333 on 2008-03-04
Upgrade to 11 went well.

Only remark so far, no working wireless LED.

Cheers all

---

### Post by tlu on 2008-03-04
> **goldsniper said:**
> tlu:
Glad that u mention it, i did some testing :

goldsniper, thanks for your reply!

> 

**hdparm -i /dev/sda**

/dev/sda:

 Model=FUJITSU MHV2080BH PL                    , FwRev=892C    , 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 
 * signifies the current active mode

This means that your HD is already running with the fastest UDMA mode it is capable of (UDMA5).

> 
[B]
hdparm -Tt /dev/sda[/B]

/dev/sda:
 Timing cached reads:   2228 MB in  2.00 seconds = 1115.04 MB/sec
 Timing buffered disk reads:  108 MB in  3.01 seconds =  35.84 MB/sec

The second value seems to indicate that the HD is probably some years old (36 MB/sec is rather low).

> [B]
hdparm -X68 /dev/sda[/B]

/dev/sda:
 setting xfermode to 68 (UltraDMA mode4)


Since your HD is already running with UDMA5 this doesn't make too much sense ;)

> Frankly, i do not know if the problems consist! What do you think?

It seems that at least on your system this problem doesn't exist. I will try 2.6.24.11 again. Thanks again!

---

### Post by goldsniper on 2008-03-04
tlu thanks for replying.

It is nice to know my lappy doesn't have the problem. 


Quote:

hdparm -Tt /dev/sda

/dev/sda:
Timing cached reads: 2228 MB in 2.00 seconds = 1115.04 MB/sec
Timing buffered disk reads: 108 MB in 3.01 seconds = 35.84 MB/sec

[B]The second value seems to indicate that the HD is probably some years old (36 MB/sec is rather low).
[/B]

Is this a bad thing?

---

### Post by tlu on 2008-03-04
> **goldsniper said:**
>  The second value seems to indicate that the HD is probably some years old (36 MB/sec is rather low).
[/B]

Is this a bad thing?

Well, it only says that the performance of that disk is not overwhelming compared to newer disks. On the other hand, you indicated that you are using a laptop, and HDs used in laptops are often a little bit slower as many of them are running only with 5,400 UPM.

---

### Post by lemurian on 2008-03-04
I've upgraded to 11 a few minutes ago.  Everything looks fine so far.

I had a strange problem with 10 however.  This morning I suspended my laptop.  When I resumed it, it looked like X crashed.  I had a login prompt in X but all the text consoles were gone.  I tried logging in but the login freezed in mid-process.  I killed X (Ctrl-Alt-Backspace) and logged in again but this time, the login process did not even start.

The syslog file show some really strange stuff like segfaults and X crashing:

```

Mar  4 10:38:01 bodhi kernel: [10429.799852] hald-addon-keyb[10178]: segfault at
 fffffffd eip b7e2139c esp bfb47c08 error 4
Mar  4 10:38:01 bodhi kernel: [10429.862869] hald-addon-keyb[10179]: segfault at
 fffffffd eip b7e1b39c esp bfdc8668 error 4
Mar  4 10:38:01 bodhi kernel: [10429.879195] usb 4-1.2.2.3: USB disconnect, address 14
Mar  4 10:38:01 bodhi kernel: [10429.899837] btnx[10466]: segfault at 00000000 eip 0804a1ed esp bfa8b620 error 4
Mar  4 10:38:01 bodhi kernel: [10429.947830] hald-addon-keyb[10405]: segfault at fffffffd eip b7e4339c esp bfc63d18 error 4
Mar  4 10:38:01 bodhi kernel: [10429.980016] usb 4-1.2.2.4: USB disconnect, address 15
Mar  4 10:38:01 bodhi kernel: [10430.011784] hald-addon-keyb[10284]: segfault at fffffffd eip b7e3d39c esp bfc2e4f8 error 4
Mar  4 10:38:01 bodhi kernel: [10430.099686] hald-addon-keyb[10458]: segfault at fffffffd eip b7db939c esp bfbf7e08 error 4
Mar  4 10:38:05 bodhi gdm[5877]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

```

That's after the sleep command had been received by the kernel.  I put it to sleep several times without any problem before.  But it looks like this time, the sh.. hit the fan real bad.  :confused:  

Anyone experienced something like this?

---

### Post by johnny9794 on 2008-03-04
I installed the upgrade with the easy install script, everything went perfect, everything works network, sound ect.

I'm going back to gutsy's original kernel because i cannot get nvidia settings installed.

I did get nvidia settings installed by uninstalling nvidia-glx-new, that was not quite such a good idea opps, now when i boot into the new 2.6.24 kernel, wow resolution is very low before the logon window and after.

So, I uninstalled nvidia-settings to get nvidia-glx-new to reinstall "nvidia-glx-new is reinstalled", same thing, very low res. and and cannot get any higher than 800x600 with a 50mhz refresh rate.

um if there is a way to access the nvidia control panel using kernel 2.6.24, then i will reinstall the OS and upgrade again with fresh new install.

for meanwhile ima reinstall and stick with gutsy's original kernel.

---

### Post by SomeGuyDude on 2008-03-04
Any updates on WPA Enterprise with the Intel wireless?

---

### Post by Hero of Time on 2008-03-04
Still no WPA or 802.1x possible. As long as they keep the 1.2.0 driver module, this stays broken.

---

### Post by SomeGuyDude on 2008-03-04
(double)

---

### Post by SomeGuyDude on 2008-03-04
Tsk. I'd been gathering documentation and gearing up for a change sometime. Ah well.

---

### Post by lemurian on 2008-03-04
> **SomeGuyDude said:**
> Any updates on WPA Enterprise with the Intel wireless?

> **Hero of Time said:**
> Still no WPA or 802.1x possible. As long as they keep the 1.2.0 driver module, this stays broken.

I presume based on previous posts that you're still talking about the iwl3945.  Someone googling and stumbling upon the question and answer could easily think that WPA (in whatever form) does not work at all with the iwlwifi driver bundled with 2.6.24-11.  That would be incorrect since WPA personal works with the iwl4965 which is also part of the iwlwifi driver.  I don't know whether WPA Enterprise works with the iwl4965.

---

### Post by Hero of Time on 2008-03-04
> **lemurian said:**
> I presume based on previous posts that you're still talking about the iwl3945.  Someone googling and stumbling upon the question and answer could easily think that WPA (in whatever form) does not work at all with the iwlwifi driver bundled with 2.6.24-11.  That would be incorrect since WPA personal works with the iwl4965 which is also part of the iwlwifi driver.  I don't know whether WPA Enterprise works with the iwl4965.
Yes, we are still talking about that damned iwl3945 module, because the 4965 is a less common card atm compared to the 3945.

As for WPA enterprise working, as long as WPA Personal works, Enterprise should work too.

---

### Post by BC7333 on 2008-03-05
> **BC7333 said:**
> Upgrade to 11 went well.

Only remark so far, no working wireless LED.

Cheers all

In addition:

Backlight turning off / hang problem still present as with all versions 8 and up..

Fan seems to run constantly with this kernel.

:(

3945 networking is fine and much better than -5 (I use open though)

---

### Post by DJ_Peng on 2008-03-05
I made the upgrade with no discovered issues so far. I did a manual upgrade last time (pre-Gutsy) but I ran the script and it was so easy it should be illegal. :) I simply ran the script, rebooted into Recovery mode, ran Envy, and rebooted into the GUI

Old kernel: 2.6.20-16-generic
New kernel: 2.6.24-11-generic
Hardware: psuedo-homebuilt (white box with several upgrades)
Mobo: Intel D845GLVA
CPU: Intel(R) Celeron(R) CPU 2.20GHz (128KB L2 cache)
RAM: 748MiB
Video: Nvidia GeForce2 MX 100/200
Display: Envision H712a
Wired network on mobo
Sound card: Creative SB Live! EMU10k1 (rev 0a)
Envy version 0.9.10

Awesome job once again, walkerk! :guitar:

---

### Post by walkerk on 2008-03-05
> **DJ_Peng said:**
> I made the upgrade with no discovered issues so far. I did a manual upgrade last time (pre-Gutsy) but I ran the script and it was so easy it should be illegal. :) I simply ran the script, rebooted into Recovery mode, ran Envy, and rebooted into the GUI

Old kernel: 2.6.20-16-generic
New kernel: 2.6.24-11-generic
Hardware: psuedo-homebuilt (white box with several upgrades)
Mobo: Intel D845GLVA
CPU: Intel(R) Celeron(R) CPU 2.20GHz (128KB L2 cache)
RAM: 748MiB
Video: Nvidia GeForce2 MX 100/200
Display: Envision H712a
Wired network on mobo
Sound card: Creative SB Live! EMU10k1 (rev 0a)
Envy version 0.9.10

Awesome job once again, walkerk! :guitar:

Glad all went well :)

---

### Post by goldsniper on 2008-03-05
Walkerk,

i just want to say thanks for your wonderful HOWTO.
I also like to thanks all of you - people in this thread. I'd leant a lot since!

It realy helps me a lot with testing the new kernel. Now i'm using Hardy 8.04 Live CD which i just dload last night. Everything is looking fine and great. 

Compiz works well and so does my wifi. My sound problem (in gutsy) also has been corrected. In fact all my hardware is natively supported now! No proprietary drivers used!

I'll install hardy on my HD afterwards and i'll post the result afterwards. 

BTW uname -r in live cd give me 2.6.24-8-generic kernel and i'll upgrade to 11 afterwardsto test using your wonderful script.

---

### Post by SomeGuyDude on 2008-03-05
Just out of curiosity, if these problems are existing with an Intel 3945 wireless card and Hardy's kernel, shouldn't Hardy itself be experiencing the same difficulties?

I ask because, just on a whim, I threw in the Alpha 5 CD I burned a bit ago today and everything worked fine, installed it, and am currently running that giant update one must do on first installation. WPA Enterprise wireless connection, Intel 3945 card in my notebook.

Unless I'm just confused, which wouldn't be impossible.

EDIT: of course, now I find out that Alpha 6 comes out TOMORROW. Dangit. Suppose I'll just do the partial upgrade.

---

### Post by gerscht on 2008-03-05
great stuff! works like a charme.

specs:
asus p5nd2-sli
pentium D 2.66
nvidia Geforce 7300

This kernel has fixed my problems with sata_nv ADMA which caused complete lock-ups.

---

### Post by goldsniper on 2008-03-05
> **SomeGuyDude said:**
> Just out of curiosity, if these problems are existing with an Intel 3945 wireless card and Hardy's kernel, shouldn't Hardy itself be experiencing the same difficulties?

I ask because, just on a whim, I threw in the Alpha 5 CD I burned a bit ago today and everything worked fine, installed it, and am currently running that giant update one must do on first installation. WPA Enterprise wireless connection, Intel 3945 card in my notebook.

Unless I'm just confused, which wouldn't be impossible.

EDIT: of course, now I find out that Alpha 6 comes out TOMORROW. Dangit. Suppose I'll just do the partial upgrade.


Yes.. it is weird because my intel 3945 worked fine both on upgrade and on hardy alpha 5 installation...

unless it is not the same chipset?

p/s : Alpha 6 tomorrow? Dang! I just did the partial upgrade for Alpha 5.

---

### Post by Depressed Man on 2008-03-05
My intel 3945 works fine with Alpha 5 (recently installed it). Though I am getting an ACPI error whenever I boot up in Hardy but that's noted as bug #191137 on launchpad.

---

### Post by Hero of Time on 2008-03-06
Does Hardy have any problems with ATi cards like on Fiesty and Gutsy? If you have X right away without any problems, then I might check the live CD and see if I have the same problem with my wireless. If I do, then I know nothing is wrong with my upgrade, but if it works, then there is something wrong with my system and I will reinstall the whole thing in the summer (Windows and Linux).

---

### Post by lemurian on 2008-03-06
> **SomeGuyDude said:**
> Just out of curiosity, if these problems are existing with an Intel 3945 wireless card and Hardy's kernel, shouldn't Hardy itself be experiencing the same difficulties?

I ask because, just on a whim, I threw in the Alpha 5 CD I burned a bit ago today and everything worked fine, installed it, and am currently running that giant update one must do on first installation. WPA Enterprise wireless connection, Intel 3945 card in my notebook.

Unless I'm just confused, which wouldn't be impossible.

EDIT: of course, now I find out that Alpha 6 comes out TOMORROW. Dangit. Suppose I'll just do the partial upgrade.
Could it be that the problem is not in the iwlwifi driver but in wpa_supplicant?  If the wpa_supplicant bundled with Hardy is different than the one in Gutsy, that could explain why there's no problem when you do a full upgrade. 

 Walkerk's script does not upgrade wpa_supplicant.

---

### Post by Hero of Time on 2008-03-06
> **lemurian said:**
> Could it be that the problem is not in the iwlwifi driver but in wpa_supplicant?  If the wpa_supplicant bundled with Hardy is different than the one in Gutsy, that could explain why there's no problem when you do a full upgrade. 

 Walkerk's script does not upgrade wpa_supplicant.
Could be, but why does it work with the 1.1.17 module and not with the 1.2.0? Also, it's the same version (0.5.6/0.6.0 I think).

---

### Post by goldsniper on 2008-03-06
okay. i did the partial upgrade to 11 which is sent down the pipe. Unfortunately Network Manager was problematic. I couldn't connect to my wireless Access Point because it was not found. Wired worked great though.

Installed WiCD and reboot.

wiCD scanned my wifi router and connected. I'll stick to WiCD until nm is fixed!

---

### Post by lemurian on 2008-03-06
> **Hero of Time said:**
> Could be, but why does it work with the 1.1.17 module and not with the 1.2.0? Also, it's the same version (0.5.6/0.6.0 I think).
Maybe for the same reasons that if you just upgrade to a Hardy kernel on Gutsy some of your usb stuff won't work unless you upgrade your udev and even then you might have to manually mess with some of the .rules files.

In the usb case, there is no bug anywhere.  It's just that the kernel, udev and modules which include .rules file in Gutsy work in a certain way and that way has changed for Hardy.  So if you mix stuff from Gutsy and Hardy, you can experience failures.  If you run a 100% Hardy system, you should not experience those failures.

Maybe the same is true for iwlwifi.  Some conventions have changed so if all packages that participate in bringing up a wireless connexion do not use the same conventions, a failure occurs.  This hypothesis remains to be proved but that's what I'd be looking for based on the fact that upgrading to a Hardy kernel on a Gutsy (or Feisty system) results in a failure that does not occur on a system which is 100% Hardy.

Why only the 3945 is affected, I don't know.

---

### Post by SomeGuyDude on 2008-03-06
> **Hero of Time said:**
> Could be, but why does it work with the 1.1.17 module and not with the 1.2.0? Also, it's the same version (0.5.6/0.6.0 I think).

Moot point, it broke after a later update.

The kernel update didn't seem to do anything (it appeared to upgrade to 11 the first go-round). After that there was a small update including, I believe, gnome-network-manager, and THEN my wireless stopped working.

After I rebooted once the giant first-run update happened and everything worked I didn't really pay attention to the next one since I assumed everything was fine. Since everything went ***-up I ended up back on Gutsy, but I'm tempted to go for Alpha 6 just so I can more closely pay attention and see if the same thing happens.

---

### Post by Hero of Time on 2008-03-06
I don't use NM, as I am an Xubuntu user. All I use is wpa_supplicant for my wireless.

---

### Post by SomeGuyDude on 2008-03-06
> **Hero of Time said:**
> I don't use NM, as I am an Xubuntu user. All I use is wpa_supplicant for my wireless.

Well then I'm extremely confused. Something definitely broke AFTER I updated everything upon first boot. Restarted, got about four updates, and then my network connection shat out.

Regardless, it didn't feel that different from Gutsy, so I can wait another month or so for all these issues to get ironed out I suppose.

---

### Post by jw5801 on 2008-03-07
Are any of you using ndiswrapper for your wireless connection that has now died?

---

### Post by SomeGuyDude on 2008-03-07
I know I'm talking Hardy's kernel on Hardy, but I'm currently running Alpha 6 (just gambled on a full install). Did a full update and on my school's WPA Enterprise connection. No more updates to install, so I'm assuming this is just how it goes.

Maybe something updated?

---

### Post by jw5801 on 2008-03-07
If you're using ndiswrapper, I believe it may be broken in this particular kernel. I just upgraded to the newer kernel to check and ndiswrapper can't even create an interface (eth1 isn't present). I remember reading about this issue and I know there's a patch around somewhere. I'm just not sure if it's the problem that I'm seeing, or if it's something else interfering.

[http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL](http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL)
[http://lkml.org/lkml/2008/3/4/300](http://lkml.org/lkml/2008/3/4/300)

---

### Post by Hero of Time on 2008-03-07
I just finished downloading alpha 6 from torrents and burnt to dvd (cd won't work, strange enough, I get errors). I will see if full hardy stuff will work properly with my wireless today.

---

### Post by SomeGuyDude on 2008-03-07
> **jw5801 said:**
> If you're using ndiswrapper, I believe it may be broken in this particular kernel. I just upgraded to the newer kernel to check and ndiswrapper can't even create an interface (eth1 isn't present). I remember reading about this issue and I know there's a patch around somewhere. I'm just not sure if it's the problem that I'm seeing, or if it's something else interfering.

[http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL](http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL)
[http://lkml.org/lkml/2008/3/4/300](http://lkml.org/lkml/2008/3/4/300)

I'm not sure if this could possibly be the culprit, but for some reason my wireless in Hardy is labeled "wlan0" and not "eth0" like it was under Gutsy.

Could it be that something is trying to read as eth0 or eth1 when the kernel wants wlan0?

If not, feel free to totally ignore this post. :lolflag:

---

### Post by Hero of Time on 2008-03-07
> **SomeGuyDude said:**
> I'm not sure if this could possibly be the culprit, but for some reason my wireless in Hardy is labeled "wlan0" and not "eth0" like it was under Gutsy.

Could it be that something is trying to read as eth0 or eth1 when the kernel wants wlan0?

If not, feel free to totally ignore this post. :lolflag:
No, the reason your wifi is labeled wlan0 is because the driver wants it like that. I had eth1 too at first with the ipw3945 module, but since the iwlwifi it's called wlan0. It's also possible that in the new kernel, all ethernet (wired) connections are called ethx, and wireless are called wlanx.

I'm now trying to get my wifi working in the live cd version of alpha 6, but so far I get nothing. Wpa_supplicant comes with error 04 and 05 messages. The exact message is:
> ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 -
I had this before, and still have sometimes but when ran via scripts or with ifup, wpa_supplicant works just fine.

Small side note, my Scroll Lock key doesn't work anymore, the LED won't go on when I hit that key. Num Lock and Caps Lock do work. Not that I ever use Scroll Lock, but it's strange the LED won't go on.

---

### Post by Hero of Time on 2008-03-07
Well, that's it, I'm done testing with the live cd. The iwl3945 module 1.2.0 just doesn't work. At least not the way I always use drivers, through wpa_supplicant.

---

### Post by tlu on 2008-03-07
I updated to kernel 2.6.24-11 using the script and ran into the same problems  I had with 2.6.24-8 mentioned in [post #498]("http://ubuntuforums.org/showpost.php?p=4445404&postcount=498"). My two harddisks ran only with UDMA 2 mode again after I booted the new kernel. Then I tried to boot the old kernel 2.6.22 but didn't succeed - the boot process just hung. After restoring the image of my root partition everything's working fine again and the harddisks are running with UDMA 5 + 6 as they should.

That was my last attempt - I'm waiting for Hardy. :(

---

### Post by DJ_Peng on 2008-03-09
I ran the script to update my kernel from 2.6.24-11-generic to 2.6.24-12-generic but when I booted back into Ubuntu my SB Live! 5.1 sound card refused to load. Anyone have any ideas why this may be and how to fix it? I tried searching the forums but couldn't come up with anything and I had to roll back to the -11 kernel just to get my sound back.

---

### Post by Ilera on 2008-03-10
This is a known issue with ubuntu kernel 2.6.24-12

Apparently it is fixed in 2.6.24-12.2, so when that package is available  for kubuntu things should work again I expect

---

### Post by goldsniper on 2008-03-10
just update to *12. Lost my sound too.

The sound card driver wasnot loaded, i think.

Edit :  Fix *12.20 just been uploaded in the launchpad

For those who are not patient:

 [COLOR="Red"]Extaliones wrote 2 hours ago: (permalink)

even quicker workaround:

sudo cp /lib/modules/2.6.24-11-generic/kernel/sound/soundcore.ko /lib/modules/2.6.24-12-generic/kernel/sound/
sudo depmod -a
sudo modprobe snd-hda-intel (or whatever you need)

and sound works again :)
[/COLOR]

---

### Post by rotorcraig on 2008-03-10
Since I upgraded to Gutsy I've suffered random freezes when using 'nvidia' drivers; if I stick with 'nv' drivers all is okay.

I've used your script and it pulled down kernel 2.6.24.12.11

All seems good so far with the exception of Google Earth.  This previously ran very slowly as I was on the 'nv' drivers.  Now when I run it I get the following message:

> "Google Earth is unable to identify your graphics card.  This is most likely because the driver for your graphics card has not been installed.  You may continue but the Google Earth is unlikely to work until you upgrade your driver."
My PC is a home build based on an ASUS A7N266-VM motherboard with a Tornado GeForce FX5200 graphics card.

RC

---

### Post by goldsniper on 2008-03-10
Looks like *12.20 is online. I updated and the sound problem is gone. Alpha 6 is back to bussiness.

---

### Post by Hero of Time on 2008-03-11
I added some info about the association problem with the iwl3945 module 1.2.0. As it seems, the 1.1.17 module is already build in the kernel, so apparently you don't need the linux-ubuntu-modules package. But I don't know what modules are in there and I might end up with hardware that doesn't work. Here is the launchpad url:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192493](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192493)

---

### Post by vijaym on 2008-03-11
good script
have a problem in trying to set up my wireless

the error message is:

[http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.bz2:) Hash Sum mismatch

any ideas

I have tried to install the b43-fwcutter via the link to the firmware site. I also notice that the software is not on the site [http://packages.ubuntu.com/hardy/net/](http://packages.ubuntu.com/hardy/net/)

been battling to get my wlan working. it can link to the router but not to the internet.


any ideas

vijay

---

### Post by ssc351 on 2008-03-11
Yo,

Since I upgaded to 2.6.24-12.19  I lost sound and want to do the latest upgrade to -12.20  but the tutorial won't find the update.  I tried doing both ways in the tutorial but it still won't update.  Anyone?  I would really like my sound back.

---

### Post by goldsniper on 2008-03-11
changre your source server to 'main server'

---

### Post by mrazster on 2008-03-12
I haven't read the whole thread..it's too big...so pardon me if this has already been asked..if so point me to the right posts.

I'm running a ATI X300 card with the restricted drivers on 2.6.22.14...how will this kenrel upgrade play with restricted drivers?....will it work without to much trouble?

---

### Post by jw5801 on 2008-03-12
You'll need to upgrade fglrx from the Hardy repo's as well. Otherwise you won't make it to a working X environment! The newer version doesn't play nice with 2.6.22 though, so it's not very well interchangeable. At least that was my experience anyway.

---

### Post by rotorcraig on 2008-03-12
> All seems good so far with the exception of Google Earth.
Spoke to soon / didn't understand.

The script had left me on 'nv' drivers which is why Google Earth wouldn't play.  As soon as I enabled 'nvidia' drivers using the Restricted Drivers menu option I experienced exactly the same freeze problems that I did with the Gutsy kernel.

I've used the Restricted Drivers menu option to go back to 'nv' drivers and all is stable now.  Haven't removed Hardy kernel as there doesn't seem any need to - it works fine.  Shame I still can't get 'nvidia' cracked though; has been driving me mad for months!!!

RC

---

### Post by ssc351 on 2008-03-12
> **goldsniper said:**
> changre your source server to 'main server'


I tried what you suggested and it was a little weird...when I went through and did the usual "sudo python hardy.py" to get the thing to update...it started going through its thing looking for updates...then it got hung on 99%, and then all of a sudden the update manager gui popped saying I had like 548 updates.  But then it disappeared as soon as the terminal command finished up.

But still no update, I can't get the terminal command to find the latest kernal nor can I do it through the update manager gui.

Any thoughts?

---

### Post by radamanthis78 on 2008-03-12
Hi,

Firstly congratulations for the script in python. It's very easy to understand (well documented) and very useful. I have a Sony Vaio VGN-SZ61MN with Intel 3945ABG wireless card. My system is Kubuntu Gutsy and my old kernel was 2.6.22 (kernel by default in Gutsy instalation). My problem is that my wireless card doesn't work, and I've tried to solve this problem with this upgrade. Unfortunately my wireless card doesn't work with the new kernel 2.6.24-12. I have a connection in intranet but not out of my net. I mean when I do "ping www.google.com" it isn't respond. Now I'm using Windows Vista because I have no option if I use Internet, but I'd like to solve my problem because I prefer to work with linux.
Any ideas for this question?

Thank you very much.

These are the outputs of main commands:

> javier@aiacos:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:"DSL"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:07:92:B6
          Bit Rate=54 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B
          Power Management: off
          Link Quality=91/100  Signal level=-39 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> javier@aiacos:~$ ifconfig
eth1      Link encap:UNSPEC  direccionHW 00-1B-77-E3-56-7C-00-00-00-00-00-00-00-00-00-00
          UP DIFUSION CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Bucle local
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0
          RX bytes:9344 (9.1 KB)  TX bytes:9344 (9.1 KB)

wlan0_ren Link encap:Ethernet  direccionHW 00:1B:77:E3:56:7C
          inet addr:192.168.1.6  Difusion:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fee3:567c/64 Scope:Link
          UP DIFUSION CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:6062 (5.9 KB)  TX bytes:26007 (25.3 KB)

> javier@aiacos:~$ dmesg | grep Intel
[   13.716344] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[   13.807767] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[   26.302380] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   29.304540] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   29.304548] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.326836] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection


---

### Post by walkerk on 2008-03-12
Did you try the WLAN NIC rename fix in my original post? I had the same problem while my wireless interface registered as wlan_ren, wlan_rename, or wmaster0...

try renaming it to **eth2** as eth1 seems to be your wired interface...

---

### Post by radamanthis78 on 2008-03-12
Hi,

I'm very happy because I'm writing by using Kubuntu. I made WLAN NIC rename fix as you explain in Miscellaneous fixes section. However I don't know why a ping doesn't work. I mean if I put "ping www.google.com", it doesn't respond, but apt-get works well and firefox also. Maybe the wireless worked well before this change. Since I've only tested my internet connection with pings. Anyways it works now. Thank you very much for your help.

These ones are my files:

File /etc/udev/rules.d/70-persistent-net.rules
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4363 (sky2)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:80:56:7c:e7", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1b:77:e3:56:7c", NAME="eth2"

```
File /etc/modprobe.d/iwl3945
```
alias eth2 iwl3945

```

And the ping tests were:

```
javier@aiacos:~$ ping www.google.com
PING www.l.google.com (64.233.169.147) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
54 packets transmitted, 0 received, 100% packet loss, time 53051ms

javier@aiacos:~$ ping 64.233.169.147
PING 64.233.169.147 (64.233.169.147) 56(84) bytes of data.

--- 64.233.169.147 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9019ms

javier@aiacos:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.90 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.72 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.53 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.27 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 1.271/1.609/1.906/0.237 ms
```

---

### Post by Hero of Time on 2008-03-13
For the ping, can you ping from Windows? I think your ping response gets blocked by your router or just doesn't go beyond the router.

---

### Post by Nunslaughter on 2008-03-13
Does anybody know why nvidia-settings isn't taken along with the nvidia drivers anymore?
It worked with 2.6.24-5, then I upgraded to -8 and from then no new kernel took nvidia-settings along...

---

### Post by radamanthis78 on 2008-03-13
> **Hero of Time said:**
> For the ping, can you ping from Windows? I think your ping response gets blocked by your router or just doesn't go beyond the router.

In Windows Vista doesn't work a ping. Yes, you have the truth.
Thanks,
  Javier.

---

### Post by radamanthis78 on 2008-03-13
Hi,

After I've fixed my problem with wireless, I've found another problem. This problem is related to sound card. It is very similar to post 543 in which sound card doesn't work. In my case my card works well but not the jack of earphones. Maybe in next kernel is solved.

Thanks,
  Javier.

---

### Post by lemurian on 2008-03-13
> **Nunslaughter said:**
> Does anybody know why nvidia-settings isn't taken along with the nvidia drivers anymore?
It worked with 2.6.24-5, then I upgraded to -8 and from then no new kernel took nvidia-settings along...
I think it is because nvidia-settings must be in lockstep with the nvidia driver and the nvidia-settings as now shipped with Hardy depends on libraries that are shipped **only** with Hardy.  

The hardy.py script issues "apt-get install" to upgrade the kernel and nvidia driver but the way "apt-get install" works, it performs "conservative" upgrades.  If there is a conflict between dependencies, it will resolve it by taking the least disturbing action.  At some point in the upgrades to newer Hardy kernels, the "least disturbing action" was to uninstall nvidia-settings rather than upgrade nvidia-settings and all the libraries it depends on.

It would be possible to request apt-get to install nvidia-settings but I think it would pull such a large amount of stuff from Hardy that you'd end up with a Frankenbuntu: half-Gutsy, half-Hardy.  (Gutsy Heron, Hardy Gibbon?)

If you must use nvidia-settings, the safe thing to do is to return to a pure Gutsy setup.  The second choice is to use Hardy alpha.  The third choice is to go with Frankenbuntu.  Or you could forget about all these choices and compile nvidia-settings for your machine.  That would probably work...

---

### Post by wilbotIV on 2008-03-19
Thanks walkerk, your script did the trick I got my mic working on my new xps 1530.  Thanks again.

---

### Post by dirk_k on 2008-03-20
I got a kernel bug after resuming from hibernation:

[   50.633081] WARNING: at /build/buildd/linux-2.6.24/fs/proc/generic.c:736 remove_proc_entry()
[   50.633088] Pid: 15650, comm: modprobe Tainted: P        2.6.24-12-generic #1
[   50.633090] 
[   50.633090] Call Trace:
[   50.633107]  [<ffffffff802f3526>] remove_proc_entry+0x1b6/0x1c0
[   50.633114]  [<ffffffff80344720>] kobject_release+0x0/0x10
[   50.633117]  [<ffffffff8034581f>] kref_put+0x3f/0x80
[   50.633130]  [<ffffffff802655ed>] sys_delete_module+0x14d/0x1e0
[   50.633136]  [<ffffffff80347bb2>] __up_write+0x22/0x130
[   50.633151]  [<ffffffff8020c37e>] system_call+0x7e/0x83

And just before it gave a segfault, but this may be unrelated (?):
[   50.418232] hald-addon-keyb[5838]: segfault at 7fe0efd rip 7f89fe451c1b rsp 7fff06da0650 error 4

After the resume I didn't have sound anymore, but I didn't notice any other problems.
Where should I report this? On the LKML or Ubuntu Launchpad bugs for the ubuntu kernel team to sort this out?

On another note: I wanted to use the new kernel because Gutsy's performance was crap: I always got high iowait problems. These high iowait problems are reported by many users in the forum and Gutsy was definitely less responsive on my system. But this new kernel is a remarkable improvement, thus unless I will be getting more oopses I will stay on this version.

Thanks.

---

### Post by BC7333 on 2008-03-22
Upgraded to hardy beta now.  Guess walkerk will be taking a (hopefully short) break.  Can't wait for his new hardy.py edition.

=D>

---

### Post by walkerk on 2008-03-22
> **BC7333 said:**
> Upgraded to hardy beta now.  Guess walkerk will be taking a (hopefully short) break.  Can't wait for his new hardy.py edition.

=D>

Won't be long :)

---

### Post by JohnFish on 2008-03-22
hardy.py worked great on a P4 3.4 2GB RAM 120 GB SATA. easiest kernel upgrade I've EVER done...

---

### Post by dart1007 on 2008-03-22
It just worked!!! on my P4 2.4Ghz 1GB RAM 200BG IDE Thank You!!!:)\\:D/

---

### Post by walkerk on 2008-03-23
> **JohnFish said:**
> hardy.py worked great on a P4 3.4 2GB RAM 120 GB SATA. easiest kernel upgrade I've EVER done...

> **dart1007 said:**
> It just worked!!! on my P4 2.4Ghz 1GB RAM 200BG IDE Thank You!!!:)\\:D/

Glad to hear it :)

---

### Post by whizkid25 on 2008-03-24
I recently installed it and everything is well...so far. However, I noticed that my original kernel 2.6.22-14 displays different memory size than that of 2.6.24-12 in the System Monitor. I have 1GB of memory by the way.

In 2.6.22, the memory is 1011MB whereas in 2.6.24 it shows 1010.9MB. I know it's not heck a lot of a difference but I'm just curious about this. 

My specs. are: Intel Centrino 1.5GHz, 1GB PC2700 DDR, 120GB Seagate HDD, 64MB ATI Mobility Radeon 9000, Dual OS - Windows XP Pro SP2 and Ubuntu 7.10

Thanks in advance.

---

### Post by walkerk on 2008-03-24
> **whizkid25 said:**
> I recently installed it and everything is well...so far. However, I noticed that my original kernel 2.6.22-14 displays different memory size than that of 2.6.24-12 in the System Monitor. I have 1GB of memory by the way.

In 2.6.22, the memory is 1011MB whereas in 2.6.24 it shows 1010.9MB. I know it's not heck a lot of a difference but I'm just curious about this. 

My specs. are: Intel Centrino 1.5GHz, 1GB PC2700 DDR, 120GB Seagate HDD, 64MB ATI Mobility Radeon 9000, Dual OS - Windows XP Pro SP2 and Ubuntu 7.10

Thanks in advance.

Not certain but its only off by 0.1. :lol

---

### Post by jw5801 on 2008-03-24
> **whizkid25 said:**
> I recently installed it and everything is well...so far. However, I noticed that my original kernel 2.6.22-14 displays different memory size than that of 2.6.24-12 in the System Monitor. I have 1GB of memory by the way.

In 2.6.22, the memory is 1011MB whereas in 2.6.24 it shows 1010.9MB. I know it's not heck a lot of a difference but I'm just curious about this. 

My specs. are: Intel Centrino 1.5GHz, 1GB PC2700 DDR, 120GB Seagate HDD, 64MB ATI Mobility Radeon 9000, Dual OS - Windows XP Pro SP2 and Ubuntu 7.10

Thanks in advance.

Possibly calculates it a little more accurately?! Dunno, should be 1024 though, I think the other 23MB is reserved for kernel bits and pieces, so maybe the new kernel just wants another 102.4kB of RAM to play with?

---

### Post by Hero of Time on 2008-03-24
The 'lost' memory is your video memory that is shared I think. Do you have an onboard video or laptop?

---

### Post by jeffebert on 2008-03-28
This is exactly what I was looking for. Thanks!

---

### Post by whizkid25 on 2008-03-30
> **Hero of Time said:**
> The 'lost' memory is your video memory that is shared I think. Do you have an onboard video or laptop?

Sorry for the late reply. It's a Dell Inspiron 600m.

My specs. are: Intel Centrino 1.5GHz, 1GB PC2700 DDR, 120GB Seagate HDD, 64MB ATI Mobility Radeon 9000, Dual OS - Windows XP Pro SP2 and Ubuntu 7.10

I'm not at all too worried about it though, just curious.

---

### Post by eagles051387 on 2008-03-31
> **crazyness003 said:**
> Hi, n00b here. I tried the python script once, and while it was running I saw something about i386 in there. I originally have kernel 2.6.22-14-rt
installed on 64 bit system. It's the Ubuntu Studio 7.10 x86_64 release. 

Is this "Hardy" Kernel a 64 bit one, or a x86?

anyway, as I was pondering on that question, the upgrade was complete and I restarted. 
When it booted back up, it told me my X server was not configured right and X windows couldnt load. I attribute this to the nvidia drivers for my display, but could it be something else?
And it its not, how to I install the nvidia drivers in that kernel?

My machine is an HP Pavilion tx1000 series (tx1308nr) tablet pc. 
It's got a Broadcom BCM94311MCG wlan wi-fi card (that I **can not** get working in 2.6.22)
and I was also wondering if the tablet screen will fully work
(In 2.6.22 I can only use it s a left mouse click, no biggie), WebCam and (most importantly sound.
lspci tells me i have an nVidia Corporation MCP51 High Definition Audio (rev a2).

Sorry about lack of organization, but it is what it is.

Any help is welcome, even telling to go ***** is also understandable.

edit: one more thing, how do I add the nvidia driver install command to the python script?


i have the exact same laptop and im trying to install hardy beta. my problem is this i can get it installed using the alternate install of hardy beta thing is when i come to boot it it hangs on loading hardware devices

---

### Post by John L on 2008-03-31
Hi there

Just wanted to say that I had no probs upgrading and whats more it restored my sound!!!  Super!

My specs are: intel core 2 duo E4500, 2GB ram, nvidia 8600gs, dual boot with vista.  

Glad I gave it a go.

John

---

### Post by sp00ner on 2008-04-13
Total Linux rookie here. Stumbled across this thread because my wireless card (Intel 3945) suddenly stopped working. The trail of links lead me here. I Copied and pasted the commands from the manual installation section and it worked great. Wireless card is now working again...YAY!!! :guitar:



HP NC6400
Intel Centrino Duo T2400@1.83GHz.
1GB DDR2 SDRAM
ATI Mobility Radeon

---

### Post by articpenguin on 2008-04-15
Works here.

T3626 

replaced the sempron with a be-2350.

---

### Post by schneidexe on 2008-04-16
Hi,

I used the script to Update directly from feisty using a 2.6.21 kernel. And it worked like charm on my Samsung R70 (C2D 2x1.8Ghz, 2GB RAM, Nividia M8600GS).

uname -a says:
Linux uranus 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Thanks!

P.S.: Cooool! Now even standby and hibernate seem to work! :-) To bad that btsco does not (seems to be a 2.6.24-problem)! :-(

---

### Post by fourscore on 2008-04-18
Have upgraded the kernel ( from Gutsy)  successfully in my  laptop - HPnx6110 . The wireless is now not working.   
The wireless card is : -  Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I get the following error while trying to install the driver :
 sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter

Am I missing something ?

The wireless worked perfectly under Gutsy after installing the restricted drivers.  Pls help how to get this to work in the new kernel.

---

### Post by era86 on 2008-04-18
Works like a charm using T61 thinkpad.  I used the py script.

uname -r reads
2.6.24-16-generic

Thank you!

---

### Post by Callinator on 2008-04-18
Works fine with E6400, GF7950, Asus P5B-E

Thanks!

---

### Post by schneidexe on 2008-04-18
@fourscore

Have you tried this: [http://packages.ubuntu.com/hardy/b43-fwcutter](http://packages.ubuntu.com/hardy/b43-fwcutter)
It's only available since hardy.

---

### Post by fourscore on 2008-04-18
> **fourscore said:**
> Have upgraded the kernel ( from Gutsy)  successfully in my  laptop - HPnx6110 . The wireless is now not working.   
The wireless card is : -  Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I get the following error while trying to install the driver :
 sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter

Am I missing something ?

The wireless worked perfectly under Gutsy after installing the restricted drivers.  Pls help how to get this to work in the new kernel.

Reinstalled  b43-fwcutter thru Synaptic and the insall  proceeded to download the firmware too  successfully.   The wireless is now working.   IN the blacklist file  I also commented out  the entry blacklist  bcm43xx .

I am now running   Gutsy with  Kernel 2.6.24.16 on my   HP nx6110 - the specs are given below for reference.
-------------
Intel Pentium M processor 730* (1.6-GHz, 533-MHz FSB, 2-MB L2 cache)
768-MB 333-MHz DDR SDRAM
40-GB 5400 rpm
Dual boot -  XP and Gutsy
Display 14.0-inch TFT XGA with 1024 x 768 resolution (up to 16.7 M colors internal)
Intel Graphics Media Accelerator 900 - Up to 128 MB of shared system memory
Audio ADI AC '97 CODEC, Line out/headphone and microphone jacks
24X DVD/CDRW Combo
56K Fax/Modem,
Integrated NetXtreme Ethernet Controller (10/100 NIC)
Integrated Wireless Broadcom 4318 802.11b/g WLAN
Touchpad with scroll zone
----------------
There were some errors at boot - apparmor, powernowd, cupsysd.  Once I upgraded these packages the errors went away.  Had to update    the  HP drivers too for my printer.

Thanks to all the posts above .

---

### Post by fourscore on 2008-04-19
Now that the kernel has been successfully upgraded  in Gutsy ,  is there a way to upgrade  Gnome to the new version ?

---

### Post by jw5801 on 2008-04-19
> **fourscore said:**
> Now that the kernel has been successfully upgraded  in Gutsy ,  is there a way to upgrade  Gnome to the new version ?

Much the same way, but if you're going to do that you may as well upgrade all the way to Hardy, even if you wait until the end of next week when it's released.

---

### Post by fourscore on 2008-04-19
> **jw5801 said:**
> Much the same way, but if you're going to do that you may as well upgrade all the way to Hardy, even if you wait until the end of next week when it's released.

I'm already running OO2.4 ( removed 2.3 and installed 2.4 directly).   I have installed FF2 using ubuntuzilla ,  Not interested in FF3 beta,   willing to wait for the final release and will update directly from FF2 to FF3.    I also have  a few windows apps running under wine.    I  feel i can give  Hardy a  skip and  go  directly to  Intrepid 8.10.

Tks

---

### Post by phr024 on 2008-04-20
Hello,

I use a Acer Extensa 5220 Notebook it's worked like a charm.

Only the Atheros wireless network drivers does not work in this kernel??

U use a d-link wireless usb stick instead.

Kind regards.

Patrick.

---

### Post by daflame on 2008-05-05
I know that this is probably not directly related to this channel, but I noticed the new release 2.6.24-17 is out and there are no virtualbox modules yet and the current module sources would not compile.

---

### Post by simoncullen on 2008-05-17
Hello,

I've just reinstalled Gutsy after a very unhappy 4 day experience with Hardy (it was riddled with problems -- and I'm using fairly well-supported hardware!).

So I've started with a fresh install of Gutsy.  Ran all of the updates and then ran the script to upgrade to the Hardy kernel (as I had with my previous pre-Hardy Gutsy install).  Everything seemed to go swell -- but I can't get my Nvidia drivers going.  I upgraded the nvidia-glx-new to Hardy's version when I ran the script. 

When the login screen comes up its at 640x480 (or 800x600?) and there's no acceleration (i.e., it's falling back to the VESA driver, I guess).  Nvidia is enabled in Restricted Drivers -- so I have no idea why this isn't working.  It's an 8500 GT card, which is well-supported.

I would usually fall back on Envy but when I run it:
> 
simon@aristurtle:~$ envy -t

...

The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed
E: Broken packages

ENVY ERROR: The following packages cannot be installed:
libc6-i386
simon@aristurtle:~$ 

I can't find away around this.  I've tried using Hardy's version (EnvyNG), but that complains that I don't have a supported operating system (it's for Hardy and I'm using Gutsy).

I've tried uninstalling all Nvidia related things and reinstalling.  I've searched around the forums and tried everything I can think of, to no avail.

So any tips will be much appreciated.

Edit: I'm using Gutsy 64 bit

Thanks!

---

### Post by BC7333 on 2008-05-18
> **simoncullen said:**
> Hello,

I've just reinstalled Gutsy after a very unhappy 4 day experience with Hardy (it was riddled with problems -- and I'm using fairly well-supported hardware!).

So I've started with a fresh install of Gutsy.  Ran all of the updates and then ran the script to upgrade to the Hardy kernel (as I had with my previous pre-Hardy Gutsy install).  Everything seemed to go swell -- but I can't get my Nvidia drivers going.  I upgraded the nvidia-glx-new to Hardy's version when I ran the script. 

When the login screen comes up its at 640x480 (or 800x600?) and there's no acceleration (i.e., it's falling back to the VESA driver, I guess).  Nvidia is enabled in Restricted Drivers -- so I have no idea why this isn't working.  It's an 8500 GT card, which is well-supported.

I would usually fall back on Envy but when I run it:


I can't find away around this.  I've tried using Hardy's version (EnvyNG), but that complains that I don't have a supported operating system (it's for Hardy and I'm using Gutsy).

I've tried uninstalling all Nvidia related things and reinstalling.  I've searched around the forums and tried everything I can think of, to no avail.

So any tips will be much appreciated.

Edit: I'm using Gutsy 64 bit

Thanks!

Simon,  Not running 64 bit but this is what helped me with the nvidia problem:

[http://www.nvnews.net/vbulletin/showthread.php?t=111460](http://www.nvnews.net/vbulletin/showthread.php?t=111460)

Good luck!

edit:  another good reference: [http://tuxicity.wordpress.com/2008/03/05/ubuntu-hardy-nvidia-and-craziness/](http://tuxicity.wordpress.com/2008/03/05/ubuntu-hardy-nvidia-and-craziness/)

---

### Post by Cato2 on 2008-05-31
**THANK YOU** to kwalkerk for writing this HOWTO.  It worked perfectly for me and Hardy's kernel is a lot better than Gutsy's in two ways, at least for my setup:
[LIST] 
[*]Hibernate actually works (with a little tweaking around NVidia card setup - first two tips from [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend) - note that these tips work with the open-source 'nv' driver too)
[*]a USB card reader (Enlight 26 in 1) no longer causes intermittent freezes with an 'irq 16 - nobody cared' message from kernel - I've tried a lot of workarounds for this with 2.6.22 but the Hardy 2.6.24 kernel seems to have finally fixed this.
[/LIST]
Once that was sorted, I could finally install the NVidia binary driver.  I initially upgraded using the hardy.py script without doing this driver.  When I went back and did the manual equivalent (adding to sources.list.d and then aptitude install nvidia-glx-new), it appeared to work but I got an API/version mismatch on boot.  

I have now installed the NVidia binary driver using Envy, which worked flawlessly without hassles.  Although I generally recommend using APT for everything, in this case Envy worked really well - see [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) and download 'Envy Legacy' for Gutsy.  I found I had to do an 'aptitude hold' on envy and some other packages it was threatening to remove, after an initial run of the script.

Generally [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) is quite good, but it should really mention Envy more as a last resort.

I'm using the following system spec and really recommend this kernel upgrade and Envy for people with a similar setup, particularly a P35-based motherboard and NVidia card:
```

Gigabyte GA-P35-DS3R iP35 Socket 775 8 channel audio ATX Motherboard    
Intel Core 2 Duo E8200 Socket 775 (2.66GHz) FSB1333 6MB Cache 
NVidia 7900GS PCI Express 256 MB (XpertVision) with passive cooler 
Corsair 4GB Kit (2x2GB) DDR2 800MHz/PC2-6400 XMS2 Memory Non-ECC Unbuffered CL4(4-4-4-12)
Samsung HD753LJ 750GB Hard Drive SATAII 7200rpm 32MB Cache
Samsung SP2514N 250GB Hard Drive PATA 7200rpm
Pioneer DVR-106D DVD writer (PATA)
Enlight Black 26-in-1 Internal 3.5" Card Reader
```

UPDATE: Unfortunately the 2.6.24 update did not actually fix the freeze problem (IRQ "nobody cared" issue) - however, booting with "all_generic_ide irqpoll" does fix this (probably just the latter is enough), and performance is fine including with NVidia binary driver for 3D gaming, so I'm going to just leave irqpoll enabled.

---

### Post by Cato2 on 2008-05-31
@simoncullen: I had to upgrade libc6 to 2.7-10ubuntu3 as part of the kernel upgrade process.  I've just run Envy and not had any problems as a result.  So maybe you should re-run the kernel upgrade process using hardy.py and check that libc6 is upgraded - if not, try using the manual process to see what's happening in more detail.

---

### Post by simoncullen on 2008-05-31
Thanks BC7333 and Cato2!

It was indeed the c libraries not matching the kernel!  

Cheers!

> **Cato2 said:**
> @simoncullen: I had to upgrade libc6 to 2.7-10ubuntu3 as part of the kernel upgrade process.  I've just run Envy and not had any problems as a result.  So maybe you should re-run the kernel upgrade process using hardy.py and check that libc6 is upgraded - if not, try using the manual process to see what's happening in more detail.

---

### Post by Cato2 on 2008-06-06
Good that it's working for you now! 

See my earlier post at [http://ubuntuforums.org/showpost.php?p=5083979&postcount=594](http://ubuntuforums.org/showpost.php?p=5083979&postcount=594) for an update on the nobody-cared freeze problem.  Basically, 2.6.24 doesn't fix the issue but irqpoll seems to fix it without performance problems.

---

### Post by rated_emman on 2008-06-11
HI GUYS! i tried to make my Wireless NETWORK to be working.. but when i go the first step, i go to the terminal and type it... and a window opens, require my password, and show this thing:

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:16:d3:f2:1c:d0", ATTR{type}=="1", NAME="eth0"

# PCI device 0x14e4:0x4311 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:00:1a:73:cf", ATTR{type}=="1", NAME="eth1"
```

what am i suppose to remove?? and on the step 4, what do i replace the "00:00:00:00:00:00" with? how will i know that?
im soo sorry guys. im soo new to this stuff.. 

thank you guys in advance :D
here's the specs if this will help:

```
emmanuel@emmanuel-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:f2:1c:d0  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fef2:1cd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4950677 (4.7 MB)  TX bytes:369048 (360.3 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9228 (9.0 KB)  TX bytes:9228 (9.0 KB  
```

```
 emmanuel@emmanuel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

emmanuel@emmanuel-laptop:~$  
```

```
emmanuel@emmanuel-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
emmanuel@emmanuel-laptop:~$  
```

```
emman@emmanuel-laptop:~$ sudo lshw -C network
[sudo] password for emman: 
PCI (sysfs)
```

then i installed the "b43-fwcutter" with:

```
sudo apt-get install b43-fwcutter
```

then i try to follow the instruction in here... :( and i can't get it figured out :(

this is like my 8th day working with linux so i desperately need your help plzz...


thank you guys soo much in advance!

---

### Post by earther on 2008-06-21
> **lemurian said:**
> Try adding the rules I'm attaching to this message to /etc/udev/rules.d/  (You must gunzip the file before installing it.)

I created this file by taking the old rules file bundled with libsane and modifying the syntax to the new specs.
Kudos to you for sorting this out.  Xsane is now able to access my old HP ScanJet 3300C as user.  I am sooo happy!!!

I would have thanked you but the 'Thanks' icon was missing from that post.  ;)

---

### Post by earther on 2008-06-23
I'm confused . . .

Once I figured out the Xsane glitch, I though I'd run the script to update to the latest kernel but it didn't change anything:

> Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux is already the newest version.
linux-generic is already the newest version.
linux-headers-generic is already the newest version.
linux-image-generic is already the newest version.
linux-restricted-modules-generic is already the newest version.
nvidia-glx-new is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 913 not upgraded.

Is 2.6.24-16-generic the latest kernel available?  On my Hardy test install there are 2.6.24-18-generic and 2.6.24-19-generic kernels and headers etc. available for download.  Why didn't the script install them?

---

### Post by Cato2 on 2008-06-24
Did you do an apt-get update before trying the upgrade?  You need to do this, with hardy repository enabled: ```
aptitude update && aptitude safe-upgrade
```

---

### Post by earther on 2008-06-24
> **Cato2 said:**
> Did you do an apt-get update before trying the upgrade?  You need to do this, with hardy repository enabled: ```
aptitude update && aptitude safe-upgrade
```
I used the hardy.py script as I did the last time.  There is an apt-get update in there and it went through the process - I was keeping an eye on it.

The reason I'm wanting to update is that since getting the scanner to work, I am occasionally having a little glitch with my GeForce 8400 GS after hibernation.  There is an annoying flicker mid-screen and the desktop doesn't load quite properly in the window.  This may be Compiz related because this appeared in the logs just before the post-hibernation flicker appeared:

```
Jun 23 19:07:49 localhost kernel: [   68.757991] compiz.real[6171]: segfault at 006e6962 eip 08054bd0 esp bfff6110 error 4
```

It wasn't happening before the scanner upgrades (usb and libsane fixes both posted in this thread).

Any more thoughts?

PS.  FWIW, I just spend several days reading this entire thread!

---

### Post by earther on 2008-06-27
Interestingly, this little problem seems to have settled down.  In the past few days it's only happened once after I was doing a lot of cube rotating.  I'm pretty sure it's Compiz related.  I found a nice little script to disable/enable Compiz if it ever becomes troublesome again.

---

### Post by PCZahra on 2008-07-11
I need the internet so I can download this kernel so I can get the internet. Any idea how I can save all neccesary packages to disk so I can transfer through a memory card?

---

### Post by DJ_Peng on 2008-09-25
@walkerk:
With Intrepid being less than month away, is there any idea when we'll see a thread for adding the Intrepid kernel to Hardy? I know there are some issues with the Intrepid kernel (especially the Nvidia driver) but I'm wondering if I should look forward to a new thread or if I should just get ready to start testing Intrepid itself once it hits beta.

---

### Post by vlad1234 on 2008-12-14
I've upgraded kernel to 2.6.24 as described. Everything went smoothly. Since I have encrypted root, I'also upgraded to hardy cryptsetup and dmcrypt as recommended in this link:

> Encrypted Hard drives
> If you are going to be booting from an encrypted hard drive see the link below:
> [http://ubuntuforums.org/showpost.php...&postcount=456](http://ubuntuforums.org/showpost.php...&postcount=456)

After reboot I got message:

[FONT="Courier New"]cryptsetup: Source device /dev/disk/by-uuid/00fe9e93-9611-... not found[/FONT]

I modified /etc/crypttab replacing /dev/disk/by-uuid by /dev/sda2 - the original location, run update-initframes and rebooted. This time I got message

[FONT="Courier New"]cryptsetup: Source device /dev/sda2 not found[/FONT]

So now I am stuck. Please help.

---

### Post by rebegin on 2009-01-28
hello,
it seems that there's not much life around but if anyone else would be interested in:
i can confirm that this method works great from intrepid to jaunty's kernel and nvidia driver :)
all the best.

---

### Post by Sulomania on 2009-11-11
Hi! I am using Toshiba Sattelite Pro A200 1BP Laptop. Dual core cpu, Nvidia 7300 etc... 
I couldn't get my nvidia driver work, cuz I think the drivers are for kernel 2.6.24. Thus I planned to upgrade my kernel and I ended up in this forum.
I have updated my ubuntu 7.10 and now I have kernel: 2.6.22-14-generic. I tried the script, everything went well. I rebooted but the kernel didn't change. Here is the result:

```
suleyman@suleyman-laptop:~$ uname -r
2.6.22-14-generic
```

I tried manual upgrade and the weird part comes as:

```
suleyman@suleyman-laptop:~$ sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux is already the newest version.
linux-generic is already the newest version.
linux-headers-generic is already the newest version.
linux-image-generic is already the newest version.
linux-restricted-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Any idea about how to solve it? I have been fighting with ubuntu for more than a week. It started to piss me off :/

---

### Post by jw5801 on 2009-11-11
> **Sulomania said:**
> Hi! I am using Toshiba Sattelite Pro A200 1BP Laptop. Dual core cpu, Nvidia 7300 etc... 
I couldn't get my nvidia driver work, cuz I think the drivers are for kernel 2.6.24. Thus I planned to upgrade my kernel and I ended up in this forum.
I have updated my ubuntu 7.10 and now I have kernel: 2.6.22-14-generic. I tried the script, everything went well. I rebooted but the kernel didn't change. Here is the result:

```
suleyman@suleyman-laptop:~$ uname -r
2.6.22-14-generic
```

I tried manual upgrade and the weird part comes as:

```
suleyman@suleyman-laptop:~$ sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux is already the newest version.
linux-generic is already the newest version.
linux-headers-generic is already the newest version.
linux-image-generic is already the newest version.
linux-restricted-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Any idea about how to solve it? I have been fighting with ubuntu for more than a week. It started to piss me off :/

Seriously, Hardy is the current LTS (long term support) release, you should at the very least do a complete upgrade to that, not just attempt to upgrade the kernel. Security updates and backports for Gutsy stopped when it reached end of life back in April.

Follow the upgrade notes here: [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

