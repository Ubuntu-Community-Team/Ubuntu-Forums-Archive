---
title: "Mono.Cairo not working..."
date: 2005-11-13
forum: Programming Talk
---

### Post by GameGod on 2005-11-13
Hi everyone,

I've been playing around with Mono for an hour or two, and I can't seem to get Mono.Cairo working...

If I compile my code by hand (or in Monodevelop), I get:

```
mcs -pkg:gtk-sharp -pkg:glade-sharp -r:Mono.Cairo Main.cs
Main.cs(6) error CS0234: The type or namespace name `Cairo' could not be found in namespace `Mono'
Main.cs(6) error CS0234: The type or namespace name `Cairo' could not be found in namespace `Mono'
Main.cs(6) error CS0246: The namespace `Mono.Cairo' can not be found (missing assembly reference?)
Compilation failed: 3 error(s), 0 warnings

```

I'm pretty sure I have all the right packages installed... anyone used Cairo before with Mono on Breezy?

---

### Post by GameGod on 2005-11-14
Aha!
Just had to figure out how to use MonoDevelop...
In the solutions pane, I had to right-click on the "references" folder, and select "Edit References"... I just had to check off the "Cairo" assembly, and change my code to have "using Cairo;" at the top (I previously had "using Mono.Cairo;")...

:)

---

