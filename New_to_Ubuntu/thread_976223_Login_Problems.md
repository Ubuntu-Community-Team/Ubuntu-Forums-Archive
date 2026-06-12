---
title: "Login Problems"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by SujayV on 2008-11-09
Hi All

Just installed Ubuntu 8.04 via a CD I received in the mail.

Installation went smoothly.  I remember what I chose for username and password etc.  

My problem is that when I try to login using the said username and password, I get an error message that says :

"Incorrect Username or Password. Letters must be typed in the correct case."

I am inputting the username and password in the correct case and exactly as it was on the installation screen.

I re-installed asking installation process to use the entire hard disk, re-configured the username and password.

I get the same problem.

I am new to Ubuntu (Linux in fact).  I know I am missing something but can not put my finger on it.

Can someone please help with why this is happening and if there is a way for a non-linux person to find out what the username and password the application is expecting is ?

I thank you all in advance and look forward to some help.

:confused:

---

### Post by bennachie on 2008-11-09
This is really just a blind guess, but, as I recall, the installer forces you to use an "all-lower-case" user name. Thus, if you type "Sujay" you actually get "sujay". However, the normal logon screen may just possibly accept "Sujay", hence the mismatch. If that's actually the case, I would class it as a bug. So far as I know, passwords are rendered faithfully in both environments.

Worth a try.

---

### Post by Peter09 on 2008-11-09
If you cannot succeed with this you can try logging in to recovery mode command prompt and trying

```
passwd <your user name> <your new password>
```

---

### Post by SujayV on 2008-11-09
Thank you to everyone.  I tried everything that our esteemed forumers have recommended.  Alas, with no success.  In the end, I re-installed Ubuntu 8.04 LE and re-entered the username / password carefully.  It now works.

WOW!  What a beautiful O/S.  Can't believe my loyalty to Microshmuck has kept me away from this O/S for so long.  I must add it was loyalty in ONE direction only.

I had reservations about the ease of installing applications, printers and so forth but it really isn't that difficult.

I am a convert who will be receommending Ubuntu to anyone who wants to listen.

Thanks again everyone.

---

