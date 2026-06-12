---
title: "New user needs help installing software"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by carbondalebaby on 2011-11-13
hi im new to ubuntu and completely confused i dont know how to install apps from the software store for ubuntu i tryed some of the codes here and i got sudo password i tryed to type in my password but the command promt wouldnt let me what am i doing wrong?!?! please help!!!!!!!!!!!!!!!!

---

### Post by oldos2er on 2011-11-14
It's normal not to see anything echoed to the screen when entering your password in terminal (and it's *not* for security, it's an old bug that will probably never be fixed.)

Help installing software: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre](http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre)

---

### Post by matt_symes on 2011-11-14
Hi

It is possible to get feedback from sudo. Add pwfeedback to the defaults line in your sudoers file.

Use

```
sudo visudo
```to edit the file.

Find this line
```

Defaults        env_reset
```and change to
```

Defaults        env_reset, pwfeedback
```You then get feedback like this.

```
matthew@matthew-laptop:~$ sudo apt-get update
[sudo] password for matthew: **********
```

Maybe not a step for a total beginner though.

Kind regards

---

### Post by critin on 2011-11-14
> **carbondalebaby said:**
> hi im new to ubuntu and completely confused i dont know how to install apps from the software store for ubuntu i tryed some of the codes here and i got sudo password i tryed to type in my password but the command promt wouldnt let me what am i doing wrong?!?! please help!!!!!!!!!!!!!!!!

I assume you're talking of the 'Software Center"?  When you click --INSTALL-- at the right of the subject, it doesn't install? You shouldn't need to use codes.

The password in the terminal will not show, that's normal, just enter the password, hit enter, and it will work.
If you're talking of the password for authentication to actually install from the Software Center, you don't type 'sudo', just the password.

---

