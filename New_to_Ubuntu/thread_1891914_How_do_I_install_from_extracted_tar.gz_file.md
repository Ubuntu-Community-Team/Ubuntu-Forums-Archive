---
title: "How do I install from extracted tar.gz file?"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by LearningPerson on 2011-12-06
Hello,  I'm trying to set up wireless for my Lucid 10.04.  I bought an Alfa AWUS0364H adapter which says it's for Linux 2.6x.

It came with a mini-CD and I extracted the Linux tar.gz file onto my Desktop but I don't know what to do from there.  Would there be an "install" file?  I can only do simple commands in the terminal and would like somehow to get this into Synaptic.

Will someone help?

Thanks, Sharon

---

### Post by searchfgold6789 on 2011-12-06
That's strange, Google says that device doesn't exist...

Anyway, can you tell us what files are inside the folder you extracted?

---

### Post by bluexrider on 2011-12-06
**step #1** : After you got the source code, extract it, using following commands (it will extract it in the same directory) 
for tar.gz type :
 tar -xvzf source_code.tar.gz 

for tar.bz2 type :
 tar -jxvf source_code.tar.bz2 [B]

step #2[/B] : Move to the directory, Read the readme  file to go further (if necessary). 
Some applications may have  installation script such as install.sh or something like that, you just  need to execute that script using
 cd source_code  ./install.sh command. 

If it&#8217;s the source code then you may need to first configure it by using the command -
 ./configure 

**step #3** : Now use a build automation tools such as  make to create executable from the source code; it scans makefiles to  get instruction on how to derive target file.

 make [B]

step #4[/B] : Now install the application using the command (followed by your login password) -
 
sudo make install

---

### Post by wildmanne39 on 2011-12-06
Hi, there should be a readme file that tells you how to install it, but I find it is easier and better to download the driver for wireless adapters in a lot of cases that way you make sure you get the right driver version for the adapter but the install procedure is much the same.

Can you please copy and paste this command into the terminal then paste the results here: 
```
lsusb
```
the adapter needs to be plugged in before you run the command.
Thank you

---

### Post by leeper69 on 2011-12-06
to unzip and extract a tarball place it in your chosen directory. open terminal and cd to your chosen directory then type the following command at the user prompt ( tar -zxvpf your-tarball-file name.) Next type ./configure and the files and directorye should be configured.If you type man tar in terminal you can get a listing of all the commands for tar. When you are done looking just type q to quit and go back to your user prompt.

---

### Post by LearningPerson on 2011-12-06
Hi Bluexrider ....again,  Am still working on getting wireless to work.  And yes, searchfgold, I do have ther Alfa AWUS036H right here.

This is the folder from the mini CD:  file:///home/sharon/Desktop/rtl8187_linux_26.1025.0328.2007/    Inside are wpa-supplicant, drv.tar.gz, ifcfg-wlan0, makedrv, stack.tar.gz, and a bunch of wlan0 files.   

I wrote this in the terminal: tar -xvzf  rtl8187_linux_26.1025.0328.2007 tar.gz    

but it's not happy.  It says:  
$ tar -xvzf rtl8187_linux_26.1025.0328.2007 tar.gz
tar: rtl8187_linux_26.1025.0328.2007: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: tar.gz: Not found in archive
tar: Exiting with failure status due to previous errors

I read the Readme and one source code seems to be:  Unpack source code of WPA supplicant:

	  tar -zxvf wpa_supplicant-0.4.9.tar.gz

	  cd wpa_supplicant-0.4.9

Can I write that exactly as the first thing I now do in the terminal?

Sharon

---

### Post by LearningPerson on 2011-12-06
Hi wildmanne,  Here it is:
 lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 003: ID 03f0:5311 Hewlett-Packard OfficeJet 6300
Bus 002 Device 002: ID eb1a:5060 eMPIA Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by azmyth on 2011-12-06
> **LearningPerson said:**
> Hi Bluexrider ....again,  Am still working on getting wireless to work.  And yes, searchfgold, I do have ther Alfa AWUS036H right here.

