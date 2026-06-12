---
title: "VirtualBox-3.2.6_OSE"
date: 2010-07-24
forum: Packaging and Compiling Programs
---

### Post by masque7 on 2010-07-24
I am using Ubuntu x86_64 10.04 

My reason for compiling is because the version of VBox-OSE in the repos isn't compatible with the version of X that Arch Linux uses (since arch is rolling release, Ubuntu is not), which means I cannot install guest additions for Arch.

Going through ./configure a few times, I ended up with having all the dependencies I needed and successfully configured it. :)

The last 2 entries of the ./configure are interesting:
```
Checking for compiler.h: compiler.h **not found**, OK.
Checking for 32-bit support: OK.
```
As you can see I have  gcc-multilib. 

After a successful ./configure:
```
successfully generated '/home/jake/VirtualBox-3.2.6_OSE/AutoConfig.kmk' and '/home/jake/VirtualBox-3.2.6_OSE/env.sh'.
Source '/home/jake/VirtualBox-3.2.6_OSE/env.sh' once before you start to build VBox:

source /home/jake/VirtualBox-3.2.6_OSE/env.sh
kmk
```
And so I did kmk in that directoy.
[URL="http://pastebin.com/VBBFkWGk"]
Here[/URL] are the error sections/fails.

---

### Post by SevenMachines on 2010-07-24
looks like its missing the pam dev files, try
$ sudo apt-get install libpam-dev

---

### Post by interval1066 on 2010-07-30
You know... Oracle offers a non-oem (with usb) deb package for Ubuntu.... no need to compilt it from scratch if you don't need to...

---

### Post by masque7 on 2010-07-30
That's not the OSE though is it? Prefer to support that one. More demand, more support

---

