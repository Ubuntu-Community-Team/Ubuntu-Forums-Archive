---
title: "can you get this .net app to run?"
date: 2006-12-28
forum: Programming Talk
---

### Post by dguido on 2006-12-28
I can't seem to get this app to run with Mono.  It depends on the included dll but it looks like mono never finds it.  This is what I get when I run it:

```
MONO_LOG_LEVEL=debug mono UPS.exe 
Mono-INFO: Assembly Loader probing location: '/usr/lib/mono/2.0/mscorlib.dll'.
Mono-INFO: Image addref mscorlib 0x8209e98 -> /usr/lib/mono/2.0/mscorlib.dll 0x8206288: 2

Mono-INFO: AOT failed to load AOT module /usr/lib/mono/2.0/mscorlib.dll.so: /usr/lib/mono/2.0/mscorlib.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: '/usr/lib/mono/2.0/mscorlib.dll'.
Mono-INFO: Config attempting to parse: '/usr/lib/mono/2.0/mscorlib.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/mscorlib/mscorlib.config'.
Mono-INFO: Config attempting to parse: '/home/dan/.mono/assemblies/mscorlib/mscorlib.config'.
Mono-INFO: Assembly mscorlib 0x8209e98 added to domain UPS.exe, ref_count=1

Mono-INFO: Config attempting to parse: '/etc/mono/config'.
Mono-INFO: Config attempting to parse: '/home/dan/.mono/config'.
Mono-INFO: Assembly Loader probing location: 'UPS.exe'.
Mono-INFO: Image addref UPS 0x82494f8 -> /home/dan/UPS.exe 0x82034d0: 3

Mono-INFO: Assembly Ref addref UPS 0x82494f8 -> mscorlib 0x8209e98: 2

Mono-INFO: Assembly UPS 0x82494f8 added to domain UPS.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module /home/dan/UPS.exe.so: /home/dan/UPS.exe.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: 'UPS.exe'.
Mono-INFO: Config attempting to parse: '/home/dan/UPS.exe.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/UPS/UPS.config'.
Mono-INFO: Config attempting to parse: '/home/dan/.mono/assemblies/UPS/UPS.config'.
Mono-INFO: Assembly Loader probing location: 'UPS.exe'.
Mono-INFO: AOT failed to load AOT module /home/dan/UPS.exe.so: /home/dan/UPS.exe.so: cannot open shared object file: No such file or directory

Mono-INFO: DllImport attempting to load: 'rscoree.dll'.
Mono-INFO: DllImport loading location: 'librscoree.dll.so'.
Mono-INFO: DllImport error loading library: 'librscoree.dll.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './librscoree.dll.so'.
Mono-INFO: DllImport error loading library './librscoree.dll.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'rscoree.dll'.
Mono-INFO: DllImport error loading library 'rscoree.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'librscoree.so'.
Mono-INFO: DllImport error loading library: 'librscoree.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './librscoree.so'.
Mono-INFO: DllImport error loading library './librscoree.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'rscoree'.
Mono-INFO: DllImport error loading library 'rscoree.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'librscoree.dll'.
Mono-INFO: DllImport error loading library: 'librscoree.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './librscoree.dll'.
Mono-INFO: DllImport error loading library './librscoree.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'librscoree.dll'.
Mono-INFO: DllImport error loading library 'librscoree.dll: cannot open shared object file: No such file or directory'.

(UPS.exe:2336): Mono-WARNING **: DllImport unable to load library 'librscoree.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport attempting to load: 'rscoree.dll'.
Mono-INFO: DllImport loading location: 'librscoree.dll.so'.
Mono-INFO: DllImport error loading library: 'librscoree.dll.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './librscoree.dll.so'.
Mono-INFO: DllImport error loading library './librscoree.dll.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'rscoree.dll'.
Mono-INFO: DllImport error loading library 'rscoree.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'librscoree.so'.
Mono-INFO: DllImport error loading library: 'librscoree.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './librscoree.so'.
Mono-INFO: DllImport error loading library './librscoree.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'rscoree'.
Mono-INFO: DllImport error loading library 'rscoree.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'librscoree.dll'.
Mono-INFO: DllImport error loading library: 'librscoree.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './librscoree.dll'.
Mono-INFO: DllImport error loading library './librscoree.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'librscoree.dll'.
Mono-INFO: DllImport error loading library 'librscoree.dll: cannot open shared object file: No such file or directory'.

(UPS.exe:2336): Mono-WARNING **: DllImport unable to load library 'librscoree.dll: cannot open shared object file: No such file or directory'.

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for . ---> System.DllNotFoundException: rscoree.dll
  at (wrapper managed-to-native) <PrivateImplementationDetails>:_RSEEStartup (int)
  at <PrivateImplementationDetails>.$$method-1 () [0x00000] 
  at ...cctor () [0x00000] --- End of inner exception stack trace ---

```

---

### Post by ohgod on 2006-12-28
It looks like the rscoree.dll file is an assembly that Mono cannot load.

What is the rscoree.dll file?  It doesn't appear to be a .Net assembly.  Is it related to the fact that your .exe is obfuscated?  You might want to try building without the obfuscation and try again.

---

### Post by dguido on 2006-12-28
It's not my app.  It's from [http://www.proventsure.com/ups.html](http://www.proventsure.com/ups.html)

---

### Post by ohgod on 2006-12-28
Hmm.  You might be out of luck then.  From some googling, it seems that dll file is used by a .net code obfuscator.  I'm guessing that since they obfuscated the code, they're not going to give you the source.  You could try contacting them I suppose.  Sorry I couldn't help.

---