This is the folder from the mini CD:  file:///home/sharon/Desktop/rtl8187_linux_26.1025.0328.2007/    Inside are wpa-supplicant, drv.tar.gz, ifcfg-wlan0, makedrv, stack.tar.gz, and a bunch of wlan0 files.   

I wrote this in the terminal: tar -xvzf  rtl8187_linux_26.1025.0328.2007 tar.gz    

but it's not happy.  It says:  
$ tar -xvzf rtl8187_linux_26.1025.0328.2007 tar.gz
tar: rtl8187_linux_26.1025.0328.2007: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: tar.gz: Not found in archive
tar: Exiting with failure status due to previous errors

I read the Readme and one source code seems to be:  Unpack source code of WPA supplicant:

	  tar -zxvf wpa_supplicant-0.4.9.tar.gz

	  cd wpa_supplicant-0.4.9

Can I write that exactly as the first thing I now do in the terminal?

Sharon

This doesn't look right because of the space after the 7 before the t

rtl8187_linux_26.1025.0328.2007 tar.gz

just use autocomplete

type

tar -xvzf rt[TAB]

where [TAB] means use the tab key then hit enter

---

### Post by F.G. on 2011-12-06
odd, i'v got an Alfa AWUS036H and it seems to work on both Crunchbang, and Ubuntu 11.04, 10.10 and 10.04 out of the box for me. 
also i've got an rtl8187b wifi card in my laptop, which works fine, which i think uses the same driver as the rtl8187. 

the output of: ```
iwconfig
```could be helpful.

---

### Post by beew on 2011-12-06
You can open the tar.gz file by just right clicking it and choose "extract here", or if you want to extract it to some other directory choose Open with File Manager and then press "Extract" and choose the directory to extract to.

Your command didn't work because you have to execute it in the directory where the tarball is stored. So if it is in Desktop (note the capital D) you have to do

```
cd Desktop
tar -xvzf  rtl8187_linux_26.1025.0328.2007 tar.gz    


```Anyway, just right click and see the content, save you the typing troubles. :)

---

### Post by wildmanne39 on 2011-12-06
Hi, I have researched your issue and the driver should be included in ubuntu so please post the results of the following commands:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

If you do install this driver it may conflict with the one installed so I would not continue with installing it until we troubleshoot the one that is already installed.
Thank you

---

### Post by LearningPerson on 2011-12-06
Here's what I get:

~$ tar -xvzf rt
tar: rt: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

cd Desktop
sharon@sharon-desktop:~/Desktop$ tar -xvzf  rtl8187_linux_26.1025.0328.2007 tar.gz
tar: rtl8187_linux_26.1025.0328.2007: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: tar.gz: Not found in archive
tar: Exiting with failure status due to previous errors



I don't think I have the right file.  This is actually the folder that I extracted.

---

### Post by LearningPerson on 2011-12-06
Here it is: sharon@sharon-desktop:~$ cat /etc/lsb-release

DISTRIB_ID=Ubuntu

DISTRIB_RELEASE=10.04

DISTRIB_CODENAME=lucid

DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

sharon@sharon-desktop:~$ uname -a

Linux sharon-desktop 2.6.32-34-generic-pae #77-Ubuntu SMP Tue Sep 13 21:16:18 UTC 2011 i686 GNU/Linux

sharon@sharon-desktop:~$ lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

	Kernel driver in use: ath5k

	Kernel modules: ath5k

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

	Kernel driver in use: r8169

	Kernel modules: r8169


$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:off/any  

          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   

          Tx-Power=20 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          

wlan1     IEEE 802.11bg  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off


sharon@sharon-desktop:~$ rfkill list all

0: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: no

1: phy1: Wireless LAN

	Soft blocked: no

	Hard blocked: no


~$ lsmod

Module                  Size  Used by

