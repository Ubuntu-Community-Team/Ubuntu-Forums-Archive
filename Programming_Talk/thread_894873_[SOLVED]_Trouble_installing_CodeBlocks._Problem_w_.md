---
title: "[SOLVED] Trouble installing Code::Blocks. Problem w/ Depencency"
date: 2008-08-19
forum: Programming Talk
---

### Post by meanburrito920 on 2008-08-19
On attempting to install Code::Blocks from the deb of the website, I am given the error 'Dependency is not satisfyable: libwxgtk2.8-0'

So I try to install the library, but guess what, it's already installed, but for some reason, it can't be found by the libcodeblocks0.deb file. I don't really want to try uninstalling the library and then reinstalling, just in case something important depends on it... Has anyone run across this before? Any suggestions?

---

### Post by pdwerryhouse on 2008-08-19
It probably needs the development package, with header and possibly static libraries: libwxgtk2.8-dev

---

### Post by jinksys on 2008-08-19
> **pdwerryhouse said:**
> It probably needs the development package, with header and possibly static libraries: libwxgtk2.8-dev

No.


> 
On attempting to install Code::Blocks from the deb of the website, I am given the error 'Dependency is not satisfyable: libwxgtk2.8-0'

Are you sure you have 2.8-0 installed?  On my machine I had 2.6-0 installed, but not 2.8-0.  This is how I installed the codeblocks package.

```

1. Extracted the debs into a folder.
2. sudo dpkg -i * --force-all
3. open synaptic and upgrade, then install libwxgtk2.8-0, which will also install libwxbase2.8-0

```

could you post the output of:

dpkg -l | grep libwx

---

### Post by meanburrito920 on 2008-08-19
```

ii  libwxbase2.6-0                             2.6.3.2.1.5ubuntu12                   wxBase library (runtime) - non-GUI support c
ii  libwxbase2.8-0                             2.8.4.0-0ubuntu3                      wxBase library (runtime) - non-GUI support c
ii  libwxbase2.8-dbg                           2.8.4.0-0ubuntu3                      wxBase library (debug) - non-GUI support cla
ii  libwxbase2.8-dev                           2.8.4.0-0ubuntu3                      wxBase library (development) - non-GUI suppo
ii  libwxgtk2.6-0                              2.6.3.2.1.5ubuntu12                   wxWidgets Cross-platform C++ GUI toolkit (GT
ii  libwxgtk2.8-0                              2.8.4.0-0ubuntu3                      wxWidgets Cross-platform C++ GUI toolkit (GT

```

---

### Post by jinksys on 2008-08-19
> **meanburrito920 said:**
> ```

ii  libwxbase2.6-0                             2.6.3.2.1.5ubuntu12                   wxBase library (runtime) - non-GUI support c
ii  libwxbase2.8-0                             2.8.4.0-0ubuntu3                      wxBase library (runtime) - non-GUI support c
ii  libwxbase2.8-dbg                           2.8.4.0-0ubuntu3                      wxBase library (debug) - non-GUI support cla
ii  libwxbase2.8-dev                           2.8.4.0-0ubuntu3                      wxBase library (development) - non-GUI suppo
ii  libwxgtk2.6-0                              2.6.3.2.1.5ubuntu12                   wxWidgets Cross-platform C++ GUI toolkit (GT
ii  libwxgtk2.8-0                              2.8.4.0-0ubuntu3                      wxWidgets Cross-platform C++ GUI toolkit (GT

```

Looks good, what about a

dpkg -l | grep codeblocks

and did you follow the steps I outlined above?  dpkg will still give you errors, but the packages will be installed.  Also, when codeblocks is installed you'll see it under the Programming section in your Applications menu.

---

### Post by meanburrito920 on 2008-08-19
The command returned no result. However, you instructions for installing worked great. Thanks.

---

### Post by jinksys on 2008-08-19
> **meanburrito920 said:**
> The command returned no result. However, you instructions for installing worked great. Thanks.

Glad to hear it! \\:D/

---

