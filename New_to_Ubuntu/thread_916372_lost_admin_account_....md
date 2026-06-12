---
title: "lost admin account ..."
date: 2008-09-10
forum: New to Ubuntu
---

### Post by npnutn7 on 2008-09-10
I was trying to manage the accounts and now all i have is the root and admin account without sudoers privileges , and i can not change that back,, 

what should i do now?

---

### Post by ajmorris on 2008-09-10
> **npnutn7 said:**
> I was trying to manage the accounts and now all i have is the root and admin account without sudoers privileges , and i can not change that back,, 

what should i do now?

hi there,
run ```
su
``` in a terminal, then type in visudo, you can then add your user to be able to use sudo again.

AJ

---

### Post by npnutn7 on 2008-09-10
thanks for a quick reply,
i tried it but here is what i get

> Password: 
su: Authentication failure

---

### Post by ajmorris on 2008-09-10
> **npnutn7 said:**
> thanks for a quick reply,
i tried it but here is what i get

This means your root account is disabled, and can only be access by sudo. To re-enable sudo for you user, you will have to boot into a live cd, chroot as root into your ubuntu install, and run visudo from there.

AJ

---

### Post by npnutn7 on 2008-09-10
ok, i`ll try ,
I think i am gonna install ubuntu again, it`s still a fresh copy
thanks

---

### Post by npnutn7 on 2008-09-11
ok, did Google it and here`s what i found and yes i was able to fix it.

1) on login screen choose recovery mode
2) use drop as root , i think the 3rd one
3) use this command to reset root password
> passwd root
4) reboot and logged back in with my usual account
5) open terminal and 
> su
users-admin
6) Vola, edit all your account in root mode
7) you have to restart and disable the root password 

and that`s what i want to know how?

---

### Post by npnutn7 on 2008-09-11
updates,
used this command
> 
sudo passwd -l root

but now i get this message when "sudo su"
> Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)

and then it opens root
What to do?

---

