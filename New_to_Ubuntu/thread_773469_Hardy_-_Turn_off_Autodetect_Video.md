---
title: "Hardy - Turn off Autodetect Video?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by OmahaVike on 2008-04-28
hello,

i just fresh installed hardy after years of dapper, and have found an annoying problem.  i greatly appreciate anyone's help with this.

i use a kvm switch between two machines.  when the kvm is switched away from my hardy machine, and the machine boots, X is looking to autodetect my video settings.  obviously, with the kvm pointed away, it cannot determine the monitor (and maybe video card?) -- and gives me that ugly low rez message.  when i let my hardy machine boot while being active on the kvm switch, all is wonderful.

is there ANY way to turn off that annoying autodetect feature for each time it boots?

thanks thanks thanks!

---

### Post by spiderbatdad on 2008-04-28
wondering if you have tried acpi=off?

---

### Post by OmahaVike on 2008-04-28
thanks spiderbatdad.  

```
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=917e7c4d-f646-4770-a843-48bd45cda1bd ro quiet splash acpi=off
```

unfortunately, didn't work.  any other thoughts?

---

### Post by spiderbatdad on 2008-04-28
maybe nolapic to disable local apic...just guessing obviously...searched a little but didn't turn up anything.
BTW I usually remove --quiet splash when try any other boot parameters.
Also...I would experiment by editing from the Grub boot screen by selecting 'e' then move to the kernel line...'e' again...enter...'b' to boot.
That way if there is a problem...menu.lst is intact for a restart.

---

