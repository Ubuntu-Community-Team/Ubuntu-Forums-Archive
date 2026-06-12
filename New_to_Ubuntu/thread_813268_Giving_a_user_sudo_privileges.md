---
title: "Giving a user sudo privileges"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by altonbr on 2008-05-30
I'm writing this using links2, so bare with me.

I've reinstalled Ubuntu 8.04 over 7.10 for a client of mine. She has a separate partition for /home so I could keep all of here data and preferences. The problem is, I entered her username in wrong, so I had a incorrect user as sudo from the start.

I added her real username using 'Users and Groups' and then 'adduser' when that failed. Both tries have ran me no luck in making her a sudo user.

How can I get sudo privialges back? There doesn't seem to be any GUI for it and I'm getting beyond frustrated trying to edit /etc/sudoers with ```
visudo -f /etc/sudoers
```

What is the proper GUI way to enable a user sudo privilages and what is the proper way to do it via CLI?

Thank you for your time.

---

### Post by ibuclaw on 2008-05-30
```
sudo usermod -a -G admin **username**
```

That would add the person to the admin group, and by default in Ubuntu. only admins have sudo privileges.

Regards
Iain

---

### Post by quelx on 2008-05-30
**System** > **Administration** > **Users and Groups**

**Unlock** > **Manage Groups** > higlight **admin** > **Properties**

check boxes next to users you want to be able to run **sudo**

---

### Post by bwhite82 on 2008-05-30
I'm not aware of a GUI for this (doesn't mean one couldn't exist), and visudo is the correct CLI method. I can remember there being a way to make visudo use nano instead of vim, can't remember exactly how.

EDIT:

> export EDITOR=nano && sudo -E visudo

---

### Post by Technoviking on 2008-05-30
The GUI is located at [B]System --> Administration --> User & Groups
[/B]
Add the user to the admin group to give them sudo rights.

---

### Post by ibuclaw on 2008-05-30
> **Soldierboy said:**
> I'm not aware of a GUI for this (doesn't mean one couldn't exist), and visudo is the correct CLI method. I can remember there being a way to make visudo use nano instead of vim, can't remember exactly how.

```
echo "export EDITOR=nano" >> ~/.bashrc
```
Reload the shell and type in:
```
sudo -E visudo
```
Works like a charm...

Regards
Iain

---

### Post by altonbr on 2008-06-02
> **tinivole said:**
> ```
sudo usermod -a -G admin **username**
```

That would add the person to the admin group, and by default in Ubuntu. only admins have sudo privileges.

Regards
Iain

This worked perfectly, thank you!

---

