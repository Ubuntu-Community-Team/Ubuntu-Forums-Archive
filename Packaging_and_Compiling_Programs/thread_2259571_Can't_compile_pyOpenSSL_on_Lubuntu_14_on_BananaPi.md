---
title: "Can't compile pyOpenSSL on Lubuntu 14 on BananaPi"
date: 2015-01-05
forum: Packaging and Compiling Programs
---

### Post by juliushibert63 on 2015-01-05
[FONT=arial]I'm trying to get pyOpenSSL to compile so that I can use SSL self signed certificates on a couple of python programmes I have running.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I'd check if there was a precompile binary via apt for pyOpenSSL but there doesn't appear to be one so resorted to downloading and compiling my own with the following commands.[/FONT]

[FONT=arial]However I'm getting stuck at the following error and can't seem to find a solution to get the app to compile. If I remember correctly I downloaded the source from the [Launchpad PPA site]("https://launchpad.net/ubuntu/+source/pyopenssl").

[/FONT]```
$ cd pyOpenSSL-0.14[FONT=arial]
[FONT=Verdana]$ sudo python setup.py install[/FONT][/FONT]
``````

running install
running bdist_egg
running egg_info
writing requirements to pyOpenSSL.egg-info/requires.txt
writing pyOpenSSL.egg-info/PKG-INFO
writing top-level names to pyOpenSSL.egg-info/top_level.txt
writing dependency_links to pyOpenSSL.egg-info/dependency_links.txt
reading manifest file 'pyOpenSSL.egg-info/SOURCES.txt'
reading manifest template 'MANIFEST.in'
warning: no previously-included files matching '*.pyc' found anywhere in distribution
no previously-included directories found matching 'doc/_build'
writing manifest file 'pyOpenSSL.egg-info/SOURCES.txt'
installing library code to build/bdist.linux-armv7l/egg
running install_lib
running build_py
creating build/bdist.linux-armv7l/egg
creating build/bdist.linux-armv7l/egg/OpenSSL
copying build/lib.linux-armv7l-2.7/OpenSSL/__init__.py -> build/bdist.linux-armv7l/egg/OpenSSL
copying build/lib.linux-armv7l-2.7/OpenSSL/_util.py -> build/bdist.linux-armv7l/egg/OpenSSL
copying build/lib.linux-armv7l-2.7/OpenSSL/tsafe.py -> build/bdist.linux-armv7l/egg/OpenSSL
creating build/bdist.linux-armv7l/egg/OpenSSL/test
copying build/lib.linux-armv7l-2.7/OpenSSL/test/__init__.py -> build/bdist.linux-armv7l/egg/OpenSSL/test
copying build/lib.linux-armv7l-2.7/OpenSSL/test/util.py -> build/bdist.linux-armv7l/egg/OpenSSL/test
copying build/lib.linux-armv7l-2.7/OpenSSL/test/test_crypto.py -> build/bdist.linux-armv7l/egg/OpenSSL/test
copying build/lib.linux-armv7l-2.7/OpenSSL/test/test_ssl.py -> build/bdist.linux-armv7l/egg/OpenSSL/test
copying build/lib.linux-armv7l-2.7/OpenSSL/test/test_rand.py -> build/bdist.linux-armv7l/egg/OpenSSL/test
copying build/lib.linux-armv7l-2.7/OpenSSL/crypto.py -> build/bdist.linux-armv7l/egg/OpenSSL
copying build/lib.linux-armv7l-2.7/OpenSSL/rand.py -> build/bdist.linux-armv7l/egg/OpenSSL
copying build/lib.linux-armv7l-2.7/OpenSSL/SSL.py -> build/bdist.linux-armv7l/egg/OpenSSL
copying build/lib.linux-armv7l-2.7/OpenSSL/version.py -> build/bdist.linux-armv7l/egg/OpenSSL
^Cinterrupted
enwhat@media-pi:~/Downloads/pyOpenSSL-0.14$ sudo python setup.py install
running install
running bdist_egg
running egg_info
writing requirements to pyOpenSSL.egg-info/requires.txt
writing pyOpenSSL.egg-info/PKG-INFO
writing top-level names to pyOpenSSL.egg-info/top_level.txt
writing dependency_links to pyOpenSSL.egg-info/dependency_links.txt
reading manifest file 'pyOpenSSL.egg-info/SOURCES.txt'
reading manifest template 'MANIFEST.in'
warning: no previously-included files matching '*.pyc' found anywhere in distribution
no previously-included directories found matching 'doc/_build'
writing manifest file 'pyOpenSSL.egg-info/SOURCES.txt'
installing library code to build/bdist.linux-armv7l/egg
running install_lib
running build_py
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/_util.py to _util.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/tsafe.py to tsafe.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/test/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/test/util.py to util.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/test/test_crypto.py to test_crypto.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/test/test_ssl.py to test_ssl.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/test/test_rand.py to test_rand.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/crypto.py to crypto.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/rand.py to rand.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/SSL.py to SSL.pyc
byte-compiling build/bdist.linux-armv7l/egg/OpenSSL/version.py to version.pyc
creating build/bdist.linux-armv7l/egg/EGG-INFO
copying pyOpenSSL.egg-info/PKG-INFO -> build/bdist.linux-armv7l/egg/EGG-INFO
copying pyOpenSSL.egg-info/SOURCES.txt -> build/bdist.linux-armv7l/egg/EGG-INFO
copying pyOpenSSL.egg-info/dependency_links.txt -> build/bdist.linux-armv7l/egg/EGG-INFO
copying pyOpenSSL.egg-info/requires.txt -> build/bdist.linux-armv7l/egg/EGG-INFO
copying pyOpenSSL.egg-info/top_level.txt -> build/bdist.linux-armv7l/egg/EGG-INFO
zip_safe flag not set; analyzing archive contents...
creating 'dist/pyOpenSSL-0.14-py2.7.egg' and adding 'build/bdist.linux-armv7l/egg' to it
removing 'build/bdist.linux-armv7l/egg' (and everything under it)
Processing pyOpenSSL-0.14-py2.7.egg
Removing /usr/local/lib/python2.7/dist-packages/pyOpenSSL-0.14-py2.7.egg
Copying pyOpenSSL-0.14-py2.7.egg to /usr/local/lib/python2.7/dist-packages
pyOpenSSL 0.14 is already the active version in easy-install.pth


Installed /usr/local/lib/python2.7/dist-packages/pyOpenSSL-0.14-py2.7.egg
Processing dependencies for pyOpenSSL==0.14
Searching for cryptography>=0.2.1
Reading https://pypi.python.org/simple/cryptography/
Best match: cryptography 0.7.1
Downloading https://pypi.python.org/packages/source/c/cryptography/cryptography-0.7.1.tar.gz#md5=4a933b1e01b604cee0e22ce1f9fe7c81
Processing cryptography-0.7.1.tar.gz
Writing /tmp/easy_install-2XdYx9/cryptography-0.7.1/setup.cfg
Running cryptography-0.7.1/setup.py -q bdist_egg --dist-dir /tmp/easy_install-2XdYx9/cryptography-0.7.1/egg-dist-tmp-erQ96x
Searching for pyasn1
Reading https://pypi.python.org/simple/pyasn1/
Best match: pyasn1 0.1.7
Downloading https://pypi.python.org/packages/2.7/p/pyasn1/pyasn1-0.1.7-py2.7.egg#md5=15f079cabee01402bf86ca8b83356469
Processing pyasn1-0.1.7-py2.7.egg
Moving pyasn1-0.1.7-py2.7.egg to /tmp/easy_install-2XdYx9/cryptography-0.7.1


Installed /tmp/easy_install-2XdYx9/cryptography-0.7.1/pyasn1-0.1.7-py2.7.egg
Searching for enum34
Reading https://pypi.python.org/simple/enum34/
Best match: enum34 1.0.4
Downloading https://pypi.python.org/packages/source/e/enum34/enum34-1.0.4.zip#md5=9843e97527f3126c851df7afeb0524b3
Processing enum34-1.0.4.zip
Writing /tmp/easy_install-2XdYx9/cryptography-0.7.1/temp/easy_install-HoF6hJ/enum34-1.0.4/setup.cfg
Running enum34-1.0.4/setup.py -q bdist_egg --dist-dir /tmp/easy_install-2XdYx9/cryptography-0.7.1/temp/easy_install-HoF6hJ/enum34-1.0.4/egg-dist-tmp-smXwEN
zip_safe flag not set; analyzing archive contents...


Installed /tmp/easy_install-2XdYx9/cryptography-0.7.1/enum34-1.0.4-py2.7.egg
Searching for cffi>=0.8
Reading https://pypi.python.org/simple/cffi/
Best match: cffi 0.8.6
Downloading https://pypi.python.org/packages/source/c/cffi/cffi-0.8.6.tar.gz#md5=474b5a68299a6f05009171de1dc91be6
Processing cffi-0.8.6.tar.gz
Writing /tmp/easy_install-2XdYx9/cryptography-0.7.1/temp/easy_install-X_XIhv/cffi-0.8.6/setup.cfg
Running cffi-0.8.6/setup.py -q bdist_egg --dist-dir /tmp/easy_install-2XdYx9/cryptography-0.7.1/temp/easy_install-X_XIhv/cffi-0.8.6/egg-dist-tmp-DhqBmd
compiling '_configtest.c':
__thread int some_threadlocal_variable_42;


arm-linux-gnueabihf-gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -c _configtest.c -o _configtest.o
success!
removing: _configtest.c _configtest.o


Installed /tmp/easy_install-2XdYx9/cryptography-0.7.1/cffi-0.8.6-py2.7-linux-armv7l.egg
Searching for pycparser
Reading https://pypi.python.org/simple/pycparser/
Best match: pycparser 2.10
Downloading https://pypi.python.org/packages/source/p/pycparser/pycparser-2.10.tar.gz#md5=d87aed98c8a9f386aa56d365fe4d515f
Processing pycparser-2.10.tar.gz
Writing /tmp/easy_install-2XdYx9/cryptography-0.7.1/temp/easy_install-ObxEaM/pycparser-2.10/setup.cfg
Running pycparser-2.10/setup.py -q bdist_egg --dist-dir /tmp/easy_install-2XdYx9/cryptography-0.7.1/temp/easy_install-ObxEaM/pycparser-2.10/egg-dist-tmp-VhNaog
zip_safe flag not set; analyzing archive contents...


Installed /tmp/easy_install-2XdYx9/cryptography-0.7.1/pycparser-2.10-py2.7.egg
no previously-included directories found matching 'docs/_build'
[FONT=arial][FONT=Verdana]warning: no previously-included files matching '*' found under directory 'vectors'
[/FONT][/FONT]
```[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Can anyone help?[/FONT]

---

