---
title: "[SOLVED] can't vreat file/no permission"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Mr Pockets151 on 2008-06-04
I'm trying to create "asound.conf" into my /etc.  But when I try I get permission denied.  I went to terminal and enter "su" then my password and I get an authentication error.  What did I do wrong.  I used to be able to do it.

---

### Post by Joeb454 on 2008-06-04
Just to create the file ```
sudo touch /etc/asound.conf
```

To edit it in gedit ```
gksudo gedit /etc/asound.conf
``` :)

I'd recommend running those in that order :)

---

### Post by tamoneya on 2008-06-04
follow the steps listed above.

As for why su didnt work: Ubuntu strongly advises that you do not ever log in as root and instead you should use gksudo and sudo.  To do this they set the root user password to a random password so that you cannot login to root unless you set the password after the install manually.

---

### Post by Joeb454 on 2008-06-04
su does actually work in Ubuntu, if you have more than one user.

I use it on my server a lot, say for example tamoneya has an account on my PC, I could run ```
su tamoneya
password: <I enter tamoneya's PW>

tamoneya@machine::~$
```

:) I thought I'd clear that up

---

### Post by Mr Pockets151 on 2008-06-04
Thanks that worked perfect.

---

### Post by Joeb454 on 2008-06-04
Glad to know, you can mark your thread solved from "Thread Tools" at the top of this page :)

---

