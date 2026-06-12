---
title: "webcam"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by dineshs on 2008-11-18
I am using kubuntu 8.1 and bought a webcam.I dont know how to use the camera.I installed ekiga but it has not detected my camera.Kindly help
The lsusb command gives

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6270 Microdia U-CAM PC Camera NE878
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by spiderbatdad on 2008-11-18
Is there a reason ekiga was not already installed?
Could you unplug the usb cord, then plug it back in. Then run ```
dmesg | tail
```and post the output?

---

### Post by dineshs on 2008-11-18
Ekiga was not found installed in kubuntu.the command output is 
dinesh@dinesh:~$ dmesg | tail
[ 1431.913097] Inbound IN=eth0 OUT= MAC=00:15:f2:30:8e:5b:00:1e:40:00:49:aa:08:00 SRC=69.0.209.22 DST=192.168.1.2 LEN=116 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=UDP SPT=3479 DPT=5061 LEN=96
[ 1432.913053] Inbound IN=eth0 OUT= MAC=00:15:f2:30:8e:5b:00:1e:40:00:49:aa:08:00 SRC=69.0.209.22 DST=192.168.1.2 LEN=116 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=UDP SPT=3479 DPT=5061 LEN=96
[ 1434.268995] Inbound IN=eth0 OUT= MAC=00:15:f2:30:8e:5b:00:1e:40:00:49:aa:08:00 SRC=69.0.208.27 DST=192.168.1.2 LEN=116 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=3479 DPT=5061 LEN=96
[ 1435.264957] Inbound IN=eth0 OUT= MAC=00:15:f2:30:8e:5b:00:1e:40:00:49:aa:08:00 SRC=69.0.208.27 DST=192.168.1.2 LEN=116 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=3479 DPT=5061 LEN=96
[ 1436.266920] Inbound IN=eth0 OUT= MAC=00:15:f2:30:8e:5b:00:1e:40:00:49:aa:08:00 SRC=69.0.208.27 DST=192.168.1.2 LEN=116 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=3479 DPT=5061 LEN=96
[ 1437.263176] Inbound IN=eth0 OUT= MAC=00:15:f2:30:8e:5b:00:1e:40:00:49:aa:08:00 SRC=69.0.208.27 DST=192.168.1.2 LEN=116 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=3479 DPT=5061 LEN=96
[ 1438.262840] Inbound IN=eth0 OUT= MAC=00:15:f2:30:8e:5b:00:1e:40:00:49:aa:08:00 SRC=69.0.208.27 DST=192.168.1.2 LEN=116 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=3479 DPT=5061 LEN=96
[ 2583.942324] usb 1-5: USB disconnect, address 2
[ 2599.808025] usb 1-5: new high speed USB device using ehci_hcd and address 3
[ 2599.946292] usb 1-5: configuration #1 chosen from 1 choice

---

### Post by spiderbatdad on 2008-11-18
hmmm. not exactly what I expected to see. You may need to temporarily disable usb 2.0 to get it to work. try :
```
sudo modprobe -r ehci_hcd
```Then repeat the unplugging/replugging of the cam, and try an application...you may need to reboot. If you must have usb 2.0 re-enable: ```
sudo modprobe ehci_hcd
```

EDIT: ehci_hcd may get reloaded during boot. I'm not sure if sudo rmmod ehci_hcd will solve that...you many also be able to disable usb 2.0 in your bios.

---

### Post by dineshs on 2008-11-18
sir can you explain,because I am a beginner.

---

### Post by spiderbatdad on 2008-11-18
The kernel loads modules to provide functionality to the operating system. I am asking you to try disabling one of the modules that gets loaded. ```
 sudo modprobe -r ehci_hcd 
``` Then try unplugging and replugging your cam again. If it doesn't work, enable the module:```
sudo modprobe ehci_hcd
```and try again. Sometimes removing and adding the modules is enough to fix the problem.

---

### Post by dineshs on 2008-11-18
It didnt help.
During trial and error I had installed easycam2.It displays microdia usb2.0 webcam12.But ekiga says no device found

---

### Post by spiderbatdad on 2008-11-18
during configuration for ekiga did you select v4l2? Good luck. Maybe someone else will chime in. Also search google. Kubuntu may have some bug or workaround necessary.

---

