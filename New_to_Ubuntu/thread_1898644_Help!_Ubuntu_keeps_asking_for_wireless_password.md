---
title: "Help! Ubuntu keeps asking for wireless password"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by swinston on 2011-12-21
I've just downloaded Wubi for the first time and I'm very new at all of this so bear with me. 

I've run through tons of threads, tried all the code, and still cannot seem to solve this problem. I've found my wireless network and added the password when authentication was required. I also edited the wireless connection and put the password in the wireless security tab. It seems to accept the password, but then it continually tries to connect until it asks me for the password again. This situation has happened over and over again. Help please!!

---

### Post by wildmanne39 on 2011-12-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by anewguy on 2011-12-21
Also, there have been many instances (I have had them myself) where if you initially enter the password incorrectly network manager seems to remember only the initial password - the bad one - not the latest you have entered.  This results in the loop like you are having.

I can't say it's your problem, so please do as wildmanne39 has requested, but also try the following:

- click on network manager, then on edit connections.  Click the wireless tab and DELETE any connections that show there, then close the edit connections box.

- in network manager, click on your network again - you will be prompted for the password again.   Before entering your password, double-check to be sure it is the correct password.  Then click the "show password" box so you can see what gets typed in to be sure it is correct.

If you still get stuck in the loop after that, there are a couple of other things to consider:

- did you match the encryption type as set on the router?  Some times the computer's adapter and/or driver can't support the same encryption as might be on the router, or you have selected WEP when it's really WPA, etc..

- did you match the password/password "strength" (how many bits)?

- I assume it is, but is the router broadcasting the SSID?  If your router is "hiding" the network, you MUST manually create the connection.

I'll leave you back in wildmanne39's extremely capable hands - he's very good at resolving these things!

Dave ;)

---

### Post by thenudehamster on 2011-12-22
I have similar troubles on one of my machines. It seems (I haven't yet done a detailed check) for the most part to occur after the machine has reawakened the monitor from standby. The computer itself is on 24/7 running BOINC, (along with four others that don't suffer with it,) and I have also noticed a few BOINC errors in that it is unable to contact the servers. On manually awakening it, I get the same password loop - and this IS the correct password, because it's saved, and works on a restart. The only way I've been able to resolve this is by rebooting, but it's annoying because the BOINC project is losing a lot of work.
All are running 11.04, oneiric, fully updated, as is BOINC.

---

