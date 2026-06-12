---
title: "How to &quot;stick&quot; application window to desktop?"
date: 2010-04-25
forum: Programming Talk
---

### Post by pauk960 on 2010-04-25
Hi,

Recently I've started experimenting with Mono, C# and GTK. I want to create a program that will behave like desktop widget, to be like "always in background", to stick with the desktop background.  I have a lot of programming experience with PHP, but little with desktop programming. So, if you could only point me to right direction I would be really grateful.

---

### Post by slavik on 2010-04-25
look at conky.

---

### Post by pauk960 on 2010-04-25
Thanks for the tip. After a lot of searching, and one thing leading to another I think I have an answer to my question. Since I want to imitate a widget behaviour, these conditions must be fulfilled:
1. always shown below all other windows (except other instances of widget)
2. be visible on all workspaces
3. stay visible when I "show desktop"
4. no titlebar, window border, window controls, etc.
5. don't appear in taskbar

Solutions:
1. set window property KeepBelow to true
2. call Stick() method on window
3., 4., 5. set window property TypeHint to Dock

Here is the actual code (written in C# using GTK#):
```

using System;
using Gtk;

namespace widget
{
    class MainClass
    {
        public static void Main (string[] args)
        {
            Application.Init ();
            Window window = new Window ("Widget");
            window.Destroyed += delegate (object sender, EventArgs e) {
                Application.Quit ();
            };
            window.KeepBelow = true;
            window.Stick();
            window.TypeHint = Gdk.WindowTypeHint.Dock;
            window.ShowAll ();
            Application.Run ();

        }
    }
}

```
Sure, it needs a lot more work on it to make it a fully featured widget, but for now it's a good start. :)

---

### Post by fabounet on 2010-04-26
You could just use Cairo-Dock, which has Desklets (applets detached on the desktop) that can be placed on a given desktop (or on all the desktops), on the background/foreground/Widget-Layer.

---

