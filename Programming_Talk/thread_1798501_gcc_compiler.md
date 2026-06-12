---
title: "gcc compiler"
date: 2011-07-06
forum: Programming Talk
---

### Post by Drenriza on 2011-07-06
Is it possible to compile a program made in visual studio c# with gcc?
If so, how do i do so? Ive been trying to find the correct commands, but i just cant find them.

Home someone can help me.
kind regards.

---

### Post by johnl on 2011-07-06
C# is a .NET language.  gcc is a C compiler, which is not related to C# or .NET.

You can use [mono](http:///www.mono-project.com) or **monodevelop** (the IDE) to compile and run C# code under Linux, assuming it doesn't use Windows-specific things like WPF or COM Interop.

---

### Post by Drenriza on 2011-07-06
what is WPF or COM Interop??

edit: when i have compiled a program with mono, how do i execute / start it?

---

### Post by PaulM1985 on 2011-07-06
WPF is Windows Presentation Framework.  It is an API for user interfaces.  Mono don't plan on implementing it: [http://www.mono-project.com/WPF](http://www.mono-project.com/WPF).  If you plan on using C# in linux and having it cross compatible for windows, you can use Windows Forms.  People might suggest Gtk#, but I think if you do that you need to include the Gtk dlls when you distribute your program.

COM is for Common Object Model.  This wikipedia article will explain it better than me: [http://en.wikipedia.org/wiki/Component_Object_Model](http://en.wikipedia.org/wiki/Component_Object_Model)

You can run a program you have compiled using mono by typing:
```

mono my_application.exe

```

in the terminal.  I think you can also run your app through MonoDevelop to avoid having to have the terminal open with it.

Paul

---

### Post by Drenriza on 2011-07-06
post removed.

---

