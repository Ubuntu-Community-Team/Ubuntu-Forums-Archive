---
title: "Unhandeled Exception: Glade + Monodevelop (Natty)"
date: 2011-05-12
forum: Programming Talk
---

### Post by etdsbastar on 2011-05-12
Hello there,

I am integrating Glade UI file like this:

```
using System;
using Glade;
using Gtk;

namespace calculator
{
    public class MainWindow
    {
        public static void Main (string[] args)
        {
            new MainWindow (args);
        }

        public MainWindow (string[] args)
        {
            Application.Init ();
            Glade.XML gxml = new Glade.XML (null, "mainwindow.glade", "MainWindow", null);
            gxml.Autoconnect (this);
            Application.Run ();
        }
    }
}
```

But, I am getting the following error:

```
Unhandled Exception: System.ArgumentException: Cannot get resource file 'mainwindow.glade'
Parameter name: resource_name
  at Glade.XML..ctor (System.Reflection.Assembly assembly, System.String resource_name, System.String root, System.String domain) [0x00000] in <filename unknown>:0 
  at calculator.MainWindow..ctor (System.String[] args) [0x0000b] in .../calculator/calculator/MainWindow.cs:17 
  at calculator.MainWindow.Main (System.String[] args) [0x00000] in .../calculator/calculator/MainWindow.cs:11 
The application was terminated by a signal: SIGHUP

```

Please help

---

### Post by etdsbastar on 2011-05-14
bump...

---

