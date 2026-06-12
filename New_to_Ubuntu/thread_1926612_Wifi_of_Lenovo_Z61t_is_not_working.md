---
title: "Wifi of Lenovo Z61t is not working"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by hammadsiddiqui on 2012-02-16
Hello i am new to Ubuntu, and recently installed Ubuntu 11.10. Having Lenovo Z61t laptop with Atheros Wifi Card, but unfortunately my wifi is not working. The light indicator on my machine is off.

Kindly help me to solve this issue.

Thanks
HammadSiddiqui

---

### Post by TeoBigusGeekus on 2012-02-16
Have you tried looking in the "Additional Drivers" to see if there's a driver for your card?

---

### Post by Scott Baker on 2012-02-16
If you have access to it, plug into a wired connection, and run your updates. Make sure they're ALL current. Check after updating and see if this has corrected your issues. I've seen some people install Ubuntu fresh, or they do an upgrade, and they don't have wireless capability right after the install, but once the updates are done, WHAM!! problem goes away, Try it and see if that corrects the problem.  [-o<

---

### Post by Bucky Ball on 2012-02-16
> **Scott Baker said:**
> I've seen some people install Ubuntu fresh, or they do an upgrade, and they don't have wireless capability right after the install, but once the updates are done, WHAM!! problem goes away, Try it and see if that corrects the problem.  [-o<

+1. You need to get online with a cable and get updates, then check 'Additional Drivers'. Also, Madwifi is specifically designed for Atheros cards. You could try that  rather than Network Manager (the default). 

[http://madwifi-project.org/wiki/About/MadWifi](http://madwifi-project.org/wiki/About/MadWifi)

... and:

[http://madwifi-project.org/wiki](http://madwifi-project.org/wiki)

---

### Post by wildmanne39 on 2012-02-17
Hi, if you still can not connect after you update and check in additional drivers please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by hammadsiddiqui on 2012-02-17
> **wildmanne39 said:**
> Hi, if you still can not connect after you update and check in additional drivers please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod 
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you
ibm@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

==================================================================


ibm@ubuntu:~$ lspci -nnk l grep -iA2 net
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of A2
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file

ibm@ubuntu:~$


==================================================================

ibm@ubuntu:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
irda0     no wireless extensions.
wlan0     IEEE 802.11abg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:E5:6B:AB:18   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:53   Missed beacon:0
ibm@ubuntu:~$

==================================================================


ibm@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ibm@ubuntu:~$ 

==================================================================

ibm@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_analog    75090  1 
binfmt_misc            17292  1 
joydev                 17393  0 
pcmcia                 39822  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
i915                  505108  3 
snd_seq_midi_event     14475  1 snd_seq_midi
tifm_7xx1              12937  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
thinkpad_acpi          73942  0 
ath5k                 145100  0 
ath                    19387  1 ath5k
tifm_core              15040  1 tifm_7xx1
nsc_ircc               23240  0 
irda                  185428  1 nsc_ircc
snd_timer              28932  2 snd_pcm,snd_seq
drm_kms_helper         32889  1 i915
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
mac80211              272785  1 ath5k
nvram                  14029  1 thinkpad_acpi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
drm                   192226  4 i915,drm_kms_helper
tpm_tis                14002  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
crc_ccitt              12595  1 irda
i2c_algo_bit           13199  1 i915
cfg80211              172392  3 ath5k,ath,mac80211
snd                    55902  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
tg3                   132972  0 
ibm@ubuntu:~$


This is your required result plz do the needful.

---

### Post by hammadsiddiqui on 2012-02-17
Yes i tried but it does nothing only loading appears for a long time.

---

### Post by hammadsiddiqui on 2012-02-17
> **Bucky Ball said:**
> +1. You need to get online with a cable and get updates, then check 'Additional Drivers'. Also, Madwifi is specifically designed for Atheros cards. You could try that  rather than Network Manager (the default). 

[http://madwifi-project.org/wiki/About/MadWifi](http://madwifi-project.org/wiki/About/MadWifi)

... and:

[http://madwifi-project.org/wiki](http://madwifi-project.org/wiki)
Yes i tried to connect by wired connection but still unable to connect it, i think i am missing something in configuration connection.

---

### Post by Scott Baker on 2012-02-17
I have a couple of questions for you, if you don't mind. First, how did you install this O/S? Is it a fresh install (only O/S on the hard disk), is it "dual-booting" (sharing the hard drive with another O/S like Windows),  or was it installed through Windows using WUBI (similar to installing any other piece of software through Windows). Next, what type of media were you using to install Ubuntu? (factory disk, downloaded ISO on CD/DVD or flash/thumb drive, etc). Finally, when you installed Ubuntu, you were prompted for an internet connection in the set up phase. Did you have internet access then, and if so, was it a wired connection, were you trying to do this wirelessly, or did you opt out of being online during the install and set-up. Any additional info that you can provide would help greatly. Thanks much.  :-k

---

### Post by josephmills on 2012-02-17
> 


"Ubuntu 11.10"
 3.0.0-12-generic 






ibm@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


ibm@ubuntu:~$ lsmod
Module                  Size  Used by
                38408  0 

ath5k                 145100  0 
ath                    19387  1 ath5k
                
mac80211              272785  1 ath5k
cfg80211              172392  3 ath5k,ath,mac80211
                  132972  0 
ibm@ubuntu:~$


This is your required result plz do the needful.

could we see a ```
lspci -nn | grep Ath
```
thanks

---

### Post by wildmanne39 on 2012-02-18
Hi , please copy and paste all commands into the terminal for accuracy, this one is wrong, please paste the results again.
```
lspci -nnk l grep -iA2 net
```
Also you can try this it may get your wireless working.
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Add a single line:
```
options ath5k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by Bucky Ball on 2012-02-18
> **wildmanne39 said:**
> Proofread carefully, save and close gedit. Reboot.
Thanks

Copy and paste best. ;)

---

### Post by hammadsiddiqui on 2012-02-18
> **Scott Baker said:**
> I have a couple of questions for you, if you don't mind. First, how did you install this O/S? Is it a fresh install (only O/S on the hard disk), is it "dual-booting" (sharing the hard drive with another O/S like Windows),  or was it installed through Windows using WUBI (similar to installing any other piece of software through Windows). Next, what type of media were you using to install Ubuntu? (factory disk, downloaded ISO on CD/DVD or flash/thumb drive, etc). Finally, when you installed Ubuntu, you were prompted for an internet connection in the set up phase. Did you have internet access then, and if so, was it a wired connection, were you trying to do this wirelessly, or did you opt out of being online during the install and set-up. Any additional info that you can provide would help greatly. Thanks much.  :-k
I install it by going to option which says install ubuntu inside windows, so i am using ubuntu with windows xp now. I have installed ubuntu by a CD which is a copy of original Ubuntu 11.10 CD. And at the time of installation i didn't think so that i have get an option to connect to internet, there was no option like that :(

---

### Post by Bucky Ball on 2012-02-18
Wubi install is not recommended for long term. Basically to try Ubuntu and see if you like. Not a permanent solution. Better user experience from a hard drive (partition) install. ;)

---

### Post by wildmanne39 on 2012-02-18
That is true wubi is not a permanent install solution but your internet is the same in wubi as it is in normal install and the process for getting internet to work is the same.

Please follow the directions in my last post that usually gets your wireless device to work but as stated in other posts always copy and paste for accuracy.
Thanks

---

### Post by josephmills on 2012-02-18
> **wildmanne39 said:**
> 
Please follow the directions in my last post that usually gets your wireless device to work but as stated in other posts always copy and paste for accuracy.
Thanks

wildmanne  +1 
hammadsiddiqui if you do not know/trust what you are typing in. It is always a good idea just too ask. That is what we are here for :) .In fact I would never enter anything into the terminal if I do not know what it is. Wildmanne is real smart, And knows what he is talking about. I hope that this helps and I can not wait to see your wireless up and running. Have a great one .

---

### Post by hammadsiddiqui on 2012-02-20
Thanks... budy it works.

---

### Post by hammadsiddiqui on 2012-02-20
> **wildmanne39 said:**
> Hi , please copy and paste all commands into the terminal for accuracy, this one is wrong, please paste the results again.
```
lspci -nnk l grep -iA2 net
```
Also you can try this it may get your wireless working.
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Add a single line:
```
options ath5k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks
Thanks, buddy it works. :)

---

### Post by hammadsiddiqui on 2012-02-20
> **Bucky Ball said:**
> Wubi install is not recommended for long term. Basically to try Ubuntu and see if you like. Not a permanent solution. Better user experience from a hard drive (partition) install. ;)
Yes you are right but i scared about partition installation, because it is bit confusing and if i install it in wrong manner it will delete my data.

---

### Post by hammadsiddiqui on 2012-02-20
> **josephmills said:**
> wildmanne  +1 
hammadsiddiqui if you do not know/trust what you are typing in. It is always a good idea just too ask. That is what we are here for :) .In fact I would never enter anything into the terminal if I do not know what it is. Wildmanne is real smart, And knows what he is talking about. I hope that this helps and I can not wait to see your wireless up and running. Have a great one .
Thanks for your advice. Appreciate it.

---

### Post by wildmanne39 on 2012-02-20
Hi, I am glad it worked, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by Bucky Ball on 2012-02-20
> **wildmanne39 said:**
> Hi, I am glad it worked, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

+1. This will help others. ;)

---

### Post by hammadsiddiqui on 2012-02-22
> **wildmanne39 said:**
> Hi, I am glad it worked, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you
Sure, why not. Well thanks to you all.

---

