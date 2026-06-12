---
title: "Crash report"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by bobjam2 on 2014-04-22
Ubuntu 12.04.3 LTS

Just did two non-critical upgrades that included "crash report", shown in the var/log/apt/history.log as "whoopsie:i386 (0.1.33, 0.1.34)".

The other was "ubuntu-tweak:i386 (0.8.6-1~precise1, 0.8.7-1~precise1)".

Now I have a perpetual "crash report detected" icon in my notification area, and it WON'T respond to any click nor go away on restart . . . it shows up again.

Nevertheless, the system seems to be working properly, so it looks like it is also on perpetual "ignore".

I don't want to remove the notification area in the panel to make that bothersome icon go away.  In the past, when it showed up I could always click on it, it would show me the culprit and a bunch of other path information plus an option to send a report, and on restart it would go away.

Now it shows up perpetually, and I can't even get it to show me any information.

Did this happen because of the upgrade (certainly seems so)?  Is this a bug with the upgrade?

---

### Post by bobjam2 on 2014-04-22
Update:  Now when I click on it, it shows a "crash report detected" dialog underneath it, and if I click on THAT, it gives me the warning message:

```
This problem report is damaged and cannot be processed.

TypeError(Error('Incorrect padding',),)
```No options, just the message.

Then the icon goes away.  I'm going to restart and see if it shows up again.

---

### Post by bobjam2 on 2014-04-22
Update 2:

On restart, I got the "crash report detected" icon again, but this time clicking on "crash report detected", I got the info dialog.

Part of what it showed was:

```
Title

mate-keyring-daemon crashed with SIGSEGV in getenv()


UnreportableReason

This is not an official Ubuntu package.  Please remove any third party package and try again.

```(Mate is my DE)

Looking at that "UnreportableReason" line, I'm guessing "*Ubuntu Tweak*" is causing this, however I saw no path listed for "*Ubuntu Tweak*", just a bunch of libs, addresses, and a few listings for my kernel, 3.2.0 - 60

I closed the crash report without clicking on "Continue", the icon went away, and when I restarted it didn't show up again.

I really don't want to remove "*Ubuntu Tweak*", but should I report my guess to the "*Ubuntu Tweak*" author?

In any case, it seems like this has gone away.  Should I be concerned?

---

