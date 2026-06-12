---
title: "PyGTK custom signals send a list as parameter"
date: 2013-10-05
forum: Programming Talk
---

### Post by parinporecha on 2013-10-05
[COLOR=#000000][FONT=Arial]I'm trying to a[/FONT][/COLOR][COLOR=#000000][FONT=Arial]dd a custom signal to a class -

[/FONT][/COLOR]```
[COLOR=#00008B]class[/COLOR] [COLOR=#2B91AF]TaskBrowser[/COLOR](gobject.[COLOR=#2B91AF]GObject[/COLOR]):
    __list_signal__ = (gobject.SIGNAL_RUN_FIRST, gobject.TYPE_NONE, (<[COLOR=#2B91AF]List[/COLOR] datatype>,))
    __gsignals__ = {[COLOR=#800000]'tasks-deleted'[/COLOR]: __list_signal__}

    ...

    [COLOR=#00008B]def[/COLOR] on_delete_tasks(self, widget=[COLOR=#00008B]None[/COLOR], tid=[COLOR=#00008B]None[/COLOR]):
        ...
        gobject.idle_add(self.emit, [COLOR=#800000]"tasks-deleted"[/COLOR], deleted_tasks) [COLOR=gray]#deleted_tasks is of type 'list'[/COLOR]
        ...

    ...
```
[COLOR=#000000][FONT=Arial]In th[/FONT][/COLOR][COLOR=#000000][FONT=Arial]e [/FONT][/COLOR]__gsignals__[COLOR=#000000][FONT=Arial] dict, when I state [/FONT][/COLOR]list[COLOR=#000000][FONT=Arial] as parameter type, I get the following error traceback -

[/FONT][/COLOR]```
File "/home/manhattan/GTG/Hamster_in_hands/GTG/gtk/browser/browser.py", line 61, in <module>
  class TaskBrowser(gobject.GObject):
File "/usr/lib/python2.7/site-packages/gobject/__init__.py", line 60, in __init__
  cls._type_register(cls.__dict__)
File "/usr/lib/python2.7/site-packages/gobject/__init__.py", line 115, in _type_register
  type_register(cls, namespace.get('__gtype_name__'))
TypeError: Error when calling the metaclass bases
  could not get typecode from object&#8203;
```[COLOR=#000000][FONT=Arial]
I saw the list of [possible parameter types]("http://pygstdocs.berlios.de/pygobject-reference/gobject-constants.html"), and there's no type for list[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Is there a way I can pass a list as a signal parameter ?[/FONT][/COLOR]

---

### Post by xedth2 on 2013-12-29
```
__list_signal__ = (gobject.SIGNAL_RUN_FIRST, gobject.TYPE_NONE, (gobject.TYPE_PYOBJECT,))
```

[FONT=Ubuntu Mono][COLOR=#000000]You use gobject.TYPE_PYOBJECT. Look into how [python communicates with C]("http://docs.python.org/3/c-api/intro.html") code and vice versa and you'll understand more about what exactly is going on.[/COLOR][/FONT]

---

