---
title: "Permission to save changed samba config file"
date: 2016-09-14
forum: New to Ubuntu
---

### Post by gbest5089 on 2016-09-14
Using Ubuntu 16.04 and trying to share files with a Windows network and trying to modify samba.config as recommended in instructions.  Can modify on screen but can not save; just get "you do not have permission" message.   So what do I need to change to give myself permission to change this file and (next question how do I do that?)     All help gratefully appreciated, thanks.

If I can get this working I can finally ditch that old XP computer and can have a break from struggling with that terrible Win 10 "up"grade.

Thanks,
gbest5089

---

### Post by howefield on 2016-09-14
> **gbest5089 said:**
> Can modify on screen but can not save; just get "you do not have permission" message.

Try preceding the command with sudo.

This will give you elevated rights allowing to save the file, eg..

```
sudo nano /etc/samba/smb.config
```

Not saying that's the command you need, just precede whatever command you used to edit the file with sudo, you'll be prompted for your password which you won't see being entered.

---

### Post by clazzics88 on 2016-09-14
I have found that using 
sudo gedit /etc/samba/smb.conf 
works quite well, I find the note pad style rather then the terminal style to be a little more user friendly as well

---

### Post by howefield on 2016-09-15
> **clazzics88 said:**
> ...sudo gedit /etc/samba/smb.conf  works quite well, I find the note pad style rather then the terminal style to be a little more user friendly as well

Sure, nothing wrong with that, although I'd suggest..

```
sudo -H gedit /etc/samba/smb.conf
```

---

### Post by clazzics88 on 2016-09-15
I am quite new to Ubuntu, I was just wondering for my own reference why you would use the -H option in this instance. My understanding is that it relates to setting the default security policy to the home or default environment?

---

### Post by howefield on 2016-10-03
> **clazzics88 said:**
> I am quite new to Ubuntu, I was just wondering for my own reference why you would use the -H option in this instance. My understanding is that it relates to setting the default security policy to the home or default environment?

Before being deprecated gksudo was the generally accepted way to run graphical applications with elevated rights and sudo for non graphical. Now gksudo is no longer installed by default I use sudo -H to run graphical applications as sudo on the exceptionally rare occasions that it is needed.

From man sudo
```
-H, --set-home
                 Request that the security policy set the HOME environment variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may be the default behavior.
```

---

