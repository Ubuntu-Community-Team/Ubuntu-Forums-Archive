---
title: "Changing file permissions .bash_aliases"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by r111 on 2011-12-23
I created a .bash_aliases file last night, and it seemed to be working fine and the aliases i entered in worked fine in terminal.  Today I wanted to enter in some more aliases and found that the file was read only in emacs/geddit.  I looked through the manual for chmod and tried to change the permissions on the file with this command:  

@Argon:~$ chmod a+w .bash_aliases
chmod: changing permissions of `.bash_aliases': Operation not permitted

Here are the permissions shown from ls -al:

-rw-r--r--  1 root root    62 2011-12-23 00:29 .bash_aliases

I'm guessing it's got something to do with those permissions being linked to the root and not my username, but I'm still quite new to the terminal so I'm not sure.

---

### Post by nothingspecial on 2011-12-23
```
sudo chown $USER:$USER ~/.bash_aliases
```

---

### Post by r111 on 2011-12-23
sudo chown $root:$rob ~/.bash_aliases

I tried the command like this and it didn't have any errors but it also didn't change the permissions I don't think.

---

### Post by nothingspecial on 2011-12-23
$USER expands to your username

copy and paste ;)

---

### Post by r111 on 2011-12-23
haha whoops that worked perfectly.  

Thanks.

---

