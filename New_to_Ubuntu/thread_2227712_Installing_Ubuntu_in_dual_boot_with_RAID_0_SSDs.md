---
title: "Installing Ubuntu in dual boot with RAID 0 SSDs"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by I_See_Stars on 2014-06-03
Hello, I have not used Ubuntu for a while (I think the last version I used was in the 9.xx). Back then Ubuntu had some issues so I stopped using it.

Right now I am wanting to dualboot Ubuntu with Windows 8.1 on RAID 0 840 evos, the UI for W8 is so cancer I cannot take it anymore.

However when I go into installing Ubuntu, it doesn't give me the option for dualbooting like it previously did, it just wants a clean install. How would I go about this?

---

### Post by Vladlenin5000 on 2014-06-03
Hi, welcome.

Dual-booting isn't as easy as it used to be due to many factors, the most important one being the UEFI your Windows 8.1 requires instead of the "legacy" BIOS. Also to keep in mind is Windows 8.1, by default, hibernates. This prevents the Ubuntu installer from recognizing the other OS as already installed -> the partition it would need to read for that to work is hibernated.

Here's the first piece of the many you should read in order to gain the basic knowledge for the task you'll perform: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

