---
title: "About GUIs: close or hide frame?"
date: 2008-01-21
forum: Programming Talk
---

### Post by c174 on 2008-01-21
I'm writing an application using wxWidgets. The graphical interface is supposed to facilitate the generation of an input file for a simulation program (another application).

The input data comes in chunks (objects) and I'm going to launch a frame where on can enter data for each kind of object. So my question is now:

Should I close a frame when the user presses "OK" or should I just hide it?

If I just hide the frame it is easy to redisplay the frame if the user needs to modify already entered data (closing a frame will delete all childs such as wxTextCtrl, so the data contained must be copied to other variables before closing(deleting) the frame). On the other hand, there will be _many_ objects, so just hiding the frames might consume ressources? (I guess??)

Does anybody have an opinion on this? It's easy to just hide a frame, but is it OK to have many frames with associated data in memory/"alive" at the same time?

---

### Post by aks44 on 2008-01-21
My opinion:

Unless you really have to keep it opened, close the frame ASAP. It will free memory, and guarantee that when you show it again (by creating a new one) you won't inherit from the previous state.

If you need to persist the frame's state between two displays, put all relevant data in a struct that the frame takes as an argument when it is constructed, and that is updated when the frame closes.

This will ensure clean code, and will minimize resource usage.

Also, this way makes it easier to handle several identical frames at the same time (if you need to), since the interface is well constrained.


If you want to push things a bit farther, make all constructors private, and only publish a static function:

(Warning: C++ "pseudocode" since I don't have knowledge of wxWidgets details)

```
class YourFrame : public Whatever
{
private:
  YourFrame() { /*...*/ };
public:
  struct Params
  {
    /* ... */
  };
  static bool EditParams(YourFrame::Params& params)
  {
    std::auto_ptr<YourFrame> frm(new YourFrame());
    /* fill your frame's fields from params */
    frm->Show();
    if (/* OK pressed */) // assumes there is a Cancel button too
    {
      /* update params from your frame's fields */
    };
    return (/* OK pressed */);
  };
}
```

---

### Post by c174 on 2008-01-21
Ok, thanks for giving your opinion. If somebody has a different view let's hear it :)

I'll consider making the constructor private. It's nice to have a return type from EditParams.

---

### Post by naugiedoggie on 2008-01-21
> **c174 said:**
> I'm writing an application using wxWidgets. The graphical interface is supposed to facilitate the generation of an input file for a simulation program (another application).

The input data comes in chunks (objects) and I'm going to launch a frame where on can enter data for each kind of object. So my question is now:

Should I close a frame when the user presses "OK" or should I just hide it?

If I just hide the frame it is easy to redisplay the frame if the user needs to modify already entered data (closing a frame will delete all childs such as wxTextCtrl, so the data contained must be copied to other variables before closing(deleting) the frame). On the other hand, there will be _many_ objects, so just hiding the frames might consume ressources? (I guess??)

Does anybody have an opinion on this? It's easy to just hide a frame, but is it OK to have many frames with associated data in memory/"alive" at the same time?

Hello,

Make the frame a reusable object.  If you have many objects which will need to be presented in a frame, it's naughty to create new frames for each object!  Hide it when it goes out of scope, and when you need to present, make it visible again with the necessary new parameters.

More work at the design stage ... less coding ... less work at the presentation stage.  Well, it's a thought, anyway.

Thanks.

mp

---

### Post by aks44 on 2008-01-21
> **naugiedoggie said:**
> Make the frame a reusable object.  If you have many objects which will need to be presented in a frame, it's naughty to create new frames for each object!  Hide it when it goes out of scope, and when you need to present, make it visible again with the necessary new parameters.

As far as I understand it, your notion of "reusable object" looks very much like a "global object" to me.

What if there is a need to display several such frames simultaneously? What if there are many call sites that need to display the frame? In both cases the frame class itself *_has to_* handle incoming/outgoing parameters, and the most straightforward way that allows both *_at the same time_* is to encapsulate the frame creation / display / destruction in a single higher level function.


I'm curious how one could satisfy such requirements while leaving a hidden frame in the background (possibly several ones) and being able to reuse it (them) at will, unless you're gonna clutter the design in order to specifically handle that (pools, ...).
Care to share a sketch class design?

---

### Post by c174 on 2008-01-22
I'm a little confused about naugiedoggie's suggestion. Personally I think there are two reasonable ways of doing it (pseudo-code)

Method 1:
```
class Data { ... };

class Frame {
   CreateOrEdit( Data* obj, int action );
};
```

Method 2:
```
class DataWithFrame {
   showFrame( int action );
   hideFrame();
};
```

In Method 1 the data object and the frame for user input are separated. So the data object can live, while the frame is being deleted when not in use. An instance of Frame can be made for each instance of Data, that need to be edited at the same time.

In Method 2 the data object and the frame are tied together. The advantage is that transfer or copying of variables is reduced. However, more ressources are needed.

So my question is whether Method 2 is a prohibitive design? Does somebody have experience with this method? Personally I think I prefer Method 1, but I think I could learn something from hearing other peoples opinion :)

