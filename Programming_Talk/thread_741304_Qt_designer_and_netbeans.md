---
title: "Qt designer and netbeans"
date: 2008-03-31
forum: Programming Talk
---

### Post by StOoZ on 2008-03-31
Ok, so I built a simple form with two buttons using QT designer.
now what? how Can I implement the code using Netbeans?
tried their manual, but to no avail.
I assume that QT designer creates a GUI code skeletons somewhere, which then I can import somehow to netbeans and put my code on top of it, or at least I guess its like that.

any idea?

---

### Post by kknd on 2008-03-31
> **StOoZ said:**
> Ok, so I built a simple form with two buttons using QT designer.
now what? how Can I implement the code using Netbeans?
tried their manual, but to no avail.
I assume that QT designer creates a GUI code skeletons somewhere, which then I can import somehow to netbeans and put my code on top of it, or at least I guess its like that.

any idea?

QT designer can save a GUI design into a XML, that can be loadeded with the proper API calls.

If you want to build the application under Netbeans (you can use any editor), you will need the C++ plugin.

---

### Post by StOoZ on 2008-04-01
what plug-in?
cant find anything on the web regarding this issue.. :(

---

### Post by Zugzwang on 2008-04-01
> **StOoZ said:**
> what plug-in?
cant find anything on the web regarding this issue.. :(

Thy the official site: [http://www.netbeans.org/kb/trails/cnd.html]("http://www.netbeans.org/kb/trails/cnd.html")

---

### Post by StOoZ on 2008-04-01
nothing helpful in there, already tried it.
:(

---

### Post by Zugzwang on 2008-04-01
> **StOoZ said:**
> nothing helpful in there, already tried it.
:(
It tells you how to install the plugin mentioned by kknd.

Note that the netbeans manual doesn't tell you how to program! You will notice that in Linux, everything is broken down into very small pieces and there is no single place for documentation. Try the How-To at [http://www.tsseshop.com/developer/Tutorials/HowToQtOnNetBeans/]("http://www.tsseshop.com/developer/Tutorials/HowToQtOnNetBeans/") for using QT in Linux. Then look up the documentation on using stuff built with the QT GUI builder.

---

### Post by StOoZ on 2008-04-01
well I know how to program QT, and I already used netbeans for QT programming, using the QtGUI libaries, via code, not designer

BUT I want to use the designer to "draw" the gui, its just a waste of time programming it, and then , somehow, to take that GUI and implement my codes for each button etc (in this case, connecting to another system)

---

### Post by Zugzwang on 2008-04-01
> **StOoZ said:**
> BUT I want to use the designer to "draw" the gui, its just a waste of time programming it, and then , somehow, to take that GUI and implement my codes for each button etc (in this case, connecting to another system)

Maybe you would like to read the [QT designer documentation]("http://doc.trolltech.com/3.3/designer-manual-5.html") which shows how to include forms made with the designer in your projects.

Alternatively, did you mean:
[LIST]
[*]that you want to use Netbeans's GUI editor (for Java) for QT? I guess this is not possible (at least in the near future)
[*]Open program "templates" made with the designer in Netbeans? You would have to make a new Netbeans project (probably with existing/custom Makefile) and add the created files there.
[/LIST]

I accidentally though that kknd's approach was the only one. More details on his approach can be found [here]("http://doc.trolltech.com/3.3/designer-manual-6.html#2-3-2").

---

### Post by eljotarojas on 2008-06-12
visit this page [http://sector.ynet.sk/qt4-tutorial/my-first-qt-gui-application.html](http://sector.ynet.sk/qt4-tutorial/my-first-qt-gui-application.html).

In that site there is a very good tutorial step by step of qt+netbeans using qtdesigner

---

### Post by xlinuks on 2008-06-12
> **StOoZ said:**
> well I know how to program QT, and I already used netbeans for QT programming, using the QtGUI libaries, via code, not designer

BUT I want to use the designer to "draw" the gui, its just a waste of time programming it, and then , somehow, to take that GUI and implement my codes for each button etc (in this case, connecting to another system)

I'm just curious, why not stay with QT designer?

---

### Post by Verminox on 2008-06-13
The tool that converts the *.ui files (XML geenrated by the designer) into .cpp and .h (for use with the API) is called **uic**. All I could find about it was the [uic man pages](http://linux.die.net/man/1/uic). I'm not sure if there is a way to plug this into NetBeans but you could maybe try to run the uic tool manually after updating your designer files to generate the cpp code that you can use in your api...

---

