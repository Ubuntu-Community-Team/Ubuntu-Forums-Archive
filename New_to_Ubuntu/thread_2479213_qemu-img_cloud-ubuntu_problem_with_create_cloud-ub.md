---
title: "qemu-img cloud-ubuntu problem with create cloud-ubuntu.img"
date: 2022-09-18
forum: New to Ubuntu
---

### Post by matos777 on 2022-09-18
[SIZE=4]Hay my friends maybe someone knows  how to resolve this  I have Ubuntu 22.04 jellyfish installed qemu-kvm  I have two virtual machine on it  linux 16.04 and  linux 18 server  for training course 
And now i want to install from ubuntu 22.04 cionsole the cloud-ubuntu based on xenial linux 16.04. I  cannot obey this  [COLOR=#ff0000][B]sudo qemu-img create -f qcow2 -b xenial-server-cloudimg-amd64-disk1.qcow2  cloud-ubuntu.img
qemu-img: cloud-ubuntu.img: Backing file specified without backing format
Detected format of qcow2 .[/B][/COLOR] 
Nothing helps even -F -o rebase  I need to create snapshoot  cloud-image to start instalation with  password and user     everything in linux 22.04 is updated
[/SIZE]
[SIZE=3][B]-rw-r--r-- 1 libvirt-qemu kvm    544735232 Sep 18 16:36 xenial-server-cloudimg-amd64-disk1.img
-rw-r--r-- 1 root         root  1021772136 Sep 16 19:33 xenial-server-cloudimg-amd64-disk1.qcow2
user@user-Aspire-7750G:/var/lib/libvirt/images$ sudo qemu-img create -f qcow2 -b xenial-server-cloudimg-amd64-disk1.qcow2  cloud-ubuntu.img
qemu-img: cloud-ubuntu.img: Backing file specified without backing format
Detected format of qcow2.user@user-Aspire-7750G:/var/lib/libvirt/images$ 

I trying something else installed  xenial-server-cloudimg-amd64-disk1.img  with image not converted from the page   
[COLOR=#ff0000]edited vim config [/COLOR]
#cloud-config
runcmd:
  - [ apt-get, -y, remove, cloud-init ]
password: ubuntu
chpasswd: { expire: False }
ssh_pwauth: True
~                         
and next inserted it to the[COLOR=#ff0000] sudo cloud-localds config.img config

[/COLOR]But ubuntu default password did not work and cannot log in to the system 

If someone knows the problem please help 
[/B][/SIZE]

---

### Post by TheFu on 2022-09-18
Support for 16.04 LTS ended in 2021.  Please move to a supported release.

Support for 18.04 LTS  ends in April, so that would not be a recommended release to perform new installs and certainly not to host VMs.

20.04  Server LTS  support is good until April 2025. It is stable and well documented. This is what I install new Ubuntu Servers using.

22.04 Server LTS  is fairly new still and has some issues, but it will retain support until 2027.  I don't have any production systems on it yet, but will probably move some stock services to it in the next 6 months.  Things like our VPN, but not any webapps.  There are many problems with the desktop versions of 22.04 still which break my workflows, so those will take longer to consider moving into.

Getting on supported releases is step 1. Nothing else really matters, until that is addressed. Sorry.

Why not use libvirt tools like virsh or virt-manager?  They handle these issues nicely.

Formatting for these forums:
BTW, please use standard, default, fonts here.  A little bold or colors to highlight a few words is fine.  Also, when posting terminal output, please, please, please, use forum code-tags.  My signature has a link which explains that.

---

### Post by matos777 on 2022-09-19
[SIZE=2][FONT=arial]I will try install ubuntu 20.04 and I will install qemu-kvm and I will download and install cloud image through  cmd terminal
[/FONT][/SIZE][FONT=arial][/FONT][SIZE=2][FONT=arial]I need to do everything through the command console because I learn during the course and through virt manager I somehow fail because I can't set the password there too, I install it without the possibility of setting a password I am a beginner, I go on a hard way to get to something, I will inform you about the progress[/FONT][/SIZE]

---

