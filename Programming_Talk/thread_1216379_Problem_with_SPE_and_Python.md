---
title: "Problem with SPE and Python"
date: 2009-07-18
forum: Programming Talk
---

### Post by stupiduser on 2009-07-18
Hi, newbie here

I hope i put this question in the right place

the thing is, i'm using ubuntu 8.04 and trying to install python 2.5.4 from the source using "make install", after that i can not open spe(Stani's Python Editor) anymore.
the console says :
[COLOR=Red]Error: SPE requires wxPython, which doesn't seem to be installed.
[COLOR=Black]_but i have already install wxpython_

can someone help me?
thank you
[/COLOR][/COLOR]

---

### Post by smartbei on 2009-07-18
Why are you installing from source? It is far easier to install from the repositories...
```

sudo aptitude install python2.5

```

And it probably wouldn't break anything.

---

### Post by stupiduser on 2009-07-18
> **smartbei said:**
> Why are you installing from source? It is far easier to install from the repositories...
```

sudo aptitude install python2.5

```And it probably wouldn't break anything.

just trying to get the newest python
really regret it now
wish i could turn back time

](*,):cry:
can someone help me?

---

### Post by unutbu on 2009-07-18
Please post the output:
```

ls -l /usr/local/bin/python*
ls -l /usr/bin/python*
which python
```

---

### Post by stupiduser on 2009-07-18
ls -l /usr/local/bin/python*
```
-rwxr-xr-x 2 root root 3699248 2009-07-18 18:34 /usr/local/bin/python
-rwxr-xr-x 2 root root 3699248 2009-07-18 18:34 /usr/local/bin/python2.5
-rwxr-xr-x 1 root root    1424 2009-07-18 18:35 /usr/local/bin/python2.5-config
lrwxrwxrwx 1 root root      16 2009-07-18 18:35 /usr/local/bin/python-config -> python2.5-config
```ls -l /usr/bin/python*
```
lrwxrwxrwx 1 root root       9 2009-01-30 19:29 /usr/bin/python -> python2.5
-rwxr-xr-x 1 root root 1163668 2008-08-01 01:42 /usr/bin/python2.5
-rwxr-xr-x 1 root root    1419 2008-08-01 01:41 /usr/bin/python2.5-config
lrwxrwxrwx 1 root root      16 2009-05-18 23:18 /usr/bin/python-config -> python2.5-config

```which python
```
/usr/local/bin/python
```thanks

---

### Post by unutbu on 2009-07-18
It looks like you still have the python deb package installed. The python from source appears to have been installed in /usr/local/bin. 

If the above is true, to remove python from source:

cd to the top level of the python source code -- the directory where you typed "make install".
Now type:
```

sudo make uninstall
```

If it works, /usr/local/bin/python will be removed, and SPE should work again.
If it does not work, please post the output of the above command.

---

### Post by stupiduser on 2009-07-18
it doesn't work
```
make: *** No rule to make target `uninstall'.  Stop.
```

---

### Post by unutbu on 2009-07-18
In the same directory where you typed
```

sudo make uninstall
```

type
```

