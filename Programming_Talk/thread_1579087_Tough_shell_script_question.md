---
title: "Tough shell script question"
date: 2010-09-21
forum: Programming Talk
---

### Post by conundrumx on 2010-09-21
Like many of you, I have a customized shell environment (bash) which I am very accustomed to and don't like going without.  I copy my .profile onto most of my remote boxes, but I want a more immediate differentiator (than the hostname) between an SSH session and a local one.  My solution for this is to change a color in the PS1.

For example, let's say a local tty is red, and a remote one (via ssh) is blue.  How can I accomplish this?  Short of hardcoding in checks on the output of hostname and commenting out one or another I've yet to come up with a viable solution.

---

### Post by spjackson on 2010-09-21
You could test whether the environment variables SSH_CLIENT, SSH_TTY, SSH_CONNECTION are set. Does this help?

---

### Post by conundrumx on 2010-09-21
Yes, that's all useable.  Is there some grand repository of environment variables I'm unaware of?

Thank you.  :>

What I ended up using, if anyone is curious:

```
if [ -z "${SSH_CLIENT}" ] ; then
```

---

### Post by Tibuda on 2010-09-21
> **conundrumx said:**
> Yes, that's all useable.  Is there some grand repository of environment variables I'm unaware of?

like when you type **env** in a terminal?

---

