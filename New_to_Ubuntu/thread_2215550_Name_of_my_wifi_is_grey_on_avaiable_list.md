---
title: "Name of my wifi is grey on avaiable list"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by grzegorz3 on 2014-04-07
Hello everyone, i have a problem with my wifi,
I show you a screenshot : [http://s3.ifotos.pl/img/201404071_exxxsxw.jpg](http://s3.ifotos.pl/img/201404071_exxxsxw.jpg)
I can see my wifi name (BTHub3-5QHC) but it is grey and i cant connect, as i can see this problems only appears with wifis with password because i can easily connect to wifi FON. Any ideas? Regards.

---

### Post by grzegorz3 on 2014-04-07
need help

---

### Post by m-dw on 2014-04-07
Not sure if this is the issue, but a common problem is an incompatibility between your adaptor and the security settings on the HomeHub (wireless router).  For example if you've set the hub to WPA2 only and your adaptor only supports WEP or WPA it won't work.

---

### Post by thevypr on 2014-04-07
Check your network settings and see for anything on secure networks. Maybe you have something disabled.

---

### Post by grzegorz3 on 2014-04-08
lspci -k | egrep -iA2 'net|wire|eth'
```
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
    Kernel driver in use: e1000
    Kernel modules: e1000
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
    Kernel driver in use: airo
    Kernel modules: airo
```

lshw -C network
```
 *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:10:c6:cd:04:f6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=192.168.1.97 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8400(size=64) memory:c0240000-c024ffff(prefetchable)
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:95:c0:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0214000-c0217fff memory:c0400000-c07fffff memory:c0800000-c09fffff(prefetchable)



```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:10:c6:cd:04:f6  
          inet addr:192.168.1.97  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:c6ff:fecd:4f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:483836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:625315707 (625.3 MB)  TX bytes:26970915 (26.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:02:8a:95:c0:56  
          inet6 addr: fe80::202:8aff:fe95:c056/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:375 dropped:0 overruns:0 frame:375
          TX packets:6 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:396 (396.0 B)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9428 (9.4 KB)  TX bytes:9428 (9.4 KB)

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-33 dBm  Noise level=-105 dBm
          Rx invalid nwid:144  Rx invalid crypt:13  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1208   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-33 dBm  Noise level=-105 dBm
          Rx invalid nwid:144  Rx invalid crypt:13  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1208   Missed beacon:0

```
iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results

wifi0     No scan results

```
nm-tool
```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             connected
  Default:           yes
  HW Address:        00:10:C6:CD:04:F6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.97
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airo
  State:             disconnected
  Default:           no
  HW Address:        00:02:8A:95:C0:56

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes

  Wireless Access Points 


variable@variable-dev:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results

wifi0     No scan results

variable@variable-dev:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             connected
  Default:           yes
  HW Address:        00:10:C6:CD:04:F6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.97
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airo
  State:             disconnected
  Default:           no
  HW Address:        00:02:8A:95:C0:56

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes

  Wireless Access Points 

```
**rfkill list all** dont show anything
lsmod
```
Module                  Size  Used by
binfmt_misc             6587  1 
pcmcia                 30784  0 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
joydev                  8740  0 
snd_intel8x0           25652  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                678831  3 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49847  1 radeon
thinkpad_acpi          68115  0 
drm_kms_helper         29329  1 radeon
yenta_socket           20408  2 
ppdev                   5259  0 
led_class               2864  1 thinkpad_acpi
nsc_ircc               18220  0 
snd                    54244  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
rsrc_nonstatic         10015  1 yenta_socket
drm                   163747  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
airo                   67901  0 
nvram                   6203  1 thinkpad_acpi
parport_pc             25962  1 
irda                  186780  1 nsc_ircc
crc_ccitt               1339  1 irda
intel_agp              24375  1 
video                  17375  0 
output                  1871  1 video
psmouse                63677  0 
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,intel_agp
shpchp                 28835  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
floppy                 53016  0 
e1000                  97435  0 
variable@variable-dev:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
pcmcia                 30784  0 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
joydev                  8740  0 
snd_intel8x0           25652  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                678831  3 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49847  1 radeon
thinkpad_acpi          68115  0 
drm_kms_helper         29329  1 radeon
yenta_socket           20408  2 
ppdev                   5259  0 
led_class               2864  1 thinkpad_acpi
nsc_ircc               18220  0 
snd                    54244  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
rsrc_nonstatic         10015  1 yenta_socket
drm                   163747  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
airo                   67901  0 
nvram                   6203  1 thinkpad_acpi
parport_pc             25962  1 
irda                  186780  1 nsc_ircc
crc_ccitt               1339  1 irda
intel_agp              24375  1 
video                  17375  0 
output                  1871  1 video
psmouse                63677  0 
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,intel_agp
shpchp                 28835  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
floppy                 53016  0 
e1000                  97435  0 

```
uname -a
```
Linux variable-dev 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux

```
maybe that will be helpful

---

### Post by sotiris2 on 2014-04-08
My output of nm-tools goes like this.

```
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
```

It lists all capabilities of the adapter and not the encryption in the current network so... with your showing only WEP, it would appear your adapter is WEP only. Did you ever connect to that wireless network with this adapter ?

---

### Post by grzegorz3 on 2014-04-08
Yes, i used to use wireless on windows.

---

### Post by m-dw on 2014-04-08
[http://wireless.kernel.org/en/users/Drivers/airo#airo](http://wireless.kernel.org/en/users/Drivers/airo#airo) says:

> Only firmware versions 5.30.17 or better can do WPA. The firmware can be obtained from cisco.com however you will need to register first before you can actually obtain the proprietary firmware. Furthermore, the firmware upgrade/downgrade can only be done under windows.

I'd take a guess that you need to lower the security on your router to WEP.

---

### Post by grzegorz3 on 2014-04-08
How WEP Works? Same as normal? Name and password? like WPA/WPA2

---

