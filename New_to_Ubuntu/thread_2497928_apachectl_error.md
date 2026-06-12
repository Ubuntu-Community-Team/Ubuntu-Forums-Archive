---
title: "apachectl error"
date: 2024-05-23
forum: New to Ubuntu
---

### Post by flywithjulian on 2024-05-23
Hi guys, 
I'm instaling Wordpress using this tutorial: [https://www.youtube.com/watch?v=pOESHd1G-HI&t=1399s](https://www.youtube.com/watch?v=pOESHd1G-HI&t=1399s)
at 23:19 im stuck.


apachectl -t give me:
Command 'apachectl' is available in the following places
* /sbin/apachectl
* /usr/sbin/apachectl
The command could not be located because '/sbin:/usr/sbin' is not included  the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
apachectl: command not found


What do I do to fix this issue?

Ubuntu 24.04 LTS

---

### Post by yancek on 2024-05-23
The apachectl -t should output Syntax OK if there are no problems.  When you see the error message "'/sbin:/usr/sbin' is not included  the PATH environment variable", you should run the following from a terminal and a user should have both in the PATH.  They should show on a default system.  Have you made any changes to your user PATH?

```
 echo $PATH
```

---

### Post by flywithjulian on 2024-05-23
Not as I'm aware of.
I've follow the tutorial to the letter.

I'll try  echo $PATH this evening and keep it posted.

---

### Post by yancek on 2024-05-23
Some of the commands require sudo so are you using sudo when suggested.  If you run the echo $PATH command, it should output th various directories in your user path which should include both '/sbin:/usr/sbin'.

---

### Post by flywithjulian on 2024-05-23
echo $PATH give me that:
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/snap/bin

---

### Post by flywithjulian on 2024-05-23
But if I use the command sudo apachectl -t, I have Syntax OK.

Does that means I'm good to continue?

---

### Post by yancek on 2024-05-23
If I run the apachectl -t command, I get the Syntax OK as either a user or root (sudo) but the PATH info is different.  If you are following the tutorial I would suggest you pay close attention to when sudo is used.  If you are doing commands as a regular user, you might try the full path as suggested: 

 >  /sbin/apachectl -t
  /usr/sbin/apachectl -t

I'm not expert on Apache and know nothing about wordpress.

---

