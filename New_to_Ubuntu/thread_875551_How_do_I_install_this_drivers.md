---
title: "How do I install this drivers ?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2008-07-30
Hi
I'm trying to install this
[**_tarball_**]("http://nxtvox.com/downloads/tarball/zaptel-1.4.11.tar.gz")

with this command :

```
tar zxvf zaptel-1.4.11.tar.gz
```
But it doesn't work, the output is :

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

Why is that ?

Thanks

---

### Post by PmDematagoda on 2008-07-30
Did you try unpacking the driver archive with Archive Manager or similar and seeing if that works?

---

### Post by Pierrot Lafouine on 2008-07-30
Yes, Archive Manage (File Roller 2.20) open the tarball file.
What do I do with the uncompressed folder (filled with source code and more ) ?

---

### Post by tinny on 2008-07-31
Isnt this driver available in the "universe" repository?

Enable the "universe" repository
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20the%20Universe%20and%20Multiverse%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20the%20Universe%20and%20Multiverse%20Repositories)

then..
```

sudo apt-get update
sudo apt-get install zaptel

```

---

### Post by PmDematagoda on 2008-07-31
I did think about the repositories, but I dropped it on my assumption that it is a proprietary driver, thanks for pointing out the package tinny:).

---

### Post by Pierrot Lafouine on 2008-07-31
> **tinny said:**
> Isnt this driver available in the "universe"
repository?

hummm I would be surprised, as the driver I'm trying to install is
not the standard Zaptel, but a patched one from NxtVox.

I'll give a try, but if you have an alternative, I would take it.

Thanks

---

### Post by Pierrot Lafouine on 2008-07-31
..

---

### Post by Shazaam on 2008-07-31
If you still want to install the source file there should be a "README" or an "INSTALL" file that will help you.
Usually it goes like this..
1. Open a terminal.
2. cd (change directory) to where the file is. If you extracted the tar to your desktop you would enter this (where /yourusername is your user name)-
```
cd /home/yourusername/Desktop/nameoffolder
```
or
```
cd ~/Desktop/nameoffolder
```
3. Then you would enter...
```
./configure
```
4. then
```
make
```
5. then
```
sudo make install
```

---

### Post by PmDematagoda on 2008-07-31
You might want to read the readme which can be found here if you want to install the driver manually.

Readme is here:-
[http://downloads.digium.com/pub/zaptel/README-1.4.11](http://downloads.digium.com/pub/zaptel/README-1.4.11)

---

### Post by tinny on 2008-07-31
I see that the zaptel package version in the hardy repository is 1.4.10.

The intrepid universe repository has version 1.4.11 that you are after.

You could set the intrepid repository up by using "Pinning" and then obtain this version by just using APT.

FYI:
[http://aldeby.org/blog/index.php/mixing-hardy-stable-and-intrepid-testing-repositories.html](http://aldeby.org/blog/index.php/mixing-hardy-stable-and-intrepid-testing-repositories.html)

---

