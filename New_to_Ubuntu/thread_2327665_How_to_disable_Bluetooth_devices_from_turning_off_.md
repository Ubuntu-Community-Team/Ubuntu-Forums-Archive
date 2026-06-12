---
title: "How to disable Bluetooth devices from turning off due to inactivity in 14.04"
date: 2016-06-13
forum: New to Ubuntu
---

### Post by Grace_Penniman on 2016-06-13
I am fairly new to Ubuntu. I know in Windows OS you can disable  Bluetooth power management, which disables the devices from turning  off/going to sleep. I would like to disable that for Ubuntu 14.04  because it constantly turns off my keyboard and mouse in 1-2minutes from  inactivity.

---

### Post by jeremy31 on 2016-06-13
There is a file, /etc/bluetooth/input.conf that contains
```
# Configuration file for the input service

# This section contains options which are not specific to any
# particular interface
[General]

# Set idle timeout (in minutes) before the connection will
# be disconnect (defaults to 0 for no timeout)
#IdleTimeout=30
```

It says IdleTimeout defaults to 0 for no timeout but it could be wrong
We can change it with ```
sudo sed -i 's/#IdleTimeout=30/IdleTimeout=0/' /etc/bluetooth/input.conf
```

Reboot and see if the disconnects stop

---

### Post by Geoffrey_Arndt on 2016-06-13
Bluetooth connections just do not have the same reliability of performance that radio/wireless or cabled connections have.   In many areas of DoD stations, joint services commands (Stratcom), Bluetooth connections are not allowed.   So, the lesson here is for keyboard, mouse and other mission critical peripherals . . make a different choice in the future.   For entertainment and playtime . . . bluetooth is ok.

---

