---
title: "How to Become Root?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by doctorj on 2008-10-07
I know this is a drop dead simple question but what do I use to become root in a terminal? I just forgot and need to know to restart NetworkManager.

---

### Post by christianvaldes on 2008-10-07
> **doctorj said:**
> I know this is a drop dead simple question but what do I use to become root in a terminal? I just forgot and need to know to restart NetworkManager.

su

---

### Post by jerome1232 on 2008-10-07
You can prepend the command you need to run as root with 'sudo'

```
sudo command-to-be-run-as-root
```

or if you want to launch a graphical app as root (such nautilus)
```
gksu nautilus
```

---

### Post by JoshuaRL on 2008-10-07
The better thing to do is either sudo for straight terminal commands, or gksu for commands that launch a graphical interface.

Temporary priviledges are better than switch user.

EDIT:  Beat by a hair.  JEROOOOOOOOME!

---

### Post by DGortze380 on 2008-10-07
> **doctorj said:**
> I know this is a drop dead simple question but what do I use to become root in a terminal? I just forgot and need to know to restart NetworkManager.

Ubuntu suggests that you don't, use sudo instead.

That said, you'd have to enable to root account and switch to root, I can't post exactly how in the forums.

---

### Post by doctorj on 2008-10-07
Thanks. Tried that but when I type my password in it give me "authentication error". What am I doing wrong? The password is the one I use all the time so it cannot be wrong.

---

### Post by doctorj on 2008-10-07
Thanks. I got NetworkManager going by using Sudo. Thanks.

---

### Post by Joeb454 on 2008-10-07
As mentioned above - use "sudo" to get root privileges for applications, or "gksudo" for graphical applications

---

### Post by jerome1232 on 2008-10-07
> **JoshuaRL said:**
> The better thing to do is either sudo for straight terminal commands, or gksu for commands that launch a graphical interface.

Temporary priviledges are better than switch user.

EDIT:  Beat by a hair.  JEROOOOOOOOME!

Haha! typing skills ftw!

> **doctorj said:**
> Thanks. Tried that but when I type my password in it give me "authentication error". What am I doing wrong? The password is the one I use all the time so it cannot be wrong.

It's asking for the same password you use to login with. (check caps lock and num lock make sure they aren't screwing you up)

---

### Post by Raven2k360 on 2008-10-08
> **jerome1232 said:**
> Haha! typing skills ftw!



It's asking for the same password you use to login with. (check caps lock and num lock make sure they aren't screwing you up)

I'm having the same issue trying to install an app.  The instructions say first-off to input the 'su' command in Terminal, but when I do, it asks for a password (normal, I know).  Well, I input my password (the one I use to log in AND have to input for any admin programs/changes) exactly to the letter, case and all, and it tells me 'Authentication Error'....basically telling me to GFY...LOL!  What's up with this???

---

### Post by jerome1232 on 2008-10-08
> **Raven2k360 said:**
> I'm having the same issue trying to install an app.  The instructions say first-off to input the 'su' command in Terminal, but when I do, it asks for a password (normal, I know).  Well, I input my password (the one I use to log in AND have to input for any admin programs/changes) exactly to the letter, case and all, and it tells me 'Authentication Error'....basically telling me to GFY...LOL!  What's up with this???

Ubuntu disables root by default that's why su won't work by itself, instead run the commands with sudo in front of them, or subsitute 'su' with 'sudo -i' to get the same affect, remember to use exit when your done with root privilages.

---

### Post by Raven2k360 on 2008-10-08
You da MAN!  Thank You kind Sir! :biggrin:

---

