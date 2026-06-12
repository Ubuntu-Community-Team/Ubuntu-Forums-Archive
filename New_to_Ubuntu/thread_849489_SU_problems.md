---
title: "SU problems"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by drmynatt on 2008-07-04
Hi group,  I just downloaded and installed 8.04 and my SU password disappeared. I'm trying to load JDK and I cannot create a dir to extract it to nor extract it.  Ugh!

How do I change my SU password, or re-establish it?

Appreciate help,

Dave

---

### Post by sancho panza on 2008-07-04
I dont know what you mean by SU password. I assume its the regular user password which u use while sudoing. 
If thats correct, you can change it via System>admin>user settings.
It can also be dont via command prompt. Try googling it if needed.

EDIT: If u have forgotten your password, then u'll have to boot using the recovery mode to reset the password. [Here are the details]("http://www.psychocats.net/ubuntu/resetpassword").

---

### Post by cariboo on 2008-07-04
The su command stands for switch user. You use it to switch to another user. In Ubuntu the root password is not set. You use sudo (super user do) to do the same things you would do as root in other distributions. to create a directory that is not in your home directory, in a terminal type the following:

```
sudo mkdir <directory>
```

Jim

---

### Post by drmynatt on 2008-07-04
At the command prompt, I type 'su' to enter admin priveleges so I can create things or install apps. It asks for a password and the one I used to use doesn't work. I can't even add new users. How can I reestablish a super user with all priveleges?

Thanks,

Dave

---

### Post by sancho panza on 2008-07-04
As we mentioned above, you do not need to use su in ubuntu. You only need to add sudo before any command that need superuser privileges to run. There is no root user in ubuntu; the main user is the root, the superuser.

Reread the responses above and get back if they still dont solve ur problem.

---

### Post by sancho panza on 2008-07-04
IGNORE THIS POST. My above response got repeated here for some reason, so I have deleted it.

---

### Post by drmynatt on 2008-07-04
Ooo. So at the prompt, I enter 'sudo' and if it asks for a password I use my signon password? I'll do it!

By the way, I'm trying to add java SDK.

Thanks,

Dave

---

### Post by sancho panza on 2008-07-04
Bingo! The primary user is always a superuser/root, but runs with lower privileges. Anytime a application needs higher privileges, it asks the superuser for his password, which works like the root password.

Cheers!

---

### Post by arpanaut on 2008-07-04
Good Read:

[https://help.ubuntu.com/community/RootSudo3](https://help.ubuntu.com/community/RootSudo3)

another one:

[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by txcrackers on 2008-07-04
> **drmynatt said:**
> 
By the way, I'm trying to add java SDK.


Use the JDK from the repositories and you won't have to go through all this. Use synaptic/adept/whatever to install the SDK. Make sure that you don't have any other Java "type" packages installed (GCJ, OpenJDK, etc.).

---

