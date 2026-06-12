---
title: "Py being read as gzip"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by Andre Froes on 2013-05-03
Hello, I starting with ubuntu server now for the very first time. I interacted with ubuntu sometimes, but only with graphical interface. I'm trying to put a server up for mediawiki  in my server, but when it comes to install it, it is not recognizing the extension, and keep saying that it is not a gzip file. I'm with Ubuntu server 12.04, the latest. This is the tutorial i'm following:

[http://mwlib.readthedocs.org/en/latest/installation.html#ubuntu-install](http://mwlib.readthedocs.org/en/latest/installation.html#ubuntu-install)

the line that the exception show's up is this: pip install pyfribidi mwlib mwlib.rl
The pyfribidi is correctly installed, well, everything installs and configure smoothly until i reach the mwlib and mwlib.rl that are the server that i have to run. Here's what happens in the 1st huge line (that i believe that was installed correctly):
```

 apt-get install -y gcc g++ make python python-dev python-virtualenv   \
>   libjpeg-dev libz-dev libfreetype6-dev liblcms-dev                   \
>   libxml2-dev libxslt-dev                                             \
>   ocaml-nox git-core                                                  \
>   python-imaging python-lxml                                          \
>   texlive-latex-recommended ploticus dvipng imagemagick               \
>   pdftk
Lendo listas de pacotes... Pronto
Construindo Ã¡rvore de dependÃªncias
Lendo informaÃ§Ã£o de estado... Pronto
Note, a seleccionar 'zlib1g-dev' em vez de 'libz-dev'
Note, a seleccionar 'liblcms1-dev' em vez de 'liblcms-dev'
Note, a seleccionar 'libxslt1-dev' em vez de 'libxslt-dev'
dvipng jÃ¡ Ã© a versÃ£o mais nova.
g++ jÃ¡ Ã© a versÃ£o mais nova.
gcc jÃ¡ Ã© a versÃ£o mais nova.
git-core jÃ¡ Ã© a versÃ£o mais nova.
libjpeg-dev jÃ¡ Ã© a versÃ£o mais nova.
liblcms1-dev jÃ¡ Ã© a versÃ£o mais nova.
ocaml-nox jÃ¡ Ã© a versÃ£o mais nova.
python jÃ¡ Ã© a versÃ£o mais nova.
python-dev jÃ¡ Ã© a versÃ£o mais nova.
python-imaging jÃ¡ Ã© a versÃ£o mais nova.
python-lxml jÃ¡ Ã© a versÃ£o mais nova.
texlive-latex-recommended jÃ¡ Ã© a versÃ£o mais nova.
zlib1g-dev jÃ¡ Ã© a versÃ£o mais nova.
pdftk jÃ¡ Ã© a versÃ£o mais nova.
ploticus jÃ¡ Ã© a versÃ£o mais nova.
python-virtualenv jÃ¡ Ã© a versÃ£o mais nova.
imagemagick jÃ¡ Ã© a versÃ£o mais nova.
libfreetype6-dev jÃ¡ Ã© a versÃ£o mais nova.
libxml2-dev jÃ¡ Ã© a versÃ£o mais nova.
libxslt1-dev jÃ¡ Ã© a versÃ£o mais nova.
make jÃ¡ Ã© a versÃ£o mais nova.
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 2 nÃ£o atualizados.

```
mais nova = its the most recent

the following lines also runs without any problem, until i reach that line mwlib and mwlib.rl
This is the log:
```

  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/util.py", line 494, in unpack_file
    untar_file(filename, location)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/util.py", line 418, in untar_file
    tar = tarfile.open(filename, mode)
  File "/usr/lib/python2.7/tarfile.py", line 1678, in open
    return func(name, filemode, fileobj, **kwargs)
  File "/usr/lib/python2.7/tarfile.py", line 1729, in gzopen
    raise ReadError("not a gzip file")
ReadError: not a gzip file

```

I appreciate any tips :D
Thanks

---

### Post by Andre Froes on 2013-05-03
I found out how to get the full pop.log to see if it helps

----------------------------------------
```

 Running setup.py egg_info for package odfpy


Requirement already satisfied (use --upgrade to upgrade): distribute in /usr/lib/python2.7/dist-packages (from mwlib>=0.13.0->mwlib.rl)
Downloading/unpacking greenlet (from gevent->mwlib>=0.13.0->mwlib.rl)
  Running setup.py egg_info for package greenlet


Installing collected packages: gevent, odfpy, greenlet
  Running setup.py install for gevent
    building 'gevent.core' extension
    gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.7 -c gevent/core.c -o build/temp.linux-i686-2.7/gevent/core.o
    In file included from gevent/core.c:253:0:
    gevent/libevent.h:9:19: fatal error: event.h: No such file or directory
    compilation terminated.
    error: command 'gcc' failed with exit status 1
    Complete output from command /usr/bin/python -c "import setuptools;__file__='/home/andre/build/gevent/setup.py';exec(compile(open(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --single-version-externally-managed --record /tmp/pip-0vkRtX-record/install-record.txt:
    running install


running build


running build_py


running build_ext


building 'gevent.core' extension


gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.7 -c gevent/core.c -o build/temp.linux-i686-2.7/gevent/core.o


In file included from gevent/core.c:253:0:


gevent/libevent.h:9:19: fatal error: event.h: No such file or directory


compilation terminated.


error: command 'gcc' failed with exit status 1


----------------------------------------
Command /usr/bin/python -c "import setuptools;__file__='/home/andre/build/gevent/setup.py';exec(compile(open(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --single-version-externally-managed --record /tmp/pip-0vkRtX-record/install-record.txt failed with error code 1
Storing complete log in /root/.pip/pip.log
root@ubuntu:/home/andre# pip install mwlib
Requirement already satisfied (use --upgrade to upgrade): mwlib in /usr/local/lib/python2.7/dist-packages
Requirement already satisfied (use --upgrade to upgrade): pyparsing>=1.4.11,<1.6 in /usr/local/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): timelib>=0.2 in /usr/local/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): bottle>=0.10 in /usr/local/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): pyPdf>=1.12 in /usr/local/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): apipkg>=1.2 in /usr/local/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): qserve>=0.2.7 in /usr/local/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): lxml in /usr/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): py>=1.4 in /usr/local/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): sqlite3dbm in /usr/local/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): simplejson>=2.3 in /usr/lib/python2.7/dist-packages (from mwlib)
Requirement already satisfied (use --upgrade to upgrade): roman in /usr/local/lib/python2.7/dist-packages (from mwlib)
Downloading/unpacking gevent (from mwlib)
  Running setup.py egg_info for package gevent


Downloading/unpacking odfpy>=0.9,<0.10 (from mwlib)
  Running setup.py egg_info for package odfpy


Requirement already satisfied (use --upgrade to upgrade): distribute in /usr/lib/python2.7/dist-packages (from mwlib)
Downloading/unpacking greenlet (from gevent->mwlib)
  Running setup.py egg_info for package greenlet


Installing collected packages: gevent, odfpy, greenlet
  Running setup.py install for gevent
    building 'gevent.core' extension
    gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.7 -c gevent/core.c -o build/temp.linux-i686-2.7/gevent/core.o
    In file included from gevent/core.c:253:0:
    gevent/libevent.h:9:19: fatal error: event.h: No such file or directory
    compilation terminated.
    error: command 'gcc' failed with exit status 1
    Complete output from command /usr/bin/python -c "import setuptools;__file__='/home/andre/build/gevent/setup.py';exec(compile(open(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --single-version-externally-managed --record /tmp/pip-C6We3p-record/install-record.txt:
    running install


running build


running build_py


running build_ext


building 'gevent.core' extension


gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.7 -c gevent/core.c -o build/temp.linux-i686-2.7/gevent/core.o


In file included from gevent/core.c:253:0:


gevent/libevent.h:9:19: fatal error: event.h: No such file or directory


compilation terminated.


error: command 'gcc' failed with exit status 1


----------------------------------------
Command /usr/bin/python -c "import setuptools;__file__='/home/andre/build/gevent/setup.py';exec(compile(open(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --single-version-externally-managed --record /tmp/pip-C6We3p-record/install-record.txt failed with error code 1
Storing complete log in /root/.pip/pip.log
root@ubuntu:/home/andre# virtualenv --distribute --no-site-packages ~/pp
The --no-site-packages flag is deprecated; it is now the default behavior.
New python executable in /root/pp/bin/python
Installing distribute..............................................................................................................................................................................................done.
Installing pip...............done.
root@ubuntu:/home/andre# export PATH=~/pp/bin:$PATH
root@ubuntu:/home/andre# hash -r
root@ubuntu:/home/andre# export PIP_INDEX_URL=http://pypi.pediapress.com/simple/root@ubuntu:/home/andre# pip install pil
Requirement already satisfied (use --upgrade to upgrade): pil in /root/pp/lib/python2.7/site-packages
Cleaning up...
root@ubuntu:/home/andre# pip install mwlib
Downloading/unpacking mwlib
  Downloading mwlib-0.15.7.zip (1.8Mb): 1.8Mb downloaded
  Running setup.py egg_info for package mwlib


Downloading/unpacking pyparsing>=1.4.11,<1.6 (from mwlib)
  Downloading pyparsing-1.5.6.tar.gz (unknown size): 8.1Mb downloaded
Exception:
Traceback (most recent call last):
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/basecommand.py", line 104, in main
    status = self.run(options, args)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/commands/install.py", line 245, in run
    requirement_set.prepare_files(finder, force_root_egg_info=self.bundle, bundle=self.bundle)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/req.py", line 985, in prepare_files
    self.unpack_url(url, location, self.is_download)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/req.py", line 1109, in unpack_url
    retval = unpack_http_url(link, location, self.download_cache, self.download_dir)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/download.py", line 456, in unpack_http_url
    unpack_file(temp_location, location, content_type, link)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/util.py", line 494, in unpack_file
    untar_file(filename, location)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/util.py", line 418, in untar_file
    tar = tarfile.open(filename, mode)
  File "/usr/lib/python2.7/tarfile.py", line 1678, in open
    return func(name, filemode, fileobj, **kwargs)
  File "/usr/lib/python2.7/tarfile.py", line 1729, in gzopen
    raise ReadError("not a gzip file")
ReadError: not a gzip file


Storing complete log in /root/.pip/pip.log
root@ubuntu:/home/andre# pip install mwlib.rl
Downloading/unpacking mwlib.rl
  Downloading mwlib.rl-0.14.2.zip (4.1Mb): 4.1Mb downloaded
  Running setup.py egg_info for package mwlib.rl


Downloading/unpacking mwlib>=0.13.0 (from mwlib.rl)
  Running setup.py egg_info for package mwlib


Downloading/unpacking pygments>=1.0 (from mwlib.rl)
  Downloading Pygments-1.6.tar.gz (unknown size): 6.1Mb downloaded
Exception:
Traceback (most recent call last):
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/basecommand.py", line 104, in main
    status = self.run(options, args)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/commands/install.py", line 245, in run
    requirement_set.prepare_files(finder, force_root_egg_info=self.bundle, bundle=self.bundle)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/req.py", line 985, in prepare_files
    self.unpack_url(url, location, self.is_download)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/req.py", line 1109, in unpack_url
    retval = unpack_http_url(link, location, self.download_cache, self.download_dir)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/download.py", line 456, in unpack_http_url
    unpack_file(temp_location, location, content_type, link)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/util.py", line 494, in unpack_file
    untar_file(filename, location)
  File "/root/pp/local/lib/python2.7/site-packages/pip-1.1-py2.7.egg/pip/util.py", line 418, in untar_file
    tar = tarfile.open(filename, mode)
  File "/usr/lib/python2.7/tarfile.py", line 1678, in open
    return func(name, filemode, fileobj, **kwargs)
  File "/usr/lib/python2.7/tarfile.py", line 1729, in gzopen
    raise ReadError("not a gzip file")
ReadError: not a gzip file


Storing complete log in /root/.pip/pip.log
root@ubuntu:/home/andre# vim /root/.pip/pip.log
------------------------------------------------------------
/root/pp/bin/pip run on Fri May  3 11:19:47 2013
Downloading/unpacking mwlib.rl


  Getting page [http://pypi.pediapress.com/simple/mwlib.rl](http://pypi.pediapress.com/simple/mwlib.rl)
  URLs to search for versions for mwlib.rl:
  * [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)
  Getting page [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)
  Analyzing links from page [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)
    Found link [http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.8.tar.gz](http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.8.tar.gz) (from [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)), version: 0.12.8
    Found link [http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.9.zip](http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.9.zip) (from [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)), version: 0.12.9
    Found link [http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.10.zip](http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.10.zip) (from [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)), version: 0.12.10
    Found link [http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.11.zip](http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.11.zip) (from [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)), version: 0.12.11
    Found link [http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.12.zip](http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.12.12.zip) (from [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)), version: 0.12.12
    Found link [http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.14.0.zip](http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.14.0.zip) (from [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)), version: 0.14.0
    Found link [http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.14.1.zip](http://pypi.pediapress.com/packages/mirror/mwlib.rl-0.14.1.zip) (from [http://pypi.pediapress.com/simple/mwlib.rl/](http://pypi.pediapress.com/simple/mwlib.rl/)), version: 0.14.1

```

---

### Post by Andre Froes on 2013-05-03
Problem solved, I managed to solve it after several attempts of several sites, it is not a common exception

---

