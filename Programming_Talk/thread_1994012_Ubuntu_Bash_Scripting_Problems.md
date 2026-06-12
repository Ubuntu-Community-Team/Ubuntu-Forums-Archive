---
title: "Ubuntu Bash Scripting Problems"
date: 2012-06-02
forum: Programming Talk
---

### Post by Samwise Gamgee on 2012-06-02
I am trying to make a script to maintain my ad-hoc network while I play on XboxLIVE because my 3G modem becomes undetected while I play. It is almost like the computer pulls out the 3G modem (Cricket). For example, while my internet is working, nmcli returns that "cricket internet" exists, but after it doesn't display the connection. I have to restart the network manager when this happens and restart my connection to the network (made by the xbox) and cricket. I thought I could make a script do this, and so far I have gotten this:
```

#!/bin/bash
msgneeded=1
while true; do
    #Check state of network
    #I really don't completely understand these two lines (I know nmcli though)
    LC_ALL=C nmcli -t -f TYPE,STATE dev | grep -q "^cdma:disconnected$"
    if [ $? -eq 0 ]; then
        msgneeded=1
        echo `notify-send -u normal -t 5 "Warning" "Cricket Internet is disconnected!"`
        #Re-enable mobile broadband if down
        nmcli -t nm wwan off
        sleep 1
        nmcli -t nm wwan on
        sleep 1
        nmcli -t con up id "Cricket Internet"
        #wait approximately 15 sec to get connected
        sleep 15
        #Timeout for connecting (Tested and took 10 secs to connect, 5 extra for security)
    fi
    if [ $msgneeded = 1 ]; then
    echo `notify-send -u normal -t 5 "Connection Stable" "Cricket Internet is connected."`
    msgneeded=0 
    fi
    #Do no overload the poor computer
    sleep 2  
done

```This script works fine if I simply disconnect, but doesn't if Ubuntu can't detect the Cricket modem. I want the script to detect the device instead of the connection and restart the network stuff (like I said I did) and reconnect. Any pointers welcomed. I just learned bash scripting last night (and had many problems with the syntax)

Update: Would changed the two lines checking to network state to:
LC_ALL=C nmcli -t -f TYPE,STATE dev | grep -c "^cdma:connected$"
    if [ $? -lt 1 ]; then
fix that part, if so please tell me the script to restart network manager(sudo service network-manager restart) and how to tell it to connect to the connections.

---

### Post by josephmills on 2012-06-02
This is not going to work for you but might be able to give you a better idea on how to arrange this script 
**EDITING COLOR**
DONE 
```
#!/usr/bin/env bash
##############
##Making VAR #
##############
msgneeded=1
[COLOR="PaleGreen"]dis[/COLOR]=[COLOR="YellowGreen"]$([/color]notify-send -u normal -t 5 "Warning" "Cricket Internet is disconnected!"[COLOR="YellowGreen"])[/color]
conn=[COLOR="YellowGreen"]$([/COLOR]notify-send -u normal -t 5 "Connection Stable" "Cricket Internet is connected."[COLOR="YellowGreen"])[/COLOR]

```
make all you var at top so you can change faster 
Notice how I am using [COLOR="YellowGreen"]$( [/COLOR]command[COLOR="YellowGreen"] )  [/COLOR]to get the output and not the ` does the same thing but the ` are old and out dated 

```

###################
# Making Function #
###################

function [COLOR="Red"]funky1[/COLOR](){
nmcli -t nm wwan off
sleep 1
nmcli -t nm wwan on
sleep 1
nmcli -t con up id "Cricket Internet"
sleep 15
}
```

Pulling in functions can often save time and energy looking for things later on.

function [COLOR="red"]funky1[/COLOR]()    <-- declaring the function 
{
commands
to run 
the function.
}


```
[COLOR="DeepSkyBlue"] if [/COLOR] [COLOR="DarkOrange"]C nmcli -t -f TYPE,STATE dev | grep -q "^cdma:disconnected$"[/COLOR];[COLOR="DeepSkyBlue"]then[/color]
   [COLOR="DarkOrange"] echo "[/color][COLOR="PaleGreen"]$dis[/COLOR][COLOR="DarkOrange"]"[/color]
[COLOR="DeepSkyBlue"] else [/COLOR] 
    [COLOR="red"] funky1 [/COLOR]    
[COLOR="DeepSkyBlue"] fi [/COLOR]
```

