---
title: "WinAdapter() in java??"
date: 2007-10-20
forum: Programming Talk
---

### Post by Choad on 2007-10-20
ok i said in my other thread that i was using netbeans and swing, but i am actually now using JDeveloper (i didn't realise it was available for free and for linux) and the AWT toolkit, for simplicities sake as that is what we are being taught with.

all is going well, i got through the first few tutorials fine, now it's coming to the gui stuff and i am having problems with WinAdapter()

[[IMG]http://aycu18.webshots.com/image/29377/2005031607666712185_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2005031607666712185)

as you can see, WinAdapter is saying it needs to be imported but when i press alt+enter it does nothing. is this a windows-specific class? what's the linux alternative? i thought java was supposed to be platform independent, so this strikes me as rather odd...

---

### Post by bernardfrancois on 2007-10-20
Maybe you could try adding the following line among the other import statements:
**import markclassdemo.WinAdapter;**

About the platform independence question... as long as you use the standard java objects (within the java namespace), your program is guaranteed to be platform independent. Third-party libraries *might* only work on certain platforms.

---

### Post by Choad on 2007-10-20
oh god! duhhhhhh i didnt realise it was a class within the template project she gave us.

ok this is going to be a bit easier now :p

---

