---
title: "editing cron jobs with a script"
date: 2009-10-31
forum: Programming Talk
---

### Post by hellfeuer on 2009-10-31
I want to add/remove cron jobs with a script.

I can think of one way to do this: crontab -l, edit the output, then add it back with crontab filename

But this is ugly. Is there a simpler way? Placing files in /etc/cron.d is perfect but unfortunately requires superuser privileges. Any way around this? The man pages don't help, but surely someone else has encountered this problem before?

---

### Post by ENOTTY on 2009-10-31
If you're not averse to Python, take a look at python-crontab, located at [https://launchpad.net/python-crontab](https://launchpad.net/python-crontab).

---

### Post by diesch on 2009-10-31
"crontab -e " uses $EDITOR to edit the file. It has not to be an interactive editor, just set it to a script that takes a file names as argument and modifies that file.

Or use 
```
crontab -l | some_script | crontab -
```

---

### Post by hellfeuer on 2009-11-03
Thanks for the suggestions. Both are basically the first method I was talking about. I guess there is no alternative.

---

### Post by shel-hall on 2009-11-03
It's always possible that what you want to do can be done another way.

For example, if the object of the cronjob change is a  filename substitution, set the cronjob to read the filename from a file.

Another thing folks often want to do is to control the date or time that a cronjob runs ("every other Friday except on Christmas"), something that you can also do within the cronjob itself.

So ... aside from the general idea of changing a cronjob with a script, what are you really trying to do?

-Shel

---

### Post by diesch on 2009-11-03
If you want to manage your cronjobs in e.g. ~/.cron.d/, just use something like

```
cat ~/.cron.d/* | crontab -
```

after you modified anything in ~/.cron.d/

---

