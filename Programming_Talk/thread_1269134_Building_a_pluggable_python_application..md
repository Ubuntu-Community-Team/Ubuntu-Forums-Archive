---
title: "Building a pluggable python application."
date: 2009-09-17
forum: Programming Talk
---

### Post by linuxunil on 2009-09-17
I'm building an application to backup, search, etc notes I take in school.  I'm wanting to make it pluggable so extending it will be easier for me and others.  But I am having a hard time finding information on building pluggable applications.  The few examples I have found are things like IRC bots that just pass events.

My idea for using pluggins is mainly things like changing how a function works.  Since it's going to start off as a command-line app, if I do something like ```
foo add bar
``` I would like for a plugin to be able to add or replace the functionality of add, such as instead of saving to a flat file save to a database, or online storage.


[In advance]
Any suggestions on approaches to making an application pluggable are very appriciated

---

### Post by unutbu on 2009-09-17
Really, I don't know if this is the best way to do it, but here is one way:

Put this in main.py:
[PHP]
#!/usr/bin/env python
import os
import sys
main=sys.modules['__main__']
plugin_dir=os.path.join(os.environ['HOME'],'test/plugins')

#
# You can omit this line if you put ~/test/plugins in your PYTHONPATH environment
# variable
#
sys.path.append(plugin_dir)
main_objs=set(dir(main))
plugins=[elt.replace('.py','') for elt in os.listdir(plugin_dir) if elt.endswith('.py')]
for plugin in plugins:
    package=__import__(plugin)
    package_objs=set(dir(package))
    for obj in (package_objs-main_objs):
        setattr(main,obj,getattr(package,obj))
adder=Add()
adder.do_stuff()
[/PHP]
Make a directory ~/test/plugins, into which you put add.py:
[PHP]
class Add(object):
    def do_stuff(self):
        print("I'm busy doing stuff!!")[/PHP]
        
Then when you run main.py you get
```

I'm busy doing stuff!!
```

And if you remove add.py and instead put in add_better.py:
[PHP]
class Add(object):
    def do_stuff(self):
        print("I bees better Adder!!")[/PHP]
        
then run main.py again you get 
```

I bees better Adder!!
```

---

