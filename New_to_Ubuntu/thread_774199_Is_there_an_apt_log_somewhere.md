---
title: "Is there an apt log somewhere?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Golem XIV on 2008-04-29
I am wondering if apt generates a log with the information on installed/removed/updated packages and so on.  If it does, where is it?  If it doesn't, can it be enabled?

---

### Post by Monicker on 2008-04-29
> **Golem XIV said:**
> I am wondering if apt generates a log with the information on installed/removed/updated packages and so on.  If it does, where is it?  If it doesn't, can it be enabled?

Take a look at /var/log/apt/term.log

There also seems to be some relevant info in /root/.synaptic/log

---

### Post by pedro_orange on 2008-04-29
Also take a look in:

/var/log/dpkg.log

Thats more to do with installed packages etc tho.

---

### Post by Golem XIV on 2008-04-29
> **Monicker said:**
> Take a look at /var/log/apt/term.log

There also seems to be some relevant info in /root/.synaptic/log

/var/log/apt/term.log seems tyo be what I was looking for.  Thanks!

---

### Post by Golem XIV on 2008-04-29
> **pedro_orange said:**
> Also take a look in:

/var/log/dpkg.log

Thats more to do with installed packages etc tho.

This one seems to be more detailed, probably more useful for tracing problems.  Thanks!

---

