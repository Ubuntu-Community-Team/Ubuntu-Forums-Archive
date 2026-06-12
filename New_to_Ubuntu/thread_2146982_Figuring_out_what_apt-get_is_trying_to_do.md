---
title: "Figuring out what apt-get is trying to do"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by optize on 2013-05-20
I have a package (MySQL actually) that is set as "Status: install ok half-configured" and everytime I try to install something, it tries to do something related to MySQL, which is causing it to shut down. 

While this wouldn't usually be a problem, it's on a very important database server and MySQL just can't go down like that.  I'm afraid to figure out what it's trying to do, it takes a *long* time. 

Is there a way to figure out what it's trying to do BEFORE it actually does it?  Is there a script that is set to run post-install that I can take a look at?

---

### Post by lykwydchykyn on 2013-05-20
Checking /var/log/apt/term.log for the actual output from the apt-get command is probably a good place to start.  Maybe post it here.

---

### Post by optize on 2013-05-20
Log started: 2013-05-20  15:59:14
Setting up percona-server-server-5.5 (1:5.5.30-rel30.2-503.quantal) ...
 * Stopping MySQL (Percona Server) mysqld                                                                                                                                                                                                                                                                                                                            [ OK ]
chown: cannot access `/var/run/mysqld': No such file or directory

That's where it hangs, and I'm not sure what it's doing so I ctrl-C it.  Is there a way to determine the post-install script so I can feel better about 'letting it hang'?

---

### Post by lykwydchykyn on 2013-05-20
I believe that the post-install scripts are stored in /var/lib/dpkg/info.  You can probably find the appropriate scripts with this command:

```

ls /var/lib/dpkg/info/*.postinst |grep my

```

---

### Post by optize on 2013-05-20
Yep, that's what I need.

Thanks!

---

