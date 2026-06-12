---
title: "login as root"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by vjayaraju on 2008-07-08
How can I log in as root in Ubuntu?

---

### Post by overdrank on 2008-07-08
> **vjayaraju said:**
> How can I log in as root in Ubuntu?

Hi and welcome, this link may help
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by carrarin on 2008-07-08
i dont think the let you do that. if you want in the terminal you can give yourself su abitilys, but im not sure if you can login as root
:damn beaten to the punch again: oh well

---

### Post by tamoneya on 2008-07-08
in general it is advised otherwise because of the security implications.  In ubuntu the root password is set randomly during the install.  If you want root permissions you should sudo to get them.

EDIT: late as well

---

### Post by cpetercarter on 2008-07-08
You don't. The root account is disabled by default in Ubuntu.Instead you give yourself temporary root privileges when you need them. If you are using the terminal to, say, download and install new software, you preface the command with "sudo" e.g."sudo apt-get somesupersoftware install". You will be asked for your password. Type it in and press enter. Similarly, if you are using e.g. synaptic package manager, you will be asked for your password.

---

### Post by overdrank on 2008-07-08
> **carrarin said:**
> i dont think the let you do that. if you want in the terminal you can give yourself su abitilys, but im not sure if you can login as root
:damn beaten to the punch again: oh well

Don't fret I will not always be here. :)

---

### Post by carrarin on 2008-07-08
this whole root thing i noticede from the start, hated loging in and then not having priveledges to delete opertating system files. 
:mad: i wanted to expirement

---

### Post by karasuman on 2008-07-08
It's a bad idea to log in as root, but you CAN do it.  When I told my friend the BSD-user that I logged in as root to replace a file owned by root, the look on his face convinced me to never do it again.  If you really want to be able to do it, I figured it out with about ten minutes in google, but I cannot, in good conscience, share the wisdom.

What do you want to do as root, anyway?  If you just want to have freer access to files, like I did, try

```
sudo nautilus
```

---

### Post by carrarin on 2008-07-08
the way of logging in that shouldn't be spoken of, does that only work for freebsd. i tried that with ubuntu, and i got an error.

---

### Post by chrisccoulson on 2008-07-08
[It is against forum policy to post log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=765414")

---

### Post by carrarin on 2008-07-08
you aren't gonna send me to jail will you! id get eaten alive!!!

---

### Post by sydbat on 2008-07-08
Yup. The "root" police are on their way...:lolflag:

---

### Post by carrarin on 2008-07-08
NOOOO!! I wont go back. Im taking my computer hostage. You CANT STOp MEE!!!

---

### Post by tamoneya on 2008-07-08
> **karasuman said:**
> It's a bad idea to log in as root, but you CAN do it.  When I told my friend the BSD-user that I logged in as root to replace a file owned by root, the look on his face convinced me to never do it again.  If you really want to be able to do it, I figured it out with about ten minutes in google, but I cannot, in good conscience, share the wisdom.

What do you want to do as root, anyway?  If you just want to have freer access to files, like I did, try

```
sudo nautilus
```

since nautilus is graphical you would be better off with gksudo:```
gksudo nautilus
```

---

### Post by chrisccoulson on 2008-07-08
> **carrarin said:**
> you aren't gonna send me to jail will you! id get eaten alive!!!

So far, no-one has told the original poster how to do it, and I just wanted to make sure that the original poster understood why this was, and to remind everyone that they aren't allowed to

---

### Post by carrarin on 2008-07-08
Ok ill put down the computer. that was close.

---

### Post by sydbat on 2008-07-08
> **chrisccoulson said:**
> So far, no-one has told the original poster how to do it, and I just wanted to make sure that the original poster understood why this was.

Absolutely. Just having fun now...

---

### Post by bodhi.zazen on 2008-07-08
> **sydbat said:**
> Yup. The "root" police are on their way...:lolflag:
They are here ...

```
sudo slap wrists
```

---

### Post by t0p on 2008-07-08
```
man passwd
```

---

