---
title: "MonoDevelop Question Regarding the String class"
date: 2007-03-28
forum: Programming Talk
---

### Post by rngomez on 2007-03-28
Hello and thank you for your time in advance.  I am using MonoDevelop and C#.
Issue: When trying to compile the following code, I get an error.


string sLine = "this is a line:";
bool bCheck = sLine.Contains("line");

The compiler tells me that System.String does not contain a definition for 'Contains'.  I know that this code will compile under Windows using Visual Studio.  I also know that the class does indeed contain that function and that I am using correctly.  This leads me to conclude that I have not set something up correctly, or that there is some type of bug involved.  That function appears in the editor, so MonoDevelop must be aware of it on some level.

I am a part time developer, so I'm not new to C#, but I am pretty new to using MonoDevelop and using a *nix platform.  The System namespace is imported (using) and referenced.
Any ideas?

---

### Post by _teo_ on 2007-03-29
perhaps it is not implemented in mono
you may try as an workaround:

```
int IndexOf (string value)
```

---

### Post by mardawi on 2007-03-29
Mono is currently compatible with .net 1.1
String.Contains is only available in .net 2.0 and 3.0

[http://msdn2.microsoft.com/en-us/library/system.string.contains.aspx](http://msdn2.microsoft.com/en-us/library/system.string.contains.aspx)

use _teo_ suggestion instead.

---

### Post by lukew on 2007-03-31
> **mardawi said:**
> Mono is currently compatible with .net 1.1
String.Contains is only available in .net 2.0 and 3.0

[http://msdn2.microsoft.com/en-us/library/system.string.contains.aspx](http://msdn2.microsoft.com/en-us/library/system.string.contains.aspx)

use _teo_ suggestion instead.

You can switch to version 2 though even on the mono website they say that this is currently flakey!! :o anyone tried?

---

