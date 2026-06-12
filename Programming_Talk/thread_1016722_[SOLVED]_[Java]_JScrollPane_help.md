---
title: "[SOLVED] [Java] JScrollPane help"
date: 2008-12-20
forum: Programming Talk
---

### Post by PaulM1985 on 2008-12-20
Hi

I am trying to add MyCanvas, a class I have created which is a subclass of Canvas to a JScrollPane. 

I am using the code below: ```

canv = new MyCanvas();
canv.setSize(2000, 2000);
canvContainer = new JScrollPane(canv);
frame.add(canvContainer);

```

When I run this, my canvas opens at size 500 x 500, with no scroll bars.  Can anyone see where I am going wrong.  Any help much appreciated.

Paul

---

### Post by jespdj on 2008-12-20
Not sure, but try this:
```
canv.setPreferredSize(2000, 2000);
```
instead of setSize().

---

### Post by PaulM1985 on 2008-12-20
Hi 

canv.setPreferredSize(2000, 2000);
gave a compiler error, so I tried canv.setPreferredSize(new Dimension(2000,2000));

Still didn't work.

Paul

---

### Post by PaulM1985 on 2008-12-20
Hi all

I have solved the problem.  It sounds as though JScrollPane cannot be used for "heavyweight AWT components".  AWT's ScrollPane should be used instead.  If anyone is interested in this, link is below.

[http://forums.java.net/jive/thread.jspa?threadID=9318](http://forums.java.net/jive/thread.jspa?threadID=9318)

Paul

---

