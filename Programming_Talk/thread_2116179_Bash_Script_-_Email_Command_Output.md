---
title: "Bash Script - Email Command Output"
date: 2013-02-15
forum: Programming Talk
---

### Post by StuFranks on 2013-02-15
Hello Everyone,

I'm trying to write a bash shell script that will perform the following command.
[FONT=Courier New]doall 2 24 "ipmitool sel list"[/FONT]

I want to perform that command and then have the output emailed to me from the machine. I'm new to bash scripts so I am struggling a bit!

How would I go about doing this?

Cheers,
Stu

---

### Post by schragge on 2013-02-15
```

doall 2 24 "ipmitool sel list" | mailx -s"Subject" username@host

```

---

### Post by Bachstelze on 2013-02-15
Also depending on your environment, it might be impossible to send mail directly (if you have a dynamic IP or if your ISP forbids it, for example).

---

