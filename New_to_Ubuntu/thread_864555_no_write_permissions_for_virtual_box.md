---
title: "no write permissions for virtual box"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-19
im getting the current error message when i try to start my vm to install windows


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

i really need help

im certainly not abandoning ubuntu, i just need it for my mp3 player

---

### Post by flytripper on 2008-07-19
you need to add your username to vboxusers group in system>admin>users and groups then relog and all should be well. may i inquire as to what mp3 player make it is? If it is a creative, i also have one and thought i would need windows still but found gnomad2 which in turn provided basic support to use banshee, which incidentally is a nice library and sync software for music

```
sudo apt-get install gnomad2
```

---

### Post by PatrickMoore on 2008-07-19
> **flytripper said:**
> you need to add your username to vboxusers group in system>admin>users and groups then relog and all should be well. may i inquire as to what mp3 player make it is? If it is a creative, i also have one and thought i would need windows still but found gnomad2 which in turn provided basic support to use banshee, which incidentally is a nice library and sync software for music

```
sudo apt-get install gnomad2
```

alas a zune i acquired prior to switching. i got the new one thanks to its product replacement plan via best buy but could not swap it for a sansa

---

