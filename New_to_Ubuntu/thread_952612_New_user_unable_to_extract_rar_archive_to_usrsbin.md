---
title: "New user: unable to extract rar archive to /usr/sbin"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by pingtiao on 2008-10-19
Hi there.
First post- so apologies if this is answered already- I'm too newbie to even know what terms I need to search for!

I am trying to extract some rar archives of programs (one of a sync program to sync Evolution with google calendar), but doing it gives me the error 
> checkdir error:  cannot create /usr/sbin/GCALDaemon
                 unable to process GCALDaemon/.

I don't understand how to do this- can anyone help?

thanks in advance

---

### Post by oldos2er on 2008-10-19
In order to give your self write access to anything outside your home directory, you need admin privileges. In Ubuntu this is done by prefacing the unrar command with "sudo." See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Gutt on 2008-10-19
Just do
```
Sudo Nautilus
```

And with the new Nautilus window opened, extract rar archive and send it to /usr/sbin

---

### Post by pingtiao on 2008-10-19
Thanks both of you.
Is it possible to stay within the GUI and do this?
Just clicking "extract archive" for example...?

---

### Post by oldos2er on 2008-10-19
> **Gutt said:**
> Just do
```
Sudo Nautilus
```And with the new Nautilus window opened, extract rar archive and send it to /usr/sbin

 Linux is case-sensitive; and when calling up graphical programs in Gnome, you want to use "gksu" or "gksudo." The proper command would be "gksu nautilus".

---

