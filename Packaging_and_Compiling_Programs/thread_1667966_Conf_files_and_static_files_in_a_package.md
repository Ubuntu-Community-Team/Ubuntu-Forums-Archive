---
title: "Conf files and static files in a package"
date: 2011-01-15
forum: Packaging and Compiling Programs
---

### Post by pablop on 2011-01-15
Hi

How do I tell debuild which files are conf files and should go to /etc/mypkg/fname.conf ?
I've tried to put it under mypkg-0.1/etc/mypkg/fname.conf but debuild ignores it.
The debian guide says all files under etc/ are treated automatically as conf files but it doesn't work for me:
[http://www.debian.org/doc/maint-guide/ch-dother.en.html#s-conffiles](http://www.debian.org/doc/maint-guide/ch-dother.en.html#s-conffiles)

I also don't understand how to include static files in the package.
Do I have to use the install file to list all the files and folders?
I thought that putting everything with the full path under the mypkgs-0.1 folder should work.

Thanks

---

### Post by cjssmo on 2011-02-04
Have a look at the manpage for dh_install.

Basically add the file "install" to the debian directory and in this file list all the files to be installed and the location where you want them installed.  For example if you want myapp/foo to install to /etc/myapp list it like this in the "install" file:

/foo /etc/myapp

foo is then installed into /etc/myapp/foo

you can also do the same for directories lets say you have a directory that contains

myapp/baz/myfile1
myapp/baz/myfile2
myapp/baz/myfile3

and you want to install all the content of baz into /usr/share it would be listed in the install file like this:

/baz /usr/share

Thus producing 

/usr/share/baz/myfile1
/usr/share/baz/myfile2
/usr/share/baz/myfile3

Hope this helps

---

