---
title: "Ubuntu 11.10 stuck on shutdown"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by mayur.shetye on 2012-02-01
I have **Oneric** installed on my PC (using wubi alongside win 7).Initially,I had no problem with shutdown.Since yesterday ubuntu is getting stuck when i try to shut down.It just shows the three dots and an **error message** and then nothing happens.The error is 
"**bin/sh can't access tty job control turned off**"
I googled about it but found out that others are getting this error on start up.I also tried **boot repair**.The log file is at [http://paste.ubuntu.com/825046/](http://paste.ubuntu.com/825046/) .
I had tried two things which I thing could have caused the problem
i)Tried to run **deluge** at startup using a **script** provided on thier site.(FAILED)
ii)Connected my mobile(**memory card**).
Any help would be very much appreciated.

---

### Post by bcbc on 2012-02-01
Check /var/log/syslog for issues/error messages.

Use Alt+SysRq R-E-I-S-U-B to safely reboot rather than get in the habit of powering off as this could eventually cause corruption depending on how it is getting stuck.

Make sure you've run all updates.

---

### Post by mayur.shetye on 2012-02-01
Yes I have installed the updates.
I can't figure out anything from the syslog file and cannot attach it too .. it exceeds the limit. :(

---

### Post by mayur.shetye on 2012-02-01
This is just the starting part of the syslog and syslog.1 files.
```
Feb  1 00:55:53 ubuntu anacron[933]: Job `cron.daily' terminated
Feb  1 00:55:53 ubuntu anacron[933]: Normal exit (1 job run)
Feb  1 00:57:53 ubuntu kernel: [ 2380.640035] usb 2-6: new full speed USB device number 2 using ohci_hcd
Feb  1 00:57:53 ubuntu kernel: [ 2380.824050] usb 2-6: device descriptor read/64, error -62
Feb  1 00:57:53 ubuntu kernel: [ 2381.112033] usb 2-6: device descriptor read/64, error -62
Feb  1 00:57:54 ubuntu kernel: [ 2381.392035] usb 2-6: new full speed USB device number 3 using ohci_hcd
Feb  1 00:57:54 ubuntu kernel: [ 2381.576034] usb 2-6: device descriptor read/64, error -62
Feb  1 00:57:54 ubuntu kernel: [ 2381.864038] usb 2-6: device descriptor read/64, error -62
Feb  1 00:57:55 ubuntu kernel: [ 2382.144037] usb 2-6: new full speed USB device number 4 using ohci_hcd
Feb  1 00:57:55 ubuntu kernel: [ 2382.552026] usb 2-6: device not accepting address 4, error -62
Feb  1 00:57:55 ubuntu kernel: [ 2382.728033] usb 2-6: new full speed USB device number 5 using ohci_hcd
Feb  1 00:57:56 ubuntu kernel: [ 2383.136024] usb 2-6: device not accepting address 5, error -62
Feb  1 00:57:56 ubuntu kernel: [ 2383.136046] hub 2-0:1.0: unable to enumerate USB device on port 6
Feb  1 01:02:54 ubuntu kernel: [ 2681.436034] usb 2-5: new full speed USB device number 6 using ohci_hcd
Feb  1 01:02:54 ubuntu mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:02.0/usb2/2-5"
Feb  1 01:02:54 ubuntu mtp-probe: bus: 2, device: 6 was not an MTP device
Feb  1 01:02:55 ubuntu kernel: [ 2682.438472] cdc_acm 2-5:2.3: ttyACM0: USB ACM device
Feb  1 01:02:55 ubuntu kernel: [ 2682.444489] usbcore: registered new interface driver cdc_acm
Feb  1 01:02:55 ubuntu kernel: [ 2682.444495] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
Feb  1 01:02:55 ubuntu kernel: [ 2682.452073] usbcore: registered new interface driver uas
Feb  1 01:02:55 ubuntu kernel: [ 2682.461820] usbcore: registered new interface driver cdc_ether
Feb  1 01:02:55 ubuntu kernel: [ 2682.485325] Initializing USB Mass Storage driver...
Feb  1 01:02:55 ubuntu kernel: [ 2682.485486] scsi4 : usb-storage 2-5:2.5
Feb  1 01:02:55 ubuntu kernel: [ 2682.486090] usbcore: registered new interface driver usb-storage
Feb  1 01:02:55 ubuntu kernel: [ 2682.486095] USB Mass Storage support registered.
Feb  1 01:02:55 ubuntu kernel: [ 2682.509258] usb 2-5: bad CDC descriptors
Feb  1 01:02:55 ubuntu kernel: [ 2682.509301] usbcore: registered new interface driver rndis_host
Feb  1 01:02:55 ubuntu kernel: [ 2682.582574] cfg80211: Calling CRDA to update world regulatory domain
Feb  1 01:02:55 ubuntu kernel: [ 2682.651378] usb 2-5: bad CDC descriptors
Feb  1 01:02:55 ubuntu kernel: [ 2682.651456] usbcore: registered new interface driver rndis_wlan
Feb  1 01:02:55 ubuntu modem-manager[842]: <info>  (ttyACM0) opening serial port...
Feb  1 01:02:55 ubuntu kernel: [ 2682.808290] cfg80211: World regulatory domain updated:
Feb  1 01:02:55 ubuntu kernel: [ 2682.808297] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb  1 01:02:55 ubuntu kernel: [ 2682.808301] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  1 01:02:55 ubuntu kernel: [ 2682.808304] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
```

```
Jan 31 00:39:41 ubuntu anacron[923]: Job `cron.daily' terminated
Jan 31 00:39:41 ubuntu anacron[923]: Normal exit (1 job run)
Jan 31 01:04:29 ubuntu kernel: [ 2861.539784] init: tty4 main process (899) killed by TERM signal
Jan 31 01:04:29 ubuntu kernel: [ 2861.543293] init: tty5 main process (904) killed by TERM signal
Jan 31 01:04:29 ubuntu kernel: [ 2861.546590] init: tty2 main process (913) killed by TERM signal
Jan 31 01:04:29 ubuntu kernel: [ 2861.549855] init: tty3 main process (914) killed by TERM signal
Jan 31 01:04:29 ubuntu kernel: [ 2861.554081] init: tty6 main process (916) killed by TERM signal
Jan 31 01:04:29 ubuntu kernel: [ 2861.571088] init: cron main process (926) killed by TERM signal
Jan 31 01:04:29 ubuntu kernel: [ 2861.583577] init: tty1 main process (1172) killed by TERM signal
Jan 31 01:04:29 ubuntu kernel: Kernel logging (proc) stopped.
Jan 31 01:04:29 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="810" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan 31 08:11:42 ubuntu kernel: imklog 5.8.1, log source = /proc/kmsg started.
```

