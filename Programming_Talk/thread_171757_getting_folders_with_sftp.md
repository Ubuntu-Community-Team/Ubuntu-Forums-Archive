---
title: "getting folders with sftp"
date: 2006-05-07
forum: Programming Talk
---

### Post by orlox on 2006-05-07
Hi, i'm trying to use sftp to retrieve a folder from a server, but when i try doing a get, this is what happens (the folder im trying to get is "imagenes"):
```

sftp> get imagenes
Fetching /opt/apache-tomcat-5.5.17/webapps/grupo11/imagenes to imagenes
Cannot download non-regular file: /opt/apache-tomcat-5.5.17/webapps/grupo11/imagenes

```
am I doing this right?...or to get a folder you need to do somehing else?

---

### Post by souki on 2006-05-07
you can't do a recursive get with sftp
you should use scp instead
```
scp -r user@host:/the/path/ .
```

---

### Post by orlox on 2006-05-07
I used scp and got this:
```

pablo@pcpablo:~/workspace/iic3592$ scp grupo11@kegan.ing.puc.cl:public_html/ -r
Password:
scp: public_html: not a regular file
pablo@pcpablo:~/workspace/iic3592$

```
I changed the location of the -r cause otherwise, it would give away a "usage" message...still get the same message that sftp gave me: "not a regular file"...

---

### Post by souki on 2006-05-07
you have to use absolute path, see my previous post
NB: don't forget the '.' at the end, it is the destination directory (I don't know if omiting it works)

---

### Post by orlox on 2006-05-07
Done !
thanks for your help...

---

### Post by Tyson D on 2010-07-13
Perfect! it worked for me too.

---

### Post by jumpgap on 2011-10-10
thanks for the post.  helped me also.

---

### Post by slavik on 2011-10-11
old thread.

---

