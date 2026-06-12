---
title: "[Python] __doc__"
date: 2011-03-09
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-09
Am reading Dive Into Python, just read about __doc__ now I'm wanting to do a doc but can't understand a bit of what is returned. So now I did help() the module is webkit and the .WebBackForwardList is the thing I'm interested in. I just can't seem to understand what the info is telling me.

> 
    class WebBackForwardList(gobject._gobject.GObject)
     |  Object WebKitWebBackForwardList
     |  
     |  Signals from GObject:
     |    notify (GParam)
     |  
     |  Method resolution order:
     |      WebBackForwardList
     |      gobject._gobject.GObject
     |      __builtin__.object
     |  
     |  Methods defined here:
     |  
     |  __init__(...)
     |      x.__init__(...) initializes x; see x.__class__.__doc__ for signature
     |  
     |  add_item(...)
     |  
     |  contains_item(...)
     |  
     |  get_back_item(...)
     |  
     |  get_back_length(...)
     |  
     |  get_back_list_with_limit(...)
     |  
     |  get_current_item(...)
     |  
     |  get_forward_item(...)
     |  
     |  get_forward_length(...)
     |  
     |  get_forward_list_with_limit(...)
     |  
     |  get_limit(...)
     |  
     |  get_nth_item(...)
     |  
     |  go_back(...)
     |  
     |  go_forward(...)
     |  
     |  go_to_item(...)
     |  
     |  set_limit(...)
     |  
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |  
     |  __gtype__ = <GType WebKitWebBackForwardList (143209544)>
     |  
     |  ----------------------------------------------------------------------
     |  Methods inherited from gobject._gobject.GObject:
     |  
     |  __cmp__(...)
     |      x.__cmp__(y) <==> cmp(x,y)
     |  
     |  __copy__(...)
     |  
     |  __deepcopy__(...)
     |  
     |  __delattr__(...)
     |      x.__delattr__('name') <==> del x.name
     |  
     |  __gobject_init__(...)
     |  
     |  __hash__(...)
     |      x.__hash__() <==> hash(x)
     |  
     |  __repr__(...)
     |      x.__repr__() <==> repr(x)
     |  
     |  __setattr__(...)
     |      x.__setattr__('name', value) <==> x.name = value
     |  
     |  chain(...)
     |  
     |  connect(...)
     |  
     |  connect_after(...)
     |  
     |  connect_object(...)
     |  
     |  connect_object_after(...)
     |  
     |  disconnect(...)
     |  
     |  disconnect_by_func(...)
     |  
     |  emit(...)
     |  
     |  emit_stop_by_name(...)
     |  
     |  freeze_notify(...)
     |  
     |  get_data(...)
     |  
     |  get_properties(...)
     |  
     |  get_property(...)
     |  
     |  handler_block(...)
     |  
     |  handler_block_by_func(...)
     |  
     |  handler_disconnect(...)
     |  
     |  handler_is_connected(...)
     |  
     |  handler_unblock(...)
     |  
     |  handler_unblock_by_func(...)
     |  
     |  notify(...)
     |  
     |  set_data(...)
     |  
     |  set_properties(...)
     |  
     |  set_property(...)
     |  
     |  stop_emission(...)
     |  
     |  thaw_notify(...)
     |  
     |  weak_ref(...)
     |  
     |  ----------------------------------------------------------------------
     |  Data descriptors inherited from gobject._gobject.GObject:
     |  
     |  __dict__
     |  
     |  __grefcount__
     |  
     |  ----------------------------------------------------------------------
     |  Data and other attributes inherited from gobject._gobject.GObject:
     |  
     |  __gdoc__ = 'Object WebKitWebBackForwardList\n\nSignals from GObject:\n...
     |  
     |  __new__ = <built-in method __new__ of GObjectMeta object>
     |      T.__new__(S, ...) -> a new object with type S, a subtype of T
     |  
     |  props = <gobject.GProps object>


Can someone explain all this to me? Where the parameters are, where they go. Sorry, as I said, I just started reading Dive Into Python. Is there some secret programmer's book I don't know about or something?

---

### Post by LemursDontExist on 2011-03-10
The help function is giving you all the methods and variables defined in the class along with any attached docstrings.

As an example, if I write the following in foo.py:

```
class Bar():
    """A class that does nothing interesting"""
    my_var = 5
    def my_method(self):
        """A method in Bar"""
        pass
```

then

```
import foo
help(foo.Bar)
```

outputs

```
Help on class Bar in module foo:

class Bar
 |  A class that does nothing interesting
 |  
 |  Methods defined here:
 |  
 |  my_method(self)
 |      A method in Bar
 |  
 |  ----------------------------------------------------------------------
 |  Data and other attributes defined here:
 |  
 |  my_var = 5
```

The python gtk documentation is of generally a poor quality, and most the classes and methods have no docstrings - as a result you're not getting much useful information out other than a list of methods whose use you'll have to guess at.  

I would suggest searching online for better documentation, or possibly referring to the C documentation for the library, which tends to be better.  You can also find the source code and look at it directly to try to deduce what it does.

---

### Post by nvteighen on 2011-03-10
> **LemursDontExist said:**
> 
The python gtk documentation is of generally a poor quality, and most the classes and methods have no docstrings - as a result you're not getting much useful information out other than a list of methods whose use you'll have to guess at.

Because they (incorrectly) assume that everyone will just know how to find the official API docs...

---

### Post by ki4jgt on 2011-03-10
Yay, I think I go to the original source code and try to start guessing. :-) I've tried to find documentation and it's just as helpful as this itself.

---

### Post by ki4jgt on 2011-03-11
> **LemursDontExist said:**
> I would suggest searching online for better documentation, or possibly referring to the C documentation for the library, which tends to be better.  You can also find the source code and look at it directly to try to deduce what it does.

That actually does have better documentation. Thank you very much!

---

