---
title: "Broken packages prevent me from using boot-repair - What should I do?"
date: 2022-05-07
forum: New to Ubuntu
---

### Post by goldbeere on 2022-05-07
Hey,

I have an Ubuntu 20.04 LTS installation.
```

uname --a
    Linux *** 5.13.0-40-generic #45~20.04.1-Ubuntu SMP Mon Apr 4 09:38:31 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

I need to update the boot manager.

So I tried to use boot-repair (from a live CD), which get me good results in the past.

This time I run into a problem that I procrastinate for some time now, but now I cannot ignore it anymore (although I've tried).

The output from the first of the manual steps of the boot-repair "process":

```

ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/nvme0n1p3" dpkg --configure -a

Setting up libgl1-amdgpu-mesa-dri:amd64 (1:20.1.0-1109583) ...
dpkg: error processing package libgl1-amdgpu-mesa-dri:amd64 (--configure):
 installed libgl1-amdgpu-mesa-dri:amd64 package post-installation script subprocess returned error exit status 1
Setting up libgl1-amdgpu-mesa-dri:i386 (1:20.1.0-1109583) ...
dpkg: error processing package libgl1-amdgpu-mesa-dri:i386 (--configure):
 installed libgl1-amdgpu-mesa-dri:i386 package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 libgl1-amdgpu-mesa-dri:amd64
 libgl1-amdgpu-mesa-dri:i386

```

I get such an error message at the end of every installation, but the installations are nonetheless successful usually.
It looks like this:

```

Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.7) ...
Errors were encountered while processing:
 libgl1-amdgpu-mesa-dri:amd64
 libgl1-amdgpu-mesa-dri:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

But, as I said, usually, the installations are successful nonetheless.

But boot-repair cannot go on with it.

Information about broken packages (commands copied from askubuntu.com) from the 20.04 LTS:

```

dpkg -l | grep ^..r
   # returns nothing

dpkg-query -W -f='${db:Status-Abbrev} ${binary:Package}\n' | grep -E ^.[^nci]
    # returns
    iF  libgl1-amdgpu-mesa-dri:amd64
    iF  libgl1-amdgpu-mesa-dri:i386

```

I don't remember exactly whether I've tried to install a special amd driver or what else I've done to produce this error.

I searched the web for solutions, but I am a bit afraid of just copying "force"-commands. I've naively destroyed a Pop! OS installation with this before.

So I rather ask you, what I should do about it?

Thank you for your patients, time and effort <3
Andreas

---

### Post by rsteinmetz70112 on 2022-05-07
Have you tried to run```
 $ sudo apt install -f
``` or```
$ sudo dpkg --configure -a
``` The first command will attempt to fix any broken packages and the second will attempt to configure all packages. They often work but if they don't they often will give you a clue as to what the problems is. These commands are generally pretty safe.

---

### Post by goldbeere on 2022-05-08
Thank you for your answer. I've run both commands . These are the results:

```

sudo apt install -f

    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
    2 not fully installed or removed.
    After this operation, 0 B of additional disk space will be used.
    Setting up libgl1-amdgpu-mesa-dri:amd64 (1:20.1.0-1109583) ...
    dpkg: error processing package libgl1-amdgpu-mesa-dri:amd64 (--configure):
     installed libgl1-amdgpu-mesa-dri:amd64 package post-installation script subprocess returned error exit status 1
    Setting up libgl1-amdgpu-mesa-dri:i386 (1:20.1.0-1109583) ...
    dpkg: error processing package libgl1-amdgpu-mesa-dri:i386 (--configure):
     installed libgl1-amdgpu-mesa-dri:i386 package post-installation script subprocess returned error exit status 1
    Errors were encountered while processing:
     libgl1-amdgpu-mesa-dri:amd64
     libgl1-amdgpu-mesa-dri:i386
    E: Sub-process /usr/bin/dpkg returned an error code (1)


sudo dpkg --configure -a

    Setting up libgl1-amdgpu-mesa-dri:amd64 (1:20.1.0-1109583) ...
    dpkg: error processing package libgl1-amdgpu-mesa-dri:amd64 (--configure):
     installed libgl1-amdgpu-mesa-dri:amd64 package post-installation script subprocess returned error exit status 1
    Setting up libgl1-amdgpu-mesa-dri:i386 (1:20.1.0-1109583) ...
    dpkg: error processing package libgl1-amdgpu-mesa-dri:i386 (--configure):
     installed libgl1-amdgpu-mesa-dri:i386 package post-installation script subprocess returned error exit status 1
    Errors were encountered while processing:
     libgl1-amdgpu-mesa-dri:amd64
     libgl1-amdgpu-mesa-dri:i386

```

I think now that I've tried to install an amdgpu-pro driver. I'll try to uninstall it.

---

### Post by goldbeere on 2022-05-08
The solution was to uninstall the amdgpu-pro driver.

```

./amdgpu-pro-install --uninstall

```

It seems, that this driver needs an older kernel version.

The result is this:

```

sudo apt install -f

    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.

sudo dpkg --configure -a
    # returns nothing

```

Thank you very much for helping me. :D

---

