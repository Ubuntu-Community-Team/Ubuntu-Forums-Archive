---
title: "problem compiling garnome-2.15.90.1 in 6.06.1"
date: 2006-08-09
forum: Packaging and Compiling Programs
---

### Post by cerdiogenes on 2006-08-09
Hi,

I was trying to compile garnome-2.15.90.1 in 6.06.1 but this is giving me the followin error:

make[11]: Entrando no diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/platform/pango/work/main.d/pango-1.13.5/pango'
/bin/sh ../libtool --tag=CC --mode=link cc  -g -I/home/kadu/garnome/include -L/home/kadu/garnome/lib -O2 -pipe -Wall  -Wl,--export-dynamic -L/home/kadu/garnome/lib -o libpangoxft-1.0.la -rpath /home/kadu/garnome/lib -version-info 1303:2:1303 -export-symbols-regex "^pango_.*" pangoxft-font.lo pangoxft-fontmap.lo pangoxft-render.lo libpangoft2-1.0.la libpango-1.0.la -L/home/kadu/garnome/lib -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -L/home/kadu/garnome/lib -L/home/kadu/downloads/X11R7.0/modular/lib -lXft -lXrender -lX11 -lfontconfig -lfreetype -lz   -lm
[B]grep: /usr/lib/libfontconfig.la: No such file or directory
/bin/sed: can't read /usr/lib/libfontconfig.la: No such file or directory
libtool: link: `/usr/lib/libfontconfig.la' is not a valid libtool archive
[/B]make[11]: ** [libpangoxft-1.0.la] Erro 1
make[11]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/platform/pango/work/main.d/pango-1.13.5/pango'
make[10]: ** [all-recursive] Erro 1
make[10]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/platform/pango/work/main.d/pango-1.13.5/pango'
make[9]: ** [all] Erro 2
make[9]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/platform/pango/work/main.d/pango-1.13.5/pango'
make[8]: ** [all-recursive] Erro 1
make[8]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/platform/pango/work/main.d/pango-1.13.5'
make[7]: ** [all] Erro 2
make[7]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/platform/pango/work/main.d/pango-1.13.5'
make[6]: ** [build-work/main.d/pango-1.13.5/Makefile] Erro 2
make[6]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/platform/pango'
make[5]: ** [../../platform/pango/cookies/main.d/install] Erro 2
make[5]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/desktop/libgnomeprint'
make[4]: ** [../../desktop/libgnomeprint/cookies/main.d/install] Erro 2
make[4]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/desktop/libgnomeprintui'
make[3]: ** [../../desktop/libgnomeprintui/cookies/main.d/install] Erro 2
make[3]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/bindings/gnome-python'
make[2]: ** [../../bindings/gnome-python/cookies/main.d/install] Erro 2
make[2]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/admin/pessulus'
make[1]: ** [paranoid-install] Erro 2
make[1]: Saindo do diretório `/home/kadu/downloads/garnome/garnome-2.15.90.1/admin'
make: ** [paranoid-install] Erro 2

I have /usr/lib/libfontconfig.a and tried to make a link (/usr/lib/libfontconfig.la) to it, but I still get this error:

