---
title: "RTL8180 Ubuntu Package"
date: 2005-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Termina on 2005-11-27
This is the rtl8180-sa2400 package from sourceforge.

It doesn't compile (easily) on ubuntu, but I finnally got it working.

Thought I'd share it with everyone who uses that chipset.

See this website for a list of cards that are known to work.
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

This was compiled using the 2.6.12-10-386 kernel, I'm not sure if it'll work with any other kernels. 

Make sure to add

> 
auto wlan0
iface wlan0 inet dhcp


to /etc/network/interfaces

This is my first package, so I hope you enjoy it. Anyone know how I can submit it to the ubuntu respositories?

This module should load on bootup, but to load it manually:

> 
insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211_crypt-r8180.ko
insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211_crypt_wep-r8180.ko
insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211-r8180.ko
insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/r8180.ko


Unlike using ndiswrapper, or the provided realtek drivers, this can go into managed/monitor mode.

I had to use .tar.gz which contains .deb file, since I couldn't upload it otherwise.

Enjoy!

---

### Post by alesdoc on 2005-11-29
[QUOTE=Termina]This is the rtl8180-sa2400 package from sourceforge.

It doesn't compile (easily) on ubuntu, but I finnally got it working.[/QUOTE]

Hi,

thanks for your package:)

I friend of mine has an rtl8180. Using ndiswrapper we've installed it, but after a reinstallation the ndiswrapper doesn't work. It's crazy because we've done tha same things.....but it doesn't work. We'va also tried to compile the source but we couldn't do it.

Can you tell me....how have you done?

Thanks a lot

---

### Post by orbinick on 2005-11-29
It works for me as intended, flawlessly, but you're right, I use the 686 kernel and it doesn't work.

Luckily, I keep my previous grub boot kernels.

EDIT

Found a windows driver that works on any kernel with ndiswrapper, even at boot!!

