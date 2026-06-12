---
title: "Compilling PNGWriter example problem with FreeType2"
date: 2008-03-28
forum: Programming Talk
---

### Post by mikeym on 2008-03-28
Hi,

I'm trying to get an example program to compile but I'm getting errors that seem to relate to my system setup and I thought you might be able to help.

[http://pngwriter.sourceforge.net/](http://pngwriter.sourceforge.net/) is the code I'm trying to use

I install it with:

```

$ make PREFIX=/usr
#
#
#  PNGwriter 0.5.3
#  Copyright 2002, 2003, 2004, 2005 Paul Blackburn
#  http://pngwriter.sourceforge.net/
#  This library and its associated files are covered
#  by the GNU General Public License.
#
#  Using make.include.linux for your compilation/installation prefs.
#
#  Important: If you do not have FreeType2 installed, 
#  see the README for instructions on compiling PNGwriter
#  without FreeType2 support.
#
#  Importante: Si no tienes FreeType2 instalado,
#  lee el archivo LEAME en doc/espaniol para 
#  instrucciones acerca de como compilar PNGwriter
#  sin soporte para FreeType2. 
#
#  You have selected to compile PNGwriter with
#  FreeType2 support.
#
#
cd src; make 
make[1]: Entering directory `/home/mikey/Maths/pngwriter-0.5.3/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/mikey/Maths/pngwriter-0.5.3/src'
cd examples; make
make[1]: Entering directory `/home/mikey/Maths/pngwriter-0.5.3/examples'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/mikey/Maths/pngwriter-0.5.3/examples'

```

and

```

$ sudo make install
[sudo] password for XXXXX:
cp README README.bak
cat README.bak | \
        sed   's# -  libpngwriter.a:# -  libpngwriter.a: /usr/local/lib/#g' > README
cp README README.bak
cat README.bak | \
        sed   's# -  pngwriter.h:# -  pngwriter.h: /usr/local/include/#g' > README
cp README README.bak
cat README.bak | \
        sed   's# -  documentation:# -  documentation: /usr/local/share/doc/pngwriter/#g' > README
cp README README.bak
cat README.bak | \
        sed   's# -  examples:# -  examples: /usr/local/share/doc/pngwriter/#g' > README
cp README README.bak
cat README.bak | \
        sed   's# -  fonts:# -  fonts: /usr/local/share/pngwriter/fonts/#g' > README
rm README.bak
cp doc/english/README doc/english/README.bak
cat doc/english/README.bak | \
        sed   's# -  libpngwriter.a:# -  libpngwriter.a: /usr/local/lib/#g' > doc/english/README
cp doc/english/README doc/english/README.bak
cat doc/english/README.bak | \
        sed   's# -  pngwriter.h:# -  pngwriter.h: /usr/local/include/#g' > doc/english/README
cp doc/english/README doc/english/README.bak
cat doc/english/README.bak | \
        sed   's# -  documentation:# -  documentation: /usr/local/share/doc/pngwriter/#g' > doc/english/README
cp doc/english/README doc/english/README.bak
cat doc/english/README.bak | \
        sed   's# -  examples:# -  examples: /usr/local/share/doc/pngwriter/#g' > doc/english/README
cp doc/english/README doc/english/README.bak
cat doc/english/README.bak | \
        sed   's# -  fonts:# -  fonts: /usr/local/share/pngwriter/fonts/#g' > doc/english/README
rm doc/english/README.bak
cp doc/espaniol/LEAME doc/espaniol/LEAME.bak
cat doc/espaniol/LEAME.bak | \
        sed   's# -  libpngwriter.a:# -  libpngwriter.a: /usr/local/lib/#g' > doc/espaniol/LEAME
cp doc/espaniol/LEAME doc/espaniol/LEAME.bak
cat doc/espaniol/LEAME.bak | \
        sed   's# -  pngwriter.h:# -  pngwriter.h: /usr/local/include/#g' > doc/espaniol/LEAME
cp doc/espaniol/LEAME doc/espaniol/LEAME.bak
cat doc/espaniol/LEAME.bak | \
        sed   's# -  documentacion:# -  documentacion: /usr/local/share/doc/pngwriter/#g' > doc/espaniol/LEAME
cp doc/espaniol/LEAME doc/espaniol/LEAME.bak
cat doc/espaniol/LEAME.bak | \
        sed   's# -  ejemplos:# -  ejemplos: /usr/local/share/doc/pngwriter/#g' > doc/espaniol/LEAME
cp doc/espaniol/LEAME doc/espaniol/LEAME.bak
cat doc/espaniol/LEAME.bak | \
        sed   's# -  fonts:# -  fonts: /usr/local/share/pngwriter/fonts/#g' > doc/espaniol/LEAME
rm doc/espaniol/LEAME.bak
rm -f READMEe doc/english/READMEe doc/espaniol/LEAMEe
#
#
#  PNGwriter 0.5.3
#  Copyright 2002, 2003, 2004, 2005 Paul Blackburn
#  http://pngwriter.sourceforge.net/
#  This library and its associated files are covered
#  by the GNU General Public License.
#
#  Note: You can only install to a directory you own,
#  if you are not root. To install elsewhere, compile 
#  PNGwriter by giving Make the destination directory:
#
#  make DESTDIR=OME (for example)
#
#  Alternatively, you can change DESTDIR in 'make.include'.
#
#  Using make.include.linux for your compilation/installation prefs.
#
#  The following files will be installed:
#
#    pngwriter.h     in /usr/local/include/
#    libpngwriter.a  in /usr/local/lib/
#    examples/       in /usr/local/share/doc/pngwriter/
#    doc/            in /usr/local/share/doc/pngwriter/
#    Fonts           in /usr/local/share/pngwriter/fonts
#
#
install -d -v /usr/local/include/ /usr/local/lib/
install -d -v /usr/local/share/pngwriter/fonts/
install -S -v -m644 src/pngwriter.h /usr/local/include/
install -S -v -m644 src/libpngwriter.a /usr/local/lib/
install -S -v -m644 fonts/*  /usr/local/share/pngwriter/fonts/
install -d -v /usr/local/share/doc/pngwriter
cp -a doc/* /usr/local/share/doc/pngwriter
install -d -v /usr/local/share/doc/pngwriter/examples
cp examples/*.cc examples/*png  \
        /usr/local/share/doc/pngwriter/examples/

```

But when I try to compile test.cc

```

#include <pngwriter.h>


int main()
{
   int i;
   pngwriter png(300,300,0,"test.png");
   for(i = 1; i < 300;i++)
     {
        png.plot(i,150+100*sin((double)i*9/300.0), 0.0, 0.0, 1.0);
     }
   png.close();
   return 0;
}

```

I get the following error:

```

$ gcc test.cc
In file included from /usr/local/include/pngwriter.h:57,
                 from test.cc:1:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from test.cc:1:
/usr/local/include/pngwriter.h:58:10: error: #include expects "FILENAME" or <FILENAME>
/usr/local/include/pngwriter.h:122: error: 'FT_Bitmap' has not been declared
/usr/local/include/pngwriter.h:123: error: 'FT_Bitmap' has not been declared
test.cc: In function 'int main()':
test.cc:10: warning: passing 'double' for argument 2 to 'void pngwriter::plot(int, int, double, double, double)'

```

It seems that there is a problem with finding freetype2 which I have installed. On their forums they mention it using *freetype-config* to determine the location of it:

THis is what I get:

```

$ freetype-config --prefix                            
/usr
$ locate ftheader.h
/chroot/usr/include/freetype2/freetype/config/ftheader.h
/usr/include/freetype2/freetype/config/ftheader.h

```

---

### Post by lloyd_b on 2008-03-28
It's including it as "freetype/config/ftheader.h", but given those paths it should probably be "freetype2/freetype/config/header.h".  I'm wondering if your examples are intended for an older version of freetype, which had it's includes in "/usr/include/freetype".

Ok - this is from the file "/usr/include/ft2build.h", which is the source of the error:
```
  /* `<prefix>/include/freetype2' must be in your current inclusion path */
#include <freetype/config/ftheader.h>
```

Note that comment - it looks like to compile this, you need to specify this directory to search for include files.
```
gcc -I/usr/include/freetype2 test.cc
```

Give that a try and see what happens.

Lloyd B.

---

### Post by mikeym on 2008-03-28
Hmmmm.... thanks  seemed to fix the freetype issue but like you suggested it doesn't seem to want to work.

```

t$ gcc -I/usr/include/freetype2 test.cc
test.cc: In function 'int main()':
test.cc:10: warning: passing 'double' for argument 2 to 'void pngwriter::plot(int, int, double, double, double)'
/tmp/ccTcPtoN.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cc:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccTcPtoN.o: In function `__tcf_0':
test.cc:(.text+0x66): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccTcPtoN.o: In function `main':
test.cc:(.text+0x92): undefined reference to `pngwriter::pngwriter(int, int, int, char const*)'
test.cc:(.text+0xc5): undefined reference to `sin'
test.cc:(.text+0x101): undefined reference to `pngwriter::plot(int, int, double, double, double)'
test.cc:(.text+0x117): undefined reference to `pngwriter::close()'
test.cc:(.text+0x125): undefined reference to `pngwriter::~pngwriter()'
test.cc:(.text+0x144): undefined reference to `pngwriter::~pngwriter()'
/tmp/ccTcPtoN.o:(.eh_frame+0x13): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


```

---

### Post by lloyd_b on 2008-03-28
Try
```
g++ -I/usr/include/freetype2 test.cc
```

I don't understand the differences, but I've seen that invoking "gcc" and invoking "g++" can produce considerably different results.

Other than that, I'm afraid I have no clue - I'm more a C person than a C++ person...

Lloyd B.

---

### Post by mikeym on 2008-03-28
OK I found the line I needed to compile when I actually went into pngwriter.h and read it.

```

 g++ test.cc -o my_program `freetype-config --cflags` -I/usr/local/include  -L/usr/local/lib -lpng -lpngwriter -lz -lfreetype

```

Thanks again for the help

---

### Post by mikeym on 2008-03-28
The results of my second program (OK most of the code is nicked from their example but it's quite easy really):

---

### Post by olda220 on 2009-08-02
Hello, could you tell me what I am doing wrong?
I have the same example as mikeym
Excuse my english...
```
gcc -Wall -c "priklad.c" (v adresá&#345;i: /home/olda220)
In file included from /usr/local/include/pngwriter.h:58,
                 from priklad.c:1:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from priklad.c:1:
/usr/local/include/pngwriter.h:59:10: error: #include expects "FILENAME" or <FILENAME>
/usr/local/include/pngwriter.h:73:20: error: iostream: No such file or 
directory
/usr/local/include/pngwriter.h:74:17: error: cmath: No such file or directory
/usr/local/include/pngwriter.h:75:18: error: cwchar: No such file or directory
/usr/local/include/pngwriter.h:76:18: error: string: No such file or directory
In file included from priklad.c:1:
/usr/local/include/pngwriter.h:91: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pngwriter’
priklad.c: In function ‘main’:
priklad.c:7: error: ‘pngwriter’ undeclared (first use in this function)
priklad.c:7: error: (Each undeclared identifier is reported only once
priklad.c:7: error: for each function it appears in.)
priklad.c:7: error: expected ‘;’ before ‘png’
priklad.c:10: error: ‘png’ undeclared (first use in this function)
priklad.c:10: warning: implicit declaration of function ‘sin’
priklad.c:10: warning: incompatible implicit declaration of built-in function ‘sin’
P&#345;eklad selhal.
```

---

