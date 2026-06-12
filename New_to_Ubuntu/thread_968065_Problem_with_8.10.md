---
title: "Problem with 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Ginoxy on 2008-11-02
Hi, 
Seems like there is a problem with 8.10 ! everytime i need to update i get this window message i've tried so many servers but still the same !

---

### Post by ezramorris on 2008-11-02
> **Ginoxy said:**
> Hi, 
Seems like there is a problem with 8.10 ! everytime i need to update i get this window message i've tried so many servers but still the same !

This isn't too much to worry about. You should still be able to install and update packages.

Try closing any update/install programs, opening a terminal and running
```
sudo apt-get update
```
Then try again.

If this doesn't work, you will need to reinstall the GPG key. This is pretty straight forward, but I don't know the URL you need. Maybe someone else will.

---

### Post by Ginoxy on 2008-11-02
Any idea?

---

### Post by Ginoxy on 2008-11-02
Fetched 192B in 2s (86B/s)                       
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


this is what i got in Terminal !

---

### Post by Swenghk on 2008-11-02
Maybe it's because it's still in an early stage?

---

### Post by MJWitter on 2008-11-02
Give this a try, it worked for me and a few others:
> sudo apt-get update -o Acquire::http::No-Cache=true

---

### Post by Ginoxy on 2008-11-02
YES Worked ! 

THANKS DUDE :)

---

### Post by MJWitter on 2008-11-02
No prob! Please remember to mark the thread as solved.

---

