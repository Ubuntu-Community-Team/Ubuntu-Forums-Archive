---
title: "32bit or 64bit"
date: 2013-04-05
forum: Recurring Discussions
---

### Post by Dallas2coolio on 2013-04-05
If my Sony notebook has 8GB of ram should I use the 64bit version of Ubuntu? It does say it recommends to use 32bit but is it better to use 64bit on machines that has Win 7 64bit?  Also my Sony has a Intel i3 2.4gHz processor not AMD but I don't know if that makes a difference. I got the first generation of Intel i3 processor so it was made back in 2010.

---

### Post by slickymaster on 2013-04-05
Read this article, although extensive and may seem a bit dense is quite elucidative: [Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1")

---

### Post by Dallas2coolio on 2013-04-05
Well why I was asking is that will the 32bit version detect 8gb of ram or will it only detect 3.5gb even I have 8gb like Windows basicly? Also another question is for my netbook I used the 32bit since it has 2gb of ram but will 64bit work on a netbook also?

---

### Post by QIII on 2013-04-05
Hello!

> Well why I was asking is that will the 32bit version detect 8gb of ram or will it only detect 3.5gb even I have 8gb like Windows basicly?

Without a PAE (Physical Address Extension) kernel, a 32 bit kernel can only address ~4GB (minus however much is reserved by system or hardware) of memory.

 > Also another question is for my netbook I used the 32bit since it has 2gb of ram but will 64bit work on a netbook also?

Whether or not it will run a 64 bit kernel is determined by the architecture of the CPU.  One of my machines runs 64 bit Fedora just fine with 2GB of memory.

The link given is quite explanatory.

Regards!

*Moved to** Recurring Discussions.***

---

### Post by slickymaster on 2013-04-05
QIII is absolutely rigth. Without a PAE (Physical Address Extension) kernel, a 32 bit kernel can only address 4GB. 

If you want to address more than 4 GB you need a 64 bit OS kernel which includes PAE support. PAE increases the address size from 32 bits to 36 bits which means you can address up till 64GB.

---

### Post by deadflowr on 2013-04-05
Go with the 64-bit.
And don't worry 'bout the amd64, it'll run (hopefully:P) intel cpus. It's some sort of trademark thing, or something.

---

### Post by oldos2er on 2013-04-05
> **Dallas2coolio said:**
> If my Sony notebook has 8GB of ram should I use the 64bit version of Ubuntu? It does say it recommends to use 32bit but is it better to use 64bit on machines that has Win 7 64bit?  Also my Sony has a Intel i3 2.4gHz processor not AMD but I don't know if that makes a difference. I got the first generation of Intel i3 processor so it was made back in 2010.

I'd run 64-bit on that even if it "only" had 2GB RAM.

The 32-bit recommendation is a [bug]("https://bugs.launchpad.net/ubuntu-website-content/+bug/585940") that likely won't be fixed anytime soon.

---

### Post by craig10x on 2013-04-05
Beats me why it is still called amd 64 because fact of the matter is the 64 bit version runs on both amd and intels....my last laptop and current one both have intel i3 cores and 64 bit is what i have always run!
It may be that originally, amd was first to have 64 bit support and later followed by intel but for some strange reason, ubuntu never updates that in the information on the iso links....they really SHOULD....probably confuses the heck out of "newbies" ;)

---

### Post by lisati on 2013-04-06
It's called "amd" 64 largely for historical reasons. Apparently AMD were the first to add 64-bit capabilities to their cpus before intel did.

---

### Post by 3rdalbum on 2013-04-06
Calling it "AMD64" does confuse newbies, as does the "32-bit (recommended)" on the Ubuntu website.

What's wrong with "If your computer has a 64-bit CPU, use this image" and "If your computer has a 32-bit CPU, or you don't know your CPU model, use this image". And then name the 64-bit image "x86-64".

---

