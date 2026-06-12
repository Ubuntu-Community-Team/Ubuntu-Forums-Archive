---
title: "Mono useful by its own merit?"
date: 2005-07-27
forum: Programming Talk
---

### Post by NoTiG on 2005-07-27
I have been reading up on mono and trying to understand exactly what the *framework* is..... 

> However, the main purpose of Mono is to ease migration. "It enables the large number of VB.NET and C# people to target a platform other than Windows 

Does that mean it is still useful if your a linux programmer? Say your writing an application on linux.. and targetting other platforms as well. Say you wanted to use python.. why would you use Ironpython?

> They said, ‘We can develop applications 20 to 25% faster than with ASP.NET than we can with J2EE. 

Would writing in Ironpython with mono be any faster than in developing with plain Python? Python is a portable language... would ironpython be any more portable? would you be able to use the same file for different operating systems? But they would need mono installed on their computer first ? 

> # Fast - IronPython-0.6 is up to 1.7x faster than Python-2.3 on the standard pystone benchmark.  An early performance report is are contained in this paper for PyCon 2004.
# Integrated with the Common Language Runtime - IronPython code can easily use CLR libraries and Python classes can extend CLR classes.
# Fully dynamic - IronPython supports an interactive interpreter and transparent on-the-fly compilation of source files just like standard Python.
# Optionally static - IronPython also supports static compilation of Python code to produce static executables (.exe's) that can be run directly or static libraries (.dll's) that can be called from other CLR languages including C#, VB, managed C++ and many more.  Note: static compilation is only partially implemented in the 0.6 public release.  This will need further development before being useful.
# Managed and verifiable - IronPython generates verifiable assemblies with no dependencies on native libraries that can run in environments which require verifiable managed code.
# Not finished - IronPython is currently at a pre-alpha stage suitable for experimentation but not for serious development work.  The latest public release can be downloaded below. 

Why would Ironpython be faster than python? Are they both using the same exact syntax, but just a different set of libraries? The python standard library for python, and the common language runtime libraries for ironpython?

---

### Post by LordHunter317 on 2005-07-27
[QUOTE=NoTiG]I have been reading up on mono and trying to understand exactly what the *framework* is.....[/quote]It's the reimplementation of MS' .NET framework.

> Does that mean it is still useful if your a linux programmer?Yes, and it also means that as long as you use .NET framework classes (i.e., S.W.F, not GTK#) your applications will run on Windows as well, fore free.

> Say you wanted to use python.. why would you use Ironpython?Because anyone with the .NET framework installed will be able to run your IronPython code.  With a regular python program, you'd have to get them to install the python interpreter first, or convert your python code to a compiled, native executable.

> Would writing in Ironpython with mono be any faster than in developing with plain Python?Depends on what you're trying to do.  For example, doing a web application with IronPython and ASP.NET is probably faster than working in any Python web framework (though I'm not an expert on Python webframeworks, so I could be mistaken.  But IME, nothing matches ASP.NET 100%)

> would ironpython be any more portable?It's as portable as .NET is.  Which is less portable than python proper, and likely will be that way for sometime.

> would you be able to use the same file for different operating systems?Yes.

>  But they would need mono installed on their computer first ? Or MS' .NET framework, on Windows.

> Why would Ironpython be faster than python?I'm not sure why it is, I'd have to read the performance papers.

> Are they both using the same exact syntax, but just a different set of libraries? The python standard library for python, and the common language runtime libraries for ironpython?Yes and yes.

---

### Post by NoTiG on 2005-07-27
Hmmmm. I just looked at Muines website... a mono program. You can dl it but its an RPM, not an executable :P so even with the framework... it still has to come in a package? No 1 file for all OS's ?

---

### Post by LordHunter317 on 2005-07-27
Well. they could provide one EXE and the associated DLLs for all operating systems, if they wanted to.

However, that fact the code files are the same doesn't change the fact that on RedHat they go in one place, and another on Debian.

What I'm saying is that the code files inside the RPM for RH will be the same as the files inside the DEB for Ubuntu.  However, in the RPM, it might be in /usr/bin/.netapps, and in /usr/share/mono/bin in Debian.

.NET doesn't free you from platform-specific installation issues, like where your code gets installed to.  What it does mean is that your application code doesn't have to deal with those issue, or that I have to compile different code for different distributions or operating systems.

And having to generate a zip file for Windows with the code in one place, a RPM for RH, and a .deb for Ubuntu isn't nearly as hard of a task ;)

---

### Post by NoTiG on 2005-07-28
that makes sense :P thanks for clearing that up.

---

