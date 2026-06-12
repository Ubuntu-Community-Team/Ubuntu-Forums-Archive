---
title: "'Undefined reference' to an installed openSSL RSA function"
date: 2009-02-26
forum: Programming Talk
---

### Post by gogetadbl on 2009-02-26
I used apt-get to get libssl-dev.  The code is below.  When I remove an argument the compiler says that there's too few arguments and when I add an argument the compiler says there's too many arguments, so it seems like there is "some" kind of reference to the correct function.  There's some linking going on wrongly perhaps?  I'm sure I'm doing something stupid but I can't think of what it could be.

gcc test.c
/tmp/ccPG86Ko.o: In function `main':
test.c:(.text+0x44): undefined reference to `RSA_generate_key'
collect2: ld returned 1 exit status


```
#include <stdlib.h>
#include <stdio.h>
#include <openssl/rsa.h>

int main(int argc, char **argv)
{
	RSA* rsa;
	rsa = RSA_generate_key(1,1, NULL, NULL);
}


```

---

### Post by supirman on 2009-02-26
Did you specify the ssl library in the gcc command?

```
gcc yourfile.c -lssl
```

It fails when you remove a parameter because the header file is found ok and the function arguments verified -- but you still must tell it to link the ssl library.

---

### Post by geirha on 2009-02-26
Many libraries use pkg-config to provide the options needed to compile and link against the library.
pkg-config --list-all will list all libraries that have added themselves to pkg-config

```
pkg-config --list-all | grep ssl
```

If you find it (in this case libssl or openssl), run 
```
$ pkg-config libssl --cflags --libs
 -lssl  

```

You can also use the output directly when compiling
```
$ gcc $(pkg-config libssl --cflags --libs) test.c
```

---

### Post by gogetadbl on 2009-02-26
That fixed it, thanks!  Glad to know about how to do this in the future for other libraries :)

---

