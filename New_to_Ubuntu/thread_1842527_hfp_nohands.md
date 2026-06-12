---
title: "hfp nohands"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by frost1004 on 2011-09-11
cant install nohands hfp in ubuntu from tarz   *** No rule to make target `install'.  Stop. help

---

### Post by terrykiwi83 on 2011-09-11
Can you tell us what steps your taking to install the file (i.e. what commands your using)

---

### Post by sjmoquin on 2012-06-20
frost1004, the hfp nohands team has left the procedure for building as an exercise for the user.  Here is the content of "INSTALL":

```

sjm@Oy:~/trunk$ cat INSTALL 
Installing NoHands
------------------

After building, run 'make install'.

Binaries will be placed in the prefix path, which defaults to /usr/local, 
i.e. the Qt UI will be installed as /usr/local/bin/nohands.  To set the 
prefix, use 'configure --prefix=/XYZ'

```

We aren't told explicitly how to build.  Aside from this step, the rest of the documentation---and program itself---is quite excellent.

Here are the series of commands I issued inside /trunk to build:
```

./autogen.sh
./configure

```

Now we're back on track.  We issue the commands ```
make install
```.  After installation, we can issue ```
hfconsole
```.  

I hope these instructions are clear and effective.  Please post if they are not.

sjmoquin
Linux Oy 2.6.38-13-generic #55-Ubuntu SMP Tue Jan 24 14:27:59 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by bytie on 2013-03-23
I have managed to install hfp to 12.10 (quantal).

It also shall apply to pangolin, and other releases as well.

Firstly download libaudiofile0 package from debian packages ([http://packages.debian.org/search?keywords=libaudiofile0](http://packages.debian.org/search?keywords=libaudiofile0)), pkgs ([http://pkgs.org/download/libaudiofile0](http://pkgs.org/download/libaudiofile0)), etc regarding your architecture (such as i386, amd64, etc).

Then install it. I used gdebi for installing it. Of course you can use any other methods.

to install gdebi: 
[I]
sudo apt get install gdebi[/I] 

to install libaudiofile0, right click and select *Open With GDebi Package Installer*

Next add *ppa:sebastian-ruehl/nohands* via "Software Sources", then edit it (hit edit button) and change "Distribution" from *quantal* to *natty*. (or from *pangolin* to *natty*, if your distribution is pangolin, etc.)

And install hfconsole

*sudo apt-get install* *hfconsole*

That's all.

---

### Post by oldos2er on 2013-03-23
Old thread closed.

---