### Post by swinston on 2011-12-22
```
sdavis@ubuntu:~$ cat/etch/lsb-release; uname -a 
bash: cat/etch/lsb-release: No such file or directory 
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 
sdavis@ubuntu:~$ lspci -nnk | grep -iA2 net 
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14) 
	Subsystem: Hewlett-Packard Company Device [103c:30cd] 
	Kernel driver in use: sky2 
-- 
07:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61) 
	Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100] 
	Kernel driver in use: iwl4965 
sdavis@ubuntu:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11abgn  ESSID:"TheHive"   
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:82:F5:AD:78    
          Bit Rate=1 Mb/s   Tx-Power=14 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=46/70  Signal level=-64 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
sdavis@ubuntu:~$ rekill list all 
No command 'rekill' found, did you mean: 
 Command 'rfkill' from package 'rfkill' (main) 
 Command 'rkill' from package 'pslist' (universe) 
rekill: command not found 
sdavis@ubuntu:~$ lsmod 
Module                  Size  Used by 
bnep                   18436  2  
rfcomm                 47946  0  
parport_pc             36962  0  
ppdev                  17113  0  
lp                     17799  0  
parport                46562  3 parport_pc,ppdev,lp 
snd_hda_codec_conexant    62197  1  
binfmt_misc            17540  1  
joydev                 17693  0  
uvcvideo               72711  0  
videodev               93004  1 uvcvideo 
v4l2_compat_ioctl32    17083  1 videodev 
arc4                   12529  2  
snd_hda_intel          33390  2  
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel 
snd_hwdep              13668  1 snd_hda_codec 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0  
hp_wmi                 18092  0  
sparse_keymap          13890  1 hp_wmi 
snd_rawmidi            30547  1 snd_seq_midi 
btusb                  18600  1  
snd_seq_midi_event     14899  1 snd_seq_midi 
bluetooth             166112  13 bnep,rfcomm,btusb 
iwl4965               132375  0  
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event 
i915                  566711  3  
iwl_legacy             83487  1 iwl4965 
r852                   18277  0  
psmouse                73882  0  
sm_common              16865  1 r852 
nand                   54966  2 r852,sm_common 
nand_ids               12723  1 nand 
nand_bch               13147  1 nand 
mac80211              310872  2 iwl4965,iwl_legacy 
bch                    22061  1 nand_bch 
nand_ecc               13230  1 nand 
snd_timer              29991  2 snd_pcm,snd_seq 
drm_kms_helper         42558  1 i915 
serio_raw              13166  0  
mtd                    33181  2 sm_common,nand 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
drm                   236330  4 i915,drm_kms_helper 
i2c_algo_bit           13423  1 i915 
cfg80211              199587  3 iwl4965,iwl_legacy,mac80211 
wmi                    19256  1 hp_wmi 
snd                    68266  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              12680  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
video                  19412  1 i915 
firewire_ohci          40722  0  
firewire_core          63626  1 firewire_ohci 
crc_itu_t              12707  1 firewire_core 
sdhci_pci              14032  0  
sdhci                  32166  1 sdhci_pci 
sky2                   58674  0  
ahci                   26002  1  
libahci                26861  1 ahci 
sdavis@ubuntu:~$ 

```

It's strange. Yesterday I disconnect wireless on ubuntu and then I was unable to connect to wireless on windows (running on the same laptop). When I connected to wireless again in ubuntu, and got the same continuous request for me to re-enter the wireless password, but the windows wireless started working again.

---

### Post by swinston on 2011-12-22
I have rebooted multiple times throughout the process and I am still in the loop. Since installing ubuntu yesterday, the wireless and my wireless network has never worked.

---

### Post by swinston on 2011-12-22
> **anewguy said:**
> Also, there have been many instances (I have had them myself) where if you initially enter the password incorrectly network manager seems to remember only the initial password - the bad one - not the latest you have entered.  This results in the loop like you are having.

I can't say it's your problem, so please do as wildmanne39 has requested, but also try the following:

- click on network manager, then on edit connections.  Click the wireless tab and DELETE any connections that show there, then close the edit connections box.

- in network manager, click on your network again - you will be prompted for the password again.   Before entering your password, double-check to be sure it is the correct password.  Then click the "show password" box so you can see what gets typed in to be sure it is correct.



I did that and yup I'm still in the loop. I'll check the other wireless settings now.

---

### Post by wildmanne39 on 2011-12-22
Hi, let's try this please and please **copy and paste** all commands one line at a time:
```
gksu gedit /etc/modprobe.d/options.conf
```
And add the following to it:
```
options iwl4965 11n_disable=1
```
proof read then save,exit and reboot.
Thanks

---

### Post by swinston on 2011-12-22
```
sdavis@ubuntu:~$ gksu gedit /etc/modprobe.d/options.conf

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
  

options iwl4965 11n disable=1

sdavis@ubuntu:~$ options iwl4965 11n disable=1
options: command not found


```

I hope I did this right. I added the code to the terminal one line at a time and then I copied what came up and I saved it all in gedit as a config file. 

When I rebooted I still did not have internet and I also lost the ability to see all wireless networks. It now says I have a wired connection (used two minutes ago), which is impossible since I did not connect any ethernet cables to the laptop.

---

### Post by Bluenoser81 on 2011-12-22
You mistyped two of the commands -- cat & rfkill, (added 'h' to /etc, and typed 'rekill' instead of 'rfkill') from the initial list, according to your pasted code. Don't know the answer here, just following along :)

