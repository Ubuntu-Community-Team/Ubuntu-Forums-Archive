---
title: "Python: Excluding Modules Pyinstaller"
date: 2011-02-03
forum: Programming Talk
---

### Post by Sailor5 on 2011-02-03
Greetings!
  So I've began using Pyinstaller over Py2Exe. However I've rather  quickly ran into a problem. How do I exclude modules that I don't want,  and how do I view the ones that are getting included into the single  executable file? I can remove some pyd and dll files from the DLL folder  in my Python installation so Pyinstaller doesn't find and therefore  doesn't include them. I don't really want to be doing that with all the  modules as it will get quite arguos.
  I did try edit the spec file that Pyinstaller makes.
  ```
a.binaries - [('ssl','pydoc',)],
```    But the size of the file remained the same so I conclude that didn't work. So how can I see what modules  Pyinstaller are including and how do I exclude those that I do not want?


  Thanks bye!

---

### Post by Sailor5 on 2011-02-04
[color=transparent]Bump[/color]

---

