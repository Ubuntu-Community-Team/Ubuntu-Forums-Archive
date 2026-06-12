---
title: "Linking error with libcurl on Oneiric"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by njcrawford on 2011-10-06
I'm trying to compile the libcurl example sample.c from /usr/share/doc/libcurl4-gnutls-dev/examples, but it throws errors at the linking stage. This works on Ubuntu 10.04 and 11.04.

```
g++ -lcurl simple.c -o simple
/tmp/ccqHiJqD.o: In function `main':
simple.c:(.text+0xa): undefined reference to `curl_easy_init'
simple.c:(.text+0x31): undefined reference to `curl_easy_setopt'
simple.c:(.text+0x3d): undefined reference to `curl_easy_perform'
simple.c:(.text+0x4d): undefined reference to `curl_easy_cleanup'
collect2: ld returned 1 exit status
```

I googled around a bit none of the suggestions helped. The libcurl4-gnutls-dev package is installed.

Is there something different about libcurl in Oneiric?

---

### Post by mc4man on 2011-10-06
try
g++ simple.c -lcurl -o simple

---

### Post by njcrawford on 2011-10-06
That worked, thanks mc4man! 

I'd like to understand why it worked... do the newer versions of g++ and/or ld require a specific order of arguments? Or have I made some noob mistake?

---

