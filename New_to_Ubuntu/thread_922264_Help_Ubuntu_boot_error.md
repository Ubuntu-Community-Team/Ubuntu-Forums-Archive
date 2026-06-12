---
title: "Help Ubuntu boot error"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by janne5011 on 2008-09-17
Hello my Ubuntu (latest version) boots but I can see only the desktop background color at boot screen after login(brown).
I have cronjobs in it so I know evrything else is ok,but
Its really important i can have it work again.
so waht can I do

---

### Post by whizbaby on 2008-09-17
It looks to me as if X is not starting properly. How about giving us the output of

```
sudo cat /var/log/Xorg.0.log > myxorg.log
```

You can switch to a non-graphical login by hitting ctrl-alt-F1 (or F2 through F6 too). Then login with your username and execute the command. Then copy it to another machine

```
scp myxorg.log username@othermachine:
```

Then post the log from the other machine (I believe you have one since you are writing this thread :))

---

### Post by janne5011 on 2008-09-17
whizaby thanks for reply.

 I took a chance and installed xfce from rescue boot and now it works again. but my usual vanlilla ubuntu desktop was lost in the process.
but xfce seems nice so I look at this as solved.
I dont dare to do anythingmore this is a importand server.
Now do a backup:-o

---

### Post by whizbaby on 2008-09-17
> **janne5011 said:**
> this is an important server
And youre running X on it? o_O
It might not be a big problem in your case, but installing X also means being more vulnerable, as every software that is not explicitely needed for the services provided is considered a potential security risk (on a professional server). Trying to control the server by console/ssh on the long run would be safer for sure.

But right, xfce is a nice small desktop, I enjoy using it. e17 is worth a look too if you use the dunnewind repository ([http://www.dunnewind.net/ubuntu](http://www.dunnewind.net/ubuntu) hardy e17).

---

