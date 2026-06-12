---
title: "Sun Java Studio Creator Installation"
date: 2005-11-13
forum: Programming Talk
---

### Post by ridvan on 2005-11-13
Hi,

I have tried to install Sun Java Studio Creator  ( JSC ) on Breezy.
Sun AppServer8 is needed by JSC but somehow could not be installed.
At first, everthing was looking OK but the deployment was impossible due to missing AppServer8.
I have downloaded AppServer seperately and tried to install:

[FONT="Courier New"]ridvan@p17:~$ Desktop/sjsas_pe-8_1_02_2005Q2-linux-ml.bin
Desktop/sjsas_pe-8_1_02_2005Q2-linux-ml.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory[/FONT]

Yes, you need to install the package 
[FONT="Courier New"]libstdc++2.10-glibc2.2
The GNU stdc++ library[/FONT]

After this, Install JSC again and enjoy it.

Ciao

---

### Post by mlambie on 2005-11-22
Was this the preview version of Java Studio Creator 2, or version 1?

---

### Post by mlambie on 2005-12-08
Hellloooo?

---

### Post by ridvan on 2005-12-12
Yes, it's the Early Access version

---

### Post by Poldi on 2006-01-24
same problem.

this happens with the regular version 1 (2004Q2) as well.

both Netbeans (4.0, 4.1, 5.0RC2) and Java Studio Enterprise work, though.

any ideas?

kind regards,
Carsten

---

### Post by ridvan on 2006-02-04
install libstdc++2.10-glibc2.2

---

### Post by mehaga on 2006-05-03
[QUOTE=ridvan]install libstdc++2.10-glibc2.2[/QUOTE]
Where do I find libstdc++2.10-glibc2.2 for 64bit system?

---

### Post by ridvan on 2006-05-05
No idea!

---

### Post by mehaga on 2006-05-06
Switched back to 32bit :(

---

### Post by ridvan on 2006-05-08
No wait!
Try the following instructions
[http://www.ubuntuforums.org/archive/index.php/t-145506.html](http://www.ubuntuforums.org/archive/index.php/t-145506.html)

I have successfully installed and run on a Dapper Drake flight 7 amd64 (X2 440)

---

### Post by ridvan on 2006-05-08
No wait!
Try the following instructions
[http://www.ubuntuforums.org/archive/index.php/t-145506.html](http://www.ubuntuforums.org/archive/index.php/t-145506.html)

I have successfully installed and run on a Dapper Drake flight 7 amd64 (X2 4400)

---

