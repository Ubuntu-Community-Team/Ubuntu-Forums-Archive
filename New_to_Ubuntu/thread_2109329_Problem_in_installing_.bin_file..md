---
title: "Problem in installing .bin file."
date: 2013-01-27
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2013-01-27
Hi,

I downloaded AdbeRdr9.5.3-1_i486linux_enu.bin file from acrobat.com.

Then I used command sudo chmod a+x AdbeRdr9.5.3-1_i486linux_enu.bin

and now when I use ./AdbeRdr9.5.3-1_i486linux_enu.bin 

I get error message bash: ./AdbeRdr9.5.3-1_i486linux_enu.bin: No such file or directory

jeet@jeet-laptop:~/Downloads$ ls A*

shows AdbeRdr9.5.3-1_i486linux_enu.bin in green color. 

I am using ubuntu 11.10. Am I doing anything wrong?

---

### Post by Cheesemill on 2013-01-27
Are you running the 64-bit version of Ubuntu by any chance?

---

### Post by sujitrjadhav on 2013-01-27
Yes it is 64 bit version. Did I downloaded wrong file? One which is for 32 bit? I checked [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/) once again. It dose not have option to select 32 bit or 64 bit.

---

### Post by Cheesemill on 2013-01-27
There isn't a 64-bit version of Adobe Reader available for Linux.

You can run 32-bit programs on a 64-bit OS, but you need to install the package ia32-libs first.

---

### Post by sujitrjadhav on 2013-01-27
Ok. I have started installation. Requires 15 Min. Hope it will work.

---

### Post by sujitrjadhav on 2013-01-27
It worked. Thanks very much for help.

---

