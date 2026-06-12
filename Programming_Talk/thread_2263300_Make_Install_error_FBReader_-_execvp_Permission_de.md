---
title: "Make Install error FBReader - execvp Permission denied make[1]: [do_install] Error 1"
date: 2015-01-31
forum: Programming Talk
---

### Post by harkirat_singh on 2015-01-31
Make install error.

make[1]: execvp: ./scripts/install_help.sh: Permission denied
make[1]: *** [do_install] Error 127


i changed the path of install_help.sh in the make file to full absolute path . then i got this.


  [HTML]make[1]: Entering directory `/home/harkirat/Downloads/FBReader-master/fbreader' . /home/harkirat/Downloads/FBReader-master/fbreader/scripts/install_help.sh desktop /usr/share/FBReader/help -e usage   /bin/sh <platform> <install_dir> [/HTML]

---

### Post by Bucky Ball on 2015-01-31
Are you using sudo before the commands? For instance:

```
sudo make <add the rest of command here>
```

That's probably what the permission denied error is all about.

---

### Post by harkirat_singh on 2015-01-31
i tried it but no use

---