---

### Post by swinston on 2011-12-22
Thanks for letting me know. I'll re-run the code. Yeah...I still have no idea how to get wireless up and running and after running this code my wireless options seem to have disappeared too. :(

---

### Post by wildmanne39 on 2011-12-22
> **swinston said:**
> ```
sdavis@ubuntu:~$ gksu gedit /etc/modprobe.d/options.conf

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
  

options iwl4965 11n disable=1

sdavis@ubuntu:~$ options iwl4965 11n disable=1
options: command not found


```

I hope I did this right. I added the code to the terminal one line at a time and then I copied what came up and I saved it all in gedit as a config file. 

When I rebooted I still did not have internet and I also lost the ability to see all wireless networks. It now says I have a wired connection (used two minutes ago), which is impossible since I did not connect any ethernet cables to the laptop.
Hi, to fix this error try this:
```
sudo apt-get install gtk2-engines-pixbuf
```
Run this command again:
```
gksu gedit /etc/modprobe.d/options.conf
```
and post the contents of the file here.

Please copy and paste all commands into the terminal for accuracy.
Thanks

---

### Post by swinston on 2011-12-22
This is what came up after first set of code: ```
sdavis@ubuntu:~$ sudo apt-get install gtk2-engines-pixbuf
[sudo] password for sdavis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gtk2-engines-pixbuf
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 127 kB of archives.
After this operation, 1,073 kB of additional disk space will be used.
Err http://archive.ubuntu.com/ubuntu/ oneiric/universe gtk2-engines-pixbuf amd64 2.24.6-0ubuntu5
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/g/gtk+2.0/gtk2-engines-pixbuf_2.24.6-0ubuntu5_amd64.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
sdavis@ubuntu:~$ gksu gedit /etc/modprobe.d/options.conf

(gksu:1823): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:1823): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:1823): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:1823): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 
```

This is what came up in the options.conf window after inserting second line of code:

```
sdavis@ubuntu:~$ gksu gedit /etc/modprobe.d/options.conf

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
  

options iwl4965 11n disable=1

sdavis@ubuntu:~$ options iwl4965 11n disable=1
options: command not found
```

I tried restarting to see if that would matter, but it did not. Nothing's changed.

---

### Post by wildmanne39 on 2011-12-22
Hi, that does not stop you from adding the line you need to add to that file or posting the contents here so please post the contents of the file.
Thanks

---

### Post by swinston on 2011-12-23
I'm sorry but I thought that's what I just gave you. What do you want me to do exactly?

---

### Post by swinston on 2011-12-23
After talking to an IT guys at work, it turns out that I probably need to install wireless drivers . I have no idea how to do that and the IT people do not know how to do it in ubuntu either. Could anyone help?

My wireless card is: wifi link 4965agn

---

### Post by wildmanne39 on 2011-12-23
Hi, the driver is already installed and IT guys will do you no good in ubuntu. It needs a little help to work that **iwl4965 11n disable=1** usually gets it working.

Please post the output of:
```
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by swinston on 2011-12-23
```
sdavis@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1D:72:60:51:A8

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


