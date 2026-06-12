---
title: "How to get K3b to Burn mp3s as a Audio CD For AMD64/x86/PPC"
date: 2005-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by kunjan1029 on 2005-03-29
How to get K3b to Burn mp3s as a Audio CD
[indent]1. Download the latest **k3b** and **k3b-libs** package from the following location:[/indent][indent][indent]For AMD64: [http://ftp.tiscali.nl/debian-pure64/pool/main/k/k3b/]("http://ftp.tiscali.nl/debian-pure64/pool/main/k/k3b/")
  [/indent][indent]For x86/PPC: 
[http://ftp.tiscali.nl/debian/pool/main/k/k3b/]("http://ftp.tiscali.nl/debian/pool/main/k/k3b/")
  [/indent]2. Open the package in your favourite Archive Manager/Midnight Commander and extract the following files:
  
From k3b:
k3bmaddecoder.plugin (in /usr/share/apps/k3b/plugins/)
  
From k3b-libs:
libk3bmaddecoder.la (in /usr/lib/kde3/)
libk3bmaddecoder.so (in /usr/lib/kde3/)
  
3. Login under su/sudo
4. Copy k3bmaddecoder.plugin to /usr/share/apps/k3b/plugins/
and copy the other two files to /usr/lib/kde3/
  
5. Restart K3b and enjoy!!
  
  
  
[/indent]This way you dont have to mess with alien or anything!

Have fun!

---

### Post by raum13 on 2005-03-31
Hi 

the deb way to go is 

apt-get source k3b
apt-get build-dep k3b
apt-get install libmad0 libmad0-dev
cd k3b-0.11.23
dpkg-buildpackage -tc 
dpkg -i ../k3b_0.11.23-0ubuntu1_i386.deb ../k3blibs_0.11.23-0ubuntu1_i386.deb


with this you get a k3b which has 

/usr/share/apps/k3b/plugins/k3bmaddecoder.plugin
/usr/lib/kde3/libk3bmaddecoder.la
/usr/lib/kde3/libk3bmaddecoder.so

included. these are only included if during the compile the file mad.h is found. And as libmad0-dev is not required to compile k3b it is not downloaded during the "apt-get build-dep k3b" without the extra install you get a mp3 free k3b. (politcal reasons or just forgotten ?) 

cu r13

---

### Post by kunjan1029 on 2005-03-31
Hmm thats a good way to, however I have never built an apt-package from source, never needed to... but this is good. will try it to learn something new ;)

---

### Post by Randabis on 2005-03-31
I have created k3b and k3blibs packages with mp3 audio cd burning support for x86 hoary systems. If anyone is interested in them, send me an e-mail at [email]randabis@gmail.com[/email] and I'll send you the .debs.

---

### Post by axmanak on 2005-04-01
[QUOTE=kunjan1029]How to get K3b to Burn mp3s as a Audio CD
[indent]1. Download the latest **k3b** and **k3b-libs** package from the following location:[/indent][indent][indent]For AMD64: [http://ftp.tiscali.nl/debian-pure64/pool/main/k/k3b/]("http://ftp.tiscali.nl/debian-pure64/pool/main/k/k3b/")
  [/indent][indent]For x86/PPC: 
[http://ftp.tiscali.nl/debian/pool/main/k/k3b/]("http://ftp.tiscali.nl/debian/pool/main/k/k3b/")
  [/indent]2. Open the package in your favourite Archive Manager/Midnight Commander and extract the following files:
  
From k3b:
k3bmaddecoder.plugin (in /usr/share/apps/k3b/plugins/)
  
From k3b-libs:
libk3bmaddecoder.la (in /usr/lib/kde3/)
libk3bmaddecoder.so (in /usr/lib/kde3/)
  
3. Login under su/sudo
4. Copy k3bmaddecoder.plugin to /usr/share/apps/k3b/plugins/
and copy the other two files to /usr/lib/kde3/
  
5. Restart K3b and enjoy!!
  
  
  
[/indent]This way you dont have to mess with alien or anything!

Have fun![/QUOTE]
 apt-get build-dep k3b doesn't work for me. Dependencies cannot be built.

---

### Post by kunjan1029 on 2005-04-02
your system is missing dependencies to k3b. apt should have shown you a list of missing packages install them first

---

