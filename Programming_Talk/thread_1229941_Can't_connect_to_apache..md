---
title: "Can't connect to apache."
date: 2009-08-02
forum: Programming Talk
---

### Post by liorz1984 on 2009-08-02
Hello,
I installed apache2 from the reps , and i can't seem to connect to the default index page.
Iv'e tried more or less everything, Of course, i configured the .conf file properly, changed the servername to localhost, and in my laptop using the same conf file it works.
-I tried to change the port to any other port => didn't work either.
-Checked if another server is running
-checked netstats and saw that the server is on and listening.

What am i missing? 
Thanks.

---

### Post by Dill on 2009-08-02
Just to make sure, have you tried restarting Apache?

```
sudo /etc/init.d/apache2 restart
```

Also, you mentioned that "in my laptop using the same conf file it works." Do you mean that you can connect locally on your laptop but not from other computers, or something different? I guess what I'm asking is... *what* works?

Cheers,
Dill

---

### Post by credobyte on 2009-08-02
Do you have a firewall/router ?

---

### Post by liorz1984 on 2009-08-03
Hey, I did restart the server after each change in the conf file , of course.
The problem is, I can't connect from my local computer (i.e. localhost:80), I wasn't trying to connect from outside.
In my laptop, I can connect to localhost:80 using the same conf file...
That's what I meant.

Maybe the problem is with a local linux firewall configuration?.. (iptables? although I don't see it in the services section)

---

