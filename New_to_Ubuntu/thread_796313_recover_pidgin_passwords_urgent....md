---
title: "recover pidgin passwords urgent..."
date: 2008-05-16
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-16
i recently changed my email passwords and then... forgot them
is there any way to get them back?

---

### Post by Monicker on 2008-05-16
Pidgin does not encrypt password for the accounts.

Check for the following files:

```
/home/username/.gaim/accounts.xml
/home/username/.pidgin/accounts.xml
```


Basically the accounts.xml file lists all of the accounts along with their passwords.

---

### Post by Het Irv on 2008-05-16
Where did you change them?  You may have to contact the companies that handle the individual protocols.  For example, if you forgot your AIM password, you need to go to the AOL site to get a password reminder or to change the password.

---

### Post by lunaluna on 2008-05-16
> **Monicker said:**
> Pidgin does not encrypt password for the accounts.

Check for the following files:

```
/home/username/.gaim/accounts.xml
/home/username/.pidgin/accounts.xml
```


Basically the accounts.xml file lists all of the accounts along with their passwords.

found it but no passwords there...

---

### Post by lunaluna on 2008-05-16
i've read there is a command that you can see them through terminal,but the command itshelf nowhere..
anyone know?

---

### Post by Het Irv on 2008-05-20
> **Monicker said:**
> Pidgin does not encrypt password for the accounts.

Check for the following files:

```
/home/username/.gaim/accounts.xml
/home/username/.pidgin/accounts.xml
```


Basically the accounts.xml file lists all of the accounts along with their passwords.
on my install, the file was in 
```
~/.purple/accounts.xml
```

---

### Post by Exsecrabilus on 2008-05-20
> **Het Irv said:**
> Where did you change them?  You may have to contact the companies that handle the individual protocols.  For example, if you forgot your AIM password, you need to go to the AOL site to get a password reminder or to change the password.
The quoted post will help the most.

---

### Post by rohan.modi on 2009-12-11
Is there any Way to encrypt the pass which are saved
because any one can see those very easily.
Any way to encrypt them using a master password ????

---

### Post by durand on 2009-12-11
If you changed your email password, you will not be able to recover it from pidgin because the correct password is only stored on their servers, not your computer for obvious reasons.

---

### Post by zeroseven0183 on 2010-01-08
> **rohan.modi said:**
> Is there any Way to encrypt the pass which are saved
because any one can see those very easily.

Yeah. That's one hell of a concern.

---

