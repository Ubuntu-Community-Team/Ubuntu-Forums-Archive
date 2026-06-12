---
title: "USB stick suggestion for installing a full Ubuntu in it"
date: 2020-08-30
forum: New to Ubuntu
---

### Post by j2ee on 2020-08-30
I heard Sandisk extreme pro is the best but it is too expensive. Any cheaper suggestion? Thanks.

---

### Post by sudodus on 2020-08-30
You can find tips and further links via this link: [Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick/pre)

Today a good choice can be a SSD drive (with/for an internal SATA connection) + an external USB to SATA box or adapter. It can give better performance to a lower cost compared to an advanced USB pendrive. (But it is not as convenient.)

---

### Post by j2ee on 2020-08-30
I am thinking to buy Sandisk "Extreme Go" 64GB with around local price $15.5 USD. Any good experience with it?

---

### Post by SeijiSensei on 2020-08-30
I've used all sorts of USB sticks to install Ubuntu.  Never had a problem with any of them.  The smallest I use is about 3.5 GB and probably ten years old.

Just bought three [ADATA 32 GB]("https://www.newegg.com/adata-model-auv128-32g-rbe-32gb/p/N82E16820211762") sticks for $6 each at NewEgg.  The 64 GB versions cost $9.

---

### Post by j2ee on 2020-08-30
> **SeijiSensei said:**
> I've used all sorts of USB sticks to install Ubuntu.  Never had a problem with any of them.  The smallest is about 3.5 GB.

Just bought three [ADATA 32 GB]("https://www.newegg.com/adata-model-auv128-32g-rbe-32gb/p/N82E16820211762") sticks for $6 each at NewEgg.  The 64 GB versions cost $9.

Which usb stick is good in your option? I can play like $20 USD for 64GB and this size is good enough for me.

Anyone tried Samsung USB 3.1 Flash Drive BAR Plus? Its price is similar as "Extreme Go"

---

### Post by sudodus on 2020-08-30
Most USB pendrives work well when new and when used as normal storage devices. But when you plan to use it as a system drive for an installed system, there are higher demands.

- After repeated write operations the memory cells fail. Most USB pendrives can stand far less write cycles compared to an SSD (and high quality pendrives that have similar memory hardware as SSDs).

- But long before the drive fails, it will get slow. There is a wear levelling system, that helps avoid failure because some particular memory locations get written to repeatedly.

- A USB pendrive that is getting slow, say below half of the original write speed, can be zeroised, [the whole drive overwritten with zeros](https://help.ubuntu.com/community/mkusb/wipe), and restored to almost the original speed.

- An installed system tends to write a lot to some particular locations. This can be avoided with the mount option noatime. There are also other things that can be avoided in order to reduce the wear of the memory cells. See how you can tweak an installed Ubuntu system in a USB pendrive at [this link](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks).

- A persistent live system is not writing as much as an installed system, so it can be a good alternative in a USB pendrive, but there are several other advantages with an installed system, for example stability and ability to get updated and upgraded just like any installed system in an internal drive. (You can install application programs and save data in a persistent live system, but not update and upgrade the linux kernel and the kernel drivers.)

---

### Post by j2ee on 2020-08-30
Extreme Pro should use MLC and I guess Extreme Go  uses TLC which should be resonable durable. Both have life long warranty anyway so if it is dead after like 10 years then just exchange a new one.

---

### Post by C.S.Cameron on 2020-08-30
I find lots of RAM more important than the USB stick. I understand that Ubuntu runs mainly in RAM once it gets going. My 15GB USB2 Fit seems just as fast as my 32GB USB3 Fit as long as I keep the number of running tasks reasonable. Booting and Saving data may take a little longer though.

---

### Post by mastablasta on 2020-08-31
i got a bunch of Sandisk, Kingston and Sony are good options (5 year warranty on them). the USB 3.0  version work good and reliable. i bough a bunch of them on sale for 5 EUR (the 32Gb version).

Kingston is used for server and has been running non stop now for quite some time (3 or 4 years). might be time to image it :)

EDIT1: Traveler or similar version are more robust. often resistant to water and dust. smaller that go on key chain cost a bit more. but they are often a  bit more reliable.

if i wanted to do something more on the system with a lot of writes and rewrites i would go for portable 512 GB SSD (or at least 256GB). they are small (Sandisk) and have water and dust protection. thy cost 80 EUR here and i guess they likely last longer than USB and are faster. i was thinking about getting one for games that my kid plays on laptop. but maybe will just add another internal SSD later when laptop warranty expires. i plan an upgrade (RAM and Disk next year).

edit2: for testing a system (or dual boot) i find virtualbox to be a better and more convenient option. i used to have about 8 linux distros installed on windows. various testing and learning servers and 2 desktops. no USB switching and rebooting necessary. plus i could mess up the OS and have it restored to previous state in seconds. further more there are premade images available online that you can just load. no install needed.

---

### Post by j2ee on 2020-08-31
> **mastablasta said:**
> i got a bunch of Sandisk, Kingston and Sony are good options (5 year warranty on them). the USB 3.0  version work good and reliable. i bough a bunch of them on sale for 5 EUR (the 32Gb version).

Kingston is used for server and has been running non stop now for quite some time (3 or 4 years). might be time to image it :)

EDIT1: Traveler or similar version are more robust. often resistant to water and dust. smaller that go on key chain cost a bit more. but they are often a  bit more reliable.

if i wanted to do something more on the system with a lot of writes and rewrites i would go for portable 512 GB SSD (or at least 256GB). they are small (Sandisk) and have water and dust protection. thy cost 80 EUR here and i guess they likely last longer than USB and are faster. i was thinking about getting one for games that my kid plays on laptop. but maybe will just add another internal SSD later when laptop warranty expires. i plan an upgrade (RAM and Disk next year).

edit2: for testing a system (or dual boot) i find virtualbox to be a better and more convenient option. i used to have about 8 linux distros installed on windows. various testing and learning servers and 2 desktops. no USB switching and rebooting necessary. plus i could mess up the OS and have it restored to previous state in seconds. further more there are premade images available online that you can just load. no install needed.

Thx for sharing. Virtualbox has some security issue especially Windows is the host.

---

### Post by mastablasta on 2020-08-31
everything has security issues. it's all about timely patches. ;)

---

### Post by j2ee on 2020-08-31
> **mastablasta said:**
> everything has security issues. it's all about timely patches. ;)

Virus in Windows cannot be patched, let's say there is a keylogger trojan in Windows host then it would capture anything typed in the Virtualbox that runs Linux.

---

### Post by mastablasta on 2020-09-01
> **j2ee said:**
> Virus in Windows cannot be patched, let's say there is a keylogger trojan in Windows host then it would capture anything typed in the Virtualbox that runs Linux.

if you have a trojan on host (or worse a rootkit in BIOS) then you have other problems than running linux in virtualbox would potentially create.

keeping windows up to date and running various security software should reduce the possibility of host infection. running OS in virtualbox will keep with "boxed", so you can actually infect it and the host should be safe (unless you infect it with something that uses new vbox vulnerability and that could skip to host OS).

---

### Post by j2ee on 2020-09-05
I compare benchmark of Extreme Go and Ultra 3.0 from Sandisk and those are just similar

---

