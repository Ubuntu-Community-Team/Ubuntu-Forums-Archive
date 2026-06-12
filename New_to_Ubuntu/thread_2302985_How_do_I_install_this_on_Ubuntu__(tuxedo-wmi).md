---
title: "How do I install this on Ubuntu ? (tuxedo-wmi)"
date: 2015-11-15
forum: New to Ubuntu
---

### Post by Sorawit_Kongnurat on 2015-11-15
I want to disable my keyboard back-lighting and the way to do that is by installing this file: [https://github.com/fleaplus/tuxedo-wmi](https://github.com/fleaplus/tuxedo-wmi). However, I have tried to do that but maybe something is wrong and I just couldn't get it to work. On the other hand on Arch Linux I was able to install this file from their aur and disable my keyboard back-lighting. I want to dual boot and Ubuntu and Arch Linux but before I commit to doing that I want to be sure that this work. 

(I truly believe that I did something wrong during the installation)

---

### Post by Vladlenin5000 on 2015-11-15
The site you linked contains instructions. If you followed them then please explain what and/or where it went wrong before anything else.

---

### Post by Sorawit_Kongnurat on 2015-11-15
So first I gitclone the file out. Then I went into the src folder to execute make. After that I don't know what to do. Do I have to execute sudo make install afterward? If yes, is that it?

---

### Post by Sorawit_Kongnurat on 2015-11-15
This is what happen after execute make and sudo make install.

---

### Post by Sorawit_Kongnurat on 2015-11-16
After some reading on the internet I found out that I should install this into the module. So what I should be doing is git clone then make inside the directory. After that I should modprobe module_name. Is that what I should be doing to install this file and get my keyboard working.

---

