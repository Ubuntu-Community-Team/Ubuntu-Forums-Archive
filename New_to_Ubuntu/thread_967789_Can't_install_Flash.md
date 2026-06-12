---
title: "Can't install Flash"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jollyr0ger on 2008-11-02
Hi to all. I've got the same problem, but I can't solve it!

I've installed
sudo apt-get install flashplugin-nonfree

or the adobe-flash but no one works!
I've used also the installation process into firefox and is the same thing...

Just trying with swfdec or gnash, start the flash plugin, else firefox echo the message that propose to install it.

What can I do?

Thanks

---

### Post by kansasnoob on 2008-11-02
> **jollyr0ger said:**
> Hi to all. I've got the same problem, but I can't solve it!

I've installed
sudo apt-get install flashplugin-nonfree

or the adobe-flash but no one works!
I've used also the installation process into firefox and is the same thing...

Just trying with swfdec or gnash, start the flash plugin, else firefox echo the message that propose to install it.

What can I do?

Thanks

Please start a new thread. Solved threads get little traffic.

Also include what version of Ubuntu you're using, 8.04? 8.10? Ubuntu, or Kubuntu, etc.

---

### Post by aysiu on 2008-11-02
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo updatedb
locate libflash
uname -m
cat /etc/lsb-release
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
``` Warning: the first command may take a few minutes to execute.

---

### Post by meganox on 2008-11-02
```
jezza@ubu-advent:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so

jezza@ubu-advent:~$ uname -m
i686

jezza@ubu-advent:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

jezza@ubu-advent:~$ dpkg -s flashpluin-nonfree
Package `flashpluin-nonfree' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

jezza@ubu-advent:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

jezza@ubu-advent:~$ dpkg -s swfdec-mozilla
Package `swfdec-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

jezza@ubu-advent:~$ cat /etc/apt/sources.list
# added by the release upgrader
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted

```

I can't find flashpluin-nonfree in the repos.

---

### Post by diablo75 on 2008-11-02
Try this:

Click Applications>Add/Remove

Search for "restricted" with the filter set to "All Available Applications" and check off the "Ubuntu Restricted Extra's" package.  Apply, wait for it to install (this will also install Java and some video/audio codecs, plus fonts).  See if it works and let us know.

---

### Post by aysiu on 2008-11-02
> **meganox said:**
> ```
jezza@ubu-advent:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so

jezza@ubu-advent:~$ uname -m
i686

jezza@ubu-advent:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

jezza@ubu-advent:~$ dpkg -s flashpluin-nonfree
Package `flashpluin-nonfree' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

jezza@ubu-advent:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

jezza@ubu-advent:~$ dpkg -s swfdec-mozilla
Package `swfdec-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

jezza@ubu-advent:~$ cat /etc/apt/sources.list
# added by the release upgrader
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted

```

I can't find flashpluin-nonfree in the repos.
Well, you don't have any Flash plugin installed, but you do have the proper repositories enabled, so you should be able to install it after you reload the repositories list: ```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

### Post by meganox on 2008-11-03
> **diablo75 said:**
> Try this:

Click Applications>Add/Remove

Search for "restricted" with the filter set to "All Available Applications" and check off the "Ubuntu Restricted Extra's" package.  Apply, wait for it to install (this will also install Java and some video/audio codecs, plus fonts).  See if it works and let us know.

Thanks, it worked, installed a lot of packages but I expect I would have installed most of them anyway.  I don't remember having to do this under Gutsy or Hardy, and like Aysiu says the restricted repo was already enabled.  Weird.

---

### Post by diablo75 on 2008-11-03
As useful as the terminal is, I love it more when I see problems solved without it.  Glad to hear you got things up and running.

---

### Post by meganox on 2008-11-03
I don't care if it's the terminal, GUI or Voodoo, as long as it works :)

---

### Post by Sef on 2008-11-03
> As useful as the terminal is, I love it more when I see problems solved without it.  Glad to hear you got things up and running.


Sometimes you just have to use the terminal.   It is good for figuring out why you are having a problem when something just crashes and does not tell you why.

---

