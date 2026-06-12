---
title: "Automating script command with every session/terminal login"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by siddharth007 on 2012-12-31
Hi everyone.I want to record the user activities on one of my servers(Ubuntu).There are several users which remotely login(through ssh).There is a command in ubuntu which allows to record the user activities in a session.It is the **script** command which records all the user's on-screen activity(offcourse on just a terminal) once it is executed manually something like this
**script -a filename**

It saves the onscreen activities to the specified file name after you press ctrl+D to stop the command.

However,all this needs to be done manually.I want to automate the whole thing i.e script should run automatically when a user logs in remotely or even if a terminal is opened on the local system.How do i accomplish this.Is cron the way to do it or what else.I want to invoke the command automatically.

---

### Post by fdrake on 2012-12-31
> **siddharth007 said:**
> Hi everyone.I want to record the user activities on one of my servers(Ubuntu).There are several users which remotely login(through ssh).There is a command in ubuntu which allows to record the user activities in a session.It is the **script** command which records all the user's on-screen activity(offcourse on just a terminal) once it is executed manually something like this
**script -a filename**

It saves the onscreen activities to the specified file name after you press ctrl+D to stop the command.

However,all this needs to be done manually.I want to automate the whole thing i.e script should run automatically when a user logs in remotely or even if a terminal is opened on the local system.How do i accomplish this.Is cron the way to do it or what else.I want to invoke the command automatically.
man history
man logger

---

### Post by siddharth007 on 2012-12-31
> **fdrake said:**
> man history

Hey dude **history **command is alright.But the **script **command can record the output of all commands too.Try using this command on your termainal
[B]script -a filename

[/B]to save and quit the script daemon use ctrl+D .Then check out the **filename **you specified earlier.You will find out the difference.:)

---

### Post by catalin.vasilescu on 2012-12-31
So you want that the *script* command to start running at each user session start(login) and log the activity ?

---

### Post by siddharth007 on 2012-12-31
> **catalin.vasilescu said:**
> So you want that the *script* command to start running at each user session start(login) and log the activity ?

Yes dear friend thats what i want.Can you help me plz....

---

### Post by fdrake on 2012-12-31
> **siddharth007 said:**
> Hey dude **history **command is alright.But the **script **command can record the output of all commands too.Try using this command on your termainal
[B]script -a filename

[/B]to save and quit the script daemon use ctrl+D .Then check out the **filename **you specified earlier.You will find out the difference.:)i see now what you mean.. I read the post too quickly.

well you can change the /etc/passwd file and assign the terminal/console directly to script for all the desidered users.
user:x:1000:1000:servername,,,:/home/user:/bin/bash script -e filename

---

### Post by siddharth007 on 2012-12-31
> **fdrake said:**
> i see now what you mean.. I read the post too quickly.

well you can change the /etc/passwd file and assign the terminal/console directly to script for all the desidered users.
user:x:1000:1000:servername,,,:/home/user:/bin/bash script -e filename

I tried it but its not working.:-( Moreover its the root/sudo user for which i need it.

---

### Post by fdrake on 2012-12-31
> **siddharth007 said:**
> I tried it but its not working.:-( Moreover its the  for which i need it.
Maybe the sbace between the commands creates an error (reset everything like before)
root and sudo user are not the same:
[http://teknoteknik.wordpress.com/tag/sudo-vs-root/](http://teknoteknik.wordpress.com/tag/sudo-vs-root/)

> Hi everyone.I want to record the user activities on one of my servers(Ubuntu).There are several users which remotely login(through ssh).

do not enable root to login with ssh use a sudo user instead.

also if these users have sudo privileges, they are able to stop the script command. The easiest way is add the command to the ~/.bashrc
```

echo "script -a ~./filename" >> ~/.bashrc
echo "Bash Script has been started" >> ~/.bashrc

```
logout ; login;

---

### Post by matt_symes on 2012-12-31
Hi

> Moreover its the root/sudo user for which i need it.

If you're just interested in sudo commands a user may run then look in 

```
/var/log/auth.log
```

The root account should be disabled in Ubuntu.

Kind regards

---

### Post by squakie on 2012-12-31
Personally, I'd be a bit concerned about anyone other than the server administrator being able to use sudo in the first place - you can block that.  While it is probably legitimate, I also always get a little leary when someone starts talking about key loggers - it leans a little of center.

---

### Post by siddharth007 on 2013-01-02
> **fdrake said:**
> Maybe the sbace between the commands creates an error (reset everything like before)
root and sudo user are not the same:
[http://teknoteknik.wordpress.com/tag/sudo-vs-root/](http://teknoteknik.wordpress.com/tag/sudo-vs-root/)



do not enable root to login with ssh use a sudo user instead.

also if these users have sudo privileges, they are able to stop the script command. The easiest way is add the command to the ~/.bashrc
```

echo "script -a ~./filename" >> ~/.bashrc
echo "Bash Script has been started" >> ~/.bashrc

```logout ; login;

I tried putting the above two lines in .bashrc but its not working.It is just putting the stuff under quotes to the .bashrc file. Infact, i had been trying to put the script command into the .bashrc file but its showing up error on login.Please help:(

---

### Post by fdrake on 2013-01-02
what's the error?


edit : I tried and I noticed I made a typo:

```

echo "script -a ~/filename" >> ~/.bashrc
echo "Bash Script has been started" >> ~/.bashrc


```

---

### Post by siddharth007 on 2013-01-02
> **fdrake said:**
> what's the error?


edit : I tried and I noticed I made a typo:

```

echo "script -a ~/filename" >> ~/.bashrc
echo "Bash Script has been started" >> ~/.bashrc


```

Putting the above two lines into .bashrc file will cause the lines to be written again and again every time a login terminal is opened.Anyways,i appreciate your help.I found a solution for my problem.

Instead of putting things in .bashrc, i am using the .profile file(.bash_profile on some systems).Just enter this command in the .profile file

**script -aq filename** 

The .profile(or .bash_profile file) can be found in the same location as .bashrc which is the user's home directory. Thanx everyone for the replies.Regards.

---

