---
title: "Canon Pixma ip1700 - Printer state: &quot;stopped&quot;"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by KosmicheCam on 2008-09-30
Members of the forum,

After recently installing Ubuntu 8.04 on a dual boot, I have been using [this guide]("https://answers.launchpad.net/ubuntu/+question/22555") to install my Canon Pixma ip1700 printer. The guide recommended using the linux driver for Canon's ip2200. In any case, something small seems to be wrong as the "printer state" is "stopped" and I have a small printer sign with red negative sign on my top panel, which reports the error: "*Printer 'iP2200_Ver.2.60': 'cups-missing-filter'.*

On the guide linked above, it was suggested that you try this in the terminal:
```
ldd /usr/local/bin/cifip2200
```

Here's what I came up with:
```
	linux-gate.so.1 =>  (0xb7fb4000)
	libcnbpcmcm256.so => /usr/lib/libcnbpcmcm256.so (0xb7f98000)
	libcnbpess256.so => /usr/lib/libcnbpess256.so (0xb7f66000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f40000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f3c000)
	libtiff.so.3 => not found
	libpng.so.3 => not found
	libcnbpcnclapi256.so => /usr/lib/libcnbpcnclapi256.so (0xb7f35000)
	libcnbpcnclbjcmd256.so => /usr/lib/libcnbpcnclbjcmd256.so (0xb7f2f000)
	libcnbpcnclui256.so => /usr/lib/libcnbpcnclui256.so (0xb7f28000)
	libpopt.so.0 => /lib/libpopt.so.0 (0xb7f20000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7dd1000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7db9000)
	/lib/ld-linux.so.2 (0xb7fb5000)

```

I hope this can be a help to somebody in working out what may be wrong... Any help would really be appreciated!

Cheers :-?

---

### Post by baAng on 2008-12-16
hello..
try to take a look at this thread 
[http://ubuntuforums.org/showthread.php?t=867648&highlight=ip1700]("http://ubuntuforums.org/showthread.php?t=867648&highlight=ip1700")

---

