---
title: "Changing Sudo Password?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by skymera on 2008-06-27
Hi,

Is it possible to change the sudo password so it's not my login password?

[spoil]I was thinking of creating a root password and removing myself from the sudoers file. This i would see as a last resort.[/spoil]

---

### Post by lisati on 2008-06-27
It might be easier to set up a "day to day" account without admin privileges. That way, you can use your machine with greater protection against muck-ups, and then use your admin account only for system maintenance.

---

### Post by skymera on 2008-06-27
Thats one idea.

But i install + remove programs a lot etc so it's necessary for me to have sudo.

---

### Post by neurostu on 2008-06-27
No you cannot set your SUDO password to be different then the login password. Each account has a password associated with it.

---

### Post by forger on 2008-06-27
> **skymera said:**
> Thats one idea.

But i install + remove programs a lot etc so it's necessary for me to have sudo.

You could limit your sudo: man sudoers
```
sudo cat /etc/sudoers
```

---

### Post by ibutho on 2008-06-27
> [spoil]I was thinking of creating a root password and removing myself from the sudoers file. This i would see as a last resort.[/spoil]
Thats what I do on my systems (yeah some moan that its not recommended but their justification is pretty lame in my opion because thats what other distros do and it works fine). I setup a password for root, remove myself from the admin group and also disable the privileges for the admin group using visudo.

---

### Post by skymera on 2008-06-27
> **ibutho said:**
> Thats what I do on my systems (yeah some moan that its not recommended but their justification is pretty lame in my opion because thats what other distros do and it works fine). I setup a password for root, remove myself from the admin group and also disable the privileges for the admin group using visudo.

Could you give details how i would go about doing this?

Thanks =D

---

### Post by ibutho on 2008-06-27
First you give root a password whilst logged in as the admin user (sudo passwd root). You then need to switch to root using the command "su -" and run visudo. Change
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```
to
```
# Members of the admin group may gain root privileges
#%admin ALL=(ALL) ALL

```
You can then logout as root (exit or CTRL-D) and also log out of your normal user session and then log back in. You will then need to use "su" and "su -" to switch to root. To run individual commands as root, you can do 
```
su -c "some commands"
```
To remove the user from the admin group, you can do
```
gpasswd -d user admin
```
user is the username of whoever you want to remove from the admin group. You can even go as far as removing the admin group using groupdel if you wish. 

The downside to this is that some apps are hard coded for the sudo stuff, but you can start then using su or gksu.

---

