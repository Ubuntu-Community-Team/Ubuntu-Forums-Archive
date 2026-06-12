---
title: "How to install tar.gz available software using Ubuntu Software Center?"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by gchmverhaag on 2013-10-05
Hi,

I'm new to Ubuntu, and would like to install tar.gz available software by using the Ubuntu Software Center, but don´t know whether that is possible?

I'm using ubuntu 13.04!

Any hints on how to proceed would be very helpfull! Thanks!

Regards,
Gerard

---

### Post by drmrgd on 2013-10-05
Software with a tar.gz extension is usually just the source code that's been compressed into an archive for easy transport (like a zip file).  You need to extract the archive and then look for a README or INSTALL file or something like that for instructions on how to build the package for your system.  As you can see that's quite a hassle.  So, the best thing is to search the software center for the program and install it directly from there rather than downloading the source code and manually building it.  

Of course, if you have no other choice (i.e. it's not available in the Software Center), then do what I suggested at the start and let us know if you have problems.  Each package is a little different and generic instructions (beyond what I suggested) aren't really feasible.

---

### Post by gchmverhaag on 2013-10-05
Hi,

Thanks for the prompt reply! Well, in fact I've installed the plotting program Veusz using Ubuntu Software Center. This version is out-dated and has some bugs. So I want to upgrade to the newest version!

I found the following URL: [https://launchpad.net/~jeremysanders/+archive/ppa](https://launchpad.net/~jeremysanders/+archive/ppa) which explains how to do just that! I'll try that, and let you know whether is works!

Regards,
Gerard

---

### Post by drmrgd on 2013-10-05
Great!  That's a good find.  Anytime you can use the package manager for software installs, it's much, much better than having to deal with building it, getting and configuring the required dependencies, and handling future upgrades.  Good luck and let us know if you run into any trouble!

---

### Post by heir4c on 2013-10-05
If you install a newer version you get a message that there is a older version in SoftwareCenter. You can install a newer version but if its give conflicts that's your choice.

Beside that: You don't need the tar.gz files while you have the .deb files. 
Look here: [https://launchpad.net/~jeremysanders/+archive/ppa/+packages](https://launchpad.net/~jeremysanders/+archive/ppa/+packages)
Click on the newest version (on top of the list) and than it open. Scroll a little bit down and you see hyperlinks. 
Click first on: 
veusz-helpers_1.18-0~ppa1~raring1_amd64.deb (if you will install for 64bit) 
or: 
veusz-helpers_1.18-0~ppa1~raring1_i386.deb (if you will install for 32bit)
Download the package. 

Than click on: veusz_1.18-0~ppa1~raring1_all.deb and Download the package.
Go to the Download map and doubleclick on the first .deb package to install it.
When it's installed, doubleclick on the second to install the package.
That's all.

---

### Post by gchmverhaag on 2013-10-11
Hoi,

Don't understand the Ubuntu Software Center way of installing software!

I added this **ppa:jeremysanders/ppa **to the repository list within the Ubuntu Software Center, but don't see any newer version it in the list of software. I only see the older version (marked as installed!) which I installed some time ago.

How to get the newer version installed from here?

Regards,
Gerard

---

### Post by heir4c on 2013-10-11
Have you updated the list?
```
sudo apt-get update
```
With this commando you renew the packageslist.

---

### Post by gchmverhaag on 2013-10-11
No, I was thinking that this is done as soon I add the new ppa!

So you have to this from the terminal?

Well, I did that what you suggested, but still don't see any new Veusz version, and no update button either, sorry?

Regards,
Gerard

---

### Post by heir4c on 2013-10-11
If you add the ppa, you don't do that from the terminal?

And have you use the links I gave you or have you used something else? 
Can't you install directly the packages with a double click in the Download folder?

---

### Post by heir4c on 2013-10-11
I had the 1.15 version and I download just the .deb packages. Without adding the ppa.
I doubleclick on the packages to install them.
If it won't work with the UbuntuSoftwareCenter than first install: gdebi
If it's installed than you can rightclick on the packages and choose for "open with" and choose there for the GDebi packageinstaller.
Maybe you get a message there is a older version in the reposito's. Ignore that and close that message and install further.
Now I have the 1.18 version installed.

---

