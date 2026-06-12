---
title: "Ubuntu 11.04 wifi fails on MacOS X 10.8.1"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by polarbearcold on 2012-09-17
Hi.  I'm totally new so if I'm posting wrong, feel free to correct me.
I have a MacBookPro with 10.8.1 (Mountain Lion) installed.
I installed VMware Fusion 4.1.3 in order to install Ubuntu as multiple virtual machines.

I installed Ubuntu 10.04 and when enabling the network adapter, I switched the default from Share the MAc's network connection (NAT) to Connect directly to the physical network (Bridged).  Ubuntu was able to configure the network with DHCP.

When I installed Ubuntu 11.04 as an additional VM, I attempted to enable the network adapter in the same fashion, ie. Bridged, but Ubuntu fails to configure the network with DHCP reporting this generic error: Network autoconfiguration failed.  Your network is probably not using the DHCP protocol.  Alternatively, the DHCP server may be slow or some network hardware is not working properly.  

I have collected this info as observed in another thread assuming that it might be helpful.

test@ubuntu:~$ cat /etc/issue
Ubuntu 11.04 \n \l
test@ubuntu:~$ sudo lspci -vnn | grep -a4 -i net
[sudo] password for test: 
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at 2080 [size=32]
    Kernel driver in use: uhci_hcd

02:01.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
    Subsystem: VMware PRO/1000 MT Single Port Adapter [15ad:0750]
    Physical Slot: 33
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    Memory at c9020000 (64-bit, non-prefetchable) [size=128K]
test@ubuntu:~$ sudo lsmod
Module                  Size  Used by
vmhgfs                 67112  0 
vsock                  47686  0 
vmci                   77740  2 vmhgfs,vsock
acpiphp                24097  0 
vesafb                 13761  1 
snd_ens1371            25634  0 
gameport               19652  1 snd_ens1371
snd_rawmidi            30486  1 snd_ens1371
snd_seq_device         14462  1 snd_rawmidi
snd_ac97_codec        134270  1 snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  2 snd_ens1371,snd_ac97_codec
btusb                  18600  0 
ppdev                  17113  0 
snd_timer              29602  1 snd_pcm
psmouse                73535  0 
bluetooth              72448  1 btusb
vmw_balloon            12841  0 
joydev                 17606  0 
serio_raw              13166  0 
snd                    67382  6 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer
soundcore              12680  1 snd
snd_page_alloc         18529  1 snd_pcm
parport_pc             36959  1 
i2c_piix4              13303  0 
lp                     17825  0 
shpchp                 37297  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
mptspi                 22738  2 
mptscsih               44457  1 mptspi
floppy                 74120  0 
e1000                 111862  0 
mptbase               102904  2 mptspi,mptscsih
scsi_transport_spi     30630  1 mptspi

---

### Post by heyandy889 on 2012-09-17
Hello. Welcome to the forums!

I've never used vmware, only Virtual Box. I remember having some trouble with "bridged" network, or the default . . . I don't really remember. I think I resolved the issue with Google searches (I was trying to get Chromium OS running at the time). 

The Mac has Internet, but Ubuntu in the virtual machine does not?

What happens when you plug into the Internet with a cable? I assume that the Mac will recognize the wired connection; maybe Ubuntu and vmware will detect the wired connection?

---

### Post by polarbearcold on 2012-09-17
Ubuntu 11.04 configures the network via DHCP when the USB Ethernet is attached and the Wi-fi is disabled.  My coworker is able to configure Ubuntu 11.04 with VMware Fusion using an older version of MacOS X.  I will investigate further in that direction.  This is a brand new MacBook Pro.

Thank you for the help.

---

