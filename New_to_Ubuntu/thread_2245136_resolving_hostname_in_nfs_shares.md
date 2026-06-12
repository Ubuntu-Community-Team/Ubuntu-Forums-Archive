---
title: "resolving hostname in nfs shares"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by schema2 on 2014-09-21
What is the name of the package that resolves hostnames in fstab entries. What is the package that enables me to use hostname.local instead of a dynamic ip? I would like to know the name of the package that does this and if it is exclusive to ubuntu or has a debian equivalence. Is it nmbd that does this?

---

### Post by JKyleOKC on 2014-09-21
Depending on the number of systems involved, you can use the /etc/hosts file to provide name-to-address resolution, or you can install the BIND server package to operate a local name server. Both these, however, require static IP address assignment, not dynamic, and both would apply only to your local network. They would not appear to any system outside your local network.

For doing such translation with dynamic IP addresses, I'm not aware of any package that you could install and run locally. A number of commercial services, however, are available. They all depend on installation of software that will notify their name servers of any change in your dynamic IP address, and not all routers provide such capabilities.

Tell us more about what you want to do and we may be able to provide additional detail.

---

### Post by bab1 on 2014-09-21
> **schema2 said:**
> What is the name of the package that resolves hostnames in fstab entries. What is the package that enables me to use hostname.local instead of a dynamic ip? I would like to know the name of the package that does this and if it is exclusive to ubuntu or has a debian equivalence. Is it nmbd that does this?

The file /etc/fstab is the configuration for mounting partitions upon boot up.  Hostnames are resolved via /etc/hosts first and then by a DNS server.

The resolver mechanism for .local names is AVAHI.

The daemon nmbd is the NETBIOS name resolver for Samba.

---

### Post by schema2 on 2014-09-21
Ah, thanks. Avahi is that I think I was looking for. This is one of those cases where I am not sure what I am talking about, so I cannot fully articulate it.  I am just trying to work the bugs out of networking over local between ubuntu and debian. My nodes get dynamic ips, and I was wondering the mechanism which allowed me to resolve the hostname instead of having to specify the dynamic ip in config files. Assigning static ips isn't practical for my home network. Thank you.

---

### Post by JKyleOKC on 2014-09-21
The wikipedia entry for avahi indicates that it's almost certainly what you are looking for. You ought not have any serious problems networking between Ubuntu and Debian, since Ubuntu is derived from Debian and many of the packages are identical or nearly so. However the Ubuntu boxes may include by default a number of packages that Debian does not, since the Debian approach is to not include more than a minimum by default and let the user decide what extras are needed, while Ubuntu attempts to make the default package fill as many needs as possible with little need for later additions.

I do know that all the *buntu packages that I have installed do include avahi capabilities by default. I've only installed one Debian VM and haven't used it enough to really be aware of what it included, but you may need to add avahi or bonjour packages to those boxes to make it all work...

---

### Post by bab1 on 2014-09-21
Avahi packages are available for the later Debian versions.  They are most likely maintained by the same folks.  Avahi is compatible with MS and Apple products.

---

