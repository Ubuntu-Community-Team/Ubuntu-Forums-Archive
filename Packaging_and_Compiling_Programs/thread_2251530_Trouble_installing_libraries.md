---
title: "Trouble installing libraries"
date: 2014-11-04
forum: Packaging and Compiling Programs
---

### Post by emanmcdow on 2014-11-04
I'm trying to install the C++ library sphinxbase. I start up terminal, extract the .tar.gz file I downloaded, read the instructions, and do ./configure, make, and make install. The configure seems to be fine(I don't really know, since I'm new to installing from source), but make and make install are giving me odd errors that I can't pin down on the internet. What's going on here?

The results of each:

./configure
[http://pastebin.ubuntu.com/8825724/](http://pastebin.ubuntu.com/8825724/)

make
[http://pastebin.ubuntu.com/8825773/](http://pastebin.ubuntu.com/8825773/)

make install
[http://pastebin.ubuntu.com/8825785/](http://pastebin.ubuntu.com/8825785/)

---

### Post by steeldriver on 2014-11-04
You (unnecessarily) used sudo to configure and make in your home directory, then didn't use sudo to make install - where it **is** necessary since the target install directory (/usr/local/lib) is owned by root

---

### Post by emanmcdow on 2014-11-04
Steel, fixed that, but it didn't change anything.

---

### Post by steeldriver on 2014-11-04
Didn't change anything? you got the exact same errors?

I suggest you start over and unpack the archive again (running configure and make with sudo will have messed up the permissions in your current build tree), then

```

./configure

make

sudo make install

```

Don't do the install unless the make completes without error.

---

### Post by emanmcdow on 2014-11-04
Unpacked again, did as you said, but still got the same. Also, for future reference, what is a build tree?

---

### Post by steeldriver on 2014-11-04
What Ubuntu version / flavor are you running? I just downloaded the sphinxbase-0.8.tar.gz from [http://sourceforge.net/projects/cmusphinx/files/sphinxbase/0.8/sphinxbase-0.8.tar.gz/download](http://sourceforge.net/projects/cmusphinx/files/sphinxbase/0.8/sphinxbase-0.8.tar.gz/download) to my 32-bit 12.04 box and it appeared to configure and make OK for me (didn't 'make install' b/c I don't know what it is or what it might do to my system)

By 'build tree' I just meant your /home/emmett/Documents/program-source/sphinx/sphinxbase-0.8/ directory

---

### Post by emanmcdow on 2014-11-04
> **steeldriver said:**
> What Ubuntu version / flavor are you running?

Ubuntu 14.10 64-bit

edit: I have been using Ubuntu since 13.04, and have had similar issues in the previous editions. I just never got around to fixing it until now.

---

### Post by emanmcdow on 2014-11-07
bump

---

### Post by monkeybrain20122 on 2014-11-07
I just compiled and installed it with no problem. Ubuntu 14.04 64 bit too. But instead of make install I used checkinstall, since it creates a .deb which I can remove with synaptic instead of having files scattering in the file system. 

You need to install it first from the repo
```
sudo apt-get install checkinstall
```

Then instead of 
```
sudo make install
```
in the last step do
```
sudo checkinstall
```
and follow the prompts.

Finally 

```
sudo ldconfig
```

This is because it is installed in /usr/local instead of /usrand has to update its path for the system to find it, otherwise it won't show up in synaptic (unless in the first step 
./configure --prefix=/usr)

Now I am removing the .deb from synaptic since I have no use for it.

**Edited:** Anyway, isn't it in the repo already, called** sphinixbase-utils** or something??

---

### Post by emanmcdow on 2014-11-07
Thanks a lot monkeybrain. That command is really useful. That fixed it.

---

