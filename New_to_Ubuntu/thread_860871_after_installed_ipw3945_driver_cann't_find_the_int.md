---
title: "after installed ipw3945 driver cann't find the interfaces in hardy"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Anjue on 2008-07-16
I tried to used ipw3945 instead of iwl3945 but after this I tried to up the interfaces I got this messages

```
sudo ifup eth1
eth1: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'eth1' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
Failed to disable WPA in the driver.
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```

but when I look in to the log I got this

```
Jul 16 09:15:50 ARX-7 kernel: [  773.318348] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jul 16 09:15:50 ARX-7 kernel: [  773.318497] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100102, writing 100106)
Jul 16 09:15:50 ARX-7 kernel: [  773.364365] Registered led device: iwl-phy0:RX
Jul 16 09:15:50 ARX-7 kernel: [  773.364389] Registered led device: iwl-phy0:TX
```

This is My lsmod result

```
Module                  Size  Used by
ipw3945               199072  0 
ieee80211              35528  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
nfsd                  228848  13 
lockd                  67720  2 nfsd
nfs_acl                 4608  1 nfsd
auth_rpcgss            43424  1 nfsd
sunrpc                185500  9 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                6016  1 nfsd
ppdev                  10372  0 
acpi_cpufreq           10796  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  2 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
af_packet              23812  2 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
ieee1394               93752  1 sbp2
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
usb_storage            73664  1 
libusual               19108  1 usb_storage
ipv6                  267780  16 
snd_hda_intel         344728  6 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
usbhid                 31872  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
hid                    38784  1 usbhid
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
battery                14212  0 
ac                      6916  0 
fglrx                1555468  23 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
video                  19856  0 
output                  4736  1 video
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                40336  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  19076  0 
button                  9232  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ricoh_mmc               4352  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  22 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mmc_core               51460  1 sdhci
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
wmi_acer                9644  1 acer_acpi
evdev                  13056  7 
soundcore               8800  1 snd
intel_agp              25492  0 
agpgart                34760  2 fglrx,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  7 
pata_acpi               8320  0 
ata_piix               19588  4 
8139cp                 24704  0 
ata_generic             8324  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  6
```

This is my ifconfig result commands

```
anjue@ARX-7:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:43:b1:16  
          inet addr:10.254.2.2  Bcast:10.254.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe43:b116/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229465 errors:27 dropped:51 overruns:27 frame:0
          TX packets:129869 errors:0 dropped:0 overruns:4 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:252586788 (240.8 MB)  TX bytes:17948287 (17.1 MB)
          Interrupt:20 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21163487 (20.1 MB)  TX bytes:21163487 (20.1 MB)
```

---

### Post by framinglory on 2008-07-16
could you type "lsmod" (without the quotes) in a terminal and tell me the results? Also, posting the results of 
ifconfig 
would help too.

---

### Post by framinglory on 2008-07-16
edit: first type iwconfig into a terminal, to make sure that eth0 is not your wireless card. If it says "eth0 no wireless extensions" then it is not. If it does return some information about wireless, ignore what i said below and use eth0 instead of eth1 in the steps you were following when you got the eth1 error.

did you first blacklist the newer iwl driver? add these lines
blacklist iwl3945
blacklist mac8021
to /etc/modprobe.d/blacklist, and then reboot to make sure this takes effect.

Also, ipw3945 has a daemon that might not be set to run on start up, use the command 
sudo /etc/init.d/ipw3945d start
to start it. and
ps -C ipw3945d
to see if it is running

If it is not starting automatically, then add these two lines to /etc/modprobe.d/ipw3945
install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; \
sleep 0.5 ; /sbin/ipw3945d --quiet

remove ipw3945  /sbin/ipw3945d --kill ; \
/sbin/modprobe -r --ignore-remove ipw3945

---

