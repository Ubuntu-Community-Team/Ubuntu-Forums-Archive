---
title: "wireless problem"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by jpbjomar on 2011-12-17
I installed Ubuntu 11.10 within Windows XP on my PC and I cannot get the wireless to work.  It tells me it is connected but when I go to Firefox it says "cannot find server ... check connecttion, firewall settings" etc.  The wireless network card is an add-on.
I have internet on laptop.  Pretty sure all the connection info was correct. 

Any help will be much appreciated.

---

### Post by mikewhatever on 2011-12-17
...and what is the model of the add-on wireless card?

Can you post the output of the following:
```
lspci -knn | grep Net -A2
```

---

### Post by jpbjomar on 2011-12-17
it's D-link wireless N 150    DWA-525
Newbee
I just installed and I cannot find the where to write the code?

---

### Post by astrognome on 2011-12-17
Type the code in a terminal.  To open a terminal, click on Applications --> Accessories --> Terminal.  Go ahead and copy and paste the whole output into the forum here.

---

### Post by jpbjomar on 2011-12-17
OMG   I cannot find it.  I found where I needed to install it but now WTF is it?  I cannot find your "applications" start point.  
Very frustrating.

---

### Post by astrognome on 2011-12-17
It should be the main menu on the screen - adjacent to the ubuntu logo in the upper left corner.

---

### Post by Ms. Daisy on 2011-12-17
or to open a terminal you can type 
Ctl + Alt + T

---

### Post by jpbjomar on 2011-12-17
Nope.  this is Ubuntu 11.10 in the upper left corner is "desktop".  If I roll over it with the mouse file, veiw, go,etc appear. then down the left side it has some icon.  the only one looks important is gear/wrench.  that's where i found install terminal. 
obviously, I'm no genius but it sucks if you cannot even find the terminal. 

sorry.  i gotta take a break before i go nuts

Later
Thanks

---

### Post by wildmanne39 on 2011-12-17
Hi, if you do what Ms. Daisy mentioned you can open a terminal then copy and paste that command into it, then enter your password, it will not show as you type the password when you are done typing it just hit enter, then post the results here.
Thanks

---

### Post by jpbjomar on 2011-12-17
Thanks M daisy


jack@ubuntu:~$ lspci -knn l grep Net -A2

lspci: No such PCI access method: 2 (see `-A help' for a list)

jack@ubuntu:~$ lspci -knn I grep Net -A2

lspci: No such PCI access method: 2 (see `-A help' for a list)

jack@ubuntu:~$ -A help

-A: command not found

jack@ubuntu:~$ lspci -knn l grep Net -A help

Known PCI access methods:

linux-sysfs

linux-proc

intel-conf1

intel-conf2

dump

jack@ubuntu:~$

---

### Post by mikewhatever on 2011-12-17
Try copy/pasting the command instead of typing it. If that's not possible, note that the symbol between **lspci -knn** and **grep Net -A2** is not an [SIZE="4"]**L**[/SIZE], it's [SIZE="4"]**|**[/SIZE]. It's usually located on the same key as [SIZE="4"]**\**[/SIZE].

It should look something like this:

```

~$ lspci -knn | grep Net -A2
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Hewlett-Packard Company Compaq 6710b or nx9420 Notebook [103c:135c]
	Kernel driver in use: iwl3945
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:30a5]
	Kernel driver in use: e100

```

---

### Post by bluexrider on 2011-12-18
> **mikewhatever said:**
> Try copy/pasting the command instead of typing it. If that's not possible, note that the symbol between **lspci -knn** and **grep Net -A2** is not an [SIZE=4]**L**[/SIZE], it's [SIZE=4]**|**[/SIZE]. It's usually located on the same key as [SIZE=4]**\**[/SIZE].

It should look something like this:

```

~$ lspci -knn | grep Net -A2
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Compaq 6710b or nx9420 Notebook [103c:135c]
    Kernel driver in use: iwl3945
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: e100

```
bring it down a notch. You have a OP that is "NEW" and needs guidance and I think understanding.

---

### Post by mikewhatever on 2011-12-18
> **bluexrider said:**
> bring it down a notch. You have a OP that is "NEW" and needs guidance and I think understanding.

If you can suggest something better, please do. Admonishing others or understanding doesn't solve problems.
:P

---

### Post by jpbjomar on 2011-12-18
Sorry guys.  I didn't notice there was a 'page 2' to this thread.

I did what you asked and got this:

 lspci -knn | grep Net -A2

00:0b.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]

 Subsystem: D-Link System Inc DWA-525 Wireless N 150 Desktop Adapter (rev.A1) [1186:3c04]

 Kernel driver in use: rt2800pci

