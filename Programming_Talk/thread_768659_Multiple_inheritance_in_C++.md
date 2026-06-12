---
title: "Multiple inheritance in C++"
date: 2008-04-26
forum: Programming Talk
---

### Post by StOoZ on 2008-04-26
In C++, how common is the use of Multiple inheritance?

to my perspective, it can cause a lot of troubles and headache.
is it very common to use it?

---

### Post by ZylGadis on 2008-04-26
Read about mixins [http://en.wikipedia.org/wiki/Mixin]("http://en.wikipedia.org/wiki/Mixin"). This is the most common use (and about the only one which makes sense). Often used in computer game development.

---

### Post by JupiterV2 on 2008-04-26
Multiple inheritance is common in Gtkmm for creating your own "super-class" of a widget:

[php]
#include <gtkmm/window.h>

class MainWindow: public Gtk::Window
{
  /* define all the widgets and what-not of your window here. The Gtk::window
   * class in turn inherits multiple classes like Gtk::Container, Gtk::Bin,
   * etc. */
};
[/php]

> Often used in computer game development.

Yes, this is common in game programming too, I think. I know when I programmed on MUDs is was ridiculously common.

---

### Post by darkwing_duck on 2008-04-27
Multiple inheritance is used several times in the UML Specifications ([www.omg.org](www.omg.org)).  However, since I am an embedded systems engineer, I've never seen or used multiple inheritance (specially since I've only worked on flight software which tends to be more functionally oriented).

---

### Post by mssever on 2008-04-27
> **ZylGadis said:**
> Read about mixins [http://en.wikipedia.org/wiki/Mixin](http://en.wikipedia.org/wiki/Mixin). This is the most common use (and about the only one which makes sense). Often used in computer game development.

Interestingly, this is the reason why Ruby doesn't support multiple inheritance; mixins serve the same purpose but in a cleaner manner.

---

### Post by DavidBell on 2008-04-28
JupiterV2, I don't see any MI in your example, are you sure gtkmm doesn't just use a hierachy? (I don't know, never used it)

Stooz, I use two libraries in windows that use C++ MI, and in both cases maybe because they are related they use *templated* multiple inhertitance *extensively*.

WTL (MS Windowing Template Library) is a windowing library that is sort of a lean alternative to MFC. While MFC has a multilevel single inheritance hierachy with extra functions being brought in at different levels for different controls as needed, and with eveything deriving from CObject in the end; WTL takes a different track flattening everything out to one level using MI to add functions. So creating a window class becomes something like
```

class CMainDlg :
            public CDialogImpl<CMainDlg>,  // << Add dialog functions
            public CUpdateUI<CMainDlg>,         // << Add UI update functions
            public CMessageFilter,              // << Windows message crackers
            public CIdleHandler                 // << return idle signal to OS
    { /// Your dialog code here with help from MI imported functions 
      /// .....

```
I use it quite a bit, and it's quite neat becasue you can just bring in the features youi need and it usually compiles very small compared to MFC.

The other related one is ATL (MS ActiveX Templating Library) which does similar things with Windows COM/OLE subsystem, and again uses multiple templates to bring in functions. But one interesting use in this one is with interfaces, interfaces are really a higher level of abstraction that C++ classes because the way they are used is that only the interface counts, implementation is never seen by the client.

Anyway the way it does interfaces is just declare a base class with pure virtual functions like

```

class MyInterface
   {void MyRequireFunction(void) = 0;
   }

```

Any class that inhertits from this thing *simply must (or it wont compile)* provide implementations for these pure virtual functions, and in this sense they 'support' the interface. As it happens nearly all COM/OLE support at least two (one being IDispatch) and you can really have as many as you want. But the easy way to implement multiple interfaces is to use MI with pure virtual base classes ... so defining a COM class in ATL is a bit like

```

class MyCOMObject :
                   public MyInterface,
                   public IDispatchImpl<MyInterface>
   { /// Implement MyInterface functions
     /// IDispatch is done by the template
     /// ....
   }

```

(it's actually more complicated with factories etc, but this is what they boil down to).

Anyway, that's two places I have seen MI used a lot, and frankly I never 'got' MI until I started using these libraries, and they are worth having a look at how they work as they are both well written from a 'get the job done with minimum fuss' perspective (WTL is open source and free, I think ATL source only comes with pro versions of MSVS). 

Just a couple of other notes 

- Using templated MI with a good library is easy enough these days, MSVC at least has no issues debugging templates or MI, don't know about gdb. 

- Writing it is a lot harder, but what I learnt from these libraries is that it's best to avoid interdependance and isolate functionality, this way you can mix and match without conflicts.

- You can actually write MI base classes exactly like single inhertitance base classes - eg I have a couple of settings base classes, one for reading text settings, one for xml settings, there's no conflicting member variables or functions so I can use them for single or multiple inhertinace depanding on what I want.

- Avoid MI polymorphism unless there's a really good reason, or you want to do your head in.

Lastly I don't think there's anything MI does that can't be done withoput either single inhertitance hierachies or with containment. I just find if the base classes are well done it's a very low effort way of adding diffrent functions to your classes.

HTH DB

PS. Please don't start another stupid OS/language war on this, MS ATL/WTL was used as an example simply because they are the only libraries I know that use a lot of MI. The only other one I can think of is std::iostream but I find it's code pretty hard to follow.

---

### Post by JupiterV2 on 2008-04-28
> JupiterV2, I don't see any MI in your example, are you sure gtkmm doesn't just use a hierachy? (I don't know, never used it)

Sorry, yeah my example was pretty crap=tacular. However, while Gtkmm primarily uses hierarchal inheritance there is MI in certain cases. As in the case where Gtk::Widget inherits both Atk::Implimentor and Gtk::Object into its class.

---

