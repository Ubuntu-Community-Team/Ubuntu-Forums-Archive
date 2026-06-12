---
title: "Install GPA (GnuPG GUI)"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by aef54 on 2012-07-01
Hello peeps,

I'm new to ubuntu and I figured out it has GPG standard installed (sweet!). I kinda figured out how to use it through the terminal. However, I'd prefer to install the GPA graphic front end for it.

So I downloaded the file [gpa-0.9.1.tar.bz2]("ftp://ftp.gnupg.org/gcrypt/gpa//gpa-0.9.1.tar.bz2") here [ftp://ftp.gnupg.org/gcrypt/gpa//](ftp://ftp.gnupg.org/gcrypt/gpa//)

Then I clicked on it and pressed: extract here, and it extracted the files into the directory. 

I followed the instructions: I used *cd  *to get into the directory and then typed: *./configure*

Then I get a wall of text and after that, an error message:
*configure: error: GPA requires zlib ([http://gzip.org/zlib](http://gzip.org/zlib) or install Debian package zlib1g-dev)*

Can anybody tell me what's going on and how to proceed from here?

Kind regards,
aef
[]("ftp://ftp.gnupg.org/gcrypt/gpa//gpa-0.9.1.tar.bz2")

---

### Post by orange2k on 2012-07-01
I'm using enigmail to manage my private and public keys.
Or you can use Seahorse.

Enigmail is a nice little addon for Thunderbird, and Seahorse is in Ubuntu called Passwords and Keys...

---

### Post by aef54 on 2012-07-01
Thanks for the advice. Seahorse looks like a nice application and I'll look into it.

However I still don't understand what this zlib is and the wikipedia page is cryptic. Do you know what it does?

---

### Post by orange2k on 2012-07-01
> **aef54 said:**
> Thanks for the advice. Seahorse looks like a nice application and I'll look into it.

However I still don't understand what this zlib is and the wikipedia page is cryptic. Do you know what it does?

I have no idea...:(

---

### Post by critin on 2012-07-01
If you use Synaptic Package Manager and search for  GPG standard, it will install for you, including the dependencies.

---

### Post by aef54 on 2012-07-01
I installed synaptic package manager using the Ubuntu software center. Then I searched for GPG standard, but could not find anything.

However, I was able to find and install the package zlib1g-dev in Synaptic . Now I could run ./configure on that directory, but I got another error later on.

I'm not even sure if I'm running the script " configure"  is the right way to install the program. 

Installing such a simple program on linux is hard :mad:

---

### Post by testerz123456 on 2013-01-09
For anyone who is having this problem, I found a solution:

1) I downloaded the GPA source from the GNUPG site. [ftp://ftp.gnupg.org/gcrypt/gpa/gpa-0.9.3.tar.bz2](ftp://ftp.gnupg.org/gcrypt/gpa/gpa-0.9.3.tar.bz2)    .... extracted, cd'd, etc.

2) Run ./configure and it will tell you which libraries it's missing.  I needed three packages to compile this: gnupg2,  gpgme, libassuan, libgpg-error.

3) If you search the Synaptic Package manager, you can find these packages in their development forms. gnupg2, libgpgme11-dev, libassuan-dev, and libgpg-error-dev. Install these and any other libs that GPA needs.

4) Assuming you got everything installed from synaptic, you should be able to successfully ./configure and then make and finally sudo make install.

5) It might give you an error about x509 if you don't have the gpgsm package installed. You install it to get rid of that error, or you can run gpa with "-[SIZE=2][FONT=Verdana,Arial,Helvetica]-disable-x509", or you can edit the source as per this discussion ([http://www.gossamer-threads.com/lists/gnupg/gpa/55668](http://www.gossamer-threads.com/lists/gnupg/gpa/55668))[/FONT][/SIZE]

This worked for me. Good luck.

---

### Post by Cheesemill on 2013-01-09
Is there any reason you didn't install it directly from the repositories?
```
sudo apt-get install gpa
```

[http://packages.ubuntu.com/search?keywords=gpa&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=gpa&searchon=names&exact=1&suite=all&section=all)

---

