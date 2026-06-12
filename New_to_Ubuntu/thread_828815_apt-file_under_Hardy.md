---
title: "apt-file under Hardy"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by kiwidoc66 on 2008-06-14
Hi
I've had to compile Hydrogen (drum machine) from source because of a bug so was trying to use apt-file to determine dependencies. 

After running apt-file update I get a range of 

Can't get [http://mirrors.easynews.com/linux/ubuntu/dists/hardy-updates/Contents-i386.gz](http://mirrors.easynews.com/linux/ubuntu/dists/hardy-updates/Contents-i386.gz)

errors despite trying several mirrors and the main site.

Is apt-file no longer supported?

---

### Post by ukripper on 2008-06-14
> **kiwidoc66 said:**
> Hi
I've had to compile Hydrogen (drum machine) from source because of a bug so was trying to use apt-file to determine dependencies. 

After running apt-file update I get a range of 

Can't get [http://mirrors.easynews.com/linux/ubuntu/dists/hardy-updates/Contents-i386.gz](http://mirrors.easynews.com/linux/ubuntu/dists/hardy-updates/Contents-i386.gz)

errors despite trying several mirrors and the main site.

Is apt-file no longer supported?

you need to install
```
sudo apt-get install apt-file
```

---

### Post by kiwidoc66 on 2008-06-14
Already installed, still doesn't work :(

---

### Post by kaptengu on 2008-06-14
Have you run:
```
/usr/share/apt-file/do-apt-file-update
```
?

---

### Post by kiwidoc66 on 2008-06-15
Thanks - unfortunately same error generated

---

### Post by js9986 on 2008-06-21
I'm seeing the same thing. 

After installing apt-file:
   sudo apt-get install apt-file

when I run this
   /usr/share/apt-file/do-apt-file-update
I see this


Can't get [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz)
Can't get [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz)
Can't get [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz)
Can't get [http://archive.canonical.com/ubuntu/dists/hardy/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/hardy/Contents-i386.gz)
Can't get [http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz)
Can't get [http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz)
Can't get [http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz)

---

### Post by firsttry on 2008-09-22
I'm getting the same problem but with a different repo:
```

sudo /usr/share/apt-file/do-apt-file-update
Can't get http://wine.budgetdedicated.com/apt/dists/hardy/Contents-i386.gz (404)

```

apt-file is installed:
```

aptitude search apt-file
i A apt-file                                            - APT package searching utility -- command-line interface      

```

I looked on wine.budgetdedicated.com and Contents-i386.gz is missing, so it *should* fail - but it shouldn't, should it? Surely the intended behaviour would be to give a warning rather than exit the program.

As a workaround I'll try and comment the wine repo from my sources.list file, hopefully that'll help.

Update: It did.

---

