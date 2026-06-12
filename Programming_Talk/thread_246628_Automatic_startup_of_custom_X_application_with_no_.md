---
title: "Automatic startup of custom X application with no login"
date: 2006-08-29
forum: Programming Talk
---

### Post by FreedomFromWindows on 2006-08-29
I'm trying to prepare a C application to automatically start and stop under Ubuntu.

I have a C application that uses X (on a virtual Xvfb screen) that needs to start on boot with no login (like a daemon, but with the twist that it is using X).

I've create a script in /etc/init.d that works to 'start' and 'stop' the application perfectly when run with sudo from a terminal command line.

I've tried using update-rc.d to place symbolic links into the /etc/rc(n).d directories.  I initially tried starting with a priority of 99 in only runlevel 5 as I need X, but reading through more on how Ubuntu uses levels it seems that everything is really running at 2.  I tried 'start' at 2,3,4 and 5 and 'stop' on 0 and 6.  I changed a couple of the priority levels of other links (acpi-support, rc.local, rmnologin) to be 95 instead of 99 so that I could guarantee that my application would be started last and everything in the environment would be ready.  I've checked the read and execute priviledges on the scripts and links.

As far as I can tell, there is no attempt by anyone to start the application.  I wondered about putting it into RCS, which ought to be started at the end of every run level transition, but I don't want the script run more than once (and I want to use the shutdown capabilities to clean up).

I have another application that is a more straightforward daemon (based on the excellent vsftpd server), and I've used the same techniques to start and stop it (at priority level 20, which is the vsftpd default) and the system starts and stops it without any problem.  The script files appear to be identical in all important respects (obviously the application name etc. is different, and my C application has to run as a specific user that is given as an argument to start-stop-daemon).

I would suspect that there is something related to X, or to no-one being logged in when it is started, but I have diagnostics that write to disk at the beginning of the program before it tries anything X and there is no sign that it ever gets executed at all.  I can't see any log entries that come from the script, and I tried but couldn't easily see how to get script logs to go to /var/log/syslog or somewhere that might show what was going wrong (assuming the script is being executed at all).

There seem to be quite a few references to people struggling with automatic startup, so I'm thinking there may be something else that more fundamental that is causing the problem.

Any ideas on what I'm doing wrong, or more importantly, what I could do right?  Thanks!

---

