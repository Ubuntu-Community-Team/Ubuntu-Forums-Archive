---
title: "Monodev Question"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by L. Cranston on 2008-09-09
I am taking a basic C# class and have installed Monodev so I can use Ubuntu and avoid Windows.....well it seems that Monodev does not recognize Console.ReadLine();
it runs my little program fine, but does not pause for input as it should. The code runs perfectly under Visual Studio 2005 at school, but not in Monodev under Ubuntu.
Is there an add-in or such that is needed? I saw something about this problem somewhere, but cannot find it again.
Any help most appreciated.

---

### Post by kjohansen on 2008-09-09
This worked for me as expected:

```

// Main.cs created with MonoDevelop
// User: johank at 11:01 PM*9/9/2008
//
// To change standard headers go to Edit->Preferences->Coding->Standard Headers
//
using System;

namespace test
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			Console.WriteLine("Hello World!");
			Console.ReadLine();
		}
	}
}

```

Can you post your code, or an excerpt of what is not working if it is too large?

---

