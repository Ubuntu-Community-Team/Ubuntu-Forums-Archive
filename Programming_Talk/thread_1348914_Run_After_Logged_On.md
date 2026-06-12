---
title: "Run After Logged On"
date: 2009-12-07
forum: Programming Talk
---

### Post by Chamillionaire2 on 2009-12-07
What's Up?

OK, So I just tried the update-rc.d method of running my script upon start-up, But I didn't know it ran in the boot process, I thought it did it after you logged on.

The problem is, Is my script is one without end, And of course that means that if you did use the above method you wouldn't be able to login, due to the script constantly running. So my question is how'd I run a script after any users logs in?

Thanks Bye.

---

### Post by dwhitney67 on 2009-12-07
If the script runs without end, why not run it in the background?

In /etc/rc.local:
```

/path/to/script &

```
There are other ways to 'skin the cat', but with the scant details you have provided, I will refrain from commenting further.

---

### Post by Barriehie on 2009-12-08
I've got one that runs at boot time and I want it to run all the time but in case I want to stop it I've got it checking for the existence of a stop file to break the loop.

Barrie

---

