---
title: "realtek rtl8192se wireless issue"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by gil.rito on 2014-03-09
Hi, I'm trying to solve the problem with this drive on my Toshiba Qosmio running ubuntu 12.04 LTS

I've tried all sort of tricks to solve the erratic signal strength that drops from 70% to 20%. 
If I use a usb with the new ubuntu kernel I d'ont have the problem. So I've compared the two systems with the wireless_script and I found that there are some diferences betteew the two systems. 

[http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)

The most notorious is  with the file rtl_pci.ko which is present on the usb version of ubuntu 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko

and is not present in my ubuntu installed in my machine (see below)

So my question is how can I solve this issue? If I try to compile myself the realtek rtl8192se I don't get this file.

Thanks. Gil
==============================================================
Ubuntu USB

```

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E3576B855061FB3E2B43629
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8363D6BED4EF1CF5A92482B
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     13B5FC2521B6DC5AB3F115C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


```
======================================================
Ubuntu Machine
```

***** modinfo *****

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B5184945312BE0F016AC596
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
parm:           fwlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           swlps:using linked sw control power save (default 1 is open)
 (bool)

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     953878FB72AD1AAE531C0BD
depends:        mac80211,cfg80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

```

---

### Post by gil.rito on 2014-03-11
Hi,

maybe this is not the correct section to post this question. Do you know how can I move this thread into the Networking & Wireless section?

---

### Post by amith3 on 2014-03-11
see this
[http://ubuntuforums.org/showthread.php?t=2087457](http://ubuntuforums.org/showthread.php?t=2087457)

---

### Post by varunendra on 2014-03-11
Hello gil.rito !

Which version have you been trying to compile? Link please.

Yes the drivers have changed quite a lot from kernel 3.2 to 3.11. But if you compile the same version manually, you should get same driver and same dependencies.

Please try this post to try compiling the driver backported from kernel 3.12 : [http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946](http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946)

---

### Post by gil.rito on 2014-03-11
Hi Varun

Thank you very much. I think I've fixed the problem using your instructions.

---

### Post by varunendra on 2014-03-11
You're welcome! And thanks for the feedback, it helps us as well as others in deciding which of the many fixes is more promising. :)

---

### Post by jimbo6 on 2014-03-19
I'm also going through terrible issues with my wifi showing similar fluctuating and dropping out symptoms as gil.rito. 

However I do not have much experience with Linux and do not know how to display diagnostic data. Could someone please advise me how to do it? Recently updated to 12.04 kernel 3.11 working off WPA2. Also running Wicd.

EDIT:
Started a new thread for my issue: [http://ubuntuforums.org/showthread.php?t=2212089](http://ubuntuforums.org/showthread.php?t=2212089)

---

