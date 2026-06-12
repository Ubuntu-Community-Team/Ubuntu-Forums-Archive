---
title: "Can only connect to internet via ethernet cord."
date: 2012-01-08
forum: New to Ubuntu
---

### Post by angel3012girls on 2012-01-08
I am a beginner with Ubuntu, so please bear with me. I have a Dell Inspiron laptop that had Windows XP removed and Ubuntu installed. I can connect to the internet via ethernet cord and I am trying to figure out how to connect wireless.  Under Network Connections the laptop cannot find it. Pls help. Be patient with me, because like I said I am completely new to this program and I'm getting a little frustrated at this point. 

Thanks in advance!

---

### Post by lechien73 on 2012-01-08
Hi & welcome to the forums,

Some wireless cards don't immediately play happily with Ubuntu, and this can be frustrating to start with.

Anyway, you don't mention what version of Ubuntu you're using, so I'm presuming it's a new install of 11.10. If it is, could you go to the **System Settings[B] menu option from the power & shutdown menu (the cog at the top right), choose [B]Additional Drivers** and see if there are any proprietary drivers available for your system.

---

### Post by angel3012girls on 2012-01-08
M10.04.3 LTS is my version.

---

### Post by corncob on 2012-01-08
There is a switch or button that toggles WiFi on and off.  Make sure that hadn't been hit by accident.

---

### Post by angel3012girls on 2012-01-08
Already tried that Corncob. 
Thanks!

---

### Post by lechien73 on 2012-01-08
> **angel3012girls said:**
> M10.04.3 LTS is my version.

Ok - then the menu option is in a different place. Please could you plug in the ethernet cable, so that you can connect to the Internet, and then go to the **System** menu, choose **Administration -> Hardware Drivers**.

Hopefully a replacement driver will be listed there.

---

### Post by angel3012girls on 2012-01-08
It says Broadcom STA wireless driver and its active and currently in use! Unfortunately that's it.

---

### Post by westie457 on 2012-01-08
> **angel3012girls said:**
> M10.04.3 LTS is my version.

Welcome to the Forum.

Could you open a terminal (press Ctrl+Alt+T at the same time), type in and press Enter after each line ```
lspci

lshw -C network

rfkill list all

lsmod
```

Highlight the entire output, copy, come back here and in a NEW REPLY paste between [Code] brackets  by clicking the # symbol at the top of the message pane.

Thank you.

---

### Post by lechien73 on 2012-01-08
Could you try clicking the **Remove** button to disable the STA driver, please? If you do this, then Ubuntu should revert to using the Broadcom B43 driver. I use this on my Dell laptop with no problems. You may need to restart after removing the STA driver.

---

### Post by sailor2001 on 2012-01-08
in synaptics, download b43 fwcutter

---

### Post by angel3012girls on 2012-01-08
OK done! I activated the Broadcom B43 driver!

---

### Post by lechien73 on 2012-01-08
Great...is it now working properly?

---

### Post by angel3012girls on 2012-01-08
No. :(

---

### Post by lechien73 on 2012-01-08
It looks like your problem is a duplicate of the one in this thread: [http://ubuntuforums.org/showthread.php?t=1905058#4](http://ubuntuforums.org/showthread.php?t=1905058#4)

Could you try the suggestion at post #4 in that thread?

---

### Post by angel3012girls on 2012-01-08
Unfortunately that didn't work either!

---

### Post by angel3012girls on 2012-01-08
alexa@alexa-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
alexa@alexa-laptop:~$ 
```

```

---

### Post by angel3012girls on 2012-01-08
Does the above post help anyone?

---

### Post by westie457 on 2012-01-08
Now we have the card id could you post the output from the two last commands in my previous post please?


Thank you

---

### Post by angel3012girls on 2012-01-08
alexa@alexa-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
alexa@alexa-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52010  1 
snd_hda_codec_intelhdmi    11622  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
b43                   163524  0 
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  9 
ipt_addrtype            1631  4 
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
joydev                  8740  0 
xt_state                1098  7 
mac80211              205402  1 b43
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
ip6table_filter         2343  1 
ip6_tables             11227  1 ip6table_filter
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
snd_rawmidi            19056  1 snd_seq_midi
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack           61615  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2271  1 
i915                  287458  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 i915
ip_tables               9991  1 iptable_filter
drm                   162345  4 i915,drm_kms_helper
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd                    54180  17 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
cfg80211              126528  2 b43,mac80211
lp                      7028  0 
intel_agp              24375  2 i915
soundcore               6620  1 snd
dell_wmi                1793  0 
dcdbas                  5422  0 
psmouse                63245  0 
serio_raw               3978  0 
led_class               2864  2 b43,sdhci
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sky2                   40807  0 
ahci                   32200  2 
ssb                    38934  1 b43
alexa@alexa-laptop:~$ 
```

```

---

### Post by westie457 on 2012-01-08
Try these two commands

~$ sudo modprobe -r b43 ssb wl

~$ sudo modprobe wl


Note: Allow several seconds for the network manager to scan for available networks before attempting a connection.

Ignore any errors. Is it working now?

If not then reboot and it should work.

---

### Post by angel3012girls on 2012-01-08
alexa@alexa-laptop:~$ ~$ sudo modprobe -r b43 ssb wl
~$: command not found
alexa@alexa-laptop:~$ ~$ sudo modprobe wl
~$: command not found
alexa@alexa-laptop:~$ 

Here's what came up and I rebooted, but its still the same.

---

### Post by lechien73 on 2012-01-08
Don't include the ~$ when you type the commands :), so just:

```
sudo modprobe -r b43 ssb wl
```

etc.

---

### Post by angel3012girls on 2012-01-08
Tried that also. Let me try again and copy what happens.

---

### Post by angel3012girls on 2012-01-08
alexa@alexa-laptop:~$ sudo modprobe -r b43 ssb wl
FATAL: Module wl not found.
alexa@alexa-laptop:~$ sudo modprobe wl
FATAL: Module wl not found.
alexa@alexa-laptop:~$

---

### Post by MARP1961 on 2012-01-08
Have a read of this, if like me you have a Dell Inspiron with a Broadcom wireless:

[http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

My Dell Inspiron only works with the B43 driver but if you have previously tried STA it is probably still causing problems.

I would do a fresh install of the latest Ubuntu and do updates by ethernet cable,
[http://www.ubuntu.com/download/ubuntu/download ]("http://www.ubuntu.com/download/ubuntu/download")
then I would ignore 'Additional Drivers' nagging you to install STA. Go to Synaptic Package Manager (which you will probably need to install via the Software Centre) and search for, mark then install **firmware-b43-installer**.

Unplug the ethernet connection and reboot. Left Click the wifi icon and you should see your router listed. Click on it to enter your WEP or WPA passkey.
[]("http://www.ubuntu.com/download/ubuntu/download")

---

