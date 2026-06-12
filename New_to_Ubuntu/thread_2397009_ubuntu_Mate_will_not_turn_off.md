---
title: "ubuntu Mate will not turn off"
date: 2018-07-24
forum: New to Ubuntu
---

### Post by dave6 on 2018-07-24
Mate, will not turn off.

Hi all.
Has any one else had this problem,  I have clean installed it twice, "ain't doing it again" some times when I press the Esc key, the thing has frozen, but most of the time I can read was is going on in the back ground, see photographs.
And how do I stop the monitor from going to sleep mode...

Thanks
Dave

---

### Post by #&amp;thj^% on 2018-07-24
Try this and edit /etc/default/grub line:
It would be better to use:
```
sudoedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

change to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

```
Run update-grub.
```
sudo update-grub
```
Good Luck

---

### Post by dave6 on 2018-07-25
Hi 1fallen
err, just how do I edit "edit /etc/default/grub line:" ? I think that would b e done in, or with terminal.

Thanks
Dave

---

### Post by Dennis N on 2018-07-25
> Has any one else had this problem?
Yes, occasionally seen over past few years. I recently started seeing it again in Ubuntu 18.04 (and also in Manjaro Gnome) a few weeks ago. It's intermittent. I did not determine a cause from journal or logs, or seen any solution. I'm planning now to keep track of what percent of shutdowns do this.

**Bug report filed** (way back in 2015; considered "low importance" and never was assigned to be solved):

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

**Posted on alt.os.linux google group:**

> 90-second startup and shutdown delays: systemd?

It is a systemd issue.  I experienced it on shutdown on Debian Sid.
I ended up setting some systemd timeout down to 5 seconds.

   [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

   /etc/systemd/system.conf

   or a similar file should be your friend

   [http://www.freedesktop.org/software/systemd/man/systemd-system.conf.html](http://www.freedesktop.org/software/systemd/man/systemd-system.conf.html)

   search for

   DefaultTimeoutStartSec=
   DefaultTimeoutStopSec=
   TimeoutSec=

   and enter lower values

Good luck!
...


I just changed **"DefaultTimeoutStopSec=90s"** to **"DefaultTimeoutStopSec=5s"** 
as suggested by above quote. I will see how that works out. (Be sure to remove the # at the start of the line as well)

Comments from the bug report help explain the shutdown process:

> Expert Martin Pitt quoted from comment section of bug report:

"What happens at shutdown is that all processes are sent SIGTERM, so that they have a chance to intercept, save their state/clean up, etc. After a timeout (default 90s) SIGKILL is sent."

"This [problem] probably got introduced with the fix for bug 1448259. So, this general behaviour is "correct" in the sense that processes should not be killed immediately after SIGTERMing them. But 90s is a bit much for session shutdowns, this could be reduced to something like 30 s. This is still a long session shutdown, but you really wan this if e. g. LibreOffice asks you about unsaved documents and the like.

I don't know what the timeout under upstart was, but apparently it was a lot smaller."


---

