---
title: "Installing NVIDIA driver on UBUNTU 11.10"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by Dblkickflip720 on 2011-11-23
I have UBUNTU 11.10 desktop version on my comp and i am trying to install a driver for my nvidia gtx 560 ti video card. When i go to additional drivers, click NVIDIA accelerated graphics driver, and click activate, it downloads half way, and then i get this error message:
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

When i go to jockey.log it says this:
```

2011-11-22 23:46:09,029 DEBUG: Installing package: nvidia-current
2011-11-22 23:46:10,727 DEBUG: install progress dpkg-exec 0.000000
2011-11-22 23:46:10,934 DEBUG: install progress nvidia-current 0.000000
2011-11-22 23:46:10,935 DEBUG: install progress nvidia-current 20.000000
2011-11-22 23:46:17,612 DEBUG: install progress man-db 20.000000
2011-11-22 23:46:18,515 DEBUG: (Reading database ... 143108 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_280.13-0ubuntu6_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-current_280.13-0ubuntu6_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-current_280.13-0ubuntu6_amd64.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

2011-11-22 23:46:18,516 ERROR: Package failed to install:
(Reading database ... 143108 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_280.13-0ubuntu6_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-current_280.13-0ubuntu6_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-current_280.13-0ubuntu6_amd64.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

2011-11-22 23:46:18,725 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-11-22 23:46:18,726 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-11-22 23:46:18,746 ERROR: xorg:nvidia_current: get_alternative_by_name(nvidia-current) returned nothing
2011-11-22 23:46:18,897 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-22 23:46:18,898 DEBUG: nvidia_current is not the alternative in use
2011-11-22 23:46:21,159 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-22 23:46:21,160 DEBUG: nvidia_current is not the alternative in use
2011-11-22 23:46:21,282 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-22 23:46:21,282 DEBUG: nvidia_current_updates is not the alternative in use
2011-11-22 23:46:21,403 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-22 23:46:21,403 DEBUG: nvidia_current is not the alternative in use
2011-11-22 23:46:21,550 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-22 23:46:21,550 DEBUG: nvidia_current is not the alternative in use
2011-11-22 23:46:21,634 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2011-11-22 23:46:21,634 DEBUG: nvidia_current_updates is not the alternative in use

```Any help with this would be very much appreciated.

---

### Post by juliandracos on 2011-11-23
You might have better luck using the terminal to install the latest drivers.  

Here is the link to how to do that:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by wolfen69 on 2011-11-23
I have heard that going into /var/cache/apt/archives (as root) and deleting all .deb files will help. Then run *sudo apt-get update*

---

### Post by Dblkickflip720 on 2011-11-23
> **wolfen69 said:**
> I have heard that going into /var/cache/apt/archives (as root) and deleting all .deb files will help. Then run *sudo apt-get update*e

Can you explain how to delete stuff as root?

---

### Post by @gu79 on 2011-11-23
Open the terminal (Ctrl + Alt + t) and type: 
[INDENT]gksudo nautilus /var/cache/apt/archives
[/INDENT]

---

### Post by tariqsheikh on 2012-07-10
> **wolfen69 said:**
> I have heard that going into /var/cache/apt/archives (as root) and deleting all .deb files will help. Then run *sudo apt-get update*

That did the trick for me. Thanks a lot!

---

### Post by sudo smith on 2012-07-11
> **Dblkickflip720 said:**
> e

Can you explain how to delete stuff as root?

Another way in addition to @gu79's way is to simply type > 
sudo cd var/cache/apt/archives
sudo rm "*.deb"

or to combine the commands in one command > 
sudo rm var/cache/apt/archives/*.deb


Both of these commands will go into /var/cache/apt/archives and delete all files ending with .deb. As in any case when you are permamently deleting things I would make a backup just in case it messes something up ;)

---

