---
title: "Crontab Question"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by DBrocks on 2008-05-08
Hey guys. I'm sure this is a very easy question. However, I am confused. How can I have crontab run a script at 6:15 in the morning, every month, every weekday (not weekends)? Thanks guys!

---

### Post by glennric on 2008-05-08
Add the following line to your crontab
```
15 06 * * 1-6 command
```

---

### Post by DBrocks on 2008-05-08
isnt 1-6 all days of the week? I only want monday-friday

---

### Post by glennric on 2008-05-08
I meant 1-5 sorry.  0 is Sunday.

---

### Post by DBrocks on 2008-05-08
Gotcha. I read another thread, but I just wanted to make absolutely sure I was correct.

---

### Post by lemming465 on 2008-05-08
1-6 was probably a typo; for Mon-Fri you want 1-5.  See *man 5 crontab* for your other options.

---

