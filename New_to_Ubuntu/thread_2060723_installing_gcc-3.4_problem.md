---
title: "installing gcc-3.4 problem"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by mark allyn on 2012-09-20
Hello everyone,
 
I have installed gcc-4.6 at /usr/bin.  I am trying to install gcc-3.4 at /usr/local/bin.  I downloaded gcc-3.4.6.tar.gz from gnu.org and "detarred" the file.   I can configure the file without any error using --prefix =-/usr/local/3.4.6 .  However, when I run make bootstrap-lean all I get is a stream of errors that indicate problems with the installed gcc-4.6 include files.  
 
I don't know how to deal with this problem.  Perhaps someone can suggest a solution.
 
Regards,
Mark Allyn

---

### Post by idoitprone on 2012-09-21
> **mark allyn said:**
> Hello everyone,
 
I have installed gcc-4.6 at /usr/bin.  I am trying to install gcc-3.4 at /usr/local/bin.  I downloaded gcc-3.4.6.tar.gz from gnu.org and "detarred" the file.   I can configure the file without any error using --prefix =-/usr/local/3.4.6 .  However, when I run make bootstrap-lean all I get is a stream of errors that indicate problems with the installed gcc-4.6 include files.  
 
I don't know how to deal with this problem.  Perhaps someone can suggest a solution.
 
Regards,
Mark Allyn


yikes. you installed it at /usr/bin

Reinstall the gcc and libraries from the ubuntu repostory

Try to install it on your gcc4.6 /usr/local/bin

breaking essential packages is not easy to fix.

---

### Post by mark allyn on 2012-09-21
Hi Idoitprone.
 
Nice name.  Well, as a matter of fact, I didn't install gcc4.6 in /usr/bin.  sudo dpkg -i did it.  But, I'm glad you responded, because I have been trying to figure out how to force sudo dpkg to install in /usr/local/bin.  What options need setting?
 
Regards,
Mark

---

### Post by mark allyn on 2012-09-21
Hello again, Idoitprone,
 
I owe an apology to sudo dpkg.  It didn't do the install at /usr/bin.  When I first installed ubuntu 12.04, gcc turned up in the /usr/bin directory.  
 
But, I'd still like to know how to get sudo dpkg to install in a directory of my choosing, for example, /usr/local/bin.
 
My original question still stands, by the way. 
 
Regards,
Mark

---

### Post by idoitprone on 2012-09-21
i dont think your need a hypen

```
-prefix =-/usr/local/3.4.6 
```


```

make clean
./configure --prefix=/usr/local/3.4.6
```

---

### Post by mark allyn on 2012-09-21
Hi Idoitprone,
 
Thanks.  I'll give it a try.  I'll report back tomorrow morning (US EDT).
 
Mark

---

### Post by BicyclerBoy on 2012-09-21
Non expert advice:
There are toolchain ppa..these let you have multiple compiler versions & switch between using the concept of alternatives..
You use couple scripts & symlinks etc..
I have 4.3 & 4.6 on same install by using the link below..

But I doubt there are any easy toolchain ppa for 12.04 with older gcc versions.
You might find a solution by looking at or using alternatives.
[http://askubuntu.com/questions/26498/choose-gcc-and-g-version/26518#26518](http://askubuntu.com/questions/26498/choose-gcc-and-g-version/26518#26518)
Note the comment about CC environ variable.

Could be easier to load up/install old ubuntu in VirtualBox..
Your app will only run (outside VirtBox) if it is compiled statically.
VirtualBox will mask/hide the CPU architecture etc.

---

### Post by mark allyn on 2012-09-22
Hi BicyclerBoy,
 
Thanks for your input on this.  I will investigate the link you sent.
 
According to the GNU GCC project it should be possible to have different versions of GCC on the same system.  This at least is their claim at gcc.gnu.org/faq.html.  That faq states that the versions must be in different directories.  In their example, for my case the directories would be /usr/local/bin/gcc-3.4.6 and /usr/bin/gcc-4.6.3 (this is where Ubuntu 12.04 installed GCC on my system).  
 
When I attempt to install gcc-3.4.6 at the aforementioned location, in the "make all" step a bunch of errors get generated due to problems with include files in /usr/include.  
 
To be continued.  But, I will indeed look into your link and read it over.
 
Regards,
Mark

---

### Post by BicyclerBoy on 2012-09-22
As I said I have multiple gcc versions on same install.

Your problem is that much more complicated by trying to compile the compiler..
This is referred to as bootstrapping.
It may not be possible to build gcc-3.4 using a later compiler without code changes.

If you can find the gcc-3.4 as a deb package you could have more luck.
This does not seem likely.

A virtualbox install of 8.04 (or older?) is a tidy soln, you need to make the application completely self contained because any shared libraries will be out-dated/abi changed.

---

