---
title: "gcc-3.4 installed on ubuntu 13.04 but not found"
date: 2013-08-16
forum: Packaging and Compiling Programs
---

### Post by ghgh21 on 2013-08-16
Hello,
I have installed gcc-3.4 on Ubuntu 13.04 in order to be able to run other programs functioning with this gcc version. But after installation, when I type " gcc --v",  I have this message "The program 'gcc' can be found in the following packages:* gcc * pentium-builder
Could you please help me solving this problem?
Thank you

---

### Post by JRV on 2013-08-16
Try: ```
sudo apt-get install build-essential
```

---

### Post by ghgh21 on 2013-08-16
Thanks for the reply,
This commands installs also gcc 4.7.3 and when I type gcc --version I obtain gcc-4.7 however I want gcc-3.4.

---

### Post by ghgh21 on 2013-08-17
Hello,
I have reinstalled gcc-3.4 and when I type "which gcc" I obtain "/usr/bin/gcc" and when I type "gcc --version" I have "gcc (GCC) 3.4.6 (Ubuntu 3.4.6-6ubuntu5)".
However I still have a problem with ./configure. I still have " checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables."
Any suggestions please?
Thanks

---

### Post by eu-h on 2013-09-11
Try

ln -s /usr/bin/gcc /bin/gcc

---

