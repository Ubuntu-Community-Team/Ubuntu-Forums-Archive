---
title: "Can't access my &quot;desktop&quot;, &quot;home folder&quot; or &quot;filesystem&quot;"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by Smuffytee on 2012-03-27
Hey...am having the same problem but my nautilus command shows:
root@anthony-desktop:~# nautilus --no-desktop
nautilus: /usr/local/MATLAB/MATLAB_Compiler_Runtime/v717/sys/os/glnx86/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libexempi.so.3)
root@anthony-desktop:

Help????????

---

### Post by Smuffytee on 2012-03-27
Hey. I'm kinda new to linux. I'm using Ubuntu 10.04 LTS. I logged in today morning and all the folders and icons on my desktop had disappeared. Nothing happens when i right click on the desktop. To make it worse, none of the items on the "Places" tab work so i cant access anything using the GUI...not my home folder, file system...nothing!

Help!!!!!

---

### Post by sanjibsinha on 2012-03-27
Open the terminal by CTR/ALT T and then type 
```
ls -l 
```
so that you will see the Desktop there in the list below. next type 
```
cd Desktop
```
So that you can see what is there in your desktop.
Best Wishes.

---

### Post by audiomick on 2012-03-27
Have you tried a restart? 

Not very helpful, I know, but that is the first thing to try. I have very very occasionally had a similar problem. A restart fixed it.

---

### Post by mörgæs on 2012-03-27
Please don't post the same question in multiple threads. Merged.

---

