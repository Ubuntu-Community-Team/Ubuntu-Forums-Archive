---
title: "wxWidgets with Code::Blocks"
date: 2008-08-02
forum: Programming Talk
---

### Post by JacoLouw on 2008-08-02
I am currently having trouble with Code::Blocks on auto completion for the wxWidgets library.

My build options are set up properly. Compiler Settings->Other Options has the line `wx-config --cxxflags` in it and the Other Linker Options has the `wx-config --libs` command in it.

Now, in Project Properties', C/C++ Parser Options has the an item added with the directory of: /usr/include/wx-2.8.

I am running Ubuntu 8.04.

Now this is the problem... when I type "wxFrame" in, the auto completion dialog pops up. It does not list wxFrame but only wxFrameBase. For all the GUI classes, it only finds the classes with Base appended to the end (i.e: wxFrameBase, wxButtonBase, etc.). How do I fix this?

All the examples that I tried compile just fine.

Thanks in advanced,
Jaco.

---

### Post by henchman on 2008-08-03
same problem here :)

when i have a class which is derived by wxFrame and i type a dot like after myBloodyFrame**.**, the context-sensitive drop down menu, which normally show the members only shows the constructor/destructor... 

when creating an object of wxFrameBase like

```
wxFrameBase a;
a**.**
```

it shows all those cool members which is really good, especially if you are to lazy to read the documentation and just want to kickstart your wxWidget programming experience :)

thanx :mad:

---

