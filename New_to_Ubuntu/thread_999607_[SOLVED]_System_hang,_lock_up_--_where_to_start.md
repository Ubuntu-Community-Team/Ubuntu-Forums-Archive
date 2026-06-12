---
title: "[SOLVED] System hang, lock up -- where to start"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Chachee on 2008-12-02
Hey all,
  Been having my workstation lock up a lot.  I'm trying to track down what could be the cause but don't know where to start.  Looked at the logs in System-> Admin -> System Logs.  The last hang, which all require a hard restart has this in the message, kernel, and syslog logs.

```
Dec  2 08:18:28 jeremy-desktop kernel: [80141.408216] usb-storage: device scan complete
Dec  2 08:18:28 jeremy-desktop kernel: [80141.409178] scsi 17:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.410054] scsi 17:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.410928] scsi 17:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.413065] scsi 17:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.456361] sd 17:0:0:0: [sdb] Attached SCSI removable disk
Dec  2 08:18:28 jeremy-desktop kernel: [80141.456789] sd 17:0:0:0: Attached scsi generic sg2 type 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.458662] sd 17:0:0:1: [sdc] Attached SCSI removable disk
Dec  2 08:18:28 jeremy-desktop kernel: [80141.459235] sd 17:0:0:1: Attached scsi generic sg3 type 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.466372] sd 17:0:0:2: [sdd] Attached SCSI removable disk
Dec  2 08:18:28 jeremy-desktop kernel: [80141.466776] sd 17:0:0:2: Attached scsi generic sg4 type 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.469504] sd 17:0:0:3: [sde] Attached SCSI removable disk
Dec  2 08:18:28 jeremy-desktop kernel: [80141.470103] sd 17:0:0:3: Attached scsi generic sg5 type 0
Dec  2 08:18:29 jeremy-desktop kernel: [80142.176086] usb 5-2: reset high speed USB device using ehci_hcd and address 16
Dec  2 08:21:07 jeremy-desktop syslogd 1.5.0#2ubuntu6: restart.
```

However, I don't think this is the cause as I didn't have those before and I still got the restarts.  It seems like it'll lock up when I'm messing with youtube/amarok or music/video, but not always.  Very intermittent, but worse than I've had on any other system.

Thanks in advance, I know this is a long shot thing.

JT

---

### Post by nakama85 on 2008-12-02
> **Chachee said:**
> Hey all,
  Been having my workstation lock up a lot.  I'm trying to track down what could be the cause but don't know where to start.  Looked at the logs in System-> Admin -> System Logs.  The last hang, which all require a hard restart has this in the message, kernel, and syslog logs.

```
Dec  2 08:18:28 jeremy-desktop kernel: [80141.408216] usb-storage: device scan complete
Dec  2 08:18:28 jeremy-desktop kernel: [80141.409178] scsi 17:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.410054] scsi 17:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.410928] scsi 17:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.413065] scsi 17:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.456361] sd 17:0:0:0: [sdb] Attached SCSI removable disk
Dec  2 08:18:28 jeremy-desktop kernel: [80141.456789] sd 17:0:0:0: Attached scsi generic sg2 type 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.458662] sd 17:0:0:1: [sdc] Attached SCSI removable disk
Dec  2 08:18:28 jeremy-desktop kernel: [80141.459235] sd 17:0:0:1: Attached scsi generic sg3 type 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.466372] sd 17:0:0:2: [sdd] Attached SCSI removable disk
Dec  2 08:18:28 jeremy-desktop kernel: [80141.466776] sd 17:0:0:2: Attached scsi generic sg4 type 0
Dec  2 08:18:28 jeremy-desktop kernel: [80141.469504] sd 17:0:0:3: [sde] Attached SCSI removable disk
Dec  2 08:18:28 jeremy-desktop kernel: [80141.470103] sd 17:0:0:3: Attached scsi generic sg5 type 0
Dec  2 08:18:29 jeremy-desktop kernel: [80142.176086] usb 5-2: reset high speed USB device using ehci_hcd and address 16
Dec  2 08:21:07 jeremy-desktop syslogd 1.5.0#2ubuntu6: restart.
```

However, I don't think this is the cause as I didn't have those before and I still got the restarts.  It seems like it'll lock up when I'm messing with youtube/amarok or music/video, but not always.  Very intermittent, but worse than I've had on any other system.

Thanks in advance, I know this is a long shot thing.

JT

I would guess it is a problem with Flash then.. Have you tried to reinstall it?

Do you have restricted drivers activated?

---

### Post by Chachee on 2008-12-03
Did a reinstall via synaptic.  Still hung about an hour or 2 later.  Had Amarok, Firefox (5 tabs), and screenlets with 4 items running.

I do have restricted drivers.  The fglrx for ATI.

JT

---

### Post by Chachee on 2008-12-04
Still hangs.
  Will do it when I've got 2 tabs, or 11 tabs open in firefox.  There seems to be no definite program I can nail it down to.  I'll restart and re-load the session that I had and everything will be fine.  


  Comp was on for most of the day and the wife watched a movie on it fine.  Then I went to a forum and it hung.

---

### Post by Chachee on 2008-12-05
Doesn't seem to be following any trend I can find.  Is there some system wide log I can turn on to monitor everything?  Very annoying, and I'm sure there's something I can do.

THanks.

JT

---

### Post by iponeverything on 2008-12-06
I had a problem under hardy, when I had high traffic over my wireless link the machine would lock. I was able to fix it by installing module backports. 

If your running hardy try:

```
sudo apt-get install linux-backports-modules-`uname -r`
```

---

### Post by Chachee on 2008-12-06
Thanks for the reply.

I'm not running Hardy, I'm on 8.10.  I went ahead and uninstalled my restricted drivers since it was kinda mentioned above.  I haven't had a hang yet, and I've run my machine through some paces.  I'm going to try a few more things before I mark it as solved though.

---

### Post by Chachee on 2008-12-06
Went through and did all the things that were hanging before with no probs.  Seems the restricted drivers were the prob, just a guess, and I don't even need them to run compiz, emerald, and BSFlag.

JT

---

