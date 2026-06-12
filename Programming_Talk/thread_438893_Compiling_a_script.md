---
title: "Compiling a script"
date: 2007-05-10
forum: Programming Talk
---

### Post by Robbyx on 2007-05-10
I have to compile some scripts so that my scanner can be accessed and run by sane.

According to the instructions I am to run ./configure --sysconfdir=/etc --prefix=/usr

When I put this into terminal it reports that

bash: ./configure: No such file or directory

I am supposed to change directories before running the command?

I would appreciate some advice as to how to get ./configure to work within Ubuntu.

Robin

---

### Post by xtacocorex on 2007-05-10
./configure is a shell script in a source directory that makes sure needed files/libraries are installed on the machine.  You do need to be in the source directory to use it, otherwise you'll need it's absolute path:

./configure
or
/home/user/soucedir/configure

I would recommend running configure in the source directory, because the make step needs to be run from that directory.

If you want to do the compile all in one command:
```
./configure --sysconfdir=/etc --prefix=/usr && make && sudo make install
```

---

### Post by Tomosaur on 2007-05-10
Yes, you need to either be in the directory where that script is, or type the full path to the script.

In the terminal, the pairing of the dot and forwards slash ("./") means 'this directory'. The tilde and slash ("~/") means 'the home directory'), and the solitary slash ("/") means 'the root of the filesystem'. A few examples:

```

gedit ./myfile.txt

```
Will open a file in the current directory.

```

gedit ~/myfile.txt

```
Will open a file in your home directory

```

gedit /myfile.txt

```
Will open a file in the root directory (although you shouldn't be storing files there!)

To change directories in the terminal, you just use the 'cd' command:
```

cd ./mydirectory

```

So all you have to do is change to the directory which holds the configure script, then run it using the command you initially tried to use.

---

### Post by Robbyx on 2007-05-10
Thanks for the replies.I can not find the directory with the config file in it so I am going to ask in the sane mail list as to its source.

Robin

---

### Post by xtacocorex on 2007-05-10
The source directory should be the one you extracted when you downloaded the tar.gz or tar.bz2 file.  configure should be one of the files right inside the top level folder of the source.

---

