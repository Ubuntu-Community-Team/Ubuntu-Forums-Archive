---
title: "eeePC 1015PEM Unclaimed - wireless not working"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by v4bes on 2012-12-19
Greetings

I have upgraded  from Ubuntu 10 to 12.10.  The wireless stopped working, so I did a  clean install.  I have tried a few fixes, but none have worked.  It used  to see wireless networks, but wouldn't log in.

I would appreciate any help. 

Using the terminal, I came up with the following.

[CENTER]sudo lshw -C network
[/CENTER]

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbffc000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:43:0f:fc
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.1.0-NAPI duplex=full ip=192.168.1.111 latency=0  link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

[CENTER]iwconfig
[/CENTER]

eth0      no wireless extensions.

lo        no wireless extensions.

[CENTER]cat /etc/lsb-release; uname -a
[/CENTER]

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux alex-1015PEM 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
alex@alex-1015PEM:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
    Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: AzureWave Device [1a3b:2047]
    Kernel modules: bcma

[CENTER]ifconfig
[/CENTER]

eth0      Link encap:Ethernet  HWaddr 20:cf:30:43:0f:fc  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe43:ffc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58497 errors:2 dropped:0 overruns:0 frame:1
          TX packets:34729 errors:0 dropped:0 overruns:0 carrier:7
          collisions:0 txqueuelen:1000 
          RX bytes:77470907 (77.4 MB)  TX bytes:3474675 (3.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:223052 (223.0 KB)  TX bytes:223052 (223.0 KB)

---

### Post by DuckHook on 2012-12-20
You've supplied an admirable amount of info. Well done. Lots to work with.

Your problem is probably an old one dealing with the broadcom chipset. Instructions for solving it can be found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"). Read thoroughly before proceeding because the page is dense with instructions and covers many different broadcom chipsets. You can ignore the other chipsets and focus on the instructions dealing with the 4313. The 4313 shouldn't be too bad because it is relatively newer. My broadcom chipsets are on older Dell laptops and harder to solve. According to the referenced page, your chipset uses the brcmsmac/brcm80211 module which was merged into the kernel way back at 2.6.37. This was probably why it worked right out of the box on your 10.x installs. Don't know if this module was dropped in 12.10. You should be able to get functionality back by following the instructions on the referenced page (including following the contained links) and reinstalling brcmsmac/brcm80211. After this is done, check with:

```
lsmod | grep brcm
```

---

### Post by v4bes on 2012-12-21
I went through that page & it looked like I should use the wl  Proprietary Broadcom STA Wireless driver.  12.10 (Quantal Quetzal)

At the end I got.

sudo modprobe wl
FATAL: Module wl not found.

There was no reply to your code.
lsmod | grep brcm

I am still getting.
sudo lshw -C network
*-network UNCLAIMED  

Any suggestions?

---

### Post by DuckHook on 2012-12-21
> **v4bes said:**
> I went through that page & it looked like I should use the wl  Proprietary Broadcom STA Wireless driver.  12.10 (Quantal Quetzal)

Correct. Specifically, [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A11.10_.28Oneiric_Ocelot.29_-_12.10_.28Quantal_Quetzal.29") section.

> At the end I got.

sudo modprobe wl
FATAL: Module wl not found.Please describe *completely* the steps you took. Should be as follows:

1. Make sure you have activated "restricted" repository. If you do not have access to "restricted" repository, package won't download.
2. Open a terminal. Do:

```
sudo apt-get update
```You will be asked for your password. While typing it in, nothing will show on the screen--not even ****. This is normal. *apt* will then update.

3. Then:

```
sudo apt-get install bcmwl-kernel-source
```You should be getting either a screen full of scrolling actions, or a question asking if you want to go ahead and install the package. Type *Y*. If this step generates error, please post it back to this thread between the ```
[\CODE] markers (substituting / for \) for easier readability).

4. Then:

[CODE]sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
```...to clean out all modules for fresh start,

5. Then, try again:

```
sudo modprobe wl
```If same error, do:

```
lsmod
```...by itself, and post whole output back to this thread.

> There was no reply to your code.
lsmod | grep brcm

I am still getting.
sudo lshw -C network
*-network UNCLAIMEDBecause module *wl* did not load, my subsequent command will indeed not return anything, nor will your network be "claimed". Other steps also possible, but let's do these for now.

---

### Post by v4bes on 2012-12-26
Delayed by holidays.  I did do those steps before, but here is they are again.

sudo apt-get update
[sudo] password for alex: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports InRelease         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal Release.gpg                 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates Release.gpg [933 B]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]   
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports Release.gpg [933 B]       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal Release                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [22.4 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages  
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports Release [49.6 kB]         
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [9,109 B]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [699 B]  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/main Sources                          
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [62.2 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/restricted Sources                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_CA                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/universe Sources  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/universe amd64 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/multiverse amd64 Packages      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [22.2 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/main i386 Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/restricted i386 Packages       
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [1,150 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/universe i386 Packages
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [61.8 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/main Translation-en
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/multiverse Translation-en
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [22.9 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/restricted Translation-en      
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,391 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/universe Translation-en_CA     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/universe Translation-en
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/main Sources [59.7 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/restricted Sources [889 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/universe Sources [65.9 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/multiverse Sources [2,934 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/main amd64 Packages [158 kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/restricted amd64 Packages [1,970 B]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/universe amd64 Packages [135 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_CA         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_CA   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_CA   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_CA     
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,936 B]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/main i386 Packages [158 kB]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/restricted i386 Packages [1,979 B]
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/universe i386 Packages [136 kB]
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,106 B]
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/main Translation-en [76.3 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/universe Translation-en [75.7 kB]
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/main Sources [14 B]      
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/restricted Sources [14 B]
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/universe Sources [4,597 B]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/multiverse Sources [14 B]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/main amd64 Packages [14 B]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/restricted amd64 Packages [14 B]
Get:40 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/universe amd64 Packages [4,748 B]
Get:41 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages [14 B]
Get:42 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/main i386 Packages [14 B]
Get:43 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/restricted i386 Packages [14 B]
Get:44 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/universe i386 Packages [5,567 B]
Get:45 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/multiverse i386 Packages [14 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Get:46 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/universe Translation-en [3,850 B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/multiverse Translation-en_CA          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal/restricted Translation-en_CA          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/main Translation-en_CA        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/multiverse Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/restricted Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates/universe Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/main Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports/universe Translation-en_CA  
Fetched 1,263 kB in 18s (69.3 kB/s)                                            
Reading package lists... Done


alex@alex-1015PEM:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
alex@alex-1015PEM:~$ sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
FATAL: Module wl not found.


alex@alex-1015PEM:~$ sudo modprobe wl
FATAL: Module wl not found.


alex@alex-1015PEM:~$ lsmod
[FONT=Courier New]Module                  Size  Used by
btrfs                 761721  0 
zlib_deflate           26914  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    74821  0 
qnx4                   13317  0 
hfsplus                84442  0 
hfs                    54553  0 
minix                  36058  0 
ntfs                   97304  0 
msdos                  17332  0 
jfs                   181093  0 
xfs                   837979  0 
reiserfs              246392  0 
ext2                   72880  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
parport_pc             32688  0 
ppdev                  17073  0 
joydev                 17457  0 
snd_hda_codec_realtek    77876  1 
uvcvideo               76749  0 
snd_hda_intel          33491  3 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
i915                  520629  3 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
snd                    78734  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeepc_wmi              13109  0 
asus_wmi               24088  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
coretemp               13400  0 
psmouse                95552  0 
serio_raw              13215  0 
microcode              22803  0 
soundcore              15047  1 snd
i2c_algo_bit           13413  1 i915
lpc_ich                17061  0 
mac_hid                13205  0 
video                  19335  1 i915
wmi                    19070  1 asus_wmi
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
atl1c                  41101  0 
[/FONT]

---

### Post by v4bes on 2013-01-22
I am still looking for help with this problem.  Any help would be appreciated.

Vince

---

