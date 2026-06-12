---
title: "network-manager wireless problems"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by RikoW on 2011-09-16
Dear all,

I upgraded today from 11.04 to 11.10-beta. Things appear to be fine as long as I'm connected to a wired network, however wireless network don't work. I see them when I click on the nm-applet, but cannot connect.

I tried to recreate the network settings, but nm does not allow me to edit any settings. It seems to have forgotten all previously defined networks as well. When I try to add a wireless network, all fields are grayed out and cannot be changed.

Any ideas about that?

Thanks, Riko

---

### Post by DogMatix on 2011-09-16
Have you tried

```
sudo rfkill list all
```

to see if your wireless is being blocked.

---

### Post by RikoW on 2011-09-16
yes, I did:

```
> rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

I wonder, however, why it says Dell Wifi, when it is Intel:

```
0c:00.0 Network controller: Intel Corporation WiFi Link 5100
```

Cheers, Riko

---

### Post by RikoW on 2011-09-16
OK, seems to be NM. Just downgrade to the Natty version and here I'm being online with wireless again.

However, that cannot be a solution.

Cheers,

          Riko

Edit: That's why I don't mark the thread as solved.

---

### Post by erikschmitz on 2011-09-16
How did you downgrade it? I'll give it a shot to see if it fixes my issue with intel centrino 1000 not connecting.

---

### Post by garvinrick4 on 2011-09-16
In google searcing I have found that no one has a problem with this in 11.04, it is an 11.10 thing that is going on with the dmesg error. Have found no fixes in 11.10 for this.
[  162.724064] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues

---

### Post by RikoW on 2011-09-16
I downgraded like this:

1) goto /etc/apt and replace the sources.list with the one from Natty (attached); make a copy of the Oneiric one first to restore later

2) in the terminal do sudo apt-get update
to load the new (natty) repositories

3) start synaptics and look for all installed packages with 'network-manager' in the name; each one of them force to be the Natty version via Package -> Force Version

4) once you applied these changes, you need to restart (may logout and back in is enough); I had to start nm-applet from the terminal at least this first time

5) replace the source.list again with the Oneiric one; sudo apt-get update

6) start synaptic and 'Package -> Lock version' on all the packages under 3) so not to replace them with the next update


Hope that helps. Good luck!

           Riko

---

### Post by RikoW on 2011-09-16
sorry! and here is the Natty sources.list.

---

### Post by garvinrick4 on 2011-09-16
Thanks for helping us out RikoW did you find any bug reports by chance?
Did you run a dmesg before down grading package by chance and get the
same as erikschmitz? If haven't found a bug report will be a good one to report
I have found thru googling a bit of traffic on this same 11.10 problem. Have a nice day.

---

### Post by RikoW on 2011-09-16
No, I haven't checked for any bug report yet. "Unfortunately", now I will not be able to provide any detailed logs anymore except from memory. So I guess my input will not be very helpful anymore ... :(

I did a casual check with dmesg and didn't notice any of the 'fail to flush' messages which doesn't they were not there. Sorry.

Certainly now, there are none:

```
> dmesg | grep iwlagn
[    9.660363] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    9.660366] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    9.660473] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.660502] iwlagn 0000:0c:00.0: setting latency timer to 64
[    9.660555] iwlagn 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    9.682358] iwlagn 0000:0c:00.0: device EEPROM VER=0x11f, CALIB=0x4
[    9.682360] iwlagn 0000:0c:00.0: Device SKU: 0Xb
[    9.682385] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.682505] iwlagn 0000:0c:00.0: irq 45 for MSI/MSI-X
[   10.257654] iwlagn 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[  100.020849] iwlagn 0000:0c:00.0: iwlagn_tx_agg_start on ra = 5c:4c:a9:95:12:08 tid = 0

```

I call it a day for tonight, but will check tomorrow again how these two threads developed.

Good night from Germany,

                   Riko

---

### Post by garvinrick4 on 2011-09-16
Thanks Riko.

---

### Post by Rocksinboxes on 2011-09-16
I was having similar problems with my wireless. Nm-Applet would work fine on the livecd then the wireless network would not be selectable once I had done a fresh install. What i did was install Wicd purge networkmanager, reboot, than reinstall networkmanager. The problem seemed to go away after that.

---

### Post by RikoW on 2011-09-17
There seem to be 2 bug report, which might be related:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/852251]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/852251")

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/852159]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/852159")

Cheers,
        Riko

---

### Post by sonicb00m on 2011-09-17
Did a reinstall with daily build today and have this problem. No password prompt is requested for the wireless key.

I tried WICD but it won't connect to my network at all.

---

### Post by garvinrick4 on 2011-09-17
Was confirmed RikoW.

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/852159]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/852159")

---

### Post by garvinrick4 on 2011-09-17
@SonicbOOm
> Did a reinstall with daily build today and have this problem. No password prompt is requested for the wireless key.
What kind of Network card and driver?

---

### Post by erikschmitz on 2011-09-17
I tried downgrading to the natty network-manager. I was able to downgrade easily enough, ran nm-applet from the terminal like you suggested, but I still get the flush errors in dmesg. Centrino 1000 bgn.

---

### Post by drawkcab on 2011-09-18
Fwiw I had a similar problem with lubuntu beta 11.10 on my netbook w/Atheros.

---

### Post by RikoW on 2011-09-21
The problem was fixed for me after the last round of updates I installed today. I was encouraged to do so by a reply to the bug report:

[https://bugs.launchpad.net/bugs/852159]("https://bugs.launchpad.net/bugs/852159")

Cheers,

             Riko

---

### Post by garvinrick4 on 2011-09-21
That is good news for network-manager and those with inability to connect with wireless.
It would have driven me nuts
I hope it cured the "iwlagn" problem as well there is going to be a lot of new users to
oneiric in a short time. Would not be pleasent to see those with a intel driver posting 
a thread and not be able to put Solved next to it. Intel never did fix the "N" problem
in that "iwlagn" driver, Ok for guys with "G" routers never new about problem at all.
3.0 kernel fixed that. We will see. Happy you are up and going RikoW and thanks for Posting. See ya around these Forums.

---

