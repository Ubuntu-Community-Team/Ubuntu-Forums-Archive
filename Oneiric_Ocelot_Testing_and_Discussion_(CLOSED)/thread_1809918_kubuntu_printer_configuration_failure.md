---
title: "kubuntu printer configuration failure"
date: 2011-07-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-07-22
I'm getting a printer fail when trying to configure the printer in kubuntu oneiric.  2 of 2 computers have this so far, anyone have any suggestions for me?

```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ systemsettings
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/buzzmandt/.config/ibus/bus
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ systemsettings(1962)/python (plugin): Error while running factory function for Python plugin:  "system-config-printer-kde/system-config-printer-kde.py" 
Traceback (most recent call last):
  File "<string>", line 18, in kpythonpluginfactory_bridge
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 4398, in CreatePlugin
    kcm = u.makeui(component_data, widget_parent)
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 135, in makeui
    self.ui = PyKcm(component_data, parent, self)
  File "/usr/share/kde4/apps/system-config-printer-kde/system-config-printer-kde.py", line 111, in __init__
    uic.loadUi(unicode(APPDIR + "/" + "system-config-printer.ui"), self)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/__init__.py", line 221, in loadUi
    return DynamicUILoader().loadUi(uifile, baseinstance)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/Loader/loader.py", line 71, in loadUi
    return self.parse(filename, basedir)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 886, in parse
    actor(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 729, in createUserInterface
    self.traverseWidgetTree(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 449, in createLayout
    self.traverseWidgetTree(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 486, in handleItem          
    self.traverseWidgetTree(elem)                                                             
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree  
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 214, in createWidget
    self.traverseWidgetTree(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 214, in createWidget
    self.traverseWidgetTree(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 449, in createLayout
    self.traverseWidgetTree(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 486, in handleItem
    self.traverseWidgetTree(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 449, in createLayout
    self.traverseWidgetTree(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 486, in handleItem
    self.traverseWidgetTree(elem)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 707, in traverseWidgetTree
    handler(self, child)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 208, in createWidget
    self.stack.push(self.setupObject(widget_class, parent, elem))
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 176, in setupObject
    obj =  self.factory.createQObject(clsname, name, args, is_attribute)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/objcreator.py", line 105, in createQObject
    classType = self.findQObjectType(classname)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/objcreator.py", line 115, in findQObjectType
    w = module.search(classname)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/Loader/qobjectcreator.py", line 92, in search
    self._modules[module] = __import__(module, {}, {}, (cls,))
ImportError: No module named kpushbutton
systemsettings(1962)/python (plugin): Failed to import module 
systemsettings(1962)/kcontrol KCModuleLoader::loadModule: This module has no valid entry symbol at all. The reason could be that it's still using K_EXPORT_COMPONENT_FACTORY with a custom X-KDE-FactoryName which is not supported anymore 

```

```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ kcmodule
kcmodule: command not found
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ system-config-printer-kde
system-config-printer-kde: command not found
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ aptitude search system-config-printer-kde
i   system-config-printer-kde              - printer configuration utility                    
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ 

```

---

### Post by buzzmandt on 2011-07-22
bug reported
[https://bugs.launchpad.net/ubuntu/+source/system-config-printer-kde/+bug/814770](https://bugs.launchpad.net/ubuntu/+source/system-config-printer-kde/+bug/814770)

---

### Post by SeijiSensei on 2011-07-22
Did you try configuring the printer via System Settings > Printer Configuration?

I find the best approach is to use a browser and visit [http://localhost:631/](http://localhost:631/) to use CUPS browser-based interface.  When KDE4's native printer application didn't work so well in earlier versions, I took this approach and kept with it ever since.  (The application works better in 10.10, but I still use the browser-based solution.)

---

### Post by buzzmandt on 2011-07-22
that was the only way i could get it to work.  definately a bug that needs squashing before release.

---