[B]libtool: link: `/usr/lib/libfontconfig.la' is not a valid libtool archive
[/B]

Thanks for any help,
Carlos.

---

### Post by ciscosurfer on 2006-08-09
Please check the main [garnome site]("http://www.gnome.org/projects/garnome/") for help.

---

### Post by cerdiogenes on 2006-08-11
I don't find anything useful in the garnome site. The only thing that was wrong with my environment is that I don't had all the dependencies installed, but now I have it and I still get the same error.

This is a better question for the garnome mailing list?

Thanks in advice,
Carlos.

---

### Post by ciscosurfer on 2006-08-11
Maybe...try posting your problem there (on the garnome mailing list)...I don't know if one exists, but I'm sure there is one.  But also keep searching here in UbuntuForums...somebody I'm sure has already had this problem as well.

---

### Post by avilella on 2006-08-14
Has anyone suceeded in using garnome to build gnome 2.16 for dapper?
Is there any howto in ubuntuforums?

This is what I have so far:

wget -b  [http://ftp.gnome.org/pub/GNOME/sources/garnome/2.15/garnome-2.15.91.tar.bz2](http://ftp.gnome.org/pub/GNOME/sources/garnome/2.15/garnome-2.15.91.tar.bz2)

#[http://www.gnome.org/projects/garnome/docs.html](http://www.gnome.org/projects/garnome/docs.html)

su
cpan
install XML::Parser

sudo apt-get install libpopt-dev


tar xjf garnome-2.15.91.tar.bz2
cd garnome-2.15.91/desktop
make paranoid-install


[===== NOW BUILDING:    gamin-0.1.7     =====]
        [fetch] complete for gamin.
        [checksum] complete for gamin.
        [extract] complete for gamin.
        [patch] complete for gamin.
        [fixup] complete for gamin.
lib/Makefile.am:1: INCLUDES defined both conditionally and unconditionally
libgamin/Makefile.am:1: INCLUDES defined both conditionally and unconditionally
libgamin/Makefile.am:58: variable `LDADDS' not defined
server/Makefile.am:1: INCLUDES defined both conditionally and unconditionally
server/Makefile.am:19: gam_server_SOURCES defined both conditionally and unconditionally
server/Makefile.am:78: gam_server_LDADD defined both conditionally and unconditionally
server/Makefile.am:78: variable `LDADDS' not defined
tests/Makefile.am:13: variable `LDADDS' not defined
python/Makefile.am:13: bad macro name `_gamin_la_LDFLAGS'
python/Makefile.am:23: bad macro name `_gamin_la_SOURCES'
python/Makefile.am:24: bad macro name `_gamin_la_LIBADD'
make[6]: *** [pre-configure] Error 1
make[6]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/bootstrap/gamin'
make[5]: *** [../../bootstrap/gamin/cookies/main.d/install] Error 2
make[5]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/platform/gnome-vfs'
make[4]: *** [../../platform/gnome-vfs/cookies/main.d/install] Error 2
make[4]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/platform/libgnome'
make[3]: *** [../../platform/libgnome/cookies/main.d/install] Error 2
make[3]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/platform/libbonoboui'
make[2]: *** [../../platform/libbonoboui/cookies/main.d/install] Error 2
make[2]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/platform/libgnomeui'
make[1]: *** [../../platform/libgnomeui/cookies/main.d/install] Error 2
make[1]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/desktop/bug-buddy'
make: *** [paranoid-install] Error 2

Has anyone gone further?

---

### Post by fflewddur on 2006-08-17
If you install the automake-1.9 package from Garnome's bootstrap directory, that error should go away.

---

### Post by avilella on 2006-08-17
ok, I installed more *-dev dependencies, and it went on for a good
while, but apparently, there is a glitch in control-center-2.15.91:


gnome-keyboard-properties-xkbpv.o: In function `xkb_layout_preview_update':/home/avilella/garnome/garnome-2.15.91/desktop/control-center/work/main.d/control-center-2.15.91/capplets/keyboard/gnome-keyboard-properties-xkbpv.c:113: undefined reference to `xkl_xkb_config_native_cleanup'
collect2: ld returned 1 exit status
make[5]: *** [gnome-keyboard-properties] Error 1
make[5]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/desktop/control-center/work/main.d/control-center-2.15.91/capplets/keyboard'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/desktop/control-center/work/main.d/control-center-2.15.91/capplets'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/desktop/control-center/work/main.d/control-center-2.15.91'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/desktop/control-center/work/main.d/control-center-2.15.91'
make[1]: *** [build-work/main.d/control-center-2.15.91/Makefile] Error 2
make[1]: Leaving directory `/home/avilella/garnome/garnome-2.15.91/desktop/control-center'
make: *** [paranoid-install] Error 2

---

### Post by Mac_D83 on 2006-08-28
I've had the same problem with garnome-2.15.92 and this is how I solved it.

1. Enable the universe repositories in /etc/apt/sources.list [(click here for help)]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

2. Install automake1.9 by opening a console and issuing the command
```
$ sudo apt-get install automake1.9
```

3. Make automake1.9 default instead of automake1.4 by issuing the command
```
$ sudo update-alternatives --config automake
```
[INDENT]You will get something like this[/INDENT]
```

There are 3 alternatives which provide `automake'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/bin/automake-1.4
      2        /usr/bin/automake-1.8
      3        /usr/bin/automake-1.9

Press enter to keep the default[*], or type selection number:

```
[INDENT]Select automake1.9[/INDENT]

You should now be good to go.

Cheers
Michael Mc Donnell
Copenhagen, Denmark

---

### Post by killhup on 2006-10-11
Hi there!

Follow this thread [http://fflewddur.livejournal.com/287880.html](http://fflewddur.livejournal.com/287880.html)

---

### Post by killhup on 2006-10-11
I also made some notice about problem with pwlib (CVS problem), actually a bug and to fix it type this.

* cd ../bootstrap/pwlib
* make makesum

Then go back into desktop directory and continue.

Hope this will be at any help

---

