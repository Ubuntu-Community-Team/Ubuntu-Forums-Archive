---
title: "[SOLVED] Need a little help with g++ and WxWidgets"
date: 2008-03-19
forum: Programming Talk
---

### Post by Amazona aestiva on 2008-03-19
I'm learning C++ hard and i like it, so I've looked for a GUI toolkit. My choice is WxWidgets because of its portability.

I downloaded a little sample source, but the compiler can't find "wx.h".
Look:

I've changed
#include </wx/wx.h>

to
#include </usr/include/wx-2.8/wx/wx.h>

Then it's all right. It wants a couple of the others of course, but doesn't see them even if I write them down like wx.h.

How can I make the compiler to see '/usr/include/wx-2.8/' as '/' ?

Thank you!

---

### Post by WW on 2008-03-19
The include statement should be
```

#include "wx/wx.h"

```
or
```

#include <wx/wx.h>

```
Take a look at [this tutorial](http://www.wxwidgets.org/docs/tutorials/hello.htm).  Near the end it shows a **g++** command that compiles their example.

---

### Post by Amazona aestiva on 2008-03-19
> **WW said:**
> The include statement should be
```

#include "wx/wx.h"

```
or
```

#include <wx/wx.h>

```
Take a look at [this tutorial](http://www.wxwidgets.org/docs/tutorials/hello.htm).  Near the end it shows a **g++** command that compiles their example.

Thanks that helped me!



PS If anyone can give me some further links, they would be accepted!
Thanks again!

---

### Post by Kadrus on 2008-03-20
Here some good links..
This is a tutorial: [http://zetcode.com/tutorials/wxwidgetstutorial/](http://zetcode.com/tutorials/wxwidgetstutorial/) 
And this one is a book: [http://en.wikibooks.org/wiki/WxWidgets](http://en.wikibooks.org/wiki/WxWidgets)
Good luck:)

---

