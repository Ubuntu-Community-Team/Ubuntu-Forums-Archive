---
title: "DllNotFoundException when running OpenTk application"
date: 2012-04-30
forum: Programming Talk
---

### Post by Chiel92 on 2012-04-30
Hi,

I want to program in C# - OpenTK - MonoDevelop on my ubuntu 12.04 computer.
I downloaded and installed everything as explained  here [http://www.opentk.com/doc/install](http://www.opentk.com/doc/install): I added the references to OpenTK.dll, added the OpenTK.dll.config in the binary folder, added the reference to System.Drawing.
However I get an exception when I run the given examples from the tutorial.
The message I get is "System.DllNotFoundException has been thrown. libX11.so".
When I run the generated binary from the terminal I get this (different) message:

```
Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for OpenTK.Graphics.GraphicsMode ---> System.PlatformNotSupportedException: Please, refer to http://www.opentk.com for more information.
  at OpenTK.Platform.Factory+UnsupportedPlatform.CreateGraphicsMode () [0x00000] in <filename unknown>:0 
  at OpenTK.Graphics.GraphicsMode..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at StarterKit.Game..ctor () [0x00000] in <filename unknown>:0 
  at StarterKit.Game.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeInitializationException: An exception was thrown by the type initializer for OpenTK.Graphics.GraphicsMode ---> System.PlatformNotSupportedException: Please, refer to http://www.opentk.com for more information.
  at OpenTK.Platform.Factory+UnsupportedPlatform.CreateGraphicsMode () [0x00000] in <filename unknown>:0 
  at OpenTK.Graphics.GraphicsMode..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at StarterKit.Game..ctor () [0x00000] in <filename unknown>:0 
  at StarterKit.Game.Main () [0x00000] in <filename unknown>:0
```Does anyone know what causes this problem? How can I solve it?
Any help very much appreciated.

BTW: Is this the right subforum to ask this question?

Regards

---

### Post by Chiel92 on 2012-05-04
Bump

---

### Post by daegul on 2012-05-21
I had this problem on 12.04 64-bit Desktop edition.

Installing libx11-dev solved it for me:
sudo apt-get install libx11-dev

---

### Post by Chiel92 on 2012-05-28
> **daegul said:**
> I had this problem on 12.04 64-bit Desktop edition.

Installing libx11-dev solved it for me:
sudo apt-get install libx11-dev

Hey, thanks!
It immediately solved my problem!
Do you know why this occured and what the libx11-dev package exactly does?

---

### Post by daegul on 2012-06-03
I believe libX11.so is to do with the X-window server (hence it's required to run up an OpenTK graphics context).  Beyond that I don't know.

Googling the library name showed which package libX11.so was in.  Installing that package installed the .so file.

It seems really odd for an X11 library to be missing when I'm running everything with through a Gnome environment.  I'm guessing it's something to do with having an x64 OS, but mono compiling to x86.

---

### Post by MadCow108 on 2012-06-03
that you need to install libx11-dev indicates a broken dllmap:
[http://www.mono-project.com/Config_DllMap](http://www.mono-project.com/Config_DllMap)

in some in *.config file there is probably something like this:
```
<configuration>
            <dllmap dll="somedll.dll" target="libX11.so"/>
</configuration>
```

the target is unversioned which is pretty much always wrong. Native libraries must always be versioned. The fix on 12.04 would be:
```
<dllmap dll="somedll.dll" target="libX11.so.6"/>
```


edit: this actually appears to be a bug in mono:
[https://bugs.launchpad.net/ubuntu/+source/mono/+bug/1008212](https://bugs.launchpad.net/ubuntu/+source/mono/+bug/1008212)
I'll see to get it fixed.

---

### Post by directhex on 2012-06-04
> **MadCow108 said:**
> that you need to install libx11-dev indicates a broken dllmap:
[http://www.mono-project.com/Config_DllMap](http://www.mono-project.com/Config_DllMap)

in some in *.config file there is probably something like this:
```
<configuration>
            <dllmap dll="somedll.dll" target="libX11.so"/>
</configuration>
```

the target is unversioned which is pretty much always wrong. Native libraries must always be versioned. The fix on 12.04 would be:
```
<dllmap dll="somedll.dll" target="libX11.so.6"/>
```


edit: this actually appears to be a bug in mono:
[https://bugs.launchpad.net/ubuntu/+source/mono/+bug/1008212](https://bugs.launchpad.net/ubuntu/+source/mono/+bug/1008212)
I'll see to get it fixed.

This is a correct analysis.

I fixed it in Debian as part of an effort to get OpenTK into the distro (which has [now happened](http://www.mail-archive.com/debian-devel-changes@lists.debian.org/msg343199.html)), but Ubuntu didn't get the fix yet.

Dllmap correctness is enforced by our packaging tools in Debian/Ubuntu - a package will fail to build if dh_clideps cannot resolve a valid library for a Dllmap. So this issue was discovered when packaging OpenTK, which was throwing the correctness error during build.

---

