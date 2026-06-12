---
title: "How to install a speedtouch 110 wireless pc card"
date: 2005-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by MisterE on 2005-06-29
please i am a beginner with ubuntu

how exaly kan i install speedtouch 110 wireless pc card word for word please help!!!!

ik ben Nederlands

---

### Post by Ashrael on 2006-09-29
I second this post!!! 

I'm a newbee too, and also...dutch...can't have it all right? 
I want to install this speedtouch (b*tch) card too, just to learn... After that i'm tossing it...and upgrade...

I have read and followed lots and lots of posts about this card and wlan in general, and it doesn't want to work! 

This is what lsmod came up with...

oem@Schatje:~$ lsmod
Module                  Size  Used by
ipv6                  286976  20
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54212  4 rfcomm,l2cap
ppdev                   9668  0
speedstep_lib           4580  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 63256  1
af_packet              24520  2
md_mod                 76052  0
lp                     12356  0
pcmcia                 41948  0
tsdev                   8032  0
pcspkr                  2244  0
parport_pc             37988  1
parport                39400  3 ppdev,lp,parport_pc
floppy                 64676  0
snd_es1968             33376  2
gameport               16776  1 snd_es1968
snd_ac97_codec        100224  1 snd_es1968
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  4 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd_page_alloc         11304  2 snd_es1968,snd_pcm
snd_mpu401_uart         8640  1 snd_es1968
snd_rawmidi            26848  1 snd_mpu401_uart
snd_seq_device          9228  1 snd_rawmidi
snd                    60004  12 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
e100                   40964  0
mii                     6176  1 e100
yenta_socket           30124  2
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9168  0
soundcore              10784  1 snd
psmouse                40004  0
i2c_core               22848  2 i2c_acpi_ec,i2c_piix4
serio_raw               7748  0
intel_agp              24700  1
agpgart                36784  1 intel_agp
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
evdev                  10176  1
ext3                  148296  1
jbd                    65876  1 ext3
ide_generic             1504  0
uhci_hcd               35536  0
usbcore               139172  2 uhci_hcd
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  3
piix                   11652  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

Did a carctl ident:
root@Schatje:/home/oem# cardctl ident
Socket 0:
  no product info available
Socket 1:
  product info: "Agere Systems", "Wireless PC Card Model 0110", "", ""
  manfid: 0x0156, 0x0003
  function: 6 (network)
root@Schatje:/home/oem#

Since i'm convinced that the card is a hermes I type card and should be working with the orinoco driver, i modprobed for orinoco_cs (or should it do that auto?) Did another lsmod:

root@Schatje:/home/oem# lsmod
Module                  Size  Used by
orinoco_cs             18344  0
orinoco                45940  1 orinoco_cs
hermes                  8352  2 orinoco_cs,orinoco
ipv6                  286976  20
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54212  4 rfcomm,l2cap
ppdev                   9668  0
speedstep_lib           4580  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 63256  1
af_packet              24520  2
md_mod                 76052  0
lp                     12356  0
pcmcia                 41948  1 orinoco_cs
tsdev                   8032  0
pcspkr                  2244  0
parport_pc             37988  1
parport                39400  3 ppdev,lp,parport_pc
floppy                 64676  0
snd_es1968             33376  2
gameport               16776  1 snd_es1968
snd_ac97_codec        100224  1 snd_es1968
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  4 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd_page_alloc         11304  2 snd_es1968,snd_pcm
snd_mpu401_uart         8640  1 snd_es1968
snd_rawmidi            26848  1 snd_mpu401_uart
snd_seq_device          9228  1 snd_rawmidi
snd                    60004  12 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
e100                   40964  0
mii                     6176  1 e100
yenta_socket           30124  4
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9168  0
soundcore              10784  1 snd
psmouse                40004  0
i2c_core               22848  2 i2c_acpi_ec,i2c_piix4
serio_raw               7748  0
intel_agp              24700  1
agpgart                36784  1 intel_agp
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
evdev                  10176  1
ext3                  148296  1
jbd                    65876  1 ext3
ide_generic             1504  0
uhci_hcd               35536  0
usbcore               139172  2 uhci_hcd
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  3
piix                   11652  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit
root@Schatje:/home/oem#

Now i'm guessing that module orinoco_cs should be used by something before the card's gonna work...I saw on another forum a lsmod list by someone else, and there orinoco_cs is used by ds...???? And that's where i'm stuck right now...Can't find any info on this module (lots of nintendo ds links)
So if any of you could enlighten me further on this subject, would be very much appreciated....



If we're not in it for the fun, for what then?

---

### Post by gijsterbeek on 2008-03-31
I've finally managed to enable my Thomson Speedtouch 110 wireless PCMCIA card (with Hermes II chipset), and access the internet with it. After trying everything to no avail, I stumbled upon this french forum.How to proceed? Well, make sure your machine is hooked to the internet (with an ethernet cable that is, wireless is to be fixed soon...)

Then, go to this URL: 

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1475908](http://forum.ubuntu-fr.org/viewtopic.php?pid=1475908)

Halfway down you'll find a script. Paste this script 
into a blank file that you'll save as: ~/speedtouch.sh :

Then, make it executable with:

```
sudo chmod +x ~/speedtouch.sh
```and run it as root:

```
sudo sh ~/speedtouch.sh
```A lot of text will be scrolling up the screen, but in the end, all you need to do is reboot the machine, and voilà! No NDISwrapper. No manual kernel tinkering. Works like a charm. The only thing that I need to find out is how to enable WEP or WPA2 properly.

What the script does? I guess it combines the sources for the PCMCIA device and the Wifi chipset into one convenient kernel module. It doesn't mess anything up. Please say thank you to huit-six if this script made you happy.

---

