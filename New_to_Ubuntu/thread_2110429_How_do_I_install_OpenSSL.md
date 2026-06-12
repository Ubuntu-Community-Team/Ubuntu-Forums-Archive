---
title: "How do I install OpenSSL?"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by regency on 2013-01-30
I'm using Ubuntu 12.10, 64-bit, English and wish to install the latest version of OpenSSL.

Could someone show me how to download and install it please?

Thanks in advance.

P.S.: Prior to posting this request, I've searched the many forums on this site and couldn't find the answers.

---

### Post by codemaniac on 2013-01-30
Hi regency,

To install the OpenSSL binary toolkit, install the openssl package.
```
sudo apt-get install openssl
```

To install the OpenSSL general-purpose library, first determine the applicable version of the library available for your Ubuntu computer with the following command issued at a terminal prompt:

```
apt-cache search libssl | grep SSL
```

---

### Post by regency on 2013-01-30
> **codemaniac said:**
> To install the OpenSSL general-purpose library, first determine the applicable version of the library available for your Ubuntu computer

Sorry, I'm new to Linux and Ubuntu. I've Ubuntu 12.10, 64-bit, English installed.

Could you explain what you mean by "determine the applicable version of the library for your Ubuntu computer"?

Thanks in advance.

---

### Post by raja.genupula on 2013-01-30
you better read this [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

---

### Post by regency on 2013-01-30
I surfed to [http://www.openssl.org](http://www.openssl.org) and downloaded the latest version 1.0.1c. The name of the file is openssl-1.0.1c.tar.gz and is about 4.25MB in size.

How do I install in on Ubuntu 12.10, 64-bit, English please?

Or would it be better for me to download and install OpenSSL via "sudo apt-get install"?

As always thanks in advance for your help.

---

### Post by omeomi on 2013-01-30
It is easier to just use apt-get to install openssl (as you can read in raja's link).
```
sudo apt-get install openssl
```
and install the shared libraries as mentioned by codemaniac.

```
omeomi@omeomi:~$ apt-cache search libssl | grep SSL
libssl-dev - SSL development libraries, header files and documentation
libssl-doc - SSL development documentation documentation
libssl1.0.0 - SSL shared libraries  <-- this number is what we are after

```
then (if 1.0.0 is the number for you):
```
sudo apt-get install libssl1.0.0
```

You will also want to install 'ca-certificates' if that is not present already.

---

### Post by santosh83 on 2013-01-30
> **regency said:**
> Sorry, I'm new to Linux and Ubuntu. I've Ubuntu 12.10, 64-bit, English installed.

Could you explain what you mean by "determine the applicable version of the library for your Ubuntu computer"?

Thanks in advance.

Hi regency. Different Ubuntu versions (and in general different versions of any software) need or depend on different versions of various libraries and programs, including OpenSSL. That's just the way software development works.

The command apt-cache queries your system's package cache (which has a copy of the metadata of all the packages available from all the repository sources you've added), and in the command you'd been given, it finds out which version of the OpenSSL library has been installed, or can be installed, for your system. If you're not familar much with the command line, you can use Synaptic package manager to search for all OpenSSL packages, read their descriptions and install any that you want.

---

### Post by regency on 2013-01-30
> **raja.genupula said:**
> you better read this [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

Thanks friend for the link to the guide on how to install OpenSSL.

According to the guide, it says that I have to install the OpenSSL Development Library but it doesn't provide the sudo command. It just says "Install the following packages libssl-dev".

So from where and how do I download and install libssl-dev package?

Thanks in advance for your help.

---

### Post by audiomick on 2013-01-30
> **regency said:**
> 
Or would it be better for me to download and install OpenSSL via "sudo apt-get install"?

Yes, it would. That will install a version that is compatible with the OS, and, given that you are using the package manager to install it, the package management will know it is there and take care of updates for it.

If you install from a .tar file, this may not be the case unless the .tar contains a .deb file. Even then, it may want dependencies that give the rest of the OS a problem.

---

### Post by raja.genupula on 2013-01-30
> **regency said:**
> Thanks friend for the link to the guide on how to install OpenSSL.

According to the guide, it says that I have to install the OpenSSL Development Library but it doesn't provide the sudo command. It just says "Install the following packages libssl-dev".

So from where and how do I download and install libssl-dev package?

Thanks in advance for your help.

Hi , you can do it with simple command my friend.
```
sudo apt-get install libssl-dev
```

(or)

```
sudo aptitude install libssl-dev 
```

those two commands we can use for installation.

for more information on how to install a package in your Ubuntu PC you better read this [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by audiomick on 2013-01-30
> **regency said:**
> ... but it doesn't provide the sudo command. It just says "Install the following packages libssl-dev".

So from where and how do I download and install libssl-dev package?


That will be sudo apt-get again. The usage is
```
sudo apt-get <package name>
```

Look at 
```
man sudo
```

and 
```
man apt-get
```

for more information about the components of the command.

---

### Post by omeomi on 2013-01-30
> **regency said:**
> According to the guide, it says that I have to install the OpenSSL Development Library but it doesn't provide the sudo command. It just says "Install the following packages libssl-dev".

So from where and how do I download and install libssl-dev package?


You only need these libraries (development) if you are building software that needs openssl. If you just want to use openssl, you don't need those.

---

### Post by santosh83 on 2013-01-30
> **regency said:**
> Thanks friend for the link to the guide on how to install OpenSSL.

According to the guide, it says that I have to install the OpenSSL Development Library but it doesn't provide the sudo command. It just says "Install the following packages libssl-dev".

So from where and how do I download and install libssl-dev package?

Thanks in advance for your help.

It will be available (like the other OpenSSL modules) from the repository for your Ubuntu release. You can just do:

```
sudo apt-get install libssl-dev
```

or since you seem to unfamilar with packages and repositories you can launch Synaptic package manager (which should be in your system menu) and search for libssl and read the descriptions and install. Also browsing around Synaptic is great way to know what are all the possible packages you can install from the default repositories.

If you want the absolute latest version of OpenSSL then I guess you'll either have to take the [PPA]("https://help.launchpad.net/Packaging/PPA") route or compile from upstream source.

---

### Post by regency on 2013-01-30
Thank you guys for your help.

I shall try out the commands and feedback here if there are any problems.

---