sdavis@ubuntu:~$ 
sdavis@ubuntu:~$ sudo iwlist scan
[sudo] password for sdavis: 
Sorry, try again.
[sudo] password for sdavis: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sdavis@ubuntu:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55
Dec 22 13:02:05 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Dec 22 13:02:12 ubuntu kernel: [ 5339.211402] wlan0: deauthenticated from 00:26:82:f5:ad:78 (Reason: 15)
Dec 22 13:02:12 ubuntu wpa_supplicant[890]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Dec 22 13:02:12 ubuntu wpa_supplicant[890]: CTRL-EVENT-DISCONNECTED bssid=00:26:82:f5:ad:78 reason=15
Dec 22 13:02:12 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Dec 22 13:02:12 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 22 13:02:14 ubuntu wpa_supplicant[890]: Trying to authenticate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz)
Dec 22 13:02:14 ubuntu wpa_supplicant[890]: Trying to associate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz)
Dec 22 13:02:14 ubuntu kernel: [ 5341.142928] wlan0: authenticate with 00:26:82:f5:ad:78 (try 1)
Dec 22 13:02:14 ubuntu kernel: [ 5341.144744] wlan0: authenticated
Dec 22 13:02:14 ubuntu kernel: [ 5341.146088] wlan0: associate with 00:26:82:f5:ad:78 (try 1)
Dec 22 13:02:14 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: scanning -> associating
Dec 22 13:02:14 ubuntu kernel: [ 5341.151182] wlan0: RX ReassocResp from 00:26:82:f5:ad:78 (capab=0x411 status=0 aid=1)
Dec 22 13:02:14 ubuntu kernel: [ 5341.151186] wlan0: associated
Dec 22 13:02:14 ubuntu wpa_supplicant[890]: Associated with 00:26:82:f5:ad:78
Dec 22 13:02:14 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: associating -> associated
Dec 22 13:02:15 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Dec 22 13:02:21 ubuntu kernel: [ 5348.311478] wlan0: deauthenticated from 00:26:82:f5:ad:78 (Reason: 15)
Dec 22 13:02:21 ubuntu wpa_supplicant[890]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Dec 22 13:02:21 ubuntu wpa_supplicant[890]: CTRL-EVENT-DISCONNECTED bssid=00:26:82:f5:ad:78 reason=15
Dec 22 13:02:21 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Dec 22 13:02:21 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 22 13:02:23 ubuntu wpa_supplicant[890]: Trying to authenticate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz)
Dec 22 13:02:23 ubuntu kernel: [ 5350.130983] wlan0: authenticate with 00:26:82:f5:ad:78 (try 1)
Dec 22 13:02:23 ubuntu wpa_supplicant[890]: Trying to associate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz)
Dec 22 13:02:23 ubuntu kernel: [ 5350.132809] wlan0: authenticated
Dec 22 13:02:23 ubuntu kernel: [ 5350.133112] wlan0: associate with 00:26:82:f5:ad:78 (try 1)
Dec 22 13:02:23 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: scanning -> associating
Dec 22 13:02:23 ubuntu kernel: [ 5350.136496] wlan0: RX ReassocResp from 00:26:82:f5:ad:78 (capab=0x411 status=0 aid=1)
Dec 22 13:02:23 ubuntu kernel: [ 5350.136504] wlan0: associated
Dec 22 13:02:23 ubuntu wpa_supplicant[890]: Associated with 00:26:82:f5:ad:78
Dec 22 13:02:23 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: associating -> associated
Dec 22 13:02:24 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Dec 22 13:02:25 ubuntu NetworkManager[836]: <warn> Activation (wlan0/wireless): association took too long.
Dec 22 13:02:25 ubuntu NetworkManager[836]: <info> (wlan0): device state change: config -> failed (reason 'no-secrets') [50 120 7]
Dec 22 13:02:25 ubuntu NetworkManager[836]: <warn> Activation (wlan0) failed for access point (TheHive)
Dec 22 13:02:25 ubuntu NetworkManager[836]: <warn> Activation (wlan0) failed.
Dec 22 13:02:25 ubuntu NetworkManager[836]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 22 13:02:25 ubuntu NetworkManager[836]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 22 13:02:25 ubuntu kernel: [ 5352.019183] wlan0: deauthenticating from 00:26:82:f5:ad:78 by local choice (reason=3)
Dec 22 13:02:25 ubuntu wpa_supplicant[890]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Dec 22 13:02:25 ubuntu NetworkManager[836]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Dec 22 13:09:50 ubuntu kernel: [   33.551972] iwl4965: Unknown parameter `11n'
Dec 22 13:09:51 ubuntu NetworkManager[803]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 22 19:37:42 ubuntu NetworkManager[2047]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 22 22:08:10 ubuntu kernel: [   33.297098] iwl4965: Unknown parameter `11n'
Dec 22 22:08:11 ubuntu NetworkManager[791]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 22 22:20:06 ubuntu kernel: [   33.477101] iwl4965: Unknown parameter `11n'
Dec 22 22:20:06 ubuntu NetworkManager[777]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 23 09:41:32 ubuntu kernel: [   33.397662] iwl4965: Unknown parameter `11n'
Dec 23 09:41:32 ubuntu NetworkManager[788]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 23 10:09:08 ubuntu kernel: [   33.587963] iwl4965: Unknown parameter `11n'
Dec 23 10:09:08 ubuntu NetworkManager[789]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 23 16:26:32 ubuntu kernel: [   33.598937] iwl4965: Unknown parameter `11n'
Dec 23 16:26:33 ubuntu NetworkManager[831]: <info> monitoring kernel firmware directory '/lib/firmware'.
sdavis@ubuntu:~$ 


