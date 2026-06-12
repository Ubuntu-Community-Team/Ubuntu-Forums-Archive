---
title: "Ubuntu abruptly shuts down after LUKS boot prompt screen"
date: 2018-03-17
forum: New to Ubuntu
---

### Post by rondinellisr on 2018-03-17
Two days ago, I installed Ubuntu 16.04.4 (as my only OS) in my Acer laptop, with UEFI/Secure Boot and LVM/full disk encryption enabled. During the installation, I've selected to 
update the system while installing it.

After a fresh install, I updated & upgraded the system. In addition, as I saw in some blogs/forums while googling about my integrated graphics (Intel 520) and processor (Skylake), I also installed (in the following order):

[LIST=1]
[*]_intel-microcode_, using the official repository version (3.20180108). Right after, I saw that a newer version was available [here]("https://downloadcenter.intel.com/download/27591/Linux-Processor-Microcode-Data-File?product=88193"), so I follow [this]("https://www.cyberciti.biz/faq/install-update-intel-microcode-firmware-linux/") to proceed with the manual update - the process was smooth and without errors, but when I check if the version was updated, it returns the same version as the one before;*****
[*]Added this [PPA]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers") to get the most updated open graphics;*****
[*]_tlp_ (I didn't change any of its default values);
[*]*Intel graphics installer* following this [link]("https://www.techzim.co.zw/2017/06/tuning-intel-graphics-card-ubuntu-16-04/");*****
[*]_virtualbox_ using the official repository packages. During the installation, a window pops up saying that in order to use it, I must turn off the *Secure boot* mode, so I did it.*****
[/LIST]
***** = Installed & rebooted.

After this last reboot, during the booting screen where it prompts for my LUKS password, I entered it and it accepted but suddenly the laptop just turned off, abruptly.

After a while, I turned it on again and I got in the Ubuntu desktop without problems. I've tried to use _journalctl_ to retrieve my last boot log, but I just found out [here]("https://askubuntu.com/questions/765315/how-to-find-previous-boot-log-after-ubuntu-16-04-restarts/858126") that - by default - the logs aren't persistent, losing them after each boot.

So, I would like to know if you guys think that something went wrong because of the changes that I did? There is another way that I can check what happened during that boot?

Hardware details:

[LIST]
[*]Acer Aspire V 15 (V3-575T)
[*]Intel Core i5-6200U
[*]Intel HD Graphics 520
[/LIST]

**P.S.** All the firmware updates (to this date) [available]("https://www.acer.com/ac/en/US/content/support-product/6444?b=1") for my laptop model were installed while I was using Windows.


[HR][/HR]
**UPDATE**:

Yesterday, I tried to create a VM machine using VirtualBox (for the first time after I had installed it) and - during the boot to start the ISO installer - my laptop froze completely, with no responses at all (nor trackpad, function keys, neither the virtual terminals).

I forced a shutdown and copied bellow the log that was generated during the event:

```
Mar 16 18:08:17 GNULinux kernel: [UFW BLOCK] IN=wlp2s0 OUT= MAC=01:00:5e:00:00:01:70:8b:cd:c4:2b:f0:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PR
Mar 16 18:08:17 GNULinux kernel: [UFW BLOCK] IN=wlp2s0 OUT= MAC=33:33:00:00:00:00:70:8b:cd:c4:2b:f0:86:dd SRC=0000:0000:0000:0000:0000:0000:0000:0000 
Mar 16 18:08:25 GNULinux NetworkManager[1117]: <warn>  [1521238105.5562] device (vboxnet0): failed to find device 4 'vboxnet0' with udev
Mar 16 18:08:25 GNULinux NetworkManager[1117]: <info>  [1521238105.5599] manager: (vboxnet0): new Ethernet device (/org/freedesktop/NetworkManager/Dev
Mar 16 18:08:25 GNULinux NetworkManager[1117]: <info>  [1521238105.5874] devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Mar 16 18:08:25 GNULinux NetworkManager[1117]: <info>  [1521238105.5874] device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no i
Mar 16 18:08:25 GNULinux gnome-session[1943]: (nm-applet:2105): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Mar 16 18:08:25 GNULinux gnome-session[1943]: (nm-applet:2105): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Mar 16 18:08:25 GNULinux gnome-session[1943]: (nm-applet:2105): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Mar 16 18:08:25 GNULinux gnome-session[1943]: (nm-applet:2105): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Mar 16 18:08:25 GNULinux gnome-session[1943]: (nm-applet:2105): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Mar 16 18:08:25 GNULinux gnome-session[1943]: (nm-applet:2105): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Mar 16 18:08:25 GNULinux gnome-session[1943]: (nm-applet:2105): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Mar 16 18:08:30 GNULinux kernel: [drm] HPD interrupt storm detected on connector DP-1: switching from hotplug detection to polling
Mar 16 18:08:57 GNULinux kernel: [UFW BLOCK] IN=wlp2s0 OUT= MAC=01:00:5e:00:00:fb:6c:ab:31:b1:e5:40:08:00 SRC=10.10.10.4 DST=224.0.0.251 LEN=32 TOS=0x
```

---

