---
title: "How to check if a tool is installed on the desktop system?"
date: 2018-08-10
forum: New to Ubuntu
---

### Post by lindseygohan on 2018-08-10
I want to build and install Erlang/OTP-21. Erlang/OTP on Ubuntu Desktop from source code.

The documentation on [http://erlang.org/doc/installation_guide/INSTALL.html](http://erlang.org/doc/installation_guide/INSTALL.html) lists the required utilities to build from source code, ie: GNU unzip,  GNU make,  Perl 5, etc...

How can I find these utilities on my system using the command line?

I've tried:

    DPKG -l | grep GNU make
    DPKG -l | grep GNU unzip
    DPKG -l | grep -i perl
    etc...

But I don't have a conclusive answer. I feel that for example, "GNU make" should be on the system, but when I search as above nothing is returned.

Please note, I want to build from source code for the learning experience, I don't want to simply alt-get install erlang.

Thanks

---

### Post by mborl on 2018-08-10
Good way to do this would be: 

```
apt list --installed | grep [PACKAGE_NAME]
```

check out: ```
apt --help
``` for more details!

---

### Post by ajgreeny on 2018-08-10
First install the package **build-essential** which pulls in just about all you'll need to install packages from source code then try running those dpkg commands again but this time without using upper case and also omitting the GNU prefix of the utilities you're searching for and also removing the grep portion of the command, simplifying it to ```
dpkg -l make
```
Those instructions are a bit confusing and I'm not sure they are very useful for Ubuntu users who are new to Linux; they are more generic.
The apt list command shown above will also help you.

However, bear in mind that most Ubuntu users seldom if ever compile and install from source as it is so much easier to use the repos and install with **sudo apt install package-name**

---

### Post by lindseygohan on 2018-08-10
Thank you, success!

---

### Post by lindseygohan on 2018-08-10
Thank you!

---

