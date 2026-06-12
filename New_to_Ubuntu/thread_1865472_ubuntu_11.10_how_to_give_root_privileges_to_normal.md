---
title: "ubuntu 11.10 how to give root privileges to normal user ?"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by qpens on 2011-10-20
ubuntu 11.10 how to give root privileges to normal user? or give more power to normal account

---

### Post by Paqman on 2011-10-20
Open up the Users and Groups* tool and change their account type from "standard" to "administrator"

*I think the name of this may have changed a little, but can't check right now.

---

### Post by Lars Noodén on 2011-10-20
Note that granting such privileges does not have to be an all or nothing affair.  You can edit /etc/sudoers so that privileges are granted for specific applications only, if that is what you are after.

---

### Post by ArgusVision on 2011-10-20
Provided you have administrative (root) privleges, you use those in ubuntu with the sudo command while you're in the terminal. If you are trying to give access to another user thay need to be added to the sudoers list. 
The easiest way, if you're new to Ubuntu,  is  from the 'Users an groups' manager. I'm pretty sure you can get there from the  'Ubuntu button' at the top left. (I still haven't dabbled with the unity interface.)
Once you open the manager, and enter your password, select (or create) the user and make sure the 'administer system' box is checked.

---

### Post by ArgusVision on 2011-10-20
Sorry about the double post. I'm posting from my 'not so smart' phone.

---

### Post by 3rdalbum on 2011-10-20
Giving root privileges to a user is bad security practice. I'm concerned that you might be asking about this to prevent the password prompts from appearing, or so you don't have to think about whether to use 'sudo' or not.

If you preface a command with the word 'sudo', it runs as root.

You can run a program (such as a file manager) with 'gksudo' to give it root privileges temporarily.

But don't use a powerful root-like account as your normal account. That's why Ubuntu doesn't enable root by default - it encourages people to use root when they don't need it.

---

### Post by qpens on 2011-10-20
thanks guys

---

### Post by ArgusVision on 2011-10-20
Hope you got the help you needed.

---

### Post by Rokkk on 2012-07-25
Goddamn it guys!:D

Why would be that dangerous if you running wonderful linux in a virtual machine for example?? Now I'm pretty messed up cause I'm a beginner Linux user and I could manage to give those root privileges perhaps three times already for different installations in the past..but I don't remember how..:D I got a multiboot laptop with win7 ubuntu and backtrack..and to be honest recently I was experimenting with backtrack(given root privileges) without the need of the mentioned commands..but today I installed blackbuntu as a guest on my win7 host because I wanted to try it out. Now I just can't find the commands and the how to in any forums but stuff like "OMG how dangerous is this"...:D
I promise that I will save those commands to a document from now on..:)

---

### Post by HiImTye on 2012-07-25
[https://wiki.ubuntu.com/RootSudo/](https://wiki.ubuntu.com/RootSudo/)

---

### Post by cariboo on 2012-07-25
What is it that you need to be root for? If you need to run your user with elevated privileges for any amount of time, use:

```
sudo -i
```

in a terminal.

I'd suggest you have a look at the [RootSudo]("https://help.ubuntu.com/community/RootSudo") wiki page, I'd further suggest you read the whole page, instead of just skipping to the juicy bits. :)

---

