---
title: "I cannot become superuser."
date: 2008-09-06
forum: New to Ubuntu
---

### Post by broivan on 2008-09-06
How can I get to the # prompt?

---

### Post by Elfy on 2008-09-06
what are you trying to do as root? You can use sudo to be the superuser

sudo command

---

### Post by kjohansen on 2008-09-06
Your question is a little vague.

You can get to a terminal by going to Applications->Accessories->Terminal

Then if you need to run a command as a superuser you can use the sudo command.

sudo <command>

> 
Be very careful that you know what you are doing whenever you execute commands in the terminal, especially as super user! 


---

### Post by malathion on 2008-09-06
Another way to get into a terminal is to press Alt-f2 and type "gnome-terminal"

Once you are there, the syntax to execute commands as superuser is:

```
sudo <command>
```

Be very careful that you know what you are doing whenever you execute commands in the terminal, especially as super user! :KS

---

### Post by ~LoKe on 2008-09-06
sudo su

---

