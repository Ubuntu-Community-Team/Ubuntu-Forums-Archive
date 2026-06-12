---
title: "Where to install Mozilla Firefox?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-07-22
Just downloaded latest version of Firefox.  It is a tar file.  Where do people put it?  /bin? /usr/?  I have no idea.

Thanks in advance.  New to Ubuntu.

---

### Post by a0u on 2008-07-22
Firefox is installed by default and is included in the official [repositories]("https://help.ubuntu.com/community/Repositories").  Thus, downloading from the main site is unneeded. Ubuntu's Update Manager handles updates for individual applications as well as the base system, so just go to "System -> Adminstration -> Update Manager" and manually force an update.

Note that the repositories might not contain the latest versions, since the maintainers have thousands of software packages to cover.  Apparently, the latest available there is 3.0, not 3.0.1.  This should be corrected in time, however.

But in case you really want the latest version, I suggest you untar it in /usr/local/firefox (or something similar).  The [Hierarchy File Standard documentation](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html) provides some good information about the filesystem.

---

### Post by steveneddy on 2008-07-22
Why don't you just do a 

```
sudo apt-get install firefox
```

in terminal and get the most up to date Firefox?

OR:

if you want to run the one you just downloaded:

Right click the .tar.gz file, select Extract.

Open the folder and double click the Firefox Icon.

---

### Post by aysiu on 2008-07-22
If you're running Ubuntu 7.10, this may help you get that .tar.bz2 installed:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

---

### Post by cariboo on 2008-07-22
You are better off using the version in the repositories as it was just updated a couple of days ago. If it hasn't shown up on your mirror site just give it a few days.

It is not advised to install software from outside the repositories as the only way they will get updated is if you download and install a new version every time one comes out.

You can install most programs using Add/Remove Programs or Synaptic Package Manager.

If you have to install a program manually, to find out where it is located in a terminal type:

```
locate <program>
```

Where <program> is the program you want to locate.

Jim

---

### Post by aysiu on 2008-07-22
> **cariboo907 said:**
> 
It is not advised to install software from outside the repositories as the only way they will get updated is if you download and install a new version every time one comes out. That's not *entirely* true. If Firefox updates from 3.0.1 to 3.0.2, you don't have to download the entire tarball again. Once installed properly (using the instructions I linked to above or using Ubuntuzilla), all you have to do is run Firefox with ```
gksudo firefox
``` go to Help > Check for Updates and then install the updates and run Firefox as normal afterwards.

Yes, it's easier to let the repositories handle it, but you don't have to re-download the entire tarball with every update. Some people like the Mozilla version because they feel it performs better on their systems, some people are using Ubuntu 7.10 (for which Firefox 3 is not available through the repositories - and, no, the Gran Paradiso version doesn't count), and some people just get impatient waiting the extra couple of days for security patches from the repositories version.

---

### Post by louieb on 2008-07-22
If you  want to play around with some program or version of a program not in the repositories the   [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html") says
> /opt is reserved for the installation of add-on application software packages. 

For example I have  **webmin**  installed. It is installed in  /opt/webmin

---

### Post by aysiu on 2008-07-22
> **louieb said:**
> If you  want to play around with some program or version of a program not in the repositories the   [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html") says
 

For example I have  **webmin**  installed. It is installed in  /opt/webmin
And the instructions I linked to will install it to /opt

So will Ubuntuzilla.

---

