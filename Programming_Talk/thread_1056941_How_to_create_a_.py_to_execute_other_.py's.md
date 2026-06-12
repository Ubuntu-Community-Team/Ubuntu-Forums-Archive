---
title: "How to create a .py to execute other .py's?"
date: 2009-02-01
forum: Programming Talk
---

### Post by officiallyme on 2009-02-01
Hi all,
As you can probably see by my maybe stupid question, I am a total beginner.

I hope you guys can help me with my problem :)

I need a .py file, lets call it "execute.py" that does nothing else than execute a different .py file (lets call it "TestFile.py") in a specific foler.

Basically it is supposed to perform the shell command "./TestFile.py".

But I just can't figure it out :(
Such a simple task one might think :(


The file also has to contain the following:

```

from Plugins.Plugin import PluginDescriptor # importiert den PluginDescriptor (s.u.)<br>
 # diese Funktion wird aufgerufen und gibt einen einzelnen PluginDescriptor oder eine Liste von PluginDescriptoren zurück
 # das **kwargs einfach ignorieren! (näheres dazu in docs/PLUGINS im enigma-baum) ***
 def Plugins(**kwargs):
   # Beispiel für ein einzelnes Plugin, welches im Plugin-Menü erscheint
   return PluginDescriptor(name="File-Manager", description="Let's you view/edit files in your Dreambox", where = 
   PluginDescriptor.WHERE_PLUGINMENU, fnc=main)
 
   # Beispiel für eine Liste von Plugins, das erste erscheint im Plugin-Menü, das zweite wird beim E2-Start aufgerufen (Autostart)
   return [PluginDescriptor(name="Plugin1", description="Example Plugin", where = PluginDescriptor.WHERE_PLUGINMENU, fnc=main),
   PluginDescriptor(where = PluginDescriptor.WHERE_AUTOSTART, fnc = autostart) ]
```
and
```
def main(session, **kwargs): 
```

full instructions of what is mandatoy in the file for it to be recognized by the system can be found [here]("http://dream.reichholf.net/wiki/Enigma2:Plugin-Erstellung") 


I don't need or want any screens to be created or anything else. all of that is done in the TestFile.py that I want to execute. So I guess the execution command "simply" needs to be implemented into the "def main" part?

I hope you guys can help me. I just can't figure it out :(

---

### Post by jimi_hendrix on 2009-02-01
just use a shell script?

---

### Post by officiallyme on 2009-02-01
if you can write me a .py that executes that shell script, then no problem :D

this .py is part of an installation package. the installer checks whether there is a file called "plugin.py" and executes that and ONLY that file when you select that plugin in the menu.

so i need THAT plugin to execute a different one because that other one cannot just be renamed to "plpugin.py". it needs to remain under it's original name and be executed under that name.

i hope you understand what i mean. it's not a python script for a computer but for a hardware device.

---

### Post by geirha on 2009-02-01
```

>>> help('os')   # Read about all the exec* functions, spawn* functions and the system function

```

---

### Post by bobbocanfly on 2009-02-01
It looks like you are trying to create a plugin system (am I right?). If so I find the easiest way is to use the "exec" statement (or exec() function in Python 3.0) to import the plugin file and call the correct function. So something like:

```

import sys

sys.path.append(plugins_directory)

plugins = ["helloworld", "docoolstuff"]
instances = {}

for p in plugins:
    exec "from %s import %S_Plugin" % (p, p)
    exec "instances.append(%s_Plugin())" % p  

```

Than when you want the plugin to do something, you just cycle through the instances dict and use exec to run the do_xx() and do_yy() functions. 

This seems more complicated, but is a much "safer" and more versatile way to do plugins. Look at the sourcecode of "Deb-o-matic" to see this in action.

(If you aren't doing a plugins system use "os.system("python %s" % scriptname)" to run something)

---

### Post by officiallyme on 2009-02-01
ok, then let's see if i understand correctly. would this work:

```

from Plugins.Plugin import PluginDescriptor

def main(session, **kwargs):
    startfile(/var/usr/local/TestPlugin/TestPlugin.py)

def Plugins(**kwargs):
    return PluginDescriptor(name="TestPlugin", description="Start the TestPlugin", where = PluginDescriptor.WHERE_PLUGINMENU, fnc=main)

```

EDIT: @bobbocanfly: sorry, didn't see your reply until after i posted. looks complicated :(
i think the simpler the better. it really just needs to run the ONE TestPlugin.py file. it does not need to do anything else. basically i want the python file to act like a shell command "./TestPlugin.py".

I am just much more comfortable writing shell skripts/batches :(


EDIT2: the "def main" in my script has a "(session)". do i need this? or could it be "def main (**kwargs):"?

---

### Post by jimi_hendrix on 2009-02-01
> **officiallyme said:**
> if you can write me a .py that executes that shell script, then no problem :D

this .py is part of an installation package. the installer checks whether there is a file called "plugin.py" and executes that and ONLY that file when you select that plugin in the menu.

so i need THAT plugin to execute a different one because that other one cannot just be renamed to "plpugin.py". it needs to remain under it's original name and be executed under that name.

i hope you understand what i mean. it's not a python script for a computer but for a hardware device.

just curious...why must it be python....this strikes me as a 2 liner shell script (one liner even)

---

### Post by officiallyme on 2009-02-01
it is a one liner shell script. no problem at all.
only problem is, that in order for the system to be able to use the python program i already have, this program needs to be "registered" in the system.

to do that your plugin/program needs to have a file called "_init_.py" (which is empty) and a file called "plugin.py" which I am trying to create here. if those are available and you put all of that into an ipkg packages (which I can do and have many times), the system will register the program/plugin upon installation of this .ipk packages.

If those two are present then upon installation via the addon manager, the plugin/program will be automatically registered in the system and will become available via the main menu and can be assigned to any key on the remote control.

As i cannot alter the program's .py file to turn it into the necessary "plugin.py", i would like to create a simple "plugin.py" file that simply opens the more complicated program/plugin I actually want.


and for the system to recognize the program/plugin, the "plugin.py" has to contain the "def plugins" and the "def main" commands. otherwise it will not work. so the execution of the .py fle of my program (TestPlugin.py) has to be done in the "def main" part.

---

