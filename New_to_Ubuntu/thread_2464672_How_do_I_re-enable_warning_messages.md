---
title: "How do I re-enable warning messages?"
date: 2021-07-08
forum: New to Ubuntu
---

### Post by yatski on 2021-07-08
Yesterday I got warning message that 'root has less than 1 GB of space left'. 
I clicked 'ignore' in mistake and now I want warning message features back. 
Is there easy way out? 
I use Focal Fossa.

---

### Post by grahammechanical on 2021-07-08
It is my understanding that clicking "ignore" on that kind of message does not disable the notification process but only ignores it for a period of time. We have System Settings>Notifications to gain some control over the notifications that appear. I doubt very much if we can turn off the notification that the root or the Ubuntu OS partition is getting low on disc space. Ignore that message too often then the OS may freeze.

While you have an opportunity to create more free space do so.

If the OS should freeze, then from the Grub menu select Advanced Options for Ubuntu and select a Linux kernel with Recovery Mode. At the Recovery Menu select Clean - Try to make free space. That may improve things at least long enough to load into the desktop.

Remember, when we send something to the Rubbish bin the file is not removed from the hard disk. So, we can create some free space by emptying the Rubbish bin.

Regards

---

### Post by TheFu on 2021-07-08
Install **Logwatch** and have it email daily system information to an account you check. Best if this was an internal email, since logs can contain very sensitive information that is best NOT sent to a gmail.com address.

Or have logwatch create html reports and get into the habit of manually checking that daily.  I retain 120 days of logwatch data, since it can be helpful to see what changed, when, if anything bad happens.

As usually there are 50 answers for this issue.

---

