---
title: "am I using root user privilege?"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by braluca on 2013-05-25
Just finish to install lubuntu.
satisfied till now (5 min boot with WinXP less than 1 with lubuntu, the same for turn off)!!!!
During installation process system asked me name.
When I make login I use that name
When I install some new sw I must give pwd for that name.
Now, question is, is this name the one has root privilege?

---

### Post by steeldriver on 2013-05-25
That user has the ability to execute programs with root privileges through the 'sudo' mechanism - there's a good explanation here --> [URL="https://help.ubuntu.com/community/RootSudo"]https://help.ubuntu.com/community/RootSudo
[/URL]

---

### Post by deadflowr on 2013-05-25
Don't know what you mean, but the first user created during installation gets admin rights.
You can execute those admin rights through[ sudo]("https://help.ubuntu.com/community/RootSudo"), or when a program asks for a password to use those admin rights, which gives the user elevated privileges.

---

### Post by grahammechanical on 2013-05-25
If you were using root user privileges then the OS would not be asking you for a password. We only get administrator/root privileges when we put in our password at the time we asked to authenticate an action that we are trying to. The administrator privileges last as long as it takes to carry out that action and they expire after a few minutes.

For example, we use the Software Centre to install an application and we are asked to authenticate. Once the application is installed and the software Centre is closed then our access as administrator is removed. All the other times we are using the OS it is as a standard user. 

Regards.

---

### Post by marlow59 on 2013-05-25
You can't logging to Ubuntu with a super user account anyway, all you can do is get these privileges by running the ```
 sudo 
``` command before executing yours :). Do not forget to mark the thread as solved if it's the case.

---

