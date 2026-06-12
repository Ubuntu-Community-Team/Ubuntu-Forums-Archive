---
title: "Wicd killed my internet connectivity!"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by jsudekum on 2008-08-22
So, considering my Atheros chipset, I was having tons of problems trying to fix my wireless. I had tried Madwifi, I had tried ndiswrapper and any variation of these things... I was reading through the threads and saw Wicd as a suggested solution, so I chose to give it a shot.

But when I installed it, my WIRED internet connection died and my networks disappeared. I can't do anything now. Of course, in my panic, I uninstalled Wicd, thinking it would go back to normal or something, but... It's still useless.

Is this even remotely common stupidity? Is there a solution?

I'm not sure what details would be needed in this case (plus, I REALLY don't want to key the longer outputs, considering the dead connection of the said laptop, haha)... But I'll tell you whatever when asked.

---

### Post by jose158 on 2008-08-22
Did you try to reset your router or just restart it? Sometimes mine gives way cause I do too much at one time :p. I let the router cool down for a bit then start it up again. Usually works for me 8)

---

### Post by tangibleorange on 2008-08-22
when plugged into the router, try typing:

```
sudo dhclient eth0
```

and see if it lets you connect to the internet.

---

### Post by jsudekum on 2008-08-22
Well flip! It's working now... This is the thread I was following:

