---
title: "[SOLVED] [HOW TO]How can I find the source code of 'ps' command?"
date: 2008-07-07
forum: Programming Talk
---

### Post by horry on 2008-07-07
Hi everyone,
I want to learn something from the ps command source code, but I can't find it, so could you kindly tell me how can I get it?
Thanks in advance!

---

### Post by ibutho on 2008-07-07
Debian based distros use the [procps]("http://procps.sourceforge.net/") package to provide the ps command.

---

### Post by horry on 2008-07-07
I got it. Thanks a lot. 
But if I want to find some other command source code, how can I to do it?
Could you tell me the way to find a some source code?
Greate thanks.

---

### Post by ibutho on 2008-07-07
You need to find out which package provides the command e.g.
```
$dpkg -S `which ps`
procps: /bin/ps

```
You would then download the source from the official project or the Debian/Ubuntu repos.

---

### Post by nvteighen on 2008-07-07
Use:
```

apt-get source *package*

```

Yes, WITHOUT sudo. That will download the source to the **current directory** (so first, create a new directory and change to there... so we keep things tidy in our home folder).

But first, you have to activate the sources repositories. Go to System->Software Sources and check 'Source code'.

---

### Post by horry on 2008-07-07
> **ibutho said:**
> You need to find out which package provides the command e.g.
```
$dpkg -S `which ps`
procps: /bin/ps

```
You would then download the source from the official project or the Debian/Ubuntu repos.

Many thanks.
:)

---

