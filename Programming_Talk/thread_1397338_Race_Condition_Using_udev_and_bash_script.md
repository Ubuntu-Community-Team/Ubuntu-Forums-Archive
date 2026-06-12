---
title: "Race Condition Using udev and bash script"
date: 2010-02-03
forum: Programming Talk
---

### Post by BeardedChimp on 2010-02-03
I have a udev rule that triggers when a hsdpa modem is plugged in. It runs a script that then attempts to dial that modem. Once it has dialed it flushes iptables and creates rules depending on how many modems are connected.

My problem is that I'm using several modems and so when the computer boots/they are plugged in via a hub, udev triggers for each modem simultaneously.
The problem is then that each script is running and they race when they try and flush the iptables and recreate it using the number of dialed modems leaving malformed iptables.

I tried creating a lock file then adding this to my bash script:
while [ -e /tmp/modem.lock ]
do
  sleep 1
done
touch /tmp/modem.lock

But udev runs so quickly on boot that each script will skip the check and create the file at the same time.

I've tried a number of hacks to get it working but nothing satisfactory

Any help?

---

### Post by MadCow108 on 2010-02-03
as you realized "touch" is not atomic, so it won't work

according to this:
[http://www.bash-hackers.org/wiki/doku.php/howto/mutex](http://www.bash-hackers.org/wiki/doku.php/howto/mutex)
mkdir will work
But I have some doubt if it really works on all file system.

I guess for proper race condition safe operation, a shellscript is not the right tool.

---

### Post by BeardedChimp on 2010-02-03
Ahh, I never considered using mkdir. That website was a lot of help thanks, I'm going to implement mkdir now.

---

### Post by BeardedChimp on 2010-02-03
Swapped everything and that is working perfect now. Cheers for the help.

How can I mark the thread solved?

---

### Post by MadCow108 on 2010-02-03
with the thread tools link/popdown to the upper right of the first message

---

