---
title: "clock problem"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by aef54 on 2012-07-05
I have a problem with the clock in Ubuntu. 

It takes the time from the BIOS clock, and then adds two hours, and displays that as the time.

So it's 16:41 now, but Ubuntu says 18:41.

But the real annoying thing is that when I change the clock in Ubuntu to 16:41, it automatically changes the BIOS clock two hours back too, to 14:41.

Then when I boot another OS, that clock is messed up (displaying 14:41).

Does anybody know how I can solve it?

---

### Post by Quackers on 2012-07-05
Do you have the correct time zone setting in System Settings > time & clock?

---

### Post by aef54 on 2012-07-05
Yes sir.

(And still, just changing the timezone, changes both Ubuntu's clock as well as the BIOS clock. There is no difference in changing the timezone or just manually setting the clock. Tried that)

---

### Post by asmoore82 on 2012-07-05
By default, Linux systems sync the hardware clock (BIOS clock on PC's) to UTC also known as GMT. The advantage is that, keeping in mind Linux's widespread use in embedded devices and mobile devices, as the system may move around the world, the clock is always right. However it becomes the responsibility of the software higher up the stack to apply the correct timezone offset for the end user.

In order to get along dual booting with other OS's, you can change this Linux behavior. On Ubuntu, you would need to edit, with admin privilege, the file "/etc/default/rcS"

```
gksudo gedit /etc/default/rcS
```

and change the line "UTC=yes" to "UTC=no"

---

### Post by aef54 on 2012-07-05
Yeah! That worked :-)

Thank you for the working solution and the clear explanation.

---

