---
title: "Cannot install tasksel"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by cuebiz on 2013-01-10
I am trying to install tasksel using the command

```
sudo apt-get install tasksel
```but I get the following error....

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 initramfs-tools : Breaks: console-setup (< 1.72) but 1.34ubuntu15 is to be installed
 initscripts : Breaks: console-setup (< 1.74) but 1.34ubuntu15 is to be installed
 libglib2.0-0 : Breaks: gvfs (< 1.8) but 1.6.4-0ubuntu1 is to be installed
E: Broken packages

```

Before running the install, I added the souce 'deb [http://*ftp.de.debian.org/debian*]("http://%3Ci%3Eftp.de.debian.org/debian%3C/i%3E") sid main' as mentioned in [http://packages.debian.org/sid/all/tasksel/download](http://packages.debian.org/sid/all/tasksel/download)

What am I doing wrong?

---

### Post by steeldriver on 2013-01-10
Hello and welcome

If you really need tasksel it should be in the standard repository - why do you think you need to add a Debian repository?

Alternatively there may be easier / better ways to install the components you want (ssh server? LAMP?) directly

---

### Post by Cheesemill on 2013-01-10
> **cuebiz said:**
> Before running the install, I added the souce 'deb [http://*ftp.de.debian.org/debian*]("http://%3Ci%3Eftp.de.debian.org/debian%3C/i%3E") sid main' as mentioned in [http://packages.debian.org/sid/all/tasksel/download](http://packages.debian.org/sid/all/tasksel/download)

That's what you've done wrong.

You've added a Debian source to your Ubuntu machine. This will break everything in your installation pretty quickly. What made you think you had to add it? The standard Ubuntu repositories already contain tasksel.

Remove the line you've added to your sources.list then just do...
```
sudo apt-get update
sudo apt-get install tasksel
```

---

### Post by cuebiz on 2013-01-10
Thank you Cheesemill and steeldriver. I am not able to find tasksel in Synaptic Package Manager

This is what I get if I run the install without this source added

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tasksel is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'tasksel' has no installation candidate

```

---

### Post by steeldriver on 2013-01-10
what version of Ubuntu are you running?

---

### Post by Cheesemill on 2013-01-10
It's definitely in the main Ubuntu repository...
[http://packages.ubuntu.com/search?keywords=tasksel&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=tasksel&searchon=names&exact=1&suite=all&section=all)

Did you run...
```
sudo apt-get update
```
first?

If you still don't have any luck can you post the output of...
```
cat -n /etc/apt/sources.list
```

---

### Post by cuebiz on 2013-01-10
I am using 10.10

yes, I did run update. It gave few 404 errors. Would that be a problem?

I am attaching my source.lst

---

### Post by arpanaut on 2013-01-10
10.10 has passed End of Life

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
those repositories do not exist you will need to upgrade to a supported release or reinstall.

---

### Post by lukeiamyourfather on 2013-01-10
> **arpanaut said:**
> 10.10 has passed End of Life

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
those repositories do not exist you will need to upgrade to a supported release or reinstall.

To the original poster, if you need an install to be supported for an extended period of time use an LTS release like 12.04 LTS (supported until April of 2017).

---

### Post by cuebiz on 2013-01-10
Thank you all. Let me upgrade and let you know the result

---