---

### Post by aks44 on 2008-01-23
> **c174 said:**
> So my question is whether Method 2 is a prohibitive design? Does somebody have experience with this method? Personally I think I prefer Method 1, but I think I could learn something from hearing other peoples opinion :)

**Disclaimer:** I'm not a GUI expert (I design & write back office servers). But of course servers need clients, so I need to work closely with GUI teams. So obviously such GUI-specific decisions are not made by me, but from the results all I can say is that those GUI people I work with are quite competent... :)


Now to the point...


Usually, usage of method 2 is restricted to data singletons that are closely tied to GUI structures, that can grow quite large, and/or that need to be accessible at any time. An example would be an object tree (bound to some sort of TreeView, which holds the tree nodes and their associated data) that (possibly) has to be updated regularly even if the frame is not open.

In this case, if you destroyed the frame everytime you'd need to have a separate tree structure, and everytime you need to display the frame you'd have to copy (possibly huge) amounts of data from your custom tree into the GUI tree widget.
Cons: too many runtime overhead when creating the frame, too many memory usage when the frame is open (the tree ends up duplicated).
Using method 2 would make sense then.



But most of the time, a single frame doesn't handle much data so creating a new frame on demand (and destroying it ASAP) doesn't create much runtime overhead or data duplication. Now what you have to remember is that a typical frame uses quite some memory. In this case method 1 makes more sense, it is *globally* more resource-friendly, and moreover it provides better encapsulation (which is Good).



A good-practice GUI architecture is to separate as much as possible the data from the interface (method 1). There are very good reasons for that, especially maintainability.
Of course as usual there are cases where you need to do Evil things (method 2), simply because they're the *_least_* Evil of all possible choices.

Be wise, think about what you need *_exactly_*. The maintainability advantages alone of method 1 (not even speaking of memory usage) will be far more important than the little additional code you have to throw in to enable it.

Again, *_truly_* lazy programmers are not afraid of doing twice the work upfront, because they know it will save them tenfold work later.
IMNSHO people that moan because a more flexible design requires a few additional thousand lines are just clueless, they probably never had to maintain any real-life project. Just my 0.02, YMMV. :)

---

### Post by c174 on 2008-01-24
So if I get right, aks44, you also think best of Method 1.

In the meantime my project has evolved a little bit. When you speak about a treeview - I actually DO have a treeview. Fortunately it is displayed always in the main window of the application. So I dont need to hide and redisplay that one.

But, some of the other frames are a little complicated also. For example one of them has a text control where the you can enter data in a matrix-like structure. Then list controls are used to select columns for x-data and y-date, which are then afterwards plotted. So quite a lot of stuff must be saved in "back-up variables" when I close the frame.

To put it in "mathematical" terms, e.g.

F(a,b,c,d,e,f,g, ... ) -> G,H

That is many input fields in the frame are needed to produces the "result", which is only two arrays of data. However, to do the "inverse" transformation I need to store everything (to be able to redisplay the frame).

Finally I realized another thing: The user should have an option to edit all fields of the frame, push "apply" (where it makes sense), and then discard changes by pushing "cancel". So, in any case using either Method 1 or Method 2 I will need temporary variables (cannot work directly on the object, if the user cancels changes).

So therefore I stick with Method 1.

A nice feature in wxWidgets would then be a function called "GetState" and another one called "SetState". If all widgets implemented these two functions it would be easy to retrieve and recreate the state of e.g. a wxRadioBox - or a wxTreeCtrl :) (although in some cases a lot of memory would be used).

Thanks everybody for your comments! :KS

---

### Post by aks44 on 2008-01-25
> **c174 said:**
> Finally I realized another thing: The user should have an option to edit all fields of the frame, push "apply" (where it makes sense), and then discard changes by pushing "cancel". So, in any case using either Method 1 or Method 2 I will need temporary variables (cannot work directly on the object, if the user cancels changes).

So therefore I stick with Method 1.

Indeed, I forgot to mention such (very common) cases. Yet another argument for good data / UI separation... :)

---

