---
title: "Newbie needs help with wireless network"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by zizzerboy on 2008-10-02
Hi,

I just installed ubuntu a couple of weeks ago, and I've been having trouble connecting to our (windows) wireless network. 

What makes me frustrated is that I was able to connect to it when I first installed ubuntu, and it worked for a couple of days. Then one time when I booted up, it said it was 'searching for wireless network key' and then it wouldn't connect.

I tried deleting the connection and setting up a new one, but it did the same thing. I know that I'm putting in the right password. Can you help me out?

---

### Post by shifty_powers on 2008-10-02
hi, do you know what wireless card you are using?

---

### Post by zizzerboy on 2008-10-02
yes, I'm using an intel 3945 mini-card

---

### Post by shifty_powers on 2008-10-02
what is the output of

```
sudo iwlist scan
```

?

---

### Post by zizzerboy on 2008-10-02
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:92:BF:82:05
                    ESSID:"Deraney"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-30 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1B:2F:07:2F:C8
                    ESSID:"OSCAR IDLEWOOD1"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-55 dBm  Noise level:-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:07:2F:C8
                    ESSID:"OSCAR IDLEWOOD1"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/100  Signal level=-82 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000016f21f19181
```

Oscar Idlewood1 is the name of my network

---

### Post by shifty_powers on 2008-10-02
well i'm no expert, but you might want to try wicd, an alternative to gnome network manager. it may well better connect to the network. helped me when knetwork manager simply would not work :D

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

(look at teh first instructions for ubuntu)

---

### Post by shifty_powers on 2008-10-02
just noticed, you have eth1 and wlan0 showing wireless networks...

do you have more than one wireless card?

could you post the out put of

```
lsusb && lscpi
```

?

---

### Post by zizzerboy on 2008-10-02
```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c526 Logitech, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05ca:18a1 Ricoh Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
bash: lscpi: command not found

```

I installed wcid. It still didn't connect, it just said 'obtaining ip address'

---

### Post by shifty_powers on 2008-10-02
bugger sorry should have been

```
lspci
```

---

### Post by zizzerboy on 2008-10-02
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0d:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

---

### Post by shifty_powers on 2008-10-02
> 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0d:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

as i thought, you actually have two wireless cards in your system. are you using a laptop or desktop?

either way, having two is not going to make your life easy...

you really need to use on or the other.

---

### Post by zizzerboy on 2008-10-02
I didn't know I had 2! I definitely  want to use the intel 3945. Should I just manually remove it, or is there some way to uninstall the broadcom?

---

### Post by shifty_powers on 2008-10-02
well are you using a laptop or a desktop?

---

### Post by zizzerboy on 2008-10-02
sorry, I forgot to mention that I am on a laptop. (Dell Studio 15)

---

### Post by shifty_powers on 2008-10-02
hmm ok.. well you aren't using a usb wlan stick are you?

you should be able to blacklist the broadcom driver, let me get back to you...

---

### Post by zizzerboy on 2008-10-02
no it's an internal card...

---

### Post by shifty_powers on 2008-10-02
well ok

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

reboot and then post output of

```
lspci
```

...

---

### Post by zizzerboy on 2008-10-02
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0d:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

---

### Post by shifty_powers on 2008-10-02
what is the output of

```
sudo iwlist scan
```

edit: you know, it is soooo much easier when you are in front of the pc in question. bear with me :D

---

### Post by zizzerboy on 2008-10-02
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:92:BF:82:05
                    ESSID:"Deraney"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-91 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:18:3F:20:BC:D1
                    ESSID:"2WIRE265"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-93 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1B:2F:07:2F:C8
                    ESSID:"OSCAR IDLEWOOD1"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-38 dBm  Noise level:-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

---

### Post by shifty_powers on 2008-10-02
have you been able to connect to your network?

---

### Post by zizzerboy on 2008-10-02
nope. still gets stuck on 'obtaining ip address' :(

---

### Post by shifty_powers on 2008-10-02
ok, a little digging on my part reveals that the bcm43xx driver has been replaced, soz about that.

so

```
modprobe -r b43
```

```
modprobe -r b44
```

```
echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
```

```
echo 'blacklist b44' | sudo tee -a /etc/modprobe.d/blacklist
```

then reboot and output of

```
sudo iwlist scan
```

---

### Post by zizzerboy on 2008-10-02
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:92:BF:82:05
                    ESSID:"Deraney"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-93 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1B:2F:07:2F:C8
                    ESSID:"OSCAR IDLEWOOD1"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-24 dBm  Noise level:-24 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

```

---

### Post by shifty_powers on 2008-10-02
is it connecting?

you are now, hopefully, only using the one wirless card...

---

### Post by zizzerboy on 2008-10-02
still not working. and apearantly still has 2 wireless cards. I have to go now, thanks for all your time, shify-powers, I really appreciate it....

---

### Post by shifty_powers on 2008-10-02
np's i hope you get it sorted.

really kind of stumped over the two cards, especially in a laptop.

very strange...

---

