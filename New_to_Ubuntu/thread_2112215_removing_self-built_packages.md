---
title: "removing self-built packages"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by jaramarana on 2013-02-04
I've read elsewhere that to uninstall a package you built using  './configure && make' etc. you have to read the Makefile to  determine where on the system files may have been placed. Only, I can't  read this out of the makefile due to inexperience.

The package  I'm trying to uninstall is called 'movgrab'. There's a directory in my  home folder that seems to contain most of the parts, but I'm guessing  the program is also registered somewhere in the system so that when I  type it in to the cli, the computer knows what to do. How do I remove  things like that?

Thanks.

---

### Post by omeomi on 2013-02-04
The only way to do that is to use the uninstall script that is (hopefully) provided with the source.

You need to cd into the program directory and then type 'make uninstall', for example:
```
cd ~/movgrab  # if that is the directory
make uninstall
```

Also, you might want to look at [checkinstall]("http://www.asic-linux.com.mx/~izto/checkinstall/") when you compile packages yourself because that will allow for much easier uninstalling.

---

### Post by jaramarana on 2013-02-04
Thanks, but unfortunately the developer did not include an uninstall script. I've emailed him to no avail. In the meantime, I get this

> make: *** No rule to make target `uninstall'. Stop.In the future I will definitely be using checkinstall. Right now, is there anything I can do to get rid of this software? Should I just delete its main directory?

---

### Post by omeomi on 2013-02-04
Yes, the only way to remove the software is to remove all the files. Note that there might be other files aside from the directory in your home folder. 

You could try this command to find other files:
```
locate *movgrab*
```

---

### Post by jaramarana on 2013-02-04
Thanks for your help. The developer actually just replied, there's only one file outside the main directory that needs removing.

In the future, I'll use checkinstall.

Problem solved.

---

### Post by Lars Noodén on 2013-02-04
Another option is to use the source code to roll your own package.  Then you can install it or remove it using dpkg just like any other Ubuntu package from the repository.

[http://www.debian-administration.org/article/Rolling_your_own_Debian_packages_part_1](http://www.debian-administration.org/article/Rolling_your_own_Debian_packages_part_1)

[http://www.debian-administration.org/article/Rolling_your_own_Debian_packages_part_2](http://www.debian-administration.org/article/Rolling_your_own_Debian_packages_part_2)

The resulting .deb file can then be installed using dpkg.

---

