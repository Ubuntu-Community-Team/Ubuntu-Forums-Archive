---
title: "the libGL.so.1 file is missing in the Nvidia-331 folder"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by Ragu_Ram_N on 2014-05-26
Hi everyone,
              I am running ubuntu 12.04 LTS. When i tried to run ansys mesh editor,  I got a error 'Unable to resolve Glxquery Extension'.I have nvidia-331 in my system. To solve that i tried the following code

sudo ln -s /usr/lib/nvidia-331/libGL.so.1 /usr/lib/libGL.so.1

, but i couldnt find the libGL.so.1 file in the directory  /lib/nvidia-331/. I can only see the modprobe.conf file in the directory /lib/nvidia-331. Is that a problem? if yes kindly help me in resolving the issue.

additional information:

when I typed: 
[COLOR=#008080]
dpkg -l | grep nvidia [/COLOR]

The following is displayed:

[COLOR=#008080]ii  nvidia-331                             331.20-0ubuntu0.0.2                                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                          1:0.2.44.2                                          Find obsolete NVIDIA drivers
ii  nvidia-settings                        331.20-0ubuntu0.0.1                                 Tool for configuring the NVIDIA graphics driver
[/COLOR]

thanks

Raguram Nagarjan

---

### Post by staticn0de on 2014-05-26
Check if the file is on your system

find / -name libGL.so.1

If it is,  add the directory to your library path

---

