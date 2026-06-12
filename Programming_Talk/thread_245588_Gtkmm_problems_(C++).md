---
title: "Gtkmm problems (C++)"
date: 2006-08-28
forum: Programming Talk
---

### Post by JoshHendo on 2006-08-28
When I try and compile the code on the following link, with the command supplied, it comes up with the following error:

[http://gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html](http://gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html)

```

josh@c1:~/Programing/C++$ g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`
Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found
simple.cc:1:19: error: gtkmm.h: No such file or directory
simple.cc: In function ‘int main(int, char**)’:
simple.cc:5: error: ‘Gtk’ has not been declared
simple.cc:5: error: ‘Main’ was not declared in this scope
simple.cc:5: error: expected `;' before ‘kit’
simple.cc:7: error: ‘Gtk’ has not been declared
simple.cc:7: error: ‘Window’ was not declared in this scope
simple.cc:7: error: expected `;' before ‘window’
simple.cc:9: error: ‘Gtk’ has not been declared
simple.cc:9: error: ‘window’ was not declared in this scope
simple.cc:9: error: ‘run’ was not declared in this scope

```

How would I be able to fix this :)?

Thanks!

- Josh

---

### Post by amo-ej1 on 2006-08-28
The problem is that the substition `pkg-config gtkmm-2.4 ....` fails because it is unknown to pkg-config.
Do a pkg-config --list-all to get a list of all known modules. My guess would  be the following. Is it possible that you apt-get 'ed libgtkmm-dev instead of libgtkmm-2.4-dev ? When I isntall libgtkmm-dev pkg-config fails while it works perfectly (for me) with libgtkmm-2.4-dev

---

### Post by JoshHendo on 2006-08-28
When I run:

apt-get install libgtkmm-dev

I get the following message:

```

Reading package lists... Done
Building dependency tree... Done
libgtkmm-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

When I run libgtkmm-2.4-dev I get the following:

```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtkmm-2.4-dev: Depends: libgtk2.0-dev (> 2.6.0) but it is not going to be installed
E: Broken packages

```

---

### Post by amo-ej1 on 2006-08-28
```

edb@lapedb:~$ apt-cache search libgtkmm
libgtkmm-2.4-doc - C++ wrappers for GTK+ 2.4 (documentation)
libgtkmm-dev - C++ wrapper for GTK+ 1.2 (development files)
libgtkmm-doc - C++ wrapper for GTK+ 1.2 (documentation)
libgtkmm1.2-0c2a - C++ wrappers for GTK+ 1.2 (shared libraries)
libgtkmm2.0-1c2a - C++ wrappers for GTK+ 2.0 (shared libraries)
libgtkmm2.0-dev - C++ wrappers for GTK+ 2.0 (development files)
libgtkmm2.0-doc - C++ wrappers for GTK+ 2.0 (documentation)
libgtkmm-2.4-1c2a - C++ wrappers for GTK+ 2.4 (shared libraries)
libgtkmm-2.4-dev - C++ wrappers for GTK+ 2.4 (development files)

```

Perhaps you should fiddle with your dependencies in order to get the libgtkmm-2.4-dev installed ?

---

### Post by JoshHendo on 2006-09-01
I have got the dependecy problem down to 1 package:

libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.2-0ubuntu2 is to be installed

I can't seem to get the right version installed. Is there any thing that I can do to get this working?

Thanks!

---

### Post by kaamos on 2006-09-01
```
Is there any thing that I can do to get this working?
```

Roll back to the default ubuntu packages instead of the compiz/xgl packages you have now.

---

### Post by JoshHendo on 2006-09-01
So remove the Ubuntu repo? I will give that a go and see what happens. Thanks :)

Edit: Didn't seem to work. Have any suggestions on how I would go about rolling back everything? Thanks :)

---

### Post by kaamos on 2006-09-01
```
So remove the Ubuntu repo?
```

Err.. remove the compiz repo and then you must manually downgrade the packages with synaptic (the packages are in "local/obsolete").

You could also wait if someone has a better idea of getting gtkmm going. :)

---

### Post by JoshHendo on 2006-09-01
> **kaamos said:**
> ```
So remove the Ubuntu repo?
```

Err.. remove the compiz repo

Thats what I ment :)

Hopefully I will be able to get it working soon :)

---

### Post by chojin on 2007-04-01
surely it's not a great solution to ask someone to downgrade their software to get a dependency satisfied?

I have a similar problem trying to install some libcairo-dev packages and I seriously don't want to downgrade my entire system just to install them... gah... *installs osx*

---

