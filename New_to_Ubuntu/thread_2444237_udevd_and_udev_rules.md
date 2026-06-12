---
title: "udevd and udev rules"
date: 2020-05-27
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-05-27
Hello everyone,

I've been trying to work out how udevd works, but I have questions!

As far as I can tell, when a new device is connected udevd parses all the udev rules to ascertain if there are any that relate to that device, by comparing the match key values within the .rules files with the respective attributes inside files that the kernel creates under /sys. If a matching file is found then any assignment key values within the matching .rules file are applied.

So my questions are...


[LIST=1]
[*]When an entirely new device is connected, who's attributes udevd couldn't possibly know, how does it create the device node? As surely there would not be a .rules file containing the correct match keys for a rule to be applied and a device node to be created?
[*]When a new device is connected, does udevd parse all the files under /sys as well as all the udev rules in an attempt to find a match, or does the kernel specify which /sys file relates to the new device?
[/LIST]

I appreciate some of what I have stated might be inaccurate, I'm not a pro, I just read a lot of online instructionals (always remaining aware that they are sometimes poorly worded or contain false info)

Thanks in advance!

---

### Post by CatKiller on 2020-05-27
The files in /sys, and /dev, aren't really files. They're just an abstraction of the interfaces between the kernel and user space. As I said in the other post, having things that aren't files look like files is handy.

The kernel detects the hardware, loads drivers and so on, and communicates with udev. When the kernel tells it about hardware udev can set up the /dev interfaces, and notify other userspace applications about it, and control access. It has a lot of rules for handling devices - some generic for classes of device and some specific to a particular device. So for all network devices it might notify NetworkManager when they appear or disappear, and all storage devices it might notify a file handler, but a particular device might only be allowed to be accessed by certain users. That kind of thing.

---

### Post by jcdenton1995 on 2020-05-27
Thanks, the part about generic rules makes sense as I guess a lot of devices will have certain attributes which are the same as others of the same type.

So is it the case the udevd doesn't need the /sys file to create the node as the kernel tells it directly the details of the hardware, but it just uses /sys to check if there are any rules for that device?

---

### Post by CatKiller on 2020-05-27
As I understand it, the communication between the kernel and udev is more like passing network messages than reading files.

None of /proc, /dev, or /sys actually exist. They're just interfaces to the kernel for handling processes, devices, or the system as a whole.

---

### Post by jcdenton1995 on 2020-05-27
I see, thanks.

I understand that they are 'psuedo files' that aren't actually files and aren't written into storage like an image or word document or binary etc.

Thanks for the help, I think I'm trying to understand something that's a bit above my current level of expertise, but I'll keep all this in mind.

---

