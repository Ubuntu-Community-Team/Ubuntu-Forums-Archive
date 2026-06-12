---
title: "Mouse control: C# &amp; linux"
date: 2008-03-02
forum: Programming Talk
---

### Post by vcat on 2008-03-02
Hi everyone,

I was playing with C# (mono) in Linux and ran into one compiling question. Programs that use System.Draw or System.Windows.Forms namespaces would not compile in Linux, but if once you compile in windows, it runs just fine under Linux. I am aware that there are alternative implementations, I am just not sure which. Let me give you an example:

```

using System;
using System.Windows.Forms;
using System.Drawing;

public class MadMouse
{
	public static void Main()
	{
	Console.WriteLine("Your mouse should be jumping all over the place\nPress Ctrl+C to quit");
	for(;;)
		{
		Cursor.Position = new Point(Cursor.Position.X + 100, Cursor.Position.Y + 100);
		Cursor.Position = new Point(Cursor.Position.X - 100, Cursor.Position.Y - 100);
		continue;
		}
	}
}

```

It is a simple loop that shakes the mouse. How would you compile in linux? which namespaces would you use? It runs in linux so there must be an easy way to have it compile with mono.
Thanks!

---

