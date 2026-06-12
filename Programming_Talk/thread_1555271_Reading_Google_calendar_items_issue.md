---
title: "Reading Google calendar items issue"
date: 2010-08-17
forum: Programming Talk
---

### Post by Newbie2910 on 2010-08-17
I am using .Net code (running under Mono on Ubuntu 10.04 and the same code under Windows), and using the Google calendar APIs.

Same code, in fact the same .DLLs I use for Windows I copied over and linked in for Mono.

The problem is, under Windows my app authenticates fine and reads/writes calendar items without any problems.  When running (same PC, btw) under Ubuntu I always get 401 authentication errors.  I have checked and the names and passwords being sent to Google are correct.

Also I can log in using Firefox on both Windows and Ubuntu, to the Google calendar account.

Is there something Google does to disallow calendar API requests originating from machines running Linux?

---

