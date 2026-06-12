---
title: "Password"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by (Nes) on 2011-09-12
Is there a way to force Ubuntu to accept the password I want even if it's "too short"?

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> Is there a way to force Ubuntu to accept the password I want even if it's "too short"?


not a good idea but it is possible.

See here [https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html) and scroll down for password policy section.

and here [http://linuxpoison.blogspot.com/2010/10/how-to-set-password-length-in-ubuntu.html](http://linuxpoison.blogspot.com/2010/10/how-to-set-password-length-in-ubuntu.html)


remember passwords exist to make your life easier, shortening their strength makes them more easy to crack and circumvents the intended security model.

Cheers

---

### Post by (Nes) on 2011-09-12
terminal can't recognize the password command?
Did I read the instructions wrong :S?

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> terminal can't recognize the password command?
Did I read the instructions wrong :S?

there is no password command. there is passwd.

however i think you mean the area where is mentions type:

password required.....xxx....xxx etc

This is the entry in a file /etc/pam.d/common-password

that needs to be modified.

You dont typen it from terminal

---

### Post by (Nes) on 2011-09-12
:-# doh!

Guess I should have read more carefully!!! Thanks :)

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> :-# doh!

Guess I should have read more carefully!!! Thanks :)


ha ha no worries.

if this is solved please use thread tools menu to mark thread as solved.

glad i could help.

cheers

---

