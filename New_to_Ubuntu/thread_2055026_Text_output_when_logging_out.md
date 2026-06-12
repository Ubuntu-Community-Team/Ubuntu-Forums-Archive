---
title: "Text output when logging out"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by DGINSD on 2012-09-08
I noticed when I log out lately there's a console print out right before I'm put back to the login screen, It's very quick, too quick to get much idea what it actually is, but the first line starts out 

```
could not write bytes: Broken Pipes
```

Which doesn't sound too good. Then there's about 12 more lines with other stuff, but as I said it goes way too fast to find your place and start reading.

So my question is this is there any way to freeze the screen to give me enough time to read the output, or is there anywhere this output might be printed? I've tried looking in a few log files but haven't found anything thus far.

I've though that maybe this is the output from tty7 behind the X session but I don't know how to check to see

---

### Post by shadedpixel on 2012-09-09
> **DGINSD said:**
> I noticed when I log out lately there's a console print out right before I'm put back to the login screen, It's very quick, too quick to get much idea what it actually is, but the first line starts out 

```
could not write bytes: Broken Pipes
```

Which doesn't sound too good. Then there's about 12 more lines with other stuff, but as I said it goes way too fast to find your place and start reading.

So my question is this is there any way to freeze the screen to give me enough time to read the output, or is there anywhere this output might be printed? I've tried looking in a few log files but haven't found anything thus far.

I've though that maybe this is the output from tty7 behind the X session but I don't know how to check to see

Paste the contents of the files in your /var/logs directory

See this guide here should you need any help, [http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/).

---

### Post by Bashing-om on 2012-09-09
DGINSD; 


  I have a method that works in 10.04 / Have not tried it on 12.04 ..If I have the time this night I will implement it and see.

 The method involves editing /etc/default/grub
make a backup of the grub file ---just in case of whatever happens
delete quiet and splash from the grub command line within the grub file
save the file with the changes
in terminal run
```
sudo update-grub
```

on my system I can pause the text output by the scroll lock key, some advise the esc key works for them.

  If you want to do this and require assistance, please ask.

[INDENT]regards <==BDQ 
[/INDENT]

---

### Post by Bashing-om on 2012-09-09
My last is verified on 12.04 .... it works on my system.

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by DGINSD on 2012-09-10
> **shadedpixel said:**
> Paste the contents of the files in your /var/logs directory

See this guide here should you need any help, [http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/).

Which file there's a ton of 'em?

---

### Post by Frogs Hair on 2012-09-10
A broken pipe is a communication failure . since it occurs at log out you may want check the auth.log or the Xorg log in the log file viewer. Without the entire message it's hard to pin down.

---

### Post by DGINSD on 2012-09-10
> **Bashing-om said:**
> DGINSD; 


  I have a method that works in 10.04 / Have not tried it on 12.04 ..If I have the time this night I will implement it and see.

 The method involves editing /etc/default/grub
make a backup of the grub file ---just in case of whatever happens
delete quiet and splash from the grub command line within the grub file
save the file with the changes
in terminal run
```
sudo update-grub
```

on my system I can pause the text output by the scroll lock key, some advise the esc key works for them.

  If you want to do this and require assistance, please ask.

[INDENT]regards <==BDQ 
[/INDENT]

That seemed to change the display time a little bit (the grub edit) but I don't have a scroll lock key and <esc> did nothing.

The output does seem to have changed though it's only about 5 line now instead of 15, it does still start with "could not write bytes: broken pipe"

---

### Post by Bashing-om on 2012-09-10
scroll : unable to advise further.. perhaps some other key to provide the function... or may be able to remap a key to provide that function ???

broken pipes: look through these log files and see if you see a reason:
/var/log/dmesg
/var/log/kern.log
/var/log/syslog

post back to this thread (copy and paste) with what you find informative.

[INDENT]HTH <==BDQ

[/INDENT]

---

### Post by DGINSD on 2012-09-10
Here is the out put of kernel log

```
Sep 10 16:36:08 localhost kernel: [35840.262090] type=1400 audit(1347320168.109:427): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser" name="/etc/mtab" pid=2809 comm="Chrome_FileThre" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Sep 10 16:36:08 localhost kernel: [35840.266126] type=1400 audit(1347320168.113:428): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser" name="/etc/mtab" pid=2809 comm="Chrome_FileThre" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Sep 10 16:36:08 localhost kernel: [35840.460735] [fglrx] IRQ 44 Disabled
Sep 10 16:36:10 localhost kernel: [35843.091682] [fglrx] ATIF platform detected with notification ID: 0x81
Sep 10 16:36:11 localhost kernel: [35843.973464] fglrx_pci 0000:00:01.0: irq 44 for MSI/MSI-X
Sep 10 16:36:11 localhost kernel: [35843.974604] [fglrx] Firegl kernel thread PID: 3538
Sep 10 16:36:11 localhost kernel: [35843.975020] [fglrx] Firegl kernel thread PID: 3539
Sep 10 16:36:11 localhost kernel: [35843.975356] [fglrx] Firegl kernel thread PID: 3540
Sep 10 16:36:11 localhost kernel: [35843.975617] [fglrx] IRQ 44 Enabled
Sep 10 16:36:12 localhost kernel: [35844.206766] [fglrx] Gart USWC size:1072 M.
Sep 10 16:36:12 localhost kernel: [35844.206773] [fglrx] Gart cacheable size:424 M.
Sep 10 16:36:12 localhost kernel: [35844.206783] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Sep 10 16:36:12 localhost kernel: [35844.206789] [fglrx] Reserved FB block: Unshared offset:fca3000, size:35d000 
Sep 10 16:36:12 localhost kernel: [35844.206794] [fglrx] Reserved FB block: Unshared offset:1fff4000, size:c000 

```

