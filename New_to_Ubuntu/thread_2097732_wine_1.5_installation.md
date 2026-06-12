---
title: "wine 1.5 installation"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by Muk on 2012-12-24
i've tried multiple times installing wine 1.5 however i am always getting this package error message:
> 
chunheguo@ubuntu:~$ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.19-0ubuntu3) but it is not installable
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


i am following the instruction on this site: [http://www.noobslab.com/2012/04/install-wine-152-on-ubuntu.html](http://www.noobslab.com/2012/04/install-wine-152-on-ubuntu.html)

don't know what to do to install wine on my machine.

---

### Post by grahammechanical on 2012-12-24
There are two ways that I have used to install wine successfully.

1) Install from Ubuntu Software Centre. Use the versions available from there.

2) Follow the instructions from wine/hq itself.

[http://www.winehq.org/download/ubuntu]("http://www.winehq.org/download/ubuntu")

Note, the warning that wine 1.5 is still beta. You might be more successful with wine 1.4

Regards.

---

### Post by Muk on 2012-12-24
> **grahammechanical said:**
> There are two ways that I have used to install wine successfully.

1) Install from Ubuntu Software Centre. Use the versions available from there.

2) Follow the instructions from wine/hq itself.

[http://www.winehq.org/download/ubuntu]("http://www.winehq.org/download/ubuntu")

Note, the warning that wine 1.5 is still beta. You might be more successful with wine 1.4

Regards.

i am getting this error message when i try 1.4:

> 
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed



managed to install wine with playonlinux.

---

