---
title: "start up scripts inet, xinet, init confusion..."
date: 2012-10-20
forum: New to Ubuntu
---

### Post by kg4cjv on 2012-10-20
So I'm a bit confused about how ubuntu starts up. There are init scripts, xinet scripts and inet scripts. What are all of these and which ones should I use if I'm developing a service that I want to start up when my system boots. 

Can someone point me to some definitive answers?

Thanks!

---

### Post by Lars Noodén on 2012-10-20
Ubuntu currently uses [upstart](http://upstart.ubuntu.com/).  It used to use System V.  Maybe in the future it will use systemd.  But for now it is Upstart.  

You can find the current upstart files in /etc/init/  You'll need to make a configuration file for your service and put it there.
Look at some of the .conf files there for an idea how they are set up.

---

### Post by Lars Noodén on 2012-10-20
I can't find anything authoritative on System V init scripts, or just don't know where to look.  There is a discussion of runlevels here:
[http://linuxmafia.com/faq/Admin/init.html](http://linuxmafia.com/faq/Admin/init.html)

Ubuntu no longer uses System V init scripts, but not everything has been ported over to Upstart yet.  So there are still scripts in  /etc/init.d/  To use System V, you need a script in /etc/init.d that takes as options 'start', 'stop', 'restart', 'reload', 'force-reload' and 'status'  Then [update-rc.d](http://manpages.ubuntu.com/manpages/precise/en/man8/update-rc.d.8.html) is the tool to use to make a symlink to the script in the directories /etc/rcX.d/, where X is the runlevel.  The script will be names with S or K, for start or kill, and then a sequence number.  Lower numbers get executed first.  When the system changes to a runlevel, all the scripts for that runlevel will get executed.  

However, that's rather moot now that Ubuntu has moved to Upstart.  

inetd and [xinetd](http://manpages.ubuntu.com/manpages/precise/en/man5/xinetd.conf.5.html) are a different matter.  They are used to launch daemons on demand rather than leaving them running in the background as per System V or Upstart.  That's about all inetd does, but xinetd can do a lot more in regards to restricting access and logging.

---

