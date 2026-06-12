---
title: "Installing Gnome 3.8 on Ubuntu crashes"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by Houmie on 2013-06-21
Hey guys,

I just followed these instructions [http://www.techrepublic.com/blog/opensource/how-to-install-gnome-38-on-ubuntu/4343](http://www.techrepublic.com/blog/opensource/how-to-install-gnome-38-on-ubuntu/4343) on a fresh installed Ubuntu 13.04 and it crashed with the following error message:

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-25-generic
cp: cannot stat ‘/module-files.d/libpango1.0-0.modules’: No such file or directory
cp: cannot stat ‘/modules/pango-basic-fc.so’: No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-25-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ca-certificates ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
done.
done.
Processing triggers for ureadahead ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any idea what this is?

Many Thanks,
Hooman

---

