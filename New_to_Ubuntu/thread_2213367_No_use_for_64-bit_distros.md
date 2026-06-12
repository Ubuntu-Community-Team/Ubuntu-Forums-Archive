---
title: "No use for 64-bit distros?"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by Dr. McKay on 2014-03-26
Found this today :
[http://linuxfonts.narod.ru/best-linux-distro-this-year.html](http://linuxfonts.narod.ru/best-linux-distro-this-year.html)

I quote :
"It's not necessary to install a 64bit Linux distro - all modern Linux'es support up to 64GB of RAM in 32bit mode. In fact I'm against installing a 64bit distro because if you are going to use Skype or Wine you will end up wasting your RAM and CPU cycles since you'll be running two copies of system libraries."

Anyone care to explain ?

---

### Post by tgalati4 on 2014-03-26
You will lose some RAM with 64-bit because the pointer addresses are double in size and there are alot more of them.  You will get ~10% performance improvement in certain operations with 64-bit.  With Windows binaries, like Skype, you will be running those in a 32-bit compatible mode, so yes, you will have 32-bit libraries loaded--but only when needed.  WINE would be similar because many Windows programs are 32-bit.  

Do you notice to performance hit in a modern machine?  I doubt it.  If you are loading onto a thin client, then perhaps the 32-bit distro makes sense.

---

### Post by oldfred on 2014-03-26
While not Skype:
 32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

      
 Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by Dr. McKay on 2014-03-26
Well, I'm running Linux on a desktop and a laptop.
After trying out several distros (Mint Cinnamon and Mate, Opensuse KDE, Netrunner KDE and Ubuntu Unity), I finally decided on Xubuntu because it's nice and snappy.
My desktop is a Core2quad 2.4Ghz with 8Gb of RAM and a nVidia 9800 card. The laptop is a dual core pentium with 4Gb of RAM and intel graphics.

So, which version is best for either the desktop or the laptop, 32-bit or 64-bit Xubuntu ?

---

### Post by sudodus on 2014-03-26
There is no exact and definite answer to that question. It depends on what programs are your main programs and how you use your computer. I suggest that you try both 32-bit and 64-bit for a week or so, maybe perform some tests and decide what is best for you after that.

And please share the results with us at the Ubuntu Forums :-)

---

### Post by grahammechanical on 2014-03-26
Over the last year or so Ubuntu has introduced what the developers call mulitarch libraries. As I understand it these can be used by either 32bit programs or 64bit programs and in this way reduce the need for 2 sets of libraries. Certain user tasks will benefit greatly from being run in a 64bit program. But you will not be able to run a 64 bit version of a program on a 32 bit OS. Then there are those programs that will not benefit the user that much even if they were rewritten as 64 bit programs.

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

Personally, I much prefer an OS written specifically for the architecture of the CPU I am using rather than one that has been written for another CPU architecture and has then been modified to make use of certain features of the other CPU architecture. 

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

Regards.

---

### Post by Dr. McKay on 2014-03-26
Guess I'll be running 64-bit Xubuntu on both machines, then.
Up till now, I've only used 32-bit distros to run in Virtualbox because I only assigned 2Gb of RAM to them, but apparently, there's no reason to run 32-bit linux on my two 64-bit capable machines...

---

### Post by whitesmith on 2014-03-26
> **Dr. McKay said:**
> Found this today :
[http://linuxfonts.narod.ru/best-linux-distro-this-year.html](http://linuxfonts.narod.ru/best-linux-distro-this-year.html)

I quote :
"It's not necessary to install a 64bit Linux distro - all modern Linux'es support up to 64GB of RAM in 32bit mode. In fact I'm against installing a 64bit distro because if you are going to use Skype or Wine you will end up wasting your RAM and CPU cycles since you'll be running two copies of system libraries."

Anyone care to explain ?There are among us those with more than 64 GB of installed RAM. Remember that the laws of physics limit 32-bit addressing to 2**32 (4294967296 bytes or 4 GB), while 64-bit allows 17179869184 GB or 16384 PB). That's an enormous increase. No, Joe Six Pack doesn't need it, but a lot of scientific users do.

---

### Post by Impavidus on 2014-03-26
Furthermore, PAE allows the OS to use up to 64GiB memory, but still limits each application to 4GiB. So, if you run lots of small applications PAE helps, but if you run one or two big ones PAE doesn't get you far. I'd say, as soon as you get over 3GiB memory, use 64 bit.

1.8×10[SUP]19[/SUP] bytes, I wonder how big (physically) such a memory module would be...
Edit: Actually, 64 bit systems don't use all 64 bits for addressing.

---

### Post by 3rdalbum on 2014-03-26
64-bit kernels usually have more modern optimizations turned on because they don't need to support CPUs that predate the Athlon 64 and Core 2.

As an extended consequence of that, 64-bit distros also use security features native to newer CPUs, and such features are either not available or slowly emulated in the 32-bit distro.

---

