---
title: "moving files from guest heron to host leopard"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by hellfried on 2008-05-07
i have just installed virtualbox in leopard and am using hardy heron as a guest os. i have downloaded a file in heron and i now want to copy it into leopard. how do i access it?

---

### Post by wolfen69 on 2008-05-07
try a flash drive.

---

### Post by superprash2003 on 2008-05-07
or you could install samba in ubuntu and share via LAN.. [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by mlentink on 2008-05-07
> **wolfen69 said:**
> try a flash drive.

Which won't work if the OP has the OSE of Virtualbox: no USB support.

However, in the Virtualbox application window, you can configure the virtual machine. Setting up shared folders on the host is one of the options in the vm-config. I'd try that.

Pls be aware that I know little of OSX, so I cannot help you there.

---

