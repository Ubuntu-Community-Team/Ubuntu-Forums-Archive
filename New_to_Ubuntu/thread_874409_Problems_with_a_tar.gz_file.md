---
title: "Problems with a tar.gz file"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by gustasonfrever on 2008-07-29
I'm trying to install the Sunbird application from a tar.gz and I can't figure out what I'm doing wrong (I have ubuntu 8.04)

justin@justin-laptop:~/Desktop/sunbird$ ./configure
bash: ./configure: No such file or directory
justin@justin-laptop:~/Desktop/sunbird$ make
make: *** No targets specified and no makefile found.  Stop.
justin@justin-laptop:~/Desktop/sunbird$

---

### Post by kool_kat_os on 2008-07-29
is sunbird in the repository's?

---

### Post by tamoneya on 2008-07-29
> **gustasonfrever said:**
> I'm trying to install the Sunbird application from a tar.gz and I can't figure out what I'm doing wrong (I have ubuntu 8.04)

justin@justin-laptop:~/Desktop/sunbird$ ./configure
bash: ./configure: No such file or directory
justin@justin-laptop:~/Desktop/sunbird$ make
make: *** No targets specified and no makefile found.  Stop.
justin@justin-laptop:~/Desktop/sunbird$

```
sudo chmod +x configure
sudo ./configure
```

---

### Post by tamoneya on 2008-07-29
> **kool_kat_os said:**
> is sunbird in the repository's?

Yes but i think it is a little out of date last time i checked.

---

### Post by steveneddy on 2008-07-29
```
sudo aptitude install sunbird
```

That'll do it.

---

### Post by gustasonfrever on 2008-07-29
justin@justin-laptop:~/Desktop/sunbird$ sudo chmod +x configure
chmod: cannot access `configure': No such file or directory
justin@justin-laptop:~/Desktop/sunbird$ 

Any idea why it still isn't working?

---

### Post by kool_kat_os on 2008-07-29
is there a file called "configure" in the sunbird folder?

---

### Post by cheetaux on 2008-07-30
Since the file is a tar.gz file, you need to uncompress it (gunzip it), and untar it.  Assuming that the file is called sunbird.tar.gz, the following will uncompress the tar file:

```
gunzip sunbird.tar.gz
```

Now you should have a tar file (sunbird.tar).  To extract the files from the tar file, do the following:

```
tar xvf sunbird.tar
```

You should now have the files you need.

---

