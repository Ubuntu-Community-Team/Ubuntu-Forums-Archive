---
title: "Trouble with Python classes"
date: 2009-07-11
forum: Programming Talk
---

### Post by knopper67 on 2009-07-11
I'm having trouble with a plugin system in a program I wrote. The plugins work fine, however when I happen to execute a class in the program the plugins stops working. ie: Calling one of it's variables returns an error.

Also, I attached the entire program for reference. Just run helix.py from the command line or just double-click. The code base isn't that large if you're wondering.

Thanks in advance.

---

### Post by fr4nko on 2009-07-11
Hi,

it seems that the problem is in plugins.py when calling __import__. You program works if you do something like that
```
def start_all(pluginlist):
    if "--no-plugins" in sys.argv:
        plugin_msg("Plugins disabled")
    else:
        debug("Loading plugins")
        if not len(pluginlist) == 0:
            sys.path.insert(1, global_plugindir)
            for plugin in pluginlist:
                __import__(plugin, globals(), locals(), 1)
            for plugin in HelixPlugin.__subclasses__():
                plugin().init()
```I've also modified the functions checkdir in helix.py like that:
```
def check_dirs():
    exists = os.path.exists
    if not exists(datadir):
        os.mkdir(datadir)
        print("Created Data directories")
    if not exists(notedir):
        os.mkdir(notedir)

```Talking about the __import__ function, I'm not a python guru but looking at the documentation it seems that it needs globals() in order to define the context of the module you are importing. Otherwise, probably it does consider that PyConsole is not a subclass of HelixPlugin and then it does not perform the init method.

Francesco

---

### Post by knopper67 on 2009-07-11
I tried changing the __import__ parameters like you mentioned, It seems to be working now, awesome.

Thanks a lot for your help.

---

