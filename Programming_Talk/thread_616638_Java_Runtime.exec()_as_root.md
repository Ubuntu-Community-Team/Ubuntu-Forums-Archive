---
title: "Java: Runtime.exec() as root"
date: 2007-11-18
forum: Programming Talk
---

### Post by xlinuks on 2007-11-18
Hi,
I need to use the "mount" command from Java on Linux (on Gutsy if that matters) but the "mount" command requires root privileges. Does anyone know how one can run a command with root privileges from Java? Any idea is welcome, even not "cross-linux" ones.
Here's the code snapshot:
```

String[] str = {
    "mount",
    "-o",
    "loop",
    "-t",
    "iso9660",
    f.getPath(),
    dir.getPath()
};
try {
    Process p = r.exec( str );
} catch( Exception exc ) {
    tell( exc );
}

```

---

### Post by geirha on 2007-11-18
Don't know the best way to do that, though you could use gksu: 
```
String[] str= { "gksu",
    "mount -oloop "+f.getPath()+" "+dir.getPath()
};

```

---

### Post by xlinuks on 2007-11-18
Thanks..(didn't seem to work)
I guess the best way is to start programming in C/C++.

---

