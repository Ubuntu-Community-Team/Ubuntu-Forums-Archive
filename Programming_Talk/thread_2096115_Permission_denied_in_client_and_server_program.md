---
title: "Permission denied in client and server program"
date: 2012-12-19
forum: Programming Talk
---

### Post by sanda199 on 2012-12-19
Hi everyone, I need your valuable help. I tried to write client and server program in 2 ubuntu computers. After I run both program, I got permission denied at the terminal. If anyone have experience of this, can u pls help me?


Thanks for your help.

---

### Post by Tony Flury on 2012-12-27
Permission denied errors should be easy to fix.

you need to make sure :
[LIST=1]
[*]You have execution permission on the drive (you should have in most directories in a standard install)
[*]The executable is owned by you , or a group you belong too - try using the groups command - and the "ls -l" to check whether you own it
[*]Check that the file has the right execute bit set.
[/LIST]
To help - post the results of the following commands : 
```

groups

```
and 
```

ls -l

```
in the relevant directory of course.

remember to add code tags round your output.

---

