---
title: "Patching Question"
date: 2009-11-25
forum: Packaging and Compiling Programs
---

### Post by Yellow Pasque on 2009-11-25
EDIT: The problem I now face is running autoreconf after patches are applied in the PPA build system.

EDIT: This part is solved.
I am trying to reconfigure gnome-settings-daemon so that it supports multimedia keyboard shortcuts in GNOME through the use of gstreamer instead of Pulseaudio. There is an upstream patch in Debian for this against 2.28.0 ( [https://bugzilla.gnome.org/show_bug.cgi?id=571145](https://bugzilla.gnome.org/show_bug.cgi?id=571145) ), however, Ubuntu dropped this patch in their 2.28.1 karmic version. Is there an easy way to get this patch rebuilt for the current ubuntu source?

Simply taking the patch and putting it in the patches directory did not work for obvious reasons (but I tried anyway :P).

Thanks.

---

### Post by SevenMachines on 2009-11-25
try copying the source directory to a new directory, then try to apply the patch manually to the new source directory ( usually patch -p1 <my_patch in the source directory ) you can then see the parts that fail and make the changes manually. 
once all the changes you want are made you can create a new patch with
$ diff -ruN <old_source_directory> <new_source_directory> >new_patch.diff

---

### Post by Yellow Pasque on 2009-11-30
Ok, I manually made the patch (a little tedious, but it wasn't too large of a patch). I now see that the patch applies successfully in my PPA build (or claims to at least).
```
Trying patch debian/patches/20_gstreamer.patch at level 1 ... success.
```
and the log file for the patch:
```
patching file configure.ac
patching file plugins/media-keys/cut-n-paste/gvc-gstreamer-acme-vol.c
patching file plugins/media-keys/cut-n-paste/gvc-gstreamer-acme-vol.h
patching file plugins/media-keys/cut-n-paste/Makefile.am
patching file plugins/media-keys/gsd-media-keys-manager.c
patching file plugins/media-keys/Makefile.am
```

However, I can tell that at least some of the changes aren't taking effect. For example, one of the patches modifies the configure.ac file to add an extra field to the "report" that configure spits out at the end.

Part of the patch:
```
@@ -396,6 +436,7 @@
         dbus-1 system.d dir:      ${DBUS_SYS_DIR}
 
         Libnotify support:        ${have_libnotify}
-        PulseAudio support:       ${have_pulse}
**+	GStreamer support:        ${have_gstreamer}**        
+	PulseAudio support:       ${have_pulse}
         Profiling support:        ${enable_profiling}
```
The buildlog:
```
dbus-1 system.d dir:      ${sysconfdir}/dbus-1/system.d

        Libnotify support:        yes
        PulseAudio support:       false
        Profiling support:        no

```
Thanks for the help so far. I feel like I'm getting close..

EDIT: the buildlog: [https://launchpad.net/~dtl131/+archive/ppa/+build/1364902](https://launchpad.net/~dtl131/+archive/ppa/+build/1364902)

---

### Post by SevenMachines on 2009-11-30
on a quick look, i'm guessing that although configure.ac is being patched during the debuild, configure itself isn't rebuilt from .ac in your rules file maybe? so your still using the unchanged configure script in the build rather than the new patched one generated from .ac

---

### Post by Yellow Pasque on 2009-11-30
Yeah, I figured it out (at least for building locally). I wish I would've looked at your post an hour ago :P

I had to run autoreconf -f, and now my changes took effect, and the media-keys work without pulseaudio.

I can change this in the rules file? Thanks for the tip.

---

### Post by Yellow Pasque on 2009-12-01
So I'm now stuck again after taking a couple tries to get autoreconf in the correct section of the rules file.
```
if [ "reverse-patches" = "reverse-patches" ]; then rm -f debian/stamp-patched; fi
patches: debian/patches/01_xrdb.patch debian/patches/02_fix_randr.patch debian/patches/03_gdm_keyboard_variant_handling.patch debian/patches/16_use_synchronous_notifications.patch debian/patches/20_gstreamer.patch debian/patches/30_pkgconfig-path.patch debian/patches/40_xres_lcddefault.patch debian/patches/70_migrate_touchpad_config.patch debian/patches/71_fix_ldsm_notification_crash.patch debian/patches/90_autoreconf.patch debian/patches/91_gsd_locate_pointer_path_fix.patch
Patch debian/patches/91_gsd_locate_pointer_path_fix.patch is not applied.
Trying reverse patch debian/patches/90_autoreconf.patch at level 1 ... 0 ... 2 ... failure.
make: *** [reverse-patches] Error 1
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -d -us -uc -S failed
```
Don't know where to go from here.. :S

I would really like to start from fresh source, now that I know exactly what I need to do. Is this possible?

---

### Post by SevenMachines on 2009-12-01
hi there. you can add configure regeneration into debian/rules with something like

include /usr/share/cdbs/1/class/autotools.mk
DEB_AUTO_UPDATE_AUTOCONF := yes

though i dont know if this is the preferred way or manually generating ./configure and including that in the source tarball. maybe someone else knows. obviously the way you add autoconf to rules is very much down to how your rules file is set up and the above is just an example using cdbs

to start again with fresh source try
1. unpacking fresh source
2 copying the debian directory across from your old source tree
3. removing any stamp files in debian/ before building

note in general making changes in debian/ without first running debclean can cause problems depending on the files you alter.
generally i'd advise running debclean before making any changes just to be on the safe side unless theres some reason not to

---

### Post by Yellow Pasque on 2009-12-01
My thought was to try this to get the autoreconf to occur at the correct place in the procedure. I'm trying it now..
```
makebuilddir/gnome-settings-daemon::
        autoreconf --verbose -f
```

I also added the autotools.mk line and I've got debclean in my bag of tools now. Thanks for your patience and continued help.

---

### Post by Yellow Pasque on 2009-12-03
> DEB_AUTO_UPDATE_AUTOCONF := yes
I don't think this is for running autoreconf. It looks like it controls the version of autoconf.

> makebuilddir/gnome-settings-daemon::
        autoreconf --verbose -f
This runs the autoreconf, but does it before the patches are applied (I need the other way around).

> manually generating ./configure and including that in the source tarball.
That causes patches to fail.

---

### Post by Yellow Pasque on 2009-12-03
Ah, got it, it was;
```
configure/gnome-settings-daemon::
	autoreconf -f -v
```

..and now GNOME media-keys work without PulseAudio. Yay.
Pimping my PPA: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

Thanks again. Marking Solved.

---

### Post by SevenMachines on 2009-12-03
> **Temüjin said:**
> I don't think this is for running autoreconf. It looks like it controls the version of autoconf.
just to clear up, it doesnt run autoreconf but autoconf and it will do the trick and generate ./configure, whether its a good way or not is another question :)

---

