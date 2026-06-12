---
title: "[SOLVED] Ethernet not working on macbook ubuntu"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by shippo752 on 2008-08-04
I've been trying to follow the instructions on this thread:
[http://ubuntuforums.org/showthread.php?t=771852&highlight=wireless](http://ubuntuforums.org/showthread.php?t=771852&highlight=wireless)
but I cannot get past the Connect to Internet via ethernet part. 

I have a second generation Macbook
I plugged in the ethernet cable into the mac, but I can't get the Firefox browser working.

---

### Post by dannyboy79 on 2008-08-04
> **shippo752 said:**
> I've been trying to follow the instructions on this thread:
[http://ubuntuforums.org/showthread.php?t=771852&highlight=wireless](http://ubuntuforums.org/showthread.php?t=771852&highlight=wireless)
but I cannot get past the Connect to Internet via ethernet part. 

I have a second generation Macbook
I plugged in the ethernet cable into the mac, but I can't get the Firefox browser working.

please let us know what ethernet hardware your second gen mac has. you would issue this command:

```
dmesg | grep eth
```

then whatever eth (eth stands for ethernet) says it is (my example: VIA Rhine II), see if the module is getting loaded by issuing this command

```
lsmod | grep via
```
you may have to use capital  letters or maybe not. In my example I did. you could just output the entire module  list that's being loaded by just issuing

```
lsmod
```

you're saying you can't even get internet access even when using a ethernet cable hard wired. Are you using a router (w/ DHCP server?) or is it straight from the cable or dsl modem?

---

### Post by shippo752 on 2008-08-04
I'm using the actual cable. 

Um, so I typed in those commands, but I can't make any sense of it. Which parts of the results do you want? I can't type the whole thing.

---

### Post by shippo752 on 2008-08-04
I think it says sky2 eth0
Is that what you meant?

---

### Post by Paqman on 2008-08-04
> **shippo752 said:**
> I can't type the whole thing.

Just copy it all (maybe to a file on a USB stick?) then paste it in here.

---

### Post by LowSky on 2008-08-04
I found these instructions, but don't know if the work
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by shippo752 on 2008-08-04
```

shippo752@lauren-linux:~$ dmesg | grep eth
[   28.211810] Driver 'sr' needs updating - please use bus_type methods
[   28.218014] Driver 'sd' needs updating - please use bus_type methods
[   37.790919] sky2 eth0: addr 00:19:e3:40:4d:e2
[   38.925149] sky2 eth0: enabling interface
[   39.366067] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   63.710244] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   63.713723] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   67.304649] eth0: no IPv6 routers present
[  103.779538] sky2 eth0: disabling interface
[  103.798384] sky2 eth0: enabling interface
[  103.804046] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  104.984852] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  104.986554] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  107.916758] eth0: no IPv6 routers present
[  114.265965] sky2 eth0: Link is down.
[  115.145529] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  115.149034] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  117.128002] eth0: no IPv6 routers present
shippo752@lauren-linux:~$ lsmod | grep via
shippo752@lauren-linux:~$ lsmod
Module                  Size  Used by
i915                   32512  2 
drm                    82452  3 i915
hci_usb                16540  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  7 hci_usb,rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  2 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
ipv6                  267780  10 
joydev                 13120  0 
af_packet              23812  2 
appletouch             11264  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
appleir                 7040  0 
snd_hda_intel         344728  3 
usbhid                 31872  0 
hid                    38784  1 usbhid
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
sky2                   47492  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
video                  19856  0 
output                  4736  1 video
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
intel_agp              25492  1 
button                  9232  0 
ac                      6916  0 
agpgart                34760  3 drm,intel_agp
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
evdev                  13056  8 
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  2 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
ata_piix               19588  1 
pata_acpi               8320  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  5 sbp2,sg,sd_mod,sr_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  8 hci_usb,appletouch,uvcvideo,appleir,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

---

### Post by dannyboy79 on 2008-08-04
> **shippo752 said:**
> I think it says sky2 eth0
Is that what you meant?

what does the command
```
ifconfig
```
return, just copy it out of the terminal and paste it here.
also, you didn't answer my other questions about router (DHCP server) on the network, any switches involved so on and so forth.

also, did you see this?

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by shippo752 on 2008-08-04
```

shippo752@lauren-linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:e3:40:4d:e2  
          inet6 addr: fe80::219:e3ff:fe40:4de2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25716 (25.1 KB)  TX bytes:13731 (13.4 KB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:e3:40:4d:e2  
          inet addr:169.254.8.62  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96268 (94.0 KB)  TX bytes:96268 (94.0 KB)

```

I did look at that help page, but I couldn't make any sense of that either. Besides I think some of the instructions on that page required some sort of connection to the internet.
As for you questions about router on the network and switches, I can't really answer them either since I have no idea what they are. 
I apologize for the lack of info, but I'm a total newbie at this. All help is appreciated though :D

---

### Post by shippo752 on 2008-08-04
I should also probably mention that I had installed Ubuntu only last night. I haven't done anything to it so far (installing drivers and config. settings)
I'm using Ubuntu Hardy Heron

---

### Post by dannyboy79 on 2008-08-04
> **shippo752 said:**
> ```

shippo752@lauren-linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:e3:40:4d:e2  
          inet6 addr: fe80::219:e3ff:fe40:4de2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25716 (25.1 KB)  TX bytes:13731 (13.4 KB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:e3:40:4d:e2  
          inet addr:169.254.8.62  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96268 (94.0 KB)  TX bytes:96268 (94.0 KB)

```

I did look at that help page, but I couldn't make any sense of that either. Besides I think some of the instructions on that page required some sort of connection to the internet.
As for you questions about router on the network and switches, I can't really answer them either since I have no idea what they are. 
I apologize for the lack of info, but I'm a total newbie at this. All help is appreciated though :D

the reason you can't get on the internet is because you're not getting a valid ip address on your eth0 interface. eth0:avahi is showing 169.254.8.62, which I don't believe is a good ip. So you don't know if you have a dsl modem, a cable modem, a router or anything like that? from your computer, where does the ethernet cable plug into? is it a device that has many ports on the back of it or just one? does it have a phone cord plugged into it or a coax cable (you know, like for tv).

I have read, "The reason why we had eth0:avahi instead of eth0 was due to the fact that there was a problem with our router which could not dynamically allocate IP address. Once the router was sorted out, everything went back to normal. ALso, If it does not see the DHCP server it will give up and make up an IP address for itself. This IP will often look something like 169.x.x.x. This is a local address that will not likely have any communication with other PCs on the network."

Assuming you have a router, try this, first unplug your router's power cord, then unplug your cable modem's power cord. THen wait 10 seconds, then plug in the cable modem's power cord first, wait for all the lights to light up or at least 1 minute. then plug in the power cord for the router. wait another 30 seconds and then issue this command

sudo /etc/init.d/networking restart

after you issue that command, paste back anything that it spits out at you. also, issue this command

```
tail /var/log/syslog
```

also post back what comes from entering this in the terminal

cat /etc/network/interfaces

last thing to check, what does this return?

```
ethtool -i eth0
```
I don't use Hardy, so maybe there's something that I am missing.

---

### Post by shippo752 on 2008-08-04
```

shippo752@lauren-linux:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
shippo752@lauren-linux:~$ tail /var/log/syslog 
Aug  4 19:31:42 lauren-linux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Aug  4 19:31:42 lauren-linux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Aug  4 19:31:42 lauren-linux NetworkManager: <info>  not touching eth0 configuration, was configured externally 
Aug  4 19:31:42 lauren-linux NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Aug  4 19:31:42 lauren-linux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug  4 19:31:42 lauren-linux NetworkManager: <info>  Activation (eth0) successful, device activated. 
Aug  4 19:31:42 lauren-linux dhcdbd: Unrequested down ?:3
Aug  4 19:31:42 lauren-linux NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Aug  4 19:31:42 lauren-linux ntpdate[5881]: can't find host ntp.ubuntu.com 
Aug  4 19:31:42 lauren-linux ntpdate[5881]: no servers can be used, exiting
shippo752@lauren-linux:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



shippo752@lauren-linux:~$ ethtool -i eth0
driver: sky2
version: 1.20
firmware-version: N/A
bus-info: 0000:01:00.0

```

Sorry for the huge delay. 
I'm pretty sure I have a wireless router and a cable modem. 
This is probably irrelevant, but the ethernet cable is hooked up to the wireless router, and I take out the cable and hook it up to my laptop, which has the Linux on it. I'm not sure if I'm supposed to be doing that though :P

---

### Post by shippo752 on 2008-08-04
OMG HAAHAHA What a stupid mistake. 
Please disregard this entire thread! 
Haha. Wow. Okay so what happened was , after posting, I wondered how my other PC connected to the internet, and I realized that the ethernet cable I've been taking out and hooking into my Macbook was the WRONG END. 
Hahaha, well my internet browswer on the Linux is working perfectly fine now. 
Thanks so much for sticking by me the entire time, dannyboy. I'm sorry I wasted so much of your time.

---

### Post by dannyboy79 on 2008-08-05
> **shippo752 said:**
> OMG HAAHAHA What a stupid mistake. 
Please disregard this entire thread! 
Haha. Wow. Okay so what happened was , after posting, I wondered how my other PC connected to the internet, and I realized that the ethernet cable I've been taking out and hooking into my Macbook was the WRONG END. 
Hahaha, well my internet browswer on the Linux is working perfectly fine now. 
Thanks so much for sticking by me the entire time, dannyboy. I'm sorry I wasted so much of your time.

don't normally ask for this but could you hit the little blue ribbon with the star, that'll add a thanks to my helping people out column. A friend and I are in competition for who can help the most people before the weeks over.

---

### Post by editrix on 2008-08-05
> **dannyboy79 said:**
> don't normally ask for this but could you hit the little blue ribbon with the star, that'll add a thanks to my helping people out column. A friend and I are in competition for who can help the most people before the weeks over.

What a nice competition! You get a thanks from me just for having it.

---

