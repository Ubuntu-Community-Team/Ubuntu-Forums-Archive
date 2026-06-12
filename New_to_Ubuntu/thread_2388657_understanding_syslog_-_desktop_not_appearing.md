---
title: "understanding syslog - desktop not appearing"
date: 2018-04-05
forum: New to Ubuntu
---

### Post by andreimc on 2018-04-05
Hello,

Have installed Ubuntu and am enjoying it. very much. 

Sometimes (about 50% of loading attempts) the Ubuntu OS is not loading the desktop - what happens is, I get the loading dots of Ubuntu, then the monitor enters standby mode, as if the gnome GUI does not load at all - no wallpaper, no lock screen, nothing - and monitor enters standby. What I end up doing is resetting, then it loads perfectly fine. 
Could someone please provide some hints, what specifically should I look for in the /var/log directory, to find the culprit? I assume it's the syslog I should be looking at, correct? I think the loading stops at some point during initialization but I don't know what specific lines to look for in the log.

Thank you.
Regards,

---

### Post by oldos2er on 2018-04-05
Would you please tell us your hardware specs, and Ubuntu version?

---

### Post by andreimc on 2018-04-06
ah yes, sorry. 

lsb_release -a says:
> No LSB modules are available.Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial




lshw output txt file is too big for this forum apparently but here is a part of it:

```

 description: Desktop Computer
    product: Z87X-UD4H (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.

description: Motherboard
       product: Z87X-UD4H-CF
       vendor: Gigabyte Technology Co., Ltd.
 description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 32GiB
   
description: CPU
          product: Intel(R) Core(TM) i7-4770K CPU @ 3.50GHz
          vendor: Intel Corp.
          physical id: 41
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-4770K CPU @ 3.50GHz
          slot: SOCKET 0
          size: 3052MHz
          capacity: 3900MHz
          width: 64 bits
          clock: 100MHz
   
description: VGA compatible controller
                product: GK110 [GeForce GTX 780]
                vendor: NVIDIA Corporation
   description: ATA Disk
             product: SanDisk SDSSDHII
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sda
             version: 10RL
             serial: 152354400155
             size: 894GiB (960GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=f818dc67
           *-volume:0
                
description: Linux swap volume
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sda1
                version: 1
                serial: 24da6e25-f1df-4c8a-a4eb-30605912a905
                size: 1952MiB
                capacity: 1952MiB
                capabilities: primary bootable nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                
description: Extended partition
                physical id: 2
                bus info: scsi@5:0.0.0,2
                logical name: /dev/sda2
                size: 892GiB
                capacity: 892GiB
                capabilities: primary extended partitioned partitioned:extended






```

does that suffice?

---

### Post by dino99 on 2018-04-06
Instead of wondering what the system is doing when you are seeing the dots, press 'esc' key to get the verbose mode. that let you see possible problem. If you want setting a permanent verbose booting mode (text), you can edit:
> sudo gedit /etc/default/grub and remove 'quiet splash' options from the related line, then save, and run > sudo update-grub then reboot.

When you says desktop is not loading 1/2 time, i'm feeling the process is still done silently in the background but that scaring you.
Then you can explore the log for details, run > journalctl -b from a terminal.

---

### Post by andreimc on 2018-04-06
thanks so much!! will do it and will get back w/ feedback.

---

### Post by andreimc on 2018-04-06
I followed your instructions and have managed to make a photo of exactly the step that hangs - I have waited for 25 minutes now. This is what I saw on the screen for 25 minutes: [https://imgur.com/rxjhrfN](https://imgur.com/rxjhrfN)

Is there any reason why ehci-pci would hang like that? Can I disable it temporarily? Now I had to reset the computer 3 times until I got a login screen into Ubuntu - when it hangs, the keyboard is dead. So I cannot enter in textmode or anything - its completely unresponsive. Only the reset button works.

---

