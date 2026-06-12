---
title: "&quot;su&quot; command doesn't work?"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by Olavbs on 2013-07-11
I know this might sound like a really nooby question, but when i used linux mint, i could simply type "su" in the command line, and i would be able to do stuff as superuser (obviously), but in ubuntu 13.04, i just get "Authentication faliure"! why is that?

- Olavbs

---

### Post by overdrank on 2013-07-11
Hi and maybe this can help [_RootSudo_]("https://help.ubuntu.com/community/RootSudo")

---

### Post by fantab on 2013-07-11
It won't work in Ubuntu. Instead you must use '**sudo -i**' but just '**sudo**' is good enough. Read the info on the link which 'overdrank' shared.

---

### Post by Olavbs on 2013-07-11
Thanks a lot both of you! :)

---

### Post by leunam12 on 2013-07-11
To use "su" do:
```
sudo passwd root
```
then type a password and confirm. Now you can do "su".

---

### Post by oldos2er on 2013-07-11
> **leunam12 said:**
> To use "su" do:
```
sudo passwd root
```
then type a password and confirm. Now you can do "su".

But we don't recommend that to new users because enabling the root account subverts Ubuntu's security model, in addition to being unnecessary. Prepending "sudo" to a command or using *sudo -i* is the preferred way.

---

### Post by leunam12 on 2013-07-12
I agree with you, not for the noob. But very useful if you happen to break sudo or mess up the sudoers file (it happens). But I agree, the preferred method is the good old sudo. :D

---

### Post by CaptainMark on 2013-07-12
> **leunam12 said:**
> I agree with you, not for the noob. But very useful if you happen to break sudo or mess up the sudoers file (it happens). But I agree, the preferred method is the good old sudo. :D
If you break the sudoers file you cant exactly use sudo to repair it can you?

I just use "sudo su" to obtain a root terminal

---

### Post by oldos2er on 2013-07-12
> **leunam12 said:**
> I agree with you, not for the noob. But very useful if you happen to break sudo or mess up the sudoers file (it happens). But I agree, the preferred method is the good old sudo. :D

If you edit /etc/sudoers with ```
sudo visudo
``` it'll give you some protection against breaking your sudoers file.

---

### Post by grahammechanical on 2013-07-12
For those who do not know, gksu is not installed in 13.04 by default. We have to install it as it is depreciated. Something called pkexec is going to replace it.

Regards.

---