jack@ubuntu:~$ 06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

bash: syntax error near unexpected token `('

jack@ubuntu:~$     Subsystem: Hewlett-Packard Company Compaq 6710b or nx9420 Notebook [103c:135c]

Subsystem:: command not found

jack@ubuntu:~$     Kernel driver in use: iwl3945

Kernel: command not found

jack@ubuntu:~$ --

--: command not found

jack@ubuntu:~$ 08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)

bash: syntax error near unexpected token `('

jack@ubuntu:~$     Subsystem: Hewlett-Packard Company Device [103c:30a5]

Subsystem:: command not found

jack@ubuntu:~$     Kernel driver in use: e10

---

### Post by jpbjomar on 2011-12-18
oops.  I think I copied and pasted too much.  But I re-did it and the ssame info is in the last post.  just a little extra.

Sorry.  I do not have internet.  So I must copy to a stick and bring to laptop that has internet.  and vise versa.

---

### Post by lsemmens on 2011-12-18
Just as a thought, [jpbjomar]("http://ubuntuforums.org/member.php?u=1513161"), if you have access to a wired access point, I have found that my lappy works fine while wired but has the same issues as you have when attempting wireless (which was never an issue with windoze). I am now following this thread with interest.

---

### Post by bluexrider on 2011-12-18
> **mikewhatever said:**
> If you can suggest something better, please do. Admonishing others or understanding doesn't solve problems.
:P

I see you were trying to [SIZE=3]**make a point**[/SIZE].

---

### Post by mikewhatever on 2011-12-18
> **bluexrider said:**
> I see you were trying to [SIZE=3]**make a point**[/SIZE].

No. I was trying to show the difference between l and |, which isn't readily discernible. Fairly obvious, isn't it?

Why don't you make yourself useful and try helping the OP instead of trolling.

---

### Post by wildmanne39 on 2011-12-18
Hi jpbjomar, you have two wireless cards present and both have drivers loaded that are causing a conflict, which one do you want to use or does it matter? Please show the results of:
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jpbjomar on 2011-12-19
I think I only have one card.  
I think I copied by accident somones demo..


lsmod

Module                  Size  Used by

nls_utf8               12493  1 

isofs                  39549  1 

nls_iso8859_1          12617  1 

nls_cp437              12751  1 

vfat                   17308  1 

fat                    55577  1 vfat

ipt_MASQUERADE         12663  1 

xt_state               12514  1 

ipt_REJECT             12512  2 

xt_tcpudp              12531  4 

iptable_filter         12706  1 

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

iptable_nat            13016  1 

nf_nat                 24958  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat

nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat

nf_conntrack           70103  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4

nf_defrag_ipv4         12649  1 nf_conntrack_ipv4

ip_tables              18106  2 iptable_filter,iptable_nat

x_tables               21975  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables

rfcomm                 38408  0 

bnep                   17923  2 

bluetooth             148839  10 rfcomm,bnep

binfmt_misc            17292  1 

ppdev                  12849  0 

snd_wavefront          34737  0 

snd_intel8x0           33318  2 

snd_ac97_codec        106082  1 snd_intel8x0

ac97_bus               12642  1 snd_ac97_codec

snd_cs4236             29294  0 

snd_wss_lib            30063  2 snd_wavefront,snd_cs4236

snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236

snd_hwdep              13276  2 snd_wavefront,snd_opl3_lib

arc4                   12473  2 

rt2800pci              18340  0 

snd_pcm                80468  4 snd_intel8x0,snd_ac97_codec,snd_cs4236,snd_wss_lib

rt2800lib              48717  1 rt2800pci

crc_ccitt              12595  1 rt2800lib

snd_mpu401             13847  0 

snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401

rt2x00pci              14202  1 rt2800pci

joydev                 17393  0 

rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci

nouveau               663211  3 

snd_seq_midi           13132  0 

mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib

snd_rawmidi            25241  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi

cfg80211              172392  2 rt2x00lib,mac80211

snd_seq_midi_event     14475  1 snd_seq_midi

ttm                    65224  1 nouveau

drm_kms_helper         32889  1 nouveau

eeprom_93cx6           12653  1 rt2800pci

snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event

drm                   192226  5 nouveau,ttm,drm_kms_helper

snd_timer              28932  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq

snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq

i2c_algo_bit           13199  1 nouveau

mxm_wmi                12859  1 nouveau

snd                    55902  18 snd_wavefront,snd_intel8x0,snd_ac97_codec,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

snd_page_alloc         14115  3 snd_intel8x0,snd_wss_lib,snd_pcm

wmi                    18744  1 mxm_wmi

video                  18908  1 nouveau

ns558                  12654  0 

soundcore              12600  1 snd

gameport               15060  2 ns558

parport_pc             32114  1 

i2c_sis96x             12743  0 

shpchp                 32356  0 

sis_agp                13165  1 

lp                     17455  0 

parport                40930  3 ppdev,parport_pc,lp

usb_storage            44173  2 

uas                    17699  0 

usbhid                 41905  0 

hid                    77367  1 usbhid

firewire_ohci          35854  0 

firewire_core          56937  1 firewire_ohci

crc_itu_t              12627  1 firewire_core

floppy                 60310  0

---

### Post by jpbjomar on 2011-12-19
Some more info.
My apartment has free wifi. It works on my laptop and my PC.  When I installed Ubuntu on the PC the internet doesn't work. If I re-boot back to XP it works.
I don't have a wired connection.

---

### Post by wildmanne39 on 2011-12-19
Hi, all right I need more information please run these commands and a couple that was already ran just to make sure about the wireless cards because seeing more then one and you say you only have one is confusing.
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Run the commands one line at a time.
Thank you

---

### Post by mikewhatever on 2011-12-19
Since the OP doesn't have wired internet, perhaps it would be more convenient to dump all the outputs into a file.

jpbjomar, the following will create a text file, wifi-info.txt, on your desktop and copy all the outputs into it.

```

cat /etc/lsb-release > ~/Desktop/wifi-info.txt

uname -a >> ~/Desktop/wifi-info.txt

lspci -nnk | grep -iA2 net >> ~/Desktop/wifi-info.txt

iwconfig >> ~/Desktop/wifi-info.txt

rfkill list all >> ~/Desktop/wifi-info.txt

lsmod >> ~/Desktop/wifi-info.txt

```

As before, copy/paste instead of typing.

---

### Post by jpbjomar on 2011-12-20
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.10 
DISTRIB_CODENAME=oneiric 
DISTRIB_DESCRIPTION="Ubuntu 11.10" 
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux 
00:0b.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060] 
	Subsystem: D-Link System Inc DWA-525 Wireless N 150 Desktop Adapter (rev.A1) [1186:3c04] 
	Kernel driver in use: rt2800pci 
