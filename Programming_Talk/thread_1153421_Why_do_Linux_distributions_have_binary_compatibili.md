---
title: "Why do Linux distributions have binary compatibility issues?"
date: 2009-05-08
forum: Programming Talk
---

### Post by amrbekhit on 2009-05-08
Hello all,

As the title asks, why do Linux distributions have issue regarding binary compatibility? Many times when downloading software, I notice that there are several downloads, one for each distribution. Also when downloading not-so-popular software, you usually need to compile from source, presumably because you can't just run the original binary that the author uses. 

As a programmer migrating (happily) from Windows to Ubuntu, I'm interested in finding out how this affects programs I write for Linux and what steps I can take to minimize its effects.

Thanks,

--Amr

---

### Post by Bachstelze on 2009-05-08
Most Linux applications are dynamically compiled. This means that they must load code from shared libraries that provide some functions. Different distributions might have different versions of some libraries installed, or might have them installd in different places. This is why sometimes an executable that was dynamically compiled on one distribution might have problem on another, because it won't find a library at the place or with the version it expects.

Another problem is that different distributions have different package management systems. If the program is distributes as a packages (DEB, RPM, Slackware TGZ, etc.), it will obviously run only on a distribution that uses that packaging format (this is not entirely true, it might run on others, but with a lot of trouble).

A way to avoid the first problem is (if the licence allows) to compile your applications statically, with all the required code contained in the executable.  Most proprietary applications are compiled that way, for example the games NeverWinter Nights, Unreal Tournament 2004 or Quake 4. There are also a few open source applications like Firefox, Thunderbird or FileZilla that you can download as a statically linked executable.

---

### Post by hansdown on 2009-05-08
Hi amrbekhit.

I don't fully understand the differances, but this should help.

[http://www.google.ca/search?q=+binary+compatibility+of+++Linux+distributions++&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=+binary+compatibility+of+++Linux+distributions++&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by amrbekhit on 2009-05-10
Thanks for your replies - looks like it's not really as bad as I thought it was. So if I statically link my libraries, most people should be able to run it just fine.

---

### Post by MadMan2k on 2009-05-10
> **HymnToLife said:**
> 
A way to avoid the first problem is (if the licence allows) to compile your applications statically, with all the required code contained in the executable.  Most proprietary applications are compiled that way, for example the games NeverWinter Nights, Unreal Tournament 2004 or Quake 4. There are also a few open source applications like Firefox, Thunderbird or FileZilla that you can download as a statically linked executable.
at least the mozilla applications do not statically link - instead they include the required libraries in their package.
And if you remove those, they mostly can use the system installed ones.

---

### Post by dwhitney67 on 2009-05-10
> **amrbekhit said:**
> Thanks for your replies - looks like it's not really as bad as I thought it was. So if I statically link my libraries, most people should be able to run it just fine.

Yes, that is correct.  However bear in mind that statically linking the libraries into your app will cause the app's foot-print on the HDD to grow significantly compared to dynamically linking.  But in certain circumstances, this is an acceptable cost.

---

