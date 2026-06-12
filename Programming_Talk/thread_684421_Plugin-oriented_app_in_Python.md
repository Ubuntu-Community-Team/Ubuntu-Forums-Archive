---
title: "Plugin-oriented app in Python?"
date: 2008-02-01
forum: Programming Talk
---

### Post by Znupi on 2008-02-01
I'm fairly new to Python bu I'm not new to programming. I want to build a plugin-based application, that scans a "Plugins" folder and imports all python files from there. Or maybe even each plugin can have its own directory in "Plugins" so it can have additional files, and import only a specific file from each plugin's directory.

How do I do that? I've been searching on Google but nothing really turned up :(. Any tutorials you know on this? Any sample code? :)

Thanks :)

---

### Post by erginemr on 2008-02-01
Maybe this will help:
[http://lucumr.pocoo.org/blogarchive/python-plugin-system](http://lucumr.pocoo.org/blogarchive/python-plugin-system)

P.S. I, too, am a new Python programmer, but this is a way too advanced topic for me, yet.

---

### Post by diaa on 2008-02-01
> **Znupi said:**
> I'm fairly new to Python bu I'm not new to programming. I want to build a plugin-based application, that scans a "Plugins" folder and imports all python files from there. Or maybe even each plugin can have its own directory in "Plugins" so it can have additional files, and import only a specific file from each plugin's directory.

How do I do that? I've been searching on Google but nothing really turned up :(. Any tutorials you know on this? Any sample code? :)

Thanks :)

I've done this before in a Python application, I didn't read about this method anywhere but it's working fine up till now.

you can use [*imp* module]("http://en.wikipedia.org/wiki/Component_object_model") to import modules dynamically, the rest is something like [*COM*]("http://en.wikipedia.org/wiki/Component_object_model"), each module contains a global function that returns an object that exposes a certain interface, so you just do the following for each file in the plugins directory
```

m = LoadModule("x")
pluginObject = m.GetPluginObject()
# Do whatever you need with the plugin object.

```

---

### Post by pmasiar on 2008-02-01
Thanks, Diaa.

I learned from [http://docs.python.org/lib/modules.html](http://docs.python.org/lib/modules.html) that Python can even dynamically import compiled modules from zipped archives! Cool!

But "imp" is rather a bad name for such interesting and powerfull module. :-)

---

### Post by Znupi on 2008-02-01
Thank you :)

---

### Post by diaa on 2008-02-01
I'm glad you liked my post, thanks for you appreciation :)
Let me add one more tip, the function *imp.load_module()*  reloads a module if it has already been loaded, which is usually not necessary, so if you want to check whether a module is already loaded or not, you can use the following code
```
try:
    module = sys.modules[*module_name*] # *already imported?*
    # Yes
except KeyError:
    # No

```

Check this [simple implementation for Python's import statement]("http://docs.python.org/lib/examples-imp.html") for more details

---

