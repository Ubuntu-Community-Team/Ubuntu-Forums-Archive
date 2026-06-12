---
title: "installing an app from a tarball - ida demo"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by BillsPC on 2013-01-30
I post this to the beginners section cause I'm sure I am missing something simple

I am trying to install an app from a tarball.  idademo63.tgz from hex-rays.com.  I've read all the rhetoric about stick to the software center and using deb files but for my project I need to use IDA a very specific title.

I've followed the following procudure from a recent build of ubuntu
   1 )  downloaded and extracted idademo63.tgz to ~/Downloads/idademo63
   2 )  sudo apt-get install build-essential
   3) ./configure
Response :  bash: ./configure: No such file or directory

   4) make
Response : make: *** No targets specified and no makefile found.  Stop.

The expanded contents are as follows :
bill@ubuntu:~/Downloads/idademo63$ ls
assistant  ids                libQtNetwork.so.4      procs
cfg        libclp.so          libQtSql.so.4          qidahelpcollection.qhc
dbgsrv     libida.so          libQtXmlPatterns.so.4  qidahelp.qch
ida.hlp    libQtCLucene.so.4  libQtXml.so.4          qwingraph
ida.int    libQtCore.so.4     license.txt            sig
idaq       libQtGui.so.4      loaders                til
idc        libQtHelp.so.4     plugins

Does anyone have any advice or should I take this up with the vendor of the software

---

### Post by zeljkojagust on 2013-01-30
I downloaded IDA Demo 6.3 for linux and extracted the tarball. As I can see there is nothing to configure, you just need to start idaq from your terminal.

So open your terminal, cd into a directory ~/Downloads/idademo63 and execute the following command:

./idaq

That's it.

---

### Post by BillsPC on 2013-01-31
I know I'm missing something really fundamental on this but it just does not work :confused:
Is there some kind of prior setup that needs to be done on a Ubuntu install ?

I re-downloaded the file and used the following commands
[INDENT]bill@ubuntu:~/Downloads$ tar -xvzf idademo63_linux.tgz
...
bill@ubuntu:~/Downloads$ cd idademo63
bill@ubuntu:~/Downloads/idademo63$ ./idaq
bash: ./idaq: No such file or directory

[/INDENT]I ls the directory and I see the idaq file 
[INDENT]bill@ubuntu:~/Downloads/idademo63$ ls -l
total 34345
-rwxrwxr-x 1 bill bill   995832 Jul 30  2012 assistant
drwxrwxr-x 2 bill bill     1024 Jul 30  2012 cfg
drwxrwxr-x 2 bill bill     1024 Jul 30  2012 dbgsrv
-rwxrwxr-x 1 bill bill   773066 Jul 20  2012 ida.hlp
-rwxrwxr-x 1 bill bill   860160 Jul 20  2012 ida.int
-rwxrwxr-x 1 bill bill  3337720 Jul 30  2012 idaq
drwxrwxr-x 2 bill bill     1024 Jul 30  2012 idc
drwxrwxr-x 2 bill bill     1024 Jul 30  2012 ids
-rwxrwxr-x 1 bill bill  1818760 Jul 30  2012 libclp.so
-rwxrwxr-x 1 bill bill  2409668 Jul 30  2012 libida.so
-rwxrwxr-x 1 bill bill   982412 Jul 30  2012 libQtCLucene.so.4
-rwxrwxr-x 1 bill bill  3254988 Jul 30  2012 libQtCore.so.4
-rwxrwxr-x 1 bill bill 12217468 Jul 30  2012 libQtGui.so.4
-rwxrwxr-x 1 bill bill   562116 Jul 30  2012 libQtHelp.so.4
-rwxrwxr-x 1 bill bill  1184012 Jul 30  2012 libQtNetwork.so.4
-rwxrwxr-x 1 bill bill   798060 Jul 30  2012 libQtSql.so.4
-rwxrwxr-x 1 bill bill  4340940 Jul 30  2012 libQtXmlPatterns.so.4
-rwxrwxr-x 1 bill bill   307232 Jul 30  2012 libQtXml.so.4
-rwxrwxr-x 1 bill bill     3782 Jul 17  2012 license.txt
drwxrwxr-x 2 bill bill     1024 Jul 30  2012 loaders
drwxrwxr-x 2 bill bill     1024 Jul 30  2012 plugins
drwxrwxr-x 2 bill bill     1024 Jul 30  2012 procs
-rwxrwxr-x 1 bill bill     8192 May 31  2012 qidahelpcollection.qhc
-rwxrwxr-x 1 bill bill   701440 Jun 12  2012 qidahelp.qch
-rwxrwxr-x 1 bill bill   435976 Jul 30  2012 qwingraph
drwxrwxr-x 3 bill bill     1024 Jul 30  2012 sig
drwxrwxr-x 4 bill bill     1024 Jul 30  2012 til

[/INDENT]

---

### Post by steeldriver on 2013-01-31
If it's a binary (i.e. not a script), is it the right architecture for your machine (32-bit versus 64-bit)? You can check with the 'file' command

```
bill@ubuntu:~/Downloads/idademo63$ file idaq
```

---

### Post by kanikilu on 2013-01-31
> **steeldriver said:**
> If it's a binary (i.e. not a script), is it the right architecture for your machine (32-bit versus 64-bit)? It is a binary: ```
$ file idaq
idaq: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), BuildID[sha1]=0xa9a251a21ed3b6db381cc5d4d26231289e06cddc, stripped
``` But I don't think it matters, it runs fine on my 64-bit OS:

```
$ uname -a
Linux ubuntu 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

OP: If you are indeed in the directory where you extracted the files, I'm not sure why the "dot slash" notation isn't working (./idaq), but what happens if you explicitly state the path:

```
$ /home/bill/Downloads/idademo63/idaq
``` Same thing?

---

### Post by kanikilu on 2013-01-31
Actually, now that I think about it, I have ia32-libs installed - maybe that's why it works on my 64-bit OS?

---

### Post by monkeybrain2012 on 2013-01-31
It works in 32 bit. Just go to the extracted folder and click the idaq file, that's it. :)

you can also cd into the directory from the terminal,
like
```
cd Desktop/idademo63
```
and then
```
./idaq
```

Don't know what it is for, but just downloaded and ran it to see if it works. :)

---