pwd
ls -l
```
Please post the output.

---

### Post by stupiduser on 2009-07-18
pwd
```
/home/user/Python-2.5.4
```ls -l
```
total 10188
drwxr-xr-x  5 user user    4096 2009-07-18 17:28 build
-rw-r--r--  1 user user  368985 2009-07-18 16:31 config.log
-rwxr-xr-x  1 user user   41121 2009-07-18 16:31 config.status
-rwxr-xr-x  1 user user  625475 2008-12-13 21:13 configure
-rw-r--r--  1 user user   99329 2008-12-13 21:13 configure.in
drwxr-xr-x 22 user user    4096 2009-07-18 17:28 Demo
drwxr-xr-x 24 user user    4096 2009-07-18 17:28 Doc
drwxr-xr-x  2 user user    4096 2009-07-18 17:28 Grammar
drwxr-xr-x  2 user user    4096 2009-07-18 17:28 Include
-rwxr-xr-x  1 user user    7122 2003-06-14 13:58 install-sh
drwxr-xr-x 42 user user   12288 2009-07-18 17:28 Lib
-rw-r--r--  1 user user 5143528 2009-07-18 16:32 libpython2.5.a
-rw-r--r--  1 user user   13741 2008-02-21 18:53 LICENSE
drwxr-xr-x 11 user user    4096 2009-07-18 17:28 Mac
-rw-r--r--  1 user user   38660 2009-07-18 16:31 Makefile
-rw-r--r--  1 user user   35538 2009-07-18 16:31 Makefile.pre
-rw-r--r--  1 user user   35493 2008-09-22 07:22 Makefile.pre.in
drwxr-xr-x  4 user user    4096 2009-07-18 17:28 Misc
drwxr-xr-x  7 user user    4096 2009-07-18 17:28 Modules
drwxr-xr-x  3 user user    4096 2009-07-18 17:28 Objects
drwxr-xr-x  2 user user    4096 2009-07-18 17:28 Parser
drwxr-xr-x  8 user user    4096 2009-07-18 17:28 PC
drwxr-xr-x  2 user user    4096 2009-07-18 17:28 PCbuild
drwxr-xr-x 22 user user    4096 2009-07-18 17:28 PCbuild8
-rw-r--r--  1 user user   28582 2009-07-18 16:19 pyconfig.h
-rw-r--r--  1 user user   27218 2008-09-07 13:42 pyconfig.h.in
-rwxr-xr-x  1 user user 3699248 2009-07-18 16:32 python
drwxr-xr-x  2 user user    4096 2009-07-18 17:28 Python
-rw-r--r--  1 user user   55070 2008-12-23 20:18 README
drwxr-xr-x  5 user user    4096 2009-07-18 17:28 RISCOS
-rw-r--r--  1 user user   69115 2008-10-17 01:58 setup.py
drwxr-xr-x 19 user user    4096 2009-07-18 17:28 Tools

```

---

### Post by unutbu on 2009-07-18
Okay, it looks like the python source's Makefile does not contain a "uninstall" target.
(I downloaded [http://python.org/ftp/python/2.5.4/Python-2.5.4.tar.bz2](http://python.org/ftp/python/2.5.4/Python-2.5.4.tar.bz2) to see.)

Hm. This is new territory for me, so I hope others will pipe up if what I'm suggesting is wrong:

There is a program called checkinstall which can monitor an installation script like "make install" and create a deb package instead of directly installing the files.

So perhaps we can use checkinstall to create the deb package, and then use the deb package to uninstall the python in /usr/local:

```

sudo apt-get install checkinstall  # install the checkinstall package
cd /home/user/Python-2.5.4
sudo checkinstall -D --fstrans=no make install   # make the deb package

```
Answer the questions checkinstall asks. (Defaults should be fine).
You should end up with a deb package, called something like Python-2.5.4.deb.

So to uninstall python from source, now type
```

sudo dpkg -i Python-2.5.4.deb   # reinstall python to /usr/local
sudo dpkg -r Python-2.5.4       # remove python from /usr/local

```

---

### Post by stupiduser on 2009-07-18
Problem Solved yaayyyy \\:D/
thank you so much Unutbu

the code
```

sudo dpkg -i Python-2.5.4.deb   # reinstall python to /usr/local
sudo dpkg -r Python-2.5.4       # remove python from /usr/local

```are giving me errors
but after "checkinstall" create deb, "checkinstall" automaticaly install to my computer and overide the "python" in synaptic, then i do force downgrade and walla the "python" back to 2.5.2

thank you so much Unutbu
you event bother downloading the source code for me
is there any reputation point in ubuntuforum? i would like to klik the link 100 times for you
i really learn a lot today thx :D

---

### Post by unutbu on 2009-07-18
Yay! No problem. I'm really glad you found a way to make it work.
> 
is there any reputation point in ubuntuforum? i would like to klik the link 100 times for you i really learn a lot today thx

No, but your kind words have made my day. Thanks :)

---

