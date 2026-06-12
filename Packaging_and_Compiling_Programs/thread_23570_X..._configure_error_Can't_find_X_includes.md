---
title: "X... configure: error: Can't find X includes"
date: 2005-04-02
forum: Packaging and Compiling Programs
---

### Post by kruppe on 2005-04-02
I am trying to ./configure a package after installing all the recommended development tools, packages and gcc I get the folling error:

**checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!**

The package I'm trying to configure is synce-kde. I eventually installed it with apt-get but would like to know, how to compile from the sources. I'm new to the whole configure, make, make install environment.

Thanks. :wink:

---

### Post by mirtux on 2005-04-03
Hi,
   i think you have also to install these two packages:
[b]x-dev
libx11-dev

[/b]maybe just one of the two is enough for your needs but they are quite small packages.

Regards,
MC

---

### Post by Permafrost91 on 2006-01-08
I have both packages installed (x-dev and libx11-dev) as well as numerous other x11 dev packages and I still get the Can't find X includes error message when trying to compile a KDE theme. Any ideas about what I am missing (KDE dev files maybe?)

---

### Post by pfarmer on 2006-01-11
Hi,

Try installing kdebase-dev.



HTH

---

### Post by Permafrost91 on 2006-01-15
Yes, thank you, that did the trick ... I had realized that earlier but I forgot to edit the post. Thanks for the input though!

---

### Post by no1pointguard on 2006-01-30
i'm having same problem trying to install taskjuggler2.2.0 can anyone help need this to get organised. i'm a newbie so be gentle

---

### Post by snowsquirrel on 2006-02-28
cut and paste the output from ./configure, and I can probably help.

~S

---

### Post by uantuzri on 2006-04-23
I have the same problem:

```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

I used apt-get to install kdebase-dev, but some paqueges were not installed:
mesa-common-dev_6.5.0-0ubuntu 1_all.deb
libgl1-mesa-dev_6.5.0-0ubuntu 1_i386.deb
libglu1-mesa-dev_6.5.0-0ubunt u1_i386.deb

I think it is because I have compiz installed and it tries to get these paqueges from the "compiz repositories".

How can I fix this? Is this going to cause any problem with compiz?

Thanks

---

### Post by GarethMB on 2006-06-16
```
 sudo apt-get xlibs-dev 
```

---

### Post by uantuzri on 2006-06-17
Thankyou Gareth, it works!

---

### Post by GarethMB on 2006-06-18
No problems was having the same issue. ;)

---

### Post by BillyChow on 2007-07-12
mark.
:-)

---

### Post by Nebojsa on 2007-11-14
I am having a similar problem trying to install GPS software package called Navit. This is the error I get after I extract the files and execute the ./configure command:
...
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for X... no
Can not find X

Thanks for your help!!

Nebojsa

---

### Post by Rencipher on 2010-07-29
> **uantuzri said:**
> I have the same problem:

```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```I used apt-get to install kdebase-dev, but some paqueges were not installed:
mesa-common-dev_6.5.0-0ubuntu 1_all.deb
libgl1-mesa-dev_6.5.0-0ubuntu 1_i386.deb
libglu1-mesa-dev_6.5.0-0ubunt u1_i386.deb

I think it is because I have compiz installed and it tries to get these paqueges from the "compiz repositories".

How can I fix this? Is this going to cause any problem with compiz?

Thanks
Hi. Im trying to install kget and even though I've already installed the programs mentioned it still gives me the above error. What might be wrong?

---

### Post by Tikhon03 on 2010-09-10
Hi,
  I'm having this same problem with my attempts to install "Knights" in Lucid.  So far the suggestions have not solved the problem.  Are there any further suggestions?

---

### Post by Bachstelze on 2010-09-10
You need [font=monospace]xorg-dev[/font].

---

### Post by Tikhon03 on 2010-09-11
Thank you Bachstelze, that worked. :)

---

### Post by stevebu56 on 2010-09-13
You may want to take a look at ```
apt-get build-dep
```  It gets all the dependencies of a particular package.  This is really handy when building packages from source.

---

### Post by Bachstelze on 2010-09-13
> **stevebu56 said:**
> You may want to take a look at 'apt-get build-dep'.  It gets all the dependencies of a particular package.  This is really handy when building packages from source.

It gets all the dependencies of *the package in the Ubuntu repos*. If you are compiling from source and using another build configuration, you might need additional dependencies and/or find that build-dep installs some you don't need. I personally never use it, I like to track my dependencies myself.

---

### Post by santok on 2011-03-30
hi guys, i have same problem too. installaed NS-allinone-2.34 on my ubuntu 10.10.
here the last report from installation

checking for X11 header files
checking for X11 header files
can't find X includes
otcl-1.13 configuration failed! Exiting ...

---

