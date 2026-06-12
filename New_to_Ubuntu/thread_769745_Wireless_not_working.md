---
title: "Wireless not working"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by riptreeper on 2008-04-26
Ok I just installed Ubuntu 8.04 on my second hard disk and my wireless won't work. 

My wireless network shows up and all that and when I type my network key in it just keeps trying to connect to the network and then keeps popping up the same screen to keep putting in my passkey. 

I'm running a VAIO Ar 520 series with an Intel wireless wifi link 4965 agn. 

Thanks for any help

---

### Post by riptreeper on 2008-04-26
Anyone else having this issue

---

### Post by S@nctus on 2008-04-26
More importantly, is anyone *not* having this issue?

---

### Post by st33med on 2008-04-26
Please don't bump every 15 minutes. We will answer your question even if it falls off the front page.

Anyway, Intel wifi cards are pretty good with drivers... I am not sure if you have a good installation. Do this:
```
lspci | grep intel
```

And post it here.

---

### Post by riptreeper on 2008-04-26
Nothing came up

Sorry put an I instead of 1 

Anyways 

bash: 1spci: command not found

---

### Post by southernman on 2008-04-26
Close, but not quite... it's a small caps "L"

```
lspci | grep intel
```

---

### Post by riptreeper on 2008-04-26
yeah nothing happens 

Anything else I should try

---

### Post by southernman on 2008-04-26
try lspci by itself and paste the output here for us.

---

### Post by riptreeper on 2008-04-26
alex@VAIO:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by southernman on 2008-04-26
Kewl, that's progress!

One more time except this time, try the command
```
lsmod
```and paste the output here

---

### Post by riptreeper on 2008-04-26
alex@VAIO:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  0 
nls_cp437               6656  0 
vfat                   14464  0 
fat                    54556  1 vfat
usb_storage            73664  0 
libusual               19108  1 usb_storage
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
sonypi                 23192  0 
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_ondemand        9740  2 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
pcmcia                 40876  0 
joydev                 13120  0 
evdev                  13056  8 
serio_raw               7940  0 
tifm_7xx1               8576  0 
psmouse                40336  0 
tifm_core              11012  1 tifm_7xx1
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
iwl4965               105844  0 
iwlwifi_mac80211      219108  1 iwl4965
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  4224  0 
cfg80211               15112  1 iwlwifi_mac80211
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
uvcvideo               58116  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
sony_laptop            35292  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
sky2                   47492  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
i2c_core               24832  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
ac                      6916  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  0 
agpgart                34760  1 intel_agp
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
ata_generic             8324  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
usbhid                 31872  0 
hid                    38784  1 usbhid
ahci                   28420  2 
ata_piix               19588  0 
libata                159344  4 pata_acpi,ata_generic,ahci,ata_piix
scsi_mod              151436  6 usb_storage,sbp2,sr_mod,sg,sd_mod,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 usb_storage,libusual,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
alex@VAIO:~$

---

### Post by southernman on 2008-04-26
last output we need is

```
lshw -C network
```

I found a couple of bug reports, but those were for Gutsy...