here we just run the if statement 

like 

```

[COLOR="DeepSkyBlue"]if[/color][COLOR="DarkOrange"] command[/COLOR];[COLOR="DeepSkyBlue"]then[/color] 
[COLOR="DarkOrange"]     string of commands;[/color]
[COLOR="DeepSkyBlue"]else[/color]
[COLOR="DarkOrange"]    other things to do;[/color]
[COLOR="DeepSkyBlue"]fi[/color]

```

---

### Post by josephmills on 2012-06-02
> **Samwise Gamgee said:**
> 
Update: Would changed the two lines checking to network state to:
LC_ALL=C nmcli -t -f TYPE,STATE dev | grep -c "^cdma:connected$"
    if [ $? -lt 1 ]; then
fix that part, if so please tell me the script to restart network manager(sudo service network-manager restart) and how to tell it to connect to the connections.


Not sure what you mean sam 

could you tell us 100% what you are trying to do ?

---

### Post by Samwise Gamgee on 2012-06-02
I fixed the part I suggested to where it works, so ignore that, but I want to restart the network manager service, which I do by entering "sudo service network-manager restart" into the terminal, in a bash script that doesn't require a password, and then reconnect to the ad-hoc network my xbox made and reconnect to my cricket modem. This is what I do, when the problem arises, to fix it. I didn't want to have to go to my computer, I wanted the computer to do this itself

---

### Post by Samwise Gamgee on 2012-06-02
I used:
```
function  reconnect (){
sudo service network-manager stop
sleep 5
sudo service network-manager start
sleep 5
nmcli -t con up id "Cricket Internet"
sleep 15
}
```
as my reconnect function, however, when the network manager successfully restarted, Ubuntu started the Cricket 3G modem and said it was a wired connection and didn't work

---

### Post by josephmills on 2012-06-02
make sure that all the devices are pluged in then run 

```
lspci -nn && lsusb
```

then paste hat here please and thanks :)

---

### Post by Samwise Gamgee on 2012-06-02
austin@UbuntuFlashDrive:~$ lspci -nn && lsusb
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge [1106:3205]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:0a.0 Modem [0703]: SILICON Laboratories Intel 537 [Winmodem] [1543:3052] (rev 04)
00:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV350 AS [Radeon 9550] [1002:4153]
01:00.1 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI RV350 AS [Radeon 9550] (Secondary) [1002:4173]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 005: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 006: ID 0781:5530 SanDisk Corp. Cruzer
Bus 002 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 015: ID 106c:3717 Curitel Communications, Inc. 
austin@UbuntuFlashDrive:~$ lspci -nn && lsmod
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge [1106:3205]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:0a.0 Modem [0703]: SILICON Laboratories Intel 537 [Winmodem] [1543:3052] (rev 04)
00:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV350 AS [Radeon 9550] [1002:4153]
01:00.1 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI RV350 AS [Radeon 9550] (Secondary) [1002:4173]
Module                  Size  Used by
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52412  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13553  1 nf_nat_pptp
nf_conntrack_proto_gre    13395  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16921  0 
nf_conntrack_sip       24749  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
iptable_nat            13016  0 
nf_nat                 24959  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           73847  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21974  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12595  1 ppp_async
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
dm_crypt               22528  1 
cdc_acm                22306  3 
snd_via82xx            24719  2 
ndiswrapper           196722  0 
gameport               15060  1 snd_via82xx
snd_via82xx_modem      18377  0 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87213  0 
snd                    62064  13 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
i2c_viapro             12969  0 
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              14635  1 snd
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  8 bnep,rfcomm
ppdev                  12849  0 
parport_pc             32114  1 
shpchp                 32325  0 
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
radeon                729591  3 
ttm                    65344  1 radeon
via_rhine              27413  0 
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
sata_via               13495  0 
pata_via               13428  1 
crc_itu_t              12627  1 firewire_core
i2c_algo_bit           13199  1 radeon
usb_storage            39646  2

---

### Post by Samwise Gamgee on 2012-06-02
Is there a way to make ubuntu drop a usb port and reconnect it, because i have to replace the 3g modem after restarting network manager

---