```

---

### Post by wildmanne39 on 2011-12-23
Hi, ok I see the problem with the option you added to that file, you have a typo in it.

Please go back to post 8 and follow the directions after the file is open remove the option you put in then copy and paste the one I have in post 8 please do not type it, then save, exit the file and reboot.
Thanks

---

### Post by swinston on 2011-12-23
I tried to follow all of your instructions. 

This is from the terminal:

```
sdavis@ubuntu:~$ gksu gedit /etc/modprobe.d/options.conf 
 
(gksu:1924): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:1924): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:1924): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:1924): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
options iwl4965 11n_disable=1  
^C   
sdavis@ubuntu:~$ options iwl4965 11n_disable=1 
options: command not found 
sdavis@ubuntu:~$  
```

This is what I came out of the options.conf file:

```
sdavis@ubuntu:~$ gksu gedit /etc/modprobe.d/options.conf 
 
(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:2418): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
   
 
options iwl4965 11n disable=1 
 
sdavis@ubuntu:~$ options iwl4965 11n disable=1 
options: command not found 

```

---

### Post by arvevans on 2011-12-23
Maybe, and maybe not...
If you initially used a user ID login and password to get into your computer, then changed the operating mode to "auto login" Keyring will ask you to enter your network password every time you reboot.

Changing back to using a login ID and password will sometimes fix this problem, and sometimes it will not.

_._

---

### Post by wildmanne39 on 2011-12-23
Hi, you are making it confusing please do not show the errors all I need to see is what is in the file and it looks like a typo as I said you need to change this ```
options iwl4965 11n disable=1 
```
To this:
```
iwl4965 11n_disable=1
```
in the file and remember to save the file and reboot, this might not fix the problem but it usually does and we need to fix this before going any further.
Thanks

---

### Post by swinston on 2011-12-23
Okay the wireless is back. I found my network and typed in the correct password. It is the way it was before: the wireless asks me for my password again and again.

---

### Post by anewguy on 2011-12-23
Does it say it's asking for the keyring password, or does it show a connection box with the network name saying it requires a key or passphrase and has an area to enter that into?

Also, you've never posted back what wildmanne39 is asking you to do:

First, when you type in the gksudo gedit xxxxxxxxx, that opens a GUI'd editor that should show the file in it.  He wants you to stay in that editor window, scroll to the bottom and make the changes in the file showing in the editor, then use the save option in the editor, then exit the editor.  You *DO NOT* type the "options" line in the command line.  If you are not getting an editor window please post back saying so.  This is very important so I'll repeat - it SHOULD open the file in an EDITOR window, and the changes he is asking you to make are to the file in the EDITOR WINDOW.  Then SAVE the file via the SAVE OPTION in the editor.

And.....did you follow my first post about opening network manager and DELETING the connection definition?

---

### Post by swinston on 2011-12-23
It shows a connection box with the network name and is asking for a key/passphrase with an area to enter it in. I always check the box that shows the password and type the password in.

---

### Post by swinston on 2011-12-23
Yup I did both those things. I made the changes in the editor from options iwl4965 11n disable=1 to iwl4965 11n_disable=1, saved the file and rebooted, and that's what brought the wireless options back. I also already deleted the connections in the connection manager previously and when wireless came on this time I made the wireless connection with my network all over again.

---

### Post by wildmanne39 on 2011-12-23
Hi, run the commands in post 17 again and post here now that you have the file correct.
Thanks

---

### Post by swinston on 2011-12-23
```
sdavis@ubuntu:~$ nm-tool 
 
