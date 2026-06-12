---
title: "password problem in ubuntu 10.1"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by tbrownarcher on 2012-08-26
I unpacked an old computer with ubuntu 10.1 on it and when I went to log in the password i remember is not the right one.... how can i view it or change it?.  It seems I'm logged in even though it tells me the password is incorrect.  I'm using the computer right now but there are many things I can't seem to do.  I would like to get this right but dont' know how.  can someone help me with the password?

thanks,
Nate

---

### Post by Bashing-om on 2012-08-26
nate;

 You are not the first. Look at this link for resolution:
[http://ubuntuforums.org/showthread.php?t=896573](http://ubuntuforums.org/showthread.php?t=896573)

[INDENT]that shud help <==BDQ
[/INDENT]

---

### Post by NikTh on 2012-08-26
If you cannot login , the follow these steps to resset your password.. 

1. Boot from recovery mode 
2. Click on Root 
3 . First give this command ```
mount -o rw,remount /
``` 
4. Then give this command ```
passwd <username>
``` 
replace <username> with your actual username (I assume your remember (know) it)
Thank you.

---

### Post by tbrownarcher on 2012-08-26
i logged in as root in the recovery mode and changed my password and everything looked well but it don't work. 

Actually when i boot up i'm given a network pass key window and i type that in and and the network connects and I'm given another small window asking for my keyring password.  Maybe this is not the same thing as my login password .  
Could someone help me with what i' dealing with here?

thanks,
Nate

---

### Post by Cheesemill on 2012-08-26
For a slightly more detailed explanation, but exactly the same method as NikTh posted above take a look at the Psychocats website:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by NikTh on 2012-08-26
> **tbrownarcher said:**
> i logged in as root in the recovery mode and changed my password and everything looked well but it don't work. 

Actually when i boot up i'm given a network pass key window and i type that in and and the network connects and I'm given another small window asking for my keyring password.  Maybe this is not the same thing as my login password .  
Could someone help me with what i' dealing with here?

thanks,
Nate

Yes this is not the same problem. Now I assume you can login with your new password without a problem . Am i right ? 

As for the keyring thing , open NetworkManager from terminal (ctrl+alt+t) write 
```
nm-connection-editor
``` and edit your connection settings , be sure that **"Available to all users" is ticked. **

Thank you.

---

