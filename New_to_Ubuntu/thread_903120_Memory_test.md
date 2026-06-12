---
title: "Memory test"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Joseph5000 on 2008-08-28
How can I test the memory?

Thanks

---

### Post by Crafty Kisses on 2008-08-28
You can do the following:
```
memtest
```

---

### Post by iaculallad on 2008-08-28
Boot from your Ubuntu LivdCD and select Memtest86+/Memtest.

---

### Post by egalvan on 2008-08-28
Also, almost all LiveCD's have a 'memory test' boot option.
 Usually the third or fourth option.

If you suspect bad memory/sub-system, then (if at all possible) let it run over-night. This will put a bit of stress on the machine, and usually uncover heat-related issues.

ErnestG 

:popcorn:

---

### Post by Joseph5000 on 2008-08-28
Thanks guys, but I am confused. I just want to know if the memory in my computer is running well, I know I have two pieces of mamory in the machine, and I know that when the guy in the store put the new one in that he showed me very quickly that it was installed by start up. I just want to know if one of the two pieces had died. Thanks again.

---

### Post by egalvan on 2008-08-28
> **Joseph5000 said:**
> Thanks guys, but I am confused. .... I just want to know if one of the two pieces had died. Thanks again.

How else would you know if the memory had died?
 Unless it went up in smoke, line one of mine did one time,
 yeah, real easy to tell it was bad (well-carbonized :))

Running a memory tester will tell you if a stick died...

the test will show how much memory is found.

if this is less than you installed, then one stick is dead.

if the amount is correct, then you may also have a bad memory stick, which will still show the correct amount, but have errors.

---

### Post by egalvan on 2008-08-28
> **Joseph5000 said:**
> the guy in the store put the new one in that he showed me very quickly that it was installed by start up. Thanks again.

Also, the BIOS start-up memory test is rather worthless. I can't remember the time that BIOS showed "all is well", and there was bad memory in the machine.

Well, OK, totally dead stick, or the wrong type (ECC, registered, grossly wrong timings) also perk up BIOS mem-check.


:popcorn:

---

### Post by iaculallad on 2008-08-28
You would also want to run a stress test on your memory aside from testing it with Memtest. Try [Inquisitor]("www.inquisitor.ru").

---

### Post by egalvan on 2008-08-29
> **iaculallad said:**
> You would also want to run a stress test on your memory aside from testing it with Memtest. Try [Inquisitor]("www.inquisitor.ru").

A big

 [SIZE="5"][COLOR="Red"]THANK YOU![/COLOR][/SIZE] 

for that link to Inquisitor.

It's just what I needed for my new set-ups.

ErnestG

:popcorn:

---

