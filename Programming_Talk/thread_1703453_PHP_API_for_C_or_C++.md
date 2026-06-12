---
title: "PHP API for C or C++?"
date: 2011-03-09
forum: Programming Talk
---

### Post by samalex on 2011-03-09
I'm drafting out a new project to create a Telnet and SSH server in C or C++ (not sure which yet) to basically function like an old-school BBS.  The twist though is I'd like to give the 'SysOp' the ability to write custom pages in PHP not too dissimilar from web sites.  Granted there'll be some tweaks to getting ANSI graphics to work, but I've done some testing and I think that part won't be too difficult.

The advantage to this is some PHP code can hopefully be tweaked to 

My challenge now is finding someway to marry PHP and C or C++ so C/C++ will drive the server but accept content from the PHP parser/api.

Any suggestions or pointers on a starting point to get these working together?

Thanks --

Sam

---

### Post by laceration on 2011-03-09
The hundreds of PHP extensions are written in C (as is PHP itself).  You could write your own and compile it into PHP.
[http://us.php.net/manual/en/internals2.structure.php](http://us.php.net/manual/en/internals2.structure.php)

There may even be an extension already written for what you want to do, there is a lot of them so who knows?

---

