---
title: "Missing section in Exported Ubuntu 20.04 System Log"
date: 2023-03-27
forum: New to Ubuntu
---

### Post by bhubunt on 2023-03-27
Hi, 
I use Gnome Logs and then export the log when necessary to a file.

Just now, though, I noticed that a section of the log I was interested in and had also made a screenshot of is missing in the exported file.

The missing section deals with a glitch at 17:26:44 or 5:26:44 PM

Here is the full log [https://pastebin.com/AjvCdeQT](https://pastebin.com/AjvCdeQT)

And here is the missing section from 17:26:44

```
 17:27:45 snap-store: not handling error failed for action refine: Failed to write to snapd: Operation was cancelled 
17:27:45 snap-store: not handling error failed for action refine: Failed to write to snapd: Operation was cancelled 
17:26:45 snap-store: FIXME: Unknown progress handling is not yet implemented for GsProgressButton 
17:26:45 snap-store: FIXME: Unknown progress handling is not yet implemented for GsProgressButton 
17:26:45 snap-store: FIXME: Unknown progress handling is not yet implemented for GsProgressButton 
17:26:45 snap-store: FIXME: Unknown progress handling is not yet implemented for GsProgressButton 
17:26:44 snap-store: not handling error failed for action get-category-apps: persistent network error: Get https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=games-featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Clinks%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel: dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution 
17:26:44 snap-store: not handling error failed for action get-categories: status-code=500 kind=(null) message=persistent network error: Get https://api.snapcraft.io/api/v1/snaps/sections: dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution 
17:26:44 snap-store: not handling error failed for action get-category-apps: persistent network error: Get https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=audio-video-featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Clinks%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel: dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution 
17:26:44 snap-store: not handling error failed for action get-popular: persistent network error: Get https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Clinks%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel: dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution 
17:26:12 snap-store: not handling error no-network for action refresh: Cannot refresh cache whilst offline 
17:26:02 systemd: Reached target GNOME Wacom handling. 
17:26:02 kernel: rfkill: input handler disabled 
17:26:02 systemd: Reached target GNOME Sharing handling. 
17:25:59 Xorg: Kernel command line: BOOT_IMAGE=/vmlinuz-5.15.0-67-generic root=/dev/mapper/vgubuntu-root ro quiet splash vt.handoff=7 
17:25:59 kernel: rfkill: input handler enabled 
17:25:40 networkd-dispat:   File "/usr/bin/networkd-dispatcher", line 348, in handle_state 
17:25:30 kernel: IPI shorthand broadcast: enabled 
17:25:30 kernel: ACPI: \_SB_.PCI0.LPC_.EC__: EC: Used to handle transactions and events 
17:25:30 kernel: Kernel command line: BOOT_IMAGE=/vmlinuz-5.15.0-67-generic root=/dev/mapper/vgubuntu-root ro quiet splash vt.handoff=7 
17:25:30 kernel: Command line: BOOT_IMAGE=/vmlinuz-5.15.0-67-generic root=/dev/mapper/vgubuntu-root ro quiet splash vt.handoff=7 
```

[https://pastebin.com/WXNDtC3k](https://pastebin.com/WXNDtC3k)

And here is the screenshot (on the left) that I made before exporting this log to a text file (from which the section went missing...)

---

