---
title: "How do I install downloaded software In Xubuntu?"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by crimsonsword on 2013-05-05
I have downloaded Avast and Opera I tried to open them with Ubuntu Software center to install because this is how you install Chrome it in Ubuntu and I tried the same thing here in Xubuntu.  But it does not work.
I use Xubuntu. Can some body help me? thanks beforehand:confused:

PS: To the person who suggested I use Xubuntu instead of Ubuntu - Many many Thanks.
Its remarkably fast and intuitive.

---

### Post by ibjsb4 on 2013-05-05
How and from where did you download them?

---

### Post by Dennis N on 2013-05-05
If you have a .deb file to install, then your alternative (to the software center) is to use the gdebi package installer. You can install gdebi from the Ubuntu repositories through the software center.

After gdebi is installed, right-click on the .deb file you want to install, and select "Open with GDebi package installer" and you are on the way.

---

### Post by Buntu Bunny on 2013-05-05
> **Dennis N said:**
> If you have a .deb file to install, then your alternative (to the software center) is to use the gdebi package installer. 

This wasn't my question, but I appreciate the answer. It's useful to me too. (I love what I learn from reading the various threads).

---

### Post by BluNova on 2013-05-05
What does the file end with .deb, .tar.gz or something else

---

### Post by Peripheral Visionary on 2013-05-05
> **crimsonsword said:**
> I have downloaded Avast and Opera I tried to open them with Ubuntu Software center...

If I'm reading this right, it sounds like you downloaded these applications from some web site and then tried to use the Software Center to install them.  Is that right?

If it is, then you need to know that Linux doesn't work that way.  Software is downloaded from the Ubuntu repositories, not from a web site.  You can use the Software Center *both* to download *and* to install Avast and Opera and anything else listed in the Software Center.  It gets the "deb" (the package of software) from the Ubuntu repositories and installs it along with "libraries" and other bits of programming that your chosen package depends on to use.  Perhaps you got the package from the web, but not the dependencies that Software Center (and Synaptic Package Manager, and the apt-get command) automatically includes when installing it.

> ... because this is how you install Chrome ... and I tried the same thing here in Xubuntu.  But it does not work. 

I don't know about Chrome, but Ubuntu and all it's variants use Debian's package management to install software (that's why the packages are called "debs").

---

### Post by Dennis N on 2013-05-05
**@crimsonsword**;

About your items and sources:

Avast is a popular antivirus software for **Windows only**. You can't use it.

Opera is not in the Ubuntu repositories, so you have to get the installer from the vendor's web site if you want that software. I assume you did that. 

The reason your opera installer may not have worked may be because you were offered the wrong version for your OS. I went to their web page ([www.opera.com](www.opera.com)), clicked on the green download button, and the download file offered for Ubuntu by default is a 64-bit version (filename ends in amd64.deb), **even though I am using a 32-bit version of Xubuntu**. That should not happen. On the downloads page, you need to click the link '**show other versions**'. Then you can select the 32-bit version (filename ends in i386.deb) if you have a 32-bit version of Xubuntu. See post #3.

Good luck.

---

### Post by crimsonsword on 2013-05-05
**Thank You**. but if you visit makeuseof.com there is a list of "best of Linux software" with download links.
Avast is in that list. There is apparently a  Linux version of  Avast. Obviously I cannot install software
designed for Win, osx,  in Xubuntu.

---

### Post by ibjsb4 on 2013-05-05
Avast deb is dated.

[http://forum.avast.com/index.php?topic=116665.msg905152#msg905152](http://forum.avast.com/index.php?topic=116665.msg905152#msg905152)

I don't use it or any anti virus, but clamscan is in the software center.

[ATTACH=CONFIG]242242[/ATTACH]

---

