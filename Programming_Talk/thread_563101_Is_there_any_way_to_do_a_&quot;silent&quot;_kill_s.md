---
title: "Is there any way to do a &quot;silent&quot; kill signal?"
date: 2007-09-29
forum: Programming Talk
---

### Post by Fixman on 2007-09-29
When one sends a signal to kill another process (inside a program), like this:

```
kill(0, SIGKILL) ;
```

It appears the following code on the standart error console:

```
Killed
```

Is there any way to disable this?

---

### Post by ryanVickers on 2007-09-29
doesn't "killall <programname>" not produce anything?

also, I don't know if this will work with just any command, or a command period :p, but in BASH, if you go " >/dev/null 2>&1" after something, it does not post *error* messages...

---

### Post by NullHead on 2007-09-29
does pkill help what you are talking about?

---

### Post by Awalton on 2007-09-29
You can catch SIGTERM, but I'm afraid there isn't much you can do for SIGKILL or SIGSTOP. They're designed to kill applications that aren't responding to SIGTERM in the first place. You might be able to suppress the "Killed" output from your shell, but I'm not sure why you'd want to do this unless you're being nefarious.

Generally, you should be using SIGTERM to kill your app, unless you can't for some other reason. Or at least that's how I learned UNIX many, many years ago. I don't see why this would have changed, though.

---

### Post by DMills on 2007-09-29
That has not changed.

If the problem is a child process, you could see about disconnecting its controlling terminal before execing it. 

That may or may not help, see Stevens APUE for the gory detail. 

Regards, Dan.

---

### Post by Fixman on 2007-09-29
> **ryanVickers said:**
> doesn't "killall <programname>" not produce anything?

also, I don't know if this will work with just any command, or a command period :p, but in BASH, if you go " >/dev/null 2>&1" after something, it does not post *error* messages...

No, I actually mean from C

---