NetworkManager Tool 
 
State: connecting 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            sky2 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1D:72:60:51:A8 
 
  Capabilities: 
    Carrier Detect:  yes 
 
  Wired Properties 
    Carrier:         off 
 
 
- Device: wlan0  [TheHive] ----------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            iwl4965 
  State:             connecting (configuring) 
  Default:           no 
  HW Address:        00:1F:3B:B9:CD:0D 
 
  Capabilities: 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points  
    TheHive:         Infra, 00:26:82:F5:AD:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2 
    EYKING:          Infra, 00:26:82:D5:5C:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA2 
    another:         Infra, 00:22:6B:7D:80:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2 
    KELLANDSUNDAHL_Network: Infra, 5C:D9:98:5B:0D:F6, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2 
    jsnow:           Infra, 30:46:9A:4D:CC:76, Freq 2437 MHz, Rate 54 Mb/s, Strength 7 WPA2 
    Genja:           Infra, E8:BE:81:FC:0A:30, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WEP 
    mutundwe:        Infra, 00:1C:F0:53:C6:99, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WEP 
    johnson:         Infra, 00:17:3F:BE:6D:EA, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA 
    lk13sj11:        Infra, 68:7F:74:30:DA:1B, Freq 2452 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2 
    james01:         Infra, C8:CD:72:E6:33:82, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2 
    ALIANT985:       Infra, 00:25:3C:CE:57:19, Freq 2427 MHz, Rate 54 Mb/s, Strength 22 WPA 
    kate:            Infra, 00:1C:10:25:B6:AE, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA 
    MOTOROLA-F2108:  Infra, AC:81:12:01:75:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP 
    ALIANT746:       Infra, B0:E7:54:D7:75:81, Freq 2447 MHz, Rate 54 Mb/s, Strength 17 WPA 
    Touque:          Infra, 00:1B:11:69:EC:77, Freq 2452 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2 
    Siksika:         Infra, 30:46:9A:1E:4A:04, Freq 2427 MHz, Rate 54 Mb/s, Strength 44 WPA2 
    dlinkafbe:       Infra, 00:18:E7:CE:AF:BE, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2 
    Adams:           Infra, C0:3F:0E:DD:19:70, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 
    kate:            Infra, 00:13:46:F9:7E:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2 
    Gingerbread House: Infra, 00:1C:F0:67:15:FC, Freq 2417 MHz, Rate 54 Mb/s, Strength 87 WPA 
 
 
sdavis@ubuntu:~$ sudo iwlist scan 
[sudo] password for sdavis:  
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Interface doesn't support scanning : Device or resource busy 
 
