---
title: "Console Read"
date: 2012-05-28
forum: Programming Talk
---

### Post by VH-BIL on 2012-05-28
I am having trouble with Console.Read and ReadLine etc. where the keys pressed are being output to the console without the program writing it. Is there an option to say the keys have been handled so they are not written to the console while typed?

Example:
```
using System;

namespace test
{
	class MainClass
	{
		public static void Main (string[] args)
		{
			string s = Console.ReadLine();
			Console.WriteLine (s + " was the text");
		}
	}
}

```
is outputting: (as you can see TEST is written to the console while typed)
```

TEST
TEST was the text

Press any key to continue...

```

---

### Post by VH-BIL on 2012-05-28
I just tested this in Windows (complied in Linux) with the same results.

---