wlan0     IEEE 802.11bgn  ESSID:"NH5960"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: BE:64:7E:D5:14:F6   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
Module                  Size  Used by 
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55577  1 vfat 
ipt_MASQUERADE         12663  1 
xt_state               12514  1 
ipt_REJECT             12512  2 
xt_tcpudp              12531  4 
iptable_filter         12706  1 
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
iptable_nat            13016  1 
nf_nat                 24958  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat 
nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat 
nf_conntrack           70103  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4 
ip_tables              18106  2 iptable_filter,iptable_nat 
x_tables               21975  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm 
binfmt_misc            17292  1 
ppdev                  12849  0 
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48717  1 rt2800pci 
snd_wavefront          34737  0 
crc_ccitt              12595  1 rt2800lib 
nouveau               663211  3 
rt2x00pci              14202  1 rt2800pci 
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci 
snd_cs4236             29294  0 
snd_wss_lib            30063  2 snd_wavefront,snd_cs4236 
snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236 
snd_hwdep              13276  2 snd_wavefront,snd_opl3_lib 
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0 
joydev                 17393  0 
ac97_bus               12642  1 snd_ac97_codec 
snd_pcm                80468  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec 
snd_mpu401             13847  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401 
ttm                    65224  1 nouveau 
drm_kms_helper         32889  1 nouveau 
cfg80211              172392  2 rt2x00lib,mac80211 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi 
eeprom_93cx6           12653  1 rt2800pci 
drm                   192226  5 nouveau,ttm,drm_kms_helper 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
snd_rawmidi            25241  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi 
i2c_algo_bit           13199  1 nouveau 
mxm_wmi                12859  1 nouveau 
ns558                  12654  0 
wmi                    18744  1 mxm_wmi 
snd_timer              28932  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq 
gameport               15060  2 ns558 
video                  18908  1 nouveau 
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_seq,snd_rawmidi 
snd                    55902  18 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq,snd_rawmidi,snd_timer,snd_seq_device 
parport_pc             32114  1 
soundcore              12600  1 snd 
snd_page_alloc         14115  3 snd_wss_lib,snd_intel8x0,snd_pcm 
i2c_sis96x             12743  0 
shpchp                 32356  0 
sis_agp                13165  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp 
usb_storage            44173  2 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci 
crc_itu_t              12627  1 firewire_core 
floppy                 60310  0 



