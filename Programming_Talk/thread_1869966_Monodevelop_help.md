---
title: "Monodevelop help"
date: 2011-10-26
forum: Programming Talk
---

### Post by luishasbon on 2011-10-26
Greetings!

I'm new to mono and monodevelop, I'm looking forward to developing an Image processing app using csharp, I was wondering if there's a book that might teach me how to design and use GUI and csharp with mono in general. If I develop the project in monodevelop linux with GTK#, I can use it in windows?

---

### Post by gsmanners on 2011-10-26
I think the vast majority of C# developers go the other way around (i.e. develop in Visual Studio and then port to Mono if they need it for some reason). Lots of books show you how to use VS (not that it really needs it).

---

### Post by PaulM1985 on 2011-10-27
You probably could port a GTK# app to Windows, however, if you are looking at really simple ways to port your app, I would recommend you use Windows forms rather than GTK#.

Paul

---

### Post by directhex on 2011-10-27
> **luishasbon said:**
> Greetings!

I'm new to mono and monodevelop, I'm looking forward to developing an Image processing app using csharp, I was wondering if there's a book that might teach me how to design and use GUI and csharp with mono in general. If I develop the project in monodevelop linux with GTK#, I can use it in windows?

Yes. GTK# works fine in Windows. However, users will need to install GTK# for Microsoft.NET first - [http://download.mono-project.com/gtk-sharp/gtk-sharp-2.12.10.win32.msi](http://download.mono-project.com/gtk-sharp/gtk-sharp-2.12.10.win32.msi)

---

