---
title: "c# driver compiling  on ubuntu"
date: 2011-05-08
forum: Programming Talk
---

### Post by eladriels on 2011-05-08
Hi,
i have a source code of device driver written in c# on Windows platform. and now i need to use this on ubuntu.I should compile it again on ubuntu but i dont know what should i do with its dll files. in Windows when i want to use this driver i copy dll's to system32 directory.  i thought i should install wine next visual studio with wine , then compile this source code with its dll's. but  i realized i cant install visual studio with wine. after that tried mono, but failed again.  so  can anyone help with this, can i compile and use this source code with wine , use this device properly and with which IDE can i compile it?

Thanks in advance.

---

### Post by ve4cib on 2011-05-08
What device is this a driver for?

Since you're not using Windows you probably shouldn't be using Windows drivers anyway since the way Linux communicates with hardware is different than Windows.  My first suggestion would be to see if there is a Linux kernel module for the device in question and use that if it's available.

---

### Post by eladriels on 2011-05-08
yes you are right, linux's communication is different.so i cant use win driver. (how can be so stupid:s) i have a rfid device and this device's linux driver is not avaible. deep down i felt this is not gonna work in linux but i want to try my chance:) anyway, thanks:)

---

### Post by cgroza on 2011-05-08
> **eladriels said:**
> yes you are right, linux's communication is different.so i cant use win driver. (how can be so stupid:s) i have a rfid device and this device's linux driver is not avaible. deep down i felt this is not gonna work in linux but i want to try my chance:) anyway, thanks:)
Try to port it in a language like C++ or C.

---

