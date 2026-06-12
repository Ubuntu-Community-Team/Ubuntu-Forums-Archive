---
title: "everytime I start up I get checking disk for errors"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-03-05
I have let it do its thing it counts up to 100% and it tells me nothing. I never got this before and I do notice that the hard drives are too quiet now. There, not making the noise they use to make, when I would started the computer. Any clues on what to do?

---

### Post by deadflowr on 2014-03-06
Is the Os running or anything in particular you find wrong?

Maybe utilize [smartmontools]("https://help.ubuntu.com/community/Smartmontools") to see the status of the disk.

---

### Post by EZZ9 on 2014-03-06
I downloaded the [smartmontools  ]("https://help.ubuntu.com/community/Smartmontools") 
Came up clean when running the tests I do get Firefox crashes and it took the sofewire center 10 minutes to open. Also just tried to check for updates and can not connect on software updater and synaptic package manager.

---

### Post by ibjsb4 on 2014-03-06
Try updating in terminal:

```
sudo apt-get update
```

---

### Post by tgalati4 on 2014-03-06
How are you shutting your computer down?  If this is a laptop and the battery is crashing, then you will get a file system check on every boot.  If you are performing normal shutdowns, then there is some other problem.  Remember SMART only captures 2/3 of the failures.  1/3 are spontaneous.

Look through your dmesg.  Open a terminal:

```
dmesg | tail -100
```

Post any errors.

---

