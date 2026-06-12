---
title: "[SOLVED] problems installing a new cronjob"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by herbert tamayo on 2008-08-07
Hi, I'm trying to install a new cronjob but the command part is too long that it needs to spread in two lines, when I tried to save it, I obtained the next error:

```

"/tmp/crontab.IKiGYG/crontab":3: bad minute
errors in crontab file, can't install.
Do you want to retry the same edit? 

``` 

This error is because this command is in two lines:
```

# m h  dom mon dow   command
30 8,10,12,14 * * * /home/ok/job1.sh
0 0 * * * (command -q > command 2>&1; command -w command smth | smth -es "something " ok@ok.com)

```

My question is:
What is the way that crontab can read the "long command cronjob" as one single line?

Regards

---

### Post by Bachstelze on 2008-08-07
That's because [font="Courier new"]nano[/font] automatically wraps the lines that exceed the terminal width. You can disable this by doing

```
EDITOR="nano -w" crontab -e
```

instead of just [font="Courier new"]crontab -e[/font].

---

### Post by herbert tamayo on 2008-08-07
Thanks a lot! IT works!, Regads

---

