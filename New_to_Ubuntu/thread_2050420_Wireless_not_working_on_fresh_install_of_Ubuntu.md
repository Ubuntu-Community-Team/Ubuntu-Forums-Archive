---
title: "Wireless not working on fresh install of Ubuntu"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by cloneykinz on 2012-08-30
Hello everyone!

I'm super new to Ubuntu, this is my first time installing it. I did a fresh install on my Dell Inspiron 14R N4110 and everything works great with the exception of one thing: my wireless isn't working. The ethernet does in fact work, but the wireless doesn't. This normally wouldn't be an issue if it wouldn't defeat the purpose of having a laptop. I have tried using the fn+2 command to turn it on, this disables the bluetooth right now. I did the trick with taking the battery out then resetting the bios, no go. I hope one of you can help me. It's frustrating me to no end. 

I ran a lshw -C network command in terminal. Here are my results:


*-network UNCLAIMED
description: network controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 0
bus info: pci@000:01:00.0
version: 34
width: 64 bits
clock: 22MHZ
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:d1600000-d1601fff
*network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000003.00.0.
logical name: eth0
version: 05
serial: 14:fe:b5:ae:53:81
size: 100MB/s
capacity: 100MB/s
width: 64bits
clock: 33MHZ
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MS/s
resources: irq:28 ioport:3000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable)

---

### Post by NikTh on 2012-08-30
Hi , 
please post the results of bellow commands 
```
cat /etc/lsb-release && uname -r
lspci -nnk | grep -iA2 net
ifconfig
lsusb
lsmod
nmcli nm
```_**Put the results between ```
 brackets so can be readable. **_

[noparse][code]The Results Here
```[/noparse]

Thanks

---

### Post by cloneykinz on 2012-08-30
Thanks for the quick reply. 

lspci -nnk | -iA2 net

```

01:00.0 Network controller [0280]: Intel Corporation Device [8086:008a] (rev 34)
02:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
	Kernel driver in use: xhci_hcd
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Kernel driver in use: r8169
	Kernel modules: r8169

```

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 14:fe:b5:ae:53:81  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::16fe:b5ff:feae:5381/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3028620 (3.0 MB)  TX bytes:486747 (486.7 KB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:208 (208.0 B)  TX bytes:208 (208.0 B)


```

lsusb

```

Bus 003 Device 002: ID 046d:c530 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2b80 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

lsmod

```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
xt_limit                1382  8 
xt_tcpudp               2011  10 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  6 
binfmt_misc             6587  1 
rfcomm                 33453  4 
ppdev                   5259  0 
sco                     7949  2 
bridge                 45678  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30656  16 rfcomm,bnep
snd_hda_codec_realtek   203472  1 
joydev                  8740  0 
usbhid                 36206  0 
hid                    67288  1 usbhid
iptable_nat             4414  0 
nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10672  9 iptable_nat,nf_nat
nf_conntrack           61615  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          2771  0 
iptable_filter          2271  1 
ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14299  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_hda_intel          22165  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
uvcvideo               57470  0 
dell_wmi                1793  0 
tileblit                1999  1 fbcon
videodev               34457  1 uvcvideo
font                    7557  1 fbcon
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  11053  2 
v4l1_compat            13251  2 uvcvideo,videodev
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             6888  0 
psmouse                63677  0 
serio_raw               3978  0 
dcdbas                  5490  1 dell_laptop
video                  17375  0 
output                  1871  1 video
vga16fb                11385  1 
vgastate                8961  1 vga16fb
xhci                   38082  0 
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            40065  1 
ahci                   32712  2 
r8169                  34396  0 
mii                     4381  1 r8169


```

nmcli nm

```

nmcli: command not found

```

---

### Post by NikTh on 2012-08-30
Hi , 
please post also 
```
cat /etc/lsb-release && uname -r 
rfkill list all
apt-cache policy network-manager
``` 

Thanks

---

### Post by cloneykinz on 2012-08-30
Done and done. xD

cat /etc/lsb-release && uname -r 

```

  Installed: 0.8-0ubuntu3.3
  Candidate: 0.8-0ubuntu3.3
  Version table:
 *** 0.8-0ubuntu3.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
        100 /var/lib/dpkg/status
     0.8-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages


```

rfkill list all

```

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


```

apt-cache policy network-manager

```

network-manager:
  Installed: 0.8-0ubuntu3.3
  Candidate: 0.8-0ubuntu3.3
  Version table:
 *** 0.8-0ubuntu3.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
        100 /var/lib/dpkg/status
     0.8-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages


```

---

### Post by NikTh on 2012-08-30
> **cloneykinz said:**
> Done and done. xD

cat /etc/lsb-release && uname -r 

```

  Installed: 0.8-0ubuntu3.3
  Candidate: 0.8-0ubuntu3.3
  Version table:
 *** 0.8-0ubuntu3.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
        100 /var/lib/dpkg/status
     0.8-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages


```

Hi , 
above is not the correct output , but is ok. I saw what I want. 
Why you installed the 10.04 ? 10.04 is an old release , yes still supported , but support will end in about... 6-7 months. 

I suggest to install the newest LTS(Long Term Support) version of Ubuntu 12.04 . 
Newer kernel , newer packages , better hardware support. 
You can download it from here --> [http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

If (for your own reasons) you want to stick with 10.04 , we can try to solve your problem , but I am not sure. 

Thanks

---

### Post by cloneykinz on 2012-08-30
It was just the cd I got from my friend. If support ends soon, I'll upgrade and test it out. Doing that now.

---

### Post by NikTh on 2012-08-30
> **cloneykinz said:**
> It was just the cd I got from my friend. If support ends soon, I'll upgrade and test it out. Doing that now.

Waiting for the news.

**Better idea would be a fresh install. _Not upgrade_ via Update Manager.**

---

### Post by cloneykinz on 2012-08-30
I'm sure you know what reply I'm going to give you. It works perfectly now!! I can't thank you enough for taking the time to help me. I really appreciate the help!!!!

---

### Post by NikTh on 2012-08-31
> **cloneykinz said:**
> I'm sure you know what reply I'm going to give you. It works perfectly now!! I can't thank you enough for taking the time to help me. I really appreciate the help!!!!

Great News. ! 

Enjoy your new Ubuntu 

Thanks

---

