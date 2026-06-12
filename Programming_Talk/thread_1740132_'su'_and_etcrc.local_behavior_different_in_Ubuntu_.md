---
title: "'su' and /etc/rc.local behavior different in Ubuntu vs. Debian ?!?"
date: 2011-04-26
forum: Programming Talk
---

### Post by Peyote Coyote on 2011-04-26
On ubuntu (10.04 & earlier) we boot our apps under a user account from /etc/rc.local which runs under root. First the boot script installs drivers and does rooty things, then under "myaccount":

su myaccount -c startPrg.bash (Inside is the actual /mybin/myprg &; )

and the program is left running (our goal of course)

BUT in debian (lenny) the exit from su terminates its child, which also seems right.

Now confused...

1) How can I spin off a child from /etc/rc.local that executes under a user account, but is not terminated when the su exits?

2) Why does the script act differently on ubuntu vs. debian?

THANKS A LOT!!!

---

