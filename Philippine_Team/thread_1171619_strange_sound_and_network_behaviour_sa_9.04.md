---
title: "strange sound and network behaviour sa 9.04"
date: 2009-05-27
forum: Philippine Team
---

### Post by Script Warlock on 2009-05-27
its my 50th logins sa U9.04 at 50th instances of strange behaviour and quite sure na eto yung pabalibalik na mangayari sa sound at network.

hardwares:
2 nic cards
a pair of altec lansing desktop spkrs
a desktop pc na ginawang server
16port switch

1st start-up seq:

1. UPS up
2. pc up
3. login
4. sound works
5. 16port switch up

2nd start-up seq:

1. UPS up
2. 16port switch up
3. pc up
4. login
5. no sound

now if i'm going to disable/enable the network icon surely putol na inet connection ko for atleast 30mins. of course unlike sa 8.04 
auto lo
iface lo inet loopback 
lang ang makikita mo kahit na nakaset na sa ics. just wondering why:(

any ideas?

---

### Post by loell on 2009-05-27
what are the models of the sound cards and the built in lan devices?

are these allsmoothly working in 8.04 and 8.10?

---

### Post by Script Warlock on 2009-05-27
sorry i forgot to include the machines specs:

P4 dual core 3.0Ghz
pc667 2gig
sony cdrom
generic floppy
80gig western digital hdd - primary
500gig western digital hdd
built-in sound/lan/video(disabled)
250mb palit nvidia vcard

Audio - via vt1708
lan - eth0 vt6102 rhine 2
      eth1 3com corp. 3c905 (boomerang)
vga - nvidia gforce 8400GS
motherboard - via cn896/vn896/p4m900

ya mas stable ang 8.04LTS 
8.10- audio fine lan- rough

---

### Post by loell on 2009-05-28
the **via vt1708** not functioning sometimes, is probably a bug with pulseaudio. ALSA might be more stable with this audio controller.

can you post the specific lan set device?

```
lspci | grep net
```

---

### Post by Script Warlock on 2009-05-28
> **loell said:**
> the **via vt1708** not functioning sometimes, is probably a bug with pulseaudio. ALSA might be more stable with this audio controller.

can you post the specific lan set device?

```
lspci | grep net
```

pusoicafe@Ubuntu-Server:~$ lspci | grep net
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
04:04.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]

---

### Post by loell on 2009-05-28
if you searched for **VT6102**, seems the card has been problematic?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/48263](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/48263)

[this post suggest to disbale the irq]("http://ubuntuforums.org/showpost.php?p=4563839&postcount=5")

but you don't have trouble using this lan card in 8.04 right?

---

### Post by Script Warlock on 2009-05-28
yah right binasa ko link so try ko to mamya closing sa shop
tapos ang audio tanggalin ko na lang kaya ang pulseaudio pero wala mga apps na nangangailangan ng pulseaudio?

very stable ang machine sa 8.04LTS

---

### Post by Nhatz on 2009-05-28
Yeah kaya Hardy (8.04) parin gamit ko sa box ko. teka ano ba Ip mo DHCP or Static?

ASTIG!!! :guitar:

---

### Post by Script Warlock on 2009-05-28
dhcp

---

### Post by loell on 2009-05-28
try mo din ang later kernels yung 2.6.30 baka ma-solve yung lan problems mo.

parang may ppa yata dun?

---

### Post by Script Warlock on 2009-05-28
tinanggal ko na lang pulseaduio
boot option acpi=noirq kailalngan ko type every boot saan to ialagay sa grub?
100% werks

tried the other way
installed kernel 2.6.30 - dba under dev pa to?
100% werks

saan dito ang safe solution...

---

### Post by loell on 2009-05-28
just append it in the kernel entry

```
kernel		/boot/vmlinuz-2.6.28-11-generic ...Some_Where_Here....
```

I think .30 won't make your sytem explode. :D

just observe on what's stable between the two methods.

---

### Post by Script Warlock on 2009-05-28
heheheh oo nga naman...cge ty for the help

---

### Post by kiminaiseah on 2009-05-29
same here
nag kaka problem kami sa mga inu-ubuntu na mga workstation with the motherboard Asus P5GC-MX, lan card problem naman.. na dedetect sya ang problema di nag pa-function.. installed ubuntu(8.04.2) and also tried ubuntu(9.04).. so far di ko na masyado trinoble shoot skit lang sa ulo... kaya debian nalang ininstail ko debian(sid)

---

### Post by Script Warlock on 2009-05-29
meron akong isang workstation na asus ang motherboard text based installer lang ginamit ko kc ayaw sa cdrom at usb works fine naman tagal lang magising ang inet connection sa board na to cguro 3-5mins. yoko na bumili ng asus mas ok sa akin ang intel board no glitches..

---

