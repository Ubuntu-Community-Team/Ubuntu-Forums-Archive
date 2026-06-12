---
title: "drwxr-xr-x. and drwxr-xr-x+ : what's that? Where's the documentation?"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by uqbar on 2014-02-19
When listing files with "ls -la" I get this kind of output:
```
drwx------.  2 user user    23 gen 10 10:51 .vim
-rw-------.  1 user user   453 mag 11  2012 .vimrc
drwx------+ 13 user user  4096 feb 19 09:13 Desktop
drwx------.  3 user user  4096 feb 10 20:02 bin
drwx------.  6 user user    61 mar 16  2013 work
```
After the symbolic permissions I see a '.' or a '+'.
Neither "man ls" nor "info coreutils ls" led me to anything useful.
What's that? Where's the documentation for it?
Thanks in advance.

---

### Post by sudodus on 2014-02-19
File permissions (and d for directories) are described in this link

[http://blog.pluralsight.com/linux-file-permissions](http://blog.pluralsight.com/linux-file-permissions)

and you can find more tutorials if you browse the internet.

---

### Post by Lars Noodén on 2014-02-19
It looks like the directory *Desktop* may be using an [access control list](https://wiki.archlinux.org/index.php/Access_Control_Lists) (ACL).  They're not so commonly used so most documentation misses them.  You can read about [setfacl](http://manpages.ubuntu.com/manpages/saucy/en/man1/setfacl.1.html) and [getfacl](http://manpages.ubuntu.com/manpages/saucy/en/man1/getfacl.1.html).  Odds are that *Desktop* will show something more than the other directories.

```

getfacl ./Desktop
getfacl ./bin

```

---

### Post by sudodus on 2014-02-19
Interesting, Lars :-)

uqbar,
- What distro and version is it?
- And what file system?

---

### Post by Dennis N on 2014-02-19
> **Lars Noodén said:**
> It looks like the directory *Desktop* may be using an [access control list](https://wiki.archlinux.org/index.php/Access_Control_Lists) (ACL)... 
```

getfacl ./Desktop
getfacl ./bin

```

Thanks for the explanation and the getfacl command.

I always see this '+' when USB stick has been automounted at /media/user. Now I see what it means.

```
user@Sydney:/media$ ls -l
total 8
drwxr-x---+  3 root root 4096 Feb 19 07:56 user

```

Looking further with getfacl: The ACL gives user (and only user) r-x permissions for this folder. Otherwise, user would have --- permission (none).

---

