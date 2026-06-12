---
title: "HOWTO: Get wireless working in Hardy with Atheros 5418"
date: 2008-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by jerick70 on 2008-05-07
Hi Everyone,

I wanted to post what worked for me to get my Lenovo Thinkpad T60 working with WPA/WPA2 wireless and Hardy.  This information seems to be scattered all over the place so I thought I would compile it into a howto guide.  I will walk you through downloading and configuring the lastest Madwifi trunk, and WICD.  I used the r3616 of the Madwifi svn. I'm not sure if a newer svn will work. I prefer the WICD interface to Network Managers.  YMMV if tried with Network Manager.  I also haven't tried this in KDE. If there is anyone that wants to contribute to this or has a better way of doing this please give us your 2 cents.   Here are the steps:

Install prerequisites to download and build Madwifi 

  1) Install kernel headers, subversion and build-essential.  Open you favorite terminal program and enter the following code:

    ```
sudo aptitude install linux-headers-`uname -r` subversion build-essential
``` 

Download and install latest Madwifi svn. 

  2) Make directory to download latest svn into and download svn.
    
     ```
mkdir madwifi 
cd madwifi
svn checkout http://svn.madwifi.org/madwifi/trunk #This will take a while.

```
   
  3)Remove Madwifi drivers installed by Hardy

     ```
sudo ifconfig ath0 down
sudo ifconfig wifi0 down
#Repeat these 2 ifconfig lines for every MadWifi device you have
cd trunk/scripts
sudo ./madwifi-unload
sudo sh ./find-madwifi-modules.sh $(uname -r)
cd ..

```                           
  
  4) Install Madwifi

     ```
make
sudo make install
```

  5) Load Madwifi module and set module to start at boot

     ```
sudo modprobe ath_pci
sudo gedit /etc/modules 

```
     **the modules file only supports one device per line**
     Enter ath_pci on the last line of the file and save.

   6) Add WICD repository to Software Sources.

      Go to System -> Administration -> Software Sources
      Click on "Third-party Software" tab
      Click add.
      Add this for the "APT line" - deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
      Click "Add Source"
      Click "Close"
      Click "Reload"  #Be sure to reload or the next step will not work 
      
   7) Install WICD. #This will remove Network Manager.

      ```
sudo aptitude install wicd
```

   8) Load WICD gui at login

      Go to System -> Preferences -> Sessions
      Under the "Startup Programs" tab click "Add"
      Under name type "WICD" #without quotes
      Under command type "/opt/wicd/tray.py" #without quotes
      Click ok
      Load WICD without restarting ATL-F2 put this in the box /opt/wicd/tray.py and click run.

   9) Let's see if your new install is working
     ```
lspci -nn | grep Network
you should get this 03:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter [168c:0024] (rev 01) 

sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
you should get this 
driver=e1000
driver=ath_pci

sudo lsmod | grep ath_pci
you should get this 
ath_pci               241856  0 
wlan                  255008  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               281216  3 ath_rate_sample,ath_pci

```

   10) Connect to WPA/WPA2 access point

      ```
sudo gedit /opt/wicd/encryption/templates/wpa 
```
      Change this line psk=$_PSK to this line psk=$_KEY
      Go into the WICD Manager click on preferences and make sure that wext is the "WPA Supplicant Driver" and that ath0 is your "Wireless Interface".
      Check "Automatically Reconnect on Connection Loss"
      Click OK.
      Now click "Refresh" at the top and you should see your AP's name and all of the other APs close to your location. If your AP has a hidden SSID you will need to add the AP's name to WICD.  Just Click on the down arrow at the top of the WICD Manager next to "Network" and choose "Hidden Network" and follow the next directions.  You will need to add the PSK and any other settings necessary to connect to your particular AP.  Just click on the name of your AP and then Advanced and you can put all your settings in. 

You should be set to go now.  ENJOY!!!!

Jerick70

---

### Post by danbar on 2008-05-08
What do I need to change if I need to connect to my wireless router Edimax (WirelessG Braodband Router)  ?

---

### Post by danbar on 2008-05-08
What do I need to change (in the above instructions) to connect to a wireless router edimax ?

---

### Post by jerick70 on 2008-05-08
> **danbar said:**
> What do I need to change (in the above instructions) to connect to a wireless router edimax ?

Hi danbar,

I don't have experience with Edimax routers.  I would be happy to help though. I need a little more info from you though.  Are you receiving any errors while preforming the steps in the guide? What model Edimax router do you have?  How is the router setup? What wireless card are you using?

Jerick70

---

### Post by danbar on 2008-05-09
Thanks Jerick for answering. I'm not receiving any errors.  It's reacting as if the router does not exist. 

I went inside the settings of the router but couldn't get find information as to what model it is.  Maybe I missed something?

Secondly how would I know (through hardy) what network card do I have?

---

### Post by jerick70 on 2008-05-11
> **danbar said:**
> Thanks Jerick for answering. I'm not receiving any errors.  It's reacting as if the router does not exist. 

I went inside the settings of the router but couldn't get find information as to what model it is.  Maybe I missed something?

Secondly how would I know (through hardy) what network card do I have?

You can probably look on the bottom of your router to find the model number.  

I don't think you can see which card you have in Linux.  What output did you get with this code?

```
lspci -nn | grep Network
sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
sudo lsmod | grep ath_pci

```

Jerick70

---

### Post by danbar on 2008-05-11
thanks for your time!
 
The number written underneath the router is: 6114WG 4CE1000011

In the terminal the message that I found was: driver=b43-pci-bridge
driver=tg3

