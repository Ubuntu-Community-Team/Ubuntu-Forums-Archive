---
title: "[SOLVED] Sound after kernel update"
date: 2008-06-14
forum: Philippine Team
---

### Post by king leoric on 2008-06-14
Hello po mga kapwa ubunteros at ubunteras.. Help lang...Kasi nag fresh install me ng hardy. Did costumized and everything the way I like it. 
Did update then noticed na nabago ang kernel ko from 2.6.24-16 to 2.6.24-18.
But after I rebooted, nawala ang sound ko. Did try na hanap any specific
pero no luck. Or maybe di ko lang mahanap talaga. For now, nag reinstall na ako pero di ko muna update sa bagong kernel kasi wait ko pa ang opinions niyo...

Thanks po ng marami:)

---

### Post by loell on 2008-06-14
can you paste your ```
lspci
```

---

### Post by king leoric on 2008-06-14
> **loell said:**
> can you paste your ```
lspci
```

eto po:

jayne@acer-aspire:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
05:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
05:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

---

### Post by Fingel on 2008-06-14
> **king leoric said:**
> Hello po mga kapwa ubunteros at ubunteras.. Help lang...Kasi nag fresh install me ng hardy. Did costumized and everything the way I like it.
Man... What language is that?

---

### Post by rjmdomingo2003 on 2008-06-14
Try installing linux-386 using synaptic, then, reboot.

---

### Post by loell on 2008-06-14
adding to what rjm suggested, you can also select **2.6.24-16** in your grub to have sound again, this is a kernel update issue and quite a number of users are affected with this, this won't be the last kernel update, if ever there's a new kernel update  just test it if can have audio, if it can't, just boot to the kernel version where it had audio.

---

### Post by king leoric on 2008-06-14
> **loell said:**
> adding to what rjm suggested, you can also select **2.6.24-16** in your grub to have sound again, this is a kernel update issue and quite a number of users are affected with this, this won't be the last kernel update, if ever there's a new kernel update  just test it if can have audio, if it can't, just boot to the kernel version where it had audio.

Already downloading linux-386. Thanks for that rjm but haven't rebooted yet :-) wish me luck:)

Anyway, sir loell, actually I tried selecting the 2.6.24-16, but same as the other, no sound :confused: So I actually reintalled hardy again but this time, I did'nt select the 2.6.24-18 update showing in the update manager. For now, just finalizing everything before I have installed linux-386. I'll give you guys a feedback after I reboot :KS

---

### Post by king leoric on 2008-06-14
> **rjmdomingo2003 said:**
> Try installing linux-386 using synaptic, then, reboot.

Thanks rjm, working fine now....Have rebooted oks naman siya....Just a question though, sa update manager eh showing pa rin yung following:

linux-generic
linux-headers-2.6.24-18
linux-headers-generic
linux-image-generic
linux-restricted-modules-2.6.24-18-generic
linux-restricted-modules-generic
linux-ubuntu-modules-2.6.24-18-generic

ask ko lang kasi eto yung update dati na nawalan ng sound. Is it safe na install ko tong updates na ito? or should I leave it.....How about yung
2.6.24-16 na kernel, is it safe to removed from the system via synaptic??:confused:

---

### Post by rjmdomingo2003 on 2008-06-14
> **king leoric said:**
> Thanks rjm, working fine now....Have rebooted oks naman siya....Just a question though, sa update manager eh showing pa rin yung following:

linux-generic
linux-headers-2.6.24-18
linux-headers-generic
linux-image-generic
linux-restricted-modules-2.6.24-18-generic
linux-restricted-modules-generic
linux-ubuntu-modules-2.6.24-18-generic

ask ko lang kasi eto yung update dati na nawalan ng sound. Is it safe na install ko tong updates na ito? or should I leave it.....How about yung
2.6.24-16 na kernel, is it safe to removed from the system via synaptic??:confused:
OK lang, so far.
Iun-comment ko yung mga 'modules' na 'to sa /boot/grub/menu.lst para di masyado marami ang 'pagpipilian.

---

### Post by king leoric on 2008-06-14
Mga tropapis, follow up ko lang...Oks naman na eh...Bale update ko na rin yung 2.6.24-18-generic na kernel cause it keeps on showing sa update manager. But the default is the one sir rjm suggested, the linux-386. I tried to uninstall yung 2.6.24-16 generic using synaptic and crossed fingers, it doesn't affect my system. Have tried sa 2.6.24-18 kernel, oks na ang sound. Pero so far is default ko ang linux-386. Di ko muna change
yung menu.lst ko para may option ako in times na magloko tong 2.6.24-18..

Pero maraming tenk you po sa inyong lahat :)

---

### Post by mghambunan on 2008-06-29
I have encountered this problem before and found a solution from ubuntu documentation. The specific way that solves my problem was to reinstall the ALSA drivers from a *fresh* kernel. Follow this link for solutions regarding audio problems:

[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel")

Hope this helps...

---

### Post by king leoric on 2008-06-29
> **mghambunan said:**
> I have encountered this problem before and found a solution from ubuntu documentation. The specific way that solves my problem was to reinstall the ALSA drivers from a *fresh* kernel. Follow this link for solutions regarding audio problems:

[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel")

Hope this helps...

Many thanks! But actually so sorry I didnt marked SOLVED. Actually the advice of sir RJM works with the installing of linux-386. But as of now, after the new update kernel 2.6.24.19, I didnt encounter any problem as of the moment. But I removed the linux-386 instead I installed the linux-686 :) but thanks bro

---

### Post by rjmdomingo2003 on 2008-06-29
> **king leoric said:**
> Many thanks! But actually so sorry I didnt marked SOLVED. Actually the advice of sir RJM works with the installing of linux-386. But as of now, after the new update kernel 2.6.24.19, I didnt encounter any problem as of the moment. But I removed the linux-386 instead I installed the linux-686 :) but thanks bro
No probs.. just spreading the love.

---

