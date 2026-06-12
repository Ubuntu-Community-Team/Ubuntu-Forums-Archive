---
title: "Update information"
date: 2014-11-01
forum: New to Ubuntu
---

### Post by flex567 on 2014-11-01
I get this error mesage all the time ? 
how can I fix this error?

```

Data files for some packages could not be downloaded

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem.

```

---

### Post by bapoumba on 2014-11-01
Please run **sudo apt-get install ttf-mscorefonts-installer** and accept the EULA. You have to hit <tab> to get to the OK button.

---

### Post by flex567 on 2014-11-01
```

seba@seba-H81-D3:~$ sudo apt-get install ttf-mscorefonts-installer 
[sudo] password for seba: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


```

---

### Post by bapoumba on 2014-11-01
```
sudo apt-get --purge ttf-mscorefonts-installer
sudo apt-get install --reinstall ttf-mscorefonts-installer
```
should get you to accept the EULA again.

---

### Post by flex567 on 2014-11-01
```
seba@seba-H81-D3:~$ sudo apt-get --purge ttf-mscorefonts-installer
[sudo] password for seba: 
E: Command line option --purge is not understood

```

---

### Post by deadflowr on 2014-11-01
Just purge no --
like so,
```
sudo apt-get purge packagename
```
The second command is good, though, using install --reinstall.

When it reinstalls you should get a screen(in the terminal) for a EULA.Use the tab button and the left/right buttons to accept it.

---

### Post by ibjsb4 on 2014-11-01
Remove the two dashes.
```
sudo apt-get purge ttf-mscorefonts-installer
```

Edit
You got me deadflowr :)

---

### Post by deadflowr on 2014-11-01
> **ibjsb4 said:**
> Remove the two dashes.
```
sudo apt-get purge ttf-mscorefonts-installer
```

Edit
You got me deadflowr :)

Great minds think alike.;)

---

### Post by bapoumba on 2014-11-02
I am very sorry.

I had written that in one line, then decided to give it as two steps. Poor mind needs to think twice :)
Thanks  deadflowr & ibjsb4 :KS

---

### Post by flex567 on 2014-11-02
```
seba@seba-H81-D3:~$ sudo apt-get purge ttf-mscorefonts-installer
[sudo] password for seba: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mscorefonts-installer*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 134 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 196514 files and directories currently installed.)
Removing ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
Purging configuration files for ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.411.orig.tar.gz
Installing from local file /tmp/tmptXrNjT.gz
Flash Plugin installed.
```

I didn't have to accept anything(EULA). 
Now the error message is gone so to fix it I had to reinstall a flashplugin?

---

### Post by bapoumba on 2014-11-02
You will have to accept it once you reinstall ttf-mscorefonts-installer (second line in post #4).

---

