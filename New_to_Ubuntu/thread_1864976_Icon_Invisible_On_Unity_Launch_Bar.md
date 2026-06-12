---
title: "Icon Invisible On Unity Launch Bar"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by -kg- on 2011-10-19
I've searched the forums, as well as Ubuntu Google, and can find no reference to this problem.

I installed Ubuntu 11.10 (64 bit) last night and noticed that the Thunderbird Icon was not present on the Launcher Bar in the installation.  No problem...I pulled up the Help files, noted how to add a Launcher to the bar, and dragged and dropped the launcher from Dash to the Launcher Bar successfully.

Unfortunately, there is no Icon for Thunderbird visible.  There is a blank space on the Launcher Bar.  The launcher is there because I can click on it and launch Thunderbird, but no icon.  Any ideas on how to make the icon visible?

---

### Post by hansdown on 2011-10-19
Haha! I thought I had done something wrong, on my install, -kg-.

Not sure how to fix it though.

---

### Post by -kg- on 2011-10-19
Well all-righty then! :confused:

I was playing around with another problem I was having, installed ccsm, and managed to crash Unity.  I did a little research, reset Unity (and promptly uninstalled ccsm), and noticed that now, the Thunderbird icon is present and visible in the Launch Bar.

I don't know what I did to resolve the issue, but it's now resolved, and I'll marked this thread as solved.  I'll ***(cautiously!)*** do a little more experimentation and report back with any discoveries.

At this point, all I can think of that might have done it is resetting Unity.  The command I used:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

I logged out and back in, and everything was good.

---

### Post by -kg- on 2011-10-19
OK, I found out what the deal was.

When logging in, I have two "sessions" that I can log into..."Ubuntu" and "Ubuntu 2D."  Logging into "Ubuntu 2D" gives me a normal desktop, with everything functioning, but if I log into "Ubuntu" I get the screwed up Desktop that I had to recover from.  Apparently, running the above command didn't resolve anything.  It was logging into 2D that resolved my problem.

I guess as long as 2D works, I'm OK with it, but it sure is a strange problem.

---

