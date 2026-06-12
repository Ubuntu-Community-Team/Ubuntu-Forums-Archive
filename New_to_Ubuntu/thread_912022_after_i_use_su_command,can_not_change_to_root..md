---
title: "after i use su command,can not change to root."
date: 2008-09-06
forum: New to Ubuntu
---

### Post by patriotzhou on 2008-09-06
i open Terminal,
try use: su ,
type in the root password,
but come out this:

```
sla@sla:~$ su
Password: 
Cannot execute q: No such file or directory
sla@sla:~$ 

```

---

### Post by patriotzhou on 2008-09-06
where is q?
how to edit?

---

### Post by Ryadt on 2008-09-06
Use sudo instead.

---

### Post by patriotzhou on 2008-09-06
I know
Sudo can work
but why su can not change?
something wrong with the settings?

---

### Post by hyper_ch on 2008-09-06
root user is not activated and forum policy is that on the forums one shall not post how to activate it.

Have a read at the root-login-tutorial sticky in the security subforum.

---

### Post by jhenager on 2008-09-06
deleted post

---

### Post by zujenbe on 2008-09-06
hang on, are u simply just typing su?
its:

su - root

not just su -(nothing)

---

### Post by jhenager on 2008-09-06
> **hyper_ch said:**
> root user is not activated and forum policy is that on the forums one shall not post how to activate it.

Have a read at the root-login-tutorial sticky in the security subforum.

forum policy? I must have missed something.
I thought the forum's purpose was to help people.

---

### Post by Ryadt on 2008-09-06
> **jhenager said:**
> forum policy? I must have missed something.
I thought the forum's purpose was to help people.

READ THIS: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by jhenager on 2008-09-06
> **Ryadt said:**
> READ THIS: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

Got it.
This must be new, because I asked this question about a year or two ago, and was given the answer on this forum.
Sudo works for me most of the time anyway.

---

### Post by patriotzhou on 2008-09-06
I try use su root,same issue.
Before I just su,and type inside the root password,can work
but now can not.

sla@sla:~$ su root
Password: 
Cannot execute q: No such file or directory
sla@sla:~$

---

### Post by hyper_ch on 2008-09-06
jhenager:

Don't worry, no harm done :)

---

### Post by Ryadt on 2008-09-06
You won't get help in this forum on this question as it is against the forum's policy.......
Read this link again: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
and quit asking this question.

---

### Post by patriotzhou on 2008-09-06
I just want to ask after I type in su,and press enter key,
what the Terminal do?
It try to find a file or folder named q,right?
So which file save this setting,someone know?
If I know the file,I can edit it ,rite?

---

### Post by sisco311 on 2008-09-06
> **patriotzhou said:**
> I just want to ask after I type in su,and press enter key,
what the Terminal do?
It try to find a file or folder named q,right?
So which file save this setting,someone know?
If I know the file,I can edit it ,rite?
/root/.bashrc

---

### Post by patriotzhou on 2008-09-06
I try edit the file,can not find.
I try to delete,still same.
How?

---

### Post by sisco311 on 2008-09-06
post the output of:
```
cat /etc/passwd
```

---

### Post by Dougie187 on 2008-09-06
Even though we can't help him with su, he does have an issue with the su not working how it should. He should get something similar to this as output instead of what he is getting.
```
su: Authentication failure
```

---

### Post by patriotzhou on 2008-09-06
ok,done.
su will read the settings at file /etc/passwd
change the p to /bin/bash,can work now,thanks!

---

### Post by sisco311 on 2008-09-06
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**

---

### Post by abraracourcix on 2008-11-05
Great guys, this post helped me too.

Problem showed up after playing with chsh i guess.


Thanks!

---

