---
title: "Failure to boot ubuntu&#8207;"
date: 2020-08-12
forum: New to Ubuntu
---

### Post by Jordan159 on 2020-08-12
Hi, 

this morning I turned on my laptop and suddenly I got a bootloop saying "Unexpected return from initial read: Volume Corrupt". My laptop is running both windows 10 and ubuntu 18.04 LTS with dual boot.
I inserted a live USB, went to "try ubuntu" and went into boot repair through the terminal. After restarting, the bootloop continues, but with different text (invalid image, Failed to load header: Unsupported, Failure to load image: unsupported, start_image() returned Unsupported).
I am able to use F12 to enter windows successfully. 

This is the pastebin: [http://paste.ubuntu.com/p/wHJzsPQ6Ft/](http://paste.ubuntu.com/p/wHJzsPQ6Ft/)


Thanks alot for your help!
Jordan.

---

### Post by CelticWarrior on 2020-08-12
"volume corrupt" suggests exactly that, not any bootloader problem that could have been eventually corrected by Boot Repair. Using Boot Repair in this scenario only made things worse.

Very likely all it needed was a file system error correction (from a live session).

And then this:
```
[COLOR=#000000]Windows is hibernated, refused to mount. [/COLOR][COLOR=#000000]The disk contains an unclean file system [/COLOR][COLOR=#666666]([/COLOR][COLOR=#666666]0[/COLOR][COLOR=#000000], [/COLOR][COLOR=#666666]0[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000].[/COLOR]
```

also means exactly what it says. In any dual-boot configuration with any Windows 8 or newer users must disable Fast Startup.

---

### Post by Jordan159 on 2020-08-16
So what should I do? Do I need to reinstall ubuntu? or can I repair it somehow?
Fast Startup was working fine with ubuntu up until this happened. Do I need to disable it?
Thanks in advance!

---

### Post by CelticWarrior on 2020-08-16
There must be a reason for this being for a long time the first Google result for "Windows fast startup": [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

So, even in a standalone Windows disabling it is recommended. In any dual-boot disabling it is a must. It locks (hibernates) NTFS partitions and sometimes even FAT32 ones including the ESP itself.

---

### Post by Jordan159 on 2020-08-16
OK, I turned off the fast startup, but the same problem persists. Can I fix this with installing the new Ubuntu 20.04.01?

---

### Post by CelticWarrior on 2020-08-16
You certainly can as long as you know what you're doing.
Don't forget to have backups before anything else.

---

### Post by Jordan159 on 2020-08-16
Ok, so after disabling fast startup on Windows, I tried boot-repair again and this time it worked, I'm now able to enter Ubuntu again, with everything unchanged!

---

### Post by CelticWarrior on 2020-08-16
:guitar:

---

