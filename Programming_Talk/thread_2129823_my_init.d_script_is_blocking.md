---
title: "my init.d script is blocking"
date: 2013-03-27
forum: Programming Talk
---

### Post by mercxi on 2013-03-27
how do I run my init.d script in the background
Currently I have this:
/etc/init.d/sandbox 
su -c /files/sandbox

---

### Post by schragge on 2013-03-27
Ubuntu uses [upstart]("http://manpages.ubuntu.com/manpages/precise/en/man7/upstart.7.html") instead of SysV init. It will still execute legacy init scripts on startup, but honestly I don't know how it is implemented in detail. See [uhelp]community/UpstartHowto[/uhelp].

In Debian, you manage your */etc/init.d* scripts with [update-rc.d]("http://manpages.ubuntu.com/manpages/precise/en/man8/update-rc.d.8.html"). This command generates appropriate links under */etc/rc[0-6S].d/*. There's also [sysv-rc-conf]("http://manpages.ubuntu.com/manpages/precise/en/man8/sysv-rc-conf.8.html") in repositories. It has curses interface and is modeled after RedHat's *chkconfig*.

Init scripts are supposed to be automatically executed on boot, why would you want to run them in background? Certainly, they can start services or daemons that are then themselves running in background. For this, the [start-stop-daemon]("http://manpages.ubuntu.com/manpages/precise/en/man8/start-stop-daemon.8.html") command is usually invoked inside an init script.

---

