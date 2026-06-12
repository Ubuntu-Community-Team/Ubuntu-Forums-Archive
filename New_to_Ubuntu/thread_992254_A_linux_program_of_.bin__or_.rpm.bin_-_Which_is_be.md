---
title: "A linux program of .bin  or .rpm.bin? - Which is best?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by RLuck on 2008-11-24
With my limited knowledge of Ubuntu, linux, and working on a terminal -
Which would be easier for me to install ?

I did a search of the forums - I always either get nothing or millions of hits and most don't seem to fit.  :confused:

Bob

---

### Post by bobnutfield on 2008-11-24
A .bin file is a shell script and an rpm.bin is a shell script to install an rpm in Red Hat and Fedora systems.  The best thing is to locate a .deb file for the software you want to install, or even better look for it in the Ubuntu repos.  You would not be able to install and rpm on Ubuntu without converting it, which can be a little complicated.  "Almost" anything you can get an rpm for is also available as a .deb.  But, if you MUST install what you have, then install the .bin with:

> sudo sh <name of script>.bin

---

### Post by taurus on 2008-11-24
Are you talking about Sun's java?

---

### Post by eeeek on 2008-11-24
Using Synaptic Package Manager or the "Add-Remove Programs" tool. Both are very user-friendly and probably the easiest way to install software.

In general - rmp's are not for Linux. Yes, you can use a program called Alien to convert them, but as a fellow new user who as tried it, I wouldn't recommend that route.

Enjoy-

---

### Post by taurus on 2008-11-24
> **eeeek said:**
> 

In general - **rmp's are not for Linux**. Yes, you can use a program called Alien to convert them, but as a fellow new user who as tried it, I wouldn't recommend that route.

Enjoy-

Shoudn't it be "rmp's are not for Ubuntu"?

---

### Post by chrisccoulson on 2008-11-24
> **taurus said:**
> Shoudn't it be "rmp's are not for Ubuntu"?

Perhaps "rpm's are not for Ubuntu"? ;)

---

### Post by igknighted on 2008-11-24
> **bobnutfield said:**
> A .bin file is a shell script and an rpm.bin is a shell script to install an rpm in Red Hat and Fedora systems.  The best thing is to locate a .deb file for the software you want to install, or even better look for it in the Ubuntu repos.  You would not be able to install and rpm on Ubuntu without converting it, which can be a little complicated.  "Almost" anything you can get an rpm for is also available as a .deb.  But, if you MUST install what you have, then install the .bin with:

Not to be trivial, but a .bin file is almost certainly not a shell script.  A script is written in plain text, you can open it with an editor and change the contents.  This is source code.  A .bin on the other hand, would typically indicate a binary file.  This is compiled source code (all ones and zeros, or hex).  Binary files cannot be edited, and are their own applications.  They do not rely on an interpreter (the command sh, for example, which is interpreting shell scripts), as it was already compiled into machine language.  Hence it can be run directly.

[http://www.dsbscience.com/freepubs/start_programming/node6.html](http://www.dsbscience.com/freepubs/start_programming/node6.html)

---

### Post by bobnutfield on 2008-11-24
> **igknighted said:**
> Not to be trivial, but a .bin file is almost certainly not a shell script.  A script is written in plain text, you can open it with an editor and change the contents.  This is source code.  A .bin on the other hand, would typically indicate a binary file.  This is compiled source code (all ones and zeros, or hex).  Binary files cannot be edited, and are their own applications.  They do not rely on an interpreter (the command sh, for example, which is interpreting shell scripts), as it was already compiled into machine language.  Hence it can be run directly.

[http://www.dsbscience.com/freepubs/start_programming/node6.html](http://www.dsbscience.com/freepubs/start_programming/node6.html)

Whooops!  My sometimes mushy brain got temporarily confused with .sh.  Bound to happen again sooner or later.

Thanks for the correction.

---

### Post by handydan918 on 2008-11-24
> **taurus said:**
> Shoudn't it be "rmp's are not for Ubuntu"?

No, I don't think so...It should be RPM's are not for Ubu...(not rmp's, which are a different sort of thing altogether...)


:rofl:

---

### Post by LowSky on 2008-11-24
you can use a program called alien to install RPM packages, it works morst of the time

otherwise stick to .deb files

---

### Post by StOoZ on 2008-11-24
I usually stay away from rpm's , I prefer sources , usually its an rpm or source.
of course a deb , or ubuntu repository is the best.

---

### Post by RLuck on 2008-11-24
> **taurus said:**
> Are you talking about Sun's java?

Yes taurus - I have a program DVArchive that I have used for quite a while. I have always been able to load java 1.4.2 into Firefox and the program worked. But here in ubuntu - no such luck - my saved copy of JRE 1.4.2 was lost. So I wanted to download again from Sun.  I have since downloaded java with Synaptic Package Manager - but DVA will not start - this is usually caused by the java version or installation. The program signon comes up but then hangs.  

Is there some easy way to check if java is working. I've been to Sun but nothing leaped out telling me how to test it. 

Sun java 1.4.2 is at the end of it's life - new version is 6.xxx -  I wonder is this 1.6.x  or did they jump ahead all the way to 6  ?? 

I told you folks I was stumbling around in linux.  but I sure need this program to work. I have used it - same program in several flavors of linux and Win2k - same program works in all - I think it is written in java and I have had little trouble till now. In the past the only problems I've had were related to the installation of the java run time.

Any help is appreicated.  

Bob

---

### Post by taurus on 2008-11-24
If it is java that you want to install, you can do it either with synaptic or from a terminal.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

p.s.  When you get to the java licensing screen, press the Tab key to highlight the <OK> and Return to except it.

---

### Post by oldos2er on 2008-11-24
"In general - rmp's are not for Linux."

 It's RPM, which means RedHat package manager, so it certainly is for Linux Fedora and other RedHat derivatives; just not meant specifically for Ubuntu (and other Debian based distros).

---

