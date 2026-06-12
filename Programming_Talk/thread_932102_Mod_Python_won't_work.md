---
title: "Mod_Python won't work"
date: 2008-09-28
forum: Programming Talk
---

### Post by jacensolo on 2008-09-28
I tried using [this]("http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch") guide to install mod_python. However, when I open it FireFox asks me to download the .py file.

PHP and HTML is working fine btw.

Any ideas?

---

### Post by LaRoza on 2008-09-28
Did you restart apache?

---

### Post by jacensolo on 2008-09-28
> **LaRoza said:**
> Did you restart apache?

Yup.

Now I have a new problem. I reinstalled both (to see if it was something in my apache config), but upon installing mod-python I get an error. Also, I deleted /etc/apache2 before the install.

```
The following NEW packages will be installed:
  libapache2-mod-python
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/125kB of archives.
After this operation, 549kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package libapache2-mod-python.
(Reading database ... 23123 files and directories currently installed.)
Unpacking libapache2-mod-python (from .../libapache2-mod-python_3.3.1-2build1_i386.deb) ...
Setting up libapache2-mod-python (3.3.1-2build1) ...
ln: creating symbolic link `/etc/apache2/mods-enabled/mod_python.load': No such file or directory
dpkg: error processing libapache2-mod-python (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-mod-python
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
All I get from that is something is missing. I tried to force (-f) it... no luck.

I'm off to bed. I'll check in later.

---

### Post by jacensolo on 2008-09-28
Any idea?

---

### Post by Mindzai on 2008-09-29
Silly question maybe but did you reinstall apache before doing this? It looks like it's having trouble finding your apache2 directory.

---

### Post by jacensolo on 2008-09-29
> **Mindzai said:**
> Silly question maybe but did you reinstall apache before doing this? It looks like it's having trouble finding your apache2 directory.

Yup. I'll try again just to make sure.

---

### Post by Mindzai on 2008-09-29
Might be worth double checking that apache is installing to /etc/apache2/ and not /etc/httpd/ or some other location:

```
whereis apache2
```

---

### Post by jacensolo on 2008-10-01
Got it to install. [http://ubuntuforums.org/showthread.php?t=843690](http://ubuntuforums.org/showthread.php?t=843690)

> **drs305 said:**
> Here's my next brainstorm, now that I understand it's a hung apt install. This may work if the entire aptitude system isn't locked. Make sure no other synaptic is running.

First, trying the usual options:


```

sudo killall aptitude
sudo killall synaptic
sudo aptitude purge **appname** && sudo aptitude remove **appname** && sudo aptitude clean && sudo aptitude autoclean
```



Now back to my original problem...

---

### Post by jacensolo on 2008-10-02
I take that back. It won't work now. I think I found out why.
```
 ls /etc/apache2
mods-available

```

I've tried reinstalling... didn't work.

I used sudo apt-get remove apache2 and sudo apt-get install apache2.

I also looked for it.
```
whereis apache2
apache2: /usr/sbin/apache2 /etc/apache2 /usr/lib/apache2 /usr/include/apache2 /usr/share/apache2 /usr/share/man/man8/apache2.8.gz

```

Now what?

Edit: Got it working witht the test successful page. Here's what I did: Reinstalled ubuntu with LAMP option from the cd(had home as a different partition) and didn't change the web directory (kept it as /var/www/). How do I mark this as solved?

---

