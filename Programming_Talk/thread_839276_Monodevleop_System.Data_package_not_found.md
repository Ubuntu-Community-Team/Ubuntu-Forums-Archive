---
title: "Monodevleop System.Data package not found"
date: 2008-06-24
forum: Programming Talk
---

### Post by CoximusPrime on 2008-06-24
Hi guys,

  Not sure if this is the best place to post but you've all been good to me in the past and I couldn't find a dedicated monodevelop forum on the net.

  I've written a couple of programs so far in c# on linux (I've written plenty more on windows), basically I'm just playing around with trying to create a DataTable (System.Data.DataTable) and populate it with some data from a text file. But I'm stuck at the first hurdle. In monodevelop the first thing I did was simply add "using System.Data;" line under the existing "using System;" line, compile it, and get the following error : "The type or namespace name `System.Data' could not be found. Are you missing a using directive or an assembly reference?" ... Do I need to install additional packages or does the System.Data package simply not exist yet in mono?

Thanks guys

---

### Post by Zugzwang on 2008-06-24
No, it's there. According to [http://msdn.microsoft.com/en-us/library/system.data.datatable(VS.71).aspx]("http://msdn.microsoft.com/en-us/library/system.data.datatable(VS.71).aspx") this package is part of .NET 1.1, so Mono should have it. And if you look into /usr/lib/mono/2.0 (or whatever version you are using) you will find System.Data.dll. So you need to reference that assembly as stated in the error message. Look at the manual of MonoDevelop & gmcs/mcs to learn how to do this.

---

### Post by CoximusPrime on 2008-06-24
Cheers bud, I've had a look and the file does exist in /usr/lib/mono/2.0 .. will have a read now on how to reference it.

many thanks

---

