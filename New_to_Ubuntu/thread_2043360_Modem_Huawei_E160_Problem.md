---
title: "Modem Huawei E160 Problem"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by parcdulas on 2012-08-16
I have the same problem on 12.04. I have to use windows to connect and it would seem that the USB Huawei dongle (mine is O2) has a mass storage device with a connection program that switches over to the Modem and actually does the connection. Network manager for me on both a desktop and a laptop do not recognise that there is a Huawei modem to connect to. The choice of device is greyed out. Itried with an old Nokia mobile phone on its USB cable and network manager recognised it at once but the phone had given the choice of using it as a storage device or a modem first. Does any one know the correct syntax for Modeswitch or where to find it?:confused:

---

### Post by oldos2er on 2012-08-16
Post moved to its own thread.

---

### Post by NikTh on 2012-08-16
Hi , 
can you please open a terminal and post the output of 
```
lsusb
``` with stick plugged. 
Thanks

---

### Post by parcdulas on 2012-08-18
There are a number of entries that are for the basic machine hardware then:
Bus 001 Device 002:ID 0dba:0116 Realtek Semiconductor Corp. Mass Storage device
Bus 001 Device 003:ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem/ E230/E270/E870 HSDPA/HSUPA Modem

I only have the O2 dongle plugged in, no other usb devices

Network manager does not "see" the Modem as the device dialogue box is "greyed" out and inoperative

Martin

---

### Post by NikTh on 2012-08-18
Hi , 
can you give the output of 
```
lsmod
df
```please put the output inside  ```
 tags .  [noparse][code]the output here
```[/noparse]
Thanks

---

