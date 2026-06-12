---
title: "network disabled after fresh install 8.04"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by lincoln32 on 2008-11-07
lost lan several weeks ago and decided to reload with home partion and after formay and fresh install still no lan duel boot vista 64 lan works 
took this screen shot how do I enable etho0?todd@todd-desktop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=yes module=r8169 multicast=yes port=twisted pair
todd@todd-desktop:~$ \

---

### Post by bobnutfield on 2008-11-07
Have you tried to enable it in System>Preferences>Network Configuration?  Does the NIC show up in the window there?  Also, you can type:

> sudo ifconfig

in a terminal to see if it is being seen by the system.

---

### Post by lincoln32 on 2008-11-07
enabled in network icon drop window and shows up in hardware testing but not in confiuration
todd@todd-desktop:~$ sudo ifconfig 
[sudo] password for todd: 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93400 (91.2 KB)  TX bytes:93400 (91.2 KB)

todd@todd-desktop:~$ 
Thanks for the help!!!!!

---

### Post by drakeman007 on 2008-11-07
> **lincoln32 said:**
> enabled in network icon drop window and shows up in hardware testing but not in confiuration
todd@todd-desktop:~$ sudo ifconfig 
[sudo] password for todd: 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93400 (91.2 KB)  TX bytes:93400 (91.2 KB)

todd@todd-desktop:~$ 
Thanks for the help!!!!!


You have you eth0 successfully installed?

---

### Post by lincoln32 on 2008-11-07
that is the problem I think duel boot vista ok and card works swith to Ubuntu and card not working correct hoe do i reinstall or configure or turn on? works with wifi usb i took of another pc but want lan as I have some large files i move to other pc's on network

---

### Post by bobnutfield on 2008-11-07
You may not have the modules installed for that NIC.  Open a terminal and type:

> sudo lsmod

Post the results

---

### Post by lincoln32 on 2008-11-07
What are we looking for?
todd@todd-desktop:~$ sudo lsmod
Module                  Size  Used by
af_packet              27272  0 
ipv6                  311720  14 
binfmt_misc            14860  1 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
acpi_cpufreq           10832  1 
cpufreq_ondemand       11152  1 
cpufreq_conservative    10632  0 
cpufreq_powersave       3200  0 
cpufreq_stats           8416  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       6180  0 
video                  23444  0 
output                  5632  1 video
dock                   12960  0 
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
arc4                    3456  0 
ecb                     5248  0 
blkcipher               9476  1 ecb
rt2500usb              26368  0 
rt2x00usb              14720  1 rt2500usb
rt2x00lib              25344  2 rt2500usb,rt2x00usb
rfkill                 10144  1 rt2x00lib
input_polldev           6928  1 rt2x00lib
crc_itu_t               3584  1 rt2x00lib
snd_hda_intel         440536  4 
mac80211              192532  2 rt2x00usb,rt2x00lib
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  2 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
cfg80211               17680  1 mac80211
usblp                  17664  0 
nvidia               8858052  34 
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
i2c_core               28544  1 nvidia
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
serio_raw               9092  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                46236  0 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               15312  0 
button                 10912  0 
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              30624  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
evdev                  14976  3 
iTCO_vendor_support     5764  1 iTCO_wdt
soundcore              10400  2 snd
pcspkr                  4992  0 
ext3                  149264  2 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  4 
ata_piix               24196  3 
pata_acpi               9856  0 
floppy                 69096  0 
ata_generic             9988  0 
uhci_hcd               29856  0 
ehci_hcd               41996  0 
libata                176432  3 ata_piix,pata_acpi,ata_generic
scsi_mod              178488  4 sg,sr_mod,sd_mod,libata
usbcore               170288  6 rt2500usb,rt2x00usb,usblp,uhci_hcd,ehci_hcd
r8169                  36868  0 
thermal                19744  0 
processor              41832  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 
todd@todd-desktop:~$

---

### Post by bobnutfield on 2008-11-07
> r8169 36868 0 

I was looking for this.  This is probably the module for your NIC.  Also type in a terminal:

> lshal | grep net.interface

Look for "eth0" in the output.  It appears that your NIC is not getting recognized as a network device, even though the hardware database finds it.  What is odd to me is that you say it is working fine in Windows.  If so, it should be showing up in Ubuntu.

---

### Post by lincoln32 on 2008-11-07
the lan card was working in old ubuntu till I played with synce then had to connect usb wifi when I an using HH soI thought format and add home partion
and should get lan back----Famous last words!!!
todd@todd-desktop:~$ lshal | grep net.interface 
  net.interface = 'eth0'  (string)
todd@todd-desktop:~$

---

### Post by bobnutfield on 2008-11-07
Well, everything I could think of is in place.  You have the module loaded, HAL recognizes it, it shows up in lspci...so it should be enabled.  All I can think of is to remove the card, then re-insert it and boot back into Ubuntu to see if it automatically enables it.  

I am afraid that is the sum total of what I knew to help.  I would open a new thread in the networking forum with the title "How to ENABLE a DISABLED NIC eth0"

Sorry I couldn't be more help, but it should be working by all that I can see.

---

### Post by danielsaan on 2011-03-30
Go to /etc/udev/rules.d/70-persistent-net.rules/
Delete the old entries for all ethernet cards. Save.

Reboot.

Ifconfig

Tell me what output is

Good luck. This worked for me.


Dan

---

