---
title: "Ubuntu 12.04 dpkg-buildpackage incremental build for kernel package"
date: 2012-08-22
forum: Packaging and Compiling Programs
---

### Post by humer on 2012-08-22
All,

I installed a pre-built Ubuntu 12.04 LTS image to my OMAP4 Pandaboard through following link-->
[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

And now I was trying to do a native buld for kernel package on the Pandaboard. I installed both image tools and kernel source code by apt-get command and had successfully completed a re-build by 'sudo dpkg-buildpackage -B' command.

The question now is how can I do a incremental build for the kernel since I have only minor changes into a specifi linux kernel driver(one or two source files)? When I excute 'sodo dpkg-buildpackage -B'. This script initial a totally rebuild of whole kernel source and exaust almostly about 4-5 hours. 

I did try an alternative like 'sodo dpkg-buildpackage -B -nc', but this time my code changes in kernel driver folder will never get re-built at all. So my question is how can I do a typical incremental build for my minor code changes without a whole kernel source rebuild?

Thanks in advance for your support on that issue.

---

