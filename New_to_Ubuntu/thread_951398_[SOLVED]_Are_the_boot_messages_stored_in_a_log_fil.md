---
title: "[SOLVED] Are the boot messages stored in a log file?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by brucenduane on 2008-10-18
There are many error messages when my system boots and shuts down like invalid configurations and such.

Are these stored in a log file?
If so where is it and how do I look at it?

I have checked System=>Administration=>System Logs
and the messages I am thinking of are not in any of those logs.

The messages scroll off the screen before I can record them.

Thanks.

---

### Post by Pro-reason on 2008-10-18
You can get some by typing “dmesg”.

---

### Post by Kevbert on 2008-10-18
Most of the logs can be found in /var/log. The important ones are dmesg and kern.log which can be viewed with any text editor.  I assume that you've already looked at these.  There is another called .xsessions-errors which is a hidden file in your home directory.  You can view hidden files in Nautilus by hitting Ctrl-H.

---

### Post by brucenduane on 2008-10-18
I have looked at all the logs in /var/log.

I looked at dmesg and it does not have the error messages that I saw during boot.  Where are the messages stored that dmesg prints out?

I found the message in /var/log/syslog

It is: 
gdm[6028] GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL` failed
gdm[6028] WARNING: Request for invalid configuration key xdmcp/Enabled=false


What does that mean?  
How do I fix it?    Be detailed please!

Thank you.

---

### Post by Kevbert on 2008-10-18
This error has already been reported in Launchpad. Unfortunately I can't recall or find the actual bug report.  The message also occurs when you shut the PC down. It's just an inconvenience that's being looked at and shouldn't cause any problems with the general operation of the PC.

---

### Post by OutOfReach on 2008-10-18
Yes, I have found that message shown to me during shut down, really it doesn't seem to affect anything in a serious or harmful way.

---

