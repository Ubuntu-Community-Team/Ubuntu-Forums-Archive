---
title: "[SOLVED] How to create a user without sudo powers?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by dynamethod on 2008-06-15
hey how do you create a user account(via bash shell) that doesnt have access to the 'sudo' command?

---

### Post by sdennie on 2008-06-15
By default users aren't part of the admin group I don't think.  So:

```

sudo adduser name_of_new_user

```

---

### Post by dynamethod on 2008-06-15
actually i did sudo adduser test


and with the test account i can still use the sudo command, so how do i setup a user so that they cannot use 'sudo' at all?

---

### Post by ConMan318 on 2008-06-15
System > Admin > Users & Groups.  Then click 'unlock' and enter your password.  Then 'add user', and under the 'user privilages' tab, leave the 'administer system' box unchecked, as it is by default.

---

### Post by dynamethod on 2008-06-15
thats fine, but im trying to find the bash equivelant

---

### Post by sdennie on 2008-06-15
> **dynamethod said:**
> actually i did sudo adduser test


and with the test account i can still use the sudo command, so how do i setup a user so that they cannot use 'sudo' at all?

Odd.  I did the same thing in a test VM and the only group the user belonged to was "test".  In that case the user can't use sudo because they aren't part of the admin group.  When you are logged in as the new user, what is the output of:

```

groups

```

If it includes the admin group, you can do the following:

```

sudo deluser name_of_user admin

```

---

### Post by iaculallad on 2008-06-15
You can edit your sudoer file to restrict users from using the sudo command or you can still enable sudo but limit the commands the user can execute with sudo.

i.e:

Adding the text below to your sudoer file could only give UserMe access to command kill, mkswap.

> UserMe     ALL=    /bin/kill,/sbin/mkswap

---

### Post by dynamethod on 2008-06-15
well odly enough i could not do the command:

deluser test admin from a su shell


i had to actually login to the test account and run:

sudo deluser test admin


after which i ran 'groups' in bash


which outputted 

'test'

so i then tried 'sudo kate', kate did not run

so i assume it worked

---

### Post by dynamethod on 2008-06-15
> **iaculallad said:**
> You can edit your sudoer file to restrict users from using the sudo command or you can still enable sudo but limit the commands the user can execute with sudo.

i.e:

Adding the text below to your sudoer file could only give UserMe access to command kill, mkswap.

that would be fine if i wanted to be that concise, however if i just wanted to create a user with absolutly no access to sudo, then i think the 'sudo deluser test admin' would be more appropriate

---

### Post by Dougie187 on 2008-06-15
you can always just add the user and remove them from the admin group. The groups are listed in /etc/group

Just look for the admin line and remove the user names that you dont want.

---

### Post by ConMan318 on 2008-06-15
```
sudo adduser --group GROUPNAME
sudo adduser --ingroup GROUPNAME USERNAME

```

That will put the new user in a different group, disabling root access.

---

### Post by dynamethod on 2008-06-15
Next question, say if i wanted to disable access to certain software, ill use kate in this example, i had tried:

sudo -i
chmod 700 /usr/bin/kate
exit


however after exiting the superuser shell, i could still acess kate with the test account

how do i disable software access to users via the bash shell?

---

### Post by dynamethod on 2008-06-15
anyone?

---

### Post by sdennie on 2008-06-15
> **dynamethod said:**
> Next question, say if i wanted to disable access to certain software, ill use kate in this example, i had tried:

sudo -i
chmod 700 /usr/bin/kate
exit


however after exiting the superuser shell, i could still acess kate with the test account

how do i disable software access to users via the bash shell?

That seems impossible.  Doing a chmod 0700 on a binary would mean it can only be run by explicitly running it with sudo.

---

### Post by dynamethod on 2008-06-15
But say that i want kate(or anyother software) to only be accessable( i know its a bad example for software but just for simplicity's sake) by root, how does one go about this via bash?

---

### Post by iaculallad on 2008-06-15
> **dynamethod said:**
> But say that i want kate(or anyother software) to only be accessable( i know its a bad example for software but just for simplicity's sake) by root, how does one go about this via bash?

Any application/s installed can be accessed by the root by default without any restrictions.

---

### Post by dynamethod on 2008-06-15
> **iaculallad said:**
> Any application/s installed can be accessed by the root by default without any restrictions.

Sorry i missworded that, i mean to restrict the software to only root and no one else(using kate in this example)

---

### Post by darksizzle on 2008-06-15
```
sudo chown 'root:root' /usr/bin/kate
```
```
sudo chmod 700 /usr/bin/kate
```

---

