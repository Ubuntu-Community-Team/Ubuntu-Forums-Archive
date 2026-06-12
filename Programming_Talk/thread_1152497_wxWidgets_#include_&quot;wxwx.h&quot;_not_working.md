---
title: "wxWidgets #include &quot;wx/wx.h&quot; not working"
date: 2009-05-07
forum: Programming Talk
---

### Post by Xender1 on 2009-05-07
I took the hello world wxWidget program from the site, and copied it into netbeans. When trying to compile i get a message saying that it cannot include the header file (which is wx/wx.h). 
Then when i just save it as a document, and compile it from console i still get an error:
```

g++ hworld.cpp `wx-config --libs` `wx-config --cxxflags` -o hworld 

```
```

error while loading shared libraries: libwx_gtk2_richtext-2.8.so.0: cannot open shared object file: No such file or directory

```

---

### Post by eye208 on 2009-05-08
Try this:
```

g++ hworld.cpp `wx-config [COLOR="DarkRed"]--unicode[/COLOR] --libs` `wx-config [COLOR="DarkRed"]--unicode[/COLOR] --cxxflags` -o hworld 

```

---

