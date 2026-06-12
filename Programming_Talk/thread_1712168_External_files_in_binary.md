---
title: "External files in binary"
date: 2011-03-22
forum: Programming Talk
---

### Post by roadkillguy on 2011-03-22
I have textures and such that I don't necessarily want to be editable by the user.  Is there a way to compile external files into the final executable?  Using the linker maybe?

Thanks

---

### Post by Some Penguin on 2011-03-22
You might want to mention the language you're using.

If it's in the C family, you can likely get where you want by shoving the contents into a byte array initialized in a header file.

---

### Post by roadkillguy on 2011-03-22
Good point.  I'm using c++.  Should I write a program to output a .h file with all the data?  Could I put it in the linker args?

---

### Post by Some Penguin on 2011-03-23
If I were going to dump into a .h, I'd definitely do it via program.  I've seen this done for bitmaps in *really* old code.  The header just initializes the byte array, you include the header where you access it, and it's just another variable after that.

---

### Post by roadkillguy on 2011-03-23
Hmmm... I'm actually trying to include an image that's 512*512 at 3 bytes per pixel.. the file I generated is 4.5mb, and I can't even open it in gedit like I normally do.  Should I make some sort of .dat file to include at runtime?

This is the code I currently use to write an array:

```
for(int i = 0;i < length;i ++)
{
    fprintf(fp, "\'%c\',", (int)ambient.imageData[i]);
}
```

There's got to be another way.

---

### Post by johnl on 2011-03-23
Hi,

You can indeed do it with **ld**; for example, if you have a file named 'image.png', you can do the following:

```

ld -r -b binary -o image.png.o image.png

```

The resulting .o file (image.png.o) can be linked with your other object files, and will expose the following symbols, which are pointers to the beginning and end of the blob.

```

extern char _binary_image_png_start[];
extern char _binary_image_png_end[];

```

Which you can use like so (for example, with an embedded text file, in C):
```

#include <stdio.h>

extern char _binary_data_start[];
extern char _binary_data_end[];

int main(int argc, char* argv[]) 
{
    for(char* p = (char*)_binary_data_start; p < (char*)_binary_data_end; ++p) {
        putchar(*p);
    }
    
    return 0;
}


```

---

### Post by roadkillguy on 2011-03-24
That's just what I was looking for!

Is it png specific?

---

### Post by johnl on 2011-03-24
> **roadkillguy said:**
> That's just what I was looking for!

Is it png specific?

No, you can do it with any sort of file.  The linker doesn't care.

---

### Post by roadkillguy on 2011-03-24
Is it then possible to type cast that char into a FILE pointer to use with fread?  I have a function that would normally read from a file, but I now want to use that data with it.

---

