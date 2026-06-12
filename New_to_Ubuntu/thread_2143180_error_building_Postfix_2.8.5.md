---
title: "error building Postfix 2.8.5"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by reinold on 2013-05-08
Hello
new to Ubuntu (now 11.10) and new to Postfix.
I'm trying to rebuild Postfix 2.8.5 starting from the apt source code.
I'm aware I can use the distribution package, but I need to modify the source code to meet my needs.
Before starting with modification, I'm trying to rebuild the code.

apt-get source postfix (2.8.5)
make
../../lib/libutil.a: undefined reference to `dict_pcre_open'
../../lib/libutil.a: undefined reference to `dict_tcp_open'

I'm unable to find a solution.
BTW: did a try with Ubuntu 12.04.2, Postfix 2.9.6, got the same error.

---

### Post by dino99 on 2013-05-08
you can download the deb package you need from : [https://launchpad.net/ubuntu/+source/postfix](https://launchpad.net/ubuntu/+source/postfix) , into an empty folder, then cd to that folder, and run : sudo dpkg -i *

but why does not using the version inside your installation ?

---

### Post by Cheesemill on 2013-05-08
Make sure you have all of the postfix build dependencies installed...
```
sudo apt-get build-dep postfix
```

---

### Post by sandyd on 2013-05-08
> **reinold said:**
> Hello
new to Ubuntu (now 11.10) and new to Postfix.
I'm trying to rebuild Postfix 2.8.5 starting from the apt source code.
I'm aware I can use the distribution package, but I need to modify the source code to meet my needs.
Before starting with modification, I'm trying to rebuild the code.

apt-get source postfix (2.8.5)
make
../../lib/libutil.a: undefined reference to `dict_pcre_open'
../../lib/libutil.a: undefined reference to `dict_tcp_open'

I'm unable to find a solution.
BTW: did a try with Ubuntu 12.04.2, Postfix 2.9.6, got the same error.
Have you tried with debuild?
Sometimes, there are patches included in the source package that need to be used in order to compile it properly.

---

### Post by reinold on 2013-05-09
Thank you sandyd, I found the yellow bricks.
I switched to 12.04.2, where, first of all, I was unable to make changes to sasl sql plugin.
Debuild is a quite long way. 
Can you please suggest me a tutorial (not the man pages) to debuild? 
I suppose there's a quick way to rebuld next packages for debugging.

---

### Post by sandyd on 2013-05-10
/me fishes around my brain for a second (its been a while since ive built from source...)
Note that the below has a *few* hacks which may not work so well for other releases

```

apt-get source postfix
sudo apt-get install devscripts
sudo apt-get build-dep postfix
cd postfix*
cd debian

```
Edit the files 

Now, generate a new GPG key with your name and email
```

nano changelog
```

Carefully add the following to the front of the file (exactly as it is, replacing my name and email with yours, debuild is fussy about spaces)
```

postfix (2.10.0-20) unstable; urgency=low

  * Repackaging

 -- Celene Barjaval <celene@nowhere.com>  Fri, 10 Mar 2013 06:26:29 -0800

```
Save the file by pressing control +x
```

cd ../
debuild -D
```
and you are done. You should have some deb files outside of the folder, and those are the ones that relate to postfix

Note that this package *will* upgrade itself when the version in the repositories is newer than the current version (currently set to 2.10.0-20)

If your bored enough, you can even run
```

debuild -S
```
and upload the resulting source files to a PPA so that they can be compiled on there instead of your computer

If it results in an error along the lines of missing files, recompress the folder into postfix_2.10.0.orig.tar.gz

---

