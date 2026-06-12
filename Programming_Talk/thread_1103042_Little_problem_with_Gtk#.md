---
title: "Little problem with Gtk#"
date: 2009-03-22
forum: Programming Talk
---

### Post by Starlight on 2009-03-22
Hi! 

I've never programmed in C# before, and I've never used Gtk before, so maybe I'm just making some stupid mistake. But here's the problem I have. There's a window, and somewhere in that window there's a Gtk.Image object called image4. It's displaying an image loaded from a png file. I need to write a function that can access individual pixels of the displayed image. After looking around I found out that Gdk.Image objects have that ability. So I needed a way to convert a Gtk.Image into a Gdk.Image, and I found the Gtk.Image.ImageProp property that's supposed to return a Gdk.Image object. So, here's a fragment of my code:

```

Gdk.Image obrazek = image4.ImageProp;
Console.Out.WriteLine(obrazek.Width);
```

The program compiles with no errors or warnings, but when I run it, I get "System.NullReferenceException: Object reference not set to an instance of an object" pointing at the line that uses "obrazek.Width". If I try to use it somewhere else, such as the loop "for(int x=0; x<obrazek.Width; ++x)", it crashes with the same message and points at the "for" statement.

I've tried everything, but I can't make it work. Maybe I'm just making some silly mistake... does anyone know why it's not working? Or is there some other way to access individual pixels of an image in Gtk#?

---

