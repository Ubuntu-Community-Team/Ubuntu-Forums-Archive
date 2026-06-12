---
title: "Getting poor  perfomance in 12.04"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by dead5 on 2012-09-20
I am getting really poor performance while using Ubuntu 12.04 even though i have the latest drivers installed and can run fedora 16 without a hitch.  The launcher takes 15 - 30 seconds to respond, switching between workspaces provides poor framerates, basic applications jitter a lot etc.

I am unable to discern the cause for this.

My config is:

Biostar T5XE motherboard
Intel Core i7 860
AMD Radeon HD 5770
4GB ram.

---

### Post by ubudog on 2012-09-20
Have you tried using Unity 2D?  You can pick that when logging in, by clicking the gear over your username.

---

### Post by dead5 on 2012-09-20
Most apps(Eclipse, Rhythmbox, Ninja-IDE, firefox etc) don't perform well in gnome classic either.

If it helps, I am unable to run gnome 3  on Ubuntu although it runs on fedora.

---

### Post by NikTh on 2012-09-20
Hi , 
is this a regular installation or wubi ? (from inside windows) 

I can imagine two things . First the installation went wrong , or something with graphics driver went wrong. 
But you must provide more info. 

```
lspci -nnk | grep -iA2 vga
``` 

Run boot-repair and give here the pastebin link . [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
second option from a liveCD/Usb. 

also ```
dpkg -l | grep fglrx
``` would be helpful . 

and ```
env|grep DESK
``` 

Thanks

---

### Post by dead5 on 2012-09-20
I am running a regular installation of Ubuntu.

 lspci -nnk | grep -iA2 vga gives 
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series] [1002:68b8]
    Subsystem: PC Partner Limited Device [174b:1482]
    Kernel driver in use: radeon

```dpkg -l | grep fglrx does nothing.

env|grep desk gives
```
DESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity

```

---

### Post by NikTh on 2012-09-20
> **dead5 said:**
> I am getting really poor performance while using  Ubuntu 12.04 even though i have the latest drivers installed 
> **dead5 said:**
> 
lspci -nnk | grep -iA2 vga gives 
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series] [1002:68b8]
    Subsystem: PC Partner Limited Device [174b:1482]
    **Kernel driver in use: radeon**

```

Hi , 
If you had the latest drivers installed , the section in bold should be like this ```
Kernel driver in use: fglrx_pci
``` 

Try to install the AMD's driver . First try from additional drivers (jockey-gtk , from terminal). And try  to activate (install) the normal fglrx driver . Not this with updates. 

Thanks

---

### Post by dead5 on 2012-09-21
Thanks man. It worked.

---

