---
title: "Which version of libstdc++ is my app linking to?"
date: 2011-09-26
forum: Packaging and Compiling Programs
---

### Post by DavidA2011 on 2011-09-26
Hi
 
I am running Ubuntu 10.04 and am developing a C++ application. I have experience
of Centos but am new to Ubuntu. I am confused about which version of the 
libstdc++ library my application is linking with.
 
I wish to use g++ 4.1.3 to build my app and therefore ran:
 
```
sudo apt-get install gcc-4.1
```
 
so now I see:
 
```

g++ --version
g++ (GCC) 4.1.3 20080704 (prerelease) (Ubuntu 4.1.2-27ubuntu1)

```
 
However, when I build and run my application I see a bug which I believe is due 
to a change in behaviour of libstdc++-v3 at a certain point in its development
cycle. It seems to me that there are various releases of libstdc++-v3 and it is 
critical for me which one I use.
 
Does anyone have knowledge of how I can determine the exact version of libstdc++
that I have installed, and how I can install the version I need?
 
Best regards
 
David

---

### Post by DavidA2011 on 2011-09-27
Here's an update on my issue that will hopefully make it easy to answer.  
 
To recap, I installed g++ 4.1.3 by running:
 
```
sudo apt-get install gcc-4.1
```
 
I then confirmed that g++4.1.3 is the default compiler.
 
I rebuilt my app and ran ldd on it. This shows that the app links to libstdc++.so.6.0.13, which is the gcc-4.4.2 version of libstdc++.
 
Was I wrong to expect apt-get install gcc-4.1 to set-up the correct libstdc++ version?
 
David

---

### Post by SevenMachines on 2011-09-27
gcc uses the system libstdc++ on ubuntu, at least on my computer (except for gcc-snapshot which provides its own), thats the one you automatically link to. If you want to link to a specific libstdc++ you'll want to manually install whatever version of the gcc tools you want to use and use that as your toolchain instead... 
*But* I'd really suggest that if what version of libstdc++ is installed is so critical to your application its much, much more likely that the problem lies within your own code rather than a distributions particular gcc toolchain. It's possible of course, but it tends to transpire in 99.99% of cases that it's not :)

---

### Post by DavidA2011 on 2011-09-27
> **SevenMachines said:**
> gcc uses the system libstdc++ on ubuntu, at least on my computer (except for gcc-snapshot which provides its own), thats the one you automatically link to. If you want to link to a specific libstdc++ you'll want to manually install whatever version of the gcc tools you want to use and use that as your toolchain instead... 
*But* I'd really suggest that if what version of libstdc++ is installed is so critical to your application its much, much more likely that the problem lies within your own code rather than a distributions particular gcc toolchain. It's possible of course, but it tends to transpire in 99.99% of cases that it's not :)
 
Thanks for your reply, I take your point entirely.  However, I came across one of those 0.01% cases where the library behaviour really did change!
 
I can't help thinking that it is a bit misleading that one can do:
 
apt-get install gcc-4.1
 
and end up using a different C++ library to the one shipped with gcc 4.1.

---

### Post by SevenMachines on 2011-09-27
> **DavidA2011 said:**
> I can't help thinking that it is a bit misleading that one can do:
 
apt-get install gcc-4.1
 
and end up using a different C++ library to the one shipped with gcc 4.1.
Possibly, I dont really know enough about the reasons behind it to really comment to be honest. A local version-specific gcc install is easy enough to do if you're sure thats what you want :)

---

### Post by DavidA2011 on 2011-09-27
> **SevenMachines said:**
> Possibly, I dont really know enough about the reasons behind it to really comment to be honest. A local version-specific gcc install is easy enough to do if you're sure thats what you want :)
 
How would you do it exactly please?

---

### Post by SevenMachines on 2011-09-27
Install manually your version of gcc to its own directory somewhere, have a look at 
[http://gcc.gnu.org/install/](http://gcc.gnu.org/install/)
[http://gcc.gnu.org/faq.html#multiple](http://gcc.gnu.org/faq.html#multiple)

---