Thanks for all the help and I apologize for the delays.  Probably the time difference doesn't help plus I needed to go to work.

---

### Post by mikewhatever on 2011-12-20
```
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.10 
DISTRIB_CODENAME=oneiric 
DISTRIB_DESCRIPTION="Ubuntu 11.10" 


Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux 


00:0b.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060] 
	Subsystem: D-Link System Inc DWA-525 Wireless N 150 Desktop Adapter (rev.A1) [1186:3c04] 
	Kernel driver in use: rt2800pci 


wlan0     IEEE 802.11bgn  ESSID:"NH5960"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: BE:64:7E:D5:14:F6   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          

0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 


Module                  Size  Used by 
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55577  1 vfat 
ipt_MASQUERADE         12663  1 
xt_state               12514  1 
ipt_REJECT             12512  2 
xt_tcpudp              12531  4 
iptable_filter         12706  1 
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
iptable_nat            13016  1 
nf_nat                 24958  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat 
nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat 
nf_conntrack           70103  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4 
ip_tables              18106  2 iptable_filter,iptable_nat 
x_tables               21975  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm 
binfmt_misc            17292  1 
ppdev                  12849  0 
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48717  1 rt2800pci 
snd_wavefront          34737  0 
crc_ccitt              12595  1 rt2800lib 
nouveau               663211  3 
rt2x00pci              14202  1 rt2800pci 
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci 
snd_cs4236             29294  0 
snd_wss_lib            30063  2 snd_wavefront,snd_cs4236 
snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236 
snd_hwdep              13276  2 snd_wavefront,snd_opl3_lib 
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0 
joydev                 17393  0 
ac97_bus               12642  1 snd_ac97_codec 
snd_pcm                80468  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec 
snd_mpu401             13847  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401 
ttm                    65224  1 nouveau 
drm_kms_helper         32889  1 nouveau 
cfg80211              172392  2 rt2x00lib,mac80211 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi 
eeprom_93cx6           12653  1 rt2800pci 
drm                   192226  5 nouveau,ttm,drm_kms_helper 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
snd_rawmidi            25241  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi 
i2c_algo_bit           13199  1 nouveau 
mxm_wmi                12859  1 nouveau 
ns558                  12654  0 
wmi                    18744  1 mxm_wmi 
snd_timer              28932  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq 
gameport               15060  2 ns558 
video                  18908  1 nouveau 
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_seq,snd_rawmidi 
snd                    55902  18 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq,snd_rawmidi,snd_timer,snd_seq_device 
parport_pc             32114  1 
soundcore              12600  1 snd 
snd_page_alloc         14115  3 snd_wss_lib,snd_intel8x0,snd_pcm 
i2c_sis96x             12743  0 
shpchp                 32356  0 
sis_agp                13165  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp 
usb_storage            44173  2 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci 
crc_itu_t              12627  1 firewire_core 
floppy                 60310  0 


```

