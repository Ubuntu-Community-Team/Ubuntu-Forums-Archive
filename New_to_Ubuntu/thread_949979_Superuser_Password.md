---
title: "Superuser Password"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by toasty_ghosty on 2008-10-16
Hello

Forgive me this may seem like a stupid question or a completely pointless one. I needed to copy and paste a file but it turned out I needed to be the superuser. I type "su" in terminal to do the act of copying and pasting, and when I entered my password it said I was wrong. However, I entered the same password when I do use "sudo". Whats going on here?

Thanks.

*I just realized that Ubuntu disabled the su feature. But is there a way to activate it? Or is that just not recommended?

---

### Post by anystupidname on 2008-10-16
The root user in ubuntu is not active on purpose at first.
Many *nix users advocate rarely or never using the root account for security reasons. If you don't want to

> sudo mv /file/whatever /file/destination

and really want to log in as the actual root user, you can do so with

> sudo su


which should then prompt you to setup a root account password.

---

### Post by Sarmacid on 2008-10-16
su password is the password for the root account. Sudo password is the password for your account. If you need to do something as root, I would suggest using sudo <command>, or if you don't want to type it many times, try sudo -i, then exit after you execute all the commands.

---

### Post by toasty_ghosty on 2008-10-16
Thanks. Every once in a while I have a question you everyone here never fails to answer it. Thanks.

But now I have one "issue". My computer works just as it should. It does everything for me I need it to do, and, without complaining. 

So what next?

---

### Post by GuitarRocker2562 on 2008-10-16
> **toasty_ghosty said:**
> Thanks. Every once in a while I have a question you everyone here never fails to answer it. Thanks.

But now I have one "issue". My computer works just as it should. It does everything for me I need it to do, and, without complaining. 

So what next?

Haha, I know what you mean. If your up to it, try out Intrepid, just a warning, anything can happen, so if you need a stable system don't use it. Oh, and you may want to backup your files just incase.

---

### Post by cariboo on 2008-10-16
Fix it 'til it's broke :)

Jim

---

