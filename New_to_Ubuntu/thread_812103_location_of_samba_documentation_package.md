---
title: "location of samba documentation package"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by badperson on 2008-05-29
Hi,

I downloaded the samba-doc and samba-doc-pdf packages via synaptic package manager, but I can't find where they're located on my machine. 

the tracker tool comes up emtpy. 
thanks,
bp

---

### Post by RealPSL on 2008-05-29
Synaptic is not generally used for downloads but to install the software by marking it for installation (right click) and then choosing to apply. As for the files from the installation you can easily locate them by running this command at the shell prompt```
dpkg --listfiles samba-doc
```

---

### Post by Oldsoldier2003 on 2008-05-29
> **RealPSL said:**
> Synaptic is not generally used for downloads but to install the software by marking it for installation (right click) and then choosing to apply. As for the files from the installation you can easily locate them by running this command at the shell prompt```
dpkg --listfiles samba-doc
```

though i'm a huge fan of the command line an alternative way is to right click the installed package in synaptic and look at its properties the installed files will tell you what the package installed on your system (and where)

---

### Post by badperson on 2008-05-29
the command line did the trick,
thanks for the help!!
bp :guitar:

---

