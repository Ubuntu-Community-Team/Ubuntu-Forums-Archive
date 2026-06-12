---
title: "How to permanently enable wireless (card) ?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by krtica on 2008-11-03
I have problem with wireless on laptop. Ubuntu 8.10.

When I left-click on Network icon, I have grey letters:
**Wireless Network - wireless is disabled**.
And when I right-click on same icon, I have greyed:
**[ ] Enable _W_ireless**
so I can't click on it.

When I boot to Windows everything is ok.

I enabled wireless ON on system startup in BIOS.

Button for enabling/disabling wireless is not recognized, so I can't use it.

Wireless LED is turned on.

After I issued **lshw** command I get this:

 > *-network:1
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 6
                bus info: pci@0000:02:06.0
                logical name: eth1
                version: 04
                serial: 00:04:23:97:57:a3
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated

and

>   *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:08:0e:88:29:b3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

After **iwconfig**:

> eth1      unassociated  ESSID: off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power: off   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

after **cat rf_kill**
i get **2**

I'm newbie on Ubuntu, so I don't know what to do next. :confused:

How can I manually enable wireless card in terminal?
Is it possible?
If it is, is there any way to permanently enable wireless card?

---

### Post by Tom--d on 2008-11-03
Load the driver at boot:
```
gksu gedit /etc/rc.local
```
put this BEFORE exit 0
```
modprobe ipw2100
```

---

### Post by krtica on 2008-11-03
Thank you for a quick answer.
Unfortunately, everything is still the same... :(

---

### Post by krtica on 2008-11-03
Any idea, please? What is wrong? :(

---

### Post by mister_pink on 2008-11-03
I would also be interested to know what the answer is here. My friend has a similar issue and its been introduced at some point during the upgrade cycle to intrepid. I'll try to get some debugging output to put here.

---

### Post by krtica on 2008-11-03
Ok... I have installed Ndiswrapper and Windows drivers for 2100 wireless card.
"Enable wireless" is active (not gray anymore) - BUT! - my wireless LED is OFF now. :(
I can't turn it on by button, as I said before.

When I use **iwconfig** command, I get:
> wlan0     IEEE 802.11b  ESSID: off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          RTS thr=1600 B   Fragment thr=2344 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Is there any way to permanently enable wireless while using Ndiswraper, because I can't see any "Nickname" anymore?...

---

### Post by krtica on 2008-11-03
Saga continues... :)

I removed ndiswrapper, and after reboot "Enable Wireless" is active! :confused: Not gray anymore...

Wireless LED is ON again, but I STILL have ***-network DISABLED**...

Should I kill myself or rf? :D
(*Sorry on bad "humor".. I'm getting tired and hopeless...*)

PS: Nothing really happening when I enabling/disabling wireles...

---

### Post by lalada on 2008-11-03
Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories > Networking & Wireless forum is full of post about this problem :( and I didnt find any solution for this issue. So I just installed [Wicd]("http://wicd.sourceforge.net") and wireless works now...

---

### Post by krtica on 2008-11-04
I tried with Wicd, but it's same... With ubuntu drivers LED is ON but there is no Wireless network, and with ndiswrapper LED is OFF, and I can't activate it by button.
I tried also **sudo ifconfig [eth1/wlan0] up** comand, but it didn't help me...

---

### Post by tliotis on 2008-11-04
hello i am having acer aspire 5021 wlmi with broadcom wifi and i had the same problems.
the solution for me is this :


terminal :
sudo su
echo "1" >/proc/acpi/acer/wireless

this is for my laptop ! if anyone can help you with this will be helpfull!

good luck and if you find the way tell us the solution!
thanks for your time mate!!!
keep in touch

---

### Post by krtica on 2008-11-04
I have this:

> root@ubuntu-laptop-1:/proc/acpi# dir
ac_adapter
dsdt
fadt
power_resource
thermal_zone
battery
embedded_controller
fan
processor
video
button
event
info
sleep
wakeup

root@ubuntu-laptop-1:/proc/acpi/button# dir
lid
power
sleep

I'm a noob and I don't know much about linux, so I don't know where to search for something similar.
:confused:
Is there any way to add wireless into /proc/acpi/button ? :D

---

### Post by Krithiga on 2010-02-11
Hey.. Even i have the same problem.. wireless interface is disabled in my ubuntu... its workin well with the windows vista... so i wanna knw if ter s any way to manually enable the wireless interface.. thanks...

---

### Post by Jimcamera on 2011-02-24
Just as aside/update to this thread.  I too had the problem of my wireless being disabled.  It has happened to me a number of times, randomly, and I was getting rather cross about it, as normally it works fine.  Then, as I logged out and booted up windows on my dual-boot machine (unfortunately I'm still tied to the slothful windows for some things..) I noticed that I hadn't (on last shutdown) fully logged out of windows - windows was just hibernating.
I did a full shut-down of windows and rebooted Ubuntu and lo and behold, all was good - my wireless was indeed enabled.

Wahey!

I hope this helps others who may be in a similar predicament and not willing to go into all that scary codey stuff.

All the best

Jim

---