As I was looking for the b43cutter-011 in my harddisk I found it next to Documents, music, pictures etc....Maybe it's in the wrong place?  Maybe I need to change the path?

Thanks again.

---

### Post by jerick70 on 2008-05-11
> **danbar said:**
> thanks for your time!
 
The number written underneath the router is: 6114WG 4CE1000011

In the terminal the message that I found was: driver=b43-pci-bridge
driver=tg3

As I was looking for the b43cutter-011 in my harddisk I found it next to Documents, music, pictures etc....Maybe it's in the wrong place?  Maybe I need to change the path?

Thanks again.


Hi danbar,

Your welcome.  You have a Broadcom 4318 wireless chipset.  The drivers in this guide will not work with your wireless chipset.  They are for Atheros wireless based cards.  Here is a thread that will help:  [[COLOR="Red"]Broadcom BCM4318[/COLOR]]("http://ubuntuforums.org/showthread.php?t=738456")  The rest of the thread with the WICD install instructions should work.  Good luck in getting your wireless to work.

Jerick70

---

### Post by speed01 on 2008-06-03
Hmm...I have a 5418 in a T60. I followed your instructions and everything seemed to go OK except 1) the ...grep driver= gives me both e1000 and ath_pci;
2) ifconfig shows both ath0 and wifi0. wifi0 shows traffic but ath0 does not;
3) I can connect, but wicd reports "connected at 15%" when the signal is very strong; and
4) I can't ping my router.
The card works properly with windows.

---

### Post by jerick70 on 2008-06-03
> **speed01 said:**
> Hmm...I have a 5418 in a T60. I followed your instructions and everything seemed to go OK except 1) the ...grep driver= gives me both e1000 and ath_pci;
2) ifconfig shows both ath0 and wifi0. wifi0 shows traffic but ath0 does not;
3) I can connect, but wicd reports "connected at 15%" when the signal is very strong; and
4) I can't ping my router.
The card works properly with windows.

Hi speed01,

