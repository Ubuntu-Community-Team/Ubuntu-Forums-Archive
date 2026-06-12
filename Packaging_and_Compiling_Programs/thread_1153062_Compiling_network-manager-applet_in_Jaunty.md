---
title: "Compiling network-manager-applet in Jaunty"
date: 2009-05-08
forum: Packaging and Compiling Programs
---

### Post by Pausanias on 2009-05-08
Hi. I'd appreciate your help with this!

I cannot seem to compile network-manager-applet under amd64 in Jaunty. Why, do you say, am I trying to do this? Because there is no other way to stop all of its notification bubbles (you can stop the "Connected" notifications using a gconf key, but the gconf key to stop the "Disconnected" notifications doesn't work).

This is what I tried:

```

sudo apt-get install build-essential
sudo apt-get build-dep network-manager-applet
apt-get source network-manager-applet
cd network-manager*
dpkg-buildpackage -rfakeroot -uc -us

```

This is what I get. I've googled this, and it seems to have something to do with libtool, but nothing I've tried works---downgrading libtool rerunning libtoolize or autoreconf. I tried emailing the package maintainer but he didn't get back to me. So I'm out of options. Here is the error:

```

/bin/bash ../../libtool --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I../..  -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DG_DISABLE_DEPRECATED   -Wall -Werror -std=gnu89 -g -O2 -g -Wall -O2 -Wshadow -Wmissing-declarations -Wmissing-prototypes -Wdeclaration-after-statement -Wfloat-equal -Wno-unused-parameter -Wno-sign-compare -fno-strict-aliasing -DWITH_MBCA -c -o libmarshallers_la-nma-marshal-main.lo `test -f 'nma-marshal-main.c' || echo './'`nma-marshal-main.c
../../libtool: line 793: X--tag=CC: command not found
../../libtool: line 826: libtool: ignoring unknown tag : command not found
../../libtool: line 793: X--mode=compile: command not found
../../libtool: line 959: *** Warning: inferring the mode of operation is deprecated.: command not found
../../libtool: line 960: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../../libtool: line 1103: Xcc: command not found
../../libtool: line 1103: X-DHAVE_CONFIG_H: command not found
../../libtool: line 1103: X-I.: command not found
../../libtool: line 1103: X-I.: command not found
../../libtool: line 1103: X-I../..: No such file or directory
../../libtool: line 1103: X-I/usr/include/glib-2.0: No such file or directory
../../libtool: line 1103: X-I/usr/lib/glib-2.0/include: No such file or directory
../../libtool: line 1103: X-DG_DISABLE_DEPRECATED: command not found
../../libtool: line 1103: X-Wall: command not found
../../libtool: line 1103: X-Werror: command not found
../../libtool: line 1103: X-std=gnu89: command not found
../../libtool: line 1103: X-g: command not found
../../libtool: line 1103: X-O2: command not found
../../libtool: line 1103: X-g: command not found
../../libtool: line 1103: X-Wall: command not found
../../libtool: line 1103: X-O2: command not found
../../libtool: line 1103: X-Wshadow: command not found
../../libtool: line 1103: X-Wmissing-declarations: command not found
../../libtool: line 1103: X-Wmissing-prototypes: command not found
../../libtool: line 1103: X-Wdeclaration-after-statement: command not found
../../libtool: line 1103: X-Wfloat-equal: command not found
../../libtool: line 1103: X-Wno-unused-parameter: command not found
../../libtool: line 1103: X-Wno-sign-compare: command not found
../../libtool: line 1103: X-fno-strict-aliasing: command not found
../../libtool: line 1103: X-DWITH_MBCA: command not found
../../libtool: line 1103: X-c: command not found
../../libtool: line 1154: Xlibmarshallers_la-nma-marshal-main.lo: command not found
../../libtool: line 1159: libtool: compile: cannot determine name of library object from `': command not found
make[5]: *** [libmarshallers_la-nma-marshal-main.lo] Error 1


```

---

