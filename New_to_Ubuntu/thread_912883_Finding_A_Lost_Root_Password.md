---
title: "Finding A Lost Root Password?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Breandean on 2008-09-07
Hi again, I lost my root password, either I find it again or reconfigure, not bad option since my configuration is new.

---

### Post by ingeva on 2008-09-07
> **Breandean said:**
> Hi again, I lost my root password, either I find it again or reconfigure, not bad option since my configuration is new.

Normally there's no root password in Ubuntu. Use your own.
Someone may be able to tell you if you can use a live CD to reset the password if necessary.

---

### Post by WRDN on 2008-09-07
If you set a root password (which is unadvised), then use [this]("http://www.debuntu.org/recover-root-password-single-user-mode-and-grub") guide to boot into single user mode and retrieve it.

---

### Post by tuxerman on 2008-09-07
Ubuntu has no root password. If you are referring to your user password (which is the one that you type when executing sudo or stuff like that), boot into the "recovery mode" option from the bootloader. YOu'll be given a root session. From there you can make the necessary changes to your user password, settings etc.

---

### Post by Breandean on 2008-09-09
I thought I must have been distracted duringthe install, but you are telling me 8.04 has no root password?

I tried compiz-check... su... sudo, su wants a password, the one I have is not accepted. sudo does something, but some tasks want the root password such as changing xconfig, to enable compiz.

My password by mistake is all upper case.

---

### Post by Frenske on 2008-09-09
Are you the administrator on the machine?

---

### Post by ingeva on 2008-09-09
> **Breandean said:**
> My password by mistake is all upper case.

That should not matter. The password you typed for your user during the installation and when you log in is the one you must use, exactly as you typed it. Until you change it of course.

---

### Post by m_duck on 2008-09-09
Ubuntu has the root account disabled by default. You can use sudo (and gksudo for graphical programs) to run programs as root user. When prompted for the password, enter the same one as you use to log in. As the root account is disabled, "su" does not work (in my experience). For a root shell, you can type: ```
sudo bash
```

---

### Post by Rocket2DMn on 2008-09-09
In Ubuntu we use sudo to perform administrative tasks.  The root account is disabled by default as a security precaution, primarily to prevent users from logging into X with a root session and running as the superuser full time (**major** security problem!).  When you use sudo, you are prompted for a password - this is *your* username's password, not a root password.  The original username created on the system is put into the "admin" group which has access to sudo.  You will also be prompted for a password when you access programs from System->Administration - this is the same deal (it's using graphical sudo instead of normal sudo).

---

