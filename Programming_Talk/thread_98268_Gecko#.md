---
title: "Gecko#?"
date: 2005-12-02
forum: Programming Talk
---

### Post by celloandy on 2005-12-02
I'm trying to use Gecko# in a simple mono program, and it compiles fine, but for some reason, it doesn't work. I'm compiling using the following command:
```
mcs -pkg:gtk-sharp-2.0 -pkg:gecko-sharp-2.0 Main.cs
``` As I said, this compiles without complaint, but when I try to actually run "mono Main.exe" it spits out a whole bunch of crap:
```
$ mono Main.exe

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Gecko.WebControl ---> System.DllNotFoundException: gtkembedmoz.dll
in (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_get_type ()
in <0x00014> Gecko.WebControl:get_GType ()
in <0x00026> GtkSharp.GeckoSharp.ObjectManager:Initialize ()
in <0x00007> Gecko.WebControl:.cctor ()--- End of inner exception stack trace ---

in <0x00000> <unknown method>
in <0x0008f> RssThing:.ctor ()
in <0x00016> RssThing:Main (System.String[] args)
``` So it seems that the problem is that gtkembedmoz.dll is missing, and it does, indeed, seem not to be there. Everything I'm supposed to have seems to be installed, and Monodoc, which also uses Gecko#, works fine. What's the secret to making this thing work?

Andrew

---

### Post by celloandy on 2005-12-03
Fixed it.  Adding /usr/lib/mozilla-firefox/ to LD_LIBRARY_PATH seems to make things work.

Andrew

---

