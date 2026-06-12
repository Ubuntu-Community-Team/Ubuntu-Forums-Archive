---
title: "terminal messed up"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-09-18
I am trying out xfce and every time I open the terminal I get an old no good command . I tried reset, reset and clear, history -c,and reinstalling the terminal but can't get rid of it. 

```
bash: alias: pkill -u cmcanulty: not found
cmcanulty@HPTech:~$ 
```

---

### Post by The Cog on 2012-09-18
I wonder if that command is tucked inside your **.bashrc** or your **.profile** file, so that it runs every time a new terminal is opened. You could try and edit these two files to have a look:
> leafpad .bashrc
leafpad .profile

**P.S.**
After changing these files, you will probably have to log out and in again before you see the change take effect.

---

### Post by cmcanulty on 2012-09-18
thanks that did it without even logging out

---

### Post by Cheesemill on 2012-09-18
What are the contents of your ~/.bashrc

---