[http://ubuntuforums.org/showthread.php?t=895287&highlight=atheros+ar242x](http://ubuntuforums.org/showthread.php?t=895287&highlight=atheros+ar242x)

But now there are no networks in the tray(considering that was going to be Wicd's job, right?)... And I'm only connected because I went to system>administration>network and enabled the wired connection (which it used to do automatically without having to mess with that stuff). Also, I still have no idea how to connect with my wireless card.

Do I have to redownload the NetworkManager or what?

---

### Post by tangibleorange on 2008-08-22
> **jsudekum said:**
> Well flip! It's working now... This is the thread I was following:

[http://ubuntuforums.org/showthread.php?t=895287&highlight=atheros+ar242x](http://ubuntuforums.org/showthread.php?t=895287&highlight=atheros+ar242x)

But now there are no networks in the tray(considering that was going to be Wicd's job, right?)... And I'm only connected because I went to system>administration>network and enabled the wired connection (which it used to do automatically without having to mess with that stuff). Also, I still have no idea how to connect with my wireless card.

Do I have to redownload the NetworkManager or what?

to re-install network manager:

```
sudo apt-get install network-manager network-manager-gnome
```

---

### Post by jsudekum on 2008-08-22
Thanks. Now, how do I get this in the tray like it used to be?

Also, can you guys help me with my Atheros problem? It's an ar242x and I've attempted Madwifi/ndiswrapper.

Here's some more information...

lspci -nn:

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```

lsmod:

```
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  0 
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
psmouse                40336  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
wmi_acer                9644  0 
serio_raw               7940  0 
iTCO_wdt               13092  0 
button                  9232  0 
battery                14212  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  1 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  7 
pcspkr                  4224  0 
agpgart                34760  3 drm,intel_agp
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
sg                     36880  0 
8139too                27520  0 
sd_mod                 30720  3 
ata_piix               19588  0 
ahci                   28420  2 
pata_acpi               8320  0 
libata                159344  4 ata_generic,ata_piix,ahci,pata_acpi
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3
```

Laptop is a 32-bit Compaq Presario C700.

---

### Post by tangibleorange on 2008-08-22
i'm afraid i've no experience of atheros chipsets. i can however give you your network icon back!

[LIST]
[*]System -> Preferences -> Sessions
[*]Click 'add'
[*]Name: network icon
[*]Command: nm-applet
[*]Comment: show me t3h network! (or whatever you want :popcorn:)
[/LIST]

and reboot. you should now have a network icon!

---

### Post by jsudekum on 2008-08-22
Aw man... Thanks a billion, though! I really appreciate your prompt reply.

I might have to revert to Vista, sadly, considering this wireless issue. This is my girlfriend's laptop and her dorm in college requires wireless, so... It has to be working. If there's anything any of you could do, I would willingly give you my firstborn child.

---

### Post by tangibleorange on 2008-08-22
> **jsudekum said:**
> Aw man... Thanks a billion, though! I really appreciate your prompt reply.

I might have to revert to Vista, sadly, considering this wireless issue. This is my girlfriend's laptop and her dorm in college requires wireless, so... It has to be working. If there's anything any of you could do, I would willingly give you my firstborn child.

hmm. that's a shame but i understand. you could try this:

```

sudo apt-get install build-essential linux-headers-`uname -r`
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2008-08-06.tar.bz2
tar jxf compat-wireless-2008-08-06.tar.bz2
cd compat-wireless-2008-08-06.tar.bz2
make
sudo make install
sudo make load
```

now i don't hold out much hope, but you never know...

---

### Post by jsudekum on 2008-08-22
Oh, trust me, I'M not leaving Ubuntu at all. Heh... I'm actually about to buy the new Dell XPS M1530 with Ubuntu pre-installed. :)

I'll try this momentarily. It looks like the same old thing I've been doing, but who knows. Thanks again.

---

### Post by jsudekum on 2008-08-23
Alright. It's been a while since I logged in, so a lot has happened...

I reinstalled the Network Manager with the code you suggested. Now, I see the Network Manager icon in the tray, but it doesn't remotely reflect reality, haha. In other words, the monitors which mean "you have a wired internet connection" are always on, regardless of whether or not I do. I can also setup a wireless network now, but it's the same premise... No connection is actually made, even though the bars of connectivity are up.

Furthermore, when I try to turn it on wireless, realize it's not going to work, and then plug in the ethernet cable, I am still periodically prompted for a passphrase for my wireless network. 

What now? haha

---

### Post by tangibleorange on 2008-08-23
> **jsudekum said:**
> Alright. It's been a while since I logged in, so a lot has happened...

I reinstalled the Network Manager with the code you suggested. Now, I see the Network Manager icon in the tray, but it doesn't remotely reflect reality, haha. In other words, the monitors which mean "you have a wired internet connection" are always on, regardless of whether or not I do. I can also setup a wireless network now, but it's the same premise... No connection is actually made, even though the bars of connectivity are up.

Furthermore, when I try to turn it on wireless, realize it's not going to work, and then plug in the ethernet cable, I am still periodically prompted for a passphrase for my wireless network. 

What now? haha

i guess you could try removing its config files and then reinstalling:

```
sudo apt-get purge network-manager network-manager-gnome
sudo apt-get install network-manager network-manager-gnome
```

but i think the way forward is to install WICD. we can make it work with your wired connection:
```

sudo apt-get install wicd
```

then, make sure the only lines WITHOUT a '#' in front of them are. you can safely delete anything else:

```

auto lo
iface lo inet loopback

```

then, add WICD to the startup programs tab. follow the procedure in my previous post for doing that (like with the other network applet) but change the Command: field to:

```
/opt/wicd/tray.py
```

and then reboot. then try playing around with WICD's settings. (right click icon and select 'connect'. then select 'preferences' at the top and make sure 'always show wired interface' is ticked. it should then let you create a wired profile from its main window.
if it still won't let you connect to your wired interface, try this:

```
sudo dhclient eth0
```

---

### Post by billgoldberg on 2008-08-23
> **jsudekum said:**
> So, considering my Atheros chipset, I was having tons of problems trying to fix my wireless. I had tried Madwifi, I had tried ndiswrapper and any variation of these things... I was reading through the threads and saw Wicd as a suggested solution, so I chose to give it a shot.

But when I installed it, my WIRED internet connection died and my networks disappeared. I can't do anything now. Of course, in my panic, I uninstalled Wicd, thinking it would go back to normal or something, but... It's still useless.

Is this even remotely common stupidity? Is there a solution?

I'm not sure what details would be needed in this case (plus, I REALLY don't want to key the longer outputs, considering the dead connection of the said laptop, haha)... But I'll tell you whatever when asked.

Since you need to remove network-manager to be able to install wicd, you'll need to install that again.

You can install it from the Ubuntu live cd (and alternate I suppose).

Put in the cd, go to synaptic and search for "network-manager".

Install it and log out and back in. You're wired connection should be running by that point.

You'll need to add the applet back to the gnome panel.

I think it's calld nm-applet. You are going to have to download that from synaptic too before you can add it the panel.

--

I'm just wanted to state that wicd handels my wired and wireless connection on my desktop. Where network-manager can only handly my wired one.

---

