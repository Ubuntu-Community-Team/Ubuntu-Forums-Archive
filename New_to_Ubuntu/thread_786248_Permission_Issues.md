---
title: "Permission Issues"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Hood15 on 2008-05-08
Hello,

I'm experiencing a few issues while trying to install LAMP on my newly installed ubuntu.

I attempted doing it through the Terminal with some lines that I got off a website and they returned errors that said I wasn't permitted and to see if I was the root user. I'm logged in as the account I made when running the installer so I should have permission to do anything I want; correct? Well I decided to use the Package Manager program to install apache and php and it worked fine. Then I went to edit the php file it creates upon installation (var/www/tstphp.php) and it said, once again, that I wasn't permitted?

Why am I having these issues, any ideas?

---

### Post by tamoneya on 2008-05-08
please post the result of ```
ls -la /var/www/
```

---

### Post by Hood15 on 2008-05-08
> ls -la /var/www/

resulted

> 
total 12
drwxr-xr-x  2 root root 4096 2008-05-07 23:52 .
drwxr-xr-x 16 root root 4096 2008-05-07 23:52 ..
-rw-r--r--  1 root root   45 2008-05-07 23:52 index.html


---

### Post by tamoneya on 2008-05-08
it appears that /var/www/tstphp.php doesnt even exist.  Try creating it with ```
gksudo gedit /var/www/tstphp.php
```

---

### Post by jesusfreak107 on 2008-05-08
when you input the code, did you use "sudo" at the beginning, and have to type your password?  if not, try it.

---

### Post by jesusfreak107 on 2008-05-08
also, to access a file you are not being permitted access to, enter "gksudo nautilus" (you will have to enter your password).  that should bring up a folder window, with root privileges.

---

### Post by Hood15 on 2008-05-08
The website I was using had me typing sudo in front of the commands and it gave a different error.

---

### Post by Hood15 on 2008-05-08
> **tamoneya said:**
> it appears that /var/www/tstphp.php doesnt even exist.  Try creating it with ```
gksudo gedit /var/www/tstphp.php
```

Ok, did that and it allowed me to create the file but now when I go to [http://localhost/tstphp.php](http://localhost/tstphp.php) it asks me to download the file rather than executing it?

---

### Post by Hood15 on 2008-05-08
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) is the site I was trying to use and when I attempted to use the first line of code it suggests I got:

> 
danny@TestBox:~$ sudo apt-get install apache2
sudo: unable to resolve host TestBox


---

### Post by Hood15 on 2008-05-08
Any ideas? Anyone?

---

### Post by freebeer on 2008-05-08
You'd have better success posting over at the Server subforum, I think.

The error you're getting implies to me that the host (the name of your computer hosting the files" isn't the same as what the script is expecting.  ie the script is expecting to talk to "fred" but your host name is "barney".  Something along those lines.

---

