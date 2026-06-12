---
title: "How do I use WINE?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by zeththedarkmage on 2008-05-02
How do I use WINE to run windows programs?

---

### Post by forestpixie on 2008-05-02
From a terminal 

```
wine /path/to/program
```

---

### Post by wolfen69 on 2008-05-02
> **zeththedarkmage said:**
> How do I use WINE to run windows programs?

to install, i would just right click the .exe and select "open with wine". to run it i would go to applications>system tools?>wine and click on the app.

---

### Post by yamawho on 2008-05-02
> **wolfen69 said:**
> to install, i would just right click the .exe and select "open with wine". to run it i would go to applications>system tools?>wine and click on the app.

Now that sounds easy enough.

Is wine doors basically the same but with a GUI ?

---

### Post by LinuxRocks713 on 2008-05-02
cd /path/to/application
wine ./Application_Name.exe

---

### Post by GavinZac on 2008-05-02
> **yamawho said:**
> Now that sounds easy enough.

Is wine doors basically the same but with a GUI ?

No, wine-doors just attempts to do all the configuration for you.

Wine will create a "windows" start menu item in your applications menu, for everything you've installed, e.g. Wine->Program Files->Microsoft Office->Excel

Or you can double click a file, like you would in windows.

---

### Post by yamawho on 2008-05-02
> **GavinZac said:**
> No, wine-doors just attempts to do all the configuration for you.

Wine will create a "windows" start menu item in your applications menu, for everything you've installed, e.g. Wine->Program Files->Microsoft Office->Excel

Or you can double click a file, like you would in windows.

Is wine doors not recommended ?

---

### Post by GavinZac on 2008-05-02
> **yamawho said:**
> Is wine doors not recommended ?

I don't use it, but then I am used to using Wine on its own. It is early in Wine-door's development, but if it supports a particular program you want to run, then maybe give it a shot :)

---

