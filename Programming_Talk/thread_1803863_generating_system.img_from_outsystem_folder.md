---
title: "generating system.img from out/system folder"
date: 2011-07-14
forum: Programming Talk
---

### Post by difuiv250385 on 2011-07-14
I have the **kernel 2.6.35(for GB)** and on building the source code I am getting **system.img image** **which is in ext4 format**. If I look into the build log I can see that this system.img is getting **generated from MYDROID/out/system**/ folder using the utility **make_ext4fs**.
 
Now I want to use this system.img image in **froyo which has 2.6.32** kernel and does not support ext4. so** I want to get the ext3 format** of the system.img from the MYDROID/out/system/ folder. 
 
For this **I created a shell script** which will generate the system.img in ext3 format.
and I flashed it into phone along with other images from froyo build. and the phone is not booting as it is** not able to mount the /system**. and it **is showing "security error "** on screen.:confused:
 
To verify my shellscript I applied it on the foryo's MYDROID/out/system/ folder and got the system.img in ext3 format. and this **worked fine as the phone mounted** this /system.
 
Please tell me** is there any filesystem dependency on the out/system folder** which is generated during the build time.
 
also **to support ext3 file system what should I do in the kerne**l source code.
 
Thanks for the support.

---

### Post by difuiv250385 on 2011-07-18
Hey guys, I had made a mistake by using the larger block size (using the existing values of ext4 in gb) while generating the image. I changed the block size to 4096 and it started working. 
The shell script i wrote is absolutely fine except the block size. :guitar:

---

