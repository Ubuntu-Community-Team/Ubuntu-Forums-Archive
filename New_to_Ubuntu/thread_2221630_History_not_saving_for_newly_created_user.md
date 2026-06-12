---
title: "History not saving for newly created user"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by semicolon2 on 2014-05-03
Hi,
I created a new user via command "useradd -d /home/username -m username" . 
but when I am logged in with this new user. And execute some command , its history is not being saved. also there is no .bash_history and .bashrc .profile folder in home directory of this new user. unlike root.
every command I execute while logged in as root is saved in history and i can see by typing history.

How can i fix this issue for new user.

---

### Post by steeldriver on 2014-05-03
I don't think useradd sets the user's shell to bash (the account is probably set up to use the dash shell). You can change the shell to bash with

```

chsh -s /bin/bash

```
if you're logged in as that user, or as administrator
```

sudo chsh -s /bin/bash *username*

```

and then copy the default .bashrc and .profile files from the /etc/skel directory. Next time, you should probably use adduser instead as noted in the useradd man page:

```

DESCRIPTION
       useradd is a low level utility for adding users. On Debian, administrators **should usually use adduser(8) instead**.

```

---

### Post by semicolon2 on 2014-05-03
Thank you. I run sudo chsh -s /bin/bash username . Still .bashrc and .bash_history directory no listed when i execute ls -a. Though when i type history. it shows my previous commands.

---

### Post by steeldriver on 2014-05-03
as mentioned in my previous post, you can copy the default .bashrc and related files from/etc/skel

```

cp /etc/skel/{.bashrc,.bash_logout,.profile} ~/

```

---

