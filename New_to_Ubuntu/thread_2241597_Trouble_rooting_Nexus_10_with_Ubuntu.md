---
title: "Trouble rooting Nexus 10 with Ubuntu"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by joshua_samuel2 on 2014-08-27
I've been following zedomax's Linux method to unlock the bootloader and root the Google Nexus 10 but after I type ```
sudo ./fastboot-linux oem unlock
``` I get ```
sudo: unable to execute ./fastboot-linux: No such file or directory
```

[IMG]http://i60.tinypic.com/jtqdsh.jpg[/IMG]

---

### Post by JohnnyComeL8ly on 2014-08-27
Please enter in a terminal window and give a pic or copy its output (preferably the latter).
```
ls -l ~/Downloads/Nexus10RootNew/
```

---

### Post by sandyd on 2014-08-27
> **joshua_samuel2 said:**
> I've been following zedomax's Linux method to unlock the bootloader and root the Google Nexus 10 but after I type ```
sudo ./fastboot-linux oem unlock
``` I get ```
sudo: unable to execute ./fastboot-linux: No such file or directory
```

fastboot-linux does not have execute permissions which are needed to run executable applications.

Run
```

chmod u+x fastboot-linux
```
to grant them.

---

### Post by JohnnyComeL8ly on 2014-08-27
@sandyd

Wow! How come this didn't work for him? ```
chmod 755 *
```I think it needed to be like this, right? (worked for me)```
chmod 755 ./*
```Here's the output:```
john@OptiPlex-GX270:~/Public/testdisk-7.0-WIP$ sudo ./testdisk_static
[sudo] password for john: 
sudo: ./testdisk_static: command not found
john@OptiPlex-GX270:~/Public/testdisk-7.0-WIP$ chmod 755 ./*
chmod: changing permissions of ‘./fidentify.log’: Operation not permitted
john@OptiPlex-GX270:~/Public/testdisk-7.0-WIP$ sudo chown john:john ./fidentify.log
john@OptiPlex-GX270:~/Public/testdisk-7.0-WIP$ chmod 755 ./*
john@OptiPlex-GX270:~/Public/testdisk-7.0-WIP$ sudo ./testdisk_staticTestDisk 7.0-WIP, Data Recovery Utility, June 2014
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
john@OptiPlex-GX270:~/Public/testdisk-7.0-WIP$
```
I could have saved a step by using "sudo chmod", but I put it up the way it happened.

I tried setting a self-contained app's execute to "nobody"-- I got the same type of error he did. Obviously, you were right about that!

---

