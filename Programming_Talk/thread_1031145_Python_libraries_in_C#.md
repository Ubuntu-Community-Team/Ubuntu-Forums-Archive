---
title: "Python libraries in C#"
date: 2009-01-05
forum: Programming Talk
---

### Post by aquavitae on 2009-01-05
Hi

Does anyone know anything about using python libraries in C# program?  I am about to start writing a library which will be used in a commercial programming written in C# in Windows. I'd prefer to use Python, but I need to make sure that it can be used without the commercial developer needing anything extra to deal with the different language.  I know Mono C# can use libraries written in different languages but I don't know how its done or whether it also applies to .NET. Does anyone have any advice on this?

---

### Post by Kilon on 2009-01-05
> **aquavitae said:**
> Hi

Does anyone know anything about using python libraries in C# program?  I am about to start writing a library which will be used in a commercial programming written in C# in Windows. I'd prefer to use Python, but I need to make sure that it can be used without the commercial developer needing anything extra to deal with the different language.  I know Mono C# can use libraries written in different languages but I don't know how its done or whether it also applies to .NET. Does anyone have any advice on this?

Before someone more experienced than me steps in for a highly useful advice , I will recommend IRONPYTHON. 

[http://www.codeplex.com/Wiki/View.aspx?ProjectName=IronPython](http://www.codeplex.com/Wiki/View.aspx?ProjectName=IronPython)

you can use .NET from IronPython and vice versa. Have fun!!!

---

### Post by directhex on 2009-01-05
CLI has a relatively robust system for calling into non-CLI libraries called "P/Invoke" - however, it pretty much only works with C libs, so you'd need to write a C bridge between the non-C (Python) and CLI (C#) code. Messy. Doable, but messy. This is how Qyoto works (It uses a C bridge which can call into the C++ Qt library, to offer CLI bindings)

Kilon probably has the best idea with IronPython

---

### Post by aquavitae on 2009-01-05
Thanks for the replies.

I had a look at IronPython, but it looks like the C# dev would have to implement it as well as me - is that correct or am I misunderstanding something? I don't want to make the C# dev have to use any extra packages.

If I decide to just stick to C#, will there be any issues with me writing on Linux in Mono and the other dev writing on Windows in .Net?

---

### Post by directhex on 2009-01-05
> **aquavitae said:**
> Thanks for the replies.

I had a look at IronPython, but it looks like the C# dev would have to implement it as well as me - is that correct or am I misunderstanding something? I don't want to make the C# dev have to use any extra packages.

He'd need IronPython.dll in his GAC of the same folder as your assembly

> If I decide to just stick to C#, will there be any issues with me writing on Linux in Mono and the other dev writing on Windows in .Net?

Not if you write good code (i.e. don't do anything stupid like using 'tmpdir + "\DATA"' instead of System.IO.Path.Combine( tmpdir, "DATA" );)

---

### Post by Kilon on 2009-01-05
> **aquavitae said:**
> Thanks for the replies.

I had a look at IronPython, but it looks like the C# dev would have to implement it as well as me - is that correct or am I misunderstanding something? I don't want to make the C# dev have to use any extra packages.

If I decide to just stick to C#, will there be any issues with me writing on Linux in Mono and the other dev writing on Windows in .Net?

Code written in IRONPYTHON should generally work out of the box in a C# app. 

I have no experience with IRONPYTHON. But I have worked with JYTHON which is the same thing but for JAVA instead of .NET. 

Jython has no problems using JAVA libraries or exporting its own for JAVA. 

The problem is using the python libraries , because the python libraries are written in C++ and might not be available for Ironpython. But interfacing with .NET should be direct and requiring no additional coding.

---

### Post by aquavitae on 2009-01-05
Ok, let me see if I've got it right then:

I write my code and provide a hierarchy or .py (.pyc or .pyo?) files. The C# dev needs to copy my hierarhcy and IronPython.dll (which I assume comes directly from the IronPython distribution) into the folder containing his .cs files. Then he can simply access my classes using the normal methods, e.g. 'using' statements. When he compiles to .exe, will he still need the .py files, or will they be compiled into the exe.  And IronPython.dll?  I would assume that since it is a dll it would still be required in the path.

Another way of doing it might be to compile my files to a dll - would IronPython.dll still be required then?

---

### Post by directhex on 2009-01-05
> **aquavitae said:**
> Ok, let me see if I've got it right then:

I write my code and provide a hierarchy or .py (.pyc or .pyo?) files. The C# dev needs to copy my hierarhcy and IronPython.dll (which I assume comes directly from the IronPython distribution) into the folder containing his .cs files. Then he can simply access my classes using the normal methods, e.g. 'using' statements. When he compiles to .exe, will he still need the .py files, or will they be compiled into the exe.  And IronPython.dll?  I would assume that since it is a dll it would still be required in the path.

Another way of doing it might be to compile my files to a dll - would IronPython.dll still be required then?

Perhaps an example is worthwhile here:

```
jms@osc-franzibald:/tmp$ cat helloworld.py 
print "Hello, World!" 
jms@osc-franzibald:/tmp$ python helloworld.py 
Hello, World!
jms@osc-franzibald:/tmp$ ipy helloworld.py 
Hello, World!
jms@osc-franzibald:/tmp$ ipy -X:SaveAssemblies -X:AssembliesDir . helloworld.py
Hello, World!
jms@osc-franzibald:/tmp$ mono helloworld.exe

** (helloworld.exe:9667): WARNING **: The following assembly referenced from /tmp/helloworld.exe could not be loaded:
     Assembly:   IronPython    (assemblyref_index=0)
     Version:    1.1.0.0
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/tmp/).


** (helloworld.exe:9667): WARNING **: Could not load file or assembly 'IronPython, Version=1.1.0.0, Culture=neutral' or one of its dependencies.
The entry point method could not be loaded
jms@osc-franzibald:/tmp$ cp /usr/lib/ironpython/IronPython.dll /usr/lib/ironpython/IronMath.dll .
jms@osc-franzibald:/tmp$ mono helloworld.exe
Hello, World!
```

Compiled IronPython assemblies still need IronPython.dll (which needs IronMath.dll) - however, as you suggest, you can call into methods in there seamlessly, i.e. as far as the other developer is concerned, methods in MyPythonLib.dll and MyCsharpLib.dll are no different. Calling into .py files is harder, but also doable.

---

### Post by aquavitae on 2009-01-05
Thanks for the explanation. Do you mean that I could produce a dll in any language (ironpython, python, c#, c++, etc) and use it on its own in a c# program? I know its a bit of a daft question, but I've never quite got my head around dlls and their dependencies!

---

### Post by directhex on 2009-01-05
> **aquavitae said:**
> Do you mean that I could produce a dll in any language (ironpython, python, c#, c++, etc) and use it on its own in a c# program?

ONLY CLI assemblies. Microsoft did a great job muddying the water by re-using .dll and .exe for CLI assemblies - they shouldn't be confused with Windows executables and libraries (.exe and .dll).

So mixing IronRuby with Java with VB.NET? No problem. Outside that... you're into P/Invoke and C bridge land

---

### Post by aquavitae on 2009-01-05
Ahh! Now I understand. So I can write something in the python language, compile it to a dll using IronPython, and use provide it to the other devs. And in this case, the other devs do not need IronPython.dll?

---

### Post by directhex on 2009-01-05
> **aquavitae said:**
> Ahh! Now I understand. So I can write something in the python language, compile it to a dll using IronPython, and use provide it to the other devs. And in this case, the other devs do not need IronPython.dll?

They would still need the IronPython assemblies, as your "compiled" code references them:

```
jms@osc-franzibald:/tmp$ monodis --assemblyref helloworld.exe
AssemblyRef Table
1: Version=1.1.0.0
	Name=IronPython
	Flags=0x00000000
	Zero sized public key
2: Version=2.0.0.0
	Name=mscorlib
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
```

---

### Post by aquavitae on 2009-01-05
Right, so I need to supply three dll files: my one, IronPython.dll and IronMath.dll. Got it finally :)

Thanks for all your help!

---