It says that you are connected to the access point NH5960.

---

### Post by jpbjomar on 2011-12-20
okay.  the browser with Ubuntu is Firefox.  It won't open anything.  says to check connection, confirm address etc.  I tried the basic; google, yahoo, ubuntu start and get nothing.   I also tried to open something from the "ubuntu Software center' and it cannot access the internet either.  
I imagine I am overlooking something silly.

---

### Post by gandaran on 2011-12-20
> **jpbjomar said:**
> okay.  the browser with Ubuntu is Firefox.  It won't open anything.  says to check connection, confirm address etc.  I tried the basic; google, yahoo, ubuntu start and get nothing.   I also tried to open something from the "ubuntu Software center' and it cannot access the internet either.  
I imagine I am overlooking something silly.
could be a simple dns problem, click on the panel network manager icon » connection information, then post a screenshot of that window.

---

### Post by mikewhatever on 2011-12-20
Indeed. Alternatively, just post the output of **nm-tool** when connected to the AP.

---

### Post by jpbjomar on 2011-12-20
nm-tool 

NetworkManager Tool 

State: connected (global) 

- Device: wlan0  [NH5960] ------------------------------------------------------ 
  Type:              802.11 WiFi 
  Driver:            rt2800pci 
  State:             connected 
  Default:           no 
  HW Address:        1C:7E:E5:FC:85:FB 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points (* = current AP) 
    *NH5960:         Ad-Hoc, 6E:83:50:FB:02:00, Freq 2412 MHz, Rate 0 Mb/s, Strength 255 WEP 

  IPv4 Settings: 
    Address:         10.42.43.1 
    Prefix:          24 (255.255.255.0) 
    Gateway:         0.0.0.0

---

### Post by jpbjomar on 2011-12-20
The wireless internet works fine if I boot to Windows XP.  But not when I boot to Ubuntu.  I have tried disconnecting the connection in XP before booting to Ubuntu.

---

### Post by westie457 on 2011-12-20
Hi, someone will correct me if I am wrong, it looks to me like your network settings are wrong.

Starting with your second screenshot,you have it set as Ad-hoc, this should be set to 'Infrastructure'.

In the IPv4 tab this should be 'Automatic (DHCP)

In the IPv6 tab this should be set to ignore unless you need IPv6 routing.

---

### Post by wildmanne39 on 2011-12-20
Hi, westie457 is exactly correct making the changes he recommended should fix the problem.
Thanks

---

### Post by jpbjomar on 2011-12-21
That didn't work.  I had been playing with those settings and didn't put them back to original.

---

### Post by gandaran on 2011-12-21
> **jpbjomar said:**
> That didn't work.  I had been playing with those settings and didn't put them back to original.
look delete that wireless setup from network manager completely then reboot your computer and go to the panel network manager icon click on your network to connect, it should work automatically without you setting up any details.

---

### Post by jpbjomar on 2011-12-21
I tried to download from the software package just see if it might be possible which would indicate Firefox might be the problem but I can't download.


