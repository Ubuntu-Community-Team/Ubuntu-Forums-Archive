---
title: "Git-svn Connection Failure"
date: 2009-05-03
forum: Programming Talk
---

### Post by huangyingw on 2009-05-03
Hello,
   I am trying git. When I use command "git-svn clone -s svn://localhost/svn/myproject", I got following error:
```

Connection refused: Can't connect to host 'localhost': 
Connection refused at /usr/bin/git-svn line 1493

```
What is the cause?

---

### Post by wmcbrine on 2009-05-04
Er... you don't have an SVN server running on your machine?

Use the address of the SVN server instead of "localhost".

---

### Post by huangyingw on 2009-05-04
> **wmcbrine said:**
> Er... you don't have an SVN server running on your machine?

Use the address of the SVN server instead of "localhost".
Cheers, I have solved this. It's not the fault of localhost, for I really have a svn server on that machine. And my localhost's IP is indeed 192.168.0.8.
While, I succeed with following command: "git svn clone http://192.168.0.8/svn/myproject".

---

