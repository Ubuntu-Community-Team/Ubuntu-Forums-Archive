---
title: "nautilus-gku equivalent in Thunar?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by t0p on 2008-08-18
Nautilus has an extension, **nautilus-gksu**, so when you right-click on a folder, it gives you the option to "open as administrator".

Does Thunar have an equivalent?

---

### Post by billgoldberg on 2008-08-18
> **t0p said:**
> Nautilus has an extension, **nautilus-gksu**, so when you right-click on a folder, it gives you the option to "open as administrator".

Does Thunar have an equivalent?

In a terminal or in the "alt+f2" application

```
gksudo thunar
```

---

### Post by t0p on 2008-08-18
> **billgoldberg said:**
> In a terminal or in the "alt+f2" application

```
gksudo thunar
```

Yeah, I know I can do that, thanks.  What I want is an extension like nautilus-gksu, so I don't have to start a new instance of thunar when accessing system directories.

---

### Post by billgoldberg on 2008-08-18
> **t0p said:**
> Yeah, I know I can do that, thanks.  What I want is an extension like nautilus-gksu, so I don't have to start a new instance of thunar when accessing system directories.

I'm sorry, I don't really know how to do for thunar.

But I can suggest you bind the command "gksudo thunar" to a keyboard shortcut.

You can use the program "xkeybinds" for that.

---