aes_i586                7268  0 

aes_generic            26863  1 aes_i586

rtl8187                50485  0 

eeprom_93cx6            1333  1 rtl8187

isofs                  29250  1 

udf                    78785  0 

crc_itu_t               1371  1 udf

binfmt_misc             6587  1 

ppdev                   5259  0 

dm_crypt               11331  0 

arc4                    1153  4 

snd_hda_codec_atihdmi     2367  1 

snd_pcm_oss            35308  0 

snd_mixer_oss          13746  1 snd_pcm_oss

snd_hda_codec_realtek   203408  1 

iptable_nat             3543  0 

nf_nat                 15560  1 iptable_nat

snd_hda_intel          22165  2 

nf_conntrack_ipv4      10346  3 iptable_nat,nf_nat

snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel

snd_hwdep               5412  1 snd_hda_codec

nf_conntrack           60943  3 iptable_nat,nf_nat,nf_conntrack_ipv4

nf_defrag_ipv4          1073  1 nf_conntrack_ipv4

iptable_mangle          1549  0 

snd_seq_dummy           1338  0 

iptable_filter          1369  0 

snd_seq_oss            26722  0 

snd_seq_midi            4557  0 

ip_tables               9899  3 iptable_nat,iptable_mangle,iptable_filter

x_tables               14175  2 iptable_nat,ip_tables

snd_rawmidi            19056  1 snd_seq_midi

ath5k                 132620  0 

snd_pcm                70918  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec

snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi

snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

ath9k_htc              43487  0 

ath9k_common            2551  1 ath9k_htc

snd_timer              19098  2 snd_pcm,snd_seq

snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

ath9k_hw              284353  2 ath9k_htc,ath9k_common

ath                    13671  3 ath5k,ath9k_htc,ath9k_hw

compat_firmware_class     6296  1 ath9k_htc

mac80211              247057  3 rtl8187,ath5k,ath9k_htc

uvcvideo               57438  0 

snd                    54244  16 snd_pcm_oss,snd_mixer_oss,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device

usblp                  10481  0 

videodev               34425  1 uvcvideo

v4l1_compat            13251  2 uvcvideo,videodev

cfg80211              151118  5 rtl8187,ath5k,ath9k_htc,ath,mac80211

psmouse                63677  0 

serio_raw               3978  0 

lp                      7028  0 

compat                  7331  5 rtl8187,ath5k,ath9k_htc,mac80211,cfg80211

soundcore               6620  1 snd

snd_page_alloc          7172  2 snd_hda_intel,snd_pcm

pcmcia_core            32996  1 compat

k8temp                  3152  0 

i2c_piix4               8527  0 

led_class               2864  4 rtl8187,ath5k,ath9k_htc,compat

shpchp                 28899  0 

parport                32635  2 ppdev,lp

dm_raid45              81647  0 

xor                    15028  1 dm_raid45

fbcon                  35102  71 

tileblit                1999  1 fbcon

font                    7557  1 fbcon

bitblit                 4707  1 fbcon

usbhid                 36206  0 

hid                    67288  1 usbhid

softcursor              1189  1 bitblit

usb_storage            39873  0 

vga16fb                11385  1 

vgastate                8961  1 vga16fb

pata_atiixp             3148  0 

ahci                   32392  3 

r8169                  34396  0 

mii                     4381  1 r8169

ramzswap                6362  1 

xvmalloc                4074  1 ramzswap

lzo_decompress          2189  1 ramzswap

lzo_compress            1853  1 ramzswap

---

### Post by F.G. on 2011-12-06
hi learningperson,

i agree with wlidmanne39, i'm pretty sure the driver should be included in Ubuntu 10.04 and several previous releases.

as far as extracting the files is concerned, you may fin it easier to navigate to the file through the windowed file manager (point and click to it) and then you can right click and extract it.

---

