---
title: "package 'mozilla-gtkmozembed' not found"
date: 2009-07-23
forum: Packaging and Compiling Programs
---

### Post by denish_hp_6383 on 2009-07-23
No package 'mozilla-gtkmozembed' found...


actually i want to develop my own web browser according my requirement in gtkmmm..
so i had download gtkmozembedmm-1.4.2 from gtkmms official web site....but when i m going to configure that using ./configure command, after half of the completion it prompts error like.....

[B]checking for GTKMOZEMBEDMM... configure: error: Package requirements (gtkmm-2.4 >= 2.4.0 mozilla-gtkmozembed >= 1.4) were not met:

No package 'mozilla-gtkmozembed' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTKMOZEMBEDMM_CFLAGS
and GTKMOZEMBEDMM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/B]
......even i had set pkg_config_path.....

actually there is no mozilla-gtkmozembed.pc file in my downloaded folder......
please help me................
...........................
..........................
thanks......

---

### Post by mc4man on 2009-07-25
try installing libgtkmm-2.4-dev

---

### Post by jaalburquerque on 2009-07-26
For mozilla-gtkmozembed, I think libxul-dev will work.

---

### Post by jaalburquerque on 2009-07-26
BTW, I think gtkmozembedmm has not been developed in over 3 years now.

---

### Post by denish_hp_6383 on 2009-07-27
I hav installed both of these library (libgtkmm-2.4-dev ,libgtkmm-2.4-dev)...but its still not work...
and giving same error...
pls any one tell me where can i get the package "mozilla-gtkmozembed.pc"

---

### Post by mc4man on 2009-07-27
I'm on hardy but try also installing xulrunner-1.9-dev

If your missing that or libgtkmm-2.4-dev  the same config error is produced

If your config succeeds look for this warning
checking for gnome-vfsmm-2.6... configure: WARNING: "gnome-vfsmm not found - htmlview example won't compile"
If that's an issue install libgnome-vfsmm-2.6-dev ( or whatever the version available if different

> doug@doug-laptop:~/Desktop/gikmm/gtkmozembedmm-1.4.2$ ./configure
.....clipped
checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.4 >= 2.4.0 mozilla-gtkmozembed >= 1.4... yes
checking GTKMOZEMBEDMM_CFLAGS... -fshort-wchar -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/atk-1.0 -I/usr/include/xulrunner-1.9.0.12/unstable -I/usr/include/nspr  
checking GTKMOZEMBEDMM_LIBS... -L/usr/lib/xulrunner-devel-1.9.0.12/lib -lgtkmm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lxpcomglue_s -lxul -lxpcom -lplds4 -lplc4 -lnspr4 -lpthread -ldl  
checking for gnome-vfsmm-2.6... yes
checking GNOMEVFSMM_CFLAGS... -pthread -DORBIT2=1 -I/usr/include/gnome-vfsmm-2.6 -I/usr/lib/gnome-vfsmm-2.6/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0  
checking GNOMEVFSMM_LIBS... -pthread -lgnomevfsmm-2.6 -lglibmm-2.4 -lgnomevfs-2 -lsigc-2.0 -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0  

---

### Post by denish_hp_6383 on 2009-07-29
thanx for your help.....
so I m now able to configure my package....
and i have configure it successfully...

But when i m going to compile using **make** command It prompt error below after half successful process.....................................................................................

[COLOR=Red][COLOR=Black]/gtkmozembedmm-1.4.2$ make
Making all in tools
make[1]: Entering directory `/home/justdial/Desktop/web_browser2/gtkmozembedmm-1.4.2/tools'
Making all in extra_defs_gen
make[2]: Entering directory `/home/justdial/Desktop/web_browser2/gtkmozembedmm-1.4.2/tools/extra_defs_gen'
/bin/bash ../../libtool --mode=link g++  -g -O2   -o generate_extra_defs  generate_defs_gtkmozembed.o  -L/usr/lib/xulrunner-devel-1.9.0.12/lib -lgtkmm-2.4 -lgiomm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lxpcomglue_s -lxul -lxpcom -lplds4 -lplc4 -lnspr4 -lpthread -ldl   -lglibmm_generate_extra_defs-2.4
g++ -g -O2 -o generate_extra_defs generate_defs_gtkmozembed.o  -L/usr/lib/xulrunner-devel-1.9.0.12/lib /usr/lib/libgtkmm-2.4.so /usr/lib/libgiomm-2.4.so /usr/lib/libgdkmm-2.4.so /usr/lib/libatkmm-1.6.so /usr/lib/libgtk-x11-2.0.so -lpangomm-1.4 /usr/lib/libcairomm-1.0.so /usr/lib/libglibmm-2.4.so /usr/lib/libsigc-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libpangoft2-1.0.so /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so /usr/lib/libgio-2.0.so /usr/lib/libcairo.so -lpixman-1 -lpng12 -lxcb-render-util -lxcb-render -lxcb -lXrender -lX11 -lm /usr/lib/libpango-1.0.so /usr/lib/libfreetype.so -lz -lfontconfig /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so -lxpcomglue_s -lxul -lxpcom -lplds4 -lplc4 -lnspr4 -lpthread -ldl /usr/lib/libglibmm_generate_extra_defs-2.4.so[/COLOR]
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_TraceChildren'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_CallTracer'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_ClearOperationCallback'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_GetOperationLimit'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_CallIteratorNext'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_NewObjectWithGivenProto'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_IsGCMarkingTracer'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_SetOperationLimit'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_ValueToIterator'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_GetterOnlyPropertyStub'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_PutArgsObject'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_GetOperationCallback'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_NewSystemObject'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_SetOperationCallback'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_SetScriptStackQuota'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_CloseIterator'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_PutCallObject'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_ThrowStopIteration'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_CallClass'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_ComputeThis'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_GetGlobalForObject'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `js_GetGCThingTraceKind'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_AlreadyHasOwnUCProperty'
/usr/lib/xulrunner-devel-1.9.0.12/lib/libxul.so: undefined reference to `JS_SetExtraGCRoots'
collect2: ld returned 1 exit status
make[2]: *** [generate_extra_defs] Error 1
make[2]: Leaving directory `/home/justdial/Desktop/web_browser2/gtkmozembedmm-1.4.2/tools/extra_defs_gen'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/justdial/Desktop/web_browser2/gtkmozembedmm-1.4.2/tools'
make: *** [all-recursive] Error 1


[COLOR=Black]Plz help me thanx[/COLOR]
[/COLOR]

---

