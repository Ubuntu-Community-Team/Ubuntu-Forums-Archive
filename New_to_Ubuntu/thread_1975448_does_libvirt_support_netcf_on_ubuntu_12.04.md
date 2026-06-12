---
title: "does libvirt support netcf on ubuntu 12.04?"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by zhou jianming on 2012-05-07
Hi,
I am trying to build libvirt 0.9.10 on ubuntu 12.04. After installing libnetcf-dev and libnetcf1 packages, I have run shell commands './configure --prefex=/usr --with-netcf; make; make install' to confiure, build, and install this package, these commands work well.

I have connected  KVM hypervisor properly. But  when runing command 'virsh iface-list --all' I get:
  error: Failed to list active interfaces
  error: this function is not supported by the connection driver: virConnectionNumOfInterfaces.

I don't find the way to resolve above question. Who can help me.

regard
zhou

---