### Post by F.G. on 2011-12-06
```

iwconfig

lo no wireless extensions.



eth0 no wireless extensions.



wlan0 IEEE 802.11bg ESSIDff/any 

Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated 

Tx-Power=20 dBm 

Retry long limit:7 RTS thrff Fragment thrff

Power Managementff



wlan1 IEEE 802.11bg ESSIDff/any 

Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 

Retry long limit:7 RTS thrff Fragment thrff

Power Managementff
```
so it looks like you've got two wifi cards working, wlan0 and wlan1.

ps i would also suggest use [CODE\][/CODE\] tags around terminal outputs, makes it easier to read.

---

### Post by LearningPerson on 2011-12-06
Hi, I wondered how people got the boxes around their output.  

Before I plugged in the Alfa I had only wlan0.  I do have ath9k_htc installed from my last USB adapter.  

Will a conflict be made with wlan0 and wlan1?  What shall I do now?

---

### Post by F.G. on 2011-12-06
the way get those boxes is to type what i typed, but without either of the '\' in (i can't figure out how to actually show you what to type because it'll just come out with a code box).

you wont get a conflict between the two cards, they should both work fine if you connect them to a network.

i'm assuming you have the classic gnoe look if it is 10.04. do you have a symbol in the top right corner looks a bit like a quater circle on it's tip? (either empty if it isn't connected of filled with concentric quater circles if it isn't). the should be how you can connect to a wifi network.

---

### Post by LearningPerson on 2011-12-06
OK, while attempting to connect, I did see the ESSID but couldn't get the Access Point:
[CODE\]$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:"JT1969"  

          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   

          Tx-Power=20 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          

wlan1     IEEE 802.11bg  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off
[/CODE\]

---

### Post by LearningPerson on 2011-12-06
I'll try the bracketed code next time.  Not sure what you mean about my 10.04 - I think it's classic - nothing special.   I'm using WICD rather than Network Manager because I read on the forum here that it is better.

---

### Post by F.G. on 2011-12-06
yeah, sorry i didn't explain the code tags very well. you need to write "CODE" and "/CODE" without the "" and each of them in [] and put your code between. there is a way to write this so you can see (and it doesn't just come out with a code box), but i don't remember what it is.

so i guess the good news is that it looks like you wifi cards are both working and you *should* be able to connect to a network. precisely why it is not associating with the essid i have no idea.
but i have seen this before somewhere,and i know that there is a solution.

did the icon look like it was trying to connect, when you clicked on the network?

---

### Post by wildmanne39 on 2011-12-06
Hi, you have 3 drivers installed that are conflicting with each other.

You have an internal card and the usb adapter at present, if you want to use the usb adapter we will blacklist the other drivers and see if we can get it working or we can try to get your internal card working.
Thank you

---

### Post by LearningPerson on 2011-12-06
Yes, it does look like it will connect as it sometimes puts the ESSID in and sometimes put the Access Point in but it never gets there for more than a couple of minutes - if at all.   It will often say "bad password".

What I'm trying to do is to share bandwidth with my neighbor.  His laptop placed where I have my pc whoed a strong connection and no problem. He has placed his receiver in his window which isn't more than 70' away from my pc. When I try, my WICD says I have 30-40% signal strength.

I'm using Infrastructure and wonder if I should do Ad-Hoc?

  Not that I know what either of those means.

I think I might have everything but it's just not setup right somehow.

---

### Post by LearningPerson on 2011-12-06
OK, how do I blacklist and which ones?

---

### Post by wildmanne39 on 2011-12-06
Hi, do not change Infrastructure.

Please do the following commands just copy and paste them.
```
sudo su
echo "blacklist ath9k_htc" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
exit
```
Then:
```
sudo modprobe rtl8187
```
Reboot with wired connection unplugged.

Also that signal strength is weak you may not be able to connect at 30 to 40.

I will be off a little while for dinner.

---

### Post by F.G. on 2011-12-06
sorry learningperson, it sounds like i may have given you some incorrect advice. 

