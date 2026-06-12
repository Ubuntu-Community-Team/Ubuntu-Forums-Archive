---
title: "No Internet connection"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by Gilha on 2012-10-13
Hi,

I have an old Asus Eee pc which I now use only to write a few programms for college, since the computer is so old and I barely use Windows I decided to install Ubuntu 10.04 Lts and to erase the Windows partition (the Ubuntu installer gave me that option, which I selected). It all went great untill the time I wanted to connnect to the Internet. The pc recognizes the wireless connections in range and even asks me for the password, I type it in and wait but it just won't connect! After a few minutes it asks to input the password again and the same thing happens, and this over and over again.
Sorry for the bad English and I hope you guys can help me. Thank you.

Regards,

Gilha

---

### Post by wildmanne39 on 2012-10-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Gilha on 2012-10-13
I'm sorry but i cannot run that in the terminal of my Ubuntu pc because I've got no Internet connection on that computer. I've tried to run that in the Windows terminal, from where i'm working right now, but it doesn't work. what can I do for you to help me?
Thank you very much

---

### Post by NikTh on 2012-10-13
> **Gilha said:**
> I'm sorry but i cannot run that in the terminal of my Ubuntu pc because I've got no Internet connection on that computer. I've tried to run that in the Windows terminal, from where i'm working right now, but it doesn't work. what can I do for you to help me?

Then you must "play" with transfer files from one pc to other , through Usb-stick. 

Goto this page [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)

The script is above. Click in your browser **File** > **Save Page as** and save it inside to Usb-Stick.
Transfer the file to your /home folder inside Ubuntu and the open a terminal and do 
 
```
sudo chown **username:username** wireless_script
sudo chmod a+x wireless_script 
./wireless_script
```Where **username** , replace it with your actual username in Ubuntu.
Then transfer again the **netinfo.txt **file , that will be created, into working PC , and attach the file here. 

Thanks

---

### Post by kbrodenhau on 2012-10-13
I've noticed with the installations that wireless connectivity during  installation fails (*buntu and Debian)... So, just ignore and continue  the installation.

During installation, seems to only like WEP (and not WPA).

After install and reboot and login, easily  connect to the network from the network icon and perform any upgrades as  well as adding the language support...

I also suggest either Lubuntu (or maybe Xubuntu) if you have a really old machine... Ubuntu using Unity / Compiz might be too slugish.

---

### Post by Gilha on 2012-10-14
I tried to run the code on #4, but the terminal has the following output on the first command: "cannot access 'wireless_script': No such file or directory"

---

### Post by wildmanne39 on 2012-10-14
Hi, please run these commands then copy the results to a flash drive and use a computer with internet to post them.
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by Gilha on 2012-10-15
hi sry I took so long to reply, was away from home for a few days.

here are the results of the code u asked me to run on my terminal:
im sending the code in a txt file in an attachment.

thanks

---

### Post by NikTh on 2012-10-15
From the info you provided and after a search to Web, I found that this is a bug. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093?comments=all) 

The workaround is to install the wireless-backport-modules , although I guess that if you install a newer kernel , maybe this will solve your problem. 

If you have internet through Ethernet , try to full update your system 
```
sudo apt-get update 
sudo apt-get dist-upgrade
``` and if a newer kernel installed , boot from there and test again. 

If not, then try to install wireless - backport -modules . You can find them from synaptic package manager if you write to search box **wireless backport** . 

_**In any case wait for Wild Man's response..  **_before you proceed with any of my suggestions.

Thanks

---

### Post by Gilha on 2012-10-15
Thank you for your help NikTh!

---

### Post by pastapwr on 2012-10-15
Hello,
 
I too am a new user to Ubuntu.  I have an old Gateway M500B1 that I want to use for my 9 year old to surf the net and play some online games.  I decided that moving into the Linux world would be better than sticking with Windowz on this machine.
 
I installed Ubuntu 12.04 yesterday.  The install went fairly well until boot up.  I have two issues I am currently working on:
1. the display only fills about 2/3rds of the left side of the screen and appears to span from the top of the page up again from the bottom.  In other words I see the top screen bar/icons on the bottom of the screen and if I point the cursor at items along the top I see the cursor moving along the bottom.  Hope this is making sense.
2. the same wireless issue as the OP.
 
I tried what was described in this thread and here are my results after following the last post:
 
[EMAIL="dillon@dillon-M500B1:~$"]dillon@dillon-M500B1:~$[/EMAIL] ./wireless_script
bash: ./wireless_script: /bin/bash^M: bad interpreter: No such file or directory
[EMAIL="dillon@dillon-M500B1:~$"]dillon@dillon-M500B1:~$[/EMAIL] cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux dillon-M500B1 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux
[EMAIL="dillon@dillon-M500B1:~$"]dillon@dillon-M500B1:~$[/EMAIL] lpsci -nnk | grep -iA2 net
No command 'lpsci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lpsci: command not found
[EMAIL="dillon@dillon-M500B1:~$"]dillon@dillon-M500B1:~$[/EMAIL] lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05dc:0080 Lexar Media, Inc. Jumpdrive Secure 64MB
[EMAIL="dillon@dillon-M500B1:~$"]dillon@dillon-M500B1:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth1      IEEE 802.11b  ESSID:"mille2"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-74 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:4
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
eth0      no wireless extensions.
[EMAIL="dillon@dillon-M500B1:~$"]dillon@dillon-M500B1:~$[/EMAIL] rfkill list -all
Bogus list argument '-all'.
[EMAIL="dillon@dillon-M500B1:~$"]dillon@dillon-M500B1:~$[/EMAIL] rfkill list all
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
[EMAIL="dillon@dillon-M500B1:~$"]dillon@dillon-M500B1:~$[/EMAIL] lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
usb_storage            39646  1 
joydev                 17393  0 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                70112  1 orinoco_cs
cfg80211              178679  1 orinoco
snd_ali5451            23459  2 
snd_ac97_codec        106082  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_ali5451,snd_ac97_codec
i2c_ali15x3            12878  0 
nouveau               712356  2 
snd_seq_midi           13132  0 
pcmcia                 39791  1 orinoco_cs
snd_rawmidi            25424  1 snd_seq_midi
psmouse                72919  0 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197692  4 nouveau,ttm,drm_kms_helper
i2c_ali1535            12777  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
yenta_socket           27465  0 
rfcomm                 38139  0 
pcmcia_rsrc            18367  1 yenta_socket
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
pcmcia_core            21511  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
video                  19068  1 nouveau
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  0 
snd                    62064  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  1 snd_pcm
shpchp                 32325  0 
mac_hid                13077  0 
ali_agp                12957  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          40172  0 
8139too                23283  0 
pata_ali               13562  2 
8139cp                 26759  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

 
Your assistance is greatly appreciated.
 
Pastapwr

---

