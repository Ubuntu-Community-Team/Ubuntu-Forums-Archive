---
title: "Debian packaging - postinst, postrm, preinst, prerm and control has bad permissions?"
date: 2015-05-30
forum: Programming Talk
---

### Post by flaymond on 2015-05-30
Hello everyone!

I'm actually packaging python scripts with Debreate. I got a bunch of errors and a tons of warning while packaging my simple (for test) pygtk application. I just use standard scripts that generated from Debreate, however, the scripts for installing and removing applications has 'bad permissions'. The  pygtk application is installed fine on my PC, and I can access it without typing the actual path of the program from /usr/bin. Sadly, the error will cause the user that trying to install it using ubuntu software center mentioning about the bad quality of the package. So for short, here is the problem.

1.  prerm, postinst, postrm and control files generated script by Debreate cause Lintian put's a bunch errors about bad permissions (0755 != 0755)

2. I don't know if my applications is installed in the right directory (and this might be the ultimate problem because of this)

3. I don't believe that setup.py needed for this, because I try packaging deb with ruby, bash and others and still the errors are same although the installation are fine.

Here is the builded .deb package and the lintian output

[ATTACH]262304[/ATTACH]

and here is Debreate .deb file (for anyone wanna to try packaging with it or to see where in the process that causes the problem)

[ATTACH]262305[/ATTACH]

Thanks for help!

UPDATE - Here is the output from ls -l 

```
ls-l
-rwxr-xr-x 1 alex alex 938 May  30 17:10 myappj  # in /usr/share/
#################################################
# in /DEBIAN directory
total 12
-rw-r--r-- 1 alex alex 303 May  30 17:12 control
-rwxr-xr-x 1 alex alex  61 May  30 17:12 postinst
-rwxr-xr-x 1 alex alex  37 May  30 17:12 prerm

```

---

### Post by sudodus on 2015-05-30
I know other people know much more than I about programming and packaging, but at least I can help with some tips about file permissions.

> **InterProg said:**
> 
```
ls-l
-rwxr-xr-x 1 alex alex 938 May  30 17:10 myappj  # in /usr/share/

```

```
-rwxr-xr-x
```

corresponds to 755 permissions meaning

```
user:  read/write/execute
group: read/-/execute
others:read/-/execute
```

I don't know why the system is complaining about those permissions.

See ```
man chmod
``` and you can browse the internet for ***tutorial linux file permissions***

for example these links

[https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

[http://ryanstutorials.net/linuxtutorial/permissions.php](http://ryanstutorials.net/linuxtutorial/permissions.php)

---

### Post by flaymond on 2015-05-30
After a few times packaging it, I try to skip for generating prerm, preinst, postrm, postinst and the ERRORS reduced from 4 to 1 and ubuntu-software-center not complaining it anymore. Also, the files path is a mistake, I put the executable in the share directories instead of /usr/bin.  Although, the warning still a lot. (most of them are unecessary). I found out that file permission is correct, and after reading an article from the link give by sudodus, I narrowed down the warning from a lot to unecessary quantity of warnings(no manpages, etc). Now, I got no errors at all. Just 10 warnings, about non standard file permission (0755 != 0755 and 0664 != 0664). I believe it's something wrong with the setup, I'm glad the errors are actually gone. I should not follow the compiled program packaging style, in this case for scripts packaging. Thank you sudodus for helping me!


Now I just need to learn packaging .deb, ***in Debian way.***

---