sdavis@ubuntu:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55 
Dec 23 20:43:34 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: authenticating -> associating 
Dec 23 20:43:35 ubuntu wpa_supplicant[922]: Associated with 00:26:82:f5:ad:78 
Dec 23 20:43:35 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: associating -> associated 
Dec 23 20:43:35 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake 
Dec 23 20:43:42 ubuntu kernel: [ 1101.038245] wlan0: deauthenticated from 00:26:82:f5:ad:78 (Reason: 15) 
Dec 23 20:43:42 ubuntu wpa_supplicant[922]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect 
Dec 23 20:43:42 ubuntu wpa_supplicant[922]: CTRL-EVENT-DISCONNECTED bssid=00:26:82:f5:ad:78 reason=15 
Dec 23 20:43:42 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected 
Dec 23 20:43:42 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: disconnected -> scanning 
Dec 23 20:43:44 ubuntu wpa_supplicant[922]: Trying to authenticate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz) 
Dec 23 20:43:44 ubuntu kernel: [ 1102.927589] wlan0: authenticate with 00:26:82:f5:ad:78 (try 1) 
Dec 23 20:43:44 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: scanning -> authenticating 
Dec 23 20:43:44 ubuntu wpa_supplicant[922]: Trying to associate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz) 
Dec 23 20:43:44 ubuntu kernel: [ 1102.930098] wlan0: authenticated 
Dec 23 20:43:44 ubuntu kernel: [ 1102.930359] wlan0: associate with 00:26:82:f5:ad:78 (try 1) 
Dec 23 20:43:44 ubuntu kernel: [ 1102.932981] wlan0: RX ReassocResp from 00:26:82:f5:ad:78 (capab=0x411 status=0 aid=2) 
Dec 23 20:43:44 ubuntu kernel: [ 1102.932985] wlan0: associated 
Dec 23 20:43:44 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: authenticating -> associating 
Dec 23 20:43:44 ubuntu wpa_supplicant[922]: Associated with 00:26:82:f5:ad:78 
Dec 23 20:43:44 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: associating -> associated 
Dec 23 20:43:44 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake 
Dec 23 20:43:51 ubuntu kernel: [ 1110.038350] wlan0: deauthenticated from 00:26:82:f5:ad:78 (Reason: 15) 
Dec 23 20:43:51 ubuntu wpa_supplicant[922]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect 
Dec 23 20:43:51 ubuntu wpa_supplicant[922]: CTRL-EVENT-DISCONNECTED bssid=00:26:82:f5:ad:78 reason=15 
Dec 23 20:43:51 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected 
Dec 23 20:43:51 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: disconnected -> scanning 
Dec 23 20:43:53 ubuntu wpa_supplicant[922]: Trying to authenticate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz) 
Dec 23 20:43:53 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: scanning -> authenticating 
Dec 23 20:43:53 ubuntu wpa_supplicant[922]: Trying to associate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz) 
Dec 23 20:43:53 ubuntu kernel: [ 1111.977132] wlan0: authenticate with 00:26:82:f5:ad:78 (try 1) 
Dec 23 20:43:53 ubuntu kernel: [ 1111.978955] wlan0: authenticated 
Dec 23 20:43:53 ubuntu kernel: [ 1111.979699] wlan0: associate with 00:26:82:f5:ad:78 (try 1) 
Dec 23 20:43:53 ubuntu kernel: [ 1111.982335] wlan0: RX ReassocResp from 00:26:82:f5:ad:78 (capab=0x411 status=0 aid=2) 
Dec 23 20:43:53 ubuntu kernel: [ 1111.982342] wlan0: associated 
Dec 23 20:43:53 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: authenticating -> associating 
Dec 23 20:43:53 ubuntu wpa_supplicant[922]: Associated with 00:26:82:f5:ad:78 
Dec 23 20:43:53 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: associating -> associated 
Dec 23 20:43:53 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake 
Dec 23 20:44:00 ubuntu kernel: [ 1119.138537] wlan0: deauthenticated from 00:26:82:f5:ad:78 (Reason: 15) 
Dec 23 20:44:00 ubuntu wpa_supplicant[922]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect 
Dec 23 20:44:00 ubuntu wpa_supplicant[922]: CTRL-EVENT-DISCONNECTED bssid=00:26:82:f5:ad:78 reason=15 
Dec 23 20:44:00 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected 
Dec 23 20:44:00 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: disconnected -> scanning 
Dec 23 20:44:02 ubuntu wpa_supplicant[922]: Trying to authenticate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz) 
Dec 23 20:44:02 ubuntu kernel: [ 1120.991232] wlan0: authenticate with 00:26:82:f5:ad:78 (try 1) 
Dec 23 20:44:02 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: scanning -> authenticating 
Dec 23 20:44:02 ubuntu wpa_supplicant[922]: Trying to associate with 00:26:82:f5:ad:78 (SSID='TheHive' freq=2462 MHz) 
Dec 23 20:44:02 ubuntu kernel: [ 1120.994414] wlan0: authenticated 
Dec 23 20:44:02 ubuntu kernel: [ 1120.994744] wlan0: associate with 00:26:82:f5:ad:78 (try 1) 
Dec 23 20:44:02 ubuntu kernel: [ 1120.997362] wlan0: RX ReassocResp from 00:26:82:f5:ad:78 (capab=0x411 status=0 aid=2) 
Dec 23 20:44:02 ubuntu kernel: [ 1120.997370] wlan0: associated 
Dec 23 20:44:02 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: authenticating -> associating 
Dec 23 20:44:02 ubuntu wpa_supplicant[922]: Associated with 00:26:82:f5:ad:78 
Dec 23 20:44:02 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: associating -> associated 
Dec 23 20:44:02 ubuntu NetworkManager[788]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake 
sdavis@ubuntu:~$  
sdavis@ubuntu:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55 

