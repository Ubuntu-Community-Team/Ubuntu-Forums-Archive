---
title: "Can't connect to hidden WPA/WPA2 Protected Wi-Fi in Xubuntu 12.04.2."
date: 2013-04-17
forum: New to Ubuntu
---

### Post by AnaheimSam on 2013-04-17
I can connect to wi-fi networks that don't have any security  without an issue, like at a restaurant or a library, but when I try to connect to my home wi-fi, which is both hidden and WPA/WPA2 Personal protected, I cannot  connect. After a failed attempt to connect, I notice that my computer can see my  wi-fi, and it shows that a good signal can be seen, but I still can't  connect.
All attempts to connect to my home Wi-Fi fail in Xubuntu, though I can connect properly and have no issues in Windows 8, which leads me to believe that there is something wrong with the driver.
 
The driver I am using is the Broadcom 802.11 STA Wireless driver, and  the wi-fi receiver is a BCM4313 802.11b/g/n Wireless LAN Controller.

Any solution would be appreciated.
Cheers.

---

### Post by wildmanne39 on 2013-04-17
Hi, many linux wireless drivers have trouble connecting to hidden networks so I recommend that you unhide it also a hidden network is no more secure then a network not hidden.
Thanks

---

### Post by DuckHook on 2013-04-17
Hi, and welcome to the forum and Ubuntu!

Broadcom chips are known to be very finicky in Ubuntu, but ultimately solvable. The fact that you can see the network (though I am surprised, because you state that it is hidden) means that the driver is working and it is more likely a configuration issue. At the very least, you are more than halfway to a solution.

Please open a terminal and do:```
sudo lshw -C network
``````
sudo lspci -vk | grep -iA13 net
``````
ifconfig
``````
iwconfig
``````
lsmod
``````
cat /etc/modules
``````
grep blacklist /etc/modprobe.d/blacklist.conf
```and post output back to this thread. Output will be rather lengthy, so, for easier reading, please be sure to wrap each output separately in (CODE)output(/CODE) marks, where the round brackets are replaced with square [] ones. This will put each output into its own box like my examples above.

We will first ascertain precisely which driver you are using and if there are any conflicts with another driver.

---

### Post by DuckHook on 2013-04-17
@AnaheimSam

Do as Wild Man suggests first before embarking on all the work I set you to.

---

### Post by AnaheimSam on 2013-04-17
Wild Man:

I did as I was told, but the same thing happened. No connection was made, even though the wi-fi network was seen and the password for the network was entered correctly. This time around, the network was seen from the get-go, as opposed from after a failed attempt to connect. I have put the network back into hidden mode.

DuckHook:
Your outputs...

sudo lshw -C network
```
*-network              
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 78:e3:b5:6f:96:29
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth2
       version: 01
       serial: e0:06:e6:08:73:f9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f0300000-f0303fff
```

sudo lspci -vk | grep -iA13 net
```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
            Subsystem: Hewlett-Packard Company Device 169b
            Flags: bus master, fast devsel, latency 0, IRQ 42
            I/O ports at 3000 [size=256]
            Memory at f0004000 (64-bit, prefetchable) [size=4K]
            Memory at f0000000 (64-bit, prefetchable) [size=16K]
            Capabilities: [40] Power Management version 3
            Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Capabilities: [70] Express Endpoint, MSI 01
            Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
            Capabilities: [d0] Vital Product Data
            Capabilities: [100] Advanced Error Reporting
            Capabilities: [140] Virtual Channel
            Capabilities: [160] Device Serial Number 01-00-00-00-36-4c-e0-00
--
07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
            Subsystem: Hewlett-Packard Company Device 1795
            Flags: bus master, fast devsel, latency 0, IRQ 17
            Memory at f0300000 (64-bit, non-prefetchable) [size=16K]
            Capabilities: [40] Power Management version 3
            Capabilities: [58] Vendor Specific Information: Len=78 <?>
            Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
            Capabilities: [d0] Express Endpoint, MSI 00
            Capabilities: [100] Advanced Error Reporting
            Capabilities: [13c] Virtual Channel
            Capabilities: [160] Device Serial Number 00-00-e6-ff-ff-08-e0-06
            Capabilities: [16c] Power Budgeting <?>
            Kernel driver in use: wl
            Kernel modules: wl, bcma, brcmsmac
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:6f:96:29 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000
 
eth2      Link encap:Ethernet  HWaddr e0:06:e6:08:73:f9 
          inet6 addr: fe80::e206:e6ff:fe08:73f9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:448
          TX packets:80 errors:50 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:918 (918.0 B)  TX bytes:19204 (19.2 KB)
          Interrupt:17
 
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:792 (792.0 B)  TX bytes:792 (792.0 B)
```

