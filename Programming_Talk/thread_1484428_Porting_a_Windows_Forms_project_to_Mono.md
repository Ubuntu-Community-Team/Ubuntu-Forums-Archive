---
title: "Porting a Windows Forms project to Mono"
date: 2010-05-15
forum: Programming Talk
---

### Post by mihnea.radulescu on 2010-05-15
Hello everybody!

I developed (up to alpha stage, at this moment) a picture browsing application for .NET 2.0 and released it under GPL v3.

Explanatory article: [http://www.codeproject.com/KB/cs/ImageFan.aspx](http://www.codeproject.com/KB/cs/ImageFan.aspx)

Google Code page: [http://code.google.com/p/imagefan/](http://code.google.com/p/imagefan/)

I tried to execute it on Mono to no avail. Even though the application runs, certain features do not work as expected, especially key presses and the full screen mode.

I also tried compiling it with Mono's C# compiler using Monodevelop. Although the compilation completed successfully, the newly-built application simply crashed on load.

After searching on the Mono project page, I found out that Windows Forms in the latest Mono version is considered to be 100% compatible with the corresponding MS implementation. Still, my Winforms app simply refuses to run correctly on Ubuntu, while running as expected on Windows.

Does anyone know of possible fixes to my emerging program, outside of shifting to GTK#, instead of Windows Forms?

All the best,
Mihnea

---

### Post by JwB Zoofware on 2010-05-15
Are any errors sent to stdout when you run it from a terminal? (i.e "mono app.exe") I've noticed that mono doesn't report any uncaught exceptions graphically.

---

### Post by mihnea.radulescu on 2010-05-15
No error messages written to the console window.

---

