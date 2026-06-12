---
title: "rfkill blocks wifi but can not unblock"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2011-09-11
[SIZE=3]Hi friends,

               I am new to Linux and currently learning Linux. I have dell inspirion mini 1018 and I have installed fedora 15 and Ubuntu 11.04 on it ( dual boot ) . 

I keep on trying different commands( to learn) and while giving a try to rfkill command I found that in Ubuntu 11.04 I can block wifi, bluetooth using 
"rfkill block all". But trying to unblock dose not work at all. If I boot in to fedora 15, I am able to unblock all blocked devices using " rfkill unblock all". 

Can someone please guide me why is it so or how can I unblock wifi and bluetooth on ubuntu itself. I mean if I come across such situation and I dont have fedora on that pc then what would be solution?[/SIZE]

---

### Post by bkratz on 2011-09-11
> **sujitrjadhav said:**
> [SIZE=3]Hi friends,

               I am new to Linux and currently learning Linux. I have dell inspirion mini 1018 and I have installed fedora 15 and Ubuntu 11.04 on it ( dual boot ) . 

I keep on trying different commands( to learn) and while giving a try to rfkill command I found that in Ubuntu 11.04 I can block wifi, bluetooth using 
"rfkill block all". But trying to unblock dose not work at all. If I boot in to fedora 15, I am able to unblock all blocked devices using " rfkill unblock all". 

Can someone please guide me why is it so or how can I unblock wifi and bluetooth on ubuntu itself. I mean if I come across such situation and I dont have fedora on that pc then what would be solution?[/SIZE]


You might want to post the output of 

```
rfkill list all
```

and
```
 lsmod
```

---

### Post by sujitrjadhav on 2011-09-11
Here is output of the commands before and after blocking and then trying to unblock.

sujit@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
sujit@ubuntu:~$ rfkill block all
sujit@ubuntu:~$ rfkill unblock all
sujit@ubuntu:~$ rfkill list
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
sujit@ubuntu:~$ lsmod
Module                  Size  Used by
ppp_deflate            12838  0 
zlib_deflate           26594  1 ppp_deflate
bsd_comp               12777  0 
ppp_async              17308  1 
crc_ccitt              12595  1 ppp_async
rndis_wlan             28293  0 
rndis_host             13521  1 rndis_wlan
cdc_ether              13033  1 rndis_host
cdc_phonet             12853  0 
usbnet                 25175  3 rndis_wlan,rndis_host,cdc_ether
cdc_acm                22150  3 
phonet                 29296  1 cdc_phonet
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
rfcomm                 38125  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rtl8192ce             120858  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sco                    17827  0 
bnep                   17785  0 
l2cap                  48656  4 rfcomm,bnep
joydev                 17322  0 
rtlwifi                78961  1 rtl8192ce
binfmt_misc            13213  1 
dell_laptop            13515  0 
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  2 rtl8192ce,rtlwifi
btusb                  18160  0 
dcdbas                 14054  1 dell_laptop
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              65493  5 rfcomm,sco,bnep,l2cap,btusb
snd                    55295  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
uvcvideo               66851  0 
serio_raw              12990  0 
cfg80211              156212  3 rndis_wlan,rtlwifi,mac80211
videodev               75143  1 uvcvideo
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
i915                  451033  3 
ahci                   21591  3 
drm_kms_helper         40745  1 i915
libahci                25548  1 ahci
drm                   184164  4 i915,drm_kms_helper
r8169                  42534  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
sujit@ubuntu:~$ 


I will be back again. Need to boot  in fedora to get wifi unblocked. sending this post with mobile gprs connection

---

### Post by bkratz on 2011-09-11
The module Dell_laptop often causes problems with rfkill, it might be worth a try to:

sudo rmmod -f dell-laptop

and see if everything improves. This would only be temporary and would have to make permanent before rebooting if it does help. If not, if will reload next time you reboot. If it does help we will make it permanent, just post back.

---

### Post by sujitrjadhav on 2011-09-11
Removing dell-laptop module did help. It working now. But does removing dell-laptop disable any other functionality?. Will it have any negative impact too? And how can I make it permanent if it is safe? Also note that of the four interfaces listed by rkill list now the two with word dell in them no more appear.

---

### Post by bkratz on 2011-09-12
> **sujitrjadhav said:**
> Removing dell-laptop module did help. It working now. But does removing dell-laptop disable any other functionality?. Will it have any negative impact too? And how can I make it permanent if it is safe? Also note that of the four interfaces listed by rkill list now the two with word dell in them no more appear.



Well, we have removed the Dell_laptop module many, many, times in the Networking and Wireless forum and no one has ever returned with any problems. It you see some negative results you can simply put it back in, but I don't think you will want too! It appears to be some part of the Dell_wmi module which decodes special function keys. Anyway, to make it permanent,

Please do:

```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit

```
Before you press Enter, proofread carefully. The double arrows append the line to any other lines currently in the file.

dell-laptop is now blacklisted and will not reload on boot, unless, of course, you edit /etc/modprobe.d/blacklist.conf to remove the blacklist line.

---

### Post by sujitrjadhav on 2011-09-12
> **bkratz said:**
> Well, we have removed the Dell_laptop module many, many, times in the Networking and Wireless forum and no one has ever returned with any problems. It you see some negative results you can simply put it back in, but I don't think you will want too! It appears to be some part of the Dell_wmi module which decodes special function keys. Anyway, to make it permanent,

Please do:

```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit

```Before you press Enter, proofread carefully. The double arrows append the line to any other lines currently in the file.

dell-laptop is now blacklisted and will not reload on boot, unless, of course, you edit /etc/modprobe.d/blacklist.conf to remove the blacklist line.

Problem is solved.
But I would like to say something more- This is first time I ever posted a problem here. And I never expected such an expert and speedy resolution. It was few months before that I switched to Ubuntu from Windows. I am really impressed and very happy that not only linux is better and free but it also has such a strong problem resolution system- credit goes to people like you. I will never ever go back to windows. I do not know how to express my thanks to you.

---

### Post by sujitrjadhav on 2011-09-12
Ps: A very minor issue with it is that 

[HTML]rfkill block all[/HTML]blocks bluetooth. and 

[HTML]rfkill unblock all[/HTML]unblocks it. But bluetooth do not work unless you turn off bluetooth and restart.

---

### Post by bkratz on 2011-09-12
Glad to have been able to help you. I don't really understand your very last post, is this some sort of problem? You really should not have to mess around with rfkill block and unblock all commands at all, anymore since that module was blacklisted.

---

### Post by sujitrjadhav on 2011-09-12
[SIZE=2]I mean that
```
rfkill unblock all
```
or
```
rfkill unblock bluetooth
```

Unblocks blocked Bluetooth and Bluetooth "appears" as turned on. But still it and its settings are not accessible. "Turn off Bluetooth" option is only accessible option and if I turn Bluetooth off and turn it on again then only it works. 
[/SIZE]

---

### Post by lkjoel on 2011-09-12
Try this: [http://lkubuntu.wordpress.com/2011/09/07/how-to-fix-rfkill-issues/](http://lkubuntu.wordpress.com/2011/09/07/how-to-fix-rfkill-issues/)
EDIT: Is it fixed or not?

---

### Post by sujitrjadhav on 2011-09-12
Problem is already solved with simple commands. I just wanted to share info that turning bluetooth off and then again on is necessary to get it working fully. Anyway thanks very much for help.

---

### Post by lkjoel on 2011-09-12
Could you mark this thread as solve then? Thread tools->Mark this thread as solved

---

