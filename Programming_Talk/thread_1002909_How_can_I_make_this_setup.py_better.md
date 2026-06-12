---
title: "How can I make this setup.py better?"
date: 2008-12-05
forum: Programming Talk
---

### Post by Flimm on 2008-12-05
Hello. I though I could improve upon the [Packaging Guide for Python Applications](https://wiki.ubuntu.com/PackagingGuide/Python) by including details on distutils and Launchpad's PPAs. I would love it if you have any suggestions to make.

I've been using this method to package my own program, [Epidermis](https://launchpad.net/epidermis), and it works fine for me, but several people have found issues, mentioned in this [bug report](https://bugs.launchpad.net/epidermis/+bug/303469).
I have a few hunches on what may be the problem, such as using python 2.4 instead of python 2.5, but I don't think think that's it. Which leads me to a question, does anyone know how to require a minimum version of Python in the setup.py script?

Anyway, here's the guide, it's the one I use myself, after all suggested improvements have been made, I think I'll post it to the wiki.

**_Preparing a python program for distribution on Ubuntu:_**

(Tested on python 2.5)

**First step, create a setup.py script using distutils.**
You can find more information on distutils here: [http://wiki.python.org/moin/DistUtils](http://wiki.python.org/moin/DistUtils)
Here's a sample setup.py, suitably commented:
[php]#!/usr/bin/env python
# 2008 copyright David D Lowe
# released under the GPL v2

from distutils.core import setup
import os, sys
import glob


def main():
    
    data_files = glob.glob("epidermis/data/*")  # data_files a list of strings
    # of the relative paths of all non-py files that should be included
    # ex: data_files is ['epidermis/data/creator.glade', 'epidermis/data/epidermis.glade', ...]
    
    setup( name="epidermis", # this should start with a lowercase letter 
        #so that it can be used as a debian package name later on
    version="0.2", # string, version of your program, not python version
    description="Epidermis theme manager for your GNOME desktop on Ubuntu", # short
    author="David D Lowe",
    author_email="daviddlowesemail@whatever.com",
    url="http://epidermis.tuxfamily.org", # home page for end-users
    license="GPL v2",
    packages=["epidermis", "epidermis.pigments"], # python packages, not debian packages
    data_files=[('share/epidermis/data/', data_files), 
        ('/usr/share/applications', ['epidermis/data/epidermis.desktop']),
        ('/usr/share/pixmaps', ['epidermis/data/epidermis.svg'])], # data_files is a list of tuples
            # each tuple contaning an installation path and a list of data files
    scripts=["runner/epidermis"], # the script that should be run and installed in /usr/bin
    classifiers=["Development Status :: 5 - Production/Stable", "Intended Audience :: End Users/Desktop", "License :: OSI Approved :: GNU General Public License (GPL)", "Operating System :: POSIX :: Linux"],
        # a bunch of optional tags, a list of classifiers can be found at http://pypi.python.org/pypi?:action=list_classifiers
    long_description="""Epidermis changes the appearance of your Ubuntu GNOME desktop in all its aspects in one click. Epidermis 'skins' change the appearance of your desktop wallpaper, Metacity windows border theme, your GTK controls theme, your icon theme, your mouse cursor theme, your GRUB bootsplash screen, your GDM login screen theme and your Usplash boot splash image.
Each of these customisations are downloaded in 'pigments' which are available from an Epidermis 'repository'.
Epidermis was written in python with pygtk.
Find more information at http://epidermis.tuxfamily.org and https://launchpad.net/epidermis/""")

if __name__ == "__main__":
    main()
[/php]
You also need to create a text file named MANIFEST.in which will specify all the data files that need to be included.Python files don't need to be mentioned, except for the runnable script. Here's a sample MANIFEST.in that goes with the sample setup.py
```
recursive-include epidermis/data *
include runner/epidermis
```
recursive-include allows wildcards, include expects file names. Both use relative paths.
Now compress a source tarball by running this command in setup.py's directory:
```
python setup.py sdist
```
This will create a directory called 'dist', with the source tarball named program-x.x.tar.gz . You could distribute this file and ask people to run setup.py install, however, we're going to start step two, which is packaging a .deb

**Creating a debian package:**
First, you'll need to rename program-x.x.tar.gz to program-x.x.orig.tar.gz, in my case, that's epidermis-0.2.orig.tar.gz . Then extract it
```
tar -xzf epidermis-0.2.orig.tar.gz
```
This will create a new directory epidermis-0.2
```
cd epidermis-0.2
```
**Now follow the instructions on [https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)** which was based on an open week IRC session.

I'm going to add the following comments:
to create a manpage, follow the guide at  [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/Man-Page.pdf](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/Man-Page.pdf)
Name your manpage program.1 and put in debian/
In order to get it included in the .deb package, make sure you add this line to rules:
```
DEB_INSTALL_MANPAGES_package = debian/program.1
```

Now in order to build the package, you can do
```
dpkg-buildpackage -us -uc
```
this will not sign the packages. The next one will though, if you have an OpenPGP key.
```
dpkg-buildpackage
```
And the following will compile a signed source package, ready to be built.
```
dpkg-buildpackage -S
```
If you haven't got a private OpenPGP key, you can follow this guide on launchpad: [https://help.launchpad.net/YourAccount/ImportingYourPGPKey](https://help.launchpad.net/YourAccount/ImportingYourPGPKey)
You should sign the packages with the same OpenPGP key that you use on Launchpad.
You may be wondering why we need to bother with source and binary packages, since the source code is always included in .py files anyway, and Python files are runnable regardless of computer artitecture. The reason is that Launchpad's PPA only accept source packages, even if they don't need to be compiled as is the case with Python. 

**PPA:**
Now to upload your package to your personal PPA. First, make sure that you've got SSH and OpenPGP keys imported in your Launchpad account. Then activate your PPA, you'll need to sign the Ubuntu Code of Conduct to do this.
Install dput:
```
sudo aptitude install dput
```
Edit your ~/.dput configuration file:
```
gedit ~/.dput
```
Put this in .dput:
```
[my-ppa]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~your-launchpad-id/ubuntu/
login = anonymous
allow_unsigned_uploads = 0
```
Build a signed source package:
```
dpkg-buildpackage -S
```
Upload it:
```
dput my-ppa program_x.x_source.changes
```
You should get an email with a success message, wait half an hour or so, and your package should be ready!

---

### Post by Flimm on 2009-03-09
Here's what I've learned since then:
There is no decent way of requiring a minimum python version in a distutils setup.py script. Instead, you should include the python version in the debian/control file, like this:
```
XS-Python-Version: >= 2.5
```
There's a bazaar plugin called [Bazaar Builddeb](https://launchpad.net/bzr-builddeb), here's the [user manual for Bazaar Builddeb](http://jameswestby.net/bzr/builddeb/user_manual/). It makes packaging a lot cleaner when using Bazaar.

---

### Post by forger on 2009-05-11
> 
There is no decent way of requiring a minimum python version in a distutils setup.py script. Instead, you should include the python version in the debian/control file, like this:

You can use the version as a string:
```
import sys
if sys.version < '2.5':
    sys.exit('ERROR: Sorry, python 2.5 is required for this application.')

```

---

### Post by Flimm on 2009-05-12
> **forger said:**
> You can use the version as a string:
```
import sys
if sys.version < '2.5':
    sys.exit('ERROR: Sorry, python 2.5 is required for this application.')

```
Wow, I never knew you could compare strings like that.

---

### Post by cdekter on 2009-05-12
Thanks so much for putting these instructions together from the various sources! I followed them and managed finally to get my own PPA going on Launchpad :)

---

