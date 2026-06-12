---
title: "USB do not work"
date: 2017-09-08
forum: New to Ubuntu
---

### Post by 22chrishodge on 2017-09-08
I was trying to get a Ipod to mount to the Unbuntu and did a update at the same time so I don't know which made things not work.

Now any jump drive I try in my laptop says "the location can not be displayed you do not have permission to view the content" I have tried formatting the drives and chmod to 777. 

It shows that the drives get mounted I just cant access them

cheers

---

### Post by Mark_in_Hollywood on 2017-09-09
22chrishodge

You have not given much information and I'm concerned that my reply is inadequate, but here goes:

Can you open a Terminal (CTRL ALT T keys simultaneously) and type in

```
lsusb
```

does the device you want to work with show up in that list? If you see the Apple device, please read here:

[How do I connect an Apple iPod to an Ubuntu Linux PC?]("http://www.techrepublic.com/blog/linux-and-open-source/how-do-i-connect-an-apple-ipod-to-an-ubuntu-linux-pc/")

and

[here]("https://ubuntuforums.org/archive/index.php/t-922749.html")

I would admonish you that the above article is from 2008 and tech does change, so be cautious.

---

### Post by 22chrishodge on 2017-09-11
ran lsusb

```
Bus 001 Device 004: ID 0c45:c35a Microdia Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID 0cf3:3004 Atheros Communications, Inc. AR3012 Bluetooth 4.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

there are 2 usb's plugged. One does not seem to show up and the other says I do not have permissions to access it.

---

### Post by Mark_in_Hollywood on 2017-09-12
By "2 usb's plugged." -- Tell me what devices are plugged in.

Also, unplug those 2 "usb's", reboot the OS, attach (plug-in) the iPOD. Run lsusb again, and if the iPOD show up, we will go from there. Post the terminal output with the iPOD attached.

Here is a list of USB devices with their associated device IDs. 

[http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)

it has a lot of Apple devices listed. When you run lsusb, what we are looking for is one of those IDs. If it's not listed, try a different cable, and try a different computer with the same cable. We are troubleshooting and do one step at a time to eliminate what is working from what is not.

---

