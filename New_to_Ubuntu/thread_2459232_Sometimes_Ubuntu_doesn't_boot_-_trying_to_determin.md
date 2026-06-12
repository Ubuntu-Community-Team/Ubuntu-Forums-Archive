---
title: "Sometimes Ubuntu doesn't boot - trying to determine root cause"
date: 2021-03-14
forum: New to Ubuntu
---

### Post by sezza on 2021-03-14
Hi all

I run Ubuntu 20.04 off a portable SSD. Occasionally Ubuntu will not boot, I just get a black screen and I'm forced to restart until it boots correctly.

Running journalctl -p 3 -xb I get the following 

> 

Mar 14 12:14:08 My-Machine kernel: scsi 3:0:0:1: Wrong diagnostic page; asked for 1 got 8
Mar 14 12:14:08 My-Machine kernel: scsi 3:0:0:1: Failed to get diagnostic page 0x1
Mar 14 12:14:08 My-Machine kernel: scsi 3:0:0:1: Failed to bind enclosure -19
Mar 14 12:14:10 My-Machine kernel: pcieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)
Mar 14 12:14:10 My-Machine kernel: pcieport 0000:00:1c.5: AER:   device [8086:a115] error status/mask=00003000/00002000
Mar 14 12:14:10 My-Machine kernel: pcieport 0000:00:1c.5: AER:    [12] Timeout               
Mar 14 12:32:30 My-Machine kernel gdm-password][1764]: gkr-pam: unable to locate daemon control file



Would any of these messages constitute such a problem occuring? is there any other ways I can investigate where the issue may be coming from? Potentially Nvidia drivers? I just don't know where to start..

Obviously this doesn't stop me using Ubuntu, I can just reboot again and it works, but it would be nice to find out why that issue is occuring

---

### Post by canadianbill007 on 2021-03-16
Seen this error before from a drive not being removed properly. With it being the system you are booting Ubuntu from, then likely some other issue with the drive.

I'd recommend running [FONT=courier new]gnome-disks [FONT=arial]and checking filesystem for the portable SSD. See if that helps.[/FONT][/FONT]

---

### Post by rsteinmetz70112 on 2021-03-17
Random errors usually point to a hardware issue.
Checking the hard drive is a good place to start.
Also check the memory.

Once the computer boots is it stable? What is the longest time it has run without rebooting?

---

### Post by sezza on 2021-03-19
Yes it is stable.

What I am trying to figure out though is why sometimes when I boot, it just gives me a black screen with a flashing _ line and wont boot in.

When this happens I'm forced to power off/power on, could this be why I have that error?

---

### Post by sezza on 2021-03-19
> **rsteinmetz70112 said:**
> Random errors usually point to a hardware issue.
Checking the hard drive is a good place to start.
Also check the memory.

Once the computer boots is it stable? What is the longest time it has run without rebooting?


Sorry should have replied directly to you, yes it is stable. How do I check the longest time without rebooting? the uptime command doesn't seem to have this feature.


What I am trying to figure out though is why sometimes when I boot, it  just gives me a black screen with a flashing _ line and wont boot in.

When this happens I'm forced to power off/power on, could this be why I have that error?

---

### Post by sezza on 2021-03-19
> **canadianbill007 said:**
> Seen this error before from a drive not being removed properly. With it being the system you are booting Ubuntu from, then likely some other issue with the drive.

I'd recommend running [FONT=courier new]gnome-disks [FONT=arial]and checking filesystem for the portable SSD. See if that helps.[/FONT][/FONT]

Says Disk is OK

---

### Post by tea for one on 2021-03-20
> **sezza said:**
> Yes it is stable.

What I am trying to figure out though is why sometimes when I boot, it just gives me a black screen with a flashing _ line and wont boot in.

When this happens I'm forced to power off/power on, could this be why I have that error?

Instead of using power off/on when your boot process fails, it would be better to use REISUB or REISUO.

However, Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing this file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by sezza on 2021-03-20
> **tea for one said:**
> Instead of using power off/on when your boot process fails, it would be better to use REISUB or REISUO.

However, Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing this file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

Thank you

I will install this.

So again today this happened twice to me. ACtually its just a black screen there is no blinking _ line.

For the life of me I cant figure out why its happening.

I have done memtest, gnome disks check, all come up okay. Its just those error messages that I posted initially that keep appearing according to journalctl.

I'll keep asking around as well. Ty

---

### Post by tea for one on 2021-03-21
> **sezza said:**
> I run Ubuntu 20.04 off a portable SSD. Occasionally Ubuntu will not boot, I just get a black screen and I'm forced to restart until it boots correctly.

Just offering mundane suggestions:-

Can you replace your internal device with this portable SSD (therefore using different connectors)?
Alternatively, change the external cables or even the caddy?

---

