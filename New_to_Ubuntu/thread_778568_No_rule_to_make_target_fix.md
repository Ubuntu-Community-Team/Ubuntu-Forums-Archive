---
title: "No rule to make target fix?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by rbcl15 on 2008-05-02
"No rule to make target". Is there anyone who overcame this obstruction? Please let me know how to fix this? Thanks.

---

### Post by iSplicer on 2008-05-02
Where did you see this error? Could you please tell us more about it?

---

### Post by rbcl15 on 2008-05-02
I tried to install some packages and I got this error apparently others have had the same experience though I am still searching for the the fix. Thanks.

---

### Post by tacutu on 2008-05-02
you probably need to install some headers (the "-dev" version of the package) in order to compile stuff. Post your error message here (including as much as possible). As it is, your question is very vague and unanswerable.

---

### Post by Oldsoldier2003 on 2008-05-02
Honestly you really don't NEED to compile software often, unless you like to be on the bleeding edge or enjoy the addition freedom of customization that compiling your software grants.

but since you are having some problems here are some grnrtic tips/pointers :

Get build essential

```
sudo apt-get install build-essential
```

Get the build dependencies of the package you want to build

```
sudo apt-get build-dep <packagename>
```

after extracting the source code from the tarball cd to the source code dir and:

```
./configure
```

make

```
make install
```


to uninstall

```
sudo make uninstall
```

---

### Post by mc4man on 2008-05-02
> No rule to make target
You may see that on source's that use a shell script to configure and make, or if they don't need to be built, just run. Look for a file ending in .sh or a readme.

---

### Post by greyfox1 on 2008-05-03
I believe the OP was referring to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-kernel-headers/+bug/179114"), which seems to occur when compiling a program against the kernel headers.  Personally, I ran into it while trying to compile the qc-usb 0.6.6 Logitech Quickcam driver.  I found this thread as well as the Launchpad bug file while searching for a possible solution to my own problem.

---

