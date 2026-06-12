---
title: "Dell inspiron running hot"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-05-26
My laptop originally had win 7 on it and never had a heat issue. With Ubuntu my computer gets pretty hot to the touch. Fans are on but when it gets real hot it doesn't turn the fans up.

---

### Post by benjamin.s.vaccaro on 2012-05-26
Sometimes it is important to open the case and blow out dust that can accumulate on the fan. That will definitely improve cooling, and do you keep the vents in an open area so it can circulate air? I have a Dell Inspiron E1505 and dust often accumulates on the grill.

---

### Post by TheMTtakeover on 2012-05-26
I do clean it regularly. I'm concerned though because in windows the fans would crank up when it got hot but that isnt happening in Ubuntu

---

### Post by Hadaka on 2012-05-26
Here ya go..fan and temp monitor for ubuntu 11.10 and 12.4
[http://askubuntu.com/questions/129432/is-there-a-temparature-monitor-application-for-ubuntu-11-10](http://askubuntu.com/questions/129432/is-there-a-temparature-monitor-application-for-ubuntu-11-10)

---

### Post by TheMTtakeover on 2012-05-26
thanks, but when I try to install i get this
 ```
dpkg: error processing /tmp/indicator-sensors_0.1-1* (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /tmp/indicator-sensors_0.1-1*

```

---

### Post by Hadaka on 2012-05-26
Try Psensor in ubuntu software center

---

### Post by Hadaka on 2012-05-26
Did you read the entire page in the link i sent? There is a sensor already included
in the ubuntu package. If you read towards the bottom of the page there is an
example of what the sensor/indicator looks like....and if there is a green check
mark next to it....on the left side.....you already have it. all you need to do is
enter the sudo command it gives and follow the instructions to activate it in 
dash...apps.

---

### Post by TheMTtakeover on 2012-05-27
okay when detecting sensors this is where I get stuck at.

```
Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

dylan@dylan-Inspiron-N5010:~$ service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.107" (uid=1000 pid=7505 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
dylan@dylan-Inspiron-N5010:~$ 

```

---

### Post by TheMTtakeover on 2012-05-27
I also found this but I can't seem to get it to work

[ubuntuforums.org/showthread.php?t=1015468]("http://ubuntuforums.org/showthread.php?t=1015468")

---

### Post by idoitprone on 2012-05-27
```
lspci
```

do you have sandy brige processor?

---

### Post by TheMTtakeover on 2012-05-28
[FONT=Arial][SIZE=2]It has an i3 (First Gen) which I'm fairly certain that is Nehalem. 

[/SIZE][/FONT]```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
dylan@dylan-Inspiron-N5010:~$ 

```

---

### Post by TheMTtakeover on 2012-05-29
I am getting a code on my battery light indicator. I've been told that a cell in the battery is bad and could be overheating. Perhaps the fans aren't kicking on because the heat is coming from the battery not inside the Computer?

---

### Post by DaveyG on 2012-05-29
I'm no expert, but it could quite possibly be that your laptops battery is "on the wonk" (or possibly dying)?

When using Windows, did you ever receive any errors concerning the battery?

---

### Post by TheMTtakeover on 2012-05-29
> **DaveyG said:**
> I'm no expert, but it could quite possibly be that your laptops battery is "on the wonk" (or possibly dying)?

When using Windows, did you ever receive any errors concerning the battery?

nope, but maybe the battery wasn't a problem then. I took the battery out and re-inserted it and it seems okay now. and the computer is feeling a lot cooler as of now. I did also re-install ubuntu. I went with 64 bit this time instead of 32. Not that it should matter but you never know.

---

