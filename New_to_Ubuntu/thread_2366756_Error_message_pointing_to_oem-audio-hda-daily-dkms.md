---
title: "Error message pointing to oem-audio-hda-daily-dkms"
date: 2017-07-21
forum: New to Ubuntu
---

### Post by windandwaves on 2017-07-21
As a complete Linux beginner, I have just received my xps13 with Unbuntu 16.04 preinstalled.

Each time I am installing a new programme using sudo apt install, the installation process finishes with the following error message:

```
Setting up oem-audio-hda-daily-dkms (0.201612080732~ubuntu16.04.1) ...
Removing old oem-audio-hda-daily-0.201612080732~ubuntu16.04.1 DKMS files...

------------------------------
Deleting module version: 0.201612080732~ubuntu16.04.1
completely from the DKMS tree.
------------------------------
Done.
Loading new oem-audio-hda-daily-0.201612080732~ubuntu16.04.1 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-83-generic
Building for architecture x86_64
Building initial module for 4.4.0-83-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/oem-audio-hda-daily-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.4.0-83-generic (x86_64)
Consult /var/lib/dkms/oem-audio-hda-daily/0.201612080732~ubuntu16.04.1/build/make.log for more information.
dpkg: error processing package oem-audio-hda-daily-dkms (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up curl (7.47.0-1ubuntu2.2) ...
Errors were encountered while processing:
 oem-audio-hda-daily-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I did not find any thread pointing to same problem. Any help with this would be highly appreciated!

---

### Post by TheFu on 2017-07-21
On a pre-installed system, my first stop would be at the vendor who sold it to me, especially for proprietary audio drivers that have "daily" in the name.

**Contact Dell**.  Provide their support with the full output for your update.  I can't tell from where this oem-audio kernel driver is coming. Hopefully, it is a dell repo, but the output above is missing that relevant portion.

---

### Post by Yellow Pasque on 2017-07-22
I would remove it and install an updated version of the package:
```
sudo apt-get purge oem-audio-hda-daily-dkms
```

[https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201707220416~ubuntu16.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201707220416~ubuntu16.04.1_all.deb)

---

### Post by angelicali on 2017-08-14
Did you solve this problem? I just got my xps13 with ubuntu 16.04 and I got the same error.

---

### Post by misael.lima on 2017-09-24
I have the same error in my dell inspiron with ubuntu 16.04 too!:-k

---

### Post by lexxonnet2 on 2017-10-19
I'm getting a similar issue with 17.10 RC. Anyone have any success with this module recently? I'm trying to get sound to output through HDMI on a 7th gen i5 NUC, and it seems extremely intermittent.

```

[FONT=monospace][COLOR=#000000]Setting up oem-audio-hda-daily-dkms (0.201710170117~ubuntu17.10.1) ...[/COLOR]
Removing old oem-audio-hda-daily-0.201710170117~ubuntu17.10.1 DKMS files...

------------------------------
Deleting module version: 0.201710170117~ubuntu17.10.1
completely from the DKMS tree.
------------------------------
Done.
Loading new oem-audio-hda-daily-0.201710170117~ubuntu17.10.1 DKMS files...
First Installation: checking all kernels...
/usr/share/oem-audio-hda-daily-dkms/postinst: 36: /usr/share/oem-audio-hda-daily-dkms/postinst: 4.13.0-16-generic=
4.13.0: not found
dpkg: error processing package oem-audio-hda-daily-dkms (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 oem-audio-hda-daily-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]
```

---

### Post by ian-weisser on 2017-10-19
> **windandwaves said:**
> ```
Building only for 4.4.0-83-generic
```
The current kernel version for 16.04 is 4.4.0-97, long past -83.

Before getting deep into why an older version is failing, I would ask why your kernel is so out-of date.




> **lexxonnet2 said:**
> I'm getting a similar issue with 17.10 RC.
Read the error messages *carefully. *Compare them.
Your issue seems to have rather a different cause, though both issues have a kernel component and the end result is admittedly similar.
I gently recommend that you open a new thread for your (different) issue.

---

