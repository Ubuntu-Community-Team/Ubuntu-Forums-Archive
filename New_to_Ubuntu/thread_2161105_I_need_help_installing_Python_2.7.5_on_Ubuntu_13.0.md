---
title: "I need help installing Python 2.7.5 on Ubuntu 13.04"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by iMatheusMachado on 2013-07-09
Do I have to do the command $ sudo apt-get installed python?
For some reason, I have connection issues and Ubuntu forums are the only chance of getting help.
I need to know how I can install python, and run a python program using the terminal. :o

---

### Post by newb85 on 2013-07-09
Why do you need 2.7.5 specifically?  There are other versions in the repositories that would be easy to install with apt-get.  I believe you would have to download and compile the source code for 2.7.5.

---

### Post by patty92 on 2013-07-09
I just had a quick chat with google xD Maybe this can help you:

[http://askubuntu.com/questions/101591/how-do-i-install-python-2-7-2-on-ubuntu](http://askubuntu.com/questions/101591/how-do-i-install-python-2-7-2-on-ubuntu)

Regards,

Patty

---

### Post by oldfred on 2013-07-09
I am in 12.04 but you should have both python 2.7 and python3 installed.

```
fred@fred-Precise:~$ python3
Python 3.2.3 (default, Jul  5 2013, 08:29:02) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()
fred@fred-Precise:~$ python
Python 2.7.3 (default, Jul  5 2013, 08:39:51) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> exit
Use exit() or Ctrl-D (i.e. EOF) to exit

```

---

### Post by newb85 on 2013-07-09
On 13.04 2.7.4 is installed by default.

---

### Post by edb66083 on 2013-07-09
Yeah, you should have python installed by default with Ubuntu. Why do you need 2.7.5 rather than 2.7.4? Is there really a big difference between them? To start python, just type 'python' in the command line.

---

### Post by jgooch on 2013-09-02
> **edb66083 said:**
> Yeah, you should have python installed by default with Ubuntu. Why do you need 2.7.5 rather than 2.7.4? Is there really a big difference between them? To start python, just type 'python' in the command line.
There are applications the reference module properties that were added after 2.7.3. I ran into this today when I tried to install the sabnzbd app using apt-get . the installation failed with error "cannot import MAXREPEAT from _sre" . The module sre is a core module, but they added the MAXREPEAT "property" in 2.7.4. 

There may be applications that depend on 2.7.5 as well, though I haven't run into any yet.

---

