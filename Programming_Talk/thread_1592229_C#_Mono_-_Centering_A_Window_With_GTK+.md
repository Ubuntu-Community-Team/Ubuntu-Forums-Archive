---
title: "C# Mono - Centering A Window With GTK+?"
date: 2010-10-10
forum: Programming Talk
---

### Post by frychiko on 2010-10-10
Just started C# development with Mono and Monodevelop but the lack of documentation is killing me. How can I center a window?

Monodevelop spits out the following code, and I've got a center code in the middle which I've spotted in a few example apps on the web.

```
...
MainWindow win = new MainWindow();
**win.SetPosition(WindowPosition.Center);**
win.Show();
...
```

This works for the Window type but not for the MainWindow type.. I can manipulate MainWindow in every other way except for position.

---

### Post by pcambraia on 2011-09-14
Instead of "Center" use "CenterAlways", as in:

win.SetPosition(WindowPosition.CenterAlways);

---

