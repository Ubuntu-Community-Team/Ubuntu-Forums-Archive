---
title: "directly logging me as root without asking password with sudo su command"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by imgkg on 2008-09-04
i guess i am messed up with root account as i type "sudo su" in terminal it directly logs me in as root without asking password  please help how to fix this as before 
```
user@user-desktop:~$ sudo su
root@user-desktop:/home/user# 


```

---

### Post by lswest on 2008-09-04
did you run a sudo command shortly before running that?  As Ubuntu caches the password for a short while after running it, so it may just be that it's using the cached password.  If that's not the case can you please post the output of ```
cat /etc/sudoers
```

---

### Post by prshah on 2008-09-04
> **imgkg said:**
>  it directly logs me in as root without asking password

> **lswest said:**
> As Ubuntu caches the password for a short while after running it, so it may just be that it's using the cached password. 

To check lswest's point, use ```
sudo -k
sudo su
``` and see if you are prompted for the password.

---

### Post by imgkg on 2008-09-04
out put of that command 

```

user@user-desktop:~$ sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
user@user-desktop:~$
```

---

### Post by hyper_ch on 2008-09-04
why do you have root activated?

---

### Post by imgkg on 2008-09-04
i was installing nvidia driver anyways that didnt got installed now how to disable that root

---

### Post by iaculallad on 2008-09-04
Can you chown a file while in the root mode:

```
chown root:root /home/your_username/file
```

---

### Post by iaculallad on 2008-09-04
> **imgkg said:**
> i was installing nvidia driver anyways that didnt got installed now how to disable that root

To disable root account, simple issue the command below on your terminal:

```
sudo passwd -l root
```

---

### Post by imgkg on 2008-09-04
i can i guess
```
user@user-desktop:~$ chown root:root /home/user/Pictures/monopoly.jpg
chown: changing ownership of `/home/user/Pictures/monopoly.jpg': Operation not permitted
user@user-desktop:~$ sudo su
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)
root@user-desktop:/home/user#  chown root:root /home/user/Pictures/monopoly.jpg
root@user-desktop:/home/user# 

```

---

### Post by imgkg on 2008-09-04
i guess its still not changed ```
user@user-desktop:~$ sudo passwd -l root
Password changed.
user@user-desktop:~$ sudo su
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)
root@user-desktop:/home/user# 

```

---

### Post by ilrudie on 2008-09-04
Lets looks at the command you ran: 'sudo su'.  It means: as root, switch user (to root).  Since root can su to any user without needing the user's password you su to root just fine even if root has no password (the default state in Ubuntu).

---

### Post by imgkg on 2008-09-04
so u mean to say nothing wrong with it?

---

### Post by quanumphaze on 2008-09-04
Just a suggestion on using a root terminal. Using 'sudo su' is considered bad practice. The correct way is to use 'sudo -i' which has the same result.

Anyway if it is not asking for a password you should try to reboot (which should reset the sudo timer) and try 'sudo su' again.

Also I think that sudo will not ask for a password if your own account has no password.

---

### Post by ilrudie on 2008-09-04
> **imgkg said:**
> so u mean to say nothing wrong with it?

From what you have posted it sounds like its behaving correctly.  It doesn't seem like anything is wrong.

---

