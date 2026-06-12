---
title: "Programming machine to bootup and shutdown at set times and days"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by JustGus on 2008-08-01
Hi,

I've bought a low power consumption machine and am using it as media server.  Is there a way I can program it to automatically bootup and shutdown at certain times and on certain days.  I've had a look around for a tweak app (e.g. webmin, or Ubuntu Tweak) that does this easily, but had no luck.  Alternatively could do a command line instruction (although a tweak app would be preferable!).
Thanks,
Gus

---

### Post by Bigbob22 on 2008-08-01
I think you can make a script for that, but I don't know how. I'm sure someone else here can help you out.

---

### Post by sonofusion82 on 2008-08-01
you can probably use cron job to powerdown using "shutdown -h now"
for powering-up, i believe you might need bios support, i have seen some motherboard bios that have an automatic power-on timer settings. alternatively, you may try setting up the server for Wakeup-On-Lan (WOL) where you can power-up the server with a special magic packet sent to the machine but i have no prior experience on this.

---

### Post by chris_nava on 2008-08-01
**You can easily configure your machine to shut down at a given time.**
Adding a "shutdown -P" command to the root crontab would work.
The following cron entry should initiate a shutdown at 10:00 PM with a 5 minute warning.  Note that the warning is displayed on the terminal so you will NOT see the warning if you are only using GUI applications.

sudo crontab -u root -l > cron.txt
echo 0 22 * * * shutdown -P +5 >> cron.txt
sudo crontab -u root cron.txt

**However, booting up is an entirely different matter.**
Since the machine is OFF it can't easily start itself.
Try checking the BIOS settings (hit F2 while booting on most machines) and see if there is an option for automatically powering on the machine at a given time.  There MAY be a way to modify the BIOS settings using a linux application but I don't know it.

---

### Post by JustGus on 2008-08-02
Thanks, Chris and sonofusion.  That's a big help.  Will look into that and thanks for the tip on shutting down.

---