good luck getting your wifi going.

---

### Post by LearningPerson on 2011-12-06
Oh brother!  Here's what I did....and got:

```


~$ echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf

bash: /etc/modprobe.d/blacklist.conf: Permission denied


sharon@sharon-desktop:~$ sudo echo "blacklist ath9k_htc" >> /etc/modprobe.d/blacklist.conf

bash: /etc/modprobe.d/blacklist.conf: Permission denied



```

Sharon

---

### Post by bluexrider on 2011-12-06
OMG i'm getting a headache reading this thread. I just went to the store for dog food....what did you do

the adapter must be a realtek I found a listing for it  here [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)

and here 

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

in the read me file it has a complete instruction on how to install.

---

### Post by LearningPerson on 2011-12-06
Yeah, bluexrider, me too!

At this point,  wildmanne is trying to help me blacklist some drivers - evidently I have an embarrassment of drivers.  However, when I tried to input the commands to blacklist a few, I see that permission was denied so I'll have to wait for wildmanne to finish his dinner.

---

### Post by bluexrider on 2011-12-06
> **LearningPerson said:**
> Yeah, bluexrider, me too!

At this point,  wildmanne is trying to help me blacklist some drivers - evidently I have an embarrassment of drivers.  However, when I tried to input the commands to blacklist a few, I see that permission was denied so I'll have to wait for wildmanne to finish his dinner.


Okay well sounds like you are in good hands. sorry for the late post.

---

### Post by LearningPerson on 2011-12-06
Yes, but with 3 drivers, do I want to install more?  Or how can I get rid of the others and just use this one other than the "blacklist" command which didn't seem to work for me.

---

### Post by wildmanne39 on 2011-12-06
Hi, sorry I left out one important part of the blacklist command I was trying to post before my dinner got cold I am going to correct it in my last post then try to blacklist the drivers again.
Thank you

---

### Post by dFlyer on 2011-12-06
after you clean out the files you don't need, in the future just right click on the file you want to un-tar and select extract here. This is quicker than using the command line.

---

### Post by LearningPerson on 2011-12-06
Actually here is what happened (nothing):

```
  ~$ sudo modprobe rtl8187
[sudo] password for sharon: 
sharon@sharon-desktop:~$ 

```

---

### Post by LearningPerson on 2011-12-06
I didn't install the rtl8187 which is the driver for the Alfa.  Bluexrider gave me his link: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)    When  click on the US1 (West Coast) I get a pop-up from RealTek but it isn't clear what I do after that?

---

### Post by wildmanne39 on 2011-12-07
The driver is already installed it came with ubuntu as I stated before, that command was not suppose to show anything it had a job to do and it would have only showed output if it failed.

Did you reboot your computer with the wired connection unplugged? 

We may need to dig deeper but I will need you to not try anything but what I ask or it will undo or progress.
Thank you

---

### Post by wildmanne39 on 2011-12-07
Hi, please post the results of these commands if it is not connecting still.
```
nm-tool
```
```
iwconfig
```
```
sudo iwlist scan
```
```
dmesg | egrep 'rtl|firm|wpa|etwork'
```
Thank you

---

### Post by LearningPerson on 2011-12-07
OK, here it is:

