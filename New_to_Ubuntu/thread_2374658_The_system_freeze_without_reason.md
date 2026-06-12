---
title: "The system freeze without reason"
date: 2017-10-17
forum: New to Ubuntu
---

### Post by sed_faster on 2017-10-17
This is my system:
```

$ uname -a
Linux xxx 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```

Lately my system has freeze! My only option is push reset physic button. I wonder know where and how can I discovery why my system freeze. When system freeze I was only execute two tabs on broswer Vivaldi.
Thanks

---

### Post by Bucky Ball on 2017-10-18
Just wondering if it's got anything to do with the fact you've manually installed another kernel which is not the default 16.04.3 kernel. Did you have this issue when you were running on the regular 16.04.3 kernel? Before you manually installed the newer 4.10 kernel?

I am running 16.04.3 and it is currently using 4.4.0-97-generic. Reboot, select that kernel from the options list and see if you get the same issues. If not, it's the kernel. If so, time to dig deeper.

---

### Post by vasa1 on 2017-10-18
> **Bucky Ball said:**
> Just wondering if it's got anything to do with the fact you've manually installed another kernel which is not the default 16.04.3 kernel. ...
I'm on 16.04.3 as well:```
$ uname -a
Linux aes-Inspiron-15-3567 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux                       
$ lsb_release -a                                                                                                                          
No LSB modules are available.                                                                                                                        
Distributor ID: Ubuntu                                                                                                                               
Description:    Ubuntu 16.04.3 LTS                                                                                                                   
Release:        16.04                                                                                                                                
Codename:       xenial                                                                                                                               
$
```
And I haven't installed any kernel by myself. Those users who start with a clean install of 16.04 (original) and keep on upgrading will have the kernel version you have.
Those who install from 16.04.2 or 16.04.3 and keep on upgrading will have higher kernel versions. See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Bucky Ball on 2017-10-18
> **vasa1 said:**
> Those users who start with a clean install on 16.04 (original) and keep on upgrading will have the kernel version you have.
Those who install from 16.04.2 or 16.04.3 and keep on upgrading will have higher kernel versions.

Ah ha. Thanks for that.

Carry on. ;)

---

### Post by sed_faster on 2017-10-18
Hello,

Should I run this command?
```

$ sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-hwe-16.04 is already the newest version (1:7.7+16ubuntu3~16.04.1).
The following additional packages will be installed:
  linux-headers-4.10.0-37 linux-headers-4.10.0-37-generic
  linux-headers-generic-hwe-16.04 linux-image-4.10.0-37-generic
  linux-image-extra-4.10.0-37-generic linux-image-generic-hwe-16.04
Suggested packages:
  fdutils linux-tools
The following NEW packages will be installed:
  linux-headers-4.10.0-37 linux-headers-4.10.0-37-generic
  linux-image-4.10.0-37-generic linux-image-extra-4.10.0-37-generic
The following packages will be upgraded:
  linux-generic-hwe-16.04 linux-headers-generic-hwe-16.04
  linux-image-generic-hwe-16.04
3 upgraded, 4 newly installed, 0 to remove and 26 not upgraded.
Need to get 61,2 MB of archives.
After this operation, 308 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

This means which I have a beta kernel and I need downgrade to stable version kernel?
Thanks

---

### Post by deadflowr on 2017-10-18
> Should I run this command?
Are those packages not installed already?
Wouldn't a simple 
```
sudo apt update && sudo apt full-upgrade
``` 
update those?

> This means which I have a beta kernel and I need downgrade to stable version kernel?
No, the hwe kernels are stable.
They are not in any way beta.

---

### Post by sed_faster on 2017-10-18
Older configuration:
```

$ uname -a
Linux xxx 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
**Release:    16.04**
Codename:    xenial                                                                                                                           

```

After run sudo apt update && sudo apt full-upgrade:
```
$ uname -a
Linux xxx 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
**Release:    16.04**
Codename:    xenial

```


It's the same?
Thanks
[B]
[UPGRADE][/B]
This is means which my version kernel it is correct?

---

### Post by vasa1 on 2017-10-18
On a fully updated 16.04.3, I have```
$ uname -a
Linux aes-Inspiron-15-3567 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by deadflowr on 2017-10-18
uname -a change requires a reboot.

---

### Post by sed_faster on 2017-10-22
Now I understood. After turn off my system and back here to read the post I run command uname -a and result was this:
```

$ uname -a
Linux xxx 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

This means which the system supposedly don't will be freeze anymore! But if this is occur what can I do to monitor the supposedly cause of the problem?
Thanks

---

### Post by mastablasta on 2017-10-23
freeze is often caused by bad hardware. often GPU or another component overheating. 

you can check dmesg (the old one) and other logs for any reported errors.

you can also install psensor, so you can monitor the components temperature with a graphical interface.

if all these still fail to show what is causing troubles i suggest a stress test such as those available on UltimatebootCD or similar rescue disks.

if you think vivaldi itself is causing the issue you can also run it form terminal and output the possible errors to a file. but for example i am using Chromium on Kubuntu, because Firefox (otherwise my go to browser) suddenly had issues. it didn't crash the system but it did slow it down and made other problems (crashing components).

---

### Post by sed_faster on 2017-10-27
Well, after almost a week with works a kernal 4.10.0-37 I should tell I didn't any problems with pc freeze. But, today, when I run a virtual machine through virtualbox with 80% my ram dedicate to this virtual machine my system freeze. I can't opened terminal to find the PID relative of the task to kill this.