I am sorry to hear that you are having issues. :( I have changed the guide to include the report of the e1000 driver when running the grep driver= command.  Just to let you know the e1000 driver is the wrong driver for the T60 Intel NIC.  You can find how to install the correct drivers here: [http://whocares.de/2008/04/20/make-intels-8257x-based-gigabit-adapters-work-with-ubuntu-804-hardy-heron/](http://whocares.de/2008/04/20/make-intels-8257x-based-gigabit-adapters-work-with-ubuntu-804-hardy-heron/)  

A couple of questions.  What wireless router do you have? What version of the Madwifi drivers are you using?  Can you get to the internet when connected to your wireless router(I am guessing you can't)?

Jeff

---

### Post by speed01 on 2008-06-03
I am using a Linksys WAP54G access point connected to a DLink EBR-2310 router. WPA2-AES. I am using a fixed IP address to avoid complicating things with DHCP at this point. I am not sure how to determine the version of Madwifi driver that is in use -- please tell me and I will give you the version.
No, I cannot connect to the Internet with wireless now; as I said I can't even ping the router.

---

### Post by jerick70 on 2008-06-03
This will give you the version:

```
modinfo ath_pci | grep version
```

---

### Post by speed01 on 2008-06-04
svn r3693
srcversion F92E94FC0D46044415E370C

---

### Post by jerick70 on 2008-06-04
> **speed01 said:**
> svn r3693
srcversion F92E94FC0D46044415E370C

Well the version you have is the newest SVN from Madwifi.  I was using svn 3616, but I tested the 3695 svn and it works on my system. There are quite a few things that can be going wrong here.  Let's try 3 things that come to mind immediately.  

First - connect to your wireless network.  Then run ```
lsmod
iwconfig
ifconfig
```
Please post your output from all three.  There is a known issue with Avahi and Madwifi drivers that can cause this sort of problem.  Easy fix if this is the issue.  

Second - I am wondering if you may have an issue with your wpa_supplicant.  Let's look at your config in wicd.  Open the wicd gui and click Preferences at the top.  Please post a screen shot of this window.

Third - Do you have a hidden SSID on your wireless access point?  Sometime wicd has issues with hidden SSIDs.  

Wireless is a bit awkward in Unbuntu right now but fixable.  Be patient and we should be able to get you up and running.

Jeff

---

### Post by speed01 on 2008-06-04
Here is everything you asked for Jeff. I really appreciate your taking the time to help me with this.

vic@vic-1:~$ lsmod
Module                  Size  Used by
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
uinput                 10240  1
ipv6                  267780  12
ppdev                  10372  0
acpi_cpufreq           10796  2
cpufreq_powersave       2688  0
cpufreq_userspace       5284  0
cpufreq_conservative     8712  0
cpufreq_ondemand        9740  1
cpufreq_stats           7104  0
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5632  0
bay                     6912  0
dock                   11280  1 bay
sbs                    15112  0
sbshc                   7680  1 sbs
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
pcmcia                 40876  0
snd_hda_intel         344728  3
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
joydev                 13120  0
wlan_scan_sta          15872  1
snd_seq_dummy           4868  0
ath_rate_sample        16128  1
fglrx                1555468  23
snd_seq_oss            35584  0
ath_pci               241848  0
wlan                  236144  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               252640  3 ath_rate_sample,ath_pci
snd_seq_midi            9376  0
psmouse                40336  0
ac                      6916  0
battery                14212  0
serio_raw               7940  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
irtty_sir               9728  0
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  19856  0
sir_dev                17412  1 irtty_sir
output                  4736  1 video
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27276  1
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
thinkpad_acpi          51836  0
nsc_ircc               24208  0
button                  9232  0
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
evdev                  13056  10
nvram                   9992  2 thinkpad_acpi
soundcore               8800  1 snd
irda                  203068  3 irtty_sir,sir_dev,nsc_ircc
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  0
agpgart                34760  2 fglrx,intel_agp
crc_ccitt               3072  1 irda
pcspkr                  4224  0
sr_mod                 17956  0
ext3                  136712  1
cdrom                  37408  1 sr_mod
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
ata_generic             8324  0
sg                     36880  0
sd_mod                 30720  3
ata_piix               19588  0
usbhid                 31872  0
hid                    38784  1 usbhid
ahci                   28420  2
pata_acpi               8320  0
libata                159344  4 ata_generic,ata_piix,ahci,pata_acpi
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0
uhci_hcd               27024  0
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
e1000                 126016  0
thermal                16796  0
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3
vic@vic-1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"628318"  Nickname:""
          Mode:Managed  Frequency:5.66 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:626  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vic@vic-1:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:cf:a9:df:8f
          inet addr:192.168.0.241  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:78 (78.0 B)

eth0      Link encap:Ethernet  HWaddr 00:16:41:ad:21:83
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26603 (25.9 KB)  TX bytes:492 (492.0 B)
          Base address:0x3000 Memory:ee000000-ee020000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88900 (86.8 KB)  TX bytes:88900 (86.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-A9-DF-8F-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:985 errors:0 dropped:0 overruns:0 frame:62
          TX packets:1321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280
          RX bytes:110221 (107.6 KB)  TX bytes:59819 (58.4 KB)
          Interrupt:21

I haven't figured out how to do a screen capture in Linux yet, but the Preferences page of wicd has the following:

WPA supplicant driver: wext
Wireless interface ath0
Wired interface: eth0
Use global DNS servers - not checked
Always show wired interface - checked
Automatically reconnect on connection loss - checked
Enable debug mode - unchecked
Use dBm to measure signal strength - unchecked
Wired autoconnect setting - Use default profile

The advanced settings page in wicd for my wireless network shows

<ssid> WPA2
Automatically connect - checked
Use static IP's - checked
IP 192.168.0.241
Netmask 255.255.255.0
Gateway 192.168.0.1 (this is the router)
DNS1 192.168.0.1
Use Encryption - checked
WPA 1/2
Key (contains correct passphrase)

My AP's ssid is not hidden.

That's it.

---

### Post by speed01 on 2008-06-04
Here is everything you asked for Jeff. I really appreciate your taking the time to help me with this.

vic@vic-1:~$ lsmod
Module                  Size  Used by
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
uinput                 10240  1
ipv6                  267780  12
ppdev                  10372  0
acpi_cpufreq           10796  2
cpufreq_powersave       2688  0
cpufreq_userspace       5284  0
cpufreq_conservative     8712  0
cpufreq_ondemand        9740  1
cpufreq_stats           7104  0
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5632  0
bay                     6912  0
dock                   11280  1 bay
sbs                    15112  0
sbshc                   7680  1 sbs
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
pcmcia                 40876  0
snd_hda_intel         344728  3
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
joydev                 13120  0
wlan_scan_sta          15872  1
snd_seq_dummy           4868  0
ath_rate_sample        16128  1
fglrx                1555468  23
snd_seq_oss            35584  0
ath_pci               241848  0
wlan                  236144  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               252640  3 ath_rate_sample,ath_pci
snd_seq_midi            9376  0
psmouse                40336  0
ac                      6916  0
battery                14212  0
serio_raw               7940  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
irtty_sir               9728  0
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  19856  0
sir_dev                17412  1 irtty_sir
output                  4736  1 video
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27276  1
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
thinkpad_acpi          51836  0
nsc_ircc               24208  0
button                  9232  0
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
evdev                  13056  10
nvram                   9992  2 thinkpad_acpi
soundcore               8800  1 snd
irda                  203068  3 irtty_sir,sir_dev,nsc_ircc
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  0
agpgart                34760  2 fglrx,intel_agp
crc_ccitt               3072  1 irda
pcspkr                  4224  0
sr_mod                 17956  0
ext3                  136712  1
cdrom                  37408  1 sr_mod
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
ata_generic             8324  0
sg                     36880  0
sd_mod                 30720  3
ata_piix               19588  0
usbhid                 31872  0
hid                    38784  1 usbhid
ahci                   28420  2
pata_acpi               8320  0
libata                159344  4 ata_generic,ata_piix,ahci,pata_acpi
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0
uhci_hcd               27024  0
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
e1000                 126016  0
thermal                16796  0
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3
vic@vic-1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"628318"  Nickname:""
          Mode:Managed  Frequency:5.66 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:626  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vic@vic-1:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:cf:a9:df:8f
          inet addr:192.168.0.241  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:78 (78.0 B)

eth0      Link encap:Ethernet  HWaddr 00:16:41:ad:21:83
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26603 (25.9 KB)  TX bytes:492 (492.0 B)
          Base address:0x3000 Memory:ee000000-ee020000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88900 (86.8 KB)  TX bytes:88900 (86.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-A9-DF-8F-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:985 errors:0 dropped:0 overruns:0 frame:62
          TX packets:1321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280
          RX bytes:110221 (107.6 KB)  TX bytes:59819 (58.4 KB)
          Interrupt:21

I haven't figured out how to do a screen capture in Linux yet, but the Preferences page of wicd has the following:

WPA supplicant driver: wext
Wireless interface ath0
Wired interface: eth0
Use global DNS servers - not checked
Always show wired interface - checked
Automatically reconnect on connection loss - checked
Enable debug mode - unchecked
Use dBm to measure signal strength - unchecked
Wired autoconnect setting - Use default profile

The advanced settings page in wicd for my wireless network shows

<ssid> WPA2
Automatically connect - checked
Use static IP's - checked
IP 192.168.0.241
Netmask 255.255.255.0
Gateway 192.168.0.1 (this is the router)
DNS1 192.168.0.1
Use Encryption - checked
WPA 1/2
Key (contains correct passphrase)

My AP's ssid is not hidden.

That's it.

---

### Post by jerick70 on 2008-06-04
Hi again Speed01,

You are welcome, I am glad to help.

Everything looks good from your output.  Let's check if wpasupplicant is installed and configured correctly.

Run this to check if wpasupplicant is installed
```
dpkg -l | grep wpasupplicant
```

STOP: If you get output post it here if you don't go on. 

If nothing is returned and you are kicked back to the prompt it is not installed.  If this is the cases run this command to install it:
*You will need to be connected to the internet to install.*
```
sudo aptitude install wpasupplicant
```

And then run this to setup wpasupplicant:
```
sudo wpa_supplicant -Bw -Dwext -iath0 -c /etc/wpa_supplicant/wpa_supplicant.conf

```   

Jeff

---

### Post by speed01 on 2008-06-04
Response was
ii  wpasupplicant                              0.6.0+0.5.8-0ubuntu2                Client support for WPA and WPA2 (IEEE 802.11

Then I ran the setup code as given. There was no error.

However, it's still the same. It will connect at 0% (or sometimes 15%) but I can't reach the router.

---

### Post by jerick70 on 2008-06-04
> **speed01 said:**
> Response was
ii  wpasupplicant                              0.6.0+0.5.8-0ubuntu2                Client support for WPA and WPA2 (IEEE 802.11

Then I ran the setup code as given. There was no error.

However, it's still the same. It will connect at 0% (or sometimes 15%) but I can't reach the router.

Ok we have ruled out Avahi, wpasupplicant, and driver install. Let's look at your interfaces config file to make sure there is not an issue there.
```
gksudo gedit /etc/network/interfaces
```

Make sure that the only lines in this file are 
auto lo
iface lo inet loopback

If there is anything else please comment it out or delete it.

---

### Post by speed01 on 2008-06-04
auto lo
iface lo inet loopback

This is the entire contents of the file.

---

### Post by jerick70 on 2008-06-04
> **speed01 said:**
> auto lo
iface lo inet loopback

This is the entire contents of the file.

Ok...let's look at the wpa template for WICD and make sure the settings are correct:
```
sudo gedit /opt/wicd/encryption/templates/wpa
```

Please post the entire file.

---

### Post by speed01 on 2008-06-05
This may be it. My AP is set for AES, not TKIP.
file contents:

name = WPA 1/2
author = Adam Blackburn
version = 1
require key *Key
-----
network={
       ssid="$_ESSID"
       scan_ssid=$_SCAN
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=$_KEY
}

---

### Post by jerick70 on 2008-06-05
> **speed01 said:**
> This may be it. My AP is set for AES, not TKIP.
file contents:

name = WPA 1/2
author = Adam Blackburn
version = 1
require key *Key
-----
network={
       ssid="$_ESSID"
       scan_ssid=$_SCAN
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=$_KEY
}

This is how it should look according to my tutorial.  CCMP is the protocol that allows the use of AES for wireless under WPA2.  This is acting like you are not able to authenticate the preshared key.  Let's do this...change the line that I had you switch psk=$_KEY back to psk=$_PSK and see how that works.  I would try it with DHCP and not as a static ip. You may have to click "connect" a couple of time to get it to work.

---

### Post by speed01 on 2008-06-05
"Let's do this...change the line that I had you switch psk=$_KEY back to psk=$_PSK and see how that works. "

Yesss! That did it. It connected right away (I'm still using a fixed IP address), and I'm sending this reply with the ethernet cable unplugged! Thanks for struggling with this.

---

### Post by jerick70 on 2008-06-05
> **speed01 said:**
> "Let's do this...change the line that I had you switch psk=$_KEY back to psk=$_PSK and see how that works. "

Yesss! That did it. It connected right away (I'm still using a fixed IP address), and I'm sending this reply with the ethernet cable unplugged! Thanks for struggling with this.

SWEET!!!!  You are welcome.  Glad we got you up and going.  Just for my info and troubleshooting later what is the pass phrase you use?  Send it to jerick70 at msn dot com so it isn't posted on the forum.

---

### Post by cudaman73 on 2008-06-08
I had followed this guide for getting my 5418 to work in Hardy on wubi.. and wireless was working fine.

I installed Hardy on my spare laptop drive, and now I can't get it to work. I have tried several different versions of madwifi (the latest stable and latest svn build). I discovered that, upon boot, wicd (or even network-manager, for that matter), will initially detect wireless networks, but, after that, if i try to connect to one, or even try to scan again, it stops detecting any wireless networks. the driver is working fine, save for the fact that it can't see any networks.

I need help. And a cigarette. :confused:

---

### Post by cudaman73 on 2008-06-11
bump :(

I've now tried it in Gutsy as well, so I believe it's either a hardware problem (though it works fine in vista) or a madwifi problem.

---

### Post by jerick70 on 2008-06-11
> **cudaman73 said:**
> bump :(

I've now tried it in Gutsy as well, so I believe it's either a hardware problem (though it works fine in vista) or a madwifi problem.

Hi cudaman73,

This sounds like a driver issue.  What version of Madwifi are you using?  This could also be an issue with Avahi.  Madwifi and Avahi have issues on some systems.  You can check if it is Avahi related by running ifconfig at a command prompt.  If there is a device that says avahi:ath0 then this is most likely your issue.  

Jeff

---

### Post by cudaman73 on 2008-06-11
> **jerick70 said:**
> Hi cudaman73,

This sounds like a driver issue.  What version of Madwifi are you using?  This could also be an issue with Avahi.  Madwifi and Avahi have issues on some systems.  You can check if it is Avahi related by running ifconfig at a command prompt.  If there is a device that says avahi:ath0 then this is most likely your issue.  

Jeff

Running the latest svn commit... i think (3717)... i believe that it could be an issue with avahi... i need to put the hard drive back into my laptop so i can troubleshoot it some more :/

if it is, if you have any links and/or information, i'd be glad to have it. perhaps save me more hours of googling. :/

---

### Post by jerick70 on 2008-06-12
The Avahi issue can be fixed by uninstalling or disabling Avahi.  I had to do this on my T60 to get wireless working.  Here is an example of the bug if you want to read about it:  [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/97685](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/97685).  But before you mess with Avahi I would look at other options. 

What does your ifconfig and iwconfig look like?

---

### Post by cudaman73 on 2008-06-12
on a fresh boot, we have the output of ifconfig:

```
ath0      Link encap:Ethernet  HWaddr 00:1B:9E:7E:D2:06  
          inet6 addr: fe80::21b:9eff:fe7e:d206/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:8F:EC:C2  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe8f:ecc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38565241 (36.7 MB)  TX bytes:1268267 (1.2 MB)
          Interrupt:17 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-7E-D2-06-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:2294 (2.2 KB)  TX bytes:1330 (1.2 KB)
          Interrupt:18 

```

and iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:21  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

that's odd. It appears that ath0:avahi appears and disappears. I have seen it before.

The biggest problem is just that it won't scan and/or connect to an access point. Sometimes it will detect them on boot (wicd will show either just my AP or mine and the surrounding APs), but I can't connect to any, and when I try, if I scan again, either through wicd or iwlist or wlanconfig, it goes back to not showing any scan results. I have tried it with eth0 both up and connected, and shutdown and without a cable plugged into it. I'm tearing my hair out here :/

---

### Post by cudaman73 on 2008-06-12
I'd just like to let you know that I've gotten wireless to work flawlessly.

Turns out I was having a problem with my BIOS not reporting an age for ACPI, so it wasn't being enabled during boot. forcing ACPI to enable during boot-time has solved the problem. I am posting this without a wire.

For other people having this problem, I had to add "acpi=force" to my kernel line in /boot/grub/menu.lst.

---

### Post by jerick70 on 2008-06-12
Good to hear you got this working.  For everyone's benefit, what laptop do you have?

---

### Post by cudaman73 on 2008-06-12
> **jerick70 said:**
> Good to hear you got this working.  For everyone's benefit, what laptop do you have?

It's a Toshiba Satellite A215-S8522.

---

### Post by dfechete on 2008-06-14
madwifi.org seems to be down since yesturday or two days ago from what i read... and i need madwifi-ng-r2756+ar5007.tar.gz can anyone help me? also i might need madwifi-ng. 


please email me at [email]daniel.fechete@gmail.com[/email]

thanks.

---

### Post by CH1C0 on 2008-06-15
Hi, I just found this thread and i cant continue past where i need to download svn with  svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk)

the output i get is as follows:

svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname ([http://svn.madwifi.org](http://svn.madwifi.org))

I don't know what to do. Help would be very appreciated.
Thank you.

---

### Post by jerick70 on 2008-06-15
> **CH1C0 said:**
> Hi, I just found this thread and i cant continue past where i need to download svn with  svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk)

the output i get is as follows:

svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname ([http://svn.madwifi.org](http://svn.madwifi.org))

I don't know what to do. Help would be very appreciated.
Thank you.

Hi CH1CO,

The Madwifi site is down.  Give me your email and I will send you 3693 svn of Madwifi.

Jeff

---

### Post by CH1C0 on 2008-06-15
Thanks. my email is (edit) I'll private message it.

---

### Post by jerick70 on 2008-06-15
> **CH1C0 said:**
> Thanks. my email is (edit) I'll private message it.

The drivers are to large to send as an attachment.  It looks like the svn is up now though.  I think they have changed the svn.  Try this to downlaod the newest drivers:

```
svn checkout http://svn.madwifi.org/madwifi/trunk madwifi
``` 

I will change the guide to reflect the change. Let me know if this works for you.

Jeff

---

### Post by CH1C0 on 2008-06-15
I got the same result. Is there a certain repository I don't know about or something?

---

### Post by jerick70 on 2008-06-15
> **CH1C0 said:**
> I got the same result. Is there a certain repository I don't know about or something?

No there isn't a repository for this.  This must be a DNS server issue of some sort.  Here, let me use 7-zip to archive this and I will email.

---

### Post by CH1C0 on 2008-06-16
Thank you ever so much. It s working now. Is there a way to remaster a custom ubuntu to a CD so I dont have to go throuh this again?

---

### Post by jerick70 on 2008-06-16
> **CH1C0 said:**
> Thank you ever so much. It s working now. Is there a way to remaster a custom ubuntu to a CD so I dont have to go throuh this again?

Hi CH1CO,

Yes there is a way to slipstream your custom Ubuntu drivers, progarms, and settings into a live CD with remastersys.  I have not done this before so your milage may very. Here is a linky, [remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys"), to a howto guide.  This guide is for Gutsy but will work with Hardy.  Be sure to read the comments below the guide for changes to the repository deb line and how to get it to work with Hardy. 

Jeff

---

### Post by CH1C0 on 2008-06-17
It seems that everytime ubuntu updates its self i lose wireless so I go through this guide and it comes back. I have printed it out and backed up that madwifi folder on a flash drive. So annoying to go through this everytime i get updates, but still, it's a lot better than window's constant BS.

---

### Post by CH1C0 on 2008-06-17
Oh, I think I'll wait until an official guide to re master hardy to come out. I want to make it a wifi-friendly version with every driver I can find and see about making a pretty little GUI for it. Is that an unrealistic goal. BTW, I'm still pretty new but I'm learning lots every day.

---

### Post by jerick70 on 2008-06-17
> **CH1C0 said:**
> It seems that everytime ubuntu updates its self i lose wireless so I go through this guide and it comes back. I have printed it out and backed up that madwifi folder on a flash drive. So annoying to go through this everytime i get updates, but still, it's a lot better than window's constant BS.

Hi CH1CO,

This is normal when you update the kernel.  Any drivers that you install from source will not be built into the new kernel.  You should just have to run the removal script, recompile the madwifi drivers and run modprobe to get  wireless back.

Jeff

---

### Post by jerick70 on 2008-06-17
> **CH1C0 said:**
> Oh, I think I'll wait until an official guide to re master hardy to come out. I want to make it a wifi-friendly version with every driver I can find and see about making a pretty little GUI for it. Is that an unrealistic goal. BTW, I'm still pretty new but I'm learning lots every day.

No, this is not an unrealistic goal at all.  You can do just about anything you want with linux.  You may want to check out the Ultimate Edition of Ubuntu.  It has almost everything built in.  TheeMahn is excellent at what he does and posts source code for his project.  This is my favorite distro. Check out the forum for sources and info on the distro.  Linky - [Ubuntu Ultimate]("http://ultimateedition.info/")

It is always good to learn.  I have been using Ubuntu for many years and I am still learning new things.  The great thing about ubuntu is it is for the newbee.  The community has all sorts of howto's for beginner and advanced users and everyone in between.  Welcome to the community.

---

### Post by Frunktz on 2008-06-17
Hi!
I've used that procedure, but with WG511T (Atheros chipset) I cannot connect to WPA1-2 networks...

---

### Post by jerick70 on 2008-06-17
> **Frunktz said:**
> Hi!
I've used that procedure, but with WG511T (Atheros chipset) I cannot connect to WPA1-2 networks...

Hi Frunktz,

The Netgear WG511T is based on the 5212 Atheros chipset.  It is a little different than the 5418.  Let's see what I can do to help.  :)I just happen to have a WG511T.  It works when I plug it in.  

A few questions so we can troubleshoot.  

1) Does the light come on on the WG511T?

2) What output do you get when you type ```
lspci -nn | grep Atheros
```

3) What is the key you are using for WPA1/2?  You can PM the key to me.

Thanks,
Jeff

---

### Post by CH1C0 on 2008-06-19
Stupid computer updated again and this time my internet slowed down to dial up speed. The solution? I picked up the cheapest most generic USB wireless thingie I could find and viola, 600 plus KB/s downloads (change from ath0 to eth1). I've found that to be the case with Linux, generic stuff works better, I think because it doesn't have big name drivers with Windows hard coded into them. I've experienced this already with web cams, game pads, printers, digital cameras,(I finally discovered the SD slot on my laptop so that don't matter now, hehe), and now WIFI. I don't know about y'all but from now on when I buy stuff, it's gonna have Nexxtech or Retail Plus branded on it. Or is it just coincidence? Anyways, rawk on Ubuntu dudes. :guitar:

---

### Post by CH1C0 on 2008-06-19
HAHA, I just discover my neighbor has WPA2 security but no password or anything, I connect right to it. LOL, should I cancel my internet service? Just kidding, but how do you enable WPA2 security? My router is wide open.

---

### Post by jerick70 on 2008-06-19
> **CH1C0 said:**
> HAHA, I just discover my neighbor has WPA2 security but no password or anything, I connect right to it. LOL, should I cancel my internet service? Just kidding, but how do you enable WPA2 security? My router is wide open.

Hi CH1CO,

What router do you have?

Jeff

---

### Post by Frunktz on 2008-06-19
I use WPA1.
Yes the lights are up and it show the wifi networks...

But I can't connect using WPA..

---

### Post by jerick70 on 2008-06-19
> **Frunktz said:**
> I use WPA1.
Yes the lights are up and it show the wifi networks...

But I can't connect using WPA..

Can you answer the question below. I am wondering if you need to change your WICD wpa_supplicant config file.  One of the other users on the forum had a similar issue and we changed the variable psk=$_KEY in /opt/wicd/encryption/templates/wpa back to psk=$_PSK and this fixed his issue.    

What is the key you are using for WPA1/2? You can PM the key to me.

Thanks,
Jeff

---

### Post by CH1C0 on 2008-06-20
> **jerick70 said:**
> Hi CH1CO,

What router do you have?

Jeff

I have a linksys compact wireless g.

---

### Post by CH1C0 on 2008-06-20
Oh, and with my usb card the problem is solved. Thank you. :guitar:

---

### Post by Frunktz on 2008-06-20
> **jerick70 said:**
> Can you answer the question below. I am wondering if you need to change your WICD wpa_supplicant config file.  One of the other users on the forum had a similar issue and we changed the variable psk=$_KEY in /opt/wicd/encryption/templates/wpa back to psk=$_PSK and this fixed his issue.    

What is the key you are using for WPA1/2? You can PM the key to me.

Thanks,
Jeff

Hi used that temporany wpa key: "temp wpa key 123" (without quotes but with spaces)

I've also change _KEY with _PSK and viceversa. Using _PSK I've got WICD that stall...

---

### Post by jerick70 on 2008-06-21
> **CH1C0 said:**
> Oh, and with my usb card the problem is solved. Thank you. :guitar:

I'm glad to hear it is working for you.  Some Atheros cards are a pain with Linux.  Especially the 5418.

---

### Post by jerick70 on 2008-06-21
> **Frunktz said:**
> Hi used that temporany wpa key: "temp wpa key 123" (without quotes but with spaces)

I've also change _KEY with _PSK and viceversa. Using _PSK I've got WICD that stall...

So is it working now?

---

### Post by Frunktz on 2008-06-22
No, the problem remains...

I think I've found the problem..
The WPA KEY....madwifi seems to have problem with password with spaces..
So the key: "temp wpa key 123" don't work..
instead "tempwpakey123" works with _PSK....

Very weird..
Anyone with that problem or can test it?

---

### Post by NullHead on 2008-07-04
Is there an off-line version of this guide?

---

### Post by jerick70 on 2008-07-04
> **NullHead said:**
> Is there an off-line version of this guide?

I haven't created one yet.  You could make your own by copying the guide and pasting it into a text editor.  

Jeff

---

### Post by NullHead on 2008-07-05
That's not exactly what I meant. Is there a way to install madwifi using the basic files that are on the cd? For example, can I put in the cd, install ubuntu, and then install madwifi with the files that are included with the cd? 

I have a D-Link dwa-556 and I have no other way of getting internet access ... so I need to be able to install madwifi with out internet.

---

### Post by jerick70 on 2008-07-05
> **NullHead said:**
> That's not exactly what I meant. Is there a way to install madwifi using the basic files that are on the cd? For example, can I put in the cd, install ubuntu, and then install madwifi with the files that are included with the cd? 

I have a D-Link dwa-556 and I have no other way of getting internet access ... so I need to be able to install madwifi with out internet.

I didn't understand your last message.  No there isn't a way to do this off the cd.  The madwifi drivers included on the CD are old versions that do not support the newer Atheros chipsets, and the wicd package isn't included.  I can email a zipped copy of WICD and the madwifi drivers to you, and you can install that way.  PM your email address and I will send it.

---

### Post by NullHead on 2008-07-05
See I have a working version of Vista that I can use to download these basic files, but the problem is that, when I go to install madwifi I cannot compile it from the files on the live cd ... so what I really need is a library of the files needed to get me connected to the internet. 

If you can do this, then I'll gladly PM you my email address ;)

---

### Post by jerick70 on 2008-07-05
The only other things you will need to install are the kernel headers, and build-essential.  I would install subversion also so you can download newer svn builds of madwifi in the future.  You can download all of this from Windows and then copy the packages to your Linux drive using the Ext2 IFS drivers.  You can download Ext2 IFS here [Ext2 IFS Drivers]("http://www.fs-driver.org/") You can get the the Ubuntu packages from [Ubuntu Packages Website]("http://packages.ubuntu.com/hardy/").  You will have to search for each package separately.  When you find the packages it will tell you what dependencies you need for the installs and it includes links to the packages.  The site is down right now though. You can download the .deb wicd package from [wicd sourceforge page]("https://sourceforge.net/project/showfiles.php?group_id=194573").  You will need to use a program like [tortiseSVN]("http://tortoisesvn.net/downloads") to download the svn packages for madwifi.  If you need any help with any of this I can post more detail.

---

### Post by jerick70 on 2008-07-08
> **NullHead said:**
> See I have a working version of Vista that I can use to download these basic files, but the problem is that, when I go to install madwifi I cannot compile it from the files on the live cd ... so what I really need is a library of the files needed to get me connected to the internet. 

If you can do this, then I'll gladly PM you my email address ;)

Hi NullHead,

Did you get this installed?  The package website is up now.

Jeff

---

### Post by NullHead on 2008-07-08
I have not. The problem is, I'm too busy to give it a real hard try and I'm also too lazy to give it some real effort when I do have time. :lolflag:

call it failure from natural causes. 

:lolflag:

---

### Post by jerick70 on 2008-07-08
> **NullHead said:**
> I have not. The problem is, I'm too busy to give it a real hard try and I'm also too lazy to give it some real effort when I do have time. :lolflag:

call it failure from natural causes. 

:lolflag:

LOL :biggrin: 

That is too funny!  I needed a good laugh tonight. 

Good luck in getting it to work.  If you have any more questions please let me know.

---

### Post by NullHead on 2008-07-09
> **jerick70 said:**
> LOL :biggrin: 

That is too funny!  I needed a good laugh tonight. 

Good luck in getting it to work.  If you have any more questions please let me know.

I'm glad I could help you out :D

I'm actually, right now, trying to figure out the .debs needed to get these files and compilation abilities on a fresh install. 

I'll let you know how it goes. 

Also, I'll package up all the .debs so everyone else can download this package to install offline. :popcorn:

---

### Post by NullHead on 2008-07-09
Well ... I failed again. 

It says I need some configured kernel sources. I don't have enough resources to get those "configured kernel sources" for my ubuntu studio real time kernel. I even went to the #ubuntustudio channel and they were stumped. 

If you have any more ideas?

---

### Post by jerick70 on 2008-07-09
> **NullHead said:**
> Well ... I failed again. 

It says I need some configured kernel sources. I don't have enough resources to get those "configured kernel sources" for my ubuntu studio real time kernel. I even went to the #ubuntustudio channel and they were stumped. 

If you have any more ideas?

Hmmmm.  I am not familiar with Ubuntu Studio.  But I will help.  I am sure we can figure this out.:)  Linux is a predictable beast...but a beast at that.  It sounds like you may be missing the kernel headers, so let's take a stab at it. 

What kernel version are you running?  You can get this by typing this code at a command prompt:

```
uname -a
```


Also, will you post the exact error message so I can wrap my head around it.

This info should give me a good start. 

Thanks

---

### Post by NullHead on 2008-07-09
Ok I'll go along with it ;) FYI I am familiar with linux commands.
NOTE: this computer is off-line ... so I typed everything out from what I can see on the other computer. I'm using my laptop to type this to you. 
> jon@ubuntu-studio:~/Desktop/madwifi-0.9.4$ uname -a
Linux Ubuntustudio 2.6.24-16-rt #1 SMP PREEMPT RT Thu Apr 10 14:04:43 UTC 2008 x86_64 GNU/Linux
jon@ubuntustudio:~/Desktop/madwifi-0.9.4$ _

---

### Post by jerick70 on 2008-07-09
> **NullHead said:**
> Ok I'll go along with it ;) FYI I am familiar with linux commands.
NOTE: this computer is off-line ... so I typed everything out from what I can see on the other computer. I'm using my laptop to type this to you.

I get that you know Linux now. Hey, you never know who knows what on these boards.

Did you download all of the dependencies and the linux-headers package on the Ubuntu packages site and install them?  Here is the site:  [linux-headers-2.6.24-16-rt]("http://packages.ubuntu.com/hardy/linux-headers-2.6.24-16-rt")

Also, here is the site for build-essential [build-essential]("http://packages.ubuntu.com/hardy/build-essential")

---

### Post by NullHead on 2008-07-09
Yes I have these installed. The headers, actually, came pre-installed with Ubuntu Studio.

---

### Post by jerick70 on 2008-07-10
> **NullHead said:**
> Yes I have these installed. The headers, actually, came pre-installed with Ubuntu Studio.

I see.  Well then... what is the exact error you are getting?

---

### Post by max69 on 2008-08-01
Hi guys,
I tried this howto after a fresh install as even after I removed ndiswrapper it still caused problem with wlan0 and ath0 (maybe aliases). It is all good and I am at last rid of ndiswrapper ruining battery life on my laptop. The only problem is I cant connect with wpa-psk. I have disabled avahi-daemon and tried with both PSK and Key but to no avail. However I have no problem with WEP or open network. Any clues? Do you need specific information? I'll be more than happy to provide them for you. Thanks in advance

---

### Post by NullHead on 2008-08-01
> **jerick70 said:**
> I see.  Well then... what is the exact error you are getting?

Sorry for not responding, I forgot to get the exact code, but I gave up anyways. I have a working install of Ubuntu. I was just trying to test out ubuntu studio for a friend, but it would seem that I was unable to get it on teh interwebs. 

Thanks for your help.

---

### Post by max69 on 2008-08-04
Well never mind guys, I decided to go back to the ndiswrapper solution as the madwifi driver is just too unstable for me (only conntects when it wants too, poor reception, connection loss). Hope it gets better in the near future. Good luck with it!

---

### Post by jerick70 on 2008-08-07
> **NullHead said:**
> Sorry for not responding, I forgot to get the exact code, but I gave up anyways. I have a working install of Ubuntu. I was just trying to test out ubuntu studio for a friend, but it would seem that I was unable to get it on teh interwebs. 

Thanks for your help.

Hey no problem.  Good thing that you have a vanilla install of Ubuntu running.

---

### Post by jerick70 on 2008-08-07
> **max69 said:**
> Well never mind guys, I decided to go back to the ndiswrapper solution as the madwifi driver is just too unstable for me (only conntects when it wants too, poor reception, connection loss). Hope it gets better in the near future. Good luck with it!

Hi max69,

Madwifi is running stable on my x64 install of Ubuntu.  It could be the newest drivers.  I am using an older version of madwifi, svn 6393.  Madwifi seems to regress to past problems at times while they are trying to fix other issues.  The issues with Atheros 5418 (and a lot of the newer chipsets) cards has been around on and off for quite a few years.  If you would like I can email the working drivers to you.  PM your email to me if interested.

Jerick70

---

### Post by mnj1979 on 2008-09-14
Hello everyone,

 I have atheros 5418 and installed madwifi. The problem is that I can see all wireless networks but upon trying to connect, connection fails. Here is my config
 iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:62095  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
It appears that in ath0 link quality is 0/70

---

### Post by jerick70 on 2008-09-15
> **mnj1979 said:**
> Hello everyone,

 I have atheros 5418 and installed madwifi. The problem is that I can see all wireless networks but upon trying to connect, connection fails. Here is my config
 iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:62095  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
It appears that in ath0 link quality is 0/70

Hi,

I need a like more information here to help you with this.  Did you follow the guide in this thread to install your drivers? 

Jeff

---

