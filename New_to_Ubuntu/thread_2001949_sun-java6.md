---
title: "sun-java6"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by jiangchongyi on 2012-06-11
I tried to install the sun-java6 under ubuntu 10.04 following the instruction below:
 
 
sudo add-apt-repository "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner"

sudo apt-get update
 
sudo apt-get install sun-java6-jre sun-java6-plugin
 
 
Then I got the prompt that:
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

How can I solve the problem? 
Any help will be grateful!!

---

### Post by hansdown on 2012-06-11
Hi jiangchongyi.

Follow the instructions in this link.

[http://www.ubuntugeek.com/sun-java6-packages-got-new-ppa-new-for-ubuntu-10-1010-04.html](http://www.ubuntugeek.com/sun-java6-packages-got-new-ppa-new-for-ubuntu-10-1010-04.html)

It should help.

---

### Post by TBABill on 2012-06-11
[http://iltts.blogspot.com/2012/05/how-to-install-sun-java-or-sun-jdkjre.html](http://iltts.blogspot.com/2012/05/how-to-install-sun-java-or-sun-jdkjre.html)

---

### Post by jiangchongyi on 2012-06-12
> **hansdown said:**
> Hi jiangchongyi.
 
Follow the instructions in this link.
 
[http://www.ubuntugeek.com/sun-java6-packages-got-new-ppa-new-for-ubuntu-10-1010-04.html](http://www.ubuntugeek.com/sun-java6-packages-got-new-ppa-new-for-ubuntu-10-1010-04.html)
 
It should help.
 
I tried as it instructed but it still failed to work...
 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package sun-java6
 
 
Is there any other way can help to fix it?

---

### Post by jiangchongyi on 2012-06-12
> **TBABill said:**
> [http://iltts.blogspot.com/2012/05/how-to-install-sun-java-or-sun-jdkjre.html](http://iltts.blogspot.com/2012/05/how-to-install-sun-java-or-sun-jdkjre.html)
 
 
 
I tried many times but still can not open the website you have offered...

---

### Post by hansdown on 2012-06-12
I no longer have a 10.04 install, so I can only tell you what I have installed.
```

sun-java6-jre
```

```
sun-java6-bin
```

```
sun-java6-plugin
```

Hope this helps.

---

### Post by QIII on 2012-06-12
Java 6 reaches EOL in November and has security issues.  Furthermore, Oracle has pulled all licenses for anyone to maintain packages, so you won't find any in the Ubuntu repos.

Install Oracle Java 7 instead.

See my signature for a very easy method that handles downloading Oracle Java 7 from the Oracle website, installing it and installing the browser plugin.  This will also keep you updated as Oracle updates Java.

---

### Post by jiangchongyi on 2012-06-12
> **hansdown said:**
> I no longer have a 10.04 install, so I can only tell you what I have installed.
```

sun-java6-jre
```
 
```
sun-java6-bin
```
 
```
sun-java6-plugin
```
 
Hope this helps.
 
 
It works!
Thx a lot!!

---

### Post by hansdown on 2012-06-12
Glad you fixed it,jiangchongyi.

---

### Post by QIII on 2012-06-12
Unfortunately, what you now have is an out-dated Java and a plugin that may not work or will cause you to be told you must update Java on sites that are keeping up.

I highly recommend reconsideration.

---

