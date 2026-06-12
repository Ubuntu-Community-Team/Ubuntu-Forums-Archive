---
title: "scripting question"
date: 2009-05-27
forum: Programming Talk
---

### Post by wlraider70 on 2009-05-27
ok im just playing with scripting, and I am having a prolem with getting the password to enter.

....
#!/bin/bash
command sudo anything

sleep 10

pwd yourmom

....


the password wont enter, i tried taking out the sleep.

is the pwd command bad or wrong ?

---

### Post by samjh on 2009-05-27
Eh?  Password?  You're using the wrong command, I suspect.

pwd is for displaying the current working directory ("print working directory").

---

### Post by _Purple_ on 2009-05-27
You can add the script to the sudoers file to run it without using password.

---

### Post by AnRa on 2009-05-27
I think that you are trying to do something like this:
```
echo "*password*" | sudo -S *command*
```
or
```
sudo -S *command* < */path/to/filewithpassword*
```

---

