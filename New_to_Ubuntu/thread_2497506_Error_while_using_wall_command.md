---
title: "Error while using wall command"
date: 2024-05-08
forum: New to Ubuntu
---

### Post by ubisum83 on 2024-05-08
Hello everyone.
I'm studying for first level of LPI certification and reading the official teaching material.
I tried to use command **wall **to see its effect, but I got the following error:

```

biagio@biagio:~$ wall Messaggio
wall: /dev/seat0: No such file or directory

```

Then, I tried to use the same command as a super user, obtaining the following result:

```

biagio@biagio:~$ sudo wall Messaggio
[sudo] password for biagio: 
wall: /dev/seat0: No such file or directory
                                                                               
Broadcast message from root@biagio (pts/1) (Wed May  8 10:05:53 2024):         
                                                                               
Messaggio

```

It seems that command was correctly executed, but error continues to appear.
Can anyone explain this phenomenon?

Thanks for support.

---

### Post by ActionParsnip on 2024-05-08
Possibly this:
[https://bugs.gentoo.org/911336](https://bugs.gentoo.org/911336)

---

### Post by TheFu on 2024-05-08
Uh ... which Ubuntu release?  Every few years, things, especially security settings change.

BTW, I haven't see **wall** used anywhere since the mid-1990s, so know about it, but also know that the messages are posted to the console, which isn't likely to be seen by a GUI user.   On my 20.04 system, wall does show up in every terminal, but GUI users wouldn't see that since they wouldn't have a terminal open.  

The wall message doesn't show up in **dmesg** or system logs either, which I find surprising.

---

### Post by ubisum83 on 2024-05-08
> **TheFu said:**
> Uh ... which Ubuntu release?  Every few years, things, especially security settings change.

BTW, I haven't see **wall** used anywhere since the mid-1990s, so know about it, but also know that the messages are posted to the console, which isn't likely to be seen by a GUI user.   On my 20.04 system, wall does show up in every terminal, but GUI users wouldn't see that since they wouldn't have a terminal open.  

The wall message doesn't show up in **dmesg** or system logs either, which I find surprising.

I'm working on version 23.04.
Actually, **wall **is much more useful when system is set on a runlevel which allows users to connect via shell only.
This way, administrator can send messages to users and let them know (for instance) that they will be disconnected soon and that taking precautions is suggested.
Since there's only one user connected, the message is shown on the same terminal where command has been used.
Mine was just a test.

---

### Post by TheFu on 2024-05-08
**_Support for 23.04 ended in January._**
Move to a supported release ASAP.  You are months out of date and dangerous.  Stick with LTS releases and assume they have 3 yrs of support from the release date, since most desktop DEs only get 3 yrs of support.  Not running an unsupported OS is Admin 101.

There aren't any runlevels in systemd.  Your materials are too old.

I'm familiar with **wall** and the use.  I've been a Unix/Linux admin since the early 1990s.  Sometimes, allowing regular users access to **wall** is blocked, hence why it works with sudo, but without sudo it doesn't work.  There are others hear with 20 yrs more Unix experience than I.

---

### Post by ubisum83 on 2024-05-08
I know that systemd is based on units and not runlevels. Anyway, units are just an evolution of runlevels and command **runlevel** still works on my version of Ubuntu.
I just wanted to underline that **wall **is more useful when system is in a state allowing users to connect via shell only.

What appears weird is the fact that **wall **works properly when using**sudo**, but the error is still shown.
Is it possible that command doesn't work because current state of system expects only one user via GUI and not shell?

---

### Post by TheFu on 2024-05-08
Tested on 24.04 (ssh) and 20.04 (local).  No issue.  Get on a supported release.  Working on non-supported stuff makes no sense.

---

### Post by ubisum83 on 2024-05-08
Thanks for the hint.
I installed and configured Ubuntu on a virtual machine.
I'd like to avoid creating a new virtualization and start over again.
Isn't there any hope to fix things on my Ubuntu version?

---

### Post by TheFu on 2024-05-08
It is unsupported. Asking for help with unsupported versions is against forum standards.  I think they say "it dilutes the efforts of volunteers".  It is a waste of your time and ours.

An install takes 15 minutes. Not a big deal. If it takes you longer, you could use the practice.  I did 2 installs last week - each was under 11 minutes.

---

