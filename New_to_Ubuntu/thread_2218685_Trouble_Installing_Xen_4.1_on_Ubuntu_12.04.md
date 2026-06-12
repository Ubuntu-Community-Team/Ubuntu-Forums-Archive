---
title: "Trouble Installing Xen 4.1 on Ubuntu 12.04"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by Chas_Seadon on 2014-04-21
I am installing xen hypervisor 4.1 on unbuntu 12.04 

my machine is a dell running Intel® Core™2 Duo CPU E8400 @ 3.00GHz × 2

when I run the command "sudo apt-get install xen-hypervisor-4.1" it seems to want to install the amd processor option.  i need the VT-x option.

any ideas why this is happening? 


chas@ubuntu:~$ sudo apt-get install xen-hypervisor-4.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xen-hypervisor-4.1-amd64' instead of 'xen-hypervisor-4.1'
Suggested packages:
  xen-docs-4.1
The following NEW packages will be installed
  xen-hypervisor-4.1-amd64
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 759 kB of archives.
After this operation, 808 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xen-hypervisor-4.1-amd64
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
chas@ubuntu:~$

---

### Post by Danger_Monkey on 2014-04-21
How about if you search the repositories?  I get them both if I do this:

```

apt-cache search xen

```

xen-hypervisor-4.1-i386 Xen Hypervisor on i386
xen-hypervisor-4.1-amd64 Xen Hypervisor on amd64

---

### Post by Vladlenin5000 on 2014-04-21
Your CPU is 64-bit therefore you need "amd64".

---

### Post by sandyd on 2014-04-21
> **Chas_Seadon said:**
> I am installing xen hypervisor 4.1 on unbuntu 12.04 

my machine is a dell running Intel® Core™2 Duo CPU E8400 @ 3.00GHz × 2

when I run the command "sudo apt-get install xen-hypervisor-4.1" it seems to want to install the amd processor option.  i need the VT-x option.

any ideas why this is happening? 


chas@ubuntu:~$ sudo apt-get install xen-hypervisor-4.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xen-hypervisor-4.1-amd64' instead of 'xen-hypervisor-4.1'
Suggested packages:
  xen-docs-4.1
The following NEW packages will be installed
  xen-hypervisor-4.1-amd64
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 759 kB of archives.
After this operation, 808 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xen-hypervisor-4.1-amd64
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
chas@ubuntu:~$
The naming 'amd64' is not only for amd processors - for all 64 bit processors

---

### Post by Chas_Seadon on 2014-06-14
Excaellent thanks for your help!

---

