---
title: "Username and computer name disappear when I change the user account"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by Aeront on 2013-11-17
In ubuntu command lines, it begins with 'username@computername' , for example, tom@tomcomputer:~$, where tom is an original username when installing ubuntu, and tomcomputer is the name of the computer. However, When I create a new user account , and name it peter, I log in peter, the command line begin with '$'. How can I fix it? Thank you.

---

### Post by Impavidus on 2013-11-17
The user name shown is the name of the current user. The prompt is defined by the variable PS1, which is defined in .bashrc. Compare the .bashrc files of users tom and peter and see what's different in the definition of PS1. \u means username, \h hostname, \w working directory.

---

### Post by steeldriver on 2013-11-17
I'm guessing you created the new user with 'useradd'? iirc that sets the users login shell as '/bin/sh' so you don't get any of the .bashrc stuff (like the PS1 prompt, or tab completions)

You can check by looking at the /etc/passwd file, or running getent passwd

```
getent passwd *newuser*
```

You can change the default shell using chsh

```
chsh -s /bin/bash
```

(if logged in as *newuser*) or

```
sudo chsh -s /bin/bash *newuser*
```

Note that useradd also doesn't copy the base files from /etc/skel so the new user likely won't have a ~/.bashrc file at this point (but bash will still read the system rc file /etc/bash.bashrc).

If you want new users with all the bells and whistles, use the 'adduser' command - which is a higher-level script

---

