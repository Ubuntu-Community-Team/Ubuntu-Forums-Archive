---
title: "zlib and monodevelop"
date: 2011-05-29
forum: Programming Talk
---

### Post by Lex-Man on 2011-05-29
I'm trying to learn mono develop at the moment but would like to get access to the zlib library so I can create and modify zip archives, but I have no idea how to import it into my current project.  

Can anyone let me know how to import the library?

---

### Post by Lex-Man on 2011-06-02
I have tried importing the libary using the code:

```
using System;
using System.Runtime.InteropServices;


namespace InterlopeTest
{
	class MainClass
	{
		
		[DllImport ("zlib.so")]
		private static extern char OF();
		
		public static void Main (string[] args)
		{
			char temp = OF();
			Console.WriteLine ("Hello World!");
		}
	}
}
```

But I get the output:

Unhandled Exception: System.DllNotFoundException: zlib.so

How do I make sure that my project knows where the library is located?

---

### Post by MadCow108 on 2011-06-02
mono has a managed zlib library, its located in the libmono-sharpzip0.6-cil package.
[http://www.icsharpcode.net/OpenSource/SharpZipLib/Default.aspx](http://www.icsharpcode.net/OpenSource/SharpZipLib/Default.aspx)

but if you want to call unmanaged code, is the zlib.so installed in the default location(/usr/lib)?
you probably want to use libz.so or a dllmap to it:
[http://www.mono-project.com/Config_DllMap](http://www.mono-project.com/Config_DllMap)

---

### Post by Lex-Man on 2011-06-03
> **MadCow108 said:**
> mono has a managed zlib library, its located in the libmono-sharpzip0.6-cil package.
[http://www.icsharpcode.net/OpenSource/SharpZipLib/Default.aspx](http://www.icsharpcode.net/OpenSource/SharpZipLib/Default.aspx)

but if you want to call unmanaged code, is the zlib.so installed in the default location(/usr/lib)?
you probably want to use libz.so or a dllmap to it:
[http://www.mono-project.com/Config_DllMap](http://www.mono-project.com/Config_DllMap)

How would I import the libmono-sharpzip0.6-cil package?  I have checked the Synaptic Package Manager and the package is installed to my machine.  I tried checking under the manage Edit References menu in MonoDevelop but I not sure which if any would import libmono-sharpzip0.6-cil.  

I did manage to import the libz.so file and call the version function.  

Thanks.

---

### Post by MadCow108 on 2011-06-03
there are examples here:
[http://wiki.sharpdevelop.net/SharpZipLib-Zip-Samples.ashx](http://wiki.sharpdevelop.net/SharpZipLib-Zip-Samples.ashx)
the reference is -r:ICSharpCode.SharpZipLib.dll

---

