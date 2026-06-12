---
title: "super user by default"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by ricecakeburner on 2008-06-26
Hi all,

I know Ubuntu suppresses an notion of being a super user by default, however I would like it to be enabled by default. The reasoning behind this is simply for convenience. I work in a research lab, and we want to set up linux on a couple computers to run experiments. It's a bit cumbersome to have to use the terminal and use sudo(and it's derivatives) to run everything. Also, we have some assistants who don't know Linux well enough, so this would make transition from Windows to Linux a bit easier.

I know this is a big no no especially to beginning users, but we have them carefully monitored... :)

---

### Post by drs305 on 2008-06-26
I have sent a PM to the OP with a solution. I have removed the post from public viewing lest users with a minimal understanding of the consequences of always being root use this method.

---

### Post by Hospadar on 2008-06-26
well A) what is it that you are running all the time that requires sudo?

But: if you *really* want to avoid it (make sure you keep good backups!) then you should just log in as root.  Theoretically you could use chmod to give full privileges to all users to all the files on the system as well.

Really though, unless you are constantly reconfiguring the system in major ways, I can't imagine what you could need sudo so much for that you'd need to bypass it.  It is very dangerous, even for an experienced user.  A mistyped command can quickly wipe a system and dump tons of important data.

---

### Post by Greyed on 2008-06-26
Or set the suid bit for those applications if root is really, *really*, **really** needed.

---

