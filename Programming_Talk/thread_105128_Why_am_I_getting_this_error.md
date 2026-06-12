---
title: "Why am I getting this error???"
date: 2005-12-17
forum: Programming Talk
---

### Post by kudu on 2005-12-17
./basic2d: error while loading shared libraries: libclanApp-0.8.so.1: cannot open shared object file: No such file or directory


I use pkgconfig which is pointing to the correct lib folder, i.e. /usr/local/lib.

I checked the permissions and everybody should be able to read and execute the lib files. The program compiled fine but when I try to run it I get the above error message. Any ideas ?

Thanks as always!

---

### Post by claydoh on 2005-12-17
Do you have[ libclanlib-dev]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=breezy&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=libclan&searchon=names") , etc installed?
Those will be in /usr/lib and /usr/include when installed, so when running configure, use "./configure --prefix=/usr" then everything will be found properly.

---

### Post by kudu on 2005-12-17
I'm not using the repo version of ClanLib, I'm using the latest...0.8.0-RC1.

Everything is in /usr/local/lib or /usr/local/include. The pkg-config prefixes point to /usr/local so seems in order. However I don't have an ld.so.conf file in /etc. How do I create one ?

Thanks for replying.  :)

---

### Post by claydoh on 2005-12-17
Dunno if Ubuntu/debian use ld, I would suggest rebuilding your libs with the "--prefix=/usr", also I am not sure of the correct syntax, but you can also "EXPORT FOOLIBDIR=/usr/local/lib" before running configure.

---

### Post by toojays on 2005-12-17
I disagree with claydoh's solution, because I don't like the idea of having non-apt-managed files in the /usr tree. Better to have them in /usr/local.

You can just make a new file /etc/ld.so.conf, and put the line "/usr/local/lib" in it. Then run "sudo ldconfig". See the ldconfig man page for more info.

---

### Post by kudu on 2005-12-18
I made an ld.so.conf with /usr/local/lib/ in it and ran ldconfig. That did the trick.

Thanks for your help fellas! I really appreciate it. :))

---

### Post by claydoh on 2005-12-18
[quote=toojays]I disagree with claydoh's solution, because I don't like the idea of having non-apt-managed files in the /usr tree. Better to have them in /usr/local.
[/quote]

You can use checkinstall and have both :)

---

