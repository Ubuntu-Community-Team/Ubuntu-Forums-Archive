---
title: "trying to add iBook G3 to hardware database"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by Paul Morris on 2012-11-21
I am a total newcomer to Linux, but I have successfully installed lubuntu 12.04 on an old iBook G3 PPC Mac as a dual boot lubuntu/OS X Tiger system.  Since it seems there are a lack of PPC hardware in the database I thought I would follow the instructions to add my laptop to the database.  I executed the terminal command that was suggested, but even after installing pastebinit and clipit I still did not get the expected response.  It seems I am still missing something. Below is a clip from the terminal session.  Can anyone suggest how to install whatever is missing?

  Cheers,

  Paul

paul@ubuntu:~$ hardinfo -ram devices.so | sed '/\*\*\*\*\*\*\*/,/\*\*\*\*\*\*\*/d' | pastebinit | clipit
Computer
 Summary
sh: 1: /lib/libc.so.6: not found
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-rtbqjy/pkcs11: No such file or directory
 Operating System
 Kernel Modules
 Boots
 Languages
 Filesystems
 Display
 Environment Variables
 Users
Devices
 Processor
 Memory
 PCI Devices
 USB Devices
 Printers
 Battery
sh: 0: -c requires an argument
 Sensors
 Input Devices
 Storage
 Resources
paul@ubuntu:~$

---

