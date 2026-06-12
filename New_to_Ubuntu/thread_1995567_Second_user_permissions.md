---
title: "Second user permissions"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by gredawarha on 2012-06-03
Hello all

I use a cpu frequency controller that sits in the panel.  I have added my partner as a user, she can see the frequency icon in the panel but when attempting to change the controller she  needs my administrator password.

How do I allow her to change the clock speed without my passowrd?

---

### Post by Senior_Buckethead on 2012-06-04
Silly question, I apologize. But i think the direction you should perhaps go is that of file permissions. Take a look at this article about assigning root privileges to more than one user:
[http://linuxgazette.net/issue48/tag/16.html](http://linuxgazette.net/issue48/tag/16.html)
I can think of one test off the top of my head, get your partner to log in as a regular user and using terminal, invoke the program concerned and see what error messages if any pop up.
Eg.
```

glenn@design:~$ nautilus
glenn@design:~$ 

```
Hope there is something in there that helps.

Glenn.

---

### Post by zombifier25 on 2012-06-04
Please do not follow that tutorial. It's dangerous.

If you want your partner's user to be able to do admin tasks, you can add her to the "admin" (Ubuntu 11.10 or lower) or "sudo" group (Ubuntu 12.04)

```
sudo adduser username admin
```
or ```
sudo adduser username sudo
```

EDIT: I think she will still be asked for HER password though. There may be an easier way to do this (maybe setuid or PolicyKit). What software are you using in order to control the CPU's freq?

---

### Post by gredawarha on 2012-06-05
Hi

I am using a CPU frequency changer by Artem Popov [https://launchpad.net/~artfwo/+archive/ppa](https://launchpad.net/~artfwo/+archive/ppa)

I could give my partner admin rights but I dont want her having complete access.

---

### Post by steeldriver on 2012-06-05
> **gredawarha said:**
> I could give my partner admin rights but I dont want her having complete access.

I think you could create a new group ('tweakers' or whatever) and include your partner (and yourself) in that, then add it to your sudoers file with permissions to run ONLY that application - see  

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

[you can also add individuals via username instead of group, but imo it's easier to manage access via groups - if you decide to remove permissions later you don't need to change sudoers again, just add or remove them from the group]

---

