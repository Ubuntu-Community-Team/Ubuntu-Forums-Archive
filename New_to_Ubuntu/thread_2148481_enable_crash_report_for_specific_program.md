---
title: "enable crash report for specific program"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by MRiekerk on 2013-05-25
Hello,

A program I have installed kept giving crash reports even though it continued working.
I send the crash report to the developer and told Apport not to alert me any longer about the program.

Now the developer send me a new (test) version of the program and asked me to try it.
But because I disabled the bug alert for this program, I doubt any alert will pop up.

How can I enable the alert for this specific program? 
I didn't edit /etc/default/apport to disable Apport and I didn't disable the "Send error reports to Canonical" option in the Privacy settings. These were the things I found on Google about disabling bug reports.

Thanks in advance.
MRiekerk

---

### Post by deadflowr on 2013-05-25
If through testing you encounter problems and the apport crash thingy doesn't show up, just run
```
ubuntu-bug program-name
```

Then follow the standard bug reporting practice.

---

### Post by MRiekerk on 2013-05-25
Thanks for the (very) quick reply!

I didn't help me though... :(
The problem I described was that teamviewer 8 checked the distribution version by calling lsb_release -a and lsb_release -ds
Here is a bug report of the crash [https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1094218]("https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1094218")

When I tried ubuntu-bug lsb_release I got the message that the package does not exists, but lsb_release -ds returns Ubuntu 12.04.2 LTS. So it does exists.
When I tried ubuntu-bug teamviewer I got the message that it's a third  party package.

I hope my problem is now more clear.

---

### Post by MRiekerk on 2013-05-25
Thanks for the (very) quick reply!

I didn't help me though... :(
The problem I described was that teamviewer 8 checked the distribution version by calling lsb_release -a and lsb_release -ds
Here is a bug report of the crash [https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1094218]("https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1094218")

When I tried ubuntu-bug lsb_release I got the message that the package does not exists, but lsb_release -ds returns Ubuntu 12.04.2 LTS. So it does exists.
When I tried ubuntu-bug teamviewer I got the message that it's a third  party package.

I hope my problem is now more clear.

---

### Post by deadflowr on 2013-05-25
This is closest thing I could find on bug reporting for teamviewer
[http://www.teamviewer.com/en/help/createticket.aspx](http://www.teamviewer.com/en/help/createticket.aspx)

I would suggest contacting those devs directly.

And the package is lsb-release, not lsb_release.
lsb_release is in lsb-release.

---

