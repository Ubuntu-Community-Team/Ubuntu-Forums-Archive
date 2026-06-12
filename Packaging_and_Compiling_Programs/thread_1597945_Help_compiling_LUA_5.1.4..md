---
title: "Help compiling LUA 5.1.4."
date: 2010-10-15
forum: Packaging and Compiling Programs
---

### Post by JesterDev on 2010-10-15
Solved. Added deb [http://svn.debian.org/viewsvn/pkg-lua/packages/lua-posix](http://svn.debian.org/viewsvn/pkg-lua/packages/lua-posix)

-----------



Did: 

```
sudo apt-get install build-essential
```

Needed nothing..

Tried: 
```

make install linux

```

Results in:
```

cd src && mkdir -p /usr/local/bin /usr/local/include /usr/local/lib /usr/local/man/man1 /usr/local/share/lua/5.1 /usr/local/lib/lua/5.1
cd src && install -p -m 0755 lua luac /usr/local/bin
install: cannot stat `lua': No such file or directory
install: cannot stat `luac': No such file or directory
make: *** [install] Error 1


```

Any help greatly appreciated!

Or if there is a way to install 5.1.4 with apt-get, that would also work, but currently it only has an older version 5.0.x.

---