iwconfig
```
lo        no wireless extensions.
 
eth2      IEEE 802.11abg  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         
eth0      no wireless extensions.
```

lsmod
```
Module                  Size  Used by
michael_mic            12612  0
arc4                   12529  0
vesafb                 13844  1
joydev                 17693  0
snd_hda_codec_idt      70795  1
snd_hda_codec_hdmi     32474  1
snd_hda_intel          33719  7
snd_hda_codec         127706  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
hp_wmi                 18092  0              
sparse_keymap          13890  1 hp_wmi
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lib80211_crypt_tkip    17390  0
wl                   3074895  0
snd_seq_midi           13324  0
btusb                  18332  2
rfcomm                 47604  16
uvcvideo               72627  0
parport_pc             32866  0
snd_rawmidi            30748  1 snd_seq_midi
videodev               98259  1 uvcvideo
psmouse                97485  0
ppdev                  17113  0
bnep                   18281  2
rts_pstor             445241  0
v4l2_compat_ioctl32    17128  1 videodev
cfg80211              205774  1 wl
bluetooth             180153  23 btusb,rfcomm,bnep
snd_seq_midi_event     14899  1 snd_seq_midi
lib80211               14381  2 lib80211_crypt_tkip,wl
serio_raw              13211  0
k10temp                13166  0
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
video                  19651  0
fglrx                3264017  88
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 hp_wmi
mac_hid                13253  0
snd                    79041  24 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13301  0
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0
```

cat /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
 
lp
rtc
```

grep blacklist /etc/modprobe.d/blacklist.conf
```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi         
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
```

---

### Post by stinkeye on 2013-04-18
What authentication are you using in your router settings.
Mine would only work when using WPA2-PSK not WPA-PSK+WPA2-PSK

---

### Post by AnaheimSam on 2013-04-18
The router says that the security mode is WPA-Personal and the WPA Mode is set at WPA2 Only.
Apologies for saying that my router was WPA/WPA2. Such was the only option given when connecting from Xubuntu.

---

### Post by wildmanne39 on 2013-04-18
Please leave your network unhidden until we get it to connect.

Please do:
```
sudo apt-get install --reinstall linux-headers-generic linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
if it does not work then copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Also:
```
modinfo wl
```
Thanks

---

### Post by AnaheimSam on 2013-04-18
Wild Man:
To save time, I executed the codes in a string from an unblocked wi-fi hotspot at my college in the following fashion:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-`uname -r` && sudo apt-get install --reinstall bcmwl-kernel-source && sudo modprobe wl
```

This is what happened...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mythes-en-au hyphen-en-us amarok-help-en language-pack-kde-en kde-l10n-engb
  language-pack-kde-en-base openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/984 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 179034 files and directories currently installed.)
Preparing to replace linux-headers-3.2.0-40-generic 3.2.0-40.64 (using .../linux-headers-3.2.0-40-generic_3.2.0-40.64_amd64.deb) ...
Unpacking replacement linux-headers-3.2.0-40-generic ...
Preparing to replace linux-headers-generic 3.2.0.40.48 (using .../linux-headers-generic_3.2.0.40.48_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-headers-3.2.0-40-generic (3.2.0-40.64) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
Setting up linux-headers-generic (3.2.0.40.48) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mythes-en-au hyphen-en-us amarok-help-en language-pack-kde-en kde-l10n-engb
  language-pack-kde-en-base openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,344 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted bcmwl-kernel-source amd64 6.20.155.1+bdcom-0ubuntu0.0.1 [1,344 kB]
Fetched 1,344 kB in 2s (630 kB/s)                
(Reading database ... 179034 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-40-generic
Building for architecture x86_64
Building initial module for 3.2.0-40-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-40-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-40-generic
```

