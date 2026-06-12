---
title: "Cloning user accounts"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by HonorableFool on 2013-10-23
Hello for learning purposes Id really like to clone all the applications and preferences from my main account to a "test" account so I tried to follow some of the commands located in another forum instructing to: 

sudo mv /home/new_user /home/new_user.bak
sudo cp -R /home/old_user /home/new_user
sudo chown -R new_user:new_user /home/new_user
Log into the new user account. If all is working, delete the backup


sudo rm -rf /home/new_user.bak

however when I try line 3..
[http://imgur.com/Q3joia3](http://imgur.com/Q3joia3)

Seperate but related issue: I retried steps given on this thread [http://ubuntuforums.org/showthread.php?t=1280723](http://ubuntuforums.org/showthread.php?t=1280723), and cannot even access the home folder...
[http://imgur.com/jfo030P](http://imgur.com/jfo030P)

 Side note: I have given both accounts all the same/necessary group privileges, including adm and sudo.

Thanks in advance, anything is appreciated!

"Help me Obi Wan Kanobe, Your my only Hope"

---

### Post by zazy on 2013-10-23
I suppose the error is related to the fact that syntax of command at line 3 is wrong. It should be:

```
sudo chown -R new_user:**new_user_group** /home/new_user
```

if new_user is in the same group of old_user you can omit the :new_user_group part.

Furthermore please note that (maybe) you can't access the home folder with sudo because you forgot the blank space between **cd** and **/home/taster1 **;)

---

### Post by Habitual on 2013-10-23
```
usermod -l <New Username> -d /home/<New Username> -m <Old Username>
```
It's rather generic so I'm not sure it'll work on Ubuntu.

---

### Post by HonorableFool on 2013-10-23
Thanks, does that mean I need to create that group prior to the command?

---

### Post by zazy on 2013-10-25
> **Habitual said:**
> ```
usermod -l <New Username> -d /home/<New Username> -m <Old Username>
```
It's rather generic so I'm not sure it'll work on Ubuntu.

It works on Ubuntu but usermod will **move** the content of the **<old username>** account. 

@HonorableFool 
if you want to first test the new account and then delete the old one you have to backup the old user home folder.[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by Habitual on 2013-10-25
> **zazy said:**
> It works on Ubuntu but usermod will **move** the content of the **<old username>** account. 

His very first command:
> **HonorableFool said:**
> ```
sudo mv /home/new_user /home/new_user.bak
```

---

