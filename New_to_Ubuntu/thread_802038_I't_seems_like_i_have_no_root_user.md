---
title: "I't seems like i have no root user :/  ?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Happy-Cheese on 2008-05-21
I've installed Ubuntu Yesterday and im a total beginner :D

when i installed it it didnt said anything about a root user. But i entered an username and a password for a normal user. but it desent seems like that user is "root".
Can i see somewere if i have a root user or something?

---

### Post by wormser on 2008-05-21
Ubuntu uses sudo instead of root.  More [here]("https://wiki.ubuntu.com/RootSudo").

---

### Post by kellemes on 2008-05-21
> **Happy-Cheese said:**
> I've installed Ubuntu Yesterday and im a total beginner :D

when i installed it it didnt said anything about a root user. But i entered an username and a password for a normal user. but it desent seems like that user is "root".
Can i see somewere if i have a root user or something?

This explains it all.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Happy-Cheese on 2008-05-21
OMG that was fast :D
Ill try read that U gave me

---

### Post by Happy-Cheese on 2008-05-21
Does that meens  that when i wanna run a file as "root" ill have to write:
sudo filename.run ?

---

### Post by kellemes on 2008-05-21
> **Happy-Cheese said:**
> Does that meens  that when i wanna run a file as "root" ill have to write:
sudo filename.run ?

```
sudo ./filename.run
```

sudo asks for your (user) password and gives you root-privileges.

---

### Post by Happy-Cheese on 2008-05-21
Ty very much :)

---

### Post by Happy-Cheese on 2008-05-21
No wait it saya: SH: cant open filename.run

---

### Post by Maestro23 on 2008-05-21
> **Happy-Cheese said:**
> No wait it saya: SH: cant open filename.run

Must make it executable:

> chmod +x filename.run

./filename.run

or

> sudo sh filename.run

---

### Post by Happy-Cheese on 2008-05-21
Ohh now it works Ty:D

---

### Post by leboea on 2008-05-21
Ubuntu does not allow you to directly login as root user, you can execute the commands as the root by prefix your commands with sudo.
for example assume that this sign "$" is your Prompt on the shell then you can type: **$sudo command_name**
Where command_name is the name of the command you want to execute

OR

if you want to login as the root on the command prompt, just type: sudo -i and provide you password and start working as the root user. Do not forget to logout when done,by typing **$exit **. 

I hope you have find the solution if not let me know!

---

### Post by Maestro23 on 2008-05-21
> **Happy-Cheese said:**
> Ohh now it works Ty:D

No prob.  Please mark this thread "Solved". 

Thanks. :smile:

---

