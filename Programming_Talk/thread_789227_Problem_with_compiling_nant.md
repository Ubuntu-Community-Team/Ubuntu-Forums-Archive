---
title: "Problem with compiling nant"
date: 2008-05-10
forum: Programming Talk
---

### Post by Domie on 2008-05-10
When I want to compile nant with make, I get this error:

```
mkdir -p bootstrap
cp -R lib/ bootstrap/lib
# Mono loads log4net before privatebinpath is set-up, so we need this in the same directory
# as NAnt.exe
cp lib/common/neutral/log4net.dll bootstrap
cp src/NAnt.Console/App.config bootstrap/NAnt.exe.config
mcs -target:exe -define:MONO -out:bootstrap/NAnt.exe -r:bootstrap/log4net.dll \
                -recurse:src/NAnt.Console/*.cs src/CommonAssemblyInfo.cs

** (/usr/lib/mono/1.0/mcs.exe:10568): WARNING **: The following assembly referenced from /home/dominique/development/nant/bootstrap/log4net.dll could not be loaded:
     Assembly:   System.Data    (assemblyref_index=2)
     Version:    1.0.3300.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/dominique/development/nant/bootstrap/).


** (/usr/lib/mono/1.0/mcs.exe:10568): WARNING **: Could not load file or assembly 'System.Data, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (/usr/lib/mono/1.0/mcs.exe:10568): WARNING **: Could not load file or assembly 'System.Data, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

Unhandled Exception: System.Reflection.ReflectionTypeLoadException: The classes in the module cannot be loaded.
  at (wrapper managed-to-native) System.Reflection.Assembly:GetTypes (bool)
  at System.Reflection.Assembly.GetExportedTypes () [0x00000]
  at Mono.CSharp.TypeManager.LoadAllImportedTypes () [0x00000]
  at Mono.CSharp.Driver.MainDriver (System.String[] args) [0x00000]
  at Mono.CSharp.Driver.Main (System.String[] args) [0x00000]
make: *** [bootstrap/NAnt.exe] Fout 1
```

any ideas?

---

### Post by Domie on 2008-05-12
No?

---

### Post by Domie on 2008-05-15
bump...

---

### Post by Domie on 2008-05-25
bump...

---

### Post by Domie on 2008-05-25
> **Old Marcus said:**
> Obviously he has never touched open source. Or if he has, it was back in the 80's. Support for open source applications is far better than support for MS software. Here I have a problem, I can post my problem or find a thread that addresses it and bang, I'm done.



Bang, please???

---

