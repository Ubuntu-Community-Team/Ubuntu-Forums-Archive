---
title: "how to run tar.gz / tar.bz2 files"
date: 2008-06-21
forum: Philippine Team
---

### Post by ache109 on 2008-06-21
I have a hard time opening this kind of file types.. so I always look for .deb packages but sometimes... (hindi maiiwasan) o hindi sya supported ng ubuntu hardy heron??

---

### Post by adredz on 2008-06-21
what are you trying to install? if it's an app just follow this:

untar tarball(it will create a folder)
tar zxvf *.tar.gz

change ownership of the folder
sudo chown -R username:username <name of the folder>

move it to any folder you want it to be installed..(i use /opt)
sudo mv <folder> /opt

launch it
press Alt + F2
type the name of app and then click run

hope this helps :)

---

### Post by pendletone on 2008-06-21
Hi ache109, yung mga files na ganyan ang extension are compressed files.  It usually contains the source code for the program you're trying to install.  Kelangan mo muna i-uncompress and i-extract ang contents nito.  If the file ends with a .tar.gz or .tgz, you can extract its contents by typing in the terminal:
```
tar xfvz tarball_name
```
Pag na-extract mo na, tignan mo kung may README, INSTALL (or anything similar) na file, then follow its instructions on how to compile and install it.

---

### Post by king leoric on 2008-06-21
> **ache109 said:**
> I have a hard time opening this kind of file types.. so I always look for .deb packages but sometimes... (hindi maiiwasan) o hindi sya supported ng ubuntu hardy heron??

it is not that tar packages is not supported by hardy or ubuntu. Your can unpack naman by right-clicking on the mouse and choose extract here. Then you can read the read me file how to install. If you are looking for a .deb applications for you hardy

[www.getdeb.net](www.getdeb.net) will answer your needs (most likely)

I would recommended an ubuntu derivative which is Linuxmint. They have software portal which you can choose applications you want to install. and at the same time, debian packages is also supported cause it's main core is ubuntu...

try to visit [www.linuxmint.com](www.linuxmint.com) :)

---

### Post by wersdaluv on 2008-06-22
[LIST=1]
[*]Extract it
[*]cd to the folder where its contents are extracted (on the terminal, run cd <location of the file>)
[*]Run ./configure (it will work if there is a configure script)
[*]Run make
[*]Run sudo make install
[/LIST]

That's it. :)

More info here--> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by wersdaluv on 2008-06-22
Btw, whenever you're going to install an application,

try the repositories (sudo apt-get install <application name>)

If the application is not available there, look for a .deb.

If those things failed, that's the time when you install tarballs (tar.gz/tar.bz2)

---

### Post by lofarcom on 2012-01-10
did the above following commands. but when i come across the ./configure file. i get a message saying "permission denied". 
i did initially run the terminal in sudo su. but i still get this message. any idea why or what am doing wrong?

---

### Post by tech-hero on 2012-01-10
> **lofarcom said:**
> did the above following commands. but when i come across the ./configure file. i get a message saying "permission denied". 
i did initially run the terminal in sudo su. but i still get this message. any idea why or what am doing wrong?
Maybe the ./configure directory doesn't exist.

---

