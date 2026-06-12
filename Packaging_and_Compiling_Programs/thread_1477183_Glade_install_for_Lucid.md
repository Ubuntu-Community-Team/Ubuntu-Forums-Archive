---
title: "Glade install for Lucid"
date: 2010-05-08
forum: Packaging and Compiling Programs
---

### Post by nocturnal1 on 2010-05-08
What is the correct command to install Glade 3.7.0 in Ubuntu Lucid?
I've tried sudo apt-get install glade-3-7 and other variants but I just get; can't find package glade-3 .
Synaptic shows the following are installed but I don't have interface designer anywhere.
python-glade2
libglade2.0-cil
libglade2-0
libglade2-dev

thanks

---

### Post by Compyx on 2010-05-10
```

sudo apt-get install glade

```
should do. That will install glade-3.7.0.is.3.6.7-0ubuntu1. The interface designer should be available as '/usr/bin/glade-3.

---

### Post by nocturnal1 on 2010-05-16
Thank you very much. That worked. For future reference is there a common naming scheme for sudo apt-get? For instance it's listed as:
_ glade_  (3.7.0.is.3.6.7-0ubuntu1) [**universe**]
here about quarter the way down the page: [http://packages.ubuntu.com/lucid/devel/](http://packages.ubuntu.com/lucid/devel/)

So could I use:  sudo apt-get glade3.7.0.is.3.6.7-0ubuntu1
I assume it downloads the latest stable release. So if I was having problems with a particular release and wanted to download a older version.

Thanks

---

