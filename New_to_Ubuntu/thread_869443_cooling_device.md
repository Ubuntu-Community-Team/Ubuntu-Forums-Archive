---
title: "cooling device"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Gene_s on 2008-07-24
when I run the following in terminal I get a repeating message

sudo tail -f /var/log/messages

unable to turn cooling device on.....

is this the cooling fan??

---

### Post by ibuclaw on 2008-07-24
Are you running a laptop or desktop?

If you are running a desktop, simply open up your box and check that all fans are running.

If you are running a laptop, you can check all laptop air-vents at the bottom, but you may want to post your hardware details for people to check.

```
sudo lshw
```

Also, can you try and find out which running module is producing the error output?

Regards
Iain

---

### Post by Gene_s on 2008-07-24
I have a HP Pavilion a500n

the message says ACPI: Unable to turn on cooling device {f7c44f18} on.

---