---

### Post by bcbc on 2012-02-01
You can try compressing the syslog and attach that, or... 
attempt to shutdown. When it hangs try to get to a terminal Ctrl+Alt+F1 and run: 
```
tail -n 100 /var/log/syslog 
```

See if that shows some error.

PS. I assume you've removed the (mobile) memory card now. Or is that still attached?

---

### Post by mayur.shetye on 2012-02-02
Yes,I have removed my memory card now. Also,I cant access the terminal using ctrl+alt+T during shutdown :(. Another thing is that the error messages during shutdown have changed now.Now it is like this
```

**fsck** from util_linux 2.19.1
/dev/loop: clean, 194518/431632 files,1149572/1726464 blocks(check in **5 mounts**)
**Skipping profile** in /etc/apparmor.d/disable :usr.bin.**firefox**
*Starting **AppArmor** profiles
**bin/sh: can't acess tty:job control turned off**
#**acpid:exiting**
bin/sh: can't acess tty:job control turned off

#[240.316073] INFO: task **Xorg**:964 blocked for more than 120 seconds

```

---

### Post by bcbc on 2012-02-02
I can't believe that trying to install deluge would cause problems. Also the memory card might have caused an issue when plugged in (perhaps) but shouldn't be lasting.

Therefore, I'd boot a live CD, fsck the root.disk. You could also run 'chkdsk /r' on windows to be safe (won't hurt).

If that fails to do anything, I'm not sure what I'd do. I've had installs in the past that would freeze on shutdown, in which case I just use REISUB to at least ensure that no damage would be done.

If nothing works, try to compress and upload the log.

---

### Post by mayur.shetye on 2012-02-02
I switched back to Ubuntu 10.04 :) Just could not deal with the issue anymore! Thanks a lot for helping though :)

---