```
 ~$ nm-tool

The program 'nm-tool' is currently not installed.  You can install it by typing:

sudo apt-get install network-manager

sharon@sharon-desktop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



sharon@sharon-desktop:~$ sudo iwlist scan

[sudo] password for sharon: 

Sorry, try again.

[sudo] password for sharon: 

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



sharon@sharon-desktop:~$ dmesg | egrep 'rtl|firm|wpa|etwork'

[   21.972875] type=1505 audit(1323233136.514:3):  operation="profile_load" pid=700 name="/usr/lib/NetworkManager/nm-dhcp-client.action"

[   45.555699] type=1505 audit(1323233160.094:7):  operation="profile_replace" pid=980 name="/usr/lib/NetworkManager/nm-dhcp-client.action"

[  188.709323] ieee80211 phy0: hwaddr 00:c0:ca:4f:7d:0a, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2

[  188.722653] rtl8187: Customer ID is 0xFF

[  188.722725] Registered led device: rtl8187-phy0::radio

[  188.722752] Registered led device: rtl8187-phy0::tx

[  188.722780] Registered led device: rtl8187-phy0::rx

[  188.726648] rtl8187: wireless switch is on

[  188.726712] usbcore: registered new interface driver rtl8187

[  188.767768] udev: renamed network interface wlan0 to wlan1

[  250.037713] ieee80211 phy1: hwaddr 00:c0:ca:4f:7d:0a, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2

[  250.052162] udev: renamed network interface wlan0 to wlan1

[  250.055733] rtl8187: Customer ID is 0xFF

[  250.055829] Registered led device: rtl8187-phy1::radio

[  250.055859] Registered led device: rtl8187-phy1::tx

[  250.055885] Registered led device: rtl8187-phy1::rx

[  250.058613] rtl8187: wireless switch is on
 
```

---

### Post by wildmanne39 on 2011-12-07
Hi, 2 of the commands produced no results and that was information I really needed, let's try these commands and see if I can get good information:
```
lsmod | grep rtl
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e etwork | tail -n55
```
Did you setup your connection when you installed wicd? it should be wlan0.

We may have to install network manager and nm-tool so I can see some of the information that did not show up.

Is your neighbors router encrypted and what is it set too? Linux works best with just wpa2 and not mixed mode.
Thank you

---

