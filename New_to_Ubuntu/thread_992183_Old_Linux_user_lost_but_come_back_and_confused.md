---
title: "Old Linux user lost but come back and confused"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Daveil on 2008-11-24
I used Debian some time ago, back when I was in college. Which was some time around 2004. I was using Windows (shutters) because I was running a program that didn't run in Linux. Well My problem is I just installed Ubuntu, because someone told me that it would help me get back into the swing of things. When I installed it I set up a user, but it did not ask me to set up a root user. So now I am not sure what I can do to install programs that require Admin access. Any ideas?

---

### Post by snowpine on 2008-11-24
Hi Daveil, Ubuntu does not use a root account (unlike most other linux distros). Simply preface commands with 'sudo' if you need temporary root access. (or 'gksu' if it is a graphical application) When prompted, enter your regular user password.

example: sudo nano /etc/apt/sources.list
or: gksu gedit /etc/apt/sources.list

---

### Post by phidia on 2008-11-24
There is no root user in Ubuntu. Instead the default is to use sudo with your user password.

Added: you might also want to read the "Getting Started" section from the Ubuntu wiki [here]("https://help.ubuntu.com/community").

---

### Post by ubuntu27 on 2008-11-24
**By default, the root account password is locked in Ubuntu.** This means that you cannot login as root directly or use the su command to become the root user. However, since the root account physically exists it is still possible to run programs with root-level privileges. This is where sudo comes in - it allows authorized users (normally "Administrative" users; for further information please refer to [AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")) to run certain programs as root without having to know the root password. 

[More about Ubuntu's sudo and how to use it]("https://help.ubuntu.com/community/RootSudo")

---

### Post by snowpine on 2008-11-24
Also to clarify, since I am sure someone will ask the question sooner or later, it is possible--in fact, easy--to change Ubuntu's default security model to be more like Debian's. However, posting a how-to on this topic is not allowed on Ubuntuforums.org because the forum policy is to promote Ubuntu's default security model. It is not hard to find this information elsewhere if you prefer the Debian model. ;)

I will also point out that Debian is still around, and that it's possible for a Debian user to lock the root user and use sudo instead, just like in Ubuntu. It is great as Linux users that we have this choice. :)

---

### Post by Daveil on 2008-11-24
Thanks, I was thinking that I was not setting it up right. That helps a lot. :guitar:

---

### Post by Kellemora on 2008-11-25
Hi Daviel

I'm surprised no one mentioned that you can INSTALL a ROOT TERMINAL under Applications, System Tools simply by right clicking on Applications, then left click on Edit Menus.

It Saves a lot of extra typing if you need to do repetitive tasks as Root!

Also, Your root password is the same as your Administrator Password!

TTUL
Gary

---

### Post by Keen101 on 2008-11-25
the root user is disabled by default. You can enable it with this command, but you still will not be able to login as root (At least in the GDM login) because of security reasons.

```
sudo passwd root
```


also, get yourself a good ubuntu book.

I recommend **_Beginning Ubuntu Linux: from novice to professional_**. By APRESS.

---

### Post by ubuntu27 on 2008-11-25
Also, in the present version of Debian, when you are in the installation process if you ignore to create a root account, it automatically creates sudo like in Ubuntu.  I am saying it from my own experience, I used sudo in Debian 4.0

---

