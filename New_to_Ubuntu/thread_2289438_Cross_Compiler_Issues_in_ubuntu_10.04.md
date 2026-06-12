---
title: "Cross Compiler Issues in ubuntu 10.04"
date: 2015-08-04
forum: New to Ubuntu
---

### Post by Kishore_Poojari on 2015-08-04
Hello All ,
   I have installed Ubuntu 10.04 LTS on my host development system , To run the Bootstrap code (From Atmel vendor) for ARM processor. I installed ARM Cross Compiler using command 
sudo apt-get install gcc-arm-linux-gnueabi

and set the environment variable to 
export CROSS_COMPILE=arm-linux-gnueabi- 

And I verified the value of  CROSS_COMPILE  by command printenv.

But when I try make Bootstrap image (using make cmd) , still getting Environment variable CROSS_COMPILE is not assigned Error.

Whether along with cmd "export CROSS_COMPILE=arm-linux-gnueabi-" any file has to modified manually ....?

May I know what is the actual cause for this problem........?

Regards,
Kishore P

---

### Post by TheFu on 2015-08-04
Support for 10.04 ended. We cannot help. Sorry.
Please installed a supported release. 14.04 LTS is recommended and supported until at least April 2019.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - you probably do not want 15.04 - support is just a few more months.

---

### Post by Kishore_Poojari on 2015-08-04
Same Problem is their in 12.04 LTS and 14.04 LTS.

Regards,
Kishore P

---

### Post by TheFu on 2015-08-04
Do these instructions help?
[http://gumstix.org/basic-cross-compilation.html](http://gumstix.org/basic-cross-compilation.html)

Please copy/paste the exact commands and the exact, relevant, output produced.
A link to the Atmel instructions/packages would be nice too.

---

### Post by Kishore_Poojari on 2015-08-04
thanks,

---