### Post by LearningPerson on 2011-12-07
```
  lsmod | grep rtl
rtl8187                50485  0 
eeprom_93cx6            1333  1 rtl8187
mac80211              247057  2 rtl8187,ath9k_htc
cfg80211              151118  4 rtl8187,ath9k_htc,mac80211,ath
compat                  7331  4 rtl8187,ath9k_htc,mac80211,cfg80211
led_class               2864  3 rtl8187,ath9k_htc,compat
sharon@sharon-desktop:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e etwork | tail -n55
[sudo] password for sharon: 
Dec  6 18:12:19 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:12:20 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:17:56 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:17:57 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:17:57 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:22:46 sharon-desktop kernel: [42696.901048] ieee80211 phy2: hwaddr 00:c0:ca:4f:7d:0a, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
Dec  6 18:22:46 sharon-desktop kernel: [42696.917431] rtl8187: Customer ID is 0xFF
Dec  6 18:22:46 sharon-desktop kernel: [42696.918170] Registered led device: rtl8187-phy2::radio
Dec  6 18:22:46 sharon-desktop kernel: [42696.918567] Registered led device: rtl8187-phy2::tx
Dec  6 18:22:46 sharon-desktop kernel: [42696.918939] Registered led device: rtl8187-phy2::rx
Dec  6 18:22:46 sharon-desktop kernel: [42696.919793] rtl8187: wireless switch is on
Dec  6 18:23:02 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:23:02 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:23:03 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:23:41 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:23:41 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:23:53 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:23:53 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 18:23:53 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 20:43:40 sharon-desktop init: Failed to spawn network-manager main process: unable to execute: No such file or directory
Dec  6 20:43:40 sharon-desktop kernel: [   22.188884] type=1505 audit(1323233019.730:3):  operation="profile_load" pid=768 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec  6 20:43:40 sharon-desktop kernel: [   22.191728] type=1505 audit(1323233019.730:6):  operation="profile_replace" pid=779 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec  6 20:43:40 sharon-desktop kernel: [   22.619642] type=1505 audit(1323233020.158:9):  operation="profile_replace" pid=956 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec  6 20:43:40 sharon-desktop avahi-daemon[953]: Network interface enumeration completed.
Dec  6 20:43:50 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 20:43:50 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 20:44:35 sharon-desktop kernel: [   77.815325] ieee80211 phy0: hwaddr 00:c0:ca:4f:7d:0a, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
Dec  6 20:44:35 sharon-desktop kernel: [   77.827937] rtl8187: Customer ID is 0xFF
Dec  6 20:44:35 sharon-desktop kernel: [   77.827990] Registered led device: rtl8187-phy0::radio
Dec  6 20:44:35 sharon-desktop kernel: [   77.828014] Registered led device: rtl8187-phy0::tx
Dec  6 20:44:35 sharon-desktop kernel: [   77.828036] Registered led device: rtl8187-phy0::rx
Dec  6 20:44:35 sharon-desktop kernel: [   77.833379] rtl8187: wireless switch is on
Dec  6 20:44:35 sharon-desktop kernel: [   77.833443] usbcore: registered new interface driver rtl8187
Dec  6 20:44:35 sharon-desktop kernel: [   77.865160] udev: renamed network interface wlan0 to wlan1
Dec  6 20:46:00 sharon-desktop init: Failed to spawn network-manager main process: unable to execute: No such file or directory
Dec  6 20:46:00 sharon-desktop kernel: [   21.972875] type=1505 audit(1323233136.514:3):  operation="profile_load" pid=700 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec  6 20:46:00 sharon-desktop kernel: [   45.555699] type=1505 audit(1323233160.094:7):  operation="profile_replace" pid=980 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec  6 20:46:00 sharon-desktop avahi-daemon[968]: Network interface enumeration completed.
Dec  6 20:46:08 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 20:46:08 sharon-desktop dhclient: send_packet: Network is unreachable
Dec  6 20:48:23 sharon-desktop kernel: [  188.709323] ieee80211 phy0: hwaddr 00:c0:ca:4f:7d:0a, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
Dec  6 20:48:23 sharon-desktop kernel: [  188.722653] rtl8187: Customer ID is 0xFF
Dec  6 20:48:23 sharon-desktop kernel: [  188.722725] Registered led device: rtl8187-phy0::radio
Dec  6 20:48:23 sharon-desktop kernel: [  188.722752] Registered led device: rtl8187-phy0::tx
Dec  6 20:48:23 sharon-desktop kernel: [  188.722780] Registered led device: rtl8187-phy0::rx
Dec  6 20:48:23 sharon-desktop kernel: [  188.726648] rtl8187: wireless switch is on
Dec  6 20:48:23 sharon-desktop kernel: [  188.726712] usbcore: registered new interface driver rtl8187
Dec  6 20:48:23 sharon-desktop kernel: [  188.767768] udev: renamed network interface wlan0 to wlan1
Dec  6 20:49:24 sharon-desktop kernel: [  250.037713] ieee80211 phy1: hwaddr 00:c0:ca:4f:7d:0a, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
Dec  6 20:49:24 sharon-desktop kernel: [  250.052162] udev: renamed network interface wlan0 to wlan1
Dec  6 20:49:24 sharon-desktop kernel: [  250.055733] rtl8187: Customer ID is 0xFF
Dec  6 20:49:24 sharon-desktop kernel: [  250.055829] Registered led device: rtl8187-phy1::radio
Dec  6 20:49:24 sharon-desktop kernel: [  250.055859] Registered led device: rtl8187-phy1::tx
Dec  6 20:49:24 sharon-desktop kernel: [  250.055885] Registered led device: rtl8187-phy1::rx
Dec  6 20:49:24 sharon-desktop kernel: [  250.058613] rtl8187: wireless switch is on

```

I'll remove WICD and install Network Manager now.

---

### Post by wildmanne39 on 2011-12-07
Hi, just a minute and I will tell you how to do it safely.

---

### Post by wildmanne39 on 2011-12-07
Here is how to do it safely.
```
sudo apt-get install network-manager network-manager-gnome
```
Then open software center and remove all packages related to wicd.
Reboot
Thank you

---

