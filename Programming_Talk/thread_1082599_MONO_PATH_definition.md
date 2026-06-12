---
title: "MONO_PATH definition"
date: 2009-02-28
forum: Programming Talk
---

### Post by vladuz976 on 2009-02-28
I cannot run any mono projects that I checked out from source. I keep getting an error complaining about Mono.Addin assembly not found. I set my mono path to /usr/lib/mono but still same error:

```

danea@box:~/stage/tomboy/bin$ ./tomboy
[DEBUG]: NoteManager created with note path "/home/danea/.tomboy".

** (tomboy:26545): WARNING **: The following assembly referenced from /home/danea/stage/tomboy/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   Mono.Addins    (assemblyref_index=6)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/danea/stage/tomboy/lib/tomboy).


** (tomboy:26545): WARNING **: Could not load file or assembly 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (tomboy:26545): WARNING **: Missing method .ctor in assembly /home/danea/stage/tomboy/lib/tomboy/Tomboy.exe, type Mono.Addins.AddinEventHandler

** (tomboy:26545): WARNING **: Missing method .ctor in assembly /home/danea/stage/tomboy/lib/tomboy/Tomboy.exe, type Mono.Addins.AddinEventHandler

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'
  at Tomboy.AddinManager..ctor (System.String tomboy_conf_dir) [0x00000] 
  at Tomboy.NoteManager.CreateAddinManager () [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 
danea@box:~/stage/tomboy/bin$ 


```

---

### Post by vladuz976 on 2009-02-28
did a 
```

sudo updatedb

```

and then 

```

locate Mono.Addins.dll

```

then added 
```

export MONO_PATH= 'path where I found the dll'

```
to .bashrc (and do a 'source .bashrc')

that did it.

---

