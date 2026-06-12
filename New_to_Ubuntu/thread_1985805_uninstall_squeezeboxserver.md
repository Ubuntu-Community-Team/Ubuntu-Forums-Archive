---
title: "uninstall squeezeboxserver"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by Withanie on 2012-05-23
Hello.   Does anyone know how to uninstall the Logitech Squeezebox server?  Without also uninstalling MySQL. (I'm also in the process of setting up a LAMP installation)

sudo apt-get remove --purge squeezeboxserver tells me that "virtual packages like squeezeboxserver can't be removed."  huh.

(I suppose I should go do some reading on what a virtual package is.)

---

### Post by ikt on 2012-05-24
I would recommend downloaded synaptic from Ubuntu Software Centre and seeing if you are able to remove the individual squeezebox server package from that.

---

### Post by nothingspecial on 2012-05-24
> **Withanie said:**
> Hello.   Does anyone know how to uninstall the Logitech Squeezebox server?  Without also uninstalling MySQL. (I'm also in the process of setting up a LAMP installation)

sudo apt-get remove --purge squeezeboxserver tells me that "virtual packages like squeezeboxserver can't be removed."  huh.

(I suppose I should go do some reading on what a virtual package is.)

That's because the package is now named logitechmediaserver, try removing that.

```
$sudo apt-get remove squeezeboxserver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'squeezeboxserver' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
$sudo apt-get remove logitechmediaserver 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  logitechmediaserver
0 upgraded, 0 newly installed, 1 to remove and 16 not upgraded.
After this operation, 250 MB disk space will be freed.

```

---

