---
title: "Linking Problem while Compiling glib"
date: 2012-11-15
forum: Packaging and Compiling Programs
---

### Post by dodle on 2012-11-15
[SIZE="4"][COLOR="YellowGreen"]_This thread is marked as solved but it was solved by compiling a different version of glib_[/COLOR][/SIZE]

I'm am trying to compile glib-2.34.2 with MinGW. I have already had to fix 2 or three compile errors but now I am faced with a linking problem that I can't figure out.

Here are the configure options that I supplied and the output of the error:
```
$ ../configure --prefix=/mingw --disable-shared --enable-static --disable-libelf CFLAGS=-static-libgcc -march=i486 CXXFLAGS=-static-libgcc -march=i486 PKG_CONFIG_PATH=/c/Development/Libraries/gtk-3.7.0/lib/pkgconfig LDFLAGS=-L/c/Development/Libraries/gtk-3.7.0/lib CPPFLAGS=-I/c/Development/Libraries/gtk-3.7.0/include
```
```
....
  CC       glib-compile-resources.o
  CCLD     glib-compile-resources.exe
  CC       gsettings-tool.o
  CCLD     gsettings.exe
  CC       gdbus-tool.o
  CCLD     gdbus.exe
./.libs/libgio-2.0.a(libgio_2_0_la-gdbusaddress.o):gdbusaddress.c:(.text+0x1d9a): undefined referen   ce to `_g_io_win32_get_module'
collect2.exe: error: ld returned 1 exit status
make[4]: *** [gdbus.exe] Error 1
....
```

The problem appears to be in this area of gio/gdbusaddress.c:
[php]....
  if (address == NULL)
    {
      gio_path[MAX_PATH] = 0;
      if (GetModuleFileNameW (_g_io_win32_get_module (), gio_path, MAX_PATH))
	{
	  PROCESS_INFORMATION pi = { 0 };
	  STARTUPINFOW si = { 0 };
	  BOOL res;
	  wchar_t gio_path_short[MAX_PATH];
	  wchar_t rundll_path[MAX_PATH*2];
	  wchar_t args[MAX_PATH*4];
....[/php]

Here are the lines where I think the problem is in the Makefile:
[php]....
gdbus_LDADD = libgio-2.0.la \
	$(top_builddir)/glib/libglib-2.0.la 		\
	$(top_builddir)/gobject/libgobject-2.0.la
....

....
gdbus$(EXEEXT): $(gdbus_OBJECTS) $(gdbus_DEPENDENCIES) $(EXTRA_gdbus_DEPENDENCIES) 
	@rm -f gdbus$(EXEEXT)
	$(AM_V_CCLD)$(LINK) $(gdbus_OBJECTS) $(gdbus_LDADD) $(LIBS)
....[/php]

I don't know if I'm correct but it sounds like gdbus.exe is not being linked to the object file that contains _g_io_win32_get_module.

**----- Edit -----**

This problem occurs when building in the gio sub-directory. Also I have just noted that none of the executable produced so far actually work.

**----- Edit -----**

I've decided to try and compile the development version, 2.35.1, as well. I've run on to a couple of small problems but the executables produced seem to be working. Once again, most of the problems seem to be in the "gio" directory.

**----- SOLVED -----**

Hoorah! I able to compile a shared version of 2.35.1. I'm going to try a static version and I will post the fixes that I came across.

**----- Edit -----**

Well, static builds don't seem to work on my machine. Here is the patch that I created. It does not solve all of the issues that I faced:

```
diff -rupN glib-2.35.1/gio/gthreadedresolver.c glib-2.35.1-new/gio/gthreadedresolver.c
--- glib-2.35.1/gio/gthreadedresolver.c	2012-10-16 09:40:06 -0700
+++ glib-2.35.1-new/gio/gthreadedresolver.c	2012-11-14 23:59:14 -0800
@@ -204,12 +204,12 @@ do_lookup_records (GTask         *task,
 {
   LookupRecordsData *lrd = task_data;
   GList *targets;
+  GError *error = NULL;
 #if defined(G_OS_UNIX)
   gint len = 512;
   gint herr;
   GByteArray *answer;
   gint rrtype;
-  GError *error = NULL;
 
   rrtype = _g_resolver_record_type_to_rrtype (lrd->record_type);
   answer = g_byte_array_new ();
diff -rupN glib-2.35.1/gio/gunixmounts.h glib-2.35.1-new/gio/gunixmounts.h
--- glib-2.35.1/gio/gunixmounts.h	2012-10-13 08:01:55 -0700
+++ glib-2.35.1-new/gio/gunixmounts.h	2012-11-14 22:45:11 -0800
@@ -78,7 +78,7 @@ gint           g_unix_mount_point_compar
 const char *   g_unix_mount_point_get_mount_path    (GUnixMountPoint    *mount_point);
 const char *   g_unix_mount_point_get_device_path   (GUnixMountPoint    *mount_point);
 const char *   g_unix_mount_point_get_fs_type       (GUnixMountPoint    *mount_point);
-GLIB_AVAILABLE_IN_2_32
+GLIB_AVAILABLE_IN_2_32;
 const char *   g_unix_mount_point_get_options       (GUnixMountPoint    *mount_point);
 gboolean       g_unix_mount_point_is_readonly       (GUnixMountPoint    *mount_point);
 gboolean       g_unix_mount_point_is_user_mountable (GUnixMountPoint    *mount_point);
diff -rupN glib-2.35.1/gio/tests/Makefile.in glib-2.35.1-new/gio/tests/Makefile.in
--- glib-2.35.1/gio/tests/Makefile.in	2012-10-22 13:19:39 -0700
+++ glib-2.35.1-new/gio/tests/Makefile.in	2012-11-15 00:44:27 -0800
@@ -1011,7 +1011,7 @@ pyexecdir = @pyexecdir@
 pythondir = @pythondir@
 sbindir = @sbindir@
 sharedstatedir = @sharedstatedir@
-srcdir = @srcdir@
+srcdir = @srcdir@/
 sysconfdir = @sysconfdir@
 target_alias = @target_alias@
 top_build_prefix = @top_build_prefix@
```

Another problem I had was in the gio/Makefile. I had to change the line:
```
ZLIB_LIBS = -L -lz
```
to:
```
ZLIB_LIBS = -lz
```
before I could compile. But that could just have to do with the version of libtool that is installed.

I also got the following error:
```
No rule to make target `../../../gio/tests\test1.txt', needed by `test_resources.c'.
```
I fixed it by changing a line in gio/tests/Makefile from:
```
srcdir = ../../../gio/tests
```
to:
```
srcdir = ../../../gio/tests/
```

---