### Post by drpjkurian on 2012-08-19
Hi parcdulas
Please try this thread, it may help you 
[http://ubuntuforums.org/showthread.php?t=1814583](http://ubuntuforums.org/showthread.php?t=1814583)

---

### Post by parcdulas on 2012-08-19
This is roughly what I get from lsmod and df. sorry if it is not complete but as I can only connect under Windoze I had to transfer the terminal output ultimately to a notepad file which screwed up the formatting. This is one of the main reasons I want to migrate from Windoze to a hopefully more reliable OS.

```

martin@martin-F5RL:~$ lsmod


Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174055  1 
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
option                 25580  0 
snd_timer              28931  2 snd_pcm,snd_seq
arc4                   12473  2 
usb_wwan               19779  1 option
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
usbserial              37173  2 option,usb_wwan
radeon                733693  3 
snd			62064 16 

snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                72846  0 
soundcore              14635  1 snd
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
serio_raw              13027  0 
sp5100_tco             13495  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_piix4              13093  0 
video                  19068  0 
i2c_algo_bit           13199  1 radeon
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
asus_laptop            23693  0 
sparse_keymap          13658  1 asus_laptop
input_polldev          13648  1 asus_laptop
shpchp                 32325  0 
mac_hid                13077  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_atiixp            12999  0 
atl2                   28040  0 
usb_storage            39646  0 

martin@martin-F5RL:~$ 

martin@martin-F5RL:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda7       20115504 2481084  16625424  13% /
udev              440400       4    440396   1% /dev
tmpfs             179068     844    178224   1% /run
none                5120       0      5120   0% /run/lock
none              447668      76    447592   1% /run/shm
martin@martin-F5RL:~$ 
```


Martin

---

### Post by NikTh on 2012-08-19
Hi , 
plug the dongle and try these commands 
```
sudo modprobe -rf usbserial 
sudo modprobe -rf usb-storage 
sudo modprobe usbserial vendor=0x12d1 product=0x1003
```See now in network-manager if your dongle recognized as modem and if it is , then configure your network. 
If errors displayed from above commands post them here.
Thanks

---

### Post by Wim Sturkenboom on 2012-08-19
> **parcdulas said:**
> This is roughly what I get from lsmod and df. sorry if it is not complete but as I can only connect under Windoze I had to transfer the terminal output ultimately to a notepad file which screwed up the formatting. This is one of the main reasons I want to migrate from Windoze to a hopefully more reliable OS.

Totally off topic
I think the utility (in Ubuntu) is called 'todos'; it will convert linux text files to dos/windows textfiles. The other way around is 'fromdos'. See [http://pwet.fr/man/linux/commandes/fromdos](http://pwet.fr/man/linux/commandes/fromdos) Related commands are unix2dos and dos2unix, but if I recall correctly, Ubuntu does not know them.

Notepad did not screw up the formatting; it just does not understand the line-end as used in Linux. In windows, you can use wordpad to read the file; it will understand the line-end as used in Linux.

But as said, totally off topic

---

### Post by parcdulas on 2012-08-19
NikTh,

Tried your suggested code in Terminal. After the first line I got the response:

 FATAL: module usbserial is in use

The other two lines returned without any response.

I tried Network manager after each line but the dialogue box for the device to use was always "greyed" out and would not accept any change.

Any other suggestions?

Martin

---

### Post by NikTh on 2012-08-19
Hi , 
try one more time with different commands 
```
sudo modprobe -r option 
sudo modprobe -r usb_wwan 
sudo modprobe -r usbserial 
sudo modprobe -r usb_storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003
```
execute above commands with this order . Should not return any errors.
Wait 5-10 secs and check the lsmod command 
```
lsmod
``` 
and ```
sudo lshw -C network
``` 
Thanks

---

### Post by parcdulas on 2012-08-20
NickTh,

The first set of commands in terminal did not return any errors. I waited for a while (about 30 seconds) and then entered lsmod this gave the following output:

```
martin@martin-F5RL:~$ lsmod
Module                  Size  Used by
usbserial              37173  0 
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
joydev                 17393  0 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_si3054    12864  1 
arc4                   12473  2 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ath5k                 145127  0 
ath                    19387  1 ath5k
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              436455  1 ath5k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72846  0 
snd                    62064  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
radeon                733693  3 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
cfg80211              178679  3 ath5k,ath,mac80211
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
shpchp                 32325  0 
ati_agp                13242  0 
video                  19068  0 
asus_laptop            23693  0 
sparse_keymap          13658  1 asus_laptop
input_polldev          13648  1 asus_laptop
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_atiixp            12999  0 
atl2                   28040  0 
martin@martin-F5RL:~$ 

```


I then entered lshw -C network and the response after a few seconds was:

```

martin@martin-F5RL:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:59:6f:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-23-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fa9f0000-fa9fffff
  *-network
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:3f:49:3a
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 firmware=L2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:feac0000-feafffff memory:feaa0000-feabffff
martin@martin-F5RL:~$ 

```

This seems to have shown up the inbuilt Atheros network card which will not work any more (I now plug in an external usb wireless network dongle from Dlink if i need my home network) but no sign of the Huawei dongle.

Martin

---

### Post by NikTh on 2012-08-20
> **parcdulas said:**
> NickTh,

This seems to have shown up the inbuilt Atheros network card **which will not work any more **(I now plug in an external usb wireless network dongle from Dlink if i need my home network) but no sign of the Huawei dongle.

Martin

Hi Martin 
If you don't use the ath5k module it will be good to blacklist it. 
```
echo 'blacklist ath5k' | sudo tee -a /etc/modprobe.d/blacklist.conf
```Then reboot your system and make sure that ath5k is blacklisted 
```
lsmod | grep ath
``` must return nothing.

Then run again the commands in #11th post and see if Hauwei recognized. No other dongle  should be plugged in.
Thanks

---

### Post by parcdulas on 2012-08-21
NickTh,

I carried out the procedure to blacklist my non functional Atheros wireless network. After a reboot lsmod | grep ath gave no response so I assume the Atheros card is now disabled.

I then input the terminal commands as outlined in post 11. the responses as below:

```

sudo modprobe -r option
FATAL module option in use
sudo modprobe -r usb_wwan
FATAL module usb_wwan in use
sudo modprobe -r usbserial
FATAL module usbserial in use
sudo modprobe usb_storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003


```

The last two commands gave no failure message. I waited a while and then gave the lsmod command:

```
martin@martin-F5RL:~$ lsmod
Module                  Size  Used by
usbserial              37173  0 
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
joydev                 17393  0 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_si3054    12864  1 
arc4                   12473  2 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ath5k                 145127  0 
ath                    19387  1 ath5k
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              436455  1 ath5k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72846  0 
snd                    62064  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
radeon                733693  3 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
cfg80211              178679  3 ath5k,ath,mac80211
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
shpchp                 32325  0 
ati_agp                13242  0 
video                  19068  0 
asus_laptop            23693  0 
sparse_keymap          13658  1 asus_laptop
input_polldev          13648  1 asus_laptop
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_atiixp            12999  0 
atl2                   28040  0 
martin@martin-F5RL:~$ 

```

---

### Post by NikTh on 2012-08-21
Hi , 
I cannot guide you through the solution ( never used such dongle) , but I found a good reference to your problem in Usb-modeswitch- forums. Little old but maybe worth to read it (different dongle but same id: 12d1:1003) 
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=427&sid=a282464a5bfccfc7e831e6b2f7bd7fe8](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=427&sid=a282464a5bfccfc7e831e6b2f7bd7fe8)
It seems like the firmware of the device needs an update . Can you confirm that you have the latest firmware ? 
Thanks

---

### Post by parcdulas on 2012-08-22
Thanks NickTh, I'll work through the link. There was a software update for the WINDOZE launcher that causes problems as the old launcher is still active from the dongle (under WINDOZE) but no firmware update for the dongle as far as I have found so far. Thanks again for your help.

Martin

---

### Post by mzaam on 2012-08-22
have u tick enable wireless broadband box?

---

### Post by parcdulas on 2012-08-25
I found a site that was offering a firmware update for the dongle and after that was installed into the flash memory it is now recognised by Ubuntu although as mentioned in other threads the default entries that the wizard uses are wrong. After correcting those I was able to connect to the internet. Alas my 30 days was up so my credit reverted to zero so I could only access the O2 site for topping up. I'll fork out again to to O2 when I need it next.

Thank you everyone particularly NickTh for the help along the way.

Martin

---

### Post by NikTh on 2012-08-25
Hi , 
you have done a good job @parcdulas. You didn't abandon the effort and at the end "vindicated"
Glad you solved. 
Thanks.

---

### Post by daftu on 2013-01-08
> **parcdulas said:**
> I found a site that was offering a firmware update for the dongle and after that was installed into the flash memory it is now recognised by Ubuntu although as mentioned in other threads the default entries that the wizard uses are wrong. After correcting those I was able to connect to the internet. Alas my 30 days was up so my credit reverted to zero so I could only access the O2 site for topping up. I'll fork out again to to O2 when I need it next.

Thank you everyone particularly NickTh for the help along the way.

Martin

Can you post the link to the site with firmware that you've found working with Ubuntu?
Thanks!

---

### Post by momist on 2013-02-17
> **daftu said:**
> Can you post the link to the site with firmware that you've found working with Ubuntu?
Thanks!

Me too, please?

I've just bought a Huawei E160 ready unlocked (ex O2) for use with Samba.  It works well in WindowsXP but neither Lubuntu nor Peppermint Linux can make it work for me.

thanks for any help.

---

