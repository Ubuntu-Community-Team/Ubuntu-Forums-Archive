---
title: "Screen resolution trouble"
date: 2017-05-26
forum: New to Ubuntu
---

### Post by apol1 on 2017-05-26
Hi, Im getting my Ubuntu system all set up and my screen is absolutely huge!

I tried opening system settings but it seems to be thinking Im using a built in display...and I'm using a tower

Could someone please help me trouble shoot this? 

Thanks :)

---

### Post by Bucky Ball on 2017-05-26
We can try. Which release and flavour of Ubuntu are you using and which video card do you have? Best if you can include as much information as possible when posting for support to help us help you. Not much to go on there.

Open a terminal, run this:

```
sudo lshw -C video
```

Post the output here between code tags, please. (To do [code] tags, have a look at the link in my signature if you don't know how.)

---

### Post by apol1 on 2017-05-26
**```
 ***-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff**
```**

---

### Post by Bashing-om on 2017-05-26
apol1; Hello -

As Bucky Ball suspected, no graphic's driver is loaded .
Next we need to know the hardware, and match it to a driver.

post back:
```

lspci -k | grep -EA2 'VGA|3D'

```
and decide which way to go forward.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2017-05-26
If you look in 'Additional Drivers' you should see a driver there for the card. Should, not will. :)

Go to Software and Updates> Other Software and make sure you have the 'Canonical Partners' repository ticked first, then check Additional Drivers. Is there an driver there with 'Recommended' next to it? Do you know the model of the card you have?

Let us know the driver you see there for the card, if you see one.

---

### Post by apol1 on 2017-05-27
```
~$ lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1c03 (rev a1)
    Subsystem: eVga.com. Corp. Device 6161
    Kernel modules: nvidiafb, nouveau 
```

Here ya go Bashing-om :)

---

### Post by Bucky Ball on 2017-05-27
You must have missed post #5. Please tell us about the results of that.

---

### Post by apol1 on 2017-05-27
Yep there is no driver that I can see for the card itself. There is a NVIDIA binary driver - version 375.39 from nvidia-375. I tried using it once before but I got stuck in the infinite login loop, and not knowing what to do had to reinstall my OS :( so im avoiding it until I better understand whats happening.

Ive checked the Canonical Partners repository, and the one that says source code as well, but to no avail, I still have the same options as before, no recommended drivers as of yet.

The video card itself says EVGA GEFORCE GTX 1060

---

### Post by apol1 on 2017-05-27
there it should be up now sorry

---

### Post by Bashing-om on 2017-05-27
apol1; Well ...

That did not work out like I anticipated .
Mine:
> 
sysop@x1604:~$ lspci -k | grep -EA2 'VGA|3D'
06:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 710B] (rev a1)
	Subsystem: eVga.com. Corp. Device 2712
	Kernel driver in use: nvidia
sysop@x1604:~$ 

where my card is identified as a [GeForce GT 710B] .

Try it this-a-way
```

lspci -nnk | grep -iA3 vga

```
and let's see if Additional Drivers utility chooses the same driver as I will match .

EDIT: seen your last - EVGA GEFORCE GTX 1060 card .
That card is well supported in ubuntu - there should be no issues here .
What release are we working with ?
```

lsb_release -a

```
 
[INDENT][INDENT]many paths to an end
[/INDENT][/INDENT]

---

### Post by apol1 on 2017-05-27
no worries, heres mine ```
~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c03] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:6161]
    Kernel modules: nvidiafb, nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10f1] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:6161]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
05:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller [1b21:1242] 
```

---

### Post by apol1 on 2017-05-27
looks like ```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial 
```

---

### Post by Bashing-om on 2017-05-27
apol1; Humm ,...

