---
title: "[SOLVED] Just Switched, and love Ubuntu! But need help with Belkin FSD6020..."
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Latino Boy on 2008-09-15
Hi Everyone, 

I just switched over to ubuntu this weekend. Linux is awesome and Ubuntu is ridiculously easy to setup and run.  Feels quicker and more stable than XP :).  That being said I'm an absolute noob.  

I tried using my wireless Belkin F5D6020 card, but after plugging in the light didn't even come up...I'm 100% new to linux please take it easy on me.  Any advice is greatly appreciated.  ( I did a search and saw a few threads on this...but I don't even know how to bring up the "command line" in Ubuntu,,,) 


Thanks!!!!

---

### Post by billgoldberg on 2008-09-15
I can't help with the card, but to open the terminal (bash shell), go to applications -> accessories -> terminal.

Or press "alt + f2" and type "gnome-terminal".

Or use system -> preferences -> keyboard shortcuts to assign a key to the terminal. I use f12.

---

### Post by MegaJim on 2008-09-15
Once you bring up the terminal like bill says, can you post the output of the following command, to help us show you which steps might need to be taken:

```
sudo lshw -C network
```

---

### Post by Latino Boy on 2008-09-15
OMG this forum is awesome I was not expecting lightning fast replies.

>  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a7:25:96
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=xx.xxx.x.xxx latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
darkhawk@darkhawk-laptop:~$ 


---

### Post by MegaJim on 2008-09-15
Is your wireless card plugged in?  If not, plug it in and repeat that command.  If it is plugged in your wireless is either not being detected or something (card slot/card) is defective.

---

### Post by Latino Boy on 2008-09-15
Yes it's plugged in...Hmmm...:confused: Do I have to enable it.  The port should be fine (i've never used it till now)

---

### Post by MegaJim on 2008-09-15
I think the best way to find out what is going on is for you to open up the system log (alt+f2) and type in gnome-system-log then hit enter.

Select syslog in the left bar and scroll to the bottom of the right hand list showing the system messages.

Now plug in your wireless card - you should see some bold messages come up the moment you plug it in; please post these to the forum so we can see what is happening.

---

### Post by Latino Boy on 2008-09-15
> Sep 15 19:17:01 darkhawk-laptop /USR/SBIN/CRON[6962]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 15 19:28:18 darkhawk-laptop kernel: [ 5679.109677] pccard: card ejected from slot 0
Sep 15 19:28:18 darkhawk-laptop NetworkManager: <debug> [1221521298.540145] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_1799_6020'). 
Sep 15 19:42:22 darkhawk-laptop kernel: [ 6521.560710] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
Sep 15 19:42:22 darkhawk-laptop kernel: [ 6521.560732] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
Sep 15 19:42:22 darkhawk-laptop kernel: [ 6521.560736] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
Sep 15 19:49:13 darkhawk-laptop kernel: [ 6932.191374] pccard: CardBus card inserted into slot 0
Sep 15 19:49:13 darkhawk-laptop NetworkManager: <debug> [1221522553.276823] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1799_6020'). 
Sep 15 19:49:35 darkhawk-laptop kernel: [ 6954.043389] pccard: card ejected from slot 0
Sep 15 19:49:35 darkhawk-laptop NetworkManager: <debug> [1221522575.095371] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_1799_6020'). 
Sep 15 19:53:50 darkhawk-laptop kernel: [ 7209.275790] pccard: CardBus card inserted into slot 0
Sep 15 19:53:50 darkhawk-laptop NetworkManager: <debug> [1221522830.704402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1799_6020'). 
Sep 15 20:04:45 darkhawk-laptop kernel: [ 7862.937714] pccard: card ejected from slot 0
Sep 15 20:04:45 darkhawk-laptop NetworkManager: <debug> [1221523485.189671] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_1799_6020'). 
Sep 15 20:05:29 darkhawk-laptop pulseaudio[5518]: shm.c: shm_open() failed: No such file or directory
Sep 15 20:05:29 darkhawk-laptop pulseaudio[5518]: pstream.c: Failed to import memory block.


How's that?


when I plugged in again:

> Sep 15 20:09:01 darkhawk-laptop NetworkManager: <debug> [1221523741.928085] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1799_6020'). 

---

### Post by MegaJim on 2008-09-15
Thats great.  According to the log the card is being detected, however no driver is being loaded, the next best step would be to follow this guide and install the ndiswrapper program and use the windows drivers for the card: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Latino Boy on 2008-09-15
> **MegaJim said:**
> Thats great.  According to the log the card is being detected, however no driver is being loaded, the next best step would be to follow this guide and install the ndiswrapper program and use the windows drivers for the card: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

intalled ndisgtk/ndiswrapper the instructions are for 6.x I'm using 8.04, should I follow them anyways?  THANK YOU for your help :guitar:

---

### Post by MegaJim on 2008-09-15
Follow section 3.4 of the guide I posted, you are welcome.

---

### Post by Latino Boy on 2008-09-15
Awesome, one more question...what are the appropriate drivers and where can I get them?

---

### Post by MegaJim on 2008-09-15
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

scroll down to item 7 and you will find your card, along with some instructions

---

### Post by Latino Boy on 2008-09-15
> *Toshiba Satellite 4015CDT, Debian Sarge, kernel 2.6.8 / ndiswrapper 0.10. The Belkin driver did not work for me, it loaded but failed to do anything useful whatsoever. An ndiswrapper -l using the realtek driver reported the hardware not present. By copying the Bel6020.inf file from the Belkin driver and the rtl8180.sys file from the realtek driver into the same directory, and replacing every instance of the string “Bel6020.sys” with “rtl8180.sys” I was able to get the card work satisfactorily. ‘(Best Solution)’

Great I'm downloading the exe right now...but I'll keep looking for the zip to try this...

---

### Post by Latino Boy on 2008-09-15
Played with the ABOVE IT WORKED PERFECTLY.  Mix the ini and sys files to make the thing work. THANK YOU SO MUCH.  Anyone feel free to PM for the ini file. :)

---

