---
title: "Change in passwd file( /etc/passwd )"
date: 2017-03-12
forum: New to Ubuntu
---

### Post by saukatali14 on 2017-03-12
sir/mam,
             I accidently change the UID and GID of my UserAccount(sumali) in /etc/passwd file.
             I change the value from 1000 to 0 of both filed,
             and finally i run the command # updatedb .
             After that i get error,
             i cannot do any thing, unknown user id error is getting.
             and my user sumali is not show in useraccount.
             my system also not accept my root password.
             i cannot edit again in /etc/passwd file.(error:- read only file, cannot lock it etc) 
             please help me to recover my userid(sumali).

---

### Post by wildmanne39 on 2017-03-12
*Thread moved to **New to Ubuntu**.*

---

### Post by Impavidus on 2017-03-12
Boot into recovery mode, drop to a root shell (hope that works) and remount the file system read-write. See the first part of [this guide](http://www.psychocats.net/ubuntu/resetpassword). Then you should be able to fix your /etc/passwd. Alternatively, use a live disk.

Personally, I wouldn't mess with /etc/passwd manually. It's rarely useful.

---

### Post by saukatali14 on 2017-03-12
I got the error when i change the password:- Authentication token manipulation error

---

### Post by steeldriver on 2017-03-12
You didn't correctly remount the filesystem

```

mount -o remount,rw /

```

Note the spaces and punctuation carefully

---

### Post by saukatali14 on 2017-03-12
Yes, I successfully change the password.
But how I gain my User.
It only open in guest&#8203; session.
Not show my UserName.
Please tell the process to edit the /etc/passwd.
So I get my Username and login.

---

### Post by steeldriver on 2017-03-12
I don't really understand why you changed your password - according to your original post the issue was that you

> 
accidently change the UID and GID of my UserAccount(sumali) in /etc/passwd file


You need to change those things back - either

```

nano /etc/passwd

```

from your recovery root shell and make the appropriate edits or (perhaps safer)

```

usermod -u 1000 -g 1000 sumali

```

---

### Post by saukatali14 on 2017-03-12
Thanks, to all of you.
I got my solution.

---

### Post by oldos2er on 2017-03-12
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It will help others who might be having the same problem. Thanks.

---

