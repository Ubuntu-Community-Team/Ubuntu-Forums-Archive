---
title: "Can't Access Internet After 11.10 Software Update"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by doppel.ganger on 2011-09-21
I just did a fresh install of 11.10 Beta 1. Whenever I do a fresh install of any OS, the first thing that I do is check for and install any updates, which I did. After rebooting, I noticed the Power Cog switched back to its old design and there was no Internet icon. I thought that all of this was part of the update. I then launched Firefox to install Chrome. No connection on ANY site. I tried launching the network setup program from the Dash, but it wouldn't load. Then I went to the System Settings through the Power Cog and (tried) to launch Network Settings. It didn't work either. Then I unplugged the Ethernet cable and reinserted it. Nothing. I know for a fact that this is NOT a hardware issue because I am typing this on the SAME computer from a 11.10 Beta 1 LiveCD. I am completely LOCKED out of all Internet-related software except Firefox, in which there is no connection anyway. HHHEEELLLPPP!!!](*,)

-DG

---

### Post by josephmills on 2011-09-21
ok get a cd or a pen drive ready 
open terminal and type in 
```
lspci -nn
```\
```
lsmod 
```
```
rfkill list all 
```
```
sudo lshw -c network
```
then copy and paste into your text editor save file and put on pen drive or cd then boot what ever it is that you are typing on now and paste  the code to here using the cd/pendrive

---

### Post by coffeecat on 2011-09-21
*Thread moved to **Ubuntu +1 (Oneiric Ocelot)**.*

---

### Post by oasick on 2011-09-21
> **doppel.ganger said:**
> I just did a fresh install of 11.10 Beta 1. Whenever I do a fresh install of any OS, the first thing that I do is check for and install any updates, which I did. After rebooting, I noticed the Power Cog switched back to its old design and there was no Internet icon. I thought that all of this was part of the update. I then launched Firefox to install Chrome. No connection on ANY site. I tried launching the network setup program from the Dash, but it wouldn't load. Then I went to the System Settings through the Power Cog and (tried) to launch Network Settings. It didn't work either. Then I unplugged the Ethernet cable and reinserted it. Nothing. I know for a fact that this is NOT a hardware issue because I am typing this on the SAME computer from a 11.10 Beta 1 LiveCD. I am completely LOCKED out of all Internet-related software except Firefox, in which there is no connection anyway. HHHEEELLLPPP!!!](*,)

-DG

I had this problem too, but now works with this solution:

From a terminal open interfaces file
 
sudo gedit /etc/network/interfaces
 
add the following two lines if missing
 
 
auto eth0
iface eth0 inet dhcp
 
 
restart networking
 
sudo /etc/init.d/networking restart


I hope that works for you too ;)

---

### Post by doppel.ganger on 2011-09-21
These commands were run NOT from the CD but from the Ubuntu 11.10 Beta 1 on the Hard Drive itself.
```
                                  thomas@Thomas-Ubuntu:~$ lsmod
 Module                  Size  Used by
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17308  1  
 fat                    55577  1 vfat
 usb_storage            44173  1  
 uas                    17699  0  
 nls_utf8               12493  1  
 isofs                  39549  1  
 bnep                   17923  2  
 rfcomm                 38408  8  
 ppdev                  12849  0  
 snd_usb_audio         100880  1  
 snd_hwdep              13276  1 snd_usb_audio
 snd_usbmidi_lib        24558  1 snd_usb_audio
 snd_seq_midi           13132  0  
 snd_intel8x0           33318  2  
 snd_ac97_codec        106082  1 snd_intel8x0
 ac97_bus               12642  1 snd_ac97_codec
 snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
 dcdbas                 14098  0  
 snd_pcm                80468  3 snd_usb_audio,snd_intel8x0,snd_ac97_codec
 snd_seq_midi_event     14475  1 snd_seq_midi
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
 snd_timer              28932  2 snd_pcm,snd_seq
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
 nouveau               663211  2  
 snd                    55902  16 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_intel8x0,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
 uvcvideo               67271  0  
 psmouse                73673  0  
 i915                  505108  0  
 btusb                  18160  2  
 videodev               85626  1 uvcvideo
 soundcore              12600  1 snd
 ttm                    65224  1 nouveau
 mxm_wmi                12859  1 nouveau
 snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
 serio_raw              12990  0  
 bluetooth             148839  23 bnep,rfcomm,btusb
 wmi                    18744  1 mxm_wmi
 shpchp                 32356  0  
 drm_kms_helper         32889  2 nouveau,i915
 parport_pc             32114  1  
 drm                   192226  5 nouveau,ttm,i915,drm_kms_helper
 binfmt_misc            17292  1  
 i2c_algo_bit           13199  2 nouveau,i915
 video                  18908  2 nouveau,i915
 lp                     17455  0  
 parport                40930  3 ppdev,parport_pc,lp
 usbhid                 41905  0  
 hid                    77367  1 usbhid
 e100                   36289  0  
 thomas@Thomas-Ubuntu:~$  
 
``````
                                  thomas@Thomas-Ubuntu:~$ lspci -nn
 00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
 00:02.0 Display controller [0380]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
 00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
 00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
 00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
 00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
 00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
 00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
 01:00.0 VGA compatible controller [0300]: nVidia Corporation NV6 [Vanta/Vanta LT] [10de:002c] (rev 15)
 01:01.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20]
 01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
 thomas@Thomas-Ubuntu:~$  
 
``````
                                  thomas@Thomas-Ubuntu:~$ rfkill list all
 0: hci0: Bluetooth
     Soft blocked: no
     Hard blocked: no
 thomas@Thomas-Ubuntu:~$  
 
``````
                                  thomas@Thomas-Ubuntu:~$ sudo lshw -c network
 [sudo] password for thomas:  
   *-network DISABLED       
        description: Ethernet interface
        product: 82562EZ 10/100 Ethernet Controller
        vendor: Intel Corporation
        physical id: 8
        bus info: pci@0000:01:08.0
        logical name: eth0
        version: 02
        serial: 00:13:20:ab:66:14
        size: 100Mbit/s
        capacity: 100Mbit/s
        width: 32 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
        resources: irq:20 memory:fe9ef000-fe9effff ioport:df40(size=64)
 thomas@Thomas-Ubuntu:~$  
 
```
Will now try oasick's solution.

