---
title: "Login username - what is it?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by r_rindfuss on 2008-06-28
I just installed Ubuntu and when i try to run it, it asks me for a username and password.  during installation, it never prompted me to enter a username or password, so i have no idea what the username and password could be.  Could anyone help me?

---

### Post by NikS on 2008-06-28
Hey r_rindfuss,
y dont you creat a thread of its own?? that way U'l get more relevant replies!! (Thats wat a moderator told me to do when i was VERY new!!) {It should have asked you for a name, if u havent changed login id is same as the name but no CAPITALS, on the same page below it must also have asked for a password!!! Try to remember}

Well, This is a REALLY useful thred, how come i dint check it before!!!!

Thanks ugm6hr

---

### Post by ugm6hr on 2008-06-28
> **r_rindfuss said:**
> I just installed Ubuntu and when i try to run it, it asks me for a username and password.  during installation, it never prompted me to enter a username or password, so i have no idea what the username and password could be.  Could anyone help me?

It will have asked you to enter a username and password.

If it didn't - then there was a flaw in the installation.  Check the CD for errors / md5 for errors (see the original sticky thread for links on how to do that).

---

### Post by milton1 on 2008-06-28
Is it possible you ran the oem install option? if so, the username should, i believe, be 'oem'. However, it still should have prompted you for a password. I suppose you could try oem as the password, too and see if that works.

---

### Post by WRDN on 2008-06-28
If you can't login and were not asked for a username and password during the initial installation, try entering Recovery Mode (it should be an option in the GRUB bootloader), drop down to root shell (3rd option when recovery mode starts) and add a new user, by using the command:

```
adduser [username]
```

You can add a password to the account by using the command:

```
passwd [username]
```

Hopefully, this will work and you will be able to login normally.

---

### Post by tubuun on 2008-06-29
> **WRDN said:**
> If you can't login and were not asked for a username and password during the initial installation, try entering Recovery Mode (it should be an option in the GRUB bootloader), drop down to root shell (3rd option when recovery mode starts) and add a new user, by using the command:

```
adduser [username]
```

You can add a password to the account by using the command:

```
passwd [username]
```

Hopefully, this will work and you will be able to login normally.
[COLOR="SeaGreen"]Thanks, WRDN. Fixed me right up![/COLOR]

---

