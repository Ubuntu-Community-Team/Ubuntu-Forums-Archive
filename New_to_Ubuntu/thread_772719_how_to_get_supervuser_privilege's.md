---
title: "how to get supervuser privilege's"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by seymone on 2008-04-28
Hi, I'm getting the request as I try to load dpkg. does anyone know how i get superuser privilegs? 

dpkg: requested operation requires superuser privilege

Thanks

---

### Post by arseniy on 2008-04-28
sudo?

---

### Post by seymone on 2008-04-28
thank you!

---

### Post by arseniy on 2008-04-28
No problem!

---

### Post by lukeisthecoolest on 2008-04-28
im still having trouble gaining superuser status on terminal :/ do u perhaps have a screenshot or how to use sudo

---

### Post by i_have_a_sempron on 2008-04-28
> **lukeisthecoolest said:**
> im still having trouble gaining superuser status on terminal :/ do u perhaps have a screenshot or how to use sudo

When you open terminal use:

```
sudo bash
```

Then type in your pword and then you'll be using a root shell.

---

### Post by Oldsoldier2003 on 2008-04-28
> **lukeisthecoolest said:**
> im still having trouble gaining superuser status on terminal :/ do u perhaps have a screenshot or how to use sudo
to run a command:
```
sudo <somecommand>
```

to run a session as root:

```
sudo -i
```
then just do your commands, sudo no longer required.

to finish your sudo root session:

```
exit
```

---

### Post by DaveM753 on 2008-04-28
Just put "sudo" in front of any command you're trying to use.  For instance, to install an application, instead of typing
apt-get install applicationname
type
sudo apt-get install applicationname
You'll be prompted for a password, which is going to be your own password.  Of course, you'll be running this command as the "super user" which is a security risk, so make sure you know what you're doing!

---

### Post by john test on 2008-04-28
> **lukeisthecoolest said:**
> im still having trouble gaining superuser status on terminal :/ do u perhaps have a screenshot or how to use sudo

You can do sudo command (for what ever command you are trying to execute) or you can do SUDO SU which will make you supervisor or super user for the rest of the terminal session

---

### Post by lukeisthecoolest on 2008-04-28
how would i click okay in this pic?

---

### Post by Oldsoldier2003 on 2008-04-28
tab until its highlighted then hit enter

---

### Post by perlluver on 2008-04-28
> **lukeisthecoolest said:**
> how would i click okay in this pic?

Press the tab key on your keyboard then press enter.

---

### Post by lukeisthecoolest on 2008-04-28
wow, u guys r extremely helpful. I hope good karma comes to you

---

