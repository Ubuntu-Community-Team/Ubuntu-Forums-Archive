---
title: "Difficulty upgrading to g++-4.7"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by anachronism2 on 2013-09-28
I installed this update with sudo apt-get install g++-4.7, followed by sudo apt-get update and upgrade. Everything went smoothly. My gcc version remained:

```

jjw@jjw-Satellite-C655D:~$ g++ --version
g++ (Ubuntu/Linaro 4.6.4-1ubuntu1~12.04) 4.6.4
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

I located my new gcc version:
```

jjw@jjw-Satellite-C655D:~$ which g++-4.7
/usr/bin/g++-4.7
```

Yet there is no g++-4.7 directory:

```
jjw@jjw-Satellite-C655D:~$ cd /usr/bin/g++-4.7
-bash: cd: /usr/bin/g++-4.7: Not a directory
```

Exploring the directory reveals that it is an application, not a directory. I read through ten different webpages on updating and five threads here, nothing covers what I need. If I recall, is there an alt-install method? A Google search doesn't seem to find it.

Using Ubuntu 12.04 Precise

---

### Post by steeldriver on 2013-09-28
If you want g++-4.7 to be the system default, you may need to set that using update-alternatives - start by see what versions / priorities it already knows about

```
update-alternatives --query g++
```

---

### Post by anachronism2 on 2013-09-28
> **steeldriver said:**
> If you want g++-4.7 to be the system default, you may need to set that using update-alternatives - start by see what versions / priorities it already knows about

```
update-alternatives --query g++
```

This returns an error, no alternatives are available.

Perhaps I have some bug with the apt manager. I just sudo apt-get installed the partimage package, and I cannot find it on my system with the Application Finder, even though which partimage and partimage --version both still work. I'm going to reboot and see how things look.

---

### Post by anachronism2 on 2013-09-28
```
jjw@jjw-Satellite-C655D:~$ which g++
/usr/bin/g++
jjw@jjw-Satellite-C655D:~$ mkdir /usr/bin/g++
mkdir: cannot create directory `/usr/bin/g++': File exists
jjw@jjw-Satellite-C655D:~$ cd /usr/bin/g++
-bash: cd: /usr/bin/g++: Not a directory
jjw@jjw-Satellite-C655D:~$ 

```

```
jjw@jjw-Satellite-C655D:~$ g++ --version
-bash: /usr/bin/g++: No such file or directory
jjw@jjw-Satellite-C655D:~$ sudo apt-get update-alternate g++-4.7
E: Invalid operation update-alternate
jjw@jjw-Satellite-C655D:~$ sudo apt-get install-alternate g++-4.7
E: Invalid operation install-alternate
jjw@jjw-Satellite-C655D:~$ which g++
jjw@jjw-Satellite-C655D:~$ 
```

I am well and truly stumped. What on earth happened to my poor g++?

---

### Post by steeldriver on 2013-09-28
You can't just throw words at the command line and expect it to do what you want - the syntax is something like

```
sudo update-alterna**tives** --install /usr/bin/g++ g++ /usr/bin/g++-4.7 50
```

If you decide you need to run the original g++-4.6 you can retroactively add that to the alternatives database e.g.  

```
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.6 30
```

and then you will be able to switch between them using

```
sudo update-alternatives --config g++
```

---

### Post by anachronism2 on 2013-09-29
> **steeldriver said:**
> You can't just throw words at the command line and expect it to do what you want - the syntax is something like

```
sudo update-alterna**tives** --install /usr/bin/g++ g++ /usr/bin/g++-4.7 50
```

If you decide you need to run the original g++-4.6 you can retroactively add that to the alternatives database e.g.  

```
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.6 30
```

and then you will be able to switch between them using

```
sudo update-alternatives --config g++
```

Why is it that typing "g++ --version" returns:

```
jjw@jjw-Satellite-C655D:~$ g++ --version
The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
jjw@jjw-Satellite-C655D:~$ 

```

Yet, I know they are already installed:

```
jjw@jjw-Satellite-C655D:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jjw@jjw-Satellite-C655D:~$ sudo apt-get install g++-4.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++-4.7 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jjw@jjw-Satellite-C655D:~$ 


```

When I try to find it on my computer, I get:

```
jjw@jjw-Satellite-C655D:~$ which g++-4.7
/usr/bin/g++-4.7
jjw@jjw-Satellite-C655D:~$ /usr/bin/g++-4.7
g++-4.7: fatal error: no input files
compilation terminated.
jjw@jjw-Satellite-C655D:~$ cd /usr/bin/g++4.7
-bash: cd: /usr/bin/g++4.7: No such file or directory
jjw@jjw-Satellite-C655D:~$ 

```

I'm curious why this program doesn't follow the usual paradigm of "sudo apt-get update; sudo apt-get upgrade", and instead requires additional input. Does it have to do with g++ being associated with the gcc package?

I'm sorry if this seems trivial. I honestly want to understand my computer better, how it operates.

---

### Post by steeldriver on 2013-09-29
I think it's because g++-4.7 is treated as a different program / package from g++-4.6 (otherwise the package itself would just be called 'g++' and the package version would just increment). This is a 'feature' provided so that developers who need to can run multiple versions and switch between them relatively easily.

When you install plain gcc or g++, it installs whichever version is considered 'current' for your system, and creates a symlink to that e.g. on my mint13 box:

