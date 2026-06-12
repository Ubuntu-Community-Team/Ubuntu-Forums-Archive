---
title: "uptime and idle time in /proc/uptime"
date: 2010-03-24
forum: Programming Talk
---

### Post by yabune on 2010-03-24
Hi,

If I run:
```
cat /proc/uptime
```
I get two numbers.
I know the first one is the number of seconds the system has been up.
But what about the second number? I thought it was the idle time, but I'm getting a number bigger than the first one.
How is that possible?

Thank you!

---

### Post by falconindy on 2010-03-24
The second number represents, in seconds, how long the processor has been idle. On multi core systems, this is accumulated on a per CPU basis.

---

### Post by gerbilio on 2011-08-10
Got news for ya.  In previous releases, the first number was ALWAYS slightly larger than the second, which makes sense because modern computers spend the vast majority of their time doing absolutely nothing.  Now, the second number is much larger than the first, which would imply the system has been idle for far longer than it's been actually running!

Hey Linux kernel guys, what did you do to the uptime procfile???

---

### Post by Bachstelze on 2011-08-10
> **gerbilio said:**
> Got news for ya.  In previous releases, the first number was ALWAYS slightly larger than the second, which makes sense because modern computers spend the vast majority of their time doing absolutely nothing.  Now, the second number is much larger than the first, which would imply the system has been idle for far longer than it's been actually running!

Hey Linux kernel guys, what did you do to the uptime procfile???

Read the message above. If a quad-core CPU is entirely idle for 1 second, it will count as 4 seconds.

---

