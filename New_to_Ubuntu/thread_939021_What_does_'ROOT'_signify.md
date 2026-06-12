---
title: "What does 'ROOT' signify?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by iamshawnrice on 2008-10-05
Hi.

I was attempting to install the MS Core Fonts, but ran across this error:

wawny@sgt-pepper:~$ $sudo apt-get install msttcorefonts
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

What is root, and how do I become it?  Do I even need to?

---

### Post by oldos2er on 2008-10-05
The "sudo' command should've allowed you to temporarily become root (administrator). Were you asked for your password?

---

### Post by scragar on 2008-10-05
you become root for the length of the command when you start it with sudo...
```

sudo apt-get install msttcorefonts

```
Please note that you can only have 1 package manager running at once to prevent conflicts, so if you are running synaptic or the update manager wait for that to finish before attempting to run the command again.

it also looks like you have an extra $ at the start of the command, there is no $ in the command, that's often just used to signify that the command is to be run as a normal user(with the # indicating a command needing root perms)

---

### Post by WRDN on 2008-10-05
You put a "$" before "sudo", so the computer read the command "$sudo". The command should actually be:

```
sudo apt-get install msttcorefonts
```

---

### Post by Gutt on 2008-10-05
```
sudo [what ever you want to be root for]
```


>  /root, the Unix superuser's home directory in the Filesystem Hierarchy Standard


---

### Post by Dudman on 2008-10-05
Root is kind of the same as `Administrator' on windows. 

Some programs require administrator permissions to run. Just do "sudo [command]" to run that command as root.

Also, i see you typed $sudo. All the '$' means is to run it at a command prompt as a normal user. So if i were to say:

Type this command to install coolprogram1.0
$ sudo apt-get install coolprogram1.0

that means just type in "sudo apt-get install coolprogram1.0".

-Dudman

---

### Post by iamshawnrice on 2008-10-05
Word...Thanks.

---

