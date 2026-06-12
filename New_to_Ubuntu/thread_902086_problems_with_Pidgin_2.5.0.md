---
title: "problems with Pidgin 2.5.0"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Lelito on 2008-08-27
Hi all guys, i 've a problem with pidgin 2.5.0 i've seen this installation guide (-> [http://yisheng.wordpress.com/2008/08/20/compile-pidgin-250-for-ubuntu/](http://yisheng.wordpress.com/2008/08/20/compile-pidgin-250-for-ubuntu/) ) to install pidgin messenger, but it's so strange after the procedure the program do not run.. i see in the Application the Pidgin's icon but it do not run. How i can solve this problem? 

N.B i've already unistalled older version and update library as the guide says

Bye :lolflag:

I've just repeat the secuence and now the terminal says-> pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

---

### Post by patrickballeux on 2008-08-27
Go to [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

The packages are available for Ubuntu...


But first, remove what you have compiled (run sudo make uninstall).


You have a dependency problem with libpurple.  Probably that the libpurple library is located in /usr/local/lib and pidgin is trying to find it in /usr/lib instead.

But go with the package, you will save a lot of time.

Good luck!

---

### Post by kostkon on 2008-08-27
It will also come as an update in a few days, I assume:

[https://bugs.launchpad.net/hardy-backports/+bug/260070](https://bugs.launchpad.net/hardy-backports/+bug/260070)

---

### Post by Lelito on 2008-08-27
Hi again guys..tnx for the support but..i can't remove the program with terminal -> it says to me make: *** No rule to make target `unistall'.  Stop.
 I do not know how remove that thing..cause the original program pidgin 2.4.1 has been removed..but i still see in application Pidgin's icon.


Ok ok i've solucioned the problem like patrcik said...tnx a lot.. but i've not remove what i've compiled before...but it run :P

---