```

$ apt-cache policy gcc
gcc:
  **Installed: 4:4.7.2-1**
  Candidate: 4:4.7.2-1
  Version table:
 *** 4:4.7.2-1 0
        500 http://mirror.metrocast.net/linuxmint-debian/latest/ testing/main amd64 Packages
        100 /var/lib/dpkg/status
$ 
$ ls -al /usr/bin/gcc
lrwxrwxrwx 1 root root 7 May 29 16:15** /usr/bin/gcc -> gcc-4.7**

```

It doesn't use the 'alternatives' system at that point

```

$ update-alternatives --query gcc
update-alternatives: error: no alternatives for gcc

```

and if you install a higher version (in my case that would be gcc-4.8) it does not automatically overwrite the symlink for what it regards as the 'current' version of the compiler, so like you my version still shows as the old one:

```

$ apt-cache policy gcc-4.8
gcc-4.8:
 ** Installed: 4.8.1-2**
  Candidate: 4.8.1-2
  Version table:
 *** 4.8.1-2 0
        500 http://mirror.metrocast.net/linuxmint-debian/latest/ testing/main amd64 Packages
        100 /var/lib/dpkg/status
$ 
$ ls -al /usr/bin/gcc
lrwxrwxrwx 1 root root 7 May 29 16:15** /usr/bin/gcc -> gcc-4.7**
$
**$ gcc --version**
**gcc (Debian 4.7.2-4) 4.7.2**
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

Now, you could (probably) just manually overwrite the symlink, but instead it's usually recommended to use the update-alternatives system (it's more generic and *may* do other stuff such as updating library links - although in this case I think it doesn't) e.g.

```

$ sudo update-alternatives --install /usr/bin/gcc gcc **/usr/bin/gcc-4.8** 50
update-alternatives: using /usr/bin/gcc-4.8 to provide /usr/bin/gcc (gcc) in auto mode
$ 
$ ls -l /usr/bin/gcc
lrwxrwxrwx 1 root root 21 Sep 29 16:20 **/usr/bin/gcc -> [COLOR=#0000ff]/etc/alternatives[/COLOR]/gcc**
$ 
[B]$ gcc --version
gcc (Debian 4.8.1-2) 4.8.1[/B]
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

This now **has** overwritten the symlink, and made gcc --version show the new version, but at this point update-alternatives doesn't know about the old version i.e.

```

$ update-alternatives --list gcc
/usr/bin/gcc-4.8

```

However if we need to go back to the previous version for some reason we can just do

```

$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/**gcc-4.7** 30

```

after which

```

$ sudo update-alternatives --config gcc
There are 2 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path              Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gcc-4.8   50        auto mode
  1            /usr/bin/gcc-4.7   30        manual mode
  2            /usr/bin/gcc-4.8   50        manual mode

Press enter to keep the current choice
[*], or type selection number: 

```

I don't know why 'g++ --version' is now broken for you. FYI /usr/bin/g++ is not a  directory, you can't cd into it. Maybe your attempt to 'mkdir' has  overwritten the symlink. If you are lucky, running update-alternatives will fix that for you.

Hope this helps

---

### Post by anachronism2 on 2013-09-29
> 
I don't know why 'g++ --version' is now broken for you. FYI /usr/bin/g++ is not a  directory, you can't cd into it. Maybe your attempt to 'mkdir' has  overwritten the symlink. If you are lucky, running update-alternatives will fix that for you.

Hope this helps

That did help, thank you.

```

jjw@jjw-Satellite-C655D:~$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.7 50
update-alternatives: using /usr/bin/gcc-4.7 to provide /usr/bin/gcc (gcc) in auto mode.
jjw@jjw-Satellite-C655D:~$ apt-cache policy gcc
gcc:
  Installed: 4:4.6.3-1ubuntu5
  Candidate: 4:4.6.3-1ubuntu5
  Version table:
 *** 4:4.6.3-1ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
jjw@jjw-Satellite-C655D:~$ update-alternatives --query gcc
Link: gcc
Status: auto
Best: /usr/bin/gcc-4.7
Value: /usr/bin/gcc-4.7

Alternative: /usr/bin/gcc-4.7
Priority: 50

Alternative: /usr/bin/gcc-4.8
Priority: 50
jjw@jjw-Satellite-C655D:~$ gcc --version
gcc (Ubuntu/Linaro 4.7.3-2ubuntu1~12.04) 4.7.3
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

Sadly, I don't seem to be getting in the groove of it:

```
~$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 30
$
$ update-alternatives --query gcc
Link: gcc
Status: auto
Best: /usr/bin/gcc-4.7
Value: /usr/bin/gcc-4.7

Alternative: /usr/bin/gcc-4.7
Priority: 50

Alternative: /usr/bin/gcc-4.8
Priority: 30
$ 
```

Do you know of any good websites that explain this concept?

---

### Post by steeldriver on 2013-09-29
Sorry I don't really understand what your issue is now - you probably should have set a higher priority value for 4.8 if that's the one you want to use automatically, however you should still be able to choose it by doing 

```
sudo update-alternatives --config gcc
```

and selecting the appropriate number from the menu.

I illustrated it with **gcc** (because I already had multiple g++ versions managed by update-alternatives) - you will need to go through the same steps for g++ since that was your original question

---

