---
title: "Ubuntu 12.04 shutdown and suspend fails"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by A4Kke6k on 2014-03-28
Hello everybody,

yesterday I installed a fresh ubuntu 12.04 LTS 64bit on my desktop pc.

PC:
Chipset: Intel DP35DP
CPU: Intel Core 2 Duo E6750 
RAM: DDR2-800 4GB
HD: WD Blue 1TB
Network: Intel 82566DC-2 Gigabit Network Connection

I used the following partition scheme:

root:   186GB
swap:     9GB
home: 736GB

Bios setting ACPI: S3

The problem now is, that the computer doesnt shut down properly. I go via the button in the red upper corner of the desktop und hit shut down --> shutdown.
I hear the hard disk turning of, but the CPU fan, power supply and screen remain active. The last line printed on screen befor it hangs is > [2273.288087] reboot: Power down

```
sudo shutdown -P now
``` doesn't work either.

If i want the pc to suspend (power button upper right at desktop) it turns off, but doesnt resume. If i resume I get a blank screen with the withe cursor in the upper left corner in the screen. Nothing happens.

Restart works.

I searched the internet and find this hint:

[http://mylinuxexplore.blogspot.de/2011/11/solved-ubuntu-doesnt-shutdown-properly.html](http://mylinuxexplore.blogspot.de/2011/11/solved-ubuntu-doesnt-shutdown-properly.html)

but it didn't work for me.

I read the suspend log (/var/log/pm-suspend.log) and found out, that the network controller might not be disabled... I attached it.
>    /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed
I tried to disable the network adapter before suspending and afterwards reanabling it, sadly no effect.

```
sudo modprobe -r e1000e
sudo modprobe e1000w
```

I also tried to install a new driver from Intel, there should be one available for my network chip, i found this manual
[http://askubuntu.com/questions/411545/ethernet-driver-intel-82579lm-e1000e-update](http://askubuntu.com/questions/411545/ethernet-driver-intel-82579lm-e1000e-update)
but I failed  

Bios setting ACPI: S1

Everything works, Power down, suspend, restart!

---

### Post by frostschutz on 2014-05-26
Not quite clear from your post, did you ever solve this issue?

I have the same board (Intel DP35DP) and the same issue - for years. It does not shut down most of the time, and the kernel prints "power down" as last message. HDDs turn off, everything else keeps running. Whatever the cause, it's something specific to Linux; Windows never had a problem getting the machine to shut down properly. In the end I just turned it off manually instead, no real harm done. Except lately it sometimes refuses to turn back on... it's an old machine by now (>5 years and ran every day), might have to replace it with something else after all...

---

