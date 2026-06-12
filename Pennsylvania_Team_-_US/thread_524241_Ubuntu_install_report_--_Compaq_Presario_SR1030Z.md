---
title: "Ubuntu install report -- Compaq Presario SR1030Z"
date: 2007-08-12
forum: Pennsylvania Team - US
---

### Post by BraveSirRobin on 2007-08-12
Some of you should remember me as the guy from the BBQ with the unsupported SATA drive (had a great time. Thanks all for organizing, etc!).

I unfortunately must report that I'm still unable to install Linux on my computer, as my SATA drive (Samsung SP2504; [Broadcom SATA II](http://linuxmafia.com/faq/Hardware/sata.html#bcm5773) -- I'm not 100% sure about the Broadcom part) and network card ([Realtek RTL8139](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=354124)) still aren't recognized by the installer. ](*,)

I first booted up with the Ubuntu live CD which, after loading the kernel, told me:

> Int 14: CR2 f8000000 err 00000000 EIP c020c384 CS 00000060 flags 00010007 stack: [truncated, mostly zeros]

I then downloaded the amd64 Ubuntu alternate which, after loading the kernel, said:

> MP-BIOS bug: 8254 timer not connected to IO-APIC
ata1.00: failed to set xfermode (err_mask=0x40)
ata1.00: failed to set xfermode (err_mask=0x40)
[stuff about IRQs that scrolled by too fast to read]


Debian amd64 stable, and the latest Debian weekly, say:

> ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 130)
ata1.00: qc timeout (cmd 0xec)

several times before printing a bunch of stuff that I can't read because it scrolls too fast (I don't suppose there's a way to print a dmesg during an install...)

Both Ubuntu alternate and Debian continue with the install process but fail configuring DHCP (I haven't attempted to go any farther, assuming the filesystem step will fail after wiping out my Windows install).

Oh well, at least my drive is being acknowledged now, which looks like an improvement over the last time I attempted an install.

---

### Post by kejava on 2007-08-12
I just did a search for the SR1030Z and found some two year old posts ([here]("http://www.webservertalk.com/message1328172.html") and [here]("http://kerneltrap.org/node/6481")) that look almost identical to your issues.  Based on the [specifications]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&cc=us&dlc=en&os=228&product=1152518&lang=en") for your system, I would take the easy route and start bypassing hardware.  You have extra PCI slots so grab a 10/100 supported NIC for $10 at Best Buy.  You could try a different SATA controller or just use the extra IDE connectors to toss in a cheap, 10GB PATA (IDE) drive.

This will at least get you up and running so you can figure things out at your leisure.  Meaning, you may have to download patches and recompile kernel modules to get some of this hardware working.  That will require a running system first :-)

The only catch with using this extra hardware is that you may have to disable some of the existing "bad" stuff to prevent kernel crashes.  Doesn't seem like you're having that issue though, so we'll address that if/when it happens.  For now, just plug in a differnt NIC and a PATA drive and try again.  Let us know how far you get and we'll attempt to address the "bad" hardware once you're up and running.

---

### Post by jedijf on 2007-08-13
West Philly Welcome!!

Glad you came to the bbq and even more happy you went right home and started playing.

Before you purchase stuff, you may want to try this:

at boot prompt : linux noapic

and then see what happens with the install.

if it works, then we can add the command to the grub ; )

Good Luck !!

PS: if you want to test this LIVE first - enter the boot command: live noapic on the LIVE cd.
      <F6> for 'other' boot options

---

### Post by BraveSirRobin on 2007-08-14
> **kejava said:**
> I just did a search for the SR1030Z and found some two year old posts ([here]("http://www.webservertalk.com/message1328172.html") and [here]("http://kerneltrap.org/node/6481")) that look almost identical to your issues.

Yes they do. It's quite uncanny :)

Thanks for the responses. I tried the noapic option by hitting <F6> and adding "noapic" (sans quotes) at the end of the line, right before the "--" then hitting <enter>, and still got the apic message from the kernel. Not sure what's going on with that.

I also did a bit more research and found some references to being able to switch an unsupported SATA drive to IDE mode through the computer's BIOS. I didn't find anything that explicitly said that, but I did find an option to "disable on-chip SATA controller" or something like that, which I tried. I no longer got the xfermode message but, upon rebooting without the Ubuntu disk in the drive, I got a "no system disk" error and had to re-enable the on-chip SATA controller before I could boot Windoze again. Any ideas as to what that option actually does? I also tried switching off the "plug-and-play OS" option in BIOS, but my network card still didn't appear to be configured correctly afterwards (actually, that was disabled when I got the system disk error, so that may not necessarily have been caused by the SATA controller being disabled). Changing "plug-and-play OS" to "No" also seemed to get rid of the IRQ messages after the "xfermode" message -- not sure if that's good or bad.

Anyway, I'm going to wait until I have more time (maybe this weekend) before doing anything drastic. Any feedback/suggestions I get in the meantime are welcome.

---

### Post by jedijf on 2007-08-15
Try adding "nolapic" also, but you may want to check for a bios upgrade first.

Maybe you can get lucky and they upgraded the bios and it will work.

---

### Post by BraveSirRobin on 2007-08-16
> **jedijf said:**
> Try adding "nolapic" also, but you may want to check for a bios upgrade first.

Maybe you can get lucky and they upgraded the bios and it will work.

Great idea. There was a BIOS upgrade available, and it seems to have done the trick. I still get the APIC message (nolapic doesn't seem to have any effect, either), but the upgrade seems to have solved my hardware support problems. In fact, I'm posting this from my new Ubuntu install.

I decided to install off the live CD, just for the heck of it, even though I've tended to go with the expert install in the past on Debian. I must say I'm impressed with the ease and simplicity of the install. As long as their hardware is supported, no Windows user should ever complain about Ubuntu being to hard to install.

One issue I had with the install, however, was the wording in the partitioning step. I chose to keep my Windows installation and simply resize the partition, but I had trouble figuring out what it was that I was resizing. As it turns out, I was resizing the Windows partition which, in retrospect, makes sense. I chose, however, to act as if I was resizing the partition Ubuntu would be installed on and, as a result, now have a huge Windows partition and very small Ubuntu partition when I wanted it the other way around... I'll just run the install again and hopefully rectify the problem, but it would've been nice to get it right from the start.

I've also noticed that Ubuntu if fairly... uh... Windowsy? It boots straight into X/Gnome and even the software update tool is almost identical to the one in Windows. I suppose that's not a bad thing, though, if you're a former Windows user. Hopefully I can configure away some of the more annoying behavior.

Anyway, thanks a bunch for the suggestions. You may have won yourself an Ubuntu convert :)

---

### Post by jedijf on 2007-08-16
BraveSirRobin,

Great job, way to hang in there.  Many get frustrated and bail before they get to experience Ubuntu.  

Welcome to the team.

---

### Post by BraveSirRobin on 2007-08-16
Thanks!

I take back what I said about there not being any difference with apic. The noapic option now results in a bunch of messages about something being invalid (I remembered more of the message a few minutes ago. Sorry).

The second install run also seemed to have come up with a strange interpretation of the disk's partitions, offering to create a 17GB partition for Windows this time instead of 129GB, so I opted to wipe out Windows. Maybe I'll get a Windows install disk at some point and put it on VMWare (or re-image in HDD with Windows and start over).

---

