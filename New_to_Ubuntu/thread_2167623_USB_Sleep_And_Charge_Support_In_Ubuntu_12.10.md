---
title: "USB Sleep And Charge Support In Ubuntu 12.10"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by Cyb0rgz on 2013-08-14
Hi all,

I have a plan to Dual Boot Ubuntu 12.10 with my Samsung Series 5 (NP550PC-S03IN) Laptop With Pre-installed Windows 8 (x64 - Intel Core i7)

As Default, there is a support for Sleep and Charge feature in one of the USB 3.0 Port. Following Questions preventing me in installing Ubuntu in My Laptop

**> Does Sleep and Charge would work fine if i install ubuntu 12.10 alongside windows 8? i.e., Even when my laptop is shutdown does my mobile can be charged as i did earlier after installing Ubuntu 12.10**

Search many threads and forums, there is no clear solutions or technical answer behind this. Would look to get answers whether this is an OS Dependent feature or not.

Awaiting for your support Guys :)

Thanks,
Cyb0rgz.

---

### Post by lukeiamyourfather on 2013-08-14
That feature is likely controlled by the firmware/BIOS/UEFI on the laptop and doesn't have anything to do with the installed operating system. At least that's the case with my ThinkPad which has a similar feature.

---

### Post by Cyb0rgz on 2013-08-17
So, this means USB sleep and charge would work irrespective of the OS. Am i right?

---

### Post by tgalati4 on 2013-08-17
You can use *acpitool* to leave parts of the bus on or off during sleep.  Search the forums for *acpitool* for ways to use it.  Unless someone has your exact laptop and has tested it, you might be waiting a while for a definitive answer.  I have used USB2 ports on a desktop computer (custom Intel motherboard build) and I am able to select which USB port I want to leave powered during sleep to charge an iPod or phone.

Check your BIOS for a switch.  It might be labeled:  "Allow USB devices to wake from sleep".  This is because it requires power to a USB mouse port or keyboard port to allow those devices to wake up the computer instead of the power button.

---

