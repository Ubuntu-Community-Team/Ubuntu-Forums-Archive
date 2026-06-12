---
title: "How do you retrieve serial numbers for your hardware?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by futuroimperfetto on 2008-09-06
Hello,

I am trying to see if there is any way to find serial numbers for my hardware. I found that running:

```
 sudo dmidecode
```

does return a list of numbers, which I believe are what I'm looking for, but I am not too sure.

Is this OK or are there any other commands I could try?

I have a Dell XPS 1330 with a nVidia 8400 GS card and am trying to understand more about it, because it appears it might have issues, as it has been reported here:

[http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx]("http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx")

and here

[http://www.tgdaily.com/content/view/39045/135/]("http://www.tgdaily.com/content/view/39045/135/")

I wanted to collect as much info as possible, in case they make an official list about the versions of affected the graphic cards.

Thanks!

---

### Post by cdtech on 2008-09-06
Try in a terminal:
```
lshw
```

---

### Post by SteveNorman on 2008-09-06
I dont think you can get the serial number with those commands,,only the model number. You'll probably have to open up the machine and physically check the tag.

---

### Post by cdtech on 2008-09-06
> **SteveNorman said:**
> I dont think you can get the serial number with those commands,,only the model number. You'll probably have to open up the machine and physically check the tag.

Have you tried the command?
```
 *-usb
                description: Video
                product: HP Webcam
                vendor: SuYin
                physical id: 2
                bus info: usb@3:2
                version: 1.00
                **serial: CN0314-OV02-VH-R03.02.02**
                capabilities: usb-2.00
                configuration: driver=uvcvideo maxpower=500mA speed=480.0MB/s
```
```
*-disk:0
             description: ATA Disk
             product: WDC WD2500BEVS-6
             vendor: Western Digital
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 01.0
             **serial: WD-WXE807611475**
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000116f9
```

---

### Post by futuroimperfetto on 2008-09-06
Hi cdtech and SteveNorman,

 Thanks for your quick answers! I have tried running

```
lshw
```

and I get 

```
$ lshw
WARNING: you should run this program as super-user.

```

and then I get a list of of my hardware devices. For three of them I do get indeed a line called "serial", like for the cpu (though it looks a bit weird as a serial):

```
*-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 2201MHz
          capacity: 2201MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida nx cpufreq
          configuration: id=1
```

but for my nVidia card I get

```
*-display
                description: VGA compatible controller
                product: GeForce 8400M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
```

Now, if I try to run it as a super-user, I don't get anything! I don't know why. Is there an explanation to this? If I do

```
sudo lshw
```

or

```
$sudo su
lshw
```

I get an empty terminal, with only the following line

```
PCI (sysfs)
```

and it seems to run forever, as it does not return me a command line (aka I need to close the terminal). What do you think?

I guess I could try to open the laptop, I have no idea which one the gpu is, but maybe somebody has done it before and I can look it up.

---

