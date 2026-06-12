---
title: "Can't log onto root."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by PleaseEnjoyThis on 2008-10-25
lucifer@lucifer:~$ su root
Password: 
su: Authentication failure


The password is correct and I have been able to log on before. 

Me being the paranoid bitch I am immediately think someone has access to my computer.  What do you think?  And is there any way I can tell?  What is wrong?! HELP!

---

### Post by snova on 2008-10-25
The root account is disabled in Ubuntu. Use sudo instead, which can be used to get a shell if you really need it.

Edit: Oops, you've logged in as root before? Assuming you reactivated the root account, no idea.

---

### Post by eolson on 2008-10-25
like this

sudo su

---

### Post by PleaseEnjoyThis on 2008-10-25
thank you.  I feel really stupid.  I havn't gotten on root in awhile. humph.  well on the issue of security.  can anyone direct me to a good thread?  Or just general advice if ya feel like it?

---

### Post by eolson on 2008-10-25
You can try this

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by st33med on 2008-10-25
Have you tried:
```
sudo -s
```

That gives you a root bash shell. However, you are not root. The root user is locked up in a chest somewhere because his powers are too great and terrible for one man in Ubuntu...

Or, it is better not to screw up files and programs with root ;).

---

### Post by Dr Small on 2008-10-25
> **st33med said:**
> The root user is locked up in a chest somewhere because his powers are too great and terrible for one man in Ubuntu...


Not for me :p

---

### Post by st33med on 2008-10-25
> **Dr Small said:**
> Not for me :p

Yes, and you are OBVIOUSLY corrupt by its nature. :P

---

### Post by lifestream on 2008-10-25
You should be able to change / reset the root password with:

sudo password

then try logging in as root again :)

---

### Post by dizzy1kenobi on 2008-10-25
This seems like a good place to ask this question that has been hanging around lately.  What exactly is "root" and how does it relate to "sudo" commands?  I have a vague idea but I think some explanation is necessary.

---

### Post by drowner on 2008-10-25
> **dizzy1kenobi said:**
> This seems like a good place to ask this question that has been hanging around lately.  What exactly is "root" and how does it relate to "sudo" commands?  I have a vague idea but I think some explanation is necessary.

Root is the super-user who can access / delete / modify all parts of a linux installation. In other linux distributions, if you wanted to modify a system component etc, you had to log in as 'root' rather than your usual login.

Ubuntu uses the 'sudo' system, which temporarily gives specified super-users root priviliges, when they use the sudo command. It confirms the action with a password prompt.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bapoumba on 2008-10-26
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

Please read the link, everything is explained. CLosing the thread, sorry.

---

