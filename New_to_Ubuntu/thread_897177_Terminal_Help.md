---
title: "Terminal Help"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by mattcadu on 2008-08-21
I downloaded Java to my desktop 
jre-6u7-linux-i586-rpm.bin

Can someone please tell me what to type in the terminal to install this file?

ty

---

### Post by meanburrito920 on 2008-08-21
Just install the JDK from Add/Remove

---

### Post by PegMonster on 2008-08-21
That is an rpm file, ubuntu uses deb as default. Is there a deb download available?


Also, have you installed ubuntu-restricted-extras?
That should install java for you I believe.


PegMonster

---

### Post by frank002 on 2008-08-21
Go to Synaptic and do a search for .......sun-java. You should see all the java packages.

---

### Post by mattcadu on 2008-08-21
Ok that worked, how would i go about installing this.......


NVIDIA-Linux-x86-96.43.07-pkg1.run

---

### Post by tuxxy on 2008-08-21
Open a terminal and navigate to the files directory

```
cd Desktop
```

Then type

```
chmod +x filename.run
```

Finally run the installer

```
./filename.run
```

---

### Post by rockerphil on 2008-08-21
this should be a lot easier than installing it manually, just open up a terminal and run this

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

and that should do the trick, no having to hassle with a manual install

---

### Post by oldos2er on 2008-08-22
> **mattcadu said:**
> I downloaded Java to my desktop 
jre-6u7-linux-i586-rpm.bin

Can someone please tell me what to type in the terminal to install this file?

ty

 Install Java from the repositories. Open System, Administration, Synaptic Package Manager; use the search term 'java' to find what you need.

---

### Post by oldos2er on 2008-08-22
> **tuxxy said:**
> Open a terminal and navigate to the files directory

```
cd Desktop
```Then type

```
chmod +x filename.run
```Finally run the installer

```
./filename.run
```

 For NVIDIA-Linux-x86-96.43.07-pkg1.run, it's necessary to kill X, and run the file as admin.

---

### Post by doorknob60 on 2008-08-22
For the Nvidia, unless you have a reason not to, just install it the Ubuntu way:
```
sudo aptitude install nvidia-glx
```
That installs the 96 version, but if you have a Geforce 5 or higher, you can use a newer driver with this
```
sudo aptitude install nvidia-glx-new
```

---

