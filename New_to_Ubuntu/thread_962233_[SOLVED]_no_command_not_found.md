---
title: "[SOLVED] no: command not found"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Zularan on 2008-10-29
Having trouble compiling.  It's an alarm extension for Banshee I'm trying out.

Configured okay but failing to compile with this error.

```
 make
Making all in build
make[1]: Entering directory `/home/dave/Desktop/banshee-alarm-extension-0.4.1/build'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/Desktop/banshee-alarm-extension-0.4.1/build'
Making all in po
make[1]: Entering directory `/home/dave/Desktop/banshee-alarm-extension-0.4.1/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/Desktop/banshee-alarm-extension-0.4.1/po'
Making all in src
make[1]: Entering directory `/home/dave/Desktop/banshee-alarm-extension-0.4.1/src'
no -debug -out:Banshee.AlarmClock.dll -target:library -r:/usr/lib/banshee-1/Banshee.Widgets.dll -r:/usr/lib/banshee-1/Banshee.ThickClient.dll -r:/usr/lib/banshee-1/Banshee.Services.dll -r:Mono.Cairo -r:/usr/lib/banshee-1/Hyena.Gui.dll -r:/usr/lib/banshee-1/Banshee.Core.dll -r:System -r:/usr/lib/banshee-1/Mono.Media.dll -r:/usr/lib/cli/taglib-sharp-2.0/taglib-sharp.dll -r:/usr/lib/cli/ndesk-dbus-1.0/NDesk.DBus.dll -r:/usr/lib/cli/ndesk-dbus-glib-1.0/NDesk.DBus.GLib.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll -r:/usr/lib/cli/mono-addins-0.2/Mono.Addins.dll -r:System.Data -r:Mono.Data.SqliteClient -r:Mono.Posix -r:/usr/lib/banshee-1/Hyena.dll -r:/usr/lib/banshee-1/MusicBrainz.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll    -resource:./Banshee.AlarmClock.addin.xml,Banshee.AlarmClock.addin.xml  -resource:./AlarmMenu.xml,AlarmMenu.xml ./Alarm.cs ./AlarmClockService.cs ./AlarmConfigDialog.cs ./ConfigurationDialog.cs ./GConfSchemas.cs ./SleepTimerConfigDialog.cs ./VolumeFade.cs ./AssemblyInfo.cs
/bin/bash: no: command not found
make[1]: *** [Banshee.AlarmClock.dll] Error 127
make[1]: Leaving directory `/home/dave/Desktop/banshee-alarm-extension-0.4.1/src'
make: *** [all-recursive] Error 1

```

What is 'no' or Error 127? I've been Googling for an hour and am lost here as to what it's asking for.

---

### Post by wardrich on 2008-10-29
It's almost like there's a problem in the code, like something should be in quotes, but isn't...

Is it possible for you to paste the code up here?

---

### Post by macogw on 2008-10-29
It's just a broken Makefile.  You found a bug!  And you should probably report it to whomever makes this extension because it needs to be fixed.  In the meantime, if you post the file, we can maybe figure out exactly how to fix it.

---

### Post by Zularan on 2008-10-29
Sure thing, it's from here

[http://code.google.com/p/banshee-unofficial-plugins/downloads/list](http://code.google.com/p/banshee-unofficial-plugins/downloads/list)

---

### Post by macogw on 2008-10-29
Real quick (not relevant to this little piece exactly, but overall...):
Are you using the versions of Banshee it says to be using for 0.4.1 or are you using the version included in 8.04?

---

### Post by Zularan on 2008-10-29
Yeah, 1.2 and just installed the dev 1.3.3 version to play around with just now. 

Also, I'm using 8.10 (initial version from default repos for Intrepid).

---

### Post by directhex on 2008-10-29
It's a dumb (but common) error in makefiles for Mono apps.

Make sure you have mono-gmcs installed, and mono-mcs too to be sure.

---

### Post by Zularan on 2008-10-29
> **directhex said:**
> It's a dumb (but common) error in makefiles for Mono apps.

Make sure you have mono-gmcs installed, and mono-mcs too to be sure.

That did the trick, I had to install 'mono-gmcs' before I created this thread to get it to configure. 

However, 'mono-mcs' allowed the build to succeed now, thanks a lot :)

---

### Post by macogw on 2008-10-29
On line 351 in configure, try changing:
 if test $as_have_required = no; then

to
if test "x$as_have_required" = "xno"; then

Then re-run ./configure and make

---