```

---

### Post by wildmanne39 on 2011-12-23
Hi, you need to change your encryption in your router to just wpa2 if you can and not wpa/wpa2 it will work better and your signal strength is weak can you get a little closer to your router?

You can usually change the encryption setting by typing 198.162.0.1 into your web broswer with a wired connection to your router then click on wireless security in your router settings and change it to wpa2 if possible also if this does not work we can try another solution but this works a lot of the times and is less trouble for you.

My family is in from out of town so I am not going to be on much until Monday.
Thanks

---

### Post by pelee98 on 2011-12-26
hello all.

I seem to be having a similar problem.

I have an Acer netbook with a dual boot ubuntu 11.10 and windows 
7, in ubuntu the wireless keeps dropping out. Ran great for months - no problems. Then,for a couple of weeks, it would drop the connection and then reconnect on its own in a few seconds - annoying, but at least it reconnected. Now i need to tell it to reconnect, and to make matters worse, it will not save the access code to the wireless. So I have to keep the network password with me and type it in every time I reconnect (which is a lot).

And none of this happens when I've booted in to windows 7 - so I don't believe it's a hardware issue.  Thoughts?

I'm not sure of the proper etiquette here.  Should I be starting a new post?

---

### Post by anewguy on 2011-12-26
> **pelee98 said:**
> hello all.
I'm not sure of the proper etiquette here.  Should I be starting a new post?

Yes, please do.  We want to keep each thread on the problem the original poster had.  Any other problems should be opened in a new thread.  It not only keeps things clearer in each thread, it helps anyone who may be looking for threads about a certain topic.

Thanks for being polite enough to ask!  There are a lot of people out there who refuse to understand and end up sidetracking or completely hijacking a thread, making everything pretty much useless.

I don't know the answer to your problem, but again thanks for asking and indeed please create a separate thread.

Best of luck!

Dave ;)

---

### Post by swinston on 2012-01-04
Hi wildmanne39, 

I apologize for the delay in responding, but I was away for winter break. 

Unfortunately, I cannot change the encryption on my router because there are other computers using wireless that would lose connection if I changed to wpa2. 

Do you have any other suggestions? Do you think re-installing ubuntu might somehow get rid of the wireles problem at all?

Thank you for all your help thus far!

---

### Post by wildmanne39 on 2012-01-04
Hi, let's try this please:
```
gksu nautilus
```
click on file system>etc>modprobe.d>and delete options.conf
Then close nautilus and run the the previous command this way to see if it helps.
```
gksudo gedit /etc/modprobe.d/iwl4965.conf
``` 
And add the following to it:
```
options iwl4965 11n_disable=1
```
proof read then save,exit and reboot.
Thanks

---

