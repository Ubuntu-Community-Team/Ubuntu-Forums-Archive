---
title: "3d Drivers and Desktop Visual Effects Help"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by tlplw717 on 2011-12-26
Hi,
I am running Ubuntu 11.10 and have the graphics card Radeon HD 6490M, according to my Windows 7 Control Panel. (I cannot get my device manager to work but thats another issue, unless it relates to my current problem.
I cannot get any of my Desktop's Visual Effects to work. I have downloaded the ATI/AMD proprietary FGLRX graphics driver as the additional drivers section of my system settings tells me to do.
Any idea what is wrong?

---

### Post by wildmanne39 on 2011-12-26
Hi, welcome to the forum! I will try to help you I have limited experience with ATI/AMD drivers but let's see what drivers are load and if you can run 3D effects. 

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
lsmod
```
```
/usr/lib/nux/unity_support_test -p
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by tlplw717 on 2011-12-30
tlplw717@ubuntu:~$ lsmod
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  7 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
binfmt_misc            17540  1 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_usb_audio         118064  1 
usb_storage            57901  2 
uas                    18027  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_seq_midi           13324  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
fglrx                3101156  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
rts_pstor             445246  0 
wmi                    19256  1 hp_wmi
mac80211              462092  1 iwlagn
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
cfg80211              199587  2 iwlagn,mac80211
i915                  566827  2 
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
snd                    68266  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               82820  0 
r8169                  52788  0

---

### Post by tlplw717 on 2011-12-30
It is telling me the second one is an invalid command.
Thank you by the way

---

### Post by wildmanne39 on 2011-12-30
Hi, I just checked it is the right command and you are using 11.10 ubuntu unity right?
Thanks

---

### Post by tlplw717 on 2011-12-31
tlplw717@ubuntu:~$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  21
  Current serial number in output stream:  21

This was the output. I believe i have Unity running. I use Wubi to install

---

### Post by wildmanne39 on 2011-12-31
Hi, have a look at this link I think it will help your problem.
[http://askubuntu.com/questions/77636/getting-compiz-to-work-with-ubuntu-11-10-and-fglrx](http://askubuntu.com/questions/77636/getting-compiz-to-work-with-ubuntu-11-10-and-fglrx)
Thanks

---

### Post by Mark Phelps on 2012-01-01
I see you have the fglrx module loaded, but open a terminal and enter "fglrxinfo" (you might have to use "sudo" for this) and see what it says.

---

