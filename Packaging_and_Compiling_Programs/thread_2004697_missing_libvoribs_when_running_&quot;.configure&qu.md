---
title: "missing libvoribs when running &quot;./configure&quot; although installed via apt-get"
date: 2012-06-16
forum: Packaging and Compiling Programs
---

### Post by gone-insane on 2012-06-16
Hi,

I am trying to install [http://www.lysator.liu.se/~creideiki/radio-free-san-andreas/]("http://www.lysator.liu.se/%7Ecreideiki/radio-free-san-andreas/"). It says you need libvorbis, which I installed using
```
sudo apt-get install libvorbis-dev
```(I installed similar packages as well).

When I run ./configure, it tells me, libvorbis ain't installed. So I had a look on how "./configure" does this check: It runs

```
 g++ -o conftest -g -O2 conftest.cpp -lvorbis -lcrypto -lm
```on this code:

```
/* confdefs.h */
#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""
#define PACKAGE_URL ""
#define PACKAGE "radio-free-san-andreas"
#define VERSION "0.2"
#define HAVE_LIBM 1
#define HAVE_LIBCRYPTO 1
/* end confdefs.h.  */

/* Override any GCC internal prototype to avoid an error.
   Use char because int might match the return type of a GCC
   builtin and then its argument prototype would still apply.  */
#ifdef __cplusplus
extern "C"
#endif

char ogg_sync_buffer ();

int main ()
{
  return ogg_sync_buffer ();
  ;
  return 0;
}
```which returns
> undefined reference to `ogg_sync_buffer'
collect2: ld returned 1what is this trying to tell me? Which further steps could I make to get this compiled?

---

### Post by gone-insane on 2012-06-16
Okay I found the mistake with a little help of my friends:
./configure checks whether libvorbis-dev is avaiable using a logg command. This can be avoided (not very nicely) changing ./configure in line 4371 from
```
LIBS="-lvorbis $LIBS"
```
to 
```
LIBS="-lvorbis -logg $LIBS"
```

(this doesn't check for lvorbis anymore but it works :-) )

---

