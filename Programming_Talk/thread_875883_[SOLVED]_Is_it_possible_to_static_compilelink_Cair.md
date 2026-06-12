---
title: "[SOLVED] Is it possible to static compile/link Cairo and Rsvg ?"
date: 2008-07-31
forum: Programming Talk
---

### Post by cudjoe on 2008-07-31
Hi !

I would like to know if it's possible to static compile/link this program that uses librsvg and Cairo-pdf :

git://people.freedesktop.org/~cworth/svg2pdf

...in order to make it work on CentOS 4.6 :confused: i.e. make it depend only on libc :)

I tried adding **-static** in in the Makefile, but the binary is still very small. It should be quite big no ? So I guess it didn't work !

(CentOS 4.6 has Cairo 1.2.4 which does not have pdf backend)

Thanks for sharing your thoughts :)

---

### Post by Zugzwang on 2008-07-31
AFAIK, you need to add the "-static" cmd before the list of libraries you want to include statically. Example (using the math library):

```

me@here:/tmp$ gcc test.c -lm
me@here:/tmp$ ls -la a.out
-rwxr-xr-x 1 me users 6682 Jul 31 15:01 a.out
me@here:/tmp$ gcc test.c -static -lm
me@here:/tmp$ ls -la a.out
-rwxr-xr-x 1 me users 558099 Jul 31 15:01 a.out

```

EDIT: Ok, that's wrong. Corrected by the post below.

---

### Post by nvteighen on 2008-07-31
-static static links **all** libraries...

A way that works, but is not the best is to hardcode the .a filepath:
```

gcc test.c /usr/lib/libm.a

```

