---
title: "How to install Oracle Java 8 on Ubunt 16.10"
date: 2016-12-18
forum: New to Ubuntu
---

### Post by flex567 on 2016-12-18
Is there a good tutorial on how to install Oracle Java 8 on Ubuntu 16.10 ?

---

### Post by 1clue on 2016-12-18
[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

---

### Post by flex567 on 2016-12-22
Why would I trust some strange repository?

---

### Post by karl96 on 2016-12-22
OpenJDK is available in the repos, but if you need Oracle specifically you'll have to look at either using an rpm to deb conversion tool, or downloading the tar.gz file for your architecture.

Then run ```
 make-jpkg 
``` on the tar.gz file

And install it with dpkg

```
 dpkg -i name.deb 
```

Edit: you'll need to install ```
 apt-get install java-package 
``` to run the first command.

---

### Post by oldos2er on 2016-12-22
webupd8.org (Alin Andrei) has maintained several PPAs for years; there's nothing I'd consider "strange" about it. If you'd read the link you would've noted "As a reminder, the WebUpd8 Oracle Java PPA doesn't include any Java  binaries, just a script that automatically downloads and install Oracle  Java 8."

---

### Post by 1clue on 2016-12-23
Commercial software not directly supported by Canonical will be in a "strange" repository. Legally speaking you can't bundle non-free software with free software without violating the license terms of some of the software. There are examples where it's fine, but sole FOSS licenses object to being bundled with non-free software and vice versa.

The Ubuntu repositories don't have potentially problematic software in the main repo. Generally speaking either the third party will offer an installer directly (sometimes using the ppa approach) and sometimes somebody will make a ppa which downloads the appropriate software from the vendor website and install it for you.

Oracle requires that you accept their terms of use before downloading java. This webupd8 site's installer satisfies the legal terms set down by oracle while offering automatic updates.

---

### Post by leunam12 on 2016-12-24
If you don't want to add that PPA, then what you have to do is go to Oracle's website and download JAVA JRE and install it manually. Google how to install Oracle java on Linux or Ubuntu manually and you will find tutorials explaining how to do it. I have done it many times.

---

### Post by 1clue on 2016-12-24
If it helps you somehow, the official ubuntu docs suggest webupd8: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by QIII on 2016-12-25
That's actually the Community wiki and I am the one who put that in there.  ;)

But yes, webupd8 is the best place to go.  As was mentioned above, what you get is a series of scripts that installs what Oracle has.  The benefit is that as Oracle releases new versions, the webupd8 package is updated so you automatically get the newest.

---

