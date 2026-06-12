---
title: "Kernel compilation error"
date: 2011-11-06
forum: Packaging and Compiling Programs
---

### Post by mudasir on 2011-11-06
Hi,

I have been trying to compile a custom kernel for Ubuntu 10.04.2 LTS. I am trying to compile Kernel v2.6.39 but I keep getting the same error.
Error is this.
> dpkg-gencontrol: error: package linux-image-2.6.39-custom not in control info
make[2]: *** [debian/stamp/binary/linux-image-2.6.39-custom] Error 255
make[2]: Leaving directory `/usr/src/linux-2.6.39'
make[1]: *** [debian/stamp/binary/pre-linux-image-2.6.39-custom] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.39'
make: *** [kernel_image] Error 2


I did try the following method [http://ubuntuforums.org/showpost.php?p=9638461&postcount=1488](http://ubuntuforums.org/showpost.php?p=9638461&postcount=1488)
but still no help.

Can anyone assist me in solving this issue, or provide me a proper working page for compiling latest kernel for Ubuntu 10.04.02 LTS.

I am trying to compile kernel to get optimum CPU and RAM performance.

Looking forward for a positive response.

---

### Post by Ad@m on 2011-11-06
Are you using a kernel source from kernel.org?

[http://linuxtweaking.blogspot.com/2011/02/how-to-compile-kernel-from-kernelorg-in.html](http://linuxtweaking.blogspot.com/2011/02/how-to-compile-kernel-from-kernelorg-in.html)

---

### Post by mudasir on 2011-11-06
Hi,

Thanks for your prompt reply.

Yes I am using source from kernel.org. Same source compiles fine in CentOS and is working great giving me the exact performance boost that i expected. 
But its giving me errors in Ubuntu, I will follow this link now and will update the results here.

But by the look at the link, I have followed almost the same steps.

---

### Post by howefield on 2011-11-06
Thread moved to "*Packaging and Compiling Programs*"

---

### Post by mudasir on 2011-11-07
Hi,

I tried the link that you posted, and it works. I guess it was fakeroot that did the trick.

Thanks for the assistance.

---

