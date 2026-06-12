---
title: "Ubuntu Install Alienware Aurora R3 Issues"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by Colico on 2012-02-18
Hello all. I'm wondering if anyone can point me in the right direction for an issue I'm having. My skill level with Linux is new/moderate and I'm totally stuck.

Long story short, I have a Alienware Aurora R3 with 8G of RAM and set up in a RAID 0 configeration. I cannot get past the setup (is it called the POST?) where when you select "Live Mode" and it probes all the devices in that terminal looking start up area it just hangs and does nothing. I have unplugged all USB devices excpet for a standard Dell USB mouse and a standard Alienware USB keyboard.

I get the following error:
```
[3.497391] usb 2-1.3.2: new highspeed USB device using ehci_hcd and address 10

...timeout 180 seconds...

worker [82] failed while handling 'devices/pci0000:00/0000:00:01.1/000:02:00.01
```

Any ideas what this might be or how to fix it? I've tried both Ubuntu 11.10 and the latest PenGuy OS and they both give the same error.

---

### Post by ikt on 2012-02-18
Is it possible to stop the factory overclock? IIRC overclocking can sometimes badly affect linux.

Does the memory test go ok?

---

### Post by Colico on 2012-02-18
Yes, the memory test goes fine. It seems to bomb-out when it is probing for USB devices. I'm not sure if I can or how to stop factory overclocking on it.

---