Find my post here:[http://ubuntuforums.org/showthread.php?t=96319](http://ubuntuforums.org/showthread.php?t=96319)

and try it out. But I'd rather use your DEB based driver because it works as it was intended so I can't wait for a new compiled deb

---

### Post by encompass on 2005-12-20
Fantastic I think it is working... I will try it when I get a wireless connection to use at the school.  Thanks!  I have looked everywhere for a driver and I hope this will work.

---

### Post by sutech on 2005-12-20
It works :D :D :D

This is really great! I had a problem with ndiswrapper (quite frequent kernel panic, at least one per day ). And this may solve my problem (it isn't up more then 10 minutes, but I hope)

---

### Post by Gandalf on 2005-12-20
[QUOTE=Termina] insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211_crypt-r8180.ko
insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211_crypt_wep-r8180.ko
insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211-r8180.ko
insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/r8180.ko
[/QUOTE] It should be instead:
```

modprobe ieee80211_crypt-r8180
modprobe ieee80211_crypt_wep
modprobe ieee80211-r8180
modprobe r8180

```

but i'm pretty sure that running [COLOR="Blue"]modprobe r8180[/COLOR] will add the others, i can't confirm it because i dont have this card to try it but you can try it yourself by doing rmmod instead of modprobe in the reversed order to the above modules names

---

### Post by az on 2005-12-20
[QUOTE=alesdoc]Hi,

thanks for your package:)

I friend of mine has an rtl8180. Using ndiswrapper we've installed it, but after a reinstallation the ndiswrapper doesn't work. It's crazy because we've done tha same things.....but it doesn't work. We'va also tried to compile the source but we couldn't do it.

Can you tell me....how have you done?

Thanks a lot[/QUOTE]
the newset version of ndiswrapper always uses the newest version of the inf file.  The INF file that came with your card may be too old for ndiswrapper.  that is why it may work fine until you upgrade from, say, hoary to breezy and then it stops working.  It should work fine if you use the very latest inf file from realtek.

---

### Post by az on 2005-12-20
[QUOTE=Termina]This is the rtl8180-sa2400 package from sourceforge.

It doesn't compile (easily) on ubuntu, but I finnally got it working.

Thought I'd share it with everyone who uses that chipset.

See this website for a list of cards that are known to work.
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

This was compiled using the 2.6.12-10-386 kernel, I'm not sure if it'll work with any other kernels. 

Make sure to add



to /etc/network/interfaces

This is my first package, so I hope you enjoy it. Anyone know how I can submit it to the ubuntu respositories?

This module should load on bootup, but to load it manually:



Unlike using ndiswrapper, or the provided realtek drivers, this can go into managed/monitor mode.

I had to use .tar.gz which contains .deb file, since I couldn't upload it otherwise.

Enjoy![/QUOTE]


I will see if this has been discussed on the ubuntu kernel-team mailing list.  It would be a great driver to include in the stock kernel!

---

### Post by jamesshuang on 2005-12-20
When I tried to compile the driver, I got a pointer error. Oddly enough, when I went in and removed the pointer operator, it compiled fine and ran fine too. Any clues on why? :-p

---

### Post by forbmj on 2005-12-20
how can we enable the WPA support with this driver? Thanks.

---

### Post by encompass on 2005-12-26
Just a quick note, when I used the older driver and the newer one... if I try to use both the land connection and the wireless with the open source driver... I would get lost connections.  infact, I couldn't find any othere way of getting a dhcp connection without rebooting and trying again.  Iteresting, but when I disabled the auto startup of my eth0 connection and tried using the wireless card it would work.  Funky, but that is what happens to me.
I have reported this to the creator of the driver, but he never responds, I say if it happens to you too, ring him up and lets get this driver fixed. :p

---

### Post by encompass on 2005-12-31
I would look at the man page for iwconfig this tool set is the way for you.

> man iwconfig

There are many features that should get you started.  Google it too.  Many examples show how they setup there security in wlan and linux.

---

### Post by _MiniMe_ on 2006-01-10
[QUOTE=Termina]
This was compiled using the 2.6.12-10-386 kernel, I'm not sure if it'll work with any other kernels. 
[/QUOTE]

No, It doesn't. I'm using the K7 kernel and it won't load (wrong format error). So I've decided to compile the drivers by myself. I first tried to compile the original realtek-drivers but it didn't work. Strange thing is, with the opensource-drivers I get the same error. It alway complains about "r8180_core.c" and a missing field named "slot_name" in some struct. Here is the complete (german) output:

/home/remrot/rtl8180-0.21/r8180_core.c: In function `rtl8180_pci_probe':
/home/remrot/rtl8180-0.21/r8180_core.c:3632: Fehler: structure hat kein Element namens »slot_name«
make[2]: *** [/home/remrot/rtl8180-0.21/r8180_core.o] Fehler 1
make[1]: *** [_module_/home/remrot/rtl8180-0.21] Fehler 2
make[1]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.12-10-k7«
make: *** [2.4] Fehler 2

I hope you can help me, I could not find anything with google. And I'd really like to keep my kernel. But thanks anyway for bringing us the package!

---

### Post by direwolf on 2006-01-24
You were using the wrong source as evidenced by the following line:
/home/remrot/rtl8180-0.21/

You were using the "rtl8180-0.21" source (like from the main page) when you should be using the source from the [CVS]("http://cvs.sourceforge.net/viewcvs.py/rtl8180-sa2400/").

---

### Post by _MiniMe_ on 2006-01-24
Thanks for your reply!  I guess I didn't read the "important notes" carefully enough...

 But I'm not sure which CVS driver I should choose. I think it hast to be either the "rtl8180-sa2400-dev" or the "rtl818x-newstack" with the "ieee80211" stack. Do you know whick is the right one? Or maybe which one works better?

thx

---

### Post by direwolf on 2006-01-28
[QUOTE=_MiniMe_]Thanks for your reply!  I guess I didn't read the "important notes" carefully enough...

 But I'm not sure which CVS driver I should choose. I think it hast to be either the "rtl8180-sa2400-dev" or the "rtl818x-newstack" with the "ieee80211" stack. Do you know whick is the right one? Or maybe which one works better?

thx[/QUOTE]

No problem :) 

rtl8180-sa2400-dev hasn't been updated in a while - the rtl818x-newstack is the newer version and *should* also work. Personally, I chose the older rtl8180-sa2400-dev because I know it has worked fine for me in the past. 

If you pressed me to advise one I'd say go with the rtl8180-sa2400-dev and go to the rtl818x-newstack only if you experience problems. You can also check the forums on the sourceforge site before you decide and see if there is anything more about it. 

HTH!

---

### Post by _MiniMe_ on 2006-01-28
thx,

 I tried the "dev" drivers and they compiled without a problem. They seem to work properly, i.e. they are successfully loaded and iwconfig shows my wlan-card. The only thing you need to do is to 'modprobe arc4' before you modprobe the last three rtl8180-modules. I don't have a wlan-network here, so I can't test if it connects properly atm...

cu

---

### Post by BiggoCharley on 2006-01-30
[QUOTE=Termina]This is the rtl8180-sa2400 package from sourceforge.

It doesn't compile (easily) on ubuntu, but I finnally got it working.

Thought I'd share it with everyone who uses that chipset.

See this website for a list of cards that are known to work.
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

This was compiled using the 2.6.12-10-386 kernel, I'm not sure if it'll work with any other kernels. 

Make sure to add



to /etc/network/interfaces

This is my first package, so I hope you enjoy it. Anyone know how I can submit it to the ubuntu respositories?

This module should load on bootup, but to load it manually:



Unlike using ndiswrapper, or the provided realtek drivers, this can go into managed/monitor mode.

I had to use .tar.gz which contains .deb file, since I couldn't upload it otherwise.

Enjoy![/QUOTE]


I downloaded the tar.gz file and tried to open it with Archive Manager and I get an error message "archive type not supported". To insure that I didn't have a corrupted file I downloaded it again and tried to open it with the same results.  Can any one suggest any reason for this (to this newbie)?
:confused:

---

### Post by BiggoCharley on 2006-01-30
[QUOTE=Termina]This is the rtl8180-sa2400 package from sourceforge.

It doesn't compile (easily) on ubuntu, but I finnally got it working.

Thought I'd share it with everyone who uses that chipset.

See this website for a list of cards that are known to work.
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

This was compiled using the 2.6.12-10-386 kernel, I'm not sure if it'll work with any other kernels. 

Make sure to add



to /etc/network/interfaces

This is my first package, so I hope you enjoy it. Anyone know how I can submit it to the ubuntu respositories?

This module should load on bootup, but to load it manually:



Unlike using ndiswrapper, or the provided realtek drivers, this can go into managed/monitor mode.

I had to use .tar.gz which contains .deb file, since I couldn't upload it otherwise.

Enjoy![/QUOTE]

I downloaded the .tar.gz file but when I tried to open it with Archive Manager I got an error message thet the "archive type is not supported". To insure that I didn't have a corrupted file I downloaded it again and tried to open it with the same results.  Could anyone suggest (to this newbie) what might cause this.:confused:

---

### Post by BiggoCharley on 2006-01-30
OOPS!! sorry about the "double post -- I didn't see my post the first time around so I repeated it in error.:(  and :confused:

---

### Post by roosterx on 2006-03-06
Exactly how do i install this package?

I've DL it to my desktop, but where do i go from there, even tried dpkg install with no luck.

TIA

---

### Post by Termina on 2006-03-13
Have you tried 'dpkg -i filename.deb'?

---

### Post by kasemodz on 2006-04-02
Um I'm running 2.6.12-10-k7. Is it possible to install those modules into this kernel? Right now when I installed it made a new folder in /lib/modules/2.6.12-10-386. Could I just extract the folder and manually insmod the modules?

---

### Post by kasemodz on 2006-04-02
well i did that, and it keeps giving me error invalid module format.

---

### Post by _MiniMe_ on 2006-04-02
I tried that too (see page 2 of this thread), it doesn't work with k7-kernels. But it is fairly easy to compile the driver by yourself. See also page 2 ;)

good luck

---

### Post by kasemodz on 2006-04-02
MiniMe, it compiled fine but when I go to insmod i get these errors.
This is my make.
> admin@OnDemand:~/Desktop/realtek/rtl8180-sa2400-dev$ make
make -C /lib/modules/2.6.12-10-k7/build SUBDIRS=/home/admin/Desktop/realtek/rtl8                                             180-sa2400-dev MODVERDIR=/home/admin/Desktop/realtek/rtl8180-sa2400-dev modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-k7'
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_rx.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_tx.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_wx.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_module.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_crypt.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_crypt_wep.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180_core.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180_sa2400.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180_93cx6.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180_wx.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180_pm.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180_max2820.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180_gct.o
  CC [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180_rtl8225.o
  LD [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211-r8180.o
  LD [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180.o
  LD [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_crypt-r8180.o
  LD [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_crypt_wep-r81                                             80.o
  Building modules, stage 2.
  MODPOST
  CC      /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211-r8180.mod.o
  LD [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211-r8180.ko
  CC      /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_crypt-r8180.m                                             od.o
  LD [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_crypt-r8180.k                                             o
  CC      /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_crypt_wep-r81                                             80.mod.o
  LD [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/ieee80211_crypt_wep-r81                                             80.ko
  CC      /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180.mod.o
  LD [M]  /home/admin/Desktop/realtek/rtl8180-sa2400-dev/r8180.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-k7'


Then here are the errors when I try to insmod them.
> admin@OnDemand:~/Desktop/realtek/rtl8180-sa2400-dev$ sudo insmod ieee80211-r8180                                             .ko
insmod: error inserting 'ieee80211-r8180.ko': -1 Unknown symbol in module
admin@OnDemand:~/Desktop/realtek/rtl8180-sa2400-dev$ sudo insmod r8180.ko
insmod: error inserting 'r8180.ko': -1 Unknown symbol in module
admin@OnDemand:~/Desktop/realtek/rtl8180-sa2400-dev$ sudo insmod ieee80211_crypt
insmod: error inserting 'ieee80211_crypt_wep-r8180.ko': -1 Unknown symbol in mod


I dunno whats up with the unknown symbol in mod. I'm using the rtl8180-sa2400-dev. Here is my dmesg
> [4784753.389000] ieee80211_crypt_wep_r8180: Unknown symbol ieee80211_r8180_register_crypto_ops
[4784753.389000] ieee80211_crypt_wep_r8180: Unknown symbol ieee80211_r8180_unregister_crypto_ops
[4784787.121000] ieee80211_r8180: Unknown symbol ieee80211_r8180_get_crypto_ops
[4784787.121000] ieee80211_r8180: Unknown symbol ieee80211_r8180_crypt_deinit_entries
[4784787.122000] ieee80211_r8180: Unknown symbol ieee80211_r8180_crypt_deinit_handler
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_wake_queue
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_stop_queue
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_rx
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_flush_scan
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_8023_hardstartxmit
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_alloc
[4784804.736000] r8180: Unknown symbol wlan_frequencies
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_set_master_essid
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_wx_get_scan
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_wx_set_rate
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_wx_get_encode
[4784804.736000] r8180: Unknown symbol ieee80211_r8180_free
[4784804.737000] r8180: Unknown symbol ieee80211_r8180_wx_set_essid
[4784804.737000] r8180: Unknown symbol ieee80211_r8180_wx_set_encode
[4784804.737000] r8180: Unknown symbol ieee80211_r8180_wx_get_essid
[4784804.737000] r8180: Unknown symbol ieee80211_r8180_wx_get_rate
[4784804.737000] r8180: Unknown symbol ieee80211_probe_hidden
[4784804.737000] r8180: Unknown symbol ieee80211_r8180_reset_queue
[4784804.737000] r8180: Unknown symbol ieee80211_r8180_wx_set_wap
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_wake_queue
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_stop_queue
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_rx
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_flush_scan
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_8023_hardstartxmit
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_alloc
[4785064.702000] r8180: Unknown symbol wlan_frequencies
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_set_master_essid
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_wx_get_scan
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_wx_set_rate
[4785064.702000] r8180: Unknown symbol ieee80211_r8180_wx_get_encode
[4785064.703000] r8180: Unknown symbol ieee80211_r8180_free
[4785064.703000] r8180: Unknown symbol ieee80211_r8180_wx_set_essid
[4785064.703000] r8180: Unknown symbol ieee80211_r8180_wx_set_encode
[4785064.703000] r8180: Unknown symbol ieee80211_r8180_wx_get_essid
[4785064.703000] r8180: Unknown symbol ieee80211_r8180_wx_get_rate
[4785064.703000] r8180: Unknown symbol ieee80211_probe_hidden
[4785064.703000] r8180: Unknown symbol ieee80211_r8180_reset_queue
[4785064.703000] r8180: Unknown symbol ieee80211_r8180_wx_set_wap
[4787528.114000] ieee80211_crypt_r8180: disagrees about version of symbol struct_module
[4787557.634000] ieee80211_crypt_wep_r8180: disagrees about version of symbol struct_module
[4792623.704000] No module found in object
[4792623.706000] No module found in object
[4792623.709000] No module found in object
[4792623.711000] No module found in object
[4793324.488000] ieee80211_r8180: Unknown symbol ieee80211_r8180_get_crypto_ops
[4793324.488000] ieee80211_r8180: Unknown symbol ieee80211_r8180_crypt_deinit_entries
[4793324.488000] ieee80211_r8180: Unknown symbol ieee80211_r8180_crypt_deinit_handler
[4793337.946000] r8180: Unknown symbol ieee80211_r8180_wake_queue
[4793337.946000] r8180: Unknown symbol ieee80211_r8180_stop_queue
[4793337.946000] r8180: Unknown symbol ieee80211_r8180_rx
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_flush_scan
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_8023_hardstartxmit
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_alloc
[4793337.947000] r8180: Unknown symbol wlan_frequencies
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_set_master_essid
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_wx_get_scan
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_wx_set_rate
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_wx_get_encode
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_free
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_wx_set_essid
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_wx_set_encode
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_wx_get_essid
[4793337.947000] r8180: Unknown symbol ieee80211_r8180_wx_get_rate
[4793337.947000] r8180: Unknown symbol ieee80211_probe_hidden
[4793337.948000] r8180: Unknown symbol ieee80211_r8180_reset_queue
[4793337.948000] r8180: Unknown symbol ieee80211_r8180_wx_set_wap
[4793377.301000] ieee80211_crypt_wep_r8180: Unknown symbol ieee80211_r8180_register_crypto_ops
[4793377.301000] ieee80211_crypt_wep_r8180: Unknown symbol ieee80211_r8180_unregister_crypto_ops


---

### Post by _MiniMe_ on 2006-04-03
Sounds strange... did you 'modprobe arc4'  before loading the rtl-modules? Have you tried a 'depmod -e' before loading the modules?

btw: you should really use 'modprobe' instead of 'insmod'....

---

### Post by encompass on 2006-04-10
Thank you for the help.... it works in the 386 kernel...
But many of my features that I use with the computer need 686 support to work the best.  I tried getting the cvs but haven't found the line for line entery to get the cvs download to work.  Could someone please provide them for this driver on this post?  Thanks...

---

### Post by deus777 on 2006-06-04
[QUOTE=Gandalf]It should be instead:
```

modprobe ieee80211_crypt-r8180
modprobe ieee80211_crypt_wep
modprobe ieee80211-r8180
modprobe r8180

```

but i'm pretty sure that running [COLOR="Blue"]modprobe r8180[/COLOR] will add the others, i can't confirm it because i dont have this card to try it but you can try it yourself by doing rmmod instead of modprobe in the reversed order to the above modules names[/QUOTE]

I've installed the .deb with dpkg -i and I have the four .ko files in /lib/modules/2.6.12-10-386/kernel/net/rtl8180, but when I try to do a modprobe r8180 I get:

FATAL: Module r8180 not found.

Does anyone have any ideas?

---

### Post by rettie on 2008-08-24
Try

"depmod -a"

before modprobing, this worked for my new MSI wind machine.

Cheers!

---

### Post by ukupacha on 2008-10-13
> **Termina said:**
> This is the rtl8180-sa2400 package from sourceforge.

It doesn't compile (easily) on ubuntu, but I finnally got it working.

Thought I'd share it with everyone who uses that chipset.

See this website for a list of cards that are known to work.
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

This was compiled using the 2.6.12-10-386 kernel, I'm not sure if it'll work with any other kernels. 

Make sure to add



to /etc/network/interfaces

This is my first package, so I hope you enjoy it. Anyone know how I can submit it to the ubuntu respositories?

This module should load on bootup, but to load it manually:



Unlike using ndiswrapper, or the provided realtek drivers, this can go into managed/monitor mode.

I had to use .tar.gz which contains .deb file, since I couldn't upload it otherwise.

Enjoy!

you are awesome Termina. there should be more people like you

---

### Post by releone on 2009-10-12
can u help me i m not able to work with rtl8180

---