### Post by EZZ9 on 2014-03-06
this is from  "sudo apt-get updates" I see a failed at the end. 
```

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                     
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy InRelease                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates InRelease                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release.gpg                    
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg [933 B]             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release.gpg [933 B]            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release [49.6 kB]               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release [49.6 kB]              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [34.7 kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse i386 Packages       
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg [316 B]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en                
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [8,413 B]      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [689 B]     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en                  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Sources [75.8 kB]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [98.8 kB]   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                      
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release [11.9 kB]                         
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                      
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Sources [67.9 kB]    
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                      
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [35.1 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                      
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Sources [1,358 B]  
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main i386 Packages [215 kB]   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                      
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [1,388 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                           
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en [53.6 kB]  
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                           
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe i386 Packages [157 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en         
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,763 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                           
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en [101 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en         
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages [19.5 kB]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en        
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en [20.4 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en        
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en [79.1 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main i386 Packages   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                          
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Fetched 1,085 kB in 19s (55.3 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by EZZ9 on 2014-03-06
```
bob@bob-desktop:~$ dmesg | tail -100
[   23.239597] systemd-udevd[335]: starting version 204
[   23.410731] lp: driver loaded but no devices found
[   23.541716] [drm] Initialized drm 1.1.0 20060810
[   23.568178] wmi: Mapper loaded
[   23.659454] parport_pc 00:06: reported by Plug and Play ACPI
[   23.659521] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   23.686019] type=1400 audit(1394106977.219:2): apparmor="STATUS" operation="profile_load" parent=367 profile="unconfined" name="/sbin/dhclient" pid=370 comm="apparmor_parser"
[   23.686041] type=1400 audit(1394106977.219:3): apparmor="STATUS" operation="profile_load" parent=367 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=370 comm="apparmor_parser"
[   23.686056] type=1400 audit(1394106977.219:4): apparmor="STATUS" operation="profile_load" parent=367 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=370 comm="apparmor_parser"
[   23.687537] type=1400 audit(1394106977.219:5): apparmor="STATUS" operation="profile_replace" parent=367 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=370 comm="apparmor_parser"
[   23.687560] type=1400 audit(1394106977.219:6): apparmor="STATUS" operation="profile_replace" parent=367 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=370 comm="apparmor_parser"
[   23.692431] type=1400 audit(1394106977.227:7): apparmor="STATUS" operation="profile_replace" parent=367 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=370 comm="apparmor_parser"
[   23.720775] intel_rng: Firmware space is locked read-only. If you can't or
[   23.720775] intel_rng: don't want to disable this in firmware setup, and if
[   23.720775] intel_rng: you are certain that your system has a functional
[   23.720775] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   23.749802] lp0: using parport0 (interrupt-driven).
[   23.796531] [drm] Memory usable by graphics device = 256M
[   23.796548] i915 0000:00:02.0: setting latency timer to 64
[   23.796955] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   23.796960] [drm] Driver supports precise vblank timestamp query.
[   23.797067] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   23.798874] [drm] initialized overlay support
[   23.878785] device-mapper: multipath: version 1.6.0 loaded
[   24.057962] fbcon: inteldrmfb (fb0) is primary device
[   24.115146] Console: switching to colour frame buffer device 210x65
[   24.131995] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   24.132027] i915 0000:00:02.0: registered panic notifier
[   24.132288] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.133115] snd_intel8x0 0000:00:1e.2: setting latency timer to 64
[   24.193241] microcode: CPU0 sig=0xf41, pf=0x10, revision=0x17
[   24.564094] intel8x0_measure_ac97_clock: measured 53518 usecs (2579 samples)
[   24.564102] intel8x0: clocking to 48000
[   25.011239] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   25.252299] ppdev: user-space parallel port driver
[   25.353520] gpio_ich: ACPI BAR is busy, GPI 0 - 15 unavailable
[   25.353531] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   25.361250] microcode: CPU1 sig=0xf41, pf=0x10, revision=0x17
[   25.474684] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   25.916282] Linux video capture interface: v2.00
[   26.148047] usb 1-4: reset high-speed USB device number 3 using ehci-pci
[   26.410342] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0804)
[   26.424849] input: UVC Camera (046d:0804) as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5
[   26.427821] usbcore: registered new interface driver uvcvideo
[   26.427829] USB Video Class driver (1.1.1)
[   26.697942] usb_audio: Warning! Unlikely big volume range (=6144), cval->res is probably wrong.
[   26.697951] usb_audio: [5] FU [Mic Capture Volume] ch = 1, val = 1536/7680/1<6>[   26.698540] usbcore: registered new interface driver snd-usb-audio
[   48.509429] EXT2-fs (sdc1): warning: mounting unchecked fs, running e2fsck is recommended
[   48.870928] init: failsafe main process (746) killed by TERM signal
[   49.315423] Bluetooth: Core ver 2.16
[   49.315478] NET: Registered protocol family 31
[   49.315483] Bluetooth: HCI device and connection manager initialized
[   49.316272] Bluetooth: HCI socket layer initialized
[   49.316286] Bluetooth: L2CAP socket layer initialized
[   49.316309] Bluetooth: SCO socket layer initialized
[   49.396869] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   49.396877] Bluetooth: BNEP filters: protocol multicast
[   49.396895] Bluetooth: BNEP socket layer initialized
[   49.423959] Bluetooth: RFCOMM TTY layer initialized
[   49.423990] Bluetooth: RFCOMM socket layer initialized
[   49.423995] Bluetooth: RFCOMM ver 1.11
[   49.717039] type=1400 audit(1394107003.251:8): apparmor="STATUS" operation="profile_load" parent=861 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=868 comm="apparmor_parser"
[   49.717059] type=1400 audit(1394107003.251:9): apparmor="STATUS" operation="profile_load" parent=861 profile="unconfined" name="chromium_browser" pid=868 comm="apparmor_parser"
[   49.717368] type=1400 audit(1394107003.251:10): apparmor="STATUS" operation="profile_load" parent=861 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=869 comm="apparmor_parser"
[   49.717385] type=1400 audit(1394107003.251:11): apparmor="STATUS" operation="profile_load" parent=861 profile="unconfined" name="chromium_browser" pid=869 comm="apparmor_parser"
[   49.718619] type=1400 audit(1394107003.251:12): apparmor="STATUS" operation="profile_replace" parent=861 profile="unconfined" name="chromium_browser" pid=868 comm="apparmor_parser"
[   49.723005] type=1400 audit(1394107003.255:13): apparmor="STATUS" operation="profile_replace" parent=861 profile="unconfined" name="chromium_browser" pid=869 comm="apparmor_parser"
[   49.726905] type=1400 audit(1394107003.259:14): apparmor="STATUS" operation="profile_load" parent=861 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=870 comm="apparmor_parser"
[   49.726928] type=1400 audit(1394107003.259:15): apparmor="STATUS" operation="profile_load" parent=861 profile="unconfined" name="chromium_browser" pid=870 comm="apparmor_parser"
[   49.730195] type=1400 audit(1394107003.263:16): apparmor="STATUS" operation="profile_replace" parent=861 profile="unconfined" name="chromium_browser" pid=870 comm="apparmor_parser"
[   49.753644] type=1400 audit(1394107003.287:17): apparmor="STATUS" operation="profile_load" parent=861 profile="unconfined" name="/usr/bin/evince" pid=872 comm="apparmor_parser"
[   49.972521] init: avahi-cups-reload main process (878) terminated with status 1
[   50.918474] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.919523] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.506089] tg3 0000:40:00.0 eth0: Link is up at 1000 Mbps, full duplex
[   54.506107] tg3 0000:40:00.0 eth0: Flow control is on for TX and on for RX
[   54.506136] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   54.711831] Non-volatile memory driver v1.3
[   55.487178] WARNING! power/level is deprecated; use power/control instead
[   55.647263] usblp 2-1:1.0: usblp1: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x6104
[   55.647332] usbcore: registered new interface driver usblp
[   55.977511] init: plymouth-stop pre-start process (1575) terminated with status 1
[   79.628493] ata4.00: configured for UDMA/133
[   79.628511] ata4: EH complete
[  573.247458] audit_printk_skb: 144 callbacks suppressed
[  573.247473] type=1400 audit(1394107526.778:66): apparmor="STATUS" operation="profile_replace" parent=3483 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3487 comm="apparmor_parser"
[  573.247510] type=1400 audit(1394107526.778:67): apparmor="STATUS" operation="profile_replace" parent=3483 profile="unconfined" name="/usr/sbin/cupsd" pid=3487 comm="apparmor_parser"
[  573.249768] type=1400 audit(1394107526.782:68): apparmor="STATUS" operation="profile_replace" parent=3483 profile="unconfined" name="/usr/sbin/cupsd" pid=3487 comm="apparmor_parser"
[ 1474.345800] hud-service[2170]: segfault at 0 ip 0806b6e3 sp bfa63720 error 4 in hud-service[8048000+47000]
[ 1784.267291] systemd-hostnamed[4202]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 4507.982850] systemd-hostnamed[5143]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[38340.147745] systemd-hostnamed[8303]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[41803.547614] systemd-hostnamed[8520]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[43303.940127] usb 5-1: USB disconnect, device number 2
[43319.308060] usb 5-1: new low-speed USB device number 5 using uhci_hcd
[43319.478996] usb 5-1: New USB device found, idVendor=1bcf, idProduct=053e
[43319.479007] usb 5-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[43319.479014] usb 5-1: Product: 2.4GHz 2way RF Receiver
[43319.517559] input: 2.4GHz 2way RF Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input6
[43319.519771] hid-generic 0003:1BCF:053E.0004: input,hiddev0,hidraw0: USB HID v1.00 Mouse [2.4GHz 2way RF Receiver] on usb-0000:00:1d.3-1/input0
```

---

### Post by EZZ9 on 2014-03-06
It's a tower and I turn it off the right way.
I also see on mouse setting. The pointer speed setting is gone? I just got a new mouse and wanted to make it a little faster. the setting use to be there?

---

### Post by sammiev on 2014-03-06
You will need to edit your sources and remove this line. Then update again.

```
W: Failed to fetch http://ppa.launchpad.net/shnatsel/zr...
```

---

### Post by ibjsb4 on 2014-03-06
As sammiev said.

You have two "Err 404" and should be able to remove them from your software sources.

Zram - No saucy package
[http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/](http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/)
and
[http://ppa.launchpad.net/](http://ppa.launchpad.net/)
Which seems to be an incomplete address.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Then try another update.  If it updates without errors, then try an upgrade.
```
sudo apt-get upgrade
```

If further help is needed with this, please post the output of:
```
ls /etc/apt/sources.list.d
```

---

### Post by EZZ9 on 2014-03-09
Looked all over the web can't find where to go Again, sources?

---

### Post by EZZ9 on 2014-03-09
Where do I find "sources"  how do I get there? And remove the lines from?

---

### Post by EZZ9 on 2014-03-09
I found this listing on how to add ppa things but it's 3 years old (so I don't trust it)  I did followed it went to "software & updates" then to "other software" and found a list but [URL="http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/"]http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/
&     [/URL][http://ppa.launchpad.net/]("http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/")[URL="http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/"] 
are not there the closest one I can find there is 
 [/URL][http://ppa.launchpad.net/shnatsel/zram/ubuntu saucy]("http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/")[URL="http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/"]
so I think I'm in the  wrong places once again, will wait till someone can tell me where to go
[/URL]

---

### Post by panorain on 2014-03-09
sources.list is in /etc/apt/ you can use the terminal to get there by command:

> cd /etc/apt

then look at what is in the directory with command:

> ls -lah

then you can edit the sources.list file with gedit 

> gedit sources.list

Or you could use 'synaptic package manager' to edit your repository list but be careful!

---

### Post by EZZ9 on 2014-03-10
got this 
bob@bob-desktop:~$ cd /etc/apt 
bob@bob-desktop:/etc/apt$ ls -lah
total 80K
drwxr-xr-x   6 root root 4.0K Mar  9 19:39 .
drwxr-xr-x 163 root root  12K Mar  9 20:37 ..
drwxr-xr-x   2 root root 4.0K Mar  6 17:03 apt.conf.d
drwxr-xr-x   2 root root 4.0K Apr 20  2012 preferences.d
-rw-r--r--   1 root root 3.1K Mar  9 20:31 sources.list
drwxr-xr-x   2 root root 4.0K Mar  9 20:31 sources.list.d
-rw-r--r--   1 root root 3.1K Feb 21 14:07 sources.list.distUpgrade
-rw-r--r--   1 root root 3.1K Mar  9 20:31 sources.list.save
-rw-------   1 root root 1.2K Mar  5 23:31 trustdb.gpg
-rw-r--r--   1 root root  14K Feb 24 22:21 trusted.gpg
-rw-r--r--   1 root root  13K Feb 21 03:21 trusted.gpg~
drwxr-xr-x   2 root root 4.0K Mar  9 19:39 trusted.gpg.d
bob@bob-desktop:/etc/apt$ 

then put this in   "gedit sources.list"
got a mile long list of
(gedit:11454): Gtk-WARNING **: GtkScrolledWindow 0x91f2478 is mapped but visible child GtkScrollbar 0x91f38b0 is not mapped


Another window opened with this and the lines are not there to take out????
So I hit the wall again. Don't know what to do.

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main

---

### Post by ibjsb4 on 2014-03-10
> **EZZ9 said:**
> Where do I find "sources"  how do I get there? And remove the lines from?

> **EZZ9 said:**
> Looked all over the web can't find where to go Again, sources?

I don't understand.  The link is right there in post#10.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Maybe you cannot find it in your system?  The terminal command for it:

```
software-properties-gtk

```
Then go to the "Other Software" tab.

---

### Post by EZZ9 on 2014-03-10
Found this on the web downloaded it. Hit yes, when it's asked to delete the bad PPA and it worked! Pass it on.

I've written a quick script that checks for PPAs and Software-Sources that exhibit the 404 errors.    It's in my PPA:
  sudo add-apt-repository ppa:fossfreedom/packagefixes
sudo apt-get update
sudo apt-get install banish404
  You can just download the deb package and install that directly:
  wget [https://launchpad.net/~fossfreedom/+archive/packagefixes/+files/banish404_0.1-4_all.deb](https://launchpad.net/~fossfreedom/+archive/packagefixes/+files/banish404_0.1-4_all.deb)
sudo dpkg -i banish404_0.1-4_all.deb
  N.B. its the same deb package for all distributions.
  Questions/Comments/Improvement please via [Launchpad Contact Me link]("https://launchpad.net/%7Efossfreedom")
  How to use:
  sudo banish404
  The script will automatically backup of your sources before modification - to be found in /etc/apt
  Here is a bug report on the update manager to solve this problem:

---