And here is the output of system log

```
Sep 10 16:36:08 localhost kernel: [35840.262090] type=1400 audit(1347320168.109:427): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser" name="/etc/mtab" pid=2809 comm="Chrome_FileThre" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Sep 10 16:36:08 localhost kernel: [35840.266126] type=1400 audit(1347320168.113:428): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser" name="/etc/mtab" pid=2809 comm="Chrome_FileThre" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Sep 10 16:36:08 localhost kernel: [35840.460735] [fglrx] IRQ 44 Disabled
Sep 10 16:36:10 localhost acpid: client 1329[0:0] has disconnected
Sep 10 16:36:10 localhost acpid: client connected from 3536[0:0]
Sep 10 16:36:10 localhost acpid: 1 client rule loaded
Sep 10 16:36:10 localhost kernel: [35843.091682] [fglrx] ATIF platform detected with notification ID: 0x81
Sep 10 16:36:11 localhost kernel: [35843.973464] fglrx_pci 0000:00:01.0: irq 44 for MSI/MSI-X
Sep 10 16:36:11 localhost kernel: [35843.974604] [fglrx] Firegl kernel thread PID: 3538
Sep 10 16:36:11 localhost kernel: [35843.975020] [fglrx] Firegl kernel thread PID: 3539
Sep 10 16:36:11 localhost kernel: [35843.975356] [fglrx] Firegl kernel thread PID: 3540
Sep 10 16:36:11 localhost kernel: [35843.975617] [fglrx] IRQ 44 Enabled
Sep 10 16:36:12 localhost kernel: [35844.206766] [fglrx] Gart USWC size:1072 M.
Sep 10 16:36:12 localhost kernel: [35844.206773] [fglrx] Gart cacheable size:424 M.
Sep 10 16:36:12 localhost kernel: [35844.206783] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Sep 10 16:36:12 localhost kernel: [35844.206789] [fglrx] Reserved FB block: Unshared offset:fca3000, size:35d000 
Sep 10 16:36:12 localhost kernel: [35844.206794] [fglrx] Reserved FB block: Unshared offset:1fff4000, size:c000 
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Successfully made thread 3640 of process 3640 (n/a) owned by '104' high priority at nice level -11.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Supervising 5 threads of 2 processes of 2 users.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Successfully made thread 3641 of process 3640 (n/a) owned by '104' RT at priority 5.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Supervising 6 threads of 2 processes of 2 users.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Successfully made thread 3646 of process 3640 (n/a) owned by '104' RT at priority 5.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Supervising 7 threads of 2 processes of 2 users.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Successfully made thread 3648 of process 3640 (n/a) owned by '104' RT at priority 5.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Supervising 8 threads of 2 processes of 2 users.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Successfully made thread 3651 of process 3651 (n/a) owned by '104' high priority at nice level -11.
Sep 10 16:36:14 localhost rtkit-daemon[1932]: Supervising 9 threads of 3 processes of 2 users.
Sep 10 16:36:14 localhost pulseaudio[3651]: [pulseaudio] pid.c: Daemon already running.
Sep 10 16:36:24 localhost goa[3803]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Sep 10 16:36:25 localhost nautilus: [N-A] Nautilus-Actions Tracker 3.2.2 initializing...
Sep 10 16:36:25 localhost nautilus: [N-A] Nautilus-Actions Menu Extender 3.2.2 initializing...
Sep 10 16:36:55 localhost kernel: [35887.991508] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:26:5a:ce:6b:a5:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56352 PROTO=2 
Sep 10 16:37:30 localhost dbus[1028]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Sep 10 16:37:30 localhost AptDaemon: INFO: Initializing daemon
Sep 10 16:37:31 localhost AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Sep 10 16:37:31 localhost dbus[1028]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Sep 10 16:37:31 localhost AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Sep 10 16:37:31 localhost AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/18644a16c7af41b1a97db321b0b7ab8d
Sep 10 16:37:31 localhost AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/18644a16c7af41b1a97db321b0b7ab8d
Sep 10 16:37:31 localhost AptDaemon.PackageKit: INFO: Get updates()
Sep 10 16:37:33 localhost AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/18644a16c7af41b1a97db321b0b7ab8d
```


Both were pulled from the time of logoff. Dmesg doesn't seem to have a timestamp so I have no idea how to determine where to look

---

