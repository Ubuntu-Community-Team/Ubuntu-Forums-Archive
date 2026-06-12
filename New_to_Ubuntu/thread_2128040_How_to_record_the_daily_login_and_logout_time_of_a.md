---
title: "How to record the daily login and logout time of a particular user?"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by hhtmp88 on 2013-03-21
as titled.

Thanks for any kind of help!

---

### Post by DuckHook on 2013-03-22
All user access activity is recorded in /var/log/auth.log which is replaced every few days so that the older data is being spun off to auth.log.1 auth.log.2 etc.

You can look for individual users by building a script (which is beyond my knowledge). A quick and dirty method would be to filter through grep, e.g.:```
cat /var/log/auth.log | grep user_name
```

---

### Post by sgy on 2013-03-22
Try putting the following in a .bash_login file.
```

punchcard="$HOME/.punchcard"
echo "in:" >> $punchcard
date >> $punchcard

```
And this in the .bash_logout file.
```

punchcard="$HOME/.punchcard"
echo "out:" >> $punchcard
date >> $punchcard

```
Both in the user's home directory.

The file  .punchard will contain the time of login and logout.

---

### Post by Frogs Hair on 2013-03-22
You can see if this is of value or not. [http://www.cyberciti.biz/tips/howto-log-user-activity-using-process-accounting.html](http://www.cyberciti.biz/tips/howto-log-user-activity-using-process-accounting.html)

---

### Post by hhtmp88 on 2013-04-07
Thanks all for your comments!
-> will try them out!

---

