---
title: "path question"
date: 2013-12-16
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2013-12-16
Running 64 bit Precise on a Dell Latitude D630c that I'm refurbishing.

I installed CMU pocketsphinx, when I try to run pocketsphinx_continuous I get "error while loading shared libraries: libpocketsphinx.so.1: cannot open shared object file: No such file or directory.

The file does exist, it's in /usr/local/lib so I'm thinking it's just a path problem. 

Am I correct that I edit .bashrc as follows to correct this? 

if [ -d "$HOME/usr/local/lib" ] ; then
  PATH="$PATH:$HOME/usr/local/lib"
fi

---

### Post by steeldriver on 2013-12-16
In general, the PATH environment variable is only used when searching for executables (not shared libraries). There are a couple of special library paths (in particular LD_LIBRARY_PATH) that can be utilized in cases like this but their usage is generally regarded as a last resort - it would be preferable to find out why the library path was not added to the usual dynamic linker database when you installed the application - how exactly did you install it?

---

### Post by Robing Goodfellow on 2013-12-16
./autogen.sh  make  make check make install

---

