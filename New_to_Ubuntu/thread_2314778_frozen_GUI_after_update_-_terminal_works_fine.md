---
title: "frozen GUI after update - terminal works fine"
date: 2016-02-23
forum: New to Ubuntu
---

### Post by bmr323 on 2016-02-23
Hello.

Ok, so after a recent update, when I log in with my password on the GUI, it freezes, then returns me to the log in screen as if I entered the wrong info. When entering the same info on the terminal log in, I am able to successfully log on.

I've gotten as far as running this command to list the updates and possibly remove the most recent one.
**tail -n25 /var/log/apt/history.log**

[FONT=arial]But I'm not quite sure what to do from here. 

This is a brand new laptop that I use daily and need desperately to work.

Any help?
[/FONT]

---

### Post by sandyd on 2016-02-23
In the terminal, check these two things:

1. .Xauthority ownership.
```

ls -la ~
```

If the file .Xauthority is owned by root, run
```

sudo chown *username*: ~/.Xauthority
```
Try logging in again if you had to run the command above. Replace *username* with your username.

2. Check .xsession-errors:
```

cat ~/.xsession-errors | more
```

Check if there are any errors.

---

