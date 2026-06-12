---
title: "Hardware"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by anuraggautam on 2008-06-13
Dear Ubuntu Seekers,

I am using Ubuntu Hardy Edition in Laptop **Compaq 6720s** which has 1 GB RAM 160 GB Hard Disk configuration.

I am getting some problems while using :

1) My Sound is not coming properly.It is coming After playing with Master volume Control and also the sound is very low.It is coming sometimes and sometimes it's not.

However my speakers are not able to speak while when using Headphones may giving some sounds after playing it with Masters Volume.

Can any one tell me what the exact problem is ?

2) I am also getting regular problem during shut-down process.My computer is not able to shut-down properly after clicking the shutdown.It seems stuck with some process while shut down.So in that case i have to shut it down Forcely.While i dunt have any problem in starting it's working fine.

3) However i want to tell you that i have Brand New Laptop Just 10 days Old.


Now tell me why i am gettign such problems due to my Bad luck or Hardware problem or Software problem ? and do tell me the Solutions :)

With Regards

---

### Post by argail1980 on 2008-06-13
I have an idea. post the output of 

```
lspci
``` please.

---

### Post by anuraggautam on 2008-06-13
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

---

### Post by _sphinx_ on 2008-06-13
OK I dont' know the solution of the problem but never do cold shutdown use the following that I read somewhere in this forum:
> 
Hold alt+<print screen button>, Whilst press in order and with some time lag: REISUB


---

### Post by anuraggautam on 2008-06-13
I didn't get you should i send you screenshots or any thing else ?

Can you be please more specific ...

Regards

---

### Post by argail1980 on 2008-06-13
do also 

```
aplay -l
```..

forgot that.


and have a look at

[http://ubuntuforums.org/showthread.php?t=823552]("http://ubuntuforums.org/showthread.php?t=823552")

---

### Post by argail1980 on 2008-06-13
btw, the solution for the "not shutting down problem" could be a stuck kdm or gdm.

go to conspole by pressing Ctrl+Alt+F1

and do ```
shutdown -h now
```

---

### Post by anuraggautam on 2008-06-13
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by argail1980 on 2008-06-13
ok.

insert the line

```
options snd-hda-intel model=basic
``` 

at the bottom of the file

```
/etc/modprobe.d/alsa-base
```

and reboot (or restart the sound system, though I don't know what exactly to restart)

if that doesn't work, try

```
options snd-hda-intel model=3stack
``` 

These are options for soundcards from Intel, like yours.

---

### Post by anuraggautam on 2008-06-13
where shud i insert these commands ......in Terminal or after clicking ALT+CTRL+F1    ?????

Regards

---

### Post by argail1980 on 2008-06-13
ok... I've gone too fast

open an editor by hitting Alt+F2 and entering

```
gksu gedit /etc/modprobe.d/alsa-base
```

then look at the end of the file for some line like
```
options snd-hda-intel model=basic
```

if it's not there, create it.

then restart the sound system (or as I would do to be sure just reboot)

---

### Post by sxb182 on 2008-06-14
> **anuraggautam said:**
> where shud i insert these commands ......in Terminal or after clicking ALT+CTRL+F1    ?????

Regards

I am new too. I just joined this forum because I am having problems with bcm4312. Leave tha aside, "shutdown -h now" like this commands are supposed to type in terminal. I believe superuser in Ubuntu is disabled by default. So if "shutdown -h now" gives you "need to be in root folder" message , try "sudo shutdwon -h now".
Did you check Ubuntu CD for any errors before you install it?

---

