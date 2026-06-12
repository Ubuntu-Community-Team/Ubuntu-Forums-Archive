---
title: "livecd ubuntu user creation point"
date: 2015-07-19
forum: Packaging and Compiling Programs
---

### Post by roland-logikalsolutions on 2015-07-19
All,

This should be simple. Someone wants to add stuff to the "live" ubuntu user so people who know nothing about computers can click the "Try" button and see a presentation automatically. No problem. I have the preseed file all set up creating directories, copying files, etc.

Now comes the broken part.

"live" user doesn't use ubiquity so everything has to be in d-i preseed/late_command string

Here comes the boot to the head!

Casper runs that late_command __BEFORE__ the ubuntu user is created. Can't copy a program and .desktop file to a user home which does not yet exist.

Where in the livecd process does the "ubuntu" user get created? This should have been a 10 minute thing. I have wasted 2 days trying to find what executes AFTER casper and BEFORE the automatic login.

Thanks,

---

### Post by Portaro on 2015-07-19
The default configs of an user is placed on /etc/skel , I think you may refer to this but Im not certainly if is your real question.

---

### Post by roland-logikalsolutions on 2015-07-19
> **Portaro said:**
> The default configs of an user is placed on /etc/skel , I think you may refer to this but Im not certainly if is your real question.

Thank you for your reply. You are correct, it is not my real question. There is an execution path I'm trying to identify.

User clicks "Try" button
vmlinuz and casper chew through seed files creating a viable system without any users.
the late_command string runs at the tail end of that, or at least part of the tail end.

something-else-now-happens

That something-else creates the ubuntu user, then logs them in.

I really wanted to find that something-else

I'll see if I can hack the SKEL from within the preseed file for an ugly kind of work around until I have a chance to do it right.

(Does anyone ever get enough time to go back and do something right.)

I just looked at the environment live creates. There is nothing in skel other than the examples.desktop file.

---

