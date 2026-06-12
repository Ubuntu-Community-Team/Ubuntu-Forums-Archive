---
title: "Problem installing Wine"
date: 2024-05-25
forum: New to Ubuntu
---

### Post by ivannovich0312 on 2024-05-25
Stuck in first step enabling 32bit architecture: ```
sudo dpkg --add-architecture i386
```
What i get is ```
pkg-config-dpkghook: aviso: Architecture AMD64 not defined in architecture tables, ignored
``` This code
```
dpkg --print-foreign-architectures
``` give me this results ```
i386
AMD64
```

---

### Post by ActionParsnip on 2024-05-26
The "AMD64" entry should be removed then you're all set.

---

### Post by MAFoElffen on 2024-05-27
+1 with ActionParsnip

Explanation:

Look at this
```

mafoelffen@Mikes-B460M:~$ dpkg --print-foreign-architectures
i386

mafoelffen@Mikes-B460M:~$ dpkg-architecture --list | grep -e 'MULTIARCH'
DEB_BUILD_MULTIARCH=x86_64-linux-gnu
DEB_HOST_MULTIARCH=x86_64-linux-gnu
DEB_TARGET_MULTIARCH=x86_64-linux-gnu

mafoelffen@Mikes-B460M:~$ dpkg-architecture --list | grep -e 'DEB_HOST_ARCH='
DEB_HOST_ARCH=amd64

```
The first command verifies that i386 was added as a foreign architecture.

The second command verifies that it is multi-arch.

The third command verifies the native architecture of the host system.

The first command should include only "Foreign Architectures", and not include the "Native Architecture"... And the all CAPs "AMD64" is not a valid ARCH. They are case sensitive. You must have added that mistakenly.

That is why you are getting an error that "AMD64" is not a valid ARCH.

You need to remove that via
```

sudo dpkg --remove-architecture AMD64    ## <-- Notice the all caps word is the one you want to remove...

```

---

