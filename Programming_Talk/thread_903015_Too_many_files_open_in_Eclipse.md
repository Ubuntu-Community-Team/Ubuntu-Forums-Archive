---
title: "Too many files open in Eclipse?"
date: 2008-08-27
forum: Programming Talk
---

### Post by jamesdcarroll on 2008-08-27
I'm dropping this here though I have a feeling it could be any of a number of things.

When I download a project from Apache (JAMES) SVN in Eclipse I start getting 'Too many files open' errors and they seem to come from Mylan.  Rumor has it that there is some kind of hard coded limit to the number of files that can be open at a time (1024, I think). This raises a couple of questions:

1. What with the limit???
2. What the heck is Mylan doing in there???
3. How can I fix/ get around this issue.

Thanks,

James

---

### Post by aloshbennett on 2008-08-28
There's a kernel parameter that resricts the number of files that a user can open at the same time. This prevents OS from crashing if user screws up and tries to open a lot of files by mistake. Similar restriction prevents the fork bomb from crashing your system.

To see the limit, try
> ulimit -n

The limit can be set like this
> ulimit -n 2048

Unfortunately, ubuntu doesnt allow this. You can set it for root user (using sudo -s) but once you exit root, you have 1024.

If you want to change it permanently, you can set the value in /etc/security/limits.conf and reboot.

---

### Post by dwhitney67 on 2008-08-28
Yes, whatever the previous post says.


Btw, why are you trying to open 1024+ files at the same time?  Why are you using Eclipse?

Download the project first, then use Eclipse (yuck btw!) to open files and/or library (projects).

---

### Post by jamesdcarroll on 2008-08-28
I don't have the files open myself. I might have 3 or 4 open at any one time at most.  I have a sneaking suspicion that its actually Mylan in the background that's doing it. I'll drop a note over in the Eclipse forums and see if they know. I dropped this here first figuring/knowing the file limit was basically a Linux issue and was hoping someone else had run into it.


Thanks,

---

