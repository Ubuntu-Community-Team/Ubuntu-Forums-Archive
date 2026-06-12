---
title: "Help Compiling Enlightenment Foundation Libraries (EFLs)"
date: 2015-06-01
forum: Packaging and Compiling Programs
---

### Post by Bentleythecomputer on 2015-06-01
(This is my first post. Is this is the right location?)
I'm running Lubuntu 15.04 on an old Dell Latitude D610. A long while ago, I decided to look for a different window manager other than LXDE. I found Enlightenment, which looks very nice and sound like it doesn't consume too many resources. The official Ubuntu repositories only have e17, and I'd like e19. I found a PPA which successfully installed e19, but it gave me a lot of error messages. I've known about Linux and have been using Ubuntu for little over a year, and have successfully compiled and installed the VICE emulator, so I wouldn't exactly call myself a complete newbie. I was confident enough to try to compile Enlightenment myself.

I downloaded all of the source tarballs for Enlightenment, Terminology (the Enlightenment terminal emulator), and all of the required libraries by the Enlightenment Foundation. The information on [https://www.enlightenment.org/download](https://www.enlightenment.org/download) says that the EFL libraries should be compiled first. I extracted the code, and repeatedly used ```
./configure -enable-systemd -enable-sdl
``` because I know a few applications that use SDL, and I know that Lubuntu 15.04 uses sysemd, so I figured why not enable support for it? I did this until I had installed all of the required development libraries, and configure finally exited without error. Here's the ending piece of the log:
```
------------------------------------------------------------------------
efl 1.14.0
------------------------------------------------------------------------

Configuration...: profile=release os=linux-gnu
  EFL API Set...: both
  CPU Extensions: i686 (+mmx +sse3)
  System Feature: coroutine=ucontext +inotify +atfile_source +ipv6
  Threads.......: POSIX (+spinlocks +barrier +affinity)
  Cryptography..: openssl
  X11...........: xlib
  OpenGL........: full
  C++11.........: yes
Eina............: yes (+systemd-journal)
Eo..............: yes (+eo-id)
Eolian..........: yes (+cxx)
Emile...........: yes (crypto=openssl)
Eet.............: yes
Evas............: yes (-lua-old +fontconfig +fribidi -harfbuzz +cserve -tile-rotate dither-mask=big)
  Engines.......: buffer=static -fb -psl1ght -gl-cocoa +gl-sdl -software-gdi -software-ddraw -wayland-egl -wayland-shm -drm -gl-drm +software-xlib +gl-xlib
  Image Loaders.: bmp=static eet=static generic=static +gif ico=static jpeg=static -jp2k pmaps=static png=static psd=static tga=static +tiff wbmp=static -webp xpm=static tgv=static dds=static
Ecore...........: yes (+systemd-daemon +glib -g-main-loop)
Ecore_Con.......: yes (-cares +local-sockets +abstract-sockets resolver=dns.c +systemd-daemon)
Ecore_File......: yes
Ecore_IMF.......: yes (-ibus -scim +xim -wayland)
Ecore_X.........: xlib (-xpresent -gesture +xinput2 -xinput22)
Ecore_SDL.......: yes
Ecore_Wayland...: no
IVI-Shell.......: no
Ecore_FB........: no ()
Ecore_Audio.....: yes (-alsa +pulseaudio +sndfile)
Ecore_Avahi.....: yes (+avahi-client)
Ecore_Evas......: yes (+extn +ews -fb -drm -gl-drm -psl1ght -opengl-cocoa +software-sdl +opengl-sdl -wayland-shm -wayland-egl -software-gdi -software-ddraw +software-x11 +opengl-x11)
Ector...........: yes
Eeze............: yes (+libmount -tizen)
EPhysics........: yes
Edje............: yes (+physics +multisense -lua-old)
Emotion.........: yes (+v4l2 -xine -gstreamer +gstreamer1 generic=static)
Ethumb..........: yes
Ethumb_Client...: yes
Elua............: yes
Tests...........: make check (inexplicitly enabled)
Examples........: make examples (make install-examples)
Documentation...: make doc
Compilation.....: make (or gmake)
  CPPFLAGS......: 
  CFLAGS........: -g -O2
  CXXFLAGS......: -g -O2 -std=gnu++11
  LDFLAGS.......: 
  
Installation....: make install (as root if needed, with 'su' or 'sudo')
  prefix........: /usr/local
  dbus units....: ${datarootdir}/dbus-1/services
  systemd units.: /usr/lib/systemd/user


#-------------------------------------------------------------------#
##==--                          ALERT                          --==##
#-------------------------------------------------------------------#

  Your installation prefix is *NOT* /usr so this means you need
to ensure some files are visible to dbus and systemd otherwise services cannot
be started when needed. You will need to do the following:

System-wide installation:
  ln -s /usr/local/share/dbus-1/services/org.enlightenment.Ethumb.service /usr/share/dbus-1/services/org.enlightenment.Ethumb.service
  ln -s /usr/local/share/dbus-1/services/org.enlightenment.Efreet.service /usr/share/dbus-1/services/org.enlightenment.Efreet.service

  or add "/usr/local/share" to $XDG_DATA_DIRS

User installation:
  ln -s /usr/local/share/dbus-1/services/org.enlightenment.Ethumb.service ~/.local/share/dbus-1/services/org.enlightenment.Ethumb.service
  ln -s /usr/local/share/dbus-1/services/org.enlightenment.Efreet.service ~/.local/share/dbus-1/services/org.enlightenment.Efreet.service

System-wide installation:
  ln -s /usr/lib/systemd/user/ethumb.service /usr/lib/systemd/user/ethumb.service
  ln -s /usr/lib/systemd/user/efreet.service /usr/lib/systemd/user/efreet.service

  or add "/usr/lib" to $XDG_DATA_DIRS or $XDG_CONFIG_DIRS

User installation:
  ln -s /usr/lib/systemd/user/ethumb.service ~/.config/systemd/user/ethumb.service
  ln -s /usr/lib/systemd/user/efreet.service ~/.config/systemd/user/efreet.service

#-------------------------------------------------------------------#
```

The warning at the end sounded like something related to *running* Enlightenment, so I thought that I would compile and install it first, then execute those commands.
However, when I then typed make, I got:

 ```
/bin/bash ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating doc/Makefile
config.status: creating doc/Doxyfile
config.status: creating doc/previews/Makefile
config.status: creating src/Makefile
config.status: creating src/benchmarks/eina/Makefile
config.status: creating src/benchmarks/eo/Makefile
config.status: creating src/benchmarks/evas/Makefile
config.status: creating src/examples/eina/Makefile
config.status: creating src/examples/eina_cxx/Makefile
config.status: creating src/examples/eet/Makefile
config.status: creating src/examples/eo/Makefile
config.status: creating src/examples/evas/Makefile
config.status: creating src/examples/ecore/Makefile
config.status: creating src/examples/ecore_avahi/Makefile
config.status: creating src/examples/eio/Makefile
config.status: creating src/examples/eldbus/Makefile
config.status: creating src/examples/ephysics/Makefile
config.status: creating src/examples/edje/Makefile
config.status: creating src/examples/emotion/Makefile
config.status: creating src/examples/ethumb_client/Makefile
config.status: creating src/examples/elua/Makefile
config.status: creating src/examples/eolian_cxx/Makefile
config.status: creating src/examples/elocation/Makefile
config.status: creating src/lib/eina/eina_config.h
config.status: creating src/lib/ecore_x/ecore_x_version.h
config.status: creating src/lib/efl/Efl_Config.h
config.status: creating spec/efl.spec
config.status: creating pc/evil.pc
config.status: creating pc/escape.pc
config.status: creating pc/eina.pc
config.status: creating pc/eina-cxx.pc
config.status: creating pc/emile.pc
config.status: creating pc/eet.pc
config.status: creating pc/eet-cxx.pc
config.status: creating pc/eo.pc
config.status: creating pc/eo-cxx.pc
config.status: creating pc/eolian.pc
config.status: creating pc/eolian-cxx.pc
config.status: creating pc/efl.pc
config.status: creating pc/efl-cxx.pc
config.status: creating pc/evas-fb.pc
config.status: creating pc/evas-opengl-x11.pc
config.status: creating pc/evas-opengl-sdl.pc
config.status: creating pc/evas-opengl-cocoa.pc
config.status: creating pc/evas-psl1ght.pc
config.status: creating pc/evas-software-buffer.pc
config.status: creating pc/evas-software-x11.pc
config.status: creating pc/evas-software-gdi.pc
config.status: creating pc/evas-software-ddraw.pc
config.status: creating pc/evas-software-sdl.pc
config.status: creating pc/evas-wayland-shm.pc
config.status: creating pc/evas-wayland-egl.pc
config.status: creating pc/evas-drm.pc
config.status: creating pc/evas.pc
config.status: creating pc/evas-cxx.pc
config.status: creating pc/ecore.pc
config.status: creating pc/ecore-cxx.pc
config.status: creating pc/ecore-con.pc
config.status: creating pc/ecore-ipc.pc
config.status: creating pc/ecore-file.pc
config.status: creating pc/ecore-input.pc
config.status: creating pc/ecore-input-evas.pc
config.status: creating pc/ecore-cocoa.pc
config.status: creating pc/ecore-drm.pc
config.status: creating pc/ecore-fb.pc
config.status: creating pc/ecore-psl1ght.pc
config.status: creating pc/ecore-sdl.pc
config.status: creating pc/ecore-wayland.pc
config.status: creating pc/ecore-win32.pc
config.status: creating pc/ecore-x.pc
config.status: creating pc/ecore-evas.pc
config.status: creating pc/ecore-imf.pc
config.status: creating pc/ecore-imf-evas.pc
config.status: creating pc/ecore-audio.pc
config.status: creating pc/ecore-audio-cxx.pc
config.status: creating pc/ecore-avahi.pc
config.status: creating pc/ector.pc
config.status: creating pc/embryo.pc
config.status: creating pc/eio.pc
config.status: creating pc/eio-cxx.pc
config.status: creating pc/eldbus.pc
config.status: creating pc/efreet.pc
config.status: creating pc/efreet-mime.pc
config.status: creating pc/efreet-trash.pc
config.status: creating pc/eeze.pc
config.status: creating pc/ephysics.pc
config.status: creating pc/edje.pc
config.status: creating pc/edje-cxx.pc
config.status: creating pc/emotion.pc
config.status: creating pc/ethumb.pc
config.status: creating pc/ethumb_client.pc
config.status: creating pc/elocation.pc
config.status: creating pc/elua.pc
config.status: creating dbus-services/org.enlightenment.Efreet.service
config.status: creating dbus-services/org.enlightenment.Ethumb.service
config.status: creating systemd-services/efreet.service
config.status: creating systemd-services/ethumb.service
config.status: creating po/Makefile.in
config.status: creating cmakeconfig/EflConfig.cmake
config.status: creating cmakeconfig/EflConfigVersion.cmake
config.status: creating cmakeconfig/EinaConfig.cmake
config.status: creating cmakeconfig/EinaConfigVersion.cmake
config.status: creating cmakeconfig/EioConfig.cmake
config.status: creating cmakeconfig/EioConfigVersion.cmake
config.status: creating cmakeconfig/EezeConfig.cmake
config.status: creating cmakeconfig/EezeConfigVersion.cmake
config.status: creating cmakeconfig/EoConfig.cmake
config.status: creating cmakeconfig/EoConfigVersion.cmake
config.status: creating cmakeconfig/EolianConfig.cmake
config.status: creating cmakeconfig/EolianConfigVersion.cmake
config.status: creating cmakeconfig/EolianCxxConfig.cmake
config.status: creating cmakeconfig/EolianCxxConfigVersion.cmake
config.status: creating cmakeconfig/EinaCxxConfig.cmake
config.status: creating cmakeconfig/EinaCxxConfigVersion.cmake
config.status: creating cmakeconfig/EoCxxConfig.cmake
config.status: creating cmakeconfig/EoCxxConfigVersion.cmake
config.status: creating cmakeconfig/EcoreCxxConfig.cmake
config.status: creating cmakeconfig/EcoreCxxConfigVersion.cmake
config.status: creating cmakeconfig/EvasCxxConfig.cmake
config.status: creating cmakeconfig/EvasCxxConfigVersion.cmake
config.status: creating cmakeconfig/EetCxxConfig.cmake
config.status: creating cmakeconfig/EetCxxConfigVersion.cmake
config.status: creating cmakeconfig/EetConfig.cmake
config.status: creating cmakeconfig/EetConfigVersion.cmake
config.status: creating cmakeconfig/EvasConfig.cmake
config.status: creating cmakeconfig/EvasConfigVersion.cmake
config.status: creating cmakeconfig/EcoreConfig.cmake
config.status: creating cmakeconfig/EcoreConfigVersion.cmake
config.status: creating cmakeconfig/EdjeConfig.cmake
config.status: creating cmakeconfig/EdjeConfigVersion.cmake
config.status: creating cmakeconfig/EldbusConfig.cmake
config.status: creating cmakeconfig/EldbusConfigVersion.cmake
config.status: creating cmakeconfig/EfreetConfig.cmake
config.status: creating cmakeconfig/EfreetConfigVersion.cmake
config.status: creating cmakeconfig/EthumbConfig.cmake
config.status: creating cmakeconfig/EthumbConfigVersion.cmake
config.status: creating cmakeconfig/EthumbClientConfig.cmake
config.status: creating cmakeconfig/EthumbClientConfigVersion.cmake
config.status: creating cmakeconfig/EmotionConfig.cmake
config.status: creating cmakeconfig/EmotionConfigVersion.cmake
config.status: creating cmakeconfig/EluaConfig.cmake
config.status: creating cmakeconfig/EluaConfigVersion.cmake
config.status: creating cmakeconfig/EmileConfig.cmake
config.status: creating cmakeconfig/EmileConfigVersion.cmake
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
make --no-print-directory all-recursive
Making all in src
  CC       bin/eolian/bin_eolian_eolian_gen-common_funcs.o
  CC       bin/eolian/bin_eolian_eolian_gen-eo_generator.o
  CC       bin/eolian/bin_eolian_eolian_gen-impl_generator.o
  CC       bin/eolian/bin_eolian_eolian_gen-legacy_generator.o
  CC       bin/eolian/bin_eolian_eolian_gen-types_generator.o
  CC       bin/eolian/bin_eolian_eolian_gen-main.o
  CC       lib/eina/lib_eina_libeina_la-eina_abi.lo
  CC       lib/eina/lib_eina_libeina_la-eina_accessor.lo
  CC       lib/eina/lib_eina_libeina_la-eina_array.lo
  CC       lib/eina/lib_eina_libeina_la-eina_benchmark.lo
  CC       lib/eina/lib_eina_libeina_la-eina_binbuf.lo
  CC       lib/eina/lib_eina_libeina_la-eina_binshare.lo
  CC       lib/eina/lib_eina_libeina_la-eina_convert.lo
  CC       lib/eina/lib_eina_libeina_la-eina_counter.lo
  CC       lib/eina/lib_eina_libeina_la-eina_cow.lo
  CC       lib/eina/lib_eina_libeina_la-eina_cpu.lo
  CC       lib/eina/lib_eina_libeina_la-eina_error.lo
  CC       lib/eina/lib_eina_libeina_la-eina_file_common.lo
  CC       lib/eina/lib_eina_libeina_la-eina_fp.lo
  CC       lib/eina/lib_eina_libeina_la-eina_hamster.lo
  CC       lib/eina/lib_eina_libeina_la-eina_hash.lo
  CC       lib/eina/lib_eina_libeina_la-eina_inarray.lo
  CC       lib/eina/lib_eina_libeina_la-eina_inlist.lo
  CC       lib/eina/lib_eina_libeina_la-eina_iterator.lo
  CC       lib/eina/lib_eina_libeina_la-eina_lalloc.lo
  CC       lib/eina/lib_eina_libeina_la-eina_list.lo
  CC       lib/eina/lib_eina_libeina_la-eina_log.lo
  CC       lib/eina/lib_eina_libeina_la-eina_magic.lo
  CC       lib/eina/lib_eina_libeina_la-eina_main.lo
  CC       lib/eina/lib_eina_libeina_la-eina_matrixsparse.lo
  CC       lib/eina/lib_eina_libeina_la-eina_mempool.lo
  CC       lib/eina/lib_eina_libeina_la-eina_mmap.lo
  CC       lib/eina/lib_eina_libeina_la-eina_module.lo
  CC       lib/eina/lib_eina_libeina_la-eina_prefix.lo
  CC       lib/eina/lib_eina_libeina_la-eina_quadtree.lo
  CC       lib/eina/lib_eina_libeina_la-eina_rbtree.lo
  CC       lib/eina/lib_eina_libeina_la-eina_rectangle.lo
  CC       lib/eina/lib_eina_libeina_la-eina_safety_checks.lo
  CC       lib/eina/lib_eina_libeina_la-eina_sched.lo
  CC       lib/eina/lib_eina_libeina_la-eina_share_common.lo
  CC       lib/eina/lib_eina_libeina_la-eina_simple_xml_parser.lo
  CC       lib/eina/lib_eina_libeina_la-eina_str.lo
  CC       lib/eina/lib_eina_libeina_la-eina_strbuf.lo
  CC       lib/eina/lib_eina_libeina_la-eina_strbuf_common.lo
  CC       lib/eina/lib_eina_libeina_la-eina_stringshare.lo
  CC       lib/eina/lib_eina_libeina_la-eina_tiler.lo
  CC       lib/eina/lib_eina_libeina_la-eina_thread.lo
  CC       lib/eina/lib_eina_libeina_la-eina_tmpstr.lo
  CC       lib/eina/lib_eina_libeina_la-eina_unicode.lo
  CC       lib/eina/lib_eina_libeina_la-eina_ustrbuf.lo
  CC       lib/eina/lib_eina_libeina_la-eina_ustringshare.lo
  CC       lib/eina/lib_eina_libeina_la-eina_value.lo
  CC       lib/eina/lib_eina_libeina_la-eina_value_util.lo
  CC       lib/eina/lib_eina_libeina_la-eina_xattr.lo
  CC       lib/eina/lib_eina_libeina_la-eina_thread_queue.lo
  CC       lib/eina/lib_eina_libeina_la-eina_matrix.lo
  CC       lib/eina/lib_eina_libeina_la-eina_quad.lo
  CC       lib/eina/lib_eina_libeina_la-eina_file.lo
  CC       modules/eina/mp/chained_pool/lib_eina_libeina_la-eina_chained_mempool.lo
  CC       modules/eina/mp/one_big/lib_eina_libeina_la-eina_one_big.lo
  CC       modules/eina/mp/pass_through/lib_eina_libeina_la-eina_pass_through.lo
  CCLD     lib/eina/libeina.la
  CC       lib/eolian/lib_eolian_libeolian_la-eo_lexer.lo
  CC       lib/eolian/lib_eolian_libeolian_la-eo_parser.lo
  CC       lib/eolian/lib_eolian_libeolian_la-eolian.lo
  CC       lib/eolian/lib_eolian_libeolian_la-eolian_database.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_fill.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_class.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_class_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_function.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_function_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_function_parameter.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_function_parameter_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_type.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_type_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_implement.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_implement_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_constructor.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_constructor_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_event.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_event_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_print.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_expr.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_expr_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_var.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_var_api.lo
  CC       lib/eolian/lib_eolian_libeolian_la-database_validate.lo
  CCLD     lib/eolian/libeolian.la
/usr/bin/ld: cannot find : No such file or directory
/usr/bin/ld: cannot find : No such file or directory
collect2: error: ld returned 1 exit status
Makefile:15807: recipe for target 'lib/eolian/libeolian.la' failed
make[2]: *** [lib/eolian/libeolian.la] Error 1
Makefile:2437: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
Makefile:1582: recipe for target 'all' failed
make: *** [all] Error 2
```

I have looked in /usr/bin, and ld is clearly there. This page: [http://stackoverflow.com/questions/20616961/usr-bin-ld-cannot-find-no-such-file-or-directory](http://stackoverflow.com/questions/20616961/usr-bin-ld-cannot-find-no-such-file-or-directory) suggest a rogue comma in the makefile. I only really know the basics of general programming, and I've never looked at C and can't read a makefile. I wouldn't know what commans are OK and which aren't. What do I do to get the EFLs to compile?

---

### Post by batden on 2015-06-03
Tarball release is aimed primarily at package maintainers.

Why are you not using Git?
[http://ubuntuforums.org/showthread.php?t=2274982](http://ubuntuforums.org/showthread.php?t=2274982)
(Remove thoroughly any previous installation of EFL/Enlightenment before running my script)

---

### Post by Bentleythecomputer on 2015-06-04
I didn't know E20 was out...do you think using Git would fix my problem? It's something to try. Thanks. I'll reply if it works.

---

### Post by Bentleythecomputer on 2015-06-05
I'm marking the thread as solved now. Your script worked great! Whenever I drag anything across the desktop, it locks up, but that's probably because I should turn off composting and some of the other fancy visual effects, considering the age of the hardware. It'll look great anyways. Now when I compile, I'll get my source code using git.

---