I am sure that this completed what you asked me to do, but since I am away at school, I won't know wether or not it worked until I get home later tonight.

---

### Post by wildmanne39 on 2013-04-18
If it does not help please post the output of:
```
modinfo wl
```
Thanks

---

### Post by squakie on 2013-04-18
Might I also add a little something here? I would also open network manager, select edit connections, and delete any that are defined there.  I have noticed quite often that once you try to connect - and we know that the password may have been incorrect at 1 time - that is remembered.  No matter what you do to re-enter a password you know is correct, it still uses the saved one and can result in situation where the user puts in the correct password/passkey, but it doesn't work.  Deleting the defined entries first - especially since this was/is a hidden network - will at least give you a clean slate.  Also, Wild Man is very correct when he says a hidden network id does nothing - it can be found in a second, maybe 2 at most.  Leave the network broadcasting the session id - the encryption is what protects you.  Wild Man is a very wise man with these wireless issues - stick with what he is asking you to do. ;)

---

### Post by AnaheimSam on 2013-04-18
Squakie: I deleted the information on my connection, but it did not help. The network in question can be seen (as it is not in hidden mode anymore), and a connection can be attempted, but a connection cannot be completed. The password that I enter is correct, because it is the same information that I input when in Win 8 (which has no issue connecting to the network.)

Wild Man: The output you asked for...

```
filename:       /lib/modules/3.2.0-40-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     620417839200A53FF5C4AB5
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.2.0-40-generic SMP mod_unload modversions
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int        
parm:           intf_name:string
```

---

### Post by wildmanne39 on 2013-04-18
This is little bit of a guess since I do not have the information from the script to look at, please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac " | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot then:
```
sudo modprobe wl
```
Thanks

---

### Post by AnaheimSam on 2013-04-18
Wild Man: I did as you said, but nothing happened, and the situation is still the same.

I forgot to make and send the script, so here it is if you still want to see it.

---

### Post by wildmanne39 on 2013-04-18
Hi, you have error messages in the file you posted but from my research they should not stop you from connecting.

I believe the issue is network manger is trying to activate eht1 and your connection is shown as eth2.
If you have not done so already remove all wireless connections from network manager then reboot and let network manager find your connection and name it.
If that does not work please post the output of:
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
What is the name of the network you are trying to connect too?
Thanks

---

### Post by AnaheimSam on 2013-04-18
Wild Man: Your output...

```
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:06:e6:08:73:f9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:06:e6:08:73:f9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:06:e6:08:73:f9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="78:e3:b5:6f:96:29", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

I am trying to get to "amyfarahfowler."

---

### Post by wildmanne39 on 2013-04-18
Hi I believe you should remove this ```

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e0:06:e6:08:73:f9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
```
from that file, save it in a document file just incase we need to add it back.
```
gedit /etc/udev/rules.d/70-persistent-net.rules
```
to open the file then remove that part save, close gedit and reboot.
Thanks

---

### Post by AnaheimSam on 2013-04-18
Wild Man: I have Xubuntu. As such I do not have Gedit, so I instead ran...
```
sudo leafpad /etc/udev/rules.d/70-persistent-net.rules
```

I ran it as sudo because it wouldn't let me save changes unless I did run as sudo.

I coppied the whole document to a .odt in LibreOffice in case I need to reverse the changes. I then deleted the line you told me to and restarted the machine.

My situation did not change, though. My machine sees the network, attempts to connect, fails, and tries to connect again.

---

### Post by wildmanne39 on 2013-04-18
You did it right, I am getting tired and I am running a fever so I am going offline for tonight.

Did you  remove all wireless connections from network manager then reboot and let network manager find your connection and name of network? 

Do: 
```
iwconfig
```
see if your connection is eth1 now if not open that file and see if eth2 is back in the file.
Thanks

---

### Post by AnaheimSam on 2013-04-18
I did remove everything from the network manager, then restarted, but the situation is still the same, just in a different way.

1. Click network manager icon in the panel.
2. Click on "amyfarahfowler" (My home network) This means that the network manager is finding my network.
3. Prompt asks for password.
4. Enter password sucessfully.
5. Machine doesn't connect, but instead times out, fails, and tries again, eventually timing out again.

I ran iwconfig, and got...
```
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"amyfarahfowler"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: xx:xx:xx:xx:xx:xx:xx:xx   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