[ATTACH]209489[/ATTACH]

---

### Post by gandaran on 2011-12-21
also from the connection information screenshot the DNS and default route is missing, without both there's no internet.

---

### Post by jpbjomar on 2011-12-21
Okay.  deleted connection, rebooted went to the network manager and got this (see screenshot)
I cannot click in the network name.  My cursor cannot click into it.  make sense?

---

### Post by jpbjomar on 2011-12-21
[ATTACH]209490[/ATTACH]

sorry.

---

### Post by gandaran on 2011-12-21
so you don't see any networks detected on the network panel icon?
I believe yours is 'NH5960'

---

### Post by gandaran on 2011-12-21
or is your network set to hidden on the router?

---

### Post by jpbjomar on 2011-12-21
okay.  here we go .... I can get to the NH5960.  but it will not accept my key.  It is not the wrong key ... but I am FINALLY able to enter my key but the "Save" bnutton will not light up or activate.  Sometimes it will briefly light up but when I am not finished entering my code.  It does the same on a different window too.   It is a ligit code it is 'doraemon'   nothing fancy

can you see in the screenshot the "save" is not lit?

man this is it. I am ready to scrap this 11.10  




[ATTACH]209493[/ATTACH]

---

### Post by gandaran on 2011-12-21
> **jpbjomar said:**
> okay.  here we go .... I can get to the NH5960.  but it will not accept my key.  It is not the wrong key ... but I am FINALLY able to enter my key but the "Save" bnutton will not light up or activate.  Sometimes it will briefly light up but when I am not finished entering my code.  It does the same on a different window too.   It is a ligit code it is 'doraemon'   nothing fancy

can you see in the screenshot the "save" is not lit?

man this is it. I am ready to scrap this 11.10  




[ATTACH]209493[/ATTACH]
are you using the ubuntu account with administration rights (the one created when installing) or some other you created after?
also I'm still not understanding how you are trying to connect and why, if the network is detected you should just select it to connect then it will ask you for the password, you don't have to go on wireless settings to save the password.

---

### Post by jpbjomar on 2011-12-21
okay.  I didn't quite understand your last. 
But..
if I go to the network manager, for some reason I cannot enter the passcode.  It tries to connect but the enter passcode window keeps coming back, as if I am entering the wrong code.  
if I try to open a connection by clinking on the internet symbol in tthe upper right corner of my desk top I can enter all the info and it says I have internet connection. Can you see in the upper right corner?  the monitor insinuates I have connection.  A window appears saying just that - but I cannot catch it on a webshot.  
But I don't think I really have connection.  and why can't I enter all the info into the network manager?  



 [ATTACH]209496[/ATTACH]

---

### Post by gandaran on 2011-12-21
> It tries to connect but the enter passcode window keeps coming back, as if I am entering the wrong code. 
this is most helpful information you have given so far, look if if doesn't connect this way automatically then you wont get it connected by setting up the connection either, we know the driver is working so it must be some incompatibly between the driver and the router settings, try going to the router configurations and check the channel, if it is set to anything over 11 set to lower one, check hat DCHP server is enabled and last try WPA security mode instead WEP or no security at all just to check if it can work.

---

### Post by jpbjomar on 2011-12-21
well.  I am not sure I can do all that.  It is the building's wireless.  Their router - not mine.     It works on my windows XP boot and my laptop Windows 7.  i just can't get it to work on Ubuntu 11.10.
I am fairly sure they would give me a wired connection but i might need to pay.  Ubuntu is not that important to me.  but i was looking forward to learning.
Do you think because it is configured in the windows XP it is interfereing with the ubuntu setup?  I did try turning it off on windows once but perhaps there was also another problem at that time??

---

