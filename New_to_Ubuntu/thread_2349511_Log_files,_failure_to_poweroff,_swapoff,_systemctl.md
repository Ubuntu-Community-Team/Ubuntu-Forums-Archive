---
title: "Log files, failure to poweroff, swapoff, systemctl"
date: 2017-01-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2017-01-15
Where and which log files do I read to see what happens when the shutdown/power-off does not go cleanly?

Unless I use:

```
sudo swapoff -a && systemctl poweroff
```

as the shutdown commands, the power never shuts off and must be done so by pressing the power switch for a few seconds. Without a clean shutdown, I'm seeing the orphaned inodes error message at powerup/bootup time.

I have read and added myself to the list of affected users at [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1582011").

The last time I had this problem, updating the BIOS solved it, but I'm hesitant to do that unless so doing will resolve this power-off issue as the OS/computer is working fine otherwise.

The BIOS maker, MSI, does not address this as they don't address any Linux issues in the Notes on the BIOSes updates for this motherboard.

---

### Post by DuckHook on 2017-01-16
> **Mark_in_Hollywood said:**
> Where and which log files do I read to see what happens when the shutdown/power-off does not go cleanly?
A tough one because many shutdown hangs occur after the logging service has already been stopped. You can try syslog, but I've found that the best way is to hit the <Esc> button during shutdown so that you can see the whole process, or else change your GRUB settings to take out "quiet splash" so that the whole shutdown process rolls through on your monitor. Doing so, you can often see the last process before the shutdown hangs.
> Unless I use:

```
sudo swapoff -a && systemctl poweroff
```

as the shutdown commands, the power never shuts off and must be done so by pressing the power switch for a few seconds. Without a clean shutdown, I'm seeing the orphaned inodes error message at powerup/bootup time.
At least you've found a workaround, so good on you. In future, should you forget to invoke your workaround or for any other reason, try the REISUO method (a variant of the better known REISUB). REISUB is explained [here]("http://www.howtogeek.com/119127"). By replacing "B" with "O", you invoke system shutdown rather than reboot.
> The last time I had this problem, updating the BIOS solved it, but I'm hesitant to do that unless so doing will resolve this power-off issue as the OS/computer is working fine otherwise.
Although some people update BIOSes with no more concern than they do changing shoes, I'm with you on the matter. I won't update a BIOS unless there is something clearly dysfunctional. It's too risky to just use haphazardly.
> The BIOS maker, MSI, does not address this as they don't address any Linux issues in the Notes on the BIOSes updates for this motherboard.
Welcome to the world of Linux where the community must beg, borrow or steal to get any HW support for the OS. You might try MSI support or their forums. Often, the HW community has an appreciable Linux following even if the OEM does not "officially" support it.

---

### Post by DuckHook on 2017-01-17
Mark_in_Hollywood,

Just playing a hunch, but please post your fstab as well as results of sudo blkid. Is there a mismatch?

---