That will static link the math library, but not the C Standard Library. Check using the ldd command, which shows you which **shared** libraries your application is linked to (so, if libm**.so** doesn't appear, then it has been statically linked!)

But I've heard there's a better method using -Wl

---

### Post by cudjoe on 2008-07-31
Thanks guyz for your support !

It looks like it's more complicated with Cairo and Rsvg...

The basic gcc command is : 
```
gcc `pkg-config --cflags --libs librsvg-2.0 cairo-pdf` -o svg2pdf svg2pdf.c
```

I tried adding --static to pkg-config, but no -static flag appears :
```

svg2pdf$ pkg-config --static --cflags --libs librsvg-2.0 cairo-pdf
-I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  -lrsvg-2 -lgdk_pixbuf-2.0 -ltiff -ljpeg -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lcairo -lm -lfreetype -lz -lfontconfig -lexpat -lpng12 -lXrender -lpixman-1 -lX11 -lpthread -lxcb-xlib -lxcb -lXau -lXdmcp  

```

So I added it myself manually :
```

svg2pdf$  gcc -static `pkg-config --cflags --libs librsvg-2.0 cairo-pdf` -o svg2pdf svg2pdf.c

/tmp/cc08ModV.o: In function `main':
svg2pdf.c:(.text+0x5d): undefined reference to `g_type_init'
svg2pdf.c:(.text+0x6b): undefined reference to `rsvg_set_default_dpi'
svg2pdf.c:(.text+0x7d): undefined reference to `rsvg_handle_new_from_file'
svg2pdf.c:(.text+0xc5): undefined reference to `rsvg_handle_get_dimensions'
svg2pdf.c:(.text+0xfa): undefined reference to `cairo_pdf_surface_create'
svg2pdf.c:(.text+0x108): undefined reference to `cairo_create'
svg2pdf.c:(.text+0x11d): undefined reference to `rsvg_handle_render_cairo'
svg2pdf.c:(.text+0x128): undefined reference to `cairo_status'
svg2pdf.c:(.text+0x13c): undefined reference to `cairo_status_to_string'
svg2pdf.c:(.text+0x16d): undefined reference to `cairo_destroy'
svg2pdf.c:(.text+0x178): undefined reference to `cairo_surface_destroy'
collect2: ld returned 1 exit status

```

Linking problems ! 
Is that related to the order of gcc parameters or something ?

---

### Post by nvteighen on 2008-07-31
Usually, libraries should go after anything else. Try reversing the order:
```
gcc -o svg2pdf svg2pdf.c `pkg-config --cflags librsvg-2.0 cairo-pdf` -static `pkg-config --libs librsvg-2.0 cairo-pdf`
```

The reason why I cut the pkg-config in two is to explicitly join -static with the output of `pkg-config --libs`.

But, after succesful compiling, please send us the output of the following command:
```

ldd svg2pdf

```

That will show if only those libs were statically linked or also anything else (linux-gate, libc and something else I don't remember). This may be important if you want to have your file as smallest as possible.

Do you know about Makefiles? It could make such a horrible compile command a bit nicer. See [http://crasseux.com/books/ctutorial/Writing-a-makefile.html](http://crasseux.com/books/ctutorial/Writing-a-makefile.html) if interested.

---

### Post by cudjoe on 2008-07-31
I did a Makefile :

```

ALL=svg2pdf

MYCFLAGS=`pkg-config --cflags librsvg-2.0 cairo-pdf`
LDFLAGS=`pkg-config --libs librsvg-2.0 cairo-pdf freetype2 fontconfig pango pangoft2 pangocairo libthai datrie libgsf-1 gnome-vfs-2.0 libcroco-0.6 libpcre pixman-1 libpng libxml-2.0`
MYLDFLAGS=$(LDFLAGS) /usr/lib/libbz2.a /usr/lib/libjpeg.a /usr/lib/libtiff.a /usr/lib/libbz2.a /usr/lib/libz.a /usr/lib/libm.a

all: $(ALL)

%: %.c
	$(CC) $^ -pthread $(MYCFLAGS) -static $(MYLDFLAGS) -o $@

```

As you can see the previous pck-config were not enough... I had to add a lot. And somehow, **pck-config could not find libm, libz, ...** so I added them manually (MYLDFLAGS)

I still have some undefined references. ([see output on pastebin]("http://pastebin.com/m4000edd0"))
They are related to Gnome VFS, libXML and FreeType which are in pck-config already :(

Any idea ?

---

### Post by nvteighen on 2008-07-31
Some packages don't work with pkg-config.

Are you sure you have all needed developer packages installed? It seems you don't have some static libs installed and thus the "undefined references".

---

### Post by cudjoe on 2008-07-31
Thanks for insisting, I double checked everything and had to add more deps again :)

I could investigate inside libraries using the **nm** command. Fantastic!

Eventually it compiled ! Binary is 5.9M which is not bad :)

But **ldd** says : exited with unknown exit code (126)
I guess it's related to the warning about glibc I had :

```

/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/libglib-2.0.a(gutils.o): In function `g_get_any_init_do':
(.text+0x118f): warning: Using 'getpwuid_r' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
...
...

```

I moved the binary and did some conversions on CentOS 4.6 and it worked !

I learned a lot of things ! Once again, thank you all :) 

Updated makefile :

```

ALL=svg2pdf

MYCFLAGS=`pkg-config --cflags librsvg-2.0 cairo-pdf`
LDFLAGS=`pkg-config --libs librsvg-2.0 cairo-pdf freetype2 fontconfig pango pangoft2 pangocairo  cairo-ft libthai datrie libgsf-1 gnome-vfs-2.0 libcroco-0.6 libpcre pixman-1 libpng libxml-2.0`
MYLDFLAGS=$(LDFLAGS) /usr/lib/libgio-2.0.a  /usr/lib/libglib-2.0.a /usr/lib/libselinux.a /usr/lib/libexpat.a /usr/lib/libfreetype.a /usr/lib/libbz2.a /usr/lib/libjpeg.a /usr/lib/libtiff.a /usr/lib/libbz2.a /usr/lib/libz.a /usr/lib/libm.a

all: $(ALL)

%: %.c
	$(CC) $^ -pthread $(MYCFLAGS) -static $(MYLDFLAGS) -o $@

```

---

### Post by nvteighen on 2008-07-31
Nice to hear it worked!

---

### Post by dflock on 2010-01-20
I've been trying to get this to work too, and I think that I'm nearly there, but not quite.

I'm using Ubuntu Karmic, with the above makefile and I get this when I run make:

Package datrie was not found in the pkg-config search path.
Perhaps you should add the directory containing `datrie.pc'
to the PKG_CONFIG_PATH environment variable
No package 'datrie' found
/tmp/ccOf5SDa.o: In function `main':
svg2pdf.c:(.text+0x5a): undefined reference to `g_type_init'
svg2pdf.c:(.text+0x68): undefined reference to `rsvg_set_default_dpi'
svg2pdf.c:(.text+0x7c): undefined reference to `rsvg_handle_new_from_file'
svg2pdf.c:(.text+0xc9): undefined reference to `rsvg_handle_get_dimensions'
svg2pdf.c:(.text+0x105): undefined reference to `cairo_pdf_surface_create'
svg2pdf.c:(.text+0x115): undefined reference to `cairo_create'
svg2pdf.c:(.text+0x12d): undefined reference to `rsvg_handle_render_cairo'
svg2pdf.c:(.text+0x139): undefined reference to `cairo_status'
svg2pdf.c:(.text+0x150): undefined reference to `cairo_status_to_string'
svg2pdf.c:(.text+0x183): undefined reference to `cairo_destroy'
svg2pdf.c:(.text+0x18f): undefined reference to `cairo_surface_destroy'
collect2: ld returned 1 exit status
make: *** [svg2pdf] Error 1

It was much longer than that, but I've installed a ton of *-dev stuff and got rid of all of the other issues but I can't get rid of the 'datrie' one. I've got libdatrie1 installed, along with libdatrie-dev. Doing 'dpkg -s libdatrie-dev' outputs this:

Package: libdatrie-dev
Status: install ok installed
Priority: optional
Section: libdevel
Installed-Size: 124
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libdatrie
Version: 0.2.2-1
Depends: libdatrie1 (= 0.2.2-1)
Suggests: libdatrie-doc (= 0.2.2-1)
Conflicts: libdatrie0-dev

Anyone got any idea how to get this compiled, or failing that, got an already statically compiled version that I could have?

Thanks!!

---

### Post by Zugzwang on 2010-01-21
> **dflock said:**
> I've been trying to get this to work too, and I think that I'm nearly there, but not quite.


Try "pkg-config --cflags --libs datrie-0.2" instead of something like "pkg-config --cflags --libs datrie". 

Indeed, there is no "datrie" pkg-config configuration file in those packages you installed, only a "datrie-0.2" one: [http://packages.ubuntu.com/karmic/i386/libdatrie-dev/filelist](http://packages.ubuntu.com/karmic/i386/libdatrie-dev/filelist)

---

