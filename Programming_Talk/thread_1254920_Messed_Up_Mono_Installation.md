---
title: "Messed Up Mono Installation"
date: 2009-08-31
forum: Programming Talk
---

### Post by opticyclic on 2009-08-31
I followed [this guide]("http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx") to get the latest version of mono when actually what I wanted was the latest version of vbnc :redface:

Fortunately I kept track of the apps that were removed in the first few steps and I was able to add them back in using apt.
However, MonoDevelop no longer starts, probably as the underlying mono version is incorrect.
[See end of post for errors]

What do I need to do to revert the changes from that post?

I have removed the lines from ~/.bashrc but I don't want to just delete the src folder just yet as I suspect I need to do something else.


As a side question. How can I use a later version of vbnc with MonoDevelop? (Source [http://ftp.novell.com/pub/mono/sources-stable/](http://ftp.novell.com/pub/mono/sources-stable/))




```
~ $ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:14661): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Core.dll could not be loaded:
     Assembly:   Mono.Addins.Setup    (assemblyref_index=7)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:14661): WARNING **: Could not load file or assembly 'Mono.Addins.Setup, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:14661): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Ide.dll could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:14661): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:14661): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.exe could not be loaded:
     Assembly:   Mono.Addins    (assemblyref_index=3)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:14661): WARNING **: Could not load file or assembly 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:14661): WARNING **: Missing method get_Registry in assembly /usr/lib/monodevelop/bin/MonoDevelop.exe, type Mono.Addins.AddinManager

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'

```

---

### Post by directhex on 2009-09-01
Try reinstalling libmono-addins0.2-cil and libgtk2.0-cil

No promises though.

As for using a more recent version of VBNC, Try using a backport repo with some actual developer backing - anything which tries to update core system frameworks using "make install" is doomed to fail

---

### Post by DouglasAWh on 2009-09-02
> **directhex said:**
> Try reinstalling libmono-addins0.2-cil and libgtk2.0-cil

Any chance you could hook me up with the Fedora name of those packages? 

Gracias!

---

### Post by directhex on 2009-09-02
> **DouglasAWh said:**
> Any chance you could hook me up with the Fedora name of those packages? 

Gracias!

No idea, sorry

Oh, and the cause of the OP's issue, assuming he's the same guy I saw on IRC this morning: hand-compiled Mono in /usr/local

---

### Post by opticyclic on 2009-09-05
It wasn't actually me in IRC but you gave me an idea anyway :p
I removed everything mono related in Synaptic
Then deleted all mono dirs and related files in /usr/local
```
find . | grep mono
```
This meant removing stuff from
/usr/local/bin
/usr/local/etc
/usr/local/include
/usr/local/lib
/usr/local/shared

Anything that looked mono related.
I then reinstalled from Synaptic and I was back to normal.

Hopefully I haven't messed anything else up by the aggressive removal from /usr/local/

---

