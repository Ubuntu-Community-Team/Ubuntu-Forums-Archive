---
title: "rtorrent Issues"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by pijiu on 2008-05-21
I tried setting up rtorrent on 8.04 but it tells me:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

So I ran that and got..

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

```

Can anyone help me?

---

### Post by talsemgeest on 2008-05-22
Try opening synaptic, updating, then closing.

Then see if the problem is still happening.

Hope this helps :)

---

### Post by pijiu on 2008-05-22
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

This is what it gives me.

---

### Post by hyper_ch on 2008-05-22
or better: install rTorrent from SVN (rtorrent is one of the few appz I prefer compiling myself)

---

### Post by pijiu on 2008-05-22
and how would I do that?

---

### Post by hyper_ch on 2008-05-22
[http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron)

---

### Post by pijiu on 2008-05-22
How can I do that when it leads me straight back here:

> **pijiu said:**
> I tried setting up rtorrent on 8.04 but it tells me:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

So I ran that and got..

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

```

Can anyone help me?

---

### Post by talsemgeest on 2008-05-22
What about updating your sources.lst?

Go system> administration> software sources, then change something go ok.

---

### Post by philinux on 2008-05-22
sudo dpkg --configure -a

---

### Post by pijiu on 2008-05-22
> **philinux said:**
> sudo dpkg --configure -a

This gives me the error I listed in my first post.

> **talsemgeest said:**
> What about updating your sources.lst?

Go system> administration> software sources, then change something go ok.

I can't seem to be able to do this as this version of ubuntu is on a dedicated server which I access through NX Cient. The 'Software Sources' is not in the administration list.

---

