---
title: "Is this the right way?"
date: 2006-05-24
forum: Programming Talk
---

### Post by meniscus on 2006-05-24
I just want to clarify how i install files

i use this method to install all .tar.gz files. 
Lets just say Example.tar.gz is what im installing-its on the desktop as EXAMPLE.tar.gz

In terminal i go

[COLOR="Red"]BUILD_DIR=/tmp/EXAMPLEbuild
INSTALL_DIR=[COLOR="Lime"]/usr/local/[/COLOR]EXAMPLE

mkdir -p $BUILD_DIR
cd $BUILD_DIR[/COLOR]

Paste the EXAMPLE.tar.gz into /tmp/EXAMPLEbuild

then 

[COLOR="Red"]tar zxf EXAMPLE.tar.gz
cd EXAMPLE
./configure --prefix=$INSTALL_DIR && make && make install[/COLOR]


Is this the correct method of doing it and if so why when after i install the files the 
/usr/local/ folder doesnt contain any of the files ive installed?

---

### Post by hod139 on 2006-05-24
Try
```
 ./configure --prefix=$INSTALL_DIR && make 
sudo make install
```

Note, I prefer to use checkinstall (have to apt-get install checkinstall first) and then the process would become:
```
 ./configure [any configure options here]
make 
sudo checkinstall
```
and answer a few questions where the defaults are usually fine.  This will create a deb file and install that, which makes copying and/or removal of the package easier.

---

