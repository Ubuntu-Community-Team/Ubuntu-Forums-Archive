---
title: "error installing package in synaptic"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by garyed on 2008-11-10
I'm trying to install linuxsampler through synaptic in Gusty 7.10.
When I mark it for installing I get this error:

linuxsampler:

Package linuxsampler has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
 

Anyone know what my problem is?

---

### Post by bapoumba on 2008-11-11
[http://packages.ubuntu.com/dapper/linuxsampler](http://packages.ubuntu.com/dapper/linuxsampler)

Looks there is a dapper package but not for versions > dapper.

Home page with install instructions: [http://www.linuxsampler.org/](http://www.linuxsampler.org/)

---

### Post by garyed on 2008-11-11
Thanks, 
I'll check it out.
I just don't understand if linuxsampler shows up in Synaptic you would think all the dependencies would be there too.

---

### Post by bapoumba on 2008-11-11
Well, not really. Everything was built for dapper. I have not searched why this package has not been built for debian or ubuntu after dapper. There may be a reason.
So the package manager knows there is such a package in the repos, but also knows you cannot install it if you are not running dapper (version conflicts).

---

