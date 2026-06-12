---
title: "Problem to install rrtdtool 1.4.7 from source"
date: 2012-02-24
forum: Packaging and Compiling Programs
---

### Post by caeros on 2012-02-24
I have problem to install rrdtool 1.4.7 from source, using ./configure, it shows this:

Find 3rd-Party Libraries
checking dbi/dbi.h usability... no
checking dbi/dbi.h presence... no
checking for dbi/dbi.h... no
checking tcpd.h usability... no
checking tcpd.h presence... no
checking for tcpd.h... no
checking for cairo_font_options_create in -lcairo... yes
checking cairo.h usability... no
checking cairo.h presence... no
checking for cairo.h... no
checking for pkg-config... pkg-config
checking for cairo_font_options_create in -lcairo... yes
checking cairo.h usability... yes
checking cairo.h presence... yes
checking for cairo.h... yes
checking for cairo_svg_surface_create in -lcairo... yes
checking cairo-svg.h usability... yes
checking cairo-svg.h presence... yes
checking for cairo-svg.h... yes
checking for cairo_pdf_surface_create in -lcairo... yes
checking cairo-pdf.h usability... yes
checking cairo-pdf.h presence... yes
checking for cairo-pdf.h... yes
checking for cairo_ps_surface_create in -lcairo... yes
checking cairo-ps.h usability... yes
checking cairo-ps.h presence... yes
checking for cairo-ps.h... yes
checking for pango_cairo_context_set_font_options in -lpangocairo-1.0... no
checking for pkg-config... (cached) pkg-config
checking for pango_cairo_context_set_font_options in -lpangocairo-1.0... no
configure: WARNING:
----------------------------------------------------------------------------
* I could not find a working copy of pangocairo. Check config.log for hints on why
  this is the case. Maybe you need to set LDFLAGS and CPPFLAGS appropriately
  so that compiler and the linker can find libpangocairo-1.0 and its header files. If
  you have not installed pangocairo, you can get it either from its original home on

     [http://ftp.gnome.org/pub/GNOME/sources/pango/1.28](http://ftp.gnome.org/pub/GNOME/sources/pango/1.28)

  You can find also find an archive copy on

     [http://oss.oetiker.ch/rrdtool/pub/libs](http://oss.oetiker.ch/rrdtool/pub/libs)

  The last tested version of pangocairo is 1.28.4.

       LIBS=-lcairo -lcairo -lcairo -lm  -lcairo -lpng12   -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lrt -lglib-2.0  
   LDFLAGS= -L/usr/local/lib/libpango-1.0 -L/usr/local/lib     -L/usr/local/lib   -pthread  
  CPPFLAGS= -I/usr/local/include/cairo -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pixman-1 -I/usr/local/include -I/usr/include/libpng12 -I/usr/include/freetype2   -pthread -I/usr/local/include/pango-1.0 -I/usr/local/include/cairo -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pixman-1 -I/usr/local/include -I/usr/include/freetype2 -I/usr/include/libpng12  

----------------------------------------------------------------------------
                
checking for glib_check_version in -lglib-2.0... yes
checking glib.h usability... yes
checking glib.h presence... yes
checking for glib.h... yes
checking for xmlParseFile in -lxml2... yes
checking libxml/parser.h usability... yes
checking libxml/parser.h presence... yes
checking for libxml/parser.h... yes
configure: error: Please fix the library issues listed above and try again.




but i installed pango-1.28.4 and i really dont know what is the problem, please help me :confused:

---

### Post by Paddy Landau on 2012-02-25
May I ask why you are installing from source and not from the Ubuntu Software Centre?

BTW, I presume your title should have read "rrdtool" and not "rrtdtool".

---

### Post by caeros on 2012-02-28
Paddy:
i work in a ubuntu server using ssh to conect with the server, and was installed all programas from source, so i cant install from Ubuntu Software Centre, i saw my error in the title sorry

---

### Post by Paddy Landau on 2012-02-29
Sorry, I don't know how to help with this. I would suggest downloading the .deb from the Ubuntu repository (using another computer) and then installing normally with the package manager.

---

### Post by oldos2er on 2012-02-29
Thread moved to Packaging and Compiling Programs.

---