---

### Post by doppel.ganger on 2011-09-21
Yay! oasick's solution worked! Thanks!

---

### Post by doppel.ganger on 2011-09-21
Gah! Overlooked problem. Still no panel icon and no network settings access. There is an Internet Connection now, though.

---

### Post by Brouham on 2011-09-21
Try editing /etc/NetworkManager/NetworkManager.conf and change managed=false to managed=true as below, then reboot.

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

---

### Post by cariboo on 2011-09-21
To get network-manager back, make sure you have libnss3* in /var/cache/apt/archives, then run the following command:

 ```
sudo apt-get install --reinstall libnss3*
```

If you don't have the file in the local package archive, you can download it [here]("http://packages.ubuntu.com/oneiric/libnss3").

Once you've downloaded it, either double click the package, or cd into the directory it is located in and type the following command:

```
sudo dpkg -i libnss3*
```

---

### Post by imblack on 2011-09-21
I was having same problem thanks guys!

---

### Post by robert shearer on 2011-09-21
> **Brouham said:**
> Try editing /etc/NetworkManager/NetworkManager.conf and change managed=false to managed=true as below, then reboot.

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

Thanks !
 this fixed it in gnome-session-fallback desktop **and** returned my date/time applet that went missing at the same time.

---

### Post by imblack on 2011-09-21
> **robert shearer said:**
> Thanks !
 this fixed it in gnome-session-fallback desktop **and** returned my date/time applet that went missing at the same time.

It fixed all my problems too. Just curios, should i remove auto etho and iface etho etc from /etc/network/interfaces? or do I also need that?

---

### Post by scottstensland on 2011-09-21
imblack <-- I doubt this ubuntu update created wireless outage has anything to do with file /etc/network/interfaces - feel free to put its contents back - I feel that file is an obsolete config file anyways as it doesn't mention my wireless adaptor (wlan0)

Brouham <-- thanks again for your life saving fix :


Try editing /etc/NetworkManager/NetworkManager.conf and change managed=false to managed=true as below, then reboot.

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

that fixed my bonked machine after this update outage
once I reinstalled libnss3 - cheers

---

### Post by imblack on 2011-09-21
Thanks for prompt reply. I have removed custom configurations from /etc/network/interface and it works for now hope it stays working after reboot.

---

### Post by thatguruguy on 2011-09-21
Run update manager again.  A fix has been released.

---

### Post by rrohde on 2011-09-22
> **Brouham said:**
> Try editing /etc/NetworkManager/NetworkManager.conf and change managed=false to managed=true as below, then reboot.

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

This still didn't do it for me; my network manager still shows me "device not managed" for both wired and wireless network cards.

EDIT: I had to remove my entries in /etc/network/interfaces in order for the fix to finally work. Thanks!

---

