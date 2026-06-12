---
title: "Apt-server"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Kruti Shah on 2008-08-26
What is apt server?

---

### Post by DBrocks on 2008-08-26
Hello there!

Now, I dont think you mean an Apt SERVER, rather, do you mean an Apt REPOSITORY (Commonly referred to as a Repo)? An Apt repo is a central storage area with all sorts of apps for debian. So, one line of code, and Ubuntu figures out what app it is, and all the other dependencies. Then it connects to the apt repos, and downloads them all.

---

### Post by Kruti Shah on 2008-08-26
Thanks..
can u tell me how to configure it..i mean how to create a local repository.

---

### Post by forger on 2008-08-26
You want to mirror and use an apt repository locally on your computer?

---

### Post by Kruti Shah on 2008-08-26
yes

---

### Post by DBrocks on 2008-08-26
Wait, are you trying to build a local apt repo? Or just configure Apt for use

For local, check out this tread:
[http://ubuntuforums.org/showthread.php?t=451209](http://ubuntuforums.org/showthread.php?t=451209)

For just regular apt, it doesnt need to be configured, it should work out of the box. Test it by entering this line of code in the command line:
```
sudo apt-get install cmatrix
```if all works, then it will install cmatrix, (A command line based screensaver that looks like the matrix) if it worked you should be able to start cmatrix by running this from command line:
```
cmatrix
```

---

### Post by forger on 2008-08-26
You'll require to read up some stuff:
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)
[http://www.google.com/search?q=%22how%20to%22%20apt%20mirror%20local](http://www.google.com/search?q=%22how%20to%22%20apt%20mirror%20local)

Some package application that you might need:
> 
apt-mirror - APT sources mirroring tool
apt-proxy - Debian archive proxy and partial mirror builder


---

### Post by Kruti Shah on 2008-08-26
I want to create a local repository

---

### Post by Vivaldi Gloria on 2008-08-26
Some apt-mirror links:

[http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)
[http://popey.com/Creating_an_Ubuntu_...ith_apt-mirror](http://popey.com/Creating_an_Ubuntu_...ith_apt-mirror)
[http://odzangba.wordpress.com/2007/1...ubuntu-mirror/](http://odzangba.wordpress.com/2007/1...ubuntu-mirror/)
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

