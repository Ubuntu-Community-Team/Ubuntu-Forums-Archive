---
title: "another CPU prevented use of a memory address"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by 1888software on 2013-08-02
My 2nd "stupid" question is:

I have Ubuntu automatic software daily updates turned on. An error  reports that another CPU prevented use of a memory address. The screen  was black and required a reboot. This is on a standalone non-networked  machine connected by hardwiring to the internet via an ADSL connection  running Ubuntu 13.04 with no special programs/processes and just one  user - myself. Is this normal?

---

### Post by matt_symes on 2013-08-02
Hi

> **1888software said:**
> My 2nd "stupid" question is:

There's no such thing as a silly question; only silly answers.

> I have Ubuntu automatic software daily updates turned on. An error  reports that another CPU prevented use of a memory address. The screen  was black and required a reboot. This is on a standalone non-networked  machine connected by hardwiring to the internet via an ADSL connection  running Ubuntu 13.04 with no special programs/processes and just one  user - myself. Is this normal?

This is not normal, no.

The exact error message would help and it's not an error message that i, for one, have come across.

Kind regards

---

### Post by 1888software on 2013-08-02
AFAIK there should be NO other CPU taking control of memory on my machine. Please confirm:

To be specific, does any Ubuntu support process on my machine claim any of my CPU memory while executing? For example, when the automatic daily Ubuntu update runs on my machine, does that process take any of my CPU memory?

---

### Post by matt_symes on 2013-08-02
Hi

> **1888software said:**
> AFAIK there should be NO other CPU taking control of memory on my machine. Please confirm:

To be specific, does any Ubuntu support process on my machine claim any of my CPU memory while executing? For example, when the automatic daily Ubuntu update runs on my machine, does that process take any of my CPU memory?

When it's talking about a CPU, it'll be talking about a CPU core and not a physically seperate die on a chip in another computer (this will be the case in your average home computer/ laptop anyway).

How many cores does you computer have ?

If your not sure, open a terminal and copy and paste this into it and it'll tell you.

```
grep -c processor /proc/cpuinfo
```

From my netbook

```
matthew-S206:/home/matthew % grep -c processor /proc/cpuinfo
2
matthew-S206:/home/matthew % 

```

Dual core.

Kind regards

---

### Post by 1888software on 2013-08-02
ok, thanks very much, the machine is a dual core. We'll call this a cpu memory allocation anomaly resulting in a freeze requiring a reboot. Thank you for your help.

---

