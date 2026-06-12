---
title: "gcc / ld and libexif, &quot;undefined reference to&quot;"
date: 2009-02-11
forum: Programming Talk
---

### Post by leifjonny on 2009-02-11
I'm trying to make an application that makes use of geotags stored in jpeg photos. And I found out I can use the library libexif to read the exif/geotag info from the images. I installed libexif-dev and libexif-gtk-dev in synaptic.

When I try to use functions from the library ld complaints. Could someone please point out to me what is wrong?

```
#include <stdio.h>
#include <stdlib.h>

#include <libexif/exif-data.h>

int main(int argc, char* argv[])
{

  ExifData *data = exif_data_new_from_file (argv[1]);

  return 0;
}
```

compiling:
```
gcc -Wall -o geotag geotag.c
geotag.c: In function 'main':
geotag.c:9: warning: unused variable 'data'
/tmp/ccufNoYW.o: In function `main':
geotag.c:(.text+0x1d): undefined reference to `exif_data_new_from_file'
collect2: ld returned 1 exit status
make: *** [all] Error 1

```

---

### Post by snova on 2009-02-11
Add this to the end of your compile line:

```
-lexif
```

To link the library into the program.

---

### Post by leifjonny on 2009-02-11
thanks

---