### Post by LearningPerson on 2011-12-07
Umm, I removed WICD (but not WICD-GTK) and installed Network Manager and NM Gnome.  Will this be a problem?  Now I'm supposed to reboot.

---

### Post by LearningPerson on 2011-12-07
Umm,  in Synaptic, I just removed WICD (but not WICD-GTK) and installed Network Manager and Network Manager - Gnome.  Now I'm supposed to reboot.  Will this be a problem?

---

### Post by wildmanne39 on 2011-12-07
Hi, yes uninstall anything that says wicd.

Also some of the drivers did not blacklist properly only one of them did so we need to try again, and with network manager you will not have to manually setup your connection it should find it and ask for the password.
```
sudo su
echo "blacklist ath9k_htc" >> /etc/modprobe.d/blacklist.conf
echo "blacklist compat" >> /etc/modprobe.d/blacklist.conf
exit
```
Then Reboot

---

### Post by LearningPerson on 2011-12-07
OK, I've rebooted but did not plug in the USB Adapter yet. I don't see any wireless listed from the Network manager icon.

---

### Post by wildmanne39 on 2011-12-07
Hi, you need to reboot with the usb plugged in and hopefully it will find a network but remember the signal strength is weak I do not think it will connect if it gets lower then about 50 percent and the weaker the signal the slower the connection.

I need to get off here for the night it is getting late but I will be back on tomorrow to help if you still need it.

---

### Post by LearningPerson on 2011-12-07
Thanks for your help! I'll see what happens tomorrow.

---

### Post by bluexrider on 2011-12-07
> **LearningPerson said:**
> Thanks for your help! I'll see what happens tomorrow.

are we there yet. the drama unfolds...

---

### Post by LearningPerson on 2011-12-07
Good morning, wildmanne,

I have had a connection for 30 minutes at over 70% signal strength.  I chose Auto DHCP on the connection at IPv4 which seems to work though I didn't input a DHCP Client ID.  Although the speed at Active Network Connection says 36-64Mb/s; bandwidthplace says I have 4.34 Mpbs Download and 2.18 Upload.

I turn off my PC each night  will that be a problem?  Should I unplug the USB adapter first?  Or ?  Don't want to do a thing until you say!

Can I call Qwest and get rid of my wired connection now?

Sharon

---

### Post by LearningPerson on 2011-12-07
OMG, bluexrider,  see my last post.  Not sure how or what made it happen but I've been connected now for over 45 min. You and wildmanne stuck with me - did you notice he's from Roswell, NM?   I wonder.....

Will watch for a day here and then check in later to let you both know the status.

Thanks, Sharon

---

### Post by bluexrider on 2011-12-07
> **LearningPerson said:**
> OMG, bluexrider,  see my last post.  Not sure how or what made it happen but I've been connected now for over 45 min. You and wildmanne stuck with me - did you notice he's from Roswell, NM?   I wonder.....

Will watch for a day here and then check in later to let you both know the status.

Thanks, Sharon
Glad you got it going. NO I didn't notice but now that you mention it, really! Roswell.....humm :P

happy *buntu until nex time

---

### Post by LearningPerson on 2011-12-07
Wildmanne and bluexrider,  The wireless has been working all day now with several re-boots.  I'll try an upgrade to 2.6.32-36 and see if it still works.

Thanks so much.  

Sharon

---

### Post by wildmanne39 on 2011-12-07
Hi, I am glad it is working, I was pretty sure once the drivers were properly blacklisted with network manager installed it would since the driver you needed comes with ubuntu.

As for getting rid of your wired connection that is up to you, but I have found that a wired connection will be needed at some point to get wireless to work again after an upgrade and such.

If it continues to work please mark as solved,  also it is not a good idea to upgrade to a new release with an wireless connection because when the updates are downloading and installing you will usually loose the wireless connection and it will leave you with broken system.

My computer crashed today I am doing backups so I can reinstall so it will be at least two days before I will be back on.

---