Confirmed we are working with a 1060 card .. and I assure you that nvidia does recommend the 375 version driver :
[http://www.nvidia.com/download/driverResults.aspx/118290/en-us](http://www.nvidia.com/download/driverResults.aspx/118290/en-us)

Just  do not know why there is a problem .
Do what we can to find out.
show:
```

dpkg -l | grep -i nvidia
ls -al /etc/X11/xorg.conf 
grep -ri nvidia /etc/modprobe*

```

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by apol1 on 2017-05-27
huh, that is perplexing, lets see what we got here

```
 $ dpkg -l | grep -i nvidia
~$ ls -al /etc/X11/xorg.conf
ls: cannot access '/etc/X11/xorg.conf': No such file or directory
~$ grep -ri nvidia /etc/modprobe*
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist nvidiafb 
```

Im also unable to wake from suspend and any games I play are grainy and very slow about 3fps

---

### Post by Bashing-om on 2017-05-27
apol1; HuH ;

Nothing there to prevent installing the nvidia driver .
Another thing to check:
```

sudo find / -name "NVIDIA-Linux-*"
cat /var/log/gpu-manager.log

```

[INDENT][INDENT]again I say
[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by apol1 on 2017-05-27
I must have gremlins in my office again, here ya go :)
```
 ~$ sudo find / -name "NVIDIA-Linux-*"
[sudo] password: 
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.8.0-53-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.8.0-53-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Vendor/Device Id: 10de:1c03
BusID "PCI:1@0:0:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 0
Has amd? no
Has intel? no
Has nvidia? no
How many cards? 0
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? no
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? no
Is prime egl available? no 
```

---

### Post by Bashing-om on 2017-05-27
apol1; Welp !

That ain't good .
All those errors and I do not right off hand know what to make if it .
Getting deep here !
what returns:
```

ls -al /sys/bus/pci/devices/
ls -al /usr/src/
ls -al /lib/modules/

```
see if we can get some idea of what is not going on here .
In the meantime I am going to sleep on this, see if something comes to me .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by apol1 on 2017-05-27
I seem to have a knack for running into really weird problems

```
:~$ ls -al /sys/bus/pci/devices/
total 0
drwxr-xr-x 2 root root 0 May 26 23:52 .
drwxr-xr-x 5 root root 0 May 26 22:11 ..
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:00.0 -> ../../../devices/pci0000:00/0000:00:00.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:01.0 -> ../../../devices/pci0000:00/0000:00:01.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:01.1 -> ../../../devices/pci0000:00/0000:00:01.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:03.0 -> ../../../devices/pci0000:00/0000:00:03.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:05.0 -> ../../../devices/pci0000:00/0000:00:05.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:05.1 -> ../../../devices/pci0000:00/0000:00:05.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:05.2 -> ../../../devices/pci0000:00/0000:00:05.2
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:05.4 -> ../../../devices/pci0000:00/0000:00:05.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:11.0 -> ../../../devices/pci0000:00/0000:00:11.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:11.4 -> ../../../devices/pci0000:00/0000:00:11.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:14.0 -> ../../../devices/pci0000:00/0000:00:14.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:16.0 -> ../../../devices/pci0000:00/0000:00:16.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:19.0 -> ../../../devices/pci0000:00/0000:00:19.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:1a.0 -> ../../../devices/pci0000:00/0000:00:1a.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:1b.0 -> ../../../devices/pci0000:00/0000:00:1b.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:1c.0 -> ../../../devices/pci0000:00/0000:00:1c.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:1c.4 -> ../../../devices/pci0000:00/0000:00:1c.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:1d.0 -> ../../../devices/pci0000:00/0000:00:1d.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:1f.0 -> ../../../devices/pci0000:00/0000:00:1f.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:00:1f.3 -> ../../../devices/pci0000:00/0000:00:1f.3
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:01:00.0 -> ../../../devices/pci0000:00/0000:00:03.0/0000:01:00.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:01:00.1 -> ../../../devices/pci0000:00/0000:00:03.0/0000:01:00.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:05:00.0 -> ../../../devices/pci0000:00/0000:00:1c.4/0000:05:00.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0b.0 -> ../../../devices/pci0000:ff/0000:ff:0b.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0b.1 -> ../../../devices/pci0000:ff/0000:ff:0b.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0b.2 -> ../../../devices/pci0000:ff/0000:ff:0b.2
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0c.0 -> ../../../devices/pci0000:ff/0000:ff:0c.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0c.1 -> ../../../devices/pci0000:ff/0000:ff:0c.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0c.2 -> ../../../devices/pci0000:ff/0000:ff:0c.2
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0c.3 -> ../../../devices/pci0000:ff/0000:ff:0c.3
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0c.4 -> ../../../devices/pci0000:ff/0000:ff:0c.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0c.5 -> ../../../devices/pci0000:ff/0000:ff:0c.5
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0f.0 -> ../../../devices/pci0000:ff/0000:ff:0f.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0f.1 -> ../../../devices/pci0000:ff/0000:ff:0f.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0f.4 -> ../../../devices/pci0000:ff/0000:ff:0f.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0f.5 -> ../../../devices/pci0000:ff/0000:ff:0f.5
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:0f.6 -> ../../../devices/pci0000:ff/0000:ff:0f.6
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:10.0 -> ../../../devices/pci0000:ff/0000:ff:10.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:10.1 -> ../../../devices/pci0000:ff/0000:ff:10.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:10.5 -> ../../../devices/pci0000:ff/0000:ff:10.5
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:10.6 -> ../../../devices/pci0000:ff/0000:ff:10.6
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:10.7 -> ../../../devices/pci0000:ff/0000:ff:10.7
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:12.0 -> ../../../devices/pci0000:ff/0000:ff:12.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:12.1 -> ../../../devices/pci0000:ff/0000:ff:12.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:13.0 -> ../../../devices/pci0000:ff/0000:ff:13.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:13.1 -> ../../../devices/pci0000:ff/0000:ff:13.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:13.2 -> ../../../devices/pci0000:ff/0000:ff:13.2
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:13.3 -> ../../../devices/pci0000:ff/0000:ff:13.3
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:13.4 -> ../../../devices/pci0000:ff/0000:ff:13.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:13.5 -> ../../../devices/pci0000:ff/0000:ff:13.5
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:13.6 -> ../../../devices/pci0000:ff/0000:ff:13.6
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:13.7 -> ../../../devices/pci0000:ff/0000:ff:13.7
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:14.0 -> ../../../devices/pci0000:ff/0000:ff:14.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:14.1 -> ../../../devices/pci0000:ff/0000:ff:14.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:14.2 -> ../../../devices/pci0000:ff/0000:ff:14.2
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:14.3 -> ../../../devices/pci0000:ff/0000:ff:14.3
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:14.4 -> ../../../devices/pci0000:ff/0000:ff:14.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:14.5 -> ../../../devices/pci0000:ff/0000:ff:14.5
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:14.6 -> ../../../devices/pci0000:ff/0000:ff:14.6
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:14.7 -> ../../../devices/pci0000:ff/0000:ff:14.7
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:15.0 -> ../../../devices/pci0000:ff/0000:ff:15.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:15.1 -> ../../../devices/pci0000:ff/0000:ff:15.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:15.2 -> ../../../devices/pci0000:ff/0000:ff:15.2
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:15.3 -> ../../../devices/pci0000:ff/0000:ff:15.3
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:16.0 -> ../../../devices/pci0000:ff/0000:ff:16.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:16.6 -> ../../../devices/pci0000:ff/0000:ff:16.6
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:16.7 -> ../../../devices/pci0000:ff/0000:ff:16.7
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:17.0 -> ../../../devices/pci0000:ff/0000:ff:17.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:17.4 -> ../../../devices/pci0000:ff/0000:ff:17.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:17.5 -> ../../../devices/pci0000:ff/0000:ff:17.5
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:17.6 -> ../../../devices/pci0000:ff/0000:ff:17.6
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:17.7 -> ../../../devices/pci0000:ff/0000:ff:17.7
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:1e.0 -> ../../../devices/pci0000:ff/0000:ff:1e.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:1e.1 -> ../../../devices/pci0000:ff/0000:ff:1e.1
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:1e.2 -> ../../../devices/pci0000:ff/0000:ff:1e.2
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:1e.3 -> ../../../devices/pci0000:ff/0000:ff:1e.3
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:1e.4 -> ../../../devices/pci0000:ff/0000:ff:1e.4
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:1f.0 -> ../../../devices/pci0000:ff/0000:ff:1f.0
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:ff:1f.2 -> ../../../devices/pci0000:ff/0000:ff:1f.2

:~$ ls -al /usr/src/
total 28
drwxr-xr-x  7 root root 4096 May 26 01:46 .
drwxr-xr-x 11 root root 4096 Feb 15 13:30 ..
drwxr-xr-x 27 root root 4096 Feb 15 13:29 linux-headers-4.8.0-36
drwxr-xr-x  7 root root 4096 Feb 15 13:29 linux-headers-4.8.0-36-generic
drwxr-xr-x 27 root root 4096 May 25 22:22 linux-headers-4.8.0-53
drwxr-xr-x  7 root root 4096 May 25 22:22 linux-headers-4.8.0-53-generic
drwxr-xr-x  3 root root 4096 May 26 01:46 razer_chroma_driver-1.0.0

:~$ ls -al /lib/modules/
total 16
drwxr-xr-x  4 root root 4096 May 25 22:22 .
drwxr-xr-x 25 root root 4096 May 26 01:41 ..
drwxr-xr-x  5 root root 4096 Feb 15 13:35 4.8.0-36-generic
drwxr-xr-x  6 root root 4096 May 26 01:46 4.8.0-53-generic 
```

By the way the razer_chroma_driver-1.0.0 was installed after I encountered this problem, less it was installed somehow when I plugged in my fancy stuff. Do these tend to mess with graphics systems at all?

And thanks for looking into this, I feel like a monkey fixing a space shuttle

---

### Post by Bashing-om on 2017-05-27
apol1; yukkie on me !

I do not see a thing out of place ;
Yet there is "
> 
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
How many cards? 0

Huh --- why this path ?.. does not exist  and I do not see that it should !

But this :
> 
lrwxrwxrwx 1 root root 0 May 26 22:11 0000:01:00.0 -> ../../../devices/pci0000:00/0000:00:03.0/0000:01:00.0

why a deeper directory[0000:01:00.0] .
I ain't got fingered out !
too tired to think, so I quit for this session and as I say sleep on it !

[INDENT][INDENT]I can do that
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2017-05-27
The driver you have in Additional Drivers is the correct NVidia driver for that card.

---

### Post by apol1 on 2017-05-27
I figured it was, I have it currently using X.Org X Server -- Nouveau display driver from xserver-xorg-video-nouveau

I got stuck in a login-loop glitch when I tried the correct driver. Is there an on the fly solution for this glitch? If so I could risk turning on the NVidia driver. I probably should have mentioned that sorry.

---

### Post by Bucky Ball on 2017-05-27
With that card and that driver there was a glitch? Are you sure the login loop had anything to do with the graphics driver? That loop can happen for all sorts of reasons and not heard about it happening because of a graphics driver, but that's not saying much. I certainly am not the font of all knowledge on these things. :)

If it glitches on boot, simple boot the recovery kernel (should be under 'Advanced' entry in the grub list), when you get to the options there, choose 'Resume normal boot'. That will get you in without the nvidia driver and you can simply remove it and reboot.

---

### Post by apol1 on 2017-05-27
I can't say I really know, but yes there is a very consistent glitch, Now even restarting the computer or logging out at all is sending me into the login loop. I had to reinstall my OS multiple times, however I did get some error codes during install, does any of this mean anything? Thx :)

[ 12.651275] nouveau 0000:01:00.0: unknown chipset (136000a1]
[84.388966] EDAC sbridge: ECC is disabled. Aborting
[84.388993] EDAC sbridge: Could'nt find mci handler
[84.389015] EDAC sbridge: failed to register device with error -19

After each install I see these messages over a black screen an ubuntu message appears  saying "please remove installation medium then press ENTER: 

following these instructions leaves the machine unresponsive and I have to hard reboot to escape.

I hope this helps somewhat, let me know what you think, and thank you so much for your help so far.

---

### Post by Bucky Ball on 2017-05-27
```
[ 12.651275] **nouveau** 0000:01:00.0: unknown chipset (136000a1]
```

That looks to be throwing an error from nouveau, doesn't look like it's anything to do with the NVidia driver.

You have enabled the 375 driver in 'Additional Drivers'? (Doing so should have disabled the nouveau driver from memory.)

Note: installing over and over to reproduce the same error over and over again is not very fruitful. Best to just install and work through it, try to troubleshoot it with the help of others here and anything else you can find. If you're reproducing the same issue, exactly the same, every time you install, really no point in wasting the time.

---

### Post by Bashing-om on 2017-05-27
@apol1; Yuk !

> **Bucky Ball said:**
> ```
[ 12.651275] **nouveau** 0000:01:00.0: unknown chipset (136000a1]
```

That looks to be throwing an error from nouveau, doesn't look like it's anything to do with the NVidia driver.

You have enabled the 375 driver in 'Additional Drivers'? (Doing so should have disabled the nouveau driver from memory.)

Note: installing over and over to reproduce the same error over and over again is not very fruitful. Best to just install and work through it, try to troubleshoot it with the help of others here and anything else you can find. If you're reproducing the same issue, exactly the same, every time you install, really no point in wasting the time.

What returns:
```

grep "[[:space:]]1c03" /usr/share/misc/pci.ids

```
Let's see what that PCI ID is assigned to.

do you see anything relevant :
```

journalctl -b -0

```
in the boot log ? - long and detailed ! -

---------------------
Some background info - my use case !
GT710 nvidia card in release 14.04 was not recognized - unknown chip set . release 16.04 does support the card but I have serious issues with the nouveau driver ; the 375 version proprietary driver - from our repo - performs faultlessly in release 16.04.

We might consider here in your case to boot up with the 'nomodeset' boot parameter and then install the 375 version driver - depending on what the PCI assignments here are .

me:
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by apol1 on 2017-05-27
I have been enabling the 375 driver in Additional Drivers, but then things get weird, sometimes a dialog box appears saying I need to toggle secure boot off or third party software may not be usable. It askes me to make a password and enter it when prompted after the restart, however Im never asked for the password, and simply return to a login loop, even when Ive setup my system to log in automatically X.x 

Ive been reinstalling repeatedly since its my only option I know of at the moment to bypass the login loop. How do I boot the recovery kernel? and How do I open the grub menu to do this? Your right these reinstalls are a massive waste of time.

```
:~$ grep "[[:space:]]1c03" /usr/share/misc/pci.ids
        1133 1c03  Diva PRI/E1-30 PCI(e) v3
        17f2 1c03  Marvell 88E8001 Gigabit Ethernet Controller (Albatron)
    1c03  6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller 
```

```
 :~$ journalctl -b -0
-- Logs begin at Sat 2017-05-27 07:05:08 MST, end at Sat 2017-05-27 14:29:45 MST
May 27 07:05:08 Neptune systemd-journald[1807]: Runtime journal (/run/log/journa
May 27 07:05:08 Neptune kernel: Initializing cgroup subsys cpuset
May 27 07:05:08 Neptune kernel: Initializing cgroup subsys cpu
May 27 07:05:08 Neptune kernel: Initializing cgroup subsys cpuacct
May 27 07:05:08 Neptune kernel: Linux version 4.4.0-78-generic (buildd@lgw01-11)
May 27 07:05:08 Neptune kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-78-
May 27 07:05:08 Neptune kernel: KERNEL supported cpus:
May 27 07:05:08 Neptune kernel:   Intel GenuineIntel
May 27 07:05:08 Neptune kernel:   AMD AuthenticAMD
May 27 07:05:08 Neptune kernel:   Centaur CentaurHauls
May 27 07:05:08 Neptune kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]
May 27 07:05:08 Neptune kernel: x86/fpu: Supporting XSAVE feature 0x01: 'x87 flo
May 27 07:05:08 Neptune kernel: x86/fpu: Supporting XSAVE feature 0x02: 'SSE reg
May 27 07:05:08 Neptune kernel: x86/fpu: Supporting XSAVE feature 0x04: 'AVX reg
May 27 07:05:08 Neptune kernel: x86/fpu: Enabled xstate features 0x7, context si
May 27 07:05:08 Neptune kernel: x86/fpu: Using 'eager' FPU context switches.
May 27 07:05:08 Neptune kernel: e820: BIOS-provided physical RAM map:
May 27 07:05:08 Neptune kernel: BIOS-e820: [mem 0x0000000000000000-0x00000000000
May 27 07:05:08 Neptune kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000ba4
May 27 07:05:08 Neptune kernel: BIOS-e820: [mem 0x00000000ba4cc000-0x00000000bb2
May 27 07:05:08 Neptune kernel: BIOS-e820: [mem 0x00000000bb22f000-0x00000000bb2
May 27 07:05:08 Neptune kernel: BIOS-e820: [mem 0x00000000bb28f000-0x00000000bd4 
lines 1-23 
```

Earlier last night by machine suddenly asked me to restart my browser after installing a wine app from the software center. I suddenly lost my desktop interface and my courser turned into a black x with just the desktop background picture. I donno what it means but I figured it might help us better zero in on the problem.

---

### Post by Bashing-om on 2017-05-27
apol1; Welp.

Back to thin'n !

On my system when I execute:
```

lspci -nnk | grep -iA3 vga

```
I get the PCI ID
> 
06:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK208 [GeForce GT 710B] [10de:128b] (rev a1)

of "128b"

now I execute "
```

grep "[[:space:]]128b" /usr/share/misc/pci.ids

```
I get my card !
> 
sysop@x1604:~$ grep "[[:space:]]128b" /usr/share/misc/pci.ids
	128b  GK208 [GeForce GT 710B]
		103c 128b  1000Base-SX (PCI) [A7073A]
sysop@x1604:~$


Now why not you !
What have we going on here that the PCI assignment is intercepted -> 1133 1c03  Diva PRI/E1-30 PCI(e) v3 ?

Presently, out of my depth here as I can not explain what is taking place .

[INDENT][INDENT]just do not know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-05-27
apol1; Hummmm ...

Is this:
[https://www.dialogic.com/en/products/media/diva/diva-v-xpri-multi-span-e1t1-pri-isdn.aspx](https://www.dialogic.com/en/products/media/diva/diva-v-xpri-multi-span-e1t1-pri-isdn.aspx)
what we are looking at ?

[INDENT]which way did he go George
[/INDENT]

---

### Post by Bucky Ball on 2017-05-27
> **apol1 said:**
> I have been enabling the 375 driver in Additional Drivers, but then things get weird, sometimes a dialog box appears saying I need to toggle secure boot off or third party software may not be usable.

So did you go into the BIOS and switch of Secure Boot??? Exactly what you should be doing. It is clearly stating that secure boot may prevent third-party software, i.e. your NVidia 375 driver ...

---

### Post by apol1 on 2017-05-28
I gave it a shot a little while ago, but by BIOS doesn't have any switches that I can see, I'll have another look but I'll likely end up in another log-in loop. I'll try to open grub this time and see if i can run recovery. Be warned I have no idea what im doing :)

Also I don't think thats my graphics card, unless media cards are different then graphics cards

---

### Post by apol1 on 2017-05-28
O_O it...worked

wow I really don't know what im doing! Well gotta start somewhere

Im gotta test out everything, and get back to ya.

I am eternally grateful for your help, I know so little and I am very eager to learn how to harness this incredible technology. 

Thanks for bashing your head on the wall as hard as I was, this world needs more people like you *bows many times*

---

### Post by apol1 on 2017-05-28
Looks like to worked, every things humming as it once was, I'll mark this as solved least for now, Thank you for everything :D

---

### Post by Bucky Ball on 2017-05-28
Excellent news and well done working your way through it. If you have the NVidia driver installed you should have the NVidia config app installed also. Open the dash and type in 'nvidia' and you should get the 'nvidia x-server config tool' or something (I'm not on my box with the GTX 970 in at moment to check, sorry).

Thanks for marking as solved and enjoy. :)

---

### Post by apol1 on 2017-05-30
hmm Ive got a few random freezes here and there

It appears to be associated with using steam games, everything&#8217;s fine until I launch one, then even after several restarts Ubuntu will freeze within minuets or even seconds. After about 3-5 hardboots everything's back to normal.

---

