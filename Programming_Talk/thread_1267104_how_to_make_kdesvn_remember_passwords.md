---
title: "how to make kdesvn remember passwords?"
date: 2009-09-15
forum: Programming Talk
---

### Post by infestor on 2009-09-15
each time i do any operations with kdesvn such as commit, update, view log etc. it asks my svn/ssh password **3** times! is there a way to make kdesvn store my password or ask max. 1 time?
i tried kdewallet but couldnt get it working :(
can some of guys please give a hand?

---

### Post by infestor on 2009-09-15
nothing? :(

---

### Post by Colonel Kilkenny on 2009-09-15
I'm not familiar with kdesvn so these instructions may not work for you, but in all my projects (SVN/GIT/etc. over ssh) I've used something like this: [http://linux-programming.suite101.com/article.cfm/using_ssh_without_a_password](http://linux-programming.suite101.com/article.cfm/using_ssh_without_a_password)

Basically you need to create key pair and transfer (and add it to authorized keys list) the public key to the other end of your connection (in your case it's probably the server with svn).

Google is your friend. 
This might also help: [http://yade.wikia.com/wiki/Quick_subversion_tutorial](http://yade.wikia.com/wiki/Quick_subversion_tutorial)
See the section "Read-write access without password"

---

### Post by infestor on 2009-09-18
> **Colonel Kilkenny said:**
> I'm not familiar with kdesvn so these instructions may not work for you, but in all my projects (SVN/GIT/etc. over ssh) I've used something like this: [http://linux-programming.suite101.com/article.cfm/using_ssh_without_a_password](http://linux-programming.suite101.com/article.cfm/using_ssh_without_a_password)

Basically you need to create key pair and transfer (and add it to authorized keys list) the public key to the other end of your connection (in your case it's probably the server with svn).

Google is your friend. 
This might also help: [http://yade.wikia.com/wiki/Quick_subversion_tutorial](http://yade.wikia.com/wiki/Quick_subversion_tutorial)
See the section "Read-write access without password"

```
ssh *username*@shell.berlios.de
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
rm id_rsa.pub
chmod 644 ~/.ssh/authorized_keys

```

i came up to here but there is no dir as [B] ~/.ssh/authorized_keys.
[/B]what could it be in my project's dir?

---

### Post by KIAaze on 2009-09-18
> **infestor said:**
> ```
ssh *username*@shell.berlios.de
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
rm id_rsa.pub
chmod 644 ~/.ssh/authorized_keys

```

i came up to here but there is no dir as [B] ~/.ssh/authorized_keys.
[/B]what could it be in my project's dir?

It's not a directory. It's a file.
The command
```
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
``` will append the contents of file "~/id_rsa.pub" to file "~/.ssh/authorized_keys".
If it does not exist, it will be created.

Of course the directory "~/.ssh" has to exist before. If it doesn't just create it.

---