What should I do in this situation?


Thanks

---

### Post by sed_faster on 2017-10-27
> **mastablasta said:**
> freeze is often caused by bad hardware. often GPU or another component overheating. 

you can check dmesg (the old one) and other logs for any reported errors.

you can also install psensor, so you can monitor the components temperature with a graphical interface.

if all these still fail to show what is causing troubles i suggest a stress test such as those available on UltimatebootCD or similar rescue disks.

if you think vivaldi itself is causing the issue you can also run it form terminal and output the possible errors to a file. but for example i am using Chromium on Kubuntu, because Firefox (otherwise my go to browser) suddenly had issues. it didn't crash the system but it did slow it down and made other problems (crashing components).

My setup it is new. And the temperature it is ok, for example right now this is scenario:
> 
$ free -mh
              total        used        free      shared  buff/cache   available
Mem:           7,7G        3,5G        1,0G        402M        3,1G        3,4G
Swap:            0B          0B          0B

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +36.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:        +35.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:        +35.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:        +36.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:        +34.0°C  (high = +80.0°C, crit = +100.0°C)


acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +119.0°C)
temp2:        +29.8°C  (crit = +119.0°C)


asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM


$ uptime -p
up 27 minutes

[B]
Note: [/B]half an hour ago I need restart my system because the SO freeze
I will learn more about dmesg to know I should I interpret the reports!

---

### Post by Bucky Ball on 2017-10-28
One thing you could try to prevent the freeze is to run the virtual machine with less RAM. You gave it 80%? Why? That leaves your host OS with 20% of your RAM to use to run whatever you have running (Firefox is open in the host as well, yes?), Virtualbox and a virtual machine running in it with whatever programs you have open in the VM.

For clarity and to refresh; is the only time your system freezes when you are trying to run a VM with 80% RAM given to it? Also, I may have missed it, but how much physical RAM do you have installed in the machine?

---

### Post by sed_faster on 2017-10-28
> **Bucky Ball said:**
> One thing you could try to prevent the freeze is to run the virtual machine with less RAM. You gave it 80%? Why? That leaves your host OS with 20% of your RAM to use to run whatever you have running (Firefox is open in the host as well, yes?), Virtualbox and a virtual machine running in it with whatever programs you have open in the VM.

For clarity and to refresh; is the only time your system freezes when you are trying to run a VM with 80% RAM given to it? Also, I may have missed it, but how much physical RAM do you have installed in the machine?

Thanks to your help

This is my fault. Choose 80%, from my 8Gb ram to only virtualbox. I adjust the ram to vm, and now have only 2GB and  remaining, 6GB, dedicated to my host. This freeze, or better, the system gets very slow, occur when, for example, when I use virtuabl box with 80% dedicated to the virtual machine, or when I ran X-Plane 11 ([http://www.x-plane.com](http://www.x-plane.com)).

Exist a way to unlock machine on this situation? Without having the need push physic button restart?  Thanks

---

### Post by deadflowr on 2017-10-28
Perhaps knowing the hardware specs can shed some light.

---

### Post by sed_faster on 2017-10-28
My setup is:

Asus Prime B250-Pro
8Gb Ram Kingston
Intel(R) Core(TM) i5-7500 CPU @ 3.40G
Two disk 120Gb Kingston V300

Thanks

---

### Post by VMC on 2017-10-28
> **vasa1 said:**
> I'm on 16.04.3 as well:```
$ uname -a
Linux aes-Inspiron-15-3567 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux                       
$ lsb_release -a                                                                                                                          
No LSB modules are available.                                                                                                                        
Distributor ID: Ubuntu                                                                                                                               
Description:    Ubuntu 16.04.3 LTS                                                                                                                   
Release:        16.04                                                                                                                                
Codename:       xenial                                                                                                                               
$
```
And I haven't installed any kernel by myself. Those users who start with a clean install of 16.04 (original) and keep on upgrading will have the kernel version you have.
Those who install from 16.04.2 or 16.04.3 and keep on upgrading will have higher kernel versions. See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
Interesting. I didn't know this. I keep the original ISO and have been updating all along and I now have:
```
$ uname -r  4.4.0-98-generic
```
I guess I need to use the latest ISO. Even though I don't understand the reasoning. I thought as long as you keep current all updates would apply to LTS.

---

### Post by VMC on 2017-10-29
> **Bucky Ball said:**
> ...
I am running 16.04.3 and it is currently using 4.4.0-97-generic. Reboot, select that kernel from the options list and see if you get the same issues. If not, it's the kernel. If so, time to dig deeper.

> **vasa1 said:**
> I'm on 16.04.3 as well:```
$ uname -a
Linux aes-Inspiron-15-3567 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux                       
$ lsb_release -a                                                                                                                          
No LSB modules are available.                                                                                                                        
Distributor ID: Ubuntu                                                                                                                               
Description:    Ubuntu 16.04.3 LTS                                                                                                                   
Release:        16.04                                                                                                                                
Codename:       xenial                                                                                                                             
$
```
And I haven't installed any kernel by myself. Those users who start with a clean install of 16.04 (original) and keep on upgrading will have the kernel version you have.
Those who install from 16.04.2 or 16.04.3 and keep on upgrading will have higher kernel versions. See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
Something strange is going on here. My original is like Bucky's. (4.4.0-98-generic). I recently installed latest ISO and I too am having freezes. Obliviously its kernel related, but Artful has an even higher kernel and my system doesn't freeze at all?!

---