I opened /etc/udev/rules.d/70-persistent-net.rules and I saw that the line ending in eth2 was still gone, as you told me.

Hope you get better.

---

### Post by DuckHook on 2013-04-19
Hi AnaheimSam,

I am not close to Wild Man's knowledge calibre, but would like you to try something at router end if you are willing:

If there is an option to change encryption cipher from TKIP to AES, please try that. You will need to save and restart your router, and possibly need to reboot laptop. Sometimes, Linux drivers have problems deciphering TKIP. AES is a more secure cipher in any case. This change should not effect W8, as it should detect the cipher change automatically.

---

### Post by wildmanne39 on 2013-04-19
Hi, please change your channel to 11 and see if that helps, if not remove the netinfo.txt file in your home folder and run the script again and post the results here so we can see your wireless settings after the changes.

I may have to ask my good friend chili555 take a look because I am about out of ideas.
Thanks

---

### Post by AnaheimSam on 2013-04-22
DuckHook: I changed the cipher from TKIP to AES but nothing happened. I still cant connect.
Wild Man: I changed to channel 11, but nothing happened. I still can't connect. I am at home, so I ran the script offline. The result is here...

---

### Post by wildmanne39 on 2013-04-22
Hi, it is looking better please set your wireless settings in network manager to match the screenshots espceially the one about ipv6.
Then reboot.
Thanks

---

### Post by wildmanne39 on 2013-04-22
Also I see the your bit rate is 65 but your wirless card only supports up to 54, in your router settings please set it to auto or 54 or lower.
Thanks

---

### Post by AnaheimSam on 2013-04-22
Wild Man:
What screenshots are you referring to?
Also, I do not know how to set the bit rate on my router. The make is D-LINK and the model is DIR-632.

---

### Post by wildmanne39 on 2013-04-22
Sorry I am having some health issues at the moment and forgot to attach them.
For rate try this then:
```
sudo iwconfig wlan0 rate auto
```
Then check to see if the rate changed with:
```
iwconfig
```
Thanks

---

### Post by AnaheimSam on 2013-04-22
I did as the screenshots depicted.
As for the command, it failed because I can't get my computer to connect to the router in Xubuntu. I can connect to the router in Windows, though.

All of the changes you and the other contributors have asked by to do have been done in Windows, as nothing is wrong with connecting to the network from there.

All to say, what is the equivalent of...
```
sudo iwconfig wlan0 rate auto
```
...in a Windows CMD.

---

### Post by wildmanne39 on 2013-04-23
For the most part windows has nothing to do with ubuntu and all the changes I have asked you to make need to be made in ubuntu.

The settings in the screenshots did you make them from ubuntu?
Thanks

---

### Post by wildmanne39 on 2013-04-23
Okay I have consulted with the my good friend and the resident expert chili555 and we are going to try the other driver that sometimes works with this device.

Please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
gksu leafpad /etc/modprobe.d/blacklist.conf
```
and add a hash (#) mark in the beginning of any line which you want to disable (ineffective). So in your case, after opening that file with above command, look for the line that says blacklist bcma and brcmsmac  (it would most probably be the last lines) and add the '#' mark in the beginning of both, then save and close leafpad.

Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot
Thanks

---

### Post by AnaheimSam on 2013-05-02
Sorry for not replying for a while. Just wanted to try going about it alone and see what would happen.

Wild Man: I did what you said, but then, not only could I not get onto the network, but signal strength was severely reduced as well (which is also the same result I get from Ubuntu 13.04.)

As a result of severe frustration, I downgraded from Xubuntu 12.04.2 to 12.04.1 (which for some reason, works perfectly with my network, whether or not it is hidden or protected.)
I would like to get back up to 12.04.2, but which package do I make sure not to upgrade so that the wi-fi receiver remains unaltered both during and after the upgrade?

---

