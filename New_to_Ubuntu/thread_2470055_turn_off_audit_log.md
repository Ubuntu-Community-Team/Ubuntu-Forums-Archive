---
title: "turn off audit log"
date: 2021-12-18
forum: New to Ubuntu
---

### Post by bjlockie on 2021-12-18
I get a lot of things like this in dmesg and I'd like to turn them off:

```
[ 9743.615174] audit: type=1400 audit(1639855068.449:39): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/zoneinfo-icu/44/le/timezoneTypes.res" pid=6351 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

I tried this:
```

$ sudo systemctl disable auditd
Failed to disable unit: Unit file auditd.service does not exist.
```

---

### Post by guiverc on 2021-12-18
You can restrict the output to specific levels, eg. using 

```
**dmesg** **--level=err,warn**
```

which was just copied from [http://manpages.ubuntu.com/manpages/impish/en/man1/dmesg.1.html](http://manpages.ubuntu.com/manpages/impish/en/man1/dmesg.1.html)

You can also *permanently* restrict the level of the messages that get stored, but I think that's generally best avoided.

---

### Post by bjlockie on 2021-12-19
> **guiverc said:**
> You can restrict the output to specific levels, eg. using 

```
**dmesg** **--level=err,warn**
```

which was just copied from [http://manpages.ubuntu.com/manpages/impish/en/man1/dmesg.1.html](http://manpages.ubuntu.com/manpages/impish/en/man1/dmesg.1.html)

You can also *permanently* restrict the level of the messages that get stored, but I think that's generally best avoided.


I have an nvme drive and I don't really want it writing unnecessarily.

I created an alias. :-)
alias dmesg="sudo dmesg --level=err,warn"

---

