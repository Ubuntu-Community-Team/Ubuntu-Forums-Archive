---
title: "iCal Reminders in GNOME"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by dwitkin on 2008-07-12
Hello. I'm hoping a smart Ubuntu user can help me.

I've been using Evolution for about 4 months now and it isn't working well for me. I'm in the process of moving to KOrganizer and the Kontact suite which I like much better, but I've noticed that the calendar alarm reminders I setup in KOrganizer don't work. From what I've read, it looks like the Evolution Data Server (EDS) is responsible for querying Evolution data and sending the calendar information to the GNOME clock applet. The GNOME clock applet actually shows the calendar alarm reminder on the desktop.

I'd like to find a way to continue using KOrganizer but have still have GNOME display alarms, just like it did when I used Evolution.

As one possible solution, it appears that I could write a shell script to copy my KOrganizer iCal file and overwrite the Evolution iCal file. Then, I'd setup the script to run via CRON every 10 minutes or something. The cron job would also need to shutdown all evolution components ("evolution --force-shutdown") and wait to make sure it is done before executing the iCal file copy. I think that would do the trick, but it seems a little convoluted and I don't yet know how to write a shell script or schedule it via cron.

Any suggestions? Or can someone walk me through the shell script and cron scheduling process? 

Thanks,
Dave

---

