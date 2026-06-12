---
title: "error compiling open obex"
date: 2009-08-05
forum: Packaging and Compiling Programs
---

### Post by jndlsnl on 2009-08-05
hi,

i m getting problem with open obex....when i compile open obex then its gives the error and its shows,,,,


Making install in include
make[1]: Entering directory `/home/sunil/Desktop/openobex-1.5/include'
Making install in openobex
make[2]: Entering directory `/home/sunil/Desktop/openobex-1.5/include/openobex'
make[3]: Entering directory `/home/sunil/Desktop/openobex-1.5/include/openobex'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/openobex" || /bin/mkdir -p "/usr/local/include/openobex"
/bin/mkdir: cannot create directory `/usr/local/include/openobex': Permission denied
make[3]: *** [install-includeHEADERS] Error 1
make[3]: Leaving directory `/home/sunil/Desktop/openobex-1.5/include/openobex'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/sunil/Desktop/openobex-1.5/include/openobex'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/sunil/Desktop/openobex-1.5/include'
make: *** [install-recursive] Error 1


can anyone tell how can i fix this problem...i don't knw it giving these error...i need to install openobex

thnx in advance..

---

### Post by Leslie Viljoen on 2009-08-06
The error is where it tries to create /usr/local/include/openobex. You would likely have to sudo this compilation (at your own risk).

---

