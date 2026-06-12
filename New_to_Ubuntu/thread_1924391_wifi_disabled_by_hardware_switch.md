---
title: "wifi disabled by hardware switch?"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by faraz_k86 on 2012-02-12
just to note that wifi was not working on windows, it was installed but was not detecting any wifi networks

SO I installed Ubuntu 11.10 on my Compaq NC6220 in hopes it will resolve the issue.

I have the same problem there, its not detecting any wifi networks.. but it did inform me that "wifi was disabled by hardware switch"

the hardware switch is not working as the light in it does not come on.

any way I can force it on without the hardware switch?

thanks

---

### Post by bruban on 2012-02-12
Check your laptop's manual or online documentation for the location of the switch.

Some laptops have a switch on the outside of the laptop that you can use to disable your wifi network. On some Dell models for example it is on the right hand side closest to the user.

If you have a hardware switch, you'll have to turn the switch on before your wifi will work.

---

### Post by faraz_k86 on 2012-02-12
i already know the location of the hardware switch... 

its a soft key type: [http://www.cedarpc.com/employee/upload_ajax_simple/uploads/20101021165043-100_33541.jpg](http://www.cedarpc.com/employee/upload_ajax_simple/uploads/20101021165043-100_33541.jpg)

the problem is i think the switch is defective as its light does not turn on.

regards

---

### Post by bruban on 2012-02-12
sorry. I can't help further.

---

### Post by wildmanne39 on 2012-02-12
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Mark Phelps on 2012-02-13
> **faraz_k86 said:**
> the problem is i think the switch is defective as its light does not turn on.

These switches require special drivers and are generally not well detected or handled in Linux.  One one laptop I had, I had to tape cardboard over the switch as I kept pressing it by habit in Ubuntu and, although it would turn off, it would not turn ON.

You will probably have to turn it ON and leave it ON in Windows.  But, if as you say, it doesn't turn ON in Windows either, it could be defective and, as far as I know, there is no way to fix this in Ubuntu.

---

### Post by faraz_k86 on 2012-02-13
> **wildmanne39 said:**
> Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

```
ubuntu@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
ubuntu@ubuntu:~$ lspci -nnk | grep iA2 net
grep: net: No such file or directory
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:4223] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1351]
	Kernel driver in use: ipw2200
--
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)
	Subsystem: Hewlett-Packard Company Device [103c:0944]
	Kernel driver in use: tg3
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               22565  0 
lp                     17455  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
bnep                   17923  2 
ac97_bus               12642  1 snd_ac97_codec
bluetooth             148839  7 bnep
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
joydev                 17393  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39822  0 
ipw2200               146148  0 
libipw                 46701  1 ipw2200
tifm_7xx1              12937  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
cfg80211              172392  2 ipw2200,libipw
tifm_core              15040  1 tifm_7xx1
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
irda                  185428  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
ppdev                  12849  0 
psmouse                73673  0 
soundcore              12600  1 snd
serio_raw              12990  0 
lib80211               14570  2 ipw2200,libipw
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
parport_pc             32114  1 
parport                40930  3 lp,ppdev,parport_pc
crc_ccitt              12595  1 irda
tpm_infineon           13200  0 
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
i915                  505108  3 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
usb_storage            44173  1 
uas                    17699  0 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
tg3                   132972  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
wmi                    18744  1 hp_wmi
zram                   18007  1 
ubuntu@ubuntu:~$ 

```

Thanks

---

### Post by faraz_k86 on 2012-02-14
so.. can I turn it on from ubuntu?

---

### Post by wildmanne39 on 2012-02-14
Hi, please try this:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0
```
rmmod -f ipw2200
rfkill unblock all
modprobe ipw2200
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thanks

---

### Post by faraz_k86 on 2012-02-15
> **wildmanne39 said:**
> Hi, please try this:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0
```
rmmod -f ipw2200
rfkill unblock all
modprobe ipw2200
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thanks

Thanks, but the problem is still the same.. It still says that "wifi has been disabled by hardware switch"

:(

---

### Post by wildmanne39 on 2012-02-15
Hi, before we go further, does the light come on for your wireless in windows and just does not detect networks or the light does not come on in windows either?

If it does, turn it off in windows then back on and boot ubuntu and see if that helps, a lot of times that will turn the wireless on in ubuntu as well.
Thanks

---

### Post by pete04 on 2012-02-15
This may very well not be helpful, but I accidentally disabled my wifi with alt+F2. Didn't realize F2 was a hardware switch for my wifi... is there a function key tied to a hardware wifi switch? I looked at the photo you linked above, but couldn't tell.

---

### Post by faraz_k86 on 2012-02-16
> **wildmanne39 said:**
> Hi, before we go further, does the light come on for your wireless in windows and just does not detect networks or the light does not come on in windows either?

If it does, turn it off in windows then back on and boot ubuntu and see if that helps, a lot of times that will turn the wireless on in ubuntu as well.
Thanks

No the light does not come on. The wifi adapter is detected by windows and is installed but it does not detect any wifi networks. Also like I mentioned the button as well as the light does not work so that may be the reason.

I'd like to let you know that the output I have you after you gave me the codes to run was on live CD. but since your suggestion required me too restart the system after saving the file. I installed Ubuntu and then tried your solution. Would that have something to do with it not working? As the results were from live CD and the solution was asked on an installed Ubuntu?

---

### Post by faraz_k86 on 2012-02-16
> **pete04 said:**
> This may very well not be helpful, but I accidentally disabled my wifi with alt+F2. Didn't realize F2 was a hardware switch for my wifi... is there a function key tied to a hardware wifi switch? I looked at the photo you linked above, but couldn't tell.

Thanks but I checked that before as well there is no fn function related to my wifi.  It's only through that key.

---

### Post by ubni on 2012-02-16
> **faraz_k86 said:**
> Thanks but I checked that before as well there is no fn function related to my wifi.  It's only through that key.

Can you lift the keyboard layer and press the key sensor somehow otherwise?

---

### Post by faraz_k86 on 2012-02-16
> **ubni said:**
> Can you lift the keyboard layer and press the key sensor somehow otherwise?

yup, Ive tried that.. doesnt work..

well the reason I removed Windows and installed Ubuntu was in hopes that there was some software way like from terminal to enable the wifi

---

### Post by wildmanne39 on 2012-02-16
Hi, repost all the information from those commands again from the installed ubuntu.
Thanks

---

### Post by faraz_k86 on 2012-02-16
> **wildmanne39 said:**
> Hi, repost all the information from those commands again from the installed ubuntu.
Thanks

```
faraz@faraz-HP-Compaq-nc6220-PU982AW-ABA:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux faraz-HP-Compaq-nc6220-PU982AW-ABA 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
faraz@faraz-HP-Compaq-nc6220-PU982AW-ABA:~$ lspci -nnk | grep -iA2 net
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:4223] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1351]
	Kernel driver in use: ipw2200
--
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)
	Subsystem: Hewlett-Packard Company Device [103c:0944]
	Kernel driver in use: tg3
faraz@faraz-HP-Compaq-nc6220-PU982AW-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

faraz@faraz-HP-Compaq-nc6220-PU982AW-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
faraz@faraz-HP-Compaq-nc6220-PU982AW-ABA:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
ipw2200               146148  0 
bnep                   17923  2 
bluetooth             148839  7 bnep
joydev                 17393  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
ppdev                  12849  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 39822  0 
psmouse                73673  0 
irda                  185428  0 
soundcore              12600  1 snd
serio_raw              12990  0 
libipw                 46701  1 ipw2200
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
cfg80211              172392  2 ipw2200,libipw
i915                  505108  3 
tifm_7xx1              12937  0 
parport_pc             32114  1 
crc_ccitt              12595  1 irda
tifm_core              15040  1 tifm_7xx1
tpm_infineon           13200  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
binfmt_misc            17292  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211               14570  2 ipw2200,libipw
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
tg3                   132972  0 
faraz@faraz-HP-Compaq-nc6220-PU982AW-ABA:~$ 


```

Thank you

---

### Post by josephmills on 2012-02-16
could youo try this ```
sudo rmmod hp_wmi
```
does it work ? if not undo it with the command ```
sudo modprobe hp_wmi
```

---

### Post by faraz_k86 on 2012-02-16
Thanks a lot wildmanne39 for your help, but i just got a USB Wifi from a friend, ill just be using that :)

marking this as solved now :)

Cheers

---

### Post by wildmanne39 on 2012-02-17
Hi, your welcome! I am glad you have working wireless now.

---

### Post by adawro on 2012-06-05
I have found that entering to BIOS Setup and loading DEFAULT BIOS SETTINGS brings WIFI to life.

---

### Post by t4thfavor on 2012-06-10
> **adawro said:**
> I have found that entering to BIOS Setup and loading DEFAULT BIOS SETTINGS brings WIFI to life.

No idea why that worked... but same model of laptop (compaq NC6220) and wifi LED is now blinking happily away.

Thanks,

---

