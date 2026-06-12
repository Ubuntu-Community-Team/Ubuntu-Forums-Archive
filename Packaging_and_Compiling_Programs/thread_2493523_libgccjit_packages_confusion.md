---
title: "libgccjit packages confusion"
date: 2023-12-18
forum: Packaging and Compiling Programs
---

### Post by paaguti-p on 2023-12-18
Hi,

I'm compiling emacs master on ubuntu jammy. As far as I can see, gcc12-base is installed by default on this release. However, if I use gcc-12 and libgccjit-12-dev, the library is not detected:
```

apt-show-versions | grep gccjit


libgccjit-12-dev:amd64/jammy-security 12.3.0-1ubuntu1~22.04 uptodate
libgccjit0:amd64/jammy-security 12.3.0-1ubuntu1~22.04 uptodate


...


You can now run './configure'.
./configure --prefix=/usr  --program-suffix=30 --with-json \
    --with-x --with-x-toolkit=gtk3 --with-cairo  \
    --with-compress-install --with-modules=yes \
    --with-threads --with-included-regex --with-zlib \
    --with-tree-sitter=no \
    --with-native-compilation


...


checking for library containing inflateEnd... -lz
checking for dladdr... yes
checking for dlfunc... no
checking for gcc_jit_context_acquire in -lgccjit... no
configure: error: ELisp native compiler was requested, but libgccjit was not found.
Please try installing libgccjit or a similar package.



```

and I need to install gcc-11 and libbgccjit-11-dev.

This is somehow confiusing, ins't it?

---

