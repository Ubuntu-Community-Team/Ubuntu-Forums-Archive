---
title: "install python module without root"
date: 2009-04-17
forum: Programming Talk
---

### Post by flylehe on 2009-04-17
Hi,
I was trying to run a python script on a server. My script needs a module called subprocess, however it hasn't been installed on the server yet. I don't have root access. Is it possible to install it then? 

I remember under C++ and C, even without root, I could always install some libraries from building from source. For some binary, e.g. adobe reader, I could install it too. So what's the magic behind these difference: some could be installed without root while some cannot?

Thanks and regards!

---

### Post by amingv on 2009-04-17
If you mean install it in your home folder, yes.
If you mean install it system-wide, no.

But you can alwas just put the module next to your source file and import it from PWD...huh?

---

### Post by flylehe on 2009-04-17
Thanks.
I'd like to install in my home.
I just found that subprocess is introduced and incorporated in Python 2.4.1, while my server has Python 2.3.4. Is it possible to install subprocess for Python 2.3.4? Where can I get its source distribution?
Thanks!

---

### Post by amingv on 2009-04-17
The last version of python automatically updated in my system was 2.6, has this server been updated often?

Maybe you should speak to the admin and ask him to update it for you...

Though most modules for python 2.4 should work on 2.3 (provided they don´t need some other new modules), an update would make for a better solution altogether IMHO.

---

### Post by croto on 2009-04-17
Hi. I have installed python modules in my home directory (without root access of course) following [http://docs.python.org/install/index.html#alternate-installation-the-home-scheme]("http://docs.python.org/install/index.html#alternate-installation-the-home-scheme")

Let us know how it goes!

---

### Post by flylehe on 2009-04-18
Thanks! 
Where do you usually download the modules, e.g. subprocess?

---

### Post by evymetal on 2009-04-18
Subprocess is part of the standard libary - i.e. it's included in python itself when it's installed.

(Hence it's not available on the python package index [http://pypi.python.org/pypi](http://pypi.python.org/pypi))

It does seem to be a pure python module though, so you could try downloading the module from the python svn server, and see if it works on your version.

Here's a link to the version of the module that shipped with 2.4.3
[http://svn.python.org/view/python/tags/r243/Lib/subprocess.py?view=markup](http://svn.python.org/view/python/tags/r243/Lib/subprocess.py?view=markup)

---

### Post by flylehe on 2009-04-18
> **evymetal said:**
> 
Here's a link to the version of the module that shipped with 2.4.3
[http://svn.python.org/view/python/tags/r243/Lib/subprocess.py?view=markup](http://svn.python.org/view/python/tags/r243/Lib/subprocess.py?view=markup)

Thanks! So does it mean that I don't have to actually install the module, but just import that single file subprocess.py into my script? 
How do those modules that need setup.py make a difference then?

---

### Post by evymetal on 2009-04-18
> **flylehe said:**
> Thanks! So does it mean that I don't have to actually install the module, but just import that single file subprocess.py into my script? 
How do those modules that need setup.py make a difference then?

setup.py is used by distutils and can do loads of things, like building binary packages that include the interpreter (for different platforms), installing command line commands (cross-platform), ensuring dependencies are met, compiling C extension modules, etc.

[http://docs.python.org/library/distutils.html](http://docs.python.org/library/distutils.html)

For most libraries though setup.py will just copy the package into the lib folder of your installation.

Don't know if you could run it on your server, but you might like to look into virtualenv
[http://pypi.python.org/pypi/virtualenv](http://pypi.python.org/pypi/virtualenv)

That basically creates separate python installations for each application (so you can have different versions of libraries for different applications, and standard users can customise their installation fully)

You don't really need to know, but most standard library modules are actually just one python file (and possibly a second C file somewhere) - it just helps keep the standard library cleaner in svn.

---

### Post by ptitlouis on 2010-04-27
Sorry to bump this old thead but i don't really know where to look...

So here's the thing: i'm trying to install python 2.6 (as i've been told) on a Debian server, but the thing is that i have to install it in home folder (i don't have root acess..., shared seedbox...)

Is there somebody kindly enough to tell me how to do that (i need to  install python 2.6 (2.5 already installed) to be able to use pyWhatauto  which is a script that d/l torrents automatically to a seedbox. But  maybe this too complicated for my little mind...

Maybe this method ([http://docs.python.org/install/index.html#alternate-installation-the-home-scheme](http://docs.python.org/install/index.html#alternate-installation-the-home-scheme)) is the good one ?

Thanks for reading me.

And sorry for mistakes

---

### Post by lbthrice on 2012-05-15
for building and installing python packages in my home directory I include the --user flag in the build command.


```

python setup.py build

python setup.py install --user

```
this will install in user site-package
e.g. '/home/usrname/.local/lib/...'

you can see other options by invoking the help message
```

python setup.py install -h

```

happy coding!

---

### Post by markbl on 2012-05-15
You just replied to a post that is over 2 years old, and that post was replying to a post more than a year before his!

Anyhow, nowadays people use virtualenv to install and bundle python packages locally.

---

