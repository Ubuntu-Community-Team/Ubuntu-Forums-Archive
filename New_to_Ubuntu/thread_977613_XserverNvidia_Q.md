---
title: "Xserver/Nvidia Q"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Whisp3r on 2008-11-10
Hi everyone. I'm trying to get my Xserver for a Nvidia card up and running. I downloaded the X96 driver, but when I run to run XServer, it says I need to run nvidia-xconfig. When I try, here's what I get. I'm totally new to this. Help the poor new guy out? Thanks so much:


> 
whisp3r@LinuxBox:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

sh: pkg-config: not found
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.


---

### Post by Toet on 2008-11-10
When someone finds the awnser please give it to this person aswell:

[http://ubuntuforums.org/showthread.php?p=6145120#post6145120](http://ubuntuforums.org/showthread.php?p=6145120#post6145120)

I think this is the same problem.


Furthermore I think, but this is something I am not sure of, that the X96 driver does not run xserver 7.4. Can somebody deny or akknowlegde this?

---

