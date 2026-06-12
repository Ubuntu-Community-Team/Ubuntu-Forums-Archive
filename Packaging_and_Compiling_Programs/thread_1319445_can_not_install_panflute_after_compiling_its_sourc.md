---
title: "can not install panflute after compiling its source code"
date: 2009-11-08
forum: Packaging and Compiling Programs
---

### Post by legolas_w on 2009-11-08
Hi
Thank you for reading my post.
I installed panflute 0.5.3 and then I tried to install the newer version from the source code. To do this I fetched the Panflute source code from its repository using following bzr command:

```
bzr branch lp:panflute
```

Then I compiled and tried to install it using the following commands:

```

./configure
sudo make install


```
both command executed without reporting any error but the panflute is still showing version 0.5.3 instead of 0.6. 

I am trying to install version 0.6 to get songbird support. Please let me know what I did wrong so I can install the 0.6 with Songbird support.

Thanks

---

### Post by legolas_w on 2009-11-09
Any comment?

Thanks

---

### Post by SevenMachines on 2009-11-09
Am I right in that you have both a panflute package installed? (0.5.3), which will be installed in /usr/bin i'm guessing. and a local build (0.6) installed. a default ./configure then make install on the bzr source is most likely in /usr/local/bin. If you have things set like that then try running panflute from the command line with the full path to the binary in local and see if that works

---

### Post by legolas_w on 2009-11-09
Wow.

Thanks, I finally did it.

I copied all panflute related files from usr/local for same places in usr/ and now I have the latest panflute :D

Though I may not be able to do it again :D because I forget the sequence of what i did.

Is there some place in the build files to edit ad make sure that build files copy the result in correct location? (/usr/lib instead of /usr/local/lib ....)

Thanks again.

---

### Post by SevenMachines on 2009-11-09
copying files from local over the top of an existing package install isnt really a good idea, you can set the install prefix to /usr for a manual build using
$./configure --prefix=/usr
but to be honest /usr/local is usually the place you will want to put manual builds, they'll run fine from there but since you also had a package installed with the same binary you'd just need to specify the command to run directly, ie, 
$/usr/local/bin/panflute

---

### Post by SevenMachines on 2009-11-09
This is sometimes why checkinstall is useful in installing source directly, generating a pseudo debian package to handle the 'make install'  means that you'll get some protection from overwriting files in installed packages when installing from source.

---

