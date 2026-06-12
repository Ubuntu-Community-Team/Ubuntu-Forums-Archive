---
title: "E:The package linux-headers-3.13.0-36 archive"
date: 2014-10-08
forum: New to Ubuntu
---

### Post by Thejas_G_R on 2014-10-08
First I know nothing about ubuntu.When i was installing lubuntu an error occured saying something that my hard disk is old.then after installing i tried updating when i found this errior and when i asked my friend who also knows nothing about ubuntu told me that it might be due to improper installation of the kernel which might have occured during instalation as mentioned above.Somebody please help me.

---

### Post by zvacet on 2014-10-08
Try to install linux-headers by typing in terminal 

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Thejas_G_R on 2014-10-09
i got this after typing it in uxterm.
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package linux-headers-3.13.0-36 needs to be reinstalled, but ican ' t find an archive for it.


Now what?:(

---

### Post by zvacet on 2014-10-14
> after installing i tried updating when i found this error

Please, put here output of commands

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ian-weisser on 2014-10-14
Seems like -36 has been replaced by -37.

```
$ rmadison -u ubuntu linux-headers-generic | grep trusty
 linux-headers-generic | 3.13.0.24.28 | trusty           | amd64, arm64, armhf, i386, ppc64el
 linux-headers-generic | 3.13.0.37.44 | trusty-security  | amd64, arm64, armhf, i386, ppc64el
 linux-headers-generic | 3.13.0.37.44 | trusty-updates   | amd64, arm64, armhf, i386, ppc64el
```

---

### Post by Thejas_G_R on 2014-10-15
sorry my tests are going on will post complete result after 3 days.For the first command i got list something done.for the second command i was after a bunch of lines in the end it told.me.to.change something f-install. Again sorry will post after test

This last post was for zvacet

How to put those commanda with the straight line (like after the word generic and the symbol at the end of the each line

That latest one about symbol was for ian-weisser

---

### Post by zvacet on 2014-10-17
```
sudo apt-get -f install
```

---

### Post by Thejas_G_R on 2014-10-22
I got this error after giving that command @zvacet. 
unable to remove newly-extracted version of ' (there were many lines of this with the ending error while cleaning up:
Sub-process /usr/bin/dpkg returned an error code(2)
After there was huge command saying 
Problem executing scripts Dpkg: : Post-Invoke 'If [ -d /var/lib/update-notifier
]; then touch /var/lib/update-notifier/dpkg_run_stamp; fi; if [ -e/var/lib/update-notifier/update-available ]; then echo > /var/lib/update-notifier/update-available; fi '

And last line was
sub-process returned an error code.
Tell me if i have to enter the whole error.

---

### Post by zvacet on 2014-11-07
Sorry I really don´t know what to do next. Bump a thread and probably someone else will help you. Or you can ask for help on [IRC.]("https://wiki.ubuntu.com/IRC/ChannelList")

---

### Post by ian-weisser on 2014-11-07
Please give us the complete error that occurs when you do:
```
sudo apt-get update
sudo apt-get upgrade
```

You can copy-and-paste from the Terminal into your web browser.
Be sure to use [code] tags when you paste output here.

---

