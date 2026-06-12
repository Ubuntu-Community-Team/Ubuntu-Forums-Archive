---
title: "Running Soulseek"
date: 2015-09-04
forum: New to Ubuntu
---

### Post by gilles8 on 2015-09-04
Hello,

i've read many threads about running Soulseek on ubuntu but still did not manage it.

I use Ubuntu 14.04 LTS.

I've downloaded SoulseekQt-2015-6-25-32bit.

I've copied it to my Home folder in order to have the right file system to change the permissions. 

I ticked the "allow executing file as program".

If i doule click it, nothing happens.

If i browse through the terminal to the file and use the command line

./SoulseekQt-2015-6-25-32bit

i get 

bash: ./SoulseekQt-2015-6-25-32bit: No such file or directory

although it does exist as using ls command i get

SoulseekQt-2015-6-25-32bit

written in green suggesting it does exist and it is an executale file.


Therefore I don't understand and need help.

Any ideas? 

Thank you.

gilles

---

### Post by ptn107 on 2015-09-04
Same thing here, but the 64 bit version works fine.  Is your system only 32 bit?  I think you have 64 bit Ubuntu.  32 bit programs only run on 64 bit Ubuntu if you have the correct 32 bit libraries installed.  You will need to try the 64 bit version of soulseek or get the 32 bit libraries of these files to get it working:

linux-vdso.so.1
libX11.so.6
libX11-xcb.so.1
libxcb.so.1
libfontconfig.so.1
libfreetype.so.6
libdl.so.2
librt.so.1
libpthread.so.0
libstdc++.so.6
libm.so.6
libgcc_s.so.1
libc.so.6
ld-linux-x86-64.so.2
libXau.so.6
libXdmcp.so.6
libexpat.so.1
libz.so.1
libpng12.so.0

---

### Post by gilles8 on 2015-09-04
yes. as simple as that!

my system is indeed 64 and it does work with the 64 version.

thank you very much.

gilles

---

### Post by mcduck on 2015-09-06
You can also find Nicotine (another Soulseek client) in Ubuntu's repositories. Worked very well the last time I used it.

---

### Post by nafanz on 2016-03-23
Upsetting Nicotine+ that is frozen for several years, as well as other alternative clients. In principle, it is possible to use the basic functions it supports, but alas, in many mp3 files, it does not show bitrate, for me it is an inconvenience.

I really hope that the official client Soulseek will appear in the repositories Ubuntu. Incidentally, I wonder on what basis to enter the program and whether it is possible that the users affect it?

---

