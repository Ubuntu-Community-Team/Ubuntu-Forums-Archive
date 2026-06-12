---
title: "help"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by coffee7 on 2012-11-07
i buy new laptop dell inspiron 5520 ivy so i install ubuntu 12.04 beside windows7 and when start the laptop before i choose between windows or ubuntu appear message tell me can't read "mount file" and then i choose ubuntu and run normally but the problem is when open another directory or when add another account or add wireless network ask me about password of root what does mean??????????????please help me 

[RIGHT]thanx[/RIGHT]

---

### Post by drmrgd on 2012-11-07
Here's some documentation that might help clear up the root question for you.  In short, even though you're an administrator of the computer, you're not root, which has been disabled by default.  However, being an administrator gives you the rights to be able to act as root on a single command by command basis.  This is achieved by issuing 'sudo' in front of the command you wish to run.  Regular users do not have the ability to issue 'sudo' and that is how administrative roles are distinct under Ubuntu.  Again, here's more documentation that goes a little further and probably describes this a little more clearly:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by coffee7 on 2012-11-07
> **drmrgd said:**
> Here's some documentation that might help clear up the root question for you.  In short, even though you're an administrator of the computer, you're not root, which has been disabled by default.  However, being an administrator gives you the rights to be able to act as root on a single command by command basis.  This is achieved by issuing 'sudo' in front of the command you wish to run.  Regular users do not have the ability to issue 'sudo' and that is how administrative roles are distinct under Ubuntu.  Again, here's more documentation that goes a little further and probably describes this a little more clearly:

thanx for answer me but because this problem i cant login as admin but as guest so how can solve this problem?

---

### Post by snowpine on 2012-11-07
Here are easy instructions to reset the password for your admin user (the first user you created when you installed Ubuntu):

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

And some info to troubleshoot a broken "sudo":

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by zealibib slaughter on 2012-11-07
at the grub menu you can start in recovery mode then launch a root shell.  In the root shell you can add a user with sudo powers with ```
adduser <usernane> --group admin 
``` then assign that user a password with ```
passwd <username>
```

---

