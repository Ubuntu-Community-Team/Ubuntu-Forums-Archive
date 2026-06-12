---
title: "Unstable wireless connection with USB Adapter"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Alfango on 2012-01-14
I have Ubuntu 11.10 and I use a D-Link DWA-110 USB device for receiving signal form my router. My connection drops down after a while (sometimes minutes, sometimes hours). It seems to be connected to network, but the usb device just stops working.

I discarded ISP and router issues because my other desktop computer, with the same features but different wireless device, works perfectly.

Following this: [http://goo.gl/L2gbB](http://goo.gl/L2gbB) (I'm almost sure it is a driver issue), I got this:

Input:
```
sudo lshw -C network
```

Output:
```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 40:61:86:50:8f:d7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:ce00(size=256) memory:fd9ff000-fd9fffff memory:fda00000-fda1ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:1e:58:99:4a:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.0.0-14-generic-pae firmware=1.7 ip=192.168.0.2 link=yes multicast=yes wireless=IEEE 802.11bg
```

As you can see, my driver is rt73usb. This is what I got with lsmod:

Input:
```
lsmod
```

Output:
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20092  1 rt73usb
rt2x00lib              48114  2 rt73usb,rt2x00usb
mac80211              393459  2 rt2x00usb,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
snd_hda_intel          28358  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
usbhid                 41905  0 
snd_seq_midi           13132  0 
usb_storage            44173  0 
uas                    17699  0 
hid                    77367  1 usbhid
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                63474  0 
serio_raw              12990  0 
i915                  509290  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  47200  0
```

I don't know what this line means, but doesn't look good for me:

```
rt73usb                27029  0
```

I'll really appreciate your help. I love Ubuntu, and this is the only ploblem I have with it. I don't want to go back with Windows.

---

### Post by kalfusisagod on 2012-01-14
If it is not a hardware issue, it may be a internal network issue. You can probably login to your router through your gateway address (usually 192.168.1.1). I'm pretty sure you can find this out by going into Terminal CTRL ALT T and then typing ifconfig and look for the correct interface 

eth0 is usually your hardwire ethernet card
wlan0 is usually your wireless
lo is a loopback

Once you login to your router (may need a username and pass for your router, google it) then look for a tab called LAN and make sure there isn't a IP conflict of some sort. This may get you started IF its not a hardware issue.

---

### Post by wildmanne39 on 2012-01-14
Hi, this the first time I have seen a problem with this driver, I use this driver myself but here is something you can try:
```
gksudo gedit /etc/modprobe.d/rt73usb.conf
```
Add a single line:
```
options rt73usb nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

---

### Post by Alfango on 2012-01-14
I did it, and nothing changes in the lsmod output. However, until now, my connection hasn't dropped down, but it gets incredibly slow.

---

### Post by Alfango on 2012-01-14
I don't see nothing worng... maybe you do.

Input:
```
ifconfig
```

Output:
```
eth0      Link encap:Ethernet  direcciónHW 40:61:86:50:8f:d7  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:42 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:1e:58:99:4a:51  
          Direc. inet:192.168.0.2  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::21e:58ff:fe99:4a51/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:2796 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:2654 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:2051169 (2.0 MB)  TX bytes:478442 (478.4 KB)
```

---

### Post by wildmanne39 on 2012-01-15
Hi, you will not see any difference in the lsmod.

Have you had more problems?
Thanks

---

### Post by Alfango on 2012-01-15
Actually, yes. My connection is stable now, but incredibly slow (0.10 Mbps when my normal speed is 4Mbps).

And a weird thing happens. When I boot up from a USB device, connection is normal.

Thanks.

---

### Post by wildmanne39 on 2012-01-15
Hi, try this:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
``` 
also click on the network icon in the top panel go to edit connection, wireless and set your settings to look like what is in the screenshots, except leave auto connect checked.
Thanks

---