### Post by gandaran on 2011-12-21
> **jpbjomar said:**
> well.  I am not sure I can do all that.  It is the building's wireless.  Their router - not mine.     It works on my windows XP boot and my laptop Windows 7.  i just can't get it to work on Ubuntu 11.10.
I am fairly sure they would give me a wired connection but i might need to pay.  Ubuntu is not that important to me.  but i was looking forward to learning.
Do you think because it is configured in the windows XP it is interfereing with the ubuntu setup?  I did try turning it off on windows once but perhaps there was also another problem at that time??
okay then, one detail, if DCHP server is not enabled on the router you can still connect by manually setting the IP but you need to get that IP from the administrator only for your connection, Windows PC,s can connect to router without DCHP server but Linux cant.
another option you have is try installing the 3.1 kernel, maybe this kernel has better wireless drivers, try it but you will need a wired connection.
[http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html](http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html)

---

### Post by jpbjomar on 2011-12-21
Thank you.  I'll give it another try tomorrow.  it's getting late.

---

### Post by wildmanne39 on 2011-12-21
Hi, please try this before you change kernels it should make it where you can connect if there is not some strange setting in the router.
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```
enter your password then Add a single line:
```
options rt2800pci nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by jpbjomar on 2011-12-22
Wildmann, did what you said and got about 10 links that started with "blacklisted ..." ...  way over my head whatever it was.  

But take a look at these screenshots and see if you don't see something else???

forgive me but it is back to square 1

When I open "Network manager"  I get screen 1 notice the hardware addy and Wireless disconnected.  I cannot enter a name in the window but when I click the drop down box and click "other" I com to 
Screen 2: Note that it now say "hidden wireless network"  I don't know, just seems odd to me.  but I punch in the info and click security and we come to screen 4, punch in the info which I believe to be correct, click connect and wait about 30 seconds and i get screen 5.  so I start over.  
Now, if I open "create a Wireless network" buy clicking on the internet icon in the upper right corner I get screen 7.(there is an option for "hidden network" also)  Note it does not say "Hidden Wireless" like from the Net Manager route.
Punch in the same info, wait and I get screen 9 which is informing me that connection established.  
I then open firefox, punch in any address and nothing.  Says i am not connected.  
Please forgive me if this seems patronizing.  I'm just not the fastest ball down the alley.  I hope the screenshot come in the order intended.  [ATTACH][ATTACH][ATTACH][ATTACH][ATTACH]209547[/ATTACH][/ATTACH][/ATTACH][/ATTACH][/ATTACH]

---

### Post by jpbjomar on 2011-12-22
Shoot.   Click them in numerical order of their name.

---

### Post by jpbjomar on 2011-12-22
[attach]209548[/attach]

---

### Post by wildmanne39 on 2011-12-22
Hi, let's look at your blacklist file:
```
cat /etc/modprobe.d/blacklist.conf
```
also it is easier to connect to a network that is braodcasting not hidden if it is indeed hidden try to change it, I am not that familiar with wicd.
Thanks

---

### Post by gandaran on 2011-12-22
jpbjomar
> Now, if I open "create a Wireless network" buy clicking on the internet icon in the upper right corner I get screen 7.(there is an option for "hidden network" also) Note it does not say "Hidden Wireless" like from the Net Manager route.
hi again
so your network is hidden or you are not sure, your post is confusing and you should know from windows, if the network is hidden you don't see it on the panel network icon, if the **NH5960** network is visible you'll see it on the panel icon and you should be able to connect clicking the network,
if it's not visible and this is the network you want to connect then all you have to do is click on the panel icon » edit connections » wireless tab » add » just fill in the SSID NH5960 only, don't enter any other details including password, close the window then wait a few seconds till the network appears on the panel icon then click it.

edit:
I have just been playing around with my network hiding it so I could have a better understanding how it works, well I had to enter SSID and password too on the wireless tab setup then only with a PC reboot it showed up on the panel icon and connected automatically.
I'll be keeping my network hidden from now on!

---

### Post by jpbjomar on 2011-12-24
I haven't given up - just taking a break.
Thanks for your help and your patience.
Merry Christmas!

---

