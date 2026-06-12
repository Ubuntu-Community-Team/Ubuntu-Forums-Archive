---
title: "Kubuntu takes a lot of time to shutdown"
date: 2018-02-12
forum: New to Ubuntu
---

### Post by greenonions on 2018-02-12
Hi all! How can i determine why my kubuntu 16.04 takes a lot of time to shutdown. Any commands that would help me?

Cheers!

---

### Post by vasa1 on 2018-02-12
Please install *inxi* and post the output of *inxi -Fxz* here.

---

### Post by RobGoss on 2018-02-12
What would you consider a long time?

---

### Post by mastablasta on 2018-02-13
you can check the logs and see what is happening.

---

### Post by greenonions on 2018-02-14
```
System:    Host: onion-ThinkPad-T420s Kernel: 4.13.0-32-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: KDE Plasma 5.8.8 (Qt 5.6.1) Distro: Ubuntu 16.04 xenial                                                                                   
Machine:   System: LENOVO (portable) product: 4174E12 v: ThinkPad T420s                                                                                       
           Mobo: LENOVO model: 4174E12 Bios: LENOVO v: 8CET49WW (1.29 ) date: 09/14/2011                                                                      
CPU:       Dual core Intel Core i5-2540M (-HT-MCP-) cache: 3072 KB                                                                                            
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10367                                                                                  
           clock speeds: max: 3300 MHz 1: 2591 MHz 2: 2591 MHz 3: 2591 MHz 4: 2591 MHz                                                                        
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0                                                    
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) Resolution: 1600x900@60.00hz                                                          
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile GLX Version: 3.0 Mesa 17.2.4 Direct Rendering: Yes                                                 
Audio:     Card-1 Intel 6 Series/C200 Series Family High Definition Audio Controller                                                                          
           driver: snd_hda_intel bus-ID: 00:1b.0                                                                                                              
           Card-2 Creative driver: USB Audio usb-ID: 002-003                                                                                                  
           Sound: Advanced Linux Sound Architecture v: k4.13.0-32-generic                                                                                     
Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e v: 3.2.6-k port: 4060 bus-ID: 00:19.0                                              
           IF: enp0s25 state: down mac: <filter>                                                                                                              
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak] driver: iwlwifi bus-ID: 03:00.0                                                               
           IF: wlp3s0 state: up mac: <filter>                                                                                                                 
Drives:    HDD Total Size: 250.1GB (28.3% used) ID-1: /dev/sda model: Hitachi_HTS54502 size: 250.1GB temp: 34C                                                
Partition: ID-1: / size: 222G used: 59G (28%) fs: ext4 dev: /dev/sda1                                                                                         
           ID-2: swap-1 size: 8.47GB used: 1.84GB (22%) fs: swap dev: /dev/sda5                                                                               
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present                                                                                        
Sensors:   System Temperatures: cpu: 46.0C mobo: N/A                                                                                                          
           Fan Speeds (in rpm): cpu: 4017                                                                                                                     
Info:      Processes: 231 Uptime: 3:11 Memory: 3646.5/7858.7MB Init: systemd runlevel: 5 Gcc sys: 5.4.0                                                       
           Client: Shell (bash 4.3.481) inxi: 2.2.35
```

---

### Post by greenonions on 2018-02-14
15-20 minutes

---

### Post by vasa1 on 2018-02-14
Your system is more than competent and 15-20 min is bad.

Do you by any chance opt to save your current session on shutdown? But even that couldn't possibly account for the delay.

Can you try with a new user? Did the slow close start recently or was it always like this?

---

### Post by greenonions on 2018-02-14
> **vasa1 said:**
> Your system is more than competent and 15-20 min is bad.

Do you by any chance opt to save your current session on shutdown? But even that couldn't possibly account for the delay.

Can you try with a new user? Did the slow close start recently or was it always like this?


So, i did another shutdown without saving the current session and took a long time also. I then created a new test user and the shutdown was super fast in 1-3 seconds.

There must be something wrong with my User. What could it be ?

Cheers

---

### Post by vasa1 on 2018-02-14
> **greenonions said:**
> So, i did another shutdown without saving the current session and took a long time also. I then created a new test user and the shutdown was super fast in 1-3 seconds.

There must be something wrong with my User. What could it be ?

CheersI wish I knew!

Let's assume you've backed up all your important data elsewhere. Rename *~/.config* to *~/.config.bak*. Log out, log back in. All (or most) of your applications will have lost the customized settings but has shutdown time improved? If it has, something in there was the culprit and, *iff you want your default settings back*, you'll need to figure it out by trial and error (by gradually moving components from *~/.config.bak* to *~/.config*); if the problem is not with your *~./config* folder, there are other dot files and dot folders in your home folder for you to check out in the same way.

---

### Post by greenonions on 2018-02-15
Guys!, after the second shutdown it worked. Shutdown is normal now, thank you!

---

### Post by greenonions on 2018-05-01
Hi All, im still having this issue where Ubuntu takes more than 30 minutes to shutdown or like 30-40 seconds to boot.

**Any ideas why this is happening?**

This is my fstab:
```
onion@onion:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=40bb1e94-d051-458c-8a4c-213a80600b47 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=81b0487e-bcec-4e49-b88c-a3c7ff112ec2 none            swap    sw              0       0



```


Here is the dmesg when it boots :
```

[   10.034777] systemd[1]: systemd 234 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN default-hierarchy=hybrid)
[   10.052071] systemd[1]: Detected architecture x86-64.
[   10.065495] systemd[1]: Set hostname to <onion>.
[   14.156172] systemd[1]: Listening on udev Kernel Socket.
[   14.156260] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   14.156395] systemd[1]: Created slice System Slice.
[   14.156434] systemd[1]: Listening on Syslog Socket.
[   14.156519] systemd[1]: Listening on Journal Audit Socket.
[   14.156556] systemd[1]: Listening on Journal Socket.
[   14.157035] systemd[1]: Starting Uncomplicated firewall...
[   15.291245] lp: driver loaded but no devices found
[   15.570488] ppdev: user-space parallel port driver
[   36.137932] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   36.261569] systemd-journald[342]: Received request to flush runtime journal from PID 1
[   37.088529] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\_SB.PCI0.LPC.PMIO) (20170531/utaddress-247)
[   37.088534] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   37.088537] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0

```

---

### Post by greenonions on 2018-05-01
Ok, just solved the shutdown issue with this solution: [https://ubuntuforums.org/showthread.php?t=2374934](https://ubuntuforums.org/showthread.php?t=2374934)

---

### Post by hier-kommt-luis on 2018-05-08
> **greenonions said:**
> Guys!, after the second shutdown it worked. Shutdown is normal now, thank you!

What you actually did then?

---