[https://answers.launchpad.net/ubuntu/+question/28397](https://answers.launchpad.net/ubuntu/+question/28397)
[https://answers.launchpad.net/ubuntu/+question/16768](https://answers.launchpad.net/ubuntu/+question/16768)

---

### Post by riptreeper on 2008-04-26
alex@VAIO:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:e3:92:61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:71:57:2b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
alex@VAIO:~$ 

Thanks for all your help I'm learning quickly you have been very helpful

---

### Post by southernman on 2008-04-26
Don't thank me yet, but I'm trying to help you either sort it out or get you pointed in the right direction.

A few things that are good:

lspci shows your wifi card has been recognized
lsmod shows the driver for your card listed
lshw shows the connection point

The bad:
It's not working... uh duh! :/

Maybe bad:
The logical name given for this connection seems odd. I thought wifi's were always named wlan0 wlan1 or so on. First time I've seen them names wmaster0 as in the last output you posted.

I'm still looking so give me a little bit, or maybe someone more experienced will see what you've got and have the answer.

I'll be bach!

---

### Post by riptreeper on 2008-04-26
Awesome thanks for spending time helping me out I really appreciate it. You don't get help like this for windows.

---

### Post by southernman on 2008-04-26
Do a simple 

```
uname -r
``` to show us what kernel you have.

I've found something that *may* work and I want to be sure of the kernel version before suggesting it.

> Awesome thanks for spending time helping me out I really appreciate it. You don't get help like this for windows.

No worries riptreeper... I know you appreciate it and that makes all the difference.

---

### Post by riptreeper on 2008-04-26
2.6.24-16generic

or l6 generic

---

### Post by southernman on 2008-04-27
This was swiped from a member by the name of walkerk, on this howto:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)
It's tells how to update to the beta hardy kernel and you wouldn't need to do as the kernel is newer than that time. I've only pulled the info I feel *may* get your connection working.

Before going further make a backup copy of the file you're about to edit by doing this:

```
sudo cp /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.backup
```

Backup is done, now proceed below.

> 2. WLAN Interface naming. Fix wlan0_rename, wmaster0_rename, etc...
> I had to do this to get my wireless NIC to function correctly. (wlan0 doesn't work. It'll still end up wlan0_rename)
>> Should be a temp fix as I'd assume the kernel devs will address this bug (already on launchpad)

Replace instances of <**driver**> with your wireless driver. (Yours in this case is **iwl4965**)

1. Alter the the NICs persistent interface name:

```
gksu gedit /etc/udev/rules.d/70-persistent-net.rules
```

2. Now remove any interfaces already listed with your WLAN NIC's MAC address.

3. Add the following and then save and exit: (Replace 00:00:00:00:00:00 with your WLAN NIC's MAC address.)

```
# PCI device 0x14e4:0x4311 (**<driver>**)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:00:00:00:00", NAME="eth1"
```

***minor addtion to the swiped directions: where you see DRIVERS=="?*" above, make sure that your correct drives are listed here. If not, edit that portion also to show DRIVERS=="**iwl4965**"
***one last note, in your case it should show what is listed below as eth1, to be **wmaster0**. If it doesn't work and you want to tinker with it again, repeat the process and replace all instances of **wmaster0** with ***_wlan0_***

4. Now create an alias for eth1 and your driver, in my case b43: (again, yours is iwl4965)

```
echo 'alias eth1 **<driver>**' | sudo tee /etc/modprobe.d/**<driver>**
```

5. Reboot

Don't worry here. If it doesn't work, you just run this command after your reboot:

```
sudo cp /etc/udev/rules.d/70-persistent-net.rules.backup /etc/udev/rules.d/70-persistent-net.rules
```

If nothing else you get a little more troubleshooting and terminal seat time!

After your reboot, post back here with the output again of (if your wifi isn't working):

```
lshw -C network
```

Now that I may have thoroughly confused ya, give it a whirl and let us know what happens.

Good luck...

---

### Post by riptreeper on 2008-04-27
alex@VAIO:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:e3:92:61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:71:57:2b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g


I went through the steps as best as I could it's obviously not working yet I just plugged in my wired connection for now so that I could copy the code faster. Thanks for spending the time once again.

---

### Post by southernman on 2008-04-27
square one again huh?

Your card isn't a 802.11n by chance is it?

---

### Post by riptreeper on 2008-04-27
I am running the i386 version of Heron, Could that affect the way things run. When I go to install amarok it says that i386 is not supported. Thanks again

---

### Post by southernman on 2008-04-27
> **riptreeper said:**
> I am running the i386 version of Heron, Could that affect the way things run. When I go to install amarok it says that i386 is not supported. Thanks again
Shouldn't. Is your VAIO 32 or 64 bit?

What is the output of 
```
lwconfig
```

---

### Post by riptreeper on 2008-04-27
alex@VAIO:~$ lwconfig
bash: lwconfig: command not found
alex@VAIO:~$ 


It's 32 bit.

---

### Post by southernman on 2008-04-27
dang... my bad!

That would be 

```
iwconfig
```

---

### Post by riptreeper on 2008-04-27
No worries 

alex@VAIO:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:E5:3A:8A:72   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=98/100  Signal level=-51 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by southernman on 2008-04-27
ok, well - it's there.

Questions:
1- When editing that file earlier did you manually add your mac address for your wireless card... which would be **00:1E:E5:3A:8A:72**?
2- Did you try changing the "wmaster0" references to wlan0?
3- After saving the file, did you reboot?

BTW, I just noticed your email addy in your signature. You may want to obscure it... or remove it all together. I know gmail does good on spam, but you'll get a lot if you leave it.

---

### Post by riptreeper on 2008-04-27
k, well - it's there.

Questions:
1- When editing that file earlier did you manually add your mac address for your wireless card... which would be 00:1E:E5:3A:8A:72?
2- Did you try changing the "wmaster0" references to wlan0?
3- After saving the file, did you reboot?

BTW, I just noticed your email addy in your signature. You may want to obscure it... or remove it all together. I know gmail does good on spam, but you'll get a lot if you leave it.

1. No I didn't 

2. It was already changed

3. Yes I rebooted. Which was really fast compared to Vista

And thanks for the tip about the e-mail

---

### Post by riptreeper on 2008-04-27
this is what the file looks like now. 


# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4363 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:a9:e3:92:61", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4229 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:e8:71:57:2b", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

---

### Post by Sunflower1970 on 2008-04-27
Had a similar problem tonight when testing the live CD. I cannot connect to my WEP connection, but I can connect to an open connection with Network Manager. I've never been able to use NM in any of the previous Ubuntu releases, unfortunately. 

Just to make sure you can connect, try removing the security for a few moments on your router and then connect with your wireless.

Things that have worked for me, though, (using WEP with a hidden address) 

1. If the computer is pretty much always in one place, one can remove the NM through Synaptic then go to System-->Administration-->Network, under Wireless Connection, choose Properties then enter in the ESSID and the password, and choose the configuration. Close the dialogue box, then uncheck and check the box next to the wireless connection. This usually works quite well. 

2. I've used the command line method before shown here: [http://ubuntuforums.org/showthread.php?t=571188&highlight=enable+wireless+command+line](http://ubuntuforums.org/showthread.php?t=571188&highlight=enable+wireless+command+line) very helpful. It's worth it to read and practice, just in case the GUIs fail you.

3. Look up wicd: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) for wireless. It's the program I find I use the most. (That and the command line method) It also can use WPA2 security settings. I don't think NM has the ability to use it yet?

---

### Post by southernman on 2008-04-27
LOL well, the last part of #3 is always a given in this neck of the woods... but don't distract me! ;) ROFL


Question:

May seems stupid to ask (now) but, are you using the network manager (or something) to setup the connection for your computer... and it just doesn't connect? It seems to me, that it should be able to connect as it's been recognized and has the proper driver modules loading. Double check the network manager for your wireless connection and make sure the settings are right. Username, password, encryption and so on.

*** 
Pre post editing: Thanks for posting the file...



You've still got the backup of that file I presume, so go back to it

```
gksu gedit /etc/udev/rules.d/70-persistent-net.rules
```
You need to edit it again and show this for your wireless connection only:

Replace DRIVERS=="?*" to look like DRIVERS=="iwl4965"

Now save the file and reboot.

---

### Post by riptreeper on 2008-04-27
Ok I did that, BUT, i used the program that the user above me suggested and now I don't have the default wireless/network manager. 

How do I get it back? 

Sorry about that.

---

### Post by southernman on 2008-04-27
no worries rip. It should work as well, it just replaces the NM that comes default with Ubuntu. I just read about it tonight/this morning myself in my searches trying to help you out.

The only other thing I could do for you tonight is hand off the Google search I pulled up (the best one at least)... [http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=rPc&q=Intel+Corporation+PRO%2FWireless+4965+AG+or+AGN+Network+Connection+%28rev+61%29+on+ubuntu&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=rPc&q=Intel+Corporation+PRO%2FWireless+4965+AG+or+AGN+Network+Connection+%28rev+61%29+on+ubuntu&btnG=Search)

I did another with your system model, but it only pulled up this thread... lol!

I've gotta sign off, it's late, I'm not a spring chicken anymore, plus I've done all I know to do. Will sleep on it though and check back after my domestic duties are done tomorrow.

Thanks again to Sunflower1970 for giving more advanced help.

Good luck riptreeper... It's gonna be something amazingly simply probably.

---

### Post by riptreeper on 2008-04-27
Absolutely thanks so much for all you have done I really appreciate all your help.

---

### Post by riptreeper on 2008-04-27
Sunflower, how would I get back the default wireless manager?

---

### Post by riptreeper on 2008-04-27
I am hitting the hay for tonight 

If anyone happens upon this and can help me get back the default network manager that runs from the top panel that would be greatly appreciated. 

Thanks.

---

### Post by Sunflower1970 on 2008-04-27
riptreeper To get back Network Manager, you'll need to connect to your wired connection, then open up Synaptic and do a search for Network Manager, and reinstall it, or open up your terminal and type in "sudo apt-get install network-manager" 

HTH.

---

### Post by riptreeper on 2008-04-27
Ok sweet thanks. I got it working.

I had to turn off security for my router leaving open my network which is a bad idea but I don't have any other options for right now.

I have a linksys router. Could that be the reason for the difficulties?

---

### Post by talent03 on 2008-04-29
> **riptreeper said:**
> Anyone else having this issue

I actually have this problem on my m1330 with the same driver. I have not been able to fix it. I can connect to unsecured networks but secured networks just don't seem to work. I have been searching all over and trying different things but nothing seems to work. I will keep trying. So I will probably stick around this thread to see if we can get this solved.

---

