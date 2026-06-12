---
title: "Python import iteration question"
date: 2010-04-03
forum: Programming Talk
---

### Post by SoftwareExplorer on 2010-04-03
Why doesn't this work to import things in python:
[PHP]#!/usr/bin/env python

def import_error(module):
    print("Sorry, was unable to import python \'" + module + "\' module. This program needs it to run.")
    exit()

import_list = ("sys", "pygtk", "gtk",)

for current_import in import_list:
    try:
        import current_import
    except:
        import_error(current_import)

print("Actual program successfully run")[/PHP]

---

### Post by Wybiral on 2010-04-03
import doesn't import the value of a variable, it just uses the name. You could do something like what you want using the __import__ builtin though...

[php]
#!/usr/bin/env python

def import_error(module):
    print("Sorry, was unable to import python \'" + module + "\' module. This program needs it to run.")
    exit()

import_list = ("sys", "pygtk", "gtk",)

environment = locals()
for current_import in import_list:
    try:
        environment[current_import] = __import__(current_import)
    except:
        import_error(current_import)

print("Actual program successfully run")

print(sys.modules)
[/php]

Notice that you have to manually set that variable in the locals or globals dictionary (since __import__ just returns a reference, it doesn't do any assignment)

---

### Post by heikaman on 2010-04-03
I think if you use exec you don't have to set it in the dictionary manually

[PHP]exec('import '+current_import)[/PHP]

But It's not safe though.

---

### Post by nvteighen on 2010-04-03
eval won't work because it doesn't allow import being used. What works is exec:
```

exec "import %s" % module

```

The advantage of exec is that it actually creates a dynamic call in the same environment. The disadvantage: you should really be careful with what input you allow to be passed into the exec call.

---

### Post by heikaman on 2010-04-03
> **nvteighen said:**
> eval won't work because it doesn't allow import being used. What works is exec:
[CODE]

Correct ! before I post I tried both and exec worked, but I still wrote eval :D thanks

---

### Post by SoftwareExplorer on 2010-04-03
> **Wybiral said:**
> import doesn't import the value of a variable, it just uses the name. You could do something like what you want using the __import__ builtin though...

[php]
#!/usr/bin/env python

def import_error(module):
    print("Sorry, was unable to import python \'" + module + "\' module. This program needs it to run.")
    exit()

import_list = ("sys", "pygtk", "gtk",)

environment = locals()
for current_import in import_list:
    try:
        environment[current_import] = __import__(current_import)
    except:
        import_error(current_import)

print("Actual program successfully run")

print(sys.modules)
[/php]

Notice that you have to manually set that variable in the locals or globals dictionary (since __import__ just returns a reference, it doesn't do any assignment)
I don't really get how this solution works, but it seems to work. Could you explain how it works to me?

Also, is using exec safe as long as whoever is running the program can't influence the import_list variable?

---

### Post by Wybiral on 2010-04-03
> **SoftwareExplorer said:**
> I don't really get how this solution works, but it seems to work. Could you explain how it works to me?

Also, is using exec safe as long as whoever is running the program can't influence the import_list variable?

Yeah, if import_list isn't capable of being altered on the user end, then it's OK (and less code that way). I've always been opposed to using eval/exec out of distaste, however I've also been opposed to manually altering the environment dictionaries... But in this case, you have to do one of them to get the job done.

The __import__ version works because __import__ returns a reference to a module provided by a string name. My example just had it altering the local environment/scope (which is just a dictionary), if you changed locals to globals you could have the module imported globally.

---

### Post by nvteighen on 2010-04-04
> **Wybiral said:**
> I've always been opposed to using eval/exec out of distaste, ...


Me too, but sadly, it's the nearest thing that Python has for metaprogramming. It's not truly metaprogramming, as everything is done at compile-time and there's no macro expanding at all, but at least allows you to firstly create a string with the needed construct and then pass it to exec.

---

### Post by Wybiral on 2010-04-04
> **nvteighen said:**
> Me too, but sadly, it's the nearest thing that Python has for metaprogramming.

It wouldn't be too bad, I don't think anyway, if Python syntax was easier to programatically generate. But the syntax itself makes it pretty awkward to deal with. But in simple situations like this, it works... It just feels like committing some kind of unpythonic sin. Whatever gets the job done though I suppose.

---

### Post by SoftwareExplorer on 2010-04-08
Ok, thanks! I think I get how both solutions work.

---

