---
title: "Ubuntu on Odroid XU4"
date: 2018-02-10
forum: New to Ubuntu
---

### Post by odroid-xu4 on 2018-02-10
I am very new to Ubuntu so forgive me for the dumb questions. I am trying to install firefox and TeamViewer. No matter what I install, I get the following issues:

When I double click on the teamviewer .deb file, it tells me this error:

Error: Dependency is not satisfiable: Libc6 (>=2.17)

So I googled that and I say that I should run the following command:

sudo apt-get install libc6
When I do that, the following happens:

dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

So then I do that, and then this happens:

odroid@odroid:~$ sudo dpkg --configure -a
Setting up docker.io (1.13.1-0ubuntu1~16.04.2) ...
addgroup: The group `docker' already exists as a system group. Exiting.

And it just sits there forever. Never stops. I have let it run for hours. I can do other things, like open another window or terminal, but nothing is ever resolved. It seems like I can't install any programs correctly. I don't know if things are missing or corrupt or what. How do I fix this?
Can someone tell me what to do? I would like to get this up and going and try to replace my old Windows machines with a few of these nice Odroid machines, but if I can't get them to work, then I don't know. I am sure it is just me not knowing what to do.

I greatly appreciate any help. Thank you

---

### Post by oldos2er on 2018-02-10
You're running 16.04? Firefox and libc6 are both installed by default; and though I'm not a programmer I would imagine trying to install a different libc6 version will break your OS.

---

### Post by odroid-xu4 on 2018-02-10
Ok well why doesn't team viewer install then? And no Firefox was not installed by default. I didn't realize that was a different version of a library. I got Ubuntu already installed when I purchased the xu4. Maybe I should reinstall everything? If so where and how do I do that?

---

### Post by oldos2er on 2018-02-10
Need more information before we can determine why teamviewer won't install. Can you run the following commands and post their full output here? ```
cat /etc/apt/sources.list

ls -a /etc/apt/sources.list.d/
```

---

### Post by odroid-xu4 on 2018-02-10
Here is the output:

```
odroid@odroid:~$ sudo cat /etc/apt/sources.list
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main universe restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main universe restricted


deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-updates main universe restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-updates main universe restricted


deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-backports main restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-backports main restricted


deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security main restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security universe
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security multiverse


deb [http://apt.llvm.org/xenial/](http://apt.llvm.org/xenial/) llvm-toolchain-xenial-5.0 main
# deb-src [http://apt.llvm.org/xenial/](http://apt.llvm.org/xenial/) llvm-toolchain-xenial-5.0 main

ls -a /etc/apt/sources.list.d/
.   odroid.list   odroid.list.save                      saiarcot895-ubuntu-myppa-xenial.list.save
..  odroid.list~  saiarcot895-ubuntu-myppa-xenial.list  teamviewer.list.dpkg-new
```

---

### Post by MartyBuntu on 2018-02-12
Make sure you're downloading the 32bit version of Team Viewer. The 64bit version under Ubuntu and Ubuntu derivatives is unstable.

---

