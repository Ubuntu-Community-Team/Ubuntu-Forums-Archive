---
title: "problems with add/remove manager"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by mefistofeles666 on 2008-07-11
so Every time I try to install something from add/remove after clicking on apply changes it gives me this error

E: /var/cache/apt/archives/adblock-plus_0.7.5.4-0ubuntu1_all.deb: files list file for package `ekiga' contains empty filename

it did it for adblock and every other thing I tried to install...

any ideas?

---

### Post by tinny on 2008-07-11
This might help

Open the command line.

```

sudo apt-get clean
sudo apt-get update

```

This should clean your APT cache.

---

### Post by mefistofeles666 on 2008-07-11
nop, it still gives me the same error

---

### Post by tinny on 2008-07-11
Try this...

```

sudo apt-get remove --purge adblock-plus
sudo apt-get clean
sudo apt-get update

```

This will COMPLETELY remove adblock-plus, clean the APT cache and update the APT package list.

If you want to reinstall adblock-plus

```

sudo apt-get install adblock-plus

```

---

### Post by mefistofeles666 on 2008-07-12
I tried installing it and it now gave me this

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing ekiga (--configure):
 subprocess post-installation script returned error exit status 2
Setting up adblock-plus (0.7.5.4-0ubuntu1) ...
Errors were encountered while processing:
 ekiga
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also, I just got this crash report saying "sorry, the package 'ekiga 2.0.12-0ubuntu2' failed to install or upgrade

do you think the might be related?

---

### Post by tinny on 2008-07-12
> **mefistofeles666 said:**
> I tried installing it and it now gave me this

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing ekiga (--configure):
 subprocess post-installation script returned error exit status 2
Setting up adblock-plus (0.7.5.4-0ubuntu1) ...
Errors were encountered while processing:
 ekiga
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also, I just got this crash report saying "sorry, the package 'ekiga 2.0.12-0ubuntu2' failed to install or upgrade

do you think the might be related?

Dont know sorry.

You could try removing both ekiga and adblock-plus with the "--purge" option and then "clean" the APT cache.

---

