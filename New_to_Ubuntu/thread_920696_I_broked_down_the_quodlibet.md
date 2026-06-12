---
title: "I broked down the quodlibet"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by medya on 2008-09-15
the quod libet in the synaptic is 1.0 
they have released the 2.0 , I tried to install their newone  which is .PY files  I runned them on my desktop but after that my main quod libet 1.0 was stopped working .


I completly removed the quodlibet from the synaptic package manager and installed it again, and I got this :


> morgan@morgan-desktop:~$ sudo apt-get install quodlibet quodlibet-ext quodlibet-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
quodlibet is already the newest version.
Suggested packages:
  k3b lastfmsubmitd python-cddb python-musicbrainz
The following NEW packages will be installed:
  quodlibet-ext quodlibet-plugins
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 74.5kB of archives.
After this operation, 401kB of additional disk space will be used.
Get:1 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) hardy/universe quodlibet-plugins 20070625-1ubuntu2 [48.3kB]
Get:2 [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) hardy/universe quodlibet-ext 1.0-2ubuntu1 [26.2kB]
Fetched 74.5kB in 3s (19.4kB/s)           
(Reading database ... 130466 files and directories currently installed.)
U[COLOR="Red"]npacking quodlibet-plugins (from .../quodlibet-plugins_20070625-1ubuntu2_all.deb) ...
find: /usr/share/quodlibet: No such file or directory
dpkg: error processing /var/cache/apt/archives/quodlibet-plugins_20070625-1ubuntu2_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package quodlibet-ext.
Unpacking quodlibet-ext (from .../quodlibet-ext_1.0-2ubuntu1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/quodlibet-plugins_20070625-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
morgan@morgan-desktop:~$ 


I tried to delete the Apt cache  and I tried apt-get install -f 

> morgan@morgan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  quodlibet-plugins
Suggested packages:
  k3b lastfmsubmitd python-cddb python-musicbrainz
The following NEW packages will be installed:
  quodlibet-plugins
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/48.3kB of archives.
After this operation, 315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 130473 files and directories currently installed.)
Unpacking quodlibet-plugins (from .../quodlibet-plugins_20070625-1ubuntu2_all.deb) ...
find: /usr/share/quodlibet: No such file or directory
dpkg: error processing /var/cache/apt/archives/quodlibet-plugins_20070625-1ubuntu2_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/quodlibet-plugins_20070625-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



what should I do ? I want my quod libet back.

---

### Post by hugmenot on 2008-09-17
What happens if you do "sudo mkdir /usr/share/quodlibet" first and retry?

And be careful with manual installs. Every such install litters your system with stray files.

---

### Post by medya on 2008-09-17
I made missing directories by myself, and quodlibet gets installed without any error . (in syanptic package manager)
but now when I run it , it wont load .
it says
> morgan@morgan-desktop:~$ quodlibet
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 19, in <module>
    import config
ImportError: No module named config


I just want my Normal Quod Libet back :(

---

### Post by medya on 2008-09-17
hey guys I found out what is my problem I had manualy deleted the files in the /usr/share/quodlibet so synaptic package manager doesnt reinstall them . 

all i need is the Config files in the /usr/share/quodlibet .

can somebody plz give it to me (I belive there shoudl config.py or something like that)

---

### Post by medya on 2008-09-17
hey guys I fixed my problem
here is what I did,
I switched to Live CD and installed Quod Libet there and then copied all the files in /usr/share/quodlibet/  to my own /usr/share/quodlibet/

---

