---
title: "[C++] libvorbis Linking Error"
date: 2010-12-28
forum: Programming Talk
---

### Post by dodle on 2010-12-28
I'm trying to figure out how to decode an Ogg audio file using libvorbis but the compiler seems to be having trouble linking:

I don't know if this code is even close to correct, but I can't use any of the initialization functions listed at [http://xiph.org/vorbis/doc/vorbisfile/initialization.html](http://xiph.org/vorbis/doc/vorbisfile/initialization.html).

dog.ogg:
[php]#include <vorbis/vorbisfile.h>
#include <iostream>
using namespace std;

int main()
{
    OggVorbis_File vf;
    FILE *infile;
    infile = fopen("dog.ogg", "rb");
    if (ov_open_callbacks(infile, &vf, NULL, 0, OV_CALLBACKS_DEFAULT) < 0)
    {
        cout << "Not Vorbis file" << endl;
        fclose(infile);
        return 1;
    }
    else
    {
        cout << "Vorbis file" << endl;
        fclose(infile);
        return 0;
    }
}[/php]

```
$ g++ dog.cpp -o dog -lvorbis
/tmp/ccltgL15.o: In function `main':
dog.cpp:(.text+0xb8): undefined reference to `ov_open_callbacks'
collect2: ld returned 1 exit status
```

---

### Post by Zugzwang on 2010-12-28
The function "ov_open_callbacks" is in the library "libvorbisfile" and not "libvorbis". Thus, you need to link that to your program (as well).

---

### Post by dodle on 2010-12-28
Thanks.

---

