---
title: "ref exe file forgot how to do"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-11-03
i am running xubuntu 12.10. downloaded an exe christmas screen saver. when i  click on it and try to open it it does not give me the option to open with wine. and when i click on the open with option  still no option to open with wine. how do i add that. i just forgot know there is a way to add open with wine to an exe file tks

---

### Post by Mark Phelps on 2012-11-04
It's likely the screen saver is NOT going to work.  Just because it's an exe file doesn't mean Wine will run it.

Check the Application Compatibility database at WineHQ website.  IF your app is not listed, which I suspect, then it's most probably NOT going to work in Wine.

---

### Post by kenizl86 on 2012-11-04
You can always open up Terminal and try this:

```
wine *file.exe*
```

Of course you have to be in the folder the exe file is in. And by "file.exe" I mean the name of the screensaver exe file. If you need anymore help with the "wine" command, go to Terminal and type:

```
man wine
```

---

### Post by rburkartjo on 2012-11-04
ken tks that what i was looking for

---

### Post by kenizl86 on 2012-11-04
Sure thing! Glad I could help!

---

