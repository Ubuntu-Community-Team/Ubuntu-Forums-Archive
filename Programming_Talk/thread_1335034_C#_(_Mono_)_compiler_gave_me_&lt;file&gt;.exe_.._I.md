---
title: "C# ( Mono ) compiler gave me &lt;file&gt;.exe .. I'm confused."
date: 2009-11-23
forum: Programming Talk
---

### Post by Prodigal Son on 2009-11-23
Is there a reason for such behavior ? If I get an EXE file, can I use it on other platforms ( including Windows ) without recompiling it ? :o

---

### Post by Aayu on 2009-11-23
C# is a Microsoft .NET language, even using MonoDevelop/Mono, whatever you compile will be compiled into a .exe.
 
Usually, Mono handles the emulation of that .exe file so you can run it in Linux and OS X.  But I have had cases where Mono doesn't do a very good job.  I had a Snake clone once, Mono could not display the moving Snake, yet it emulated a silverlight game just fine, if you are a C# developer, I strongely suggest you stick with VS2008, C# on other platforms is still kinda hit or miss..

---

### Post by spupy on 2009-11-23
> **Prodigal Son said:**
> Is there a reason for such behavior ? If I get an EXE file, can I use it on other platforms ( including Windows ) without recompiling it ? :o

That stumped me as well. Yes, you can run it on Windows. There are limitations - for example, if your program uses gtk#, you need the apropriate libraries installed in windows as well.

To run the program in Linux, use this command:
```
mono <file>.exe
```

---

### Post by automaton26 on 2009-11-23
You should be able to run it on Windows, but the required .NET framework may need to be installed under Windows first. Look in the Control Panel's "Add/Remove Programs" applet, for "Microsoft .NET Framework" - you'll need the matching version that the C# .exe was built against (1.1, 2.0 or 3.5).

In reality, there's no guarantee it'll work as intended, and will almost certainly need fully testing and debugging under Windows too (I use the free "Visual C# Express" tool).

I've tried porting C# apps the other way, from Windows to Linux, and I eventually got some console apps working (after supporting the filing system differences) but Windows.Forms apps still aren't working right. I should probably convert to GTK# for Form support, when running on Linux/Mono.

---

### Post by directhex on 2009-11-23
> **Prodigal Son said:**
> Is there a reason for such behavior ? If I get an EXE file, can I use it on other platforms ( including Windows ) without recompiling it ? :o

It is indeed a cross-platform app, assuming you haven't written any platform-specific code. In the land of Mono/.NET, .exe files are like .class files in Java. They re-used the file extension from non-portable Windows apps as a cheap workaround to make Windows treat apps as executable.

[http://www2.apebox.org/wordpress/wp-content/gallery/00-single/osctool3-gtk-01.png](http://www2.apebox.org/wordpress/wp-content/gallery/00-single/osctool3-gtk-01.png) and [http://www2.apebox.org/wordpress/wp-content/gallery/00-single/osctool3-win32-01.png](http://www2.apebox.org/wordpress/wp-content/gallery/00-single/osctool3-win32-01.png) are exactly the same app, compiled on Ubuntu.

---

