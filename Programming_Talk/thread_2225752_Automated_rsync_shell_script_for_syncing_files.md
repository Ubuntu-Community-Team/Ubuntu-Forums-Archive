---
title: "Automated rsync shell script for syncing files"
date: 2014-05-23
forum: Programming Talk
---

### Post by venkatramsam on 2014-05-23
Hey guys! I am writing an rsync script to automatically sync music between my computer and a portable media device. I need some help in improvising it :) .
Assumtion: All scipts are chmod'ed to execute.
This is the code that I used: walkman_sync.sh :
```
rsync -avrh --progress --exclude-from=/home/venkat/Music/walkman_exclude /home/venkat/Music/ /media/WALKMAN/MUSIC/
```
To invoke this script whenever the device is plugged in, I added a udev rule.
/etc/udev/85-walkman-sync.rules:
```
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0404", RUN+="/usr/bin/walkman_sync_relay.sh"
```

The thing with udev that I observed was that it runs the script after the device is plugged in before actually mounting the device. So udev runs a relay script that calls the acutal script and exits so, when the actual script that uses rsync is executed, the device is mounted in its place.

walkman_sync_relay.sh:
```
#!/bin/bash
/home/venkat/Desktop/scripts/devices/walkman_sync.sh & exit
```

walkman_sync.sh
```
#!/bin/bash
sleep 5
rsync -avrh --progress --exclude-from=/home/venkat/Music/walkman_exclude /home/venkat/Music/ /media/WALKMAN/MUSIC/

```

The syncing runs properly in the background when the device is plugged in. However, owing to the size of my music collection the process takes about 20mins.
Now coming to the problem,
**MY QUESTION: **
1- Is it possible to modify the script to run the rsync command in an open terminal when the device is plugged in so that I can keep track of what files are being synced with the progress.
Note: I tried the following but it didn't work.
walkman_sync.sh: ```
#!/bin/bash
sleep 5
gnome-terminal -e rsync -avrh --progress --exclude-from=/home/venkat/Music/walkman_exclude /home/venkat/Music/ /media/WALKMAN/MUSIC/

```
I don't think the rsync command was executed as the files didn't sync. I got this error message in the terminal:
Failed to parse arguments: Unknown option -avrh

I am a beginner at shell scripting, please do help me out on this one! :)

---

### Post by Lars Noodén on 2014-05-23
Try it with quotes.

```

gnome-terminal -e "rsync -avrh --progress --exclude-from=/home/venkat/Music/walkman_exclude /home/venkat/Music/ /media/WALKMAN/MUSIC/"

```
 
rsync, and all its options, needs to get passed to gnome-terminal as a single unit.  Otherwise, it will act that -avrh, --progress, etc applies to it  rather than to rync.   

Also, -avrh might be -avh instead.  The [-r is already part of -a](http://manpages.ubuntu.com/manpages/trusty/en/man1/rsync.1.html).

---

### Post by venkatramsam on 2014-05-23
Your solution works only when I run it manually.

---

### Post by steeldriver on 2014-05-23
I don't think the udev environment is going to have any knowledge of your desktop session. At a minimum your script would need to set an appropriate DISPLAY variable - that may not be enough though.

In general I try to avoid system processes that rely on a particular user's sessions or files being available. Since the device is being automounted in your desktop session via udisks, probably the *right* way to do it is via a udisks-glue post_mount_command (DISCLAIMER: I have never tried this!!)

[http://manpages.ubuntu.com/manpages/raring/en/man5/udisks-glue.conf.5.html](http://manpages.ubuntu.com/manpages/raring/en/man5/udisks-glue.conf.5.html)

---

