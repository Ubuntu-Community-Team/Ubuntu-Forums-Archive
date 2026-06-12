---
title: "trying to install tar.bz"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by MUK3SH on 2012-09-11
[12.04]
how to install tar.bz ?
I was trying install open office 

```
tar xvzf package.tar.gz 
```worked and unziped the package.

After that in terminal 
```
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~$ cd open
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~/open$ ./configure
bash: ./configure: No such file or directory
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~/open$ 


```
How to Over come from this ??
I also want to install tar.bz2 :(

This compiling  system is Not working at all for me. :(

---

### Post by elliotn on 2012-09-11
> **MUK3SH said:**
> [12.04]
how to install tar.bz ?
I was trying install open office 

```
tar xvzf package.tar.gz 
```worked and unziped the package.

After that in terminal 
```
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~$ cd open
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~/open$ ./configure
bash: ./configure: No such file or directory
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~/open$ 


```
How to Over come from this ??
I also want to install tar.bz2 :(

This compiling  system is Not working at all for me. :(

```
sudo apt-get install libre-office
```

or add open office repo

---

### Post by MUK3SH on 2012-09-11
> **elliotn said:**
> ```
sudo apt-get install libre-office
```

or add open office repo
Main problem is How to install tar.bz files.
I have to install some other programs Too, Eg - android SDK, and so On. so want to get better solution
 for installation of .tar.gz and tar.bz2

---

### Post by opensshd on 2012-09-11
Those are just compression methods. Depending on what is compressed will determine how you are going to install it.

The Android SDK has a great install tutorial:

[http://developer.android.com/sdk/installing/index.html](http://developer.android.com/sdk/installing/index.html)

---

### Post by Lars Noodén on 2012-09-11
> **MUK3SH said:**
> Main problem is How to install tar.bz files.
I have to install some other programs Too, Eg - android SDK, and so On. so want to get better solution
 for installation of .tar.gz and tar.bz2

I'd go with  elliotn's suggestion.  Using the package manager is always the best way to go if there is an existing package.  

About the tarballs, .tar.gz is extracted by [tar zxf *somefilename.tar.gz*](http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html), .tar.bz2 is extracted by [tar jxf *somefilename.tar.gz*](http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html).  It should result in a new directory with a name similar to the original file.  Inside that directory, you'll find a file named either README or INSTALL or both.  Read both of them carefully.

About installing from source, really the best way is to build your own package and then install that package.  That way you can also more easily update or remove the package as well as track dependencies.

[http://easierbuntu.blogspot.fi/2008/05/using-apt-get-to-compile-from-source.html](http://easierbuntu.blogspot.fi/2008/05/using-apt-get-to-compile-from-source.html)

Be aware that building libreoffice will take a very long time.  Depending on your machine it might take a day or two.

---

### Post by anewguy on 2012-09-11
After you untar the file, look for the folder it created and then look for a readme file.  Normally these types of packages will have an readme file that will tell you how to install it.  It may be simple, it may just involve make and make install.

---

