---
title: "[python] What would the best method be to include (custom) plugins"
date: 2009-09-12
forum: Programming Talk
---

### Post by Pyro.699 on 2009-09-12
Alright so i have a program im looking to distrabute. And it has some plugins. To be more exact it has 42 different plugins that are each their own function inside their own file. The program does not require all 42 plugins to work it can have as little or as many as the user wants.

What im looking to do is find the easiest way for the user to "install" the python modules. They are given the pyc file, and told to place it in a folder (for examples sake, lets call it **__plugins__**) . What i want to do is extract the function and use it as if that function was placed in the main script.

With in the plugin class are used which were assigned to variables in the main script. For instance i have built a special url handler which handles cookies, refers and so on. The plugin calls this class (named **url**) several times. I dont want to create a new instance of the class but rather use the one that was declared in the main file.

I have tried adding it to globals(), locals() (before you tell me i know locals was redundant, i was just testing xP) creating special __init__.py files and so on. I originally had all of the plugins hard coded into the main script, but it got too long to manage. The code had reached over 4000 lines and was quite confusing. With each "plugin" in its each folder it will be a much better function.

Thanks
~Cody Woolaver

---

### Post by Can+~ on 2009-09-12
So your question is "how do I let the user add python scripts to a folder and have them running?"

Take a look at Linux' daemons, they all have a start and stop sequences predefined. 

A similar approach could be done, have every "plugin" with a defined structure (start sequence, continuous sequence (in case of realtime), end sequence) and have your code check the folder, import everything into a dictionary and iterate through it. 

With python's duck typing you assume that the proper functions are defined or raise an error if not, so you're covered there.

My only concern would be security, how to avoid that someone dumps malicious code on the folder and gets executed.

---

### Post by tatrefthekiller on 2009-09-13
I don't know if I understand the question, but I think you're talking about dynamic module loading :

[http://stackoverflow.com/questions/301134/dynamic-module-import-in-python](http://stackoverflow.com/questions/301134/dynamic-module-import-in-python)
[http://technogeek.org/python-module.html](http://technogeek.org/python-module.html)

---

### Post by Greyed on 2009-09-13
Tat's first link looks clean.  I did this once where I dropped python files into a subdirectory and they were imported in that manner.  I went further in that I required each plugin to register itself in a dict in the main script.  So the main script imported each plugin then called a register method which touched a global in the main script.  

The dict they registered themselves into was used to run each in turn at the appropriate time.  This was done for a log auditing program where the logs audited changed over time.  Instead of maintaining one large program I would write a plugin to spec (register and output) that the main script would call by virtue of it being in the directory.  The output was then taken and handled by the main script and mailed off to the appropriate people.  None of the plugins needed to know about each other nor how to mail and the main script never had logic for auditing any of the logs.  :D

---

### Post by Pyro.699 on 2009-09-13
Alright, i have all of that down :) Thanks for those links...

How would i go about carrying variables over from the master run file, to the plugin files?

---

### Post by Greyed on 2009-09-13
If it is only a subset that is needed put them into a dict and pass that dict as a variable to the initializing method of the plugin.  IE.

Main program:
[php]
...
shared = {'foo' : spam, 'bar' : eggs}
import_plugins()
for plugin in plugins:
    plugin.varinit(shared)
...
[/php]Plugin:
[php]
shared = {}
...
def varinit(inc_vars):# ok, not sure if this will work...  and probably boorish...
    global shared
    shared = inc_vars
...
[/php]Probably a more Pythonic way to do it but off the top of my head (and after a long shift at work) I can't think of it.

---

### Post by tatrefthekiller on 2009-09-13
When creating your plugin's object, just pass the "main" object as an argument to the constructor. You can try something like this (in this case, plugins extends Thread):

```
class Main:
   ...

   def loadPlugin(pluginName):
      plugin = Plugin(self)
      self.plugins.append(plugin)
      plugin.run()

class Plugin:
   def __init__(self, parent):
      self.parent = parent

   def run(self):
      # main loop of the plugin
      ...

```

---

