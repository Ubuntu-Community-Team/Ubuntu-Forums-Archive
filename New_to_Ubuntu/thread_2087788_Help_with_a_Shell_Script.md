---
title: "Help with a Shell Script"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by ACagliano on 2012-11-24
I am trying to write a shell script (.sh) to search the log files for  any occurrences of entries with the tags "attackalert" or "UFW BLOCK".  The following is an excerpt of what I have worked out:

   ```
  #!/bin/bash  tail -f /var/log/messages | grep "attackalert\|UFW BLOCK" | xargs -I {} dialog --ascii-lines --infobox "PortSentry  Alert: The system logs indicate one or more port scans were launched  against this computer since this script was last executed. See [the log]  for details.\n" 7 80 
```Some other things of note: This script gets executed with root  privileges. It runs as a cron job, every 15 minutes. My goal is, if the  grep command returns results, a pop-up on the screen displays the text  that I tried to display with "dialog". It seems that dialog only invokes  the terminal for a GUI, and if no terminal window is open, it doesn't show  anything. Help?

PS: I apologize. I posted a duplicate of this topic in the "Specialized Support" then got the feeling it was in the wrong place. Heck, it still may be. An admin can delete the other one. :)

---

### Post by papibe on 2012-11-24
Hi ACagliano.

A few thoughts:

The option '-f' is for a more permanent process running on the ground rather than a crontab script.

As the crontab environment is very limited, you have to define the DISPLAY variable in order to run GUI apps. Check the section 'GUI Applications' in this [tutorial]("https://help.ubuntu.com/community/CronHowto") for more details.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by The Cog on 2012-11-24
That needs to be split into two lines. As a single line, it is merely a long comment line and there is nothing to execute.

I suspect that you need to specify which display to pop the window onto. Try this (inserted extra line):
```
#!/bin/bash  
export DISPLAY=:0.0
tail -f /var/log/messages | grep "attackalert\|UFW BLOCK" | xargs -I {} dialog --ascii-lines --infobox "PortSentry  Alert: The system logs indicate one or more port scans were launched  against this computer since this script was last executed. See [the log]  for details.\n" 7 80
```

P.S.
Oops, I didn't notice the "-f" on tail (as papibe did). That's bad because it's a never-ending process. And with crontab, you would start another such process every 15 minutes until you had hundreds or thousands of them running.

---

### Post by ACagliano on 2012-11-24
Yes, I removed the -f argument. I realized that as well. That must be an older version of my script. Here is the one that I have up now, but there's the issue with rendering the GUI.

```
#!/bin/bash

tail -n 50 /var/log/syslog | grep 'attackalert\|UFW BLOCK' | xargs -I {} dialog --ascii-lines --title "Security Alert" --msgbox "The system logs indicate one or more port scans were launched against this computer since this script was last executed. See '/var/log/syslog' for details.\n" 7 80
```

I'll have a look at the tutorial and post back. Thanks.

Edit: The addition of the "export DISPLAY=:0.0" line (those are zero's right?) had no effect. Still no display on execution. And I deliberately portscanned just before the cron ran, so make sure it displayed.

---

