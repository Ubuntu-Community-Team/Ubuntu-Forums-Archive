---
title: "How to install libcurl?"
date: 2011-06-03
forum: Programming Talk
---

### Post by hakermania on 2011-06-03
I mean I have installed all the packages I found on synaptic about curl and nothing...I cannot see any output in 
```
pkg-config --libs curl
```
even after restart.


What is the accurate package to download?
Same thing with opencv....

---

### Post by Zugzwang on 2011-06-03
Step 1: Have a look at an example source code for the libraries you want to use. Write down the name of a file you need (without path), e.g., "curl.h"

Step 2: Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and under "Search the contents of packages", type in the file name. Hit the search button.

Step 3: Observe in which packages you can find the files. Which package names look correct? Install these packages.

Note that for curl, there seem to be three versions. Google for details why this is the case and then pick the package appropriately.

Also note that not all libraries support pkg-config. In that case, you will need to provide the include paths and library details manually to the compiler and linker.

---

### Post by gmargo on 2011-06-03
Try "libcurl" instead of "curl":
```

pkg-config --libs libcurl

```

---

### Post by cgroza on 2011-06-03
There is the results of an apt-cache search:

```
cgroza@cgroz-pyNerd:~$ sudo apt-cache search libcurl
[sudo] password for cgroza: 
Sorry, try again.
[sudo] password for cgroza: 
libcurl4-nss-dev - Development files and documentation for libcurl (NSS)
libcurl4-openssl-dev - Development files and documentation for libcurl (OpenSSL)
fp-units-net - Free Pascal - networking units
gnupg-curl - GNU privacy guard - a free PGP replacement (cURL)
libcurl-ocaml - OCaml curl bindings (Runtime Library)
libcurl-ocaml-dev - OCaml libcurl bindings (Development package)
libghc6-curl-dev - GHC 6 libraries for the libcurl Haskell bindings
libghc6-curl-doc - Documentation for the libcurl Haskell bindings
libghc6-curl-prof - Profiling libraries for the libcurl Haskell bindings
libghc6-hxt-curl-dev - LibCurl interface for HXT
libghc6-hxt-curl-doc - LibCurl interface for HXT; documentation
libghc6-hxt-curl-prof - LibCurl interface for HXT; profiling library
liblua5.1-curl-dev - libcURL development files for the Lua language version 5.1
liblua5.1-curl0 - libcURL bindings for the Lua language version 5.1
libwww-curl-perl - Perl bindings to libcurl
tclcurl - Tcl bindings to libcurl
wmget - Background download manager in a Window Maker dock app
gnupg - GNU privacy guard - a free PGP replacement
libcurl3 - Multi-protocol file transfer library (OpenSSL)
libcurl3-dbg - libcurl compilée avec les symboles de débogage
libcurl3-gnutls - Bibliothèque de transfert de fichiers muti-protocoles (GnuTLS)
libcurl3-nss - Multi-protocol file transfer library (NSS)
libcurl4-gnutls-dev - Development files and documentation for libcurl (GnuTLS)
python-pycurl - Liaisons Python pour libcurl
python-pycurl-dbg - Liaisons Python pour libcurl (extension de débogage)
cgroza@cgroz-pyNerd:~$ 

```

---

### Post by hakermania on 2011-06-04
> **gmargo said:**
> Try "libcurl" instead of "curl":
```

pkg-config --libs libcurl

```

Should I feel like an idiot now :D ?

---

### Post by mltsy on 2011-12-14
I was having the same problem while trying to install the patron gem, and the following solved it for me:

`apt-get install libcurl4-gnutls-dev'

---

### Post by lemhop on 2012-02-17
> **mltsy said:**
> I was having the same problem while trying to install the patron gem, and the following solved it for me:

`apt-get install libcurl4-gnutls-dev'

Thanks mltsy, installing this let me install biomaRt (R bioconductor package) in Ubuntu 11.10 (also had to install libxml2).

---

### Post by roberto32 on 2013-02-25
I've problem with libcurl too, I need it ot install opkg and it says it need libcurl I've installed libcurl3-dbg with package mannager and nuthin, it tells me to consider adjusting pkg_config_path but it don't know where I can find it

---

