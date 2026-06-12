---
title: "HowTo install g95 fortran compiler"
date: 2006-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by derjames on 2006-04-09
Hello there, 
I was looking for info about g95 fortran compiler in Ubuntu, however I found nothing,  you can install very quickly g77 using the instruction from the following wiki

[https://wiki.ubuntu.com/InstallingCompilers?highlight=%28compiler%29](https://wiki.ubuntu.com/InstallingCompilers?highlight=%28compiler%29)

however some people do prefer g95 and this is not included in the synaptic list, :-k  so if you plan to use it for whatever reason use the following instructions:

1. enter to g95 project page

[http://g95.sourceforge.net/](http://g95.sourceforge.net/)

2. download the binary (g95-x86-linux.tgz for the x86 platform In my caseor download the right binary for your system)

3. create a new directory which will hold the uncompressed file, in my case is (for example)

/etc/g95

use sudo if necessary

4. copy the downloaded file to this new location
5. untar the file using

```
tar -xzvf g95-x86-linux.tgz
```

6. The executable is located in

/etc/g95/g95-install/bin/i686-pc-linux-gnu-g95

7. Since this directory is not included in the PATH environment variables a link to this file have to be generated, there are to ways to do this (1) to use 'export' that location to the PATH using export or (2) create a symbolic link, the latter will be used.

8. A symbiolic link is a reference to an existing file from a new created file, you have to use the command 'ln'

the syntax is as follows

```
ln -s ExistingFileName NewLinkName
```

where -s indicates that a symbolic link will be created between the to files

for my case this would be

```
ln -s /etc/g95/g95-install/bin/i686-pc-linux-gnu-g95 /bin/g95
```

you can see that the new link is the file g95 located at /bin so when you call the compiler, the computer will look first at /bin then will locate g95 but g95 is just a link to the real executable file which is located at
 
/etc/g95/g95-install/bin/i686-pc-linux-gnu-g95

Why do we do this?, because  /bin  is already located in the PATH environment variables. Type

```
echo $PATH 
```

to confirm this

After this you will be able to run g95, use

```
g95 --help
```

for more info

Cheers 8)

---

### Post by Parkotron on 2006-04-09
Seems like a good howto, but generally, you shouldn't install software to /etc. /etc is reserved primarily for system wide configuration files. A more appropriate location would be either /opt or /usr/local.

For an explanation of the Debian (and Ubuntu) directory system, try [http://www.debian.org/doc/packaging-manuals/fhs/](http://www.debian.org/doc/packaging-manuals/fhs/) .

---

### Post by derjames on 2006-04-10
Amendment.
What Parkatron is saying is right, I don't know why I did write /etc/g95 (too much work I think), for my case the install directory was  /opt/g95 though you can select any other...

Cheers

---

