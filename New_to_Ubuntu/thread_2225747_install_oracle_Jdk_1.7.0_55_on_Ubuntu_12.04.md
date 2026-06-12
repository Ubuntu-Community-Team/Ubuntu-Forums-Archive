---
title: "install oracle Jdk 1.7.0_55 on Ubuntu 12.04"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by indi on 2014-05-23
Hi,

I am running Ubunti 12.04 on Oracle VirtualBox. I installed Oracle JDK 1.7, when I issue command java -version it says
"java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directoy"

I googled but helpless. Please help!

Thank you
Indi

---

### Post by indi on 2014-05-23
Hi,

I solved this by executing command,

export LD_LIBRARY_PATH=export LD_LIBRARY_PATH=<path to installation>/jre/lib/i386/jli/

Indi

---

### Post by hsaltiel on 2014-05-23
Hi Indi,

Try to include this in your profile:

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<path to installation>/jre/lib/i386/jli/

...if this is the path to your libs.
Best regards,

HeCSa.

---

### Post by indi on 2014-05-23
Hi HeCSa,

I added that line to /etc/profile but i get the old error unless i ran the export command in terminal. But I know with terminal, i have to run export line every time I open a new terminal. How to solve this

Kind Regards,
Indi

---

### Post by indi on 2014-05-23
Hi,

I solved by adding .conf file with library path to following directory "/etc/ld.so.conf.d/".

This link was useful:[http://www.linuxforums.org/forum/ubuntu-linux/176983-solved-cannot-set-ld_library_path-profile-etc-profile.html](http://www.linuxforums.org/forum/ubuntu-linux/176983-solved-cannot-set-ld_library_path-profile-etc-profile.html)

Regards,
Indi

---

