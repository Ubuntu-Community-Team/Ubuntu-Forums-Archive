---
title: "bash &amp; ssh"
date: 2010-06-22
forum: Programming Talk
---

### Post by Drenriza on 2010-06-22
Is it possible to write a bash script, where you ssh as root to a server. And then from the script, type in the pre-defined root password.

Hope it makes sence.
Thanks on advance.

---

### Post by geirha on 2010-06-22
Yes, but don't. Set up public key or hostbased authentication instead. [http://www.ssh.com/support/documentation/online/ssh/adminguide/32/User_Authentication.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/User_Authentication.html)

---

### Post by Drenriza on 2010-06-22
from what ssh version is this possible?

since i cant find the following
```
/etc/ssh2/sshd2_config 
/etc/ssh2/ssh2_config
```

files.

i can only in ```
/etc/ssh/ssh_config
``` find a section
```
#   PasswordAuthentication yes
```
is this = to ```
AllowedAuthentications   password
``` ?

also in ```
/etc/ssh/sshd_config
```
i can find ```
#PasswordAuthentication yes
``` is this = ```
AllowedAuthentications   password
``` ?

---

### Post by Drenriza on 2010-06-23
bump

---

### Post by Drenriza on 2010-06-25
bump

---

### Post by Zugzwang on 2010-06-25
A line starting with "#" in configuration files is usually ignored by the respective program (as it marks a comment line). Public-key based logins should be activated by default, so there is normally no need to change the configuration files.

BTW, the reason why you didn't got any replies earlier is that probably nobody else ever messed with the configuration files so far because that feature usually just works straight out-of-the-box.

---

### Post by mainerror on 2010-06-25
> **Zugzwang said:**
> BTW, the reason why you didn't got any replies earlier is that probably nobody else ever messed with the configuration files so far because that feature usually just works straight out-of-the-box.

This and because his post is not readable. I was not able to figure out what he was trying to ask by scattering up his post.

---

### Post by Drenriza on 2010-06-28
> **mainerror said:**
> This and because his post is not readable. I was not able to figure out what he was trying to ask by scattering up his post.

Well, thats unfurtiant.

But the question is,

> Is it possible to write a bash script, where you ssh as root to a server. And then from the script, type in the pre-defined root password.

Hope it makes sence.
Thanks on advance.

what iam asked in the guide to do is then

> To enable password authentication, make sure that the AllowedAuthentications field of the /etc/ssh2/sshd2_config and /etc/ssh2/ssh2_config configuration files contain the parameter password:

        AllowedAuthentications   password
Other authentication methods can be listed in the configuration files as well.

But i can only find
> /etc/ssh/ssh_config 
/etc/ssh/sshd_config

I do not know if i have an older SSH version then the one in the "guide". It would make sense. 

```
/etc/ssh/ssh_config
```
In this file i find a section, as follows.
#   PasswordAuthentication yes

I then ask. Is this section _#   PasswordAuthentication yes_
equal to _AllowedAuthentications   password_ which is in the guide.
[http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Password_Authentication.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Password_Authentication.html)

What i mean with this is, Do they do the same?

I don't find what i previously typed, un-readable. Maybe hard because of all the code /code tags.
But hey was short on time and was busy. So that was what i ended up with.

Thanks on advance

---

### Post by Zugzwang on 2010-06-28
@Drenriza: First of all, as already said, forget about changing the configuration file unless it does not work. I must say that I've never seen a Linux distribution in which the whole thing doesn't work straight of-the-box. Then, try to "set up public key or hostbased authentication instead.".

In about 95% of the cases, Linux documentation you find on the web is outdated. This is probably because older versions of the documentation have more links, so they rank higher on google (just a guess). For this reason, you should always look on the official pages first. Note that the documentation at "http://www.ssh.com/support/documentation/online/ssh/adminguide/32/User_Authentication.html" has copyright 2003, so it is highly likely to be outdated. You can try some more recent tutorial: "http://www.debuntu.org/ssh-key-based-authentication". Ok, that one is from 2007, but it might still be fine.

For your reference, I'll also add some information why geirha considered your post to be unreadable.

Geirha writes:
> 
Yes, but don't. Set up public key or hostbased authentication instead. [http://www.ssh.com/support/documenta...ntication.html](http://www.ssh.com/support/documenta...ntication.html)


Then you write:
> 
from what ssh version is this possible?

since i cant find the following
```

/etc/ssh2/sshd2_config 
/etc/ssh2/ssh2_config

```
files.


The point is that people will not see the connection between these missing files and the public-key or hostbased authentification as your question only makes sense after actually following the link. But almost nobody would do so since everyone would assume that the site contains data about how to setup this thing, which many people know already how to do (so they won't follow the link). And for doing so, there is no messing with configuration files necessary, so nobody can draw the connection between these filenames and the issue you are having. So it might have been wise to start your reply with something like "According to the site you linked to, the first step is to configure ssh accordingly.", so that everyone knows the context. Finally, this "PasswordAuthentication" has nothing to do with public-key or hostbased authentification, which is another source of confusion.

---

