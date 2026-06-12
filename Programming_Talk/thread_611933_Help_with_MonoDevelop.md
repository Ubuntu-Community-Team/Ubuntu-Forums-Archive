---
title: "Help with MonoDevelop"
date: 2007-11-13
forum: Programming Talk
---

### Post by Amablue on 2007-11-13
I'm trying to get Monodevelop to work but it wont run run any programs I give it. I wrote a few in Visual Studio and I was told I should be able to just open the solution and run it, but I'm having no luck. Even just running a hello world program I get errors. 

```

Building Solution Homework1-TicTacToe

Building Project: Homework1-TicTacToe (Debug|Any CPU)
Performing main compilation...
Compiling resource /media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe/Form1.resx with resgen2
Error while trying to invoke 'resgen2' to compile resource '/media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe/Form1.resx' :
 ApplicationName='resgen2', CommandLine='/compile "/media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe/Form1.resx"', CurrentDirectory='/media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
Compiling resource /media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe/Properties/Resources.resx with resgen2
Error while trying to invoke 'resgen2' to compile resource '/media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe/Properties/Resources.resx' :
 ApplicationName='resgen2', CommandLine='/compile "/media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe/Properties/Resources.resx"', CurrentDirectory='/media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe/Properties', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'

System.Deployment could not be found or is invalid.
Build failed. ApplicationName='gmcs', CommandLine='"@/tmp/tmp5bf7fcda.tmp"', CurrentDirectory='/media/sda1/temp/CS130/Homework1-TicTacToe/Homework1-TicTacToe', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'

```

---

### Post by st4rdr1ft3r on 2007-11-13
try installing mono-gmcs and mono-mcs

---

### Post by soulskater on 2008-02-16
Hi.

Just wanted to say that your tip helped me, since i did my stuff with version 2 of .NET.

Another tip in case your programming ASP.NET is to install xsp2 so you will be able to test run your website from within MonoDevelop.

/Marcus

---

### Post by arist0tle on 2008-02-17
awesome. thanks for that tip!!!!!

---

### Post by MonkeeSage on 2008-04-13
The resgen2 program is now in the mono-2.0-devel package. If that is installed, the problem should be fixed.

---

### Post by Kadrus on 2008-04-13
```
sudo apt-get install mono-devel build-essential mono-gmcs libmono-dev libpango1.0-dev libgtk2.0-dev libgtksourceview2.0-cil libgecko2.0-cil monodoc libmono-system-runtime2.0-cil libmono-cairo2.0-cil gettext
```

---

