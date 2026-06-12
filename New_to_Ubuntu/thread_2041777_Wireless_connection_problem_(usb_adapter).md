---
title: "Wireless connection problem (usb adapter)"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by VinkStevin on 2012-08-13
Hello! I'm fairly new to Ubuntu and I wasn't able to make a permanent wireless internet connection. 
I use a Belkin N300 usb adapter, my OS is Xubuntu 12.04

The first thing I tried was installing xp drivers with ndiswrapper; The usb adapter was detected but I couldn't detect any internet signal. 

After that, I successfully installed realtek's driver (RTL819xCU) and was able to connect to my wifi. There was only 1 problem left; I had to deactivate and then reactivate the driver (settings : additional drivers) to make it working. 

I have been using this technique for a week when suddenly my computer wouldn't recognize any driver. (settings : additional drivers : > no proprietary drivers are in use )

When I try to reinstall the driver; Open a terminal in the extracted folder. ```
   chmod +x install.sh
sudo ./install.sh 
```

> chmod: cannot access 'sudo': no such file or directory

I don't understand why it was working well for about a week and then suddenly the driver dissapears?

I'd be very gratefull for any help!

---

### Post by Kalanac on 2012-08-13
chmod and the sudo command need to be executed on separate lines.


Try these lines, they do the same thing, just in a slightly different syntax.  One line then the other.

```

chmod 755 install.sh
sudo sh install.sh

```

---

### Post by VinkStevin on 2012-08-14
Thanks a lot Kalanac, driver is working again!

---

