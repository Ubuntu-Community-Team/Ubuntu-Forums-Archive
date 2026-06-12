---
title: "&lt;stdio.h&gt; not found"
date: 2008-09-02
forum: Packaging and Compiling Programs
---

### Post by nsa_tanay on 2008-09-02
Dear all,
I was reading through many previous threads related to the above title. But could not make a head way. I wrote a 'c' program , and getting a compilation error that 'stdio.h' is not there.

I also tried all the 'sudo apt-get ....', 'sudo -f ...' stuffs and but it didn't help.

Can some one please tell me how to install all the necessary header files needed to compile a 'c' program. Specially the libc-6 package .


Thanks,
Tanay

---

### Post by mujambee on 2008-09-02
I assume you are trying to write and compile a c program to run in your linux box.

stdio.h can be located in 64 packages, but the one you'll need is libc-dev. So

```

sudo apt-get install libc-dev

```

should do the trick.

However, if you have a c compiler installed you should have it, so I recommend

```

sudo apt-get install gcc-4.2

```

instead.

---

### Post by Joeb454 on 2008-09-03
A simple ```
sudo apt-get install build-essential
``` should do the trick. Alternatively, while running Ubuntu, you should be able to click the link below to install ;)

[build-essential]("apt://build-essential")

---

### Post by nsa_tanay on 2008-09-03
Hi, 
Thanks for your reply. I tried 'sudo apt-get install libc-dev'
then got the following o/p :--
"
Reading Package List ... Done
Building dependency tree
Reading state information.... Done
Package libc-dev is not available, but is referred to by another package. This may mean that the package is missing or is only available from another source.
E: Package libc-dev has no installation candidate

"


Please advice me what to do. 

[Also my lap top is not connected to internet/network. But I can transfer files through USB Drive from another Windows machine which is connected to Internet.]

---

### Post by nsa_tanay on 2008-09-03
Hi,
I also tried 'sudo apt-get install build-essential'
then got the following o/p :--
"
Reading Package List ... Done
Building dependency tree
Reading state information.... Done
E:Couldn't find package build-essential

"

Please tell me what to do.

---

### Post by snova on 2008-09-03
It looks like apt doesn't know where the package is.

All I can suggest is to go to packages.ubuntu.com from the Windows machine and search for libc-dev (and build-essential if you want it), and download them that way. Then use dpkg to install them (dpkg works directly with package files, instead of with repositories):

```
sudo dpkg --install downloaded_package_file.deb
```

If it complains about missing dependencies, download and install those first, and then try again.

I have the repositories on several DVD's, which is helpful because I don't have an internet connection either. You might want to look into buying a set. You also might consider waiting two months for the next release, if you can go that long.

---

### Post by WW on 2008-09-04
> **nsa_tanay said:**
> 
[Also my lap top is not connected to internet/network. But I can transfer files through USB Drive from another Windows machine which is connected to Internet.]
If you still have your installation CD you can install build-essential from there.  (I don't recall where, but somewhere in the forum or in the Ubuntu wiki you can find instructions for enabling the CD repository.)

---

