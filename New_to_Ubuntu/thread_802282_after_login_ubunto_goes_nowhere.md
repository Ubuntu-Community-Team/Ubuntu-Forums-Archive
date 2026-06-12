---
title: "after login ubunto goes nowhere"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by thenextbond009 on 2008-05-21
I was preforming an upgrade to 8.04 and left the laptop to run that and when I came back it was in sleep mode and it wouldn't come out of it. I left it alone for a while but no change when I rebooted and tried to log back in it asks for the user name and password, but after logging it the background freezes, the mouse will still move so I know the computer isn't frozen but it doesn't boot up at all.

---

### Post by cmnorton on 2008-05-21
You could try the recovery option on grub boot screen, and try to reconfigure your video -- dkpg-reconfigure xserver-xorg taking the defaults except to ask for VGA -- but you don't know for sure it's a video problem. 

You could also try a live cd like Knoppix, mount the drive on which you installed, and look at /var/log/messages and /var/log/syslog.

If you updated, hopefully you backed up before hand. If you did not, Knoppix would allow you to go in an pull things off to a safe place. I had to get the latest version of Knoppix for my Thinkpad T61p, 5.1.1 at the time.

---

