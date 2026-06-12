---
title: "Add/Remove programs is not working (Ubuntu Noob)"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by jimmynewtron on 2008-06-08
Hi, I'm new to Ubuntu so any assistance would really be appreciated. I am getting an error when using the add/remove feature to install programs. I do have an internet connection working and the add/remove was working for me previously.

Error when installing amsn:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.16-4ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.16-4ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltk-defaults/tcl_8.4.16-1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltk-defaults/tcl_8.4.16-1_all.deb)
  404 Not Found


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcl8.5/tcl8.5_8.5.0-2ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcl8.5/tcl8.5_8.5.0-2ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2_2.2.10-dfsg1-5_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2_2.2.10-dfsg1-5_i386.deb)
  404 Not Found


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_i386.deb)
  404 Not Found


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tk8.5/tk8.5_8.5.0-3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/t/tk8.5/tk8.5_8.5.0-3_i386.deb)
  404 Not Found


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97+final-0ubuntu5_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97+final-0ubuntu5_i386.deb)
  404 Not Found

Thanks for your help.

---

### Post by OldTimeTech on 2008-06-08
Check this out....might have your answer

[http://ubuntuforums.org/showthread.php?t=581725](http://ubuntuforums.org/showthread.php?t=581725)

---

### Post by mikewhatever on 2008-06-08
It looks like an off line repository, nothing's wrong with your system. For some reason, Canadian repositories get down quite often. You can either wait or choose a different server from System>Admin>Software Sources.

---

### Post by drs305 on 2008-06-08
In synaptic, try Settings > Repositories, Download from: > Other, Select Best Server. Choose Server, Close. After doing this try running your commands again.

---

