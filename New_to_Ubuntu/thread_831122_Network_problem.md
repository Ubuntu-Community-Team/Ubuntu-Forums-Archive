---
title: "Network problem"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by falhbin on 2008-06-16
I posted this question in another part of the Forum but didn't get any responses so I try here.

First, I am very new to this so please be gentle with me...

When I boot from the Ubuntu Live CD I don't have any problems to log on to my wireless network, I works like a charm.

However, now when I have installed it on my HD I can't get it to work. I have read alot of forums regarding this but I haven't got very far. I use a USB D-Link DWL-G122. I see networks and it asks for the wep key ten it starts to log on but after about half a minute it asks for the wepkey again. I tried manual configuration and then I get aboyt 34% strenght on the signal but no internet connection. Sometimes it gets an ip-address but it never shows up in the attached device list in the router. 

I think like this. Since it works on the Live CD and it works on Backtrack 2 the drivers must be there somewhere - I just can't find them.

Please help me... "You are my only hope...."

---

### Post by cariboo on 2008-06-16
The driver that comes with the latest kernel is the rt2500usb. Make sure you have the correct module installed as there is also an rt2500pci. To find out which module is installed in a terminal type:

```
sudo lsmod | grep rt*
```

if the wrong module is installed yan can remove it using:

```
sudo rmmod rt25x
```

replace rt25x with the module you are removing.

to insert a module use:

```
sudo modprobe rt25x
```

In Linux the drivers are called modules and are located in /lib/module/kernel-version

Jim

---

### Post by falhbin on 2008-06-16
Thanx man!! You are my Guru :)

---

### Post by falhbin on 2008-06-16
Hi it's me again. I had it up and running and then I had to remove the usb network card and after that I cant get it to work again. I did a sudo lsmod | grep rt* and here is the result

arc4                    2944  2 
blkcipher               8324  1 ecb
rt2500usb              24320  0 
rt2x00usb              12800  1 rt2500usb
rt2x00lib              22528  2 rt2500usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
drm                    82580  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
ndiswrapper           192920  0 
parport_pc             36260  0 
parport                37832  3 ppdev,parport_pc,lp
snd_mixer_oss          17920  1 snd_pcm_oss
serio_raw               7940  0 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_rawmidi            25760  1 snd_seq_midi
wmi_acer                9644  0 
battery                14212  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
agpgart                34760  3 drm,intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
usbcore               146028  6 rt2500usb,rt2x00usb,ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
softcursor              3072  1 bitblit

---

