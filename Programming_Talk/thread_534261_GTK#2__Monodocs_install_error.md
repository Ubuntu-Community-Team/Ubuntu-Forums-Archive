---
title: "GTK#2 / Monodocs install error"
date: 2007-08-25
forum: Programming Talk
---

### Post by cipherzero on 2007-08-25
when installing monodocs I get this error
```
Setting up monodoc-browser (1.2.3-0ubuntu1) ...
generating monodoc index...

** (/usr/lib/monodoc/browser.exe:28117): WARNING **: The following assembly referenced from /usr/lib/monodoc/browser.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=2)
     Version:    2.10.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodoc).


** (/usr/lib/monodoc/browser.exe:28117): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/monodoc/browser.exe:28117): WARNING **: Missing method Init in assembly /usr/lib/monodoc/browser.exe, type Gtk.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
dpkg: error processing monodoc-browser (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of monodoc:
 monodoc depends on monodoc-browser; however:
  Package monodoc-browser is not configured yet.
dpkg: error processing monodoc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 monodoc-browser
 monodoc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
any advice?

---

### Post by slavik on 2007-08-25
is gtk-sharp installed?

---

### Post by cipherzero on 2007-08-25
yes, gtk - sharp 2 is installed.
thanks for the quick reply.
although this error sounds like it is not in the GAC, it is.

~$ gacutil -l
The following assemblies are installed into the GAC:
...
gsf-sharp, Version=0.0.0.7, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gtk-dotnet, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gtk-sharp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
...
Number of items = 169

---

### Post by slavik on 2007-08-25
then echo out $MONO_HOME and check where the assemblies are installed to.

---

### Post by cipherzero on 2007-08-25
it seems that $MONO_HOME is not set.

```
~$ echo $MONO_HOME

~$
```

what should it be set to?

---

### Post by slavik on 2007-08-25
I misread your first statement. check MONO_PATH

it should be the directory(ies) where assemblies are installed

---

### Post by cipherzero on 2007-08-25
MONO_PATH is also not set...
but the confusing part is that gtk-sharp2 shows up in GAC using gacutil?
```

~$ echo $MONO_PATH

~$ 
```

---

### Post by cipherzero on 2007-08-27
is anyone else having trouble with the current version of mono  or gtk-sharp2?
i reinstalled, and that did not fix it, so it must be a problem with the package?

---

