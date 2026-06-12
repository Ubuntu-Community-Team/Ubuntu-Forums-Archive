---
title: "Quick and easy way to save an image in C++"
date: 2011-05-24
forum: Programming Talk
---

### Post by jespdj on 2011-05-24
I'm writing a small C++ program that generates an image and I'd like to use something to easily save the image data in a file. I don't care much which file format.

I've looked at libpng but it does not have a very easy or user-friendly API, it looks like it is quite low-level and requires you to understand lots of details of the PNG format to use it...

What's a quick and easy way to save an image in C++?

---

### Post by nvteighen on 2011-05-24
Hm... there are a couple of libraries, but none seems to be easy...

Let's see. There's the libpng C++ wrapper, libpng++. There's also libpnglite, a C library, supposedly of lighter weight than libpng... But PNG is a quite complex format, supporting transparency, interleaving, compression and other stuff, so I expect these libraries to be quite difficult.

There's the FreeImage library project too, and its C++ wrapper FreeImagePlus. Look at [http://freeimage.sourceforge.net/](http://freeimage.sourceforge.net/) The library is available at the Debian repos, so I guess Ubuntu's have it too.

I can offer you no more help than this, unfortunately.

---

### Post by jespdj on 2011-05-24
I found [PNGwriter](http://pngwriter.sourceforge.net/) which seems quite easy to use.

---

### Post by dwhitney67 on 2011-05-24
If you do not care about the format of the image file, then merely write it out to the file in a plain-jane binary format.  Open a file stream for binary output, and use the write() function.

Here's a crude example:
```

unsigned char* imgdata = ...;
size_t         imgdata_size = ...;

std::fstream imgout("MyImage.bin", std::out | std::binary);

imgout.write(reinterpret_cast<char*>(imgdata), imgdata_size);
imgout.close();

```

---

### Post by NovaAesa on 2011-05-24
To complement dwhitney67's post, the NetPBM formats are very easy to write out to. Have a look here [http://en.wikipedia.org/wiki/Netpbm_format](http://en.wikipedia.org/wiki/Netpbm_format)

---

### Post by nvteighen on 2011-05-25
> **dwhitney67 said:**
> If you do not care about the format of the image file, then merely write it out to the file in a plain-jane binary format.  Open a file stream for binary output, and use the write() function.

Here's a crude example:
```

unsigned char* imgdata = ...;
size_t         imgdata_size = ...;

std::fstream imgout("MyImage.bin", std::out | std::binary);

imgout.write(reinterpret_cast<char*>(imgdata), imgdata_size);
imgout.close();

```

A question, why reinterpret_cast and not static_cast? Sorry, C++ casting still beats me :P

---

### Post by dwhitney67 on 2011-05-25
> **nvteighen said:**
> A question, why reinterpret_cast and not static_cast? Sorry, C++ casting still beats me :P

Usually reinterpret_cast<> is the first that comes to my mind because it is useful for treating one type of data as another.  I realize there is not "much" difference between an unsigned char and a char, but it seemed appropriate to use vs. static_cast.

Read here for more info on casting (in C++):
[http://www.cplusplus.com/doc/tutorial/typecasting/](http://www.cplusplus.com/doc/tutorial/typecasting/)


P.S.  I tend to think of static_cast<> as the equivalent of a C-style cast; I may be wrong with this loose interpretation.

---

### Post by nvteighen on 2011-05-25
> **dwhitney67 said:**
> Usually reinterpret_cast<> is the first that comes to my mind because it is useful for treating one type of data as another.  I realize there is not "much" difference between an unsigned char and a char, but it seemed appropriate to use vs. static_cast.

Read here for more info on casting (in C++):
[http://www.cplusplus.com/doc/tutorial/typecasting/](http://www.cplusplus.com/doc/tutorial/typecasting/)


P.S.  I tend to think of static_cast<> as the equivalent of a C-style cast; I may be wrong with this loose interpretation.

Oh, ok. The link was useful, thanks.

---

### Post by jespdj on 2011-05-25
> **dwhitney67 said:**
> If you do not care about the format of the image file, then merely write it out to the file in a plain-jane binary format.  Open a file stream for binary output, and use the write() function.
Well, it's not that I totally don't care, it should be a reasonably well-known format that other programs can open, not just a binary dump.

---

### Post by dwhitney67 on 2011-05-25
> **jespdj said:**
> Well, it's not that I totally don't care, it should be a reasonably well-known format that other programs can open, not just a binary dump.

When stating requirements, always state them using clear and concise words.  Don't leave anything to chance, and don't let the developer insert their own notion of what the requirement should be.

---

### Post by nvteighen on 2011-05-25
If so, then the best you can do is either use the "native" APIs for each format (libpng, libjpeg, libgimp, ...) or try using the FreeImage wrapper library. What you want to write is a program that can manipulate those file types, so you want to use the available interfaces, no matter how difficult it is.

---

### Post by jespdj on 2011-05-27
I just wanted a quick and easy way to save an image in a reasonably well-known format, for example PNG. It's for a small program just to try out something, not for some serious piece of software.

As I mentioned, [PNGwriter]("http://pngwriter.sourceforge.net/") works for my purpose. It's very easy to use:
```

#include <pngwriter.h>

int main() {
    pngwriter png(1024, 768, 0.0, "output.png");

    // plot some pixels...
    png.plot(23, 42, 0.5, 1.0, 0.7);

    png.close();
    return 0;
}

```

---

