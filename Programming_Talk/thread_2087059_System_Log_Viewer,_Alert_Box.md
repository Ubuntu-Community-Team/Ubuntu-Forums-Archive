---
title: "System Log Viewer, Alert Box"
date: 2012-11-22
forum: Programming Talk
---

### Post by ACagliano on 2012-11-22
I am trying to write a shell script (.sh) to search the log files for any occurrences of entries with the tags "attackalert" or "UFW BLOCK". The following is an excerpt of what I have worked out:

```
#!/bin/bash

tail -f /var/log/messages | grep "attackalert\|UFW BLOCK" | xargs -I {} dialog --ascii-lines --infobox "PortSentry  Alert: The system logs indicate one or more port scans were launched  against this computer since this script was last executed. See [the log]  for details.\n" 7 80
```Some other things of note: This script gets executed with root privileges. It runs as a cron job, every 15 minutes. My goal is, if the grep command returns results, a pop-up on the screen displays the text that I tried to display with "dialog". It seems that dialog only invokes the terminal for a GUI, and if one is not found, it doesn't show anything. Help?

---

