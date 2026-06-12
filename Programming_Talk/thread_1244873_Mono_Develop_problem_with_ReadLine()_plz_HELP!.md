---
title: "Mono Develop problem with ReadLine() plz HELP!"
date: 2009-08-19
forum: Programming Talk
---

### Post by Eremis on 2009-08-19
Hi! 

I just started programing in C# (used java before), and I am having a problem with a simple program that takes in a string, and then does a few tests with it (if statements). Well mono just skips the ReadLine() part.....

Here's the code:
```

#region Using directives

using System;
using System.Collections.Generic;
using System.Text;

#endregion

namespace ContinueBreak
{
	class ContinueBreak
	{
		static void Main(string[] args)
		{
			string signal = "O"; // initialize to neutral
			while (signal != "X") // X indicates stop
			{
				Console.Write("Enter a signal: ");
				signal = Console.ReadLine();
				
				// do some work here, no matter what signal you
				// recive
				
				Console.WriteLine("Received: {0}", signal);
				if (signal == "A")
				{
					// faulty - abort signal processing
					// Log the problem and abort.
					Console.WriteLine("Fault! Abort\n");
					break;
				}
				
				if (signal == "O")
				{
					// normal traffic condition
					// log and continue on
					Console.WriteLine("All is well.\n");
					continue;
				}
				
				// Problem. Take action and then log the problem
				// and then continue on
				
				Console.WriteLine("{0} -- raise alarm!\n", signal);
			} // end while
		} // end main
	} // end class 
} // end namespace

```

I attached a screenshot of the output...
For some reason it goes into a infinite loop, and i have to stop it manually in the Mono IDE. :confused:

Any feedback will be helpful!

-- Thanks!

---

### Post by Linteg on 2009-08-20
Monodevelop's console doesn't handle input, see [http://lists.ximian.com/pipermail/monodevelop-list/2008-June/007880.html](http://lists.ximian.com/pipermail/monodevelop-list/2008-June/007880.html).

---

### Post by Eremis on 2009-08-20
ok, thanks!

---

