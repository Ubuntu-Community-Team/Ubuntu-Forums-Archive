---
title: "R packages not compliling in Ubuntu"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by lbthrice on 2008-11-18
Hello all experts,

I am trying to install libcurl4-gnutls-dev
on my Hardy install 
because R (extremely popular stats app) does not compile some packages
namely the essential biomaRt package
without it
see
[http://www.nabble.com/RCurl-compilation-error-on-ubuntu-hardy-td19525423.html]("http://www.nabble.com/RCurl-compilation-error-on-ubuntu-hardy-td19525423.html")

It seems to me that the libcurl4-gnutls-dev package is not installing
due to a broken libldap2-dev package
I have attempted to install after 
```
sudo apt-get install -f
```
I have also attempted to install after manually installing the gutsy
version of libldap, which apparently worked for someone else (why not me ?????)
see: [http://backports.ubuntuforums.com/showthread.php?t=909953&page=2](http://backports.ubuntuforums.com/showthread.php?t=909953&page=2)
```
lbthrice@blahblah:~$ sudo apt-get install libcurl4-gnutls-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcurl4-gnutls-dev: Depends: libldap2-dev but it is not going to be installed
E: Broken packages

```

can anyone please suggest a workaround??

thank you kind Madams and Sirs

---

### Post by starcannon on 2008-11-18
You can get R directly from the default Ubuntu repositories:
```
sudo apt-get install r-recommended
```There are a bunch of other R related tools in the package manager as well, just search "r" or "statistics" in the Synaptic Package Manager to see them.

That said, if you prefer to build it yourself, you will need a few tools in addition to the ones that r specifically needs:
```
sudo apt-get build-essentials
```GL and happy statistical analysising :D

---

### Post by lbthrice on 2008-11-18
Thanks, I guess I will try to reinstall the R software and see if the biomaRt package will install after that.

---

### Post by lbthrice on 2008-11-18
OK, sorry about this...I fixed the issue...
I followed the instructions shown in the URLs I posted at the start of the thread.
I apologize for not correctly communicating the issue
...the problem was that curl-config is needed to compile the biomaRt package
...this was declared in the error output from R after I tried to comile the biomaRt package.
(I would post the exact output but now that I have fixed the issue I cannot reproduce the error)

so, curl-config is contained in the package:
libcurl4-gnutls-dev
Development files and documentation for libcurl (GnuTLS)

I could not install the libcurl4-gnutls-dev package due to a dependancy issue with:
libldap2-dev

I fixed it by downloading the gutsy version of libldap2-dev (I am running Hardy) from:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libldap2-dev]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libldap2-dev")
after installing this package I was able to install libcurl4-gnutls-dev
and subsequently biomaRt compiled correctly!

This was a good lesson in properly following directions and properly describing my issue...I failed at both...thank you for your patience all...ubuntu is a success because of fantastic people in this forum THANK YOU THANK YOU

---

