---
title: "Haxe Sandy Class not found"
date: 2010-04-14
forum: Packaging and Compiling Programs
---

### Post by kramulous on 2010-04-14
Hi there,

  I'm finally getting around to writing a game and will start with Haxe.  I installed it via the installer ([http://haxe.org/download]("http://haxe.org/download")) and have setup the haxelib to install libraries to /home/username/Projects/Flash/haxelibs.

  I grabbed the sandy package (```
haxelib install sandy
```) to check out the examples and how they write their code.

  However, when I go into /home/username/Projects/Flash/haxelibs/sandy/3,1,2/tutos/example01 and compile by
```
haxe simplebox.hxml
```

I get: ```
../../sandy/HaxeTypes.hx:9: characters 0-13 : Class not found : flash.utils.ByteArray
```

  Now, a first hit on google gets that I need to haxe -swf-version 9 in the compile line but same result.  The .hxml file appears to be in order when referencing version 9.

  Anybody got any pointers?  I also get this on a Fedora 12 x86_64 machine.

---

