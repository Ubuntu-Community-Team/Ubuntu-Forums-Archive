---
title: "Recompiling my Kernel."
date: 2004-11-01
forum: Packaging and Compiling Programs
---

### Post by kmf on 2004-11-01
Thanks to the Ubuntu Team.

I installed Ubuntu and very happy to everything working out of the box (tm).
One thing bugs me though if I'm gonna recompile my kernel.
Will I loose all the nice Firmware Stuff for my Wireless Card ?

The reason I'm asking is I want to patch my orinoco card for Monitor mode (for Kismet)
and I'm not sure if I recompile my kernel whether I still would have all the firmware stuff.

Any Ideas 
Karl

---

### Post by ynef on 2004-11-01
I may be behind on the vocabulary or something, but are you sure **firmware** is what you mean?

> *A google search for "define: firmware" came out of the closet to say:*
**Software that is embedded in a hardware device that allows reading and executing the software, but does not allow modification, e.g., writing or deleting data by an end user. (188 )  Note 1: An example of firmware is a computer program in a read-only memory (ROM) integrated circuit chip.  A hardware configuration is usually used to represent the software.  Note 2: Another example of firmware is a program embedded in an erasable programmable read-only memory (EPROM) chip, which program may be modified by special external hardware, but not by an application program. **

---

### Post by kmf on 2004-11-01
Well hmm
I see what you mean , I could word it perhaps like this would the non-free components in the current vanilla kernel of Ubuntu be in the source of the new kernel ...

hmm this sound stupid ...

oh well.
Trail and Error
I guess.

Karl :)

---

### Post by kmf on 2004-11-01
But I don't know if there could be non-free comps. ,because I can just reinstall the Nvidia Driver ...

---

### Post by Borgmeister on 2004-11-01
You got kismet working, in ubuntu, it says no suitable c compiler found, in Yoper, it cannot define class 'friend'. monitor mode is the last of my worries, but the wg511 from netger works, as i have used it with auditor

---

### Post by kmf on 2004-11-01
I'm trying to get monitor mode working with orinoco silver card, kismet was the least of my worries it was just a "apt-get install kismet" away :)

Karl

---

### Post by kmf on 2004-11-03
well this is what I was fearing ...
When I jacked in my SMC 2835W it said firmware not found ...

Any ideas for me to get the firmware in there ?

Karl

---

### Post by az on 2004-11-03
If you compile the same kernel using the same config file, you should have the same binary.

Get the kernel source.  Copy the config-2.6.8-wahtever file you have in /boot to your kernel source tree (call it .config)
Apply your patch and make menuconfig (or whatever, to enable your patch, if needed)
and then compile away.  I would use kernel-package, to make a kernel.

Your old kernel will stil be there, so do not be afraid...

Also, what driver does your SMC card need?

Have you tried ndiswrapper?

Another also.  Does the hostap driver support monitor mode?  Does it work with the orinoco chipset?

---

### Post by kmf on 2004-11-03
No my Orinoco work's fine after I patched the Driver.
My SMC requires firmware which is currently located in /lib/hotplug/firmware/
Since my firmware, cannot be compiled I need to add is somehow for my card to work.

So I copied my orginal firmware file "isl3890" to /lib/hotplug/firware/.
And Ta-Da it worked then 
I checked summed my orginal file and the one that came with Ubuntu :)
The Checksum was the same.

And so it worked :)

Karl

---

### Post by Borgmeister on 2004-11-03
erm, am i doing something wrong, if i apt get install kismet, it says it cannot find the package. Im thining probably my sources list is no good, if it is, can you suggest a good list, and possibly post it below?

---

### Post by kmf on 2004-11-04
I got mine from the Universe list :)

It's bound to be there 

Karl

---

### Post by macpilot on 2004-12-30
[QUOTE=kmf]I got mine from the Universe list :)

It's bound to be there 

Karl[/QUOTE]
 could you post the howto install the patch, I've previously done it in Fedora Core 3, but somehow I feel lost in Ubuntu.

Thanks,

Jose

---

### Post by Ciaran m on 2005-02-02
I would love to see how to apply the patch as well

---

### Post by kmf on 2005-02-02
On doing the Orinoco thing ?
i downloaded the latest drivers from here : [http://www.ozlabs.org/people/dgibson/dldwd/orinoco-0.15rc2.tar.gz](http://www.ozlabs.org/people/dgibson/dldwd/orinoco-0.15rc2.tar.gz)
Compiled it and tada ....
make , make install.
make sure the Kernel Headers are installed.
monitor mode works by default in the new Drivers

Karl

---

### Post by Ciaran m on 2005-02-02
Thanks for the reply
I'm very new to linux and commands, just to confirm that i do the right thing.
I download the file from the link.
open command thingy
cd /  to the file i downloaded
type "make" return
type "make install" return

Is that it then?

---

### Post by kmf on 2005-02-02
Hmm then insert the card ,
type dmesg 
You should see something like this ....
orinoco 0.15rc2STA (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
orinoco_cs 0.15rc2STA (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
eth1: Hardware identity 0001:0001:0004:0002
eth1: Station identity  001f:0001:0007:0034
eth1: Firmware determined as Lucent/Agere 7.52
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:02:2D:42:7F:14
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
eth1: New link status: Connected (0001)
eth1: no IPv6 routers present


Karl

---

