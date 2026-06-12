---
title: "help in installing linux on 7&quot; mini laptop"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by jithh on 2012-02-13
i bought a new 7" mini laptop from market.
brand named 'sonilex' , whatever the brand is, its a china made.

model : sonilex SL-LT701
CPU: WMT, ARM-WM8650, 600Mhz
Kernel version: 1.05
OS : windows CE 6.0
RAM: 256MB DDR3
WIFI: 802.11b/g

there is NO BIOS
it has only a flash drive.
windows CE 6.0 has been installed in flash drive only...

i wanted this smartbook to be installed with linux
i suppose there is few linux that can run under 256MB ram,
but i don't know how to install/flash this device to run a linux

can anyone help me out ?  :roll:

---

### Post by Lars Noodén on 2012-02-13
Nice machine.  That looks like it is using a mobile processor, [ARM](https://wiki.ubuntu.com/ARM), instead of the (outdated) x86 architecture.   I've never install on ARM.  All I can say is that the installation will be different.  There seems to be an IRC channel for ARM but no mailing list or forum/subforum:
[https://wiki.ubuntu.com/ARMTeam](https://wiki.ubuntu.com/ARMTeam)

Can you use IRC?

You might also look into Debian.  It is supported on a very wide range of architectures.

---

### Post by jithh on 2012-02-13
ok... in case of debian, how do i make it done ?
direct me clearly please...

---

### Post by Lars Noodén on 2012-02-13
I'd start with the Debian ARM mailing list:

[http://www.debian.org/ports/arm/](http://www.debian.org/ports/arm/)

You should be able to find people who can provide information about the next steps to take towards installation.

---

### Post by jithh on 2012-02-13
thanks for the link.
found many info and got documents regarding installation in ARM
but its a very big tutorial....

lemme try it..

if any steps found, that directs in installing, please lemme know....

---

### Post by jithh on 2012-02-15
i went through many blogs, forums and websites regarding this,
the only thing i repeatedly came across was, "u-boot" 
universal boot loader is being the first step to start...

but still i couldn't figure out how to install "u-boot" in my smartBook,
anyhow, lets leave that aside now...

my doubt is, why should not we install "u-boot" in a SD-card/pendrive 
make SD-card/pendrive into two or more partitions for swap and ext3 to install linux
and install a linux(that works on 256MB ram, ARM 600Mhz processor) in ext3 partition.

then try to boot with the SD-card/pendrive in my smartBook! in such case, will it work ? will it boot linux ?

any suggestions/direction please.... :confused:

---

### Post by Lars Noodén on 2012-02-15
The mention of U-boot jogs my memory.  Now I remember that I used to have an Openmoko (ARM) which used U-boot.

[http://wiki.openmoko.org/wiki/U-boot](http://wiki.openmoko.org/wiki/U-boot)

Unfortunately, I think the instructions may be very device-specific.

Did you try the mailing lists or IRC?  What about Debian resources?

---

### Post by sadaruwan12 on 2012-02-15
You can create a bootable with persistent where you can use as a small PC environment. But with your system I don't know if you'll be able to switch the first boot device but normally I think ARM have a small BIOS.

If you want to make a persistent USB I'm listing some links hope they'll help you.

[Link 1]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")

[Link 2]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

---

### Post by jithh on 2012-02-16
> **Lars Noodén said:**
> The mention of U-boot jogs my memory.  Now I remember that I used to have an Openmoko (ARM) which used U-boot.

[http://wiki.openmoko.org/wiki/U-boot](http://wiki.openmoko.org/wiki/U-boot)

Unfortunately, I think the instructions may be very device-specific.

Did you try the mailing lists or IRC?  What about Debian resources?

i couldn't find out clearly in mailing-list archives :(

am reading out debian documents for ARM :confused:

---

