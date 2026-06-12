---
title: "I may be new .............but"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by tinylittle on 2008-09-19
I am definitely new, but feel a little dumb also. I want to install 3rd party programs that say they are appropriate for Linux, like Pc Anywhere. However; and I have done the searches,  the procedure seems overly complicated. I know some of you will criticize me that using the terminal isn't for everyone, but.....I do consider myself fairly computer knowledgeable yet still find the procedures convoluted and tricky.

So my question is...isn't there some sort of installer that will take these .bin files (say, from Java) or utilize 3rd party cd's and install them without all the complicated and precise steps required in the terminal?

I appreciate any constructive responses.

Thanks

---

### Post by northern lights on 2008-09-19
[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware") might prove a worthy read.

As an aside, it's advisable to use a descriptive topic title...
"Need help installing PCAnywhere", for instance.

---

### Post by SeanHodges on 2008-09-19
Have a look at this: [http://www.youtube.com/watch?v=E8VmernM4qM](http://www.youtube.com/watch?v=E8VmernM4qM)

---

### Post by clive littlewood on 2008-09-19
Hi

Why not use synaptic or add/remove programs ??

If you canno find your program in either of these make sure you download a .deb file and then all you need to do is double click on the file to install.

Hope this helps

cl

---

### Post by tinylittle on 2008-09-19
Thanks everyone for your help. Maybe it was just because the first program I wanted to install was Pcanywhere from disk that I got the bad experience. Apparently you have to install Java first and even with the .rpm file I could not get it to work. I just assumed all the other programs worked like that also. 

I will try again. 

If anyone knows of a simple install for Pcanywhere 11.0, let me know.

Thanks again.

---

### Post by jlisek on 2008-09-21
Hi,

Try [www.gotodevice.com](www.gotodevice.com) much easier to use than pcanywhere.
GoToDevice is a real executable not some Java c...

It is fully Cross-platform allowing you to control windows pc's from linux and linux pc's from windows. 

Installs using .deb files, which is as easy to use as msi files on windows.:KS

Best regards,

John

---

### Post by anewguy on 2008-09-21
You should be able to do the same thing with the built-in remote desktop.  You may also want to check out tinyvnc.  These allow you to run the remote computers' desktop.

---

### Post by oldos2er on 2008-09-21
> **tinylittle said:**
> Thanks everyone for your help. Maybe it was just because the first program I wanted to install was Pcanywhere from disk that I got the bad experience. Apparently you have to install Java first and even with the .rpm file I could not get it to work. I just assumed all the other programs worked like that also. 

I will try again. 

If anyone knows of a simple install for Pcanywhere 11.0, let me know.

Thanks again.

 To install Java (and some other goodies), open a terminal and type "sudo apt-get update && sudo apt-get install ubuntu-restricted-extras". *.rpm files are for Red Hat Linux and its derivatives.

 Also read  [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by jimmy the saint on 2008-09-21
Just to clarify oldos2er's comment, .rpm files will not work in Ubuntu because it is derived from debian.  debian uses .deb package files.

---

