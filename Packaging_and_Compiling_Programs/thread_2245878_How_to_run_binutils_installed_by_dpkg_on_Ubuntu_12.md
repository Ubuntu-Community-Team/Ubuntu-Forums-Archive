---
title: "How to run binutils installed by dpkg on Ubuntu 12.04 LTS"
date: 2014-09-26
forum: Packaging and Compiling Programs
---

### Post by shahin on 2014-09-26
I know I have binutils installed on my Ubuntu VM, and can verify it with:
```
sansari@ubuntu:/usr/share/bug$ ld -v 
GNU ld (GNU Binutils for Ubuntu) 2.22
sansari@ubuntu:/usr/share/bug$ 

```

I installed it a while back. Now I am trying to build for a different platform, and I should be able to use the same one I installed. Right? Basically I am trying to issue this command: 

```
../binutils-2.11.2/configure --target=$TARGET --prefix=$PREFIX
```

from this url: [http://neptune.billgatliff.com/gettingStarted.html]("http://neptune.billgatliff.com/gettingStarted.html")

But I don't know where the executable for binutils is. I found this site after searching online: [http://askubuntu.com/questions/176679/how-to-find-the-executable-file-of-an-app-if-whereis-is-not-showing-it]("http://askubuntu.com/questions/176679/how-to-find-the-executable-file-of-an-app-if-whereis-is-not-showing-it")

And ran locate, and I get a huge output. None of the folders seems to be the executable that I am looking for.

---

### Post by oldos2er on 2014-09-26
Moved to Packaging & Compiling Programs.

---

### Post by steeldriver on 2014-09-27
I don't really understand your question - there is no "executable for binutils", it is a *collection* of executables (ld, ar, objdump and so on)

What are you trying to do, exactly? Re-configure a previously-downloaded binutils source package in order to cross-compile binutils for a different platform?

---

### Post by shahin on 2014-09-27
Yes. I am trying to compile another source. Actually when I initially created this build environment for the android platform, I used the toolchain to compile the source. Now I think I should be able to use the same tools to compile another source. But is that the right way to approach this? Should I really create another build environment? 

I was mistaken about looking for the executable. I was looking at this command: 
```
../binutils-2.11.2/configure --target=$TARGET --prefix=$PREFIX
```
I now see that I was mistaken.

You see, last time I created the build environment, I followed procedures. I learned a lot, but I need to learn more about toolchain and how I can use it to compile embeded systems code. If you have any suggestions on how I can learn more about this, such as urls, development boards, etc. Please let me know.

Thanks

---

