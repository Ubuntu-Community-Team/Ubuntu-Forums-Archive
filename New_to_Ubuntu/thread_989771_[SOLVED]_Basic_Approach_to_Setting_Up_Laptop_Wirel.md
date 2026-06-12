---
title: "[SOLVED] Basic Approach to Setting Up Laptop Wireless?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Andavane on 2008-11-21
I really want to get the wireless net connection working on this laptop, a Sony Vaio VGN-S3HP, and I want some advice on how to approach it.

Have seen many things on the net, and am afraid most of it is way beyond me.

Also some very basic language needed: 

I understand that I need to see which card I have.
That's "ethernet" is it? Or is that the "controller"?

I know the wireless works on it, because on Windows XP it just used to pick it up.

Any tips, or pointer to a good "How-To" for someone as dense as myself would be very much appreciated! ;)

I installed Hardy on this machine and it's working very well.

Regards

John

---

### Post by cardinals_fan on 2008-11-21
I read [here]("http://www.quadlogic.fr/fedora_linux_vaio/") that your laptop has an Intel IPW 2200 wireless card.  If you have the box from your laptop, you could verify that.

---

### Post by LowSky on 2008-11-21
first things first, try going to System> Admin > hardware drivers, it may be listed there but not activated, if it is just turn it on, and reboot, easy as that, if not we need to know what card you are using
go to applications > accessories > terminal and type 
```
lspci
```

copy and paste the info it spits out.  Thanks

---

### Post by Andavane on 2008-11-22
> **LowSky said:**
> first things first, try going to System> Admin > hardware drivers, it may be listed there but not activated, if it is just turn it on, and reboot, easy as that, if not we need to know what card you are using
go to applications > accessories > terminal and type 
```
lspci
```

copy and paste the info it spits out.  Thanks

Hi there. It says:

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processo

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) 
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03) 
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1) 
06:05.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller 
06:05.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller 
06:05.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller 
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03) 
06:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05) 



---

### Post by Andavane on 2008-11-22
> **LowSky said:**
> first things first, try going to System> Admin > hardware drivers, it may be listed there but not activated, if it is just turn it on, and reboot, easy as that, if not we need to know what card you are using
go to applications > accessories > terminal and type 
```
lspci
```

copy and paste the info it spits out.  Thanks

PS: To answer the first point: Re System>hardware drivers, only an accelerated graphics driver is listed, and it says, "not in use"

---

### Post by superprash2003 on 2008-11-22
go to the terminal and type iwconfig and post output here.

---

### Post by Andavane on 2008-11-22
> **superprash2003 said:**
> go to the terminal and type iwconfig and post output here.

Here's the output:

> 
andavane@vaayubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

andavane@vaayubuntu:~$ lo        no wireless extensions.
bash: lo: command not found
andavane@vaayubuntu:~$ 
andavane@vaayubuntu:~$ eth0      no wireless extensions.
bash: eth0: command not found
andavane@vaayubuntu:~$ 
andavane@vaayubuntu:~$ eth1      unassociated  ESSID:""  
bash: eth1: command not found
andavane@vaayubuntu:~$           Mode:Managed  Channel=0  Access Point: Not-Associated   
bash: Mode:Managed: command not found
andavane@vaayubuntu:~$           Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
bash: Bit: command not found
andavane@vaayubuntu:~$           Retry limit:7   RTS thr:off   Fragment thr:off
bash: Retry: command not found
andavane@vaayubuntu:~$           Power Management:off
bash: Power: command not found
andavane@vaayubuntu:~$           Link Quality:0  Signal level:0  Noise level:0
bash: Link: command not found
andavane@vaayubuntu:~$           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
bash: Rx: command not found
andavane@vaayubuntu:~$           Tx excessive retries:0  Invalid misc:2   Missed beacon:0
bash: Tx: command not found
andavane@vaayubuntu:~$ 




---

### Post by igknighted on 2008-11-22
There should be a little network/computer icon in your system tray (upper right).  Click it, and it should drop down a menu showing you available wireless networks.

---

### Post by ugm6hr on 2008-11-22
> **igknighted said:**
> There should be a little network/computer icon in your system tray (upper right).  Click it, and it should drop down a menu showing you available wireless networks.

Like this:
[IMG]http://projects.gnome.org/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

The icon may appear as here, or as a picture of a computer.

---

### Post by Andavane on 2008-11-22
> **ugm6hr said:**
> Like this:
[IMG]http://projects.gnome.org/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

The icon may appear as here, or as a picture of a computer.

YES!!! 

here are five networks, the strongest saying:

"Buffalo-g-001601465D5C", which is my router.

Seem to be getting somewhere ;)

BINGO!!!

We're there!

Hearty thanks to all.

Kind regards,

John

---

### Post by Andavane on 2008-11-22
PS:
I remembered:
wireless was definitely not working earlier... and had clicked that icon.
Earlier today I had typed in "wireless" into the synaptic package manager;
of the choices presented, I felt that that the package named "kismet" was worth installing, and after doing that, the tips in the replies resulted in success.

All my efforts in the earlier distro, Gutsy, had failed.

Son it appears that much work has been put into developing the wireless capabilities of Hardy.

regards

John

---

