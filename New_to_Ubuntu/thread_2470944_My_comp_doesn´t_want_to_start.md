---
title: "My comp doesn´t want to start"
date: 2022-01-17
forum: New to Ubuntu
---

### Post by eliyahu22 on 2022-01-17
When I start my comp, I get the list with parts in my comp, then the Ubuntu logo, then a flash with a row of messages, and then I am left with the message:  /dev/sdaZ:clean, 289358/145222720 files, 55592219/5847288 blocks, and that&#347; it.   I don´t get any further. 

What can I do about that?

---

### Post by TheFu on 2022-01-18
> **eliyahu22 said:**
> When I start my comp, I get the list with parts in my comp, then the Ubuntu logo, then a flash with a row of messages, and then I am left with the message:  /dev/sdaZ:clean, 289358/145222720 files, 55592219/5847288 blocks, and that&#347; it.   I don´t get any further. 

What can I do about that?

Boot from a Try Ubuntu flash drive and look at the system logs for the boot.  What you've said above doesn't tell us much that is unusual, I'm sorry to say.  A clean fsck is expected. It isn't an error.
While the system is booting, hit the <esc> key and watch the messaged scroll passed.  There are some pre-boot tasks which can take 5-10 minutes if either hardware or networking isn't working.  Once a month, I have scheduled for all my file systems to be checked. With 40TB of storage, if there are any issues, this can take some time.
If the system it setup to use DHCP for network settings but the DHCP server on the network is providing bad data, well, it might get stuck. Timeouts can be 90 seconds for each part, so if 5 problems need to time out, that's 5x90sec ... 

It is just easier to boot from a Try Ubuntu flash drive and mount the internal storage to look through logs ... or change to a different TTY - there are 8 ttys - during the boot. You may be able to login on TTY2 and look around while the boot process is continuing on TTY1 (or is it tty7?).

Of course, if there are hardware issues - perhaps a failing PSU - then nothing will help until that is fixed.  Could be anything in the hardware, so don't just suspect the PSU.  Has anything been done recently that would provide a hint?  Perhaps it is a laptop that was dropped?

Some basic information about the computer, the hardware, and the OS would help too.

---

### Post by eliyahu22 on 2022-02-14
It was a hardware problem, my SSD disk was acting up.   It is fixed now.  Thanks all for the reactions.

---

