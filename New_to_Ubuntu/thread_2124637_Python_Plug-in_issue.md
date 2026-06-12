---
title: "Python Plug-in issue"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by rheap on 2013-03-11
I have Qunatum GIS 1.8 Lisboa installed on Ubuntu. I have made a python plug-in using plugin builder. however, even on following the steps shown it fives the following error.- 

 [COLOR=#ff0000]Couldn't load plugin Amb1 due an error when calling its classFactory() method[/COLOR]

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/qgis/utils.py", line 164, in startPlugin
    plugins[packageName] = package.classFactory(iface)
  File "/home/ep/.qgis//python/plugins/Amb1/__init__.py", line 52, in classFactory
    from amb1 import Amb1
  File "/usr/lib/python2.7/dist-packages/qgis/utils.py", line 309, in _import
    mod = _builtin_import(name, globals, locals, fromlist, level)
  File "/home/ep/.qgis//python/plugins/Amb1/amb1.py", line 29, in 
    from amb1dialog import Amb1Dialog
  File "/usr/lib/python2.7/dist-packages/qgis/utils.py", line 309, in _import
    mod = _builtin_import(name, globals, locals, fromlist, level)
  File "/home/ep/.qgis//python/plugins/Amb1/amb1dialog.py", line 24, in 
    from ui_amb1 import Ui_Amb1
  File "/usr/lib/python2.7/dist-packages/qgis/utils.py", line 309, in _import
    mod = _builtin_import(name, globals, locals, fromlist, level)
ImportError: No module named ui_amb1

Python version:
2.7.3 (default, Aug  1 2012, 05:27:35) 
[GCC 4.6.3]


QGIS version:
1.8.0-Lisboa Lisboa, exported

Python path: ['/usr/share/qgis/python', '/home/ep/.qgis//python', '/home/ep/.qgis//python/plugins', '/usr/share/qgis/python/plugins', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-linux2', '/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload', '/usr/local/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages/PIL', '/usr/lib/python2.7/dist-packages/gst-0.10', '/usr/lib/python2.7/dist-packages/gtk-2.0', '/usr/lib/pymodules/python2.7', '/usr/lib/python2.7/dist-packages/ubuntu-sso-client', '/usr/lib/python2.7/dist-packages/ubuntuone-client', '/usr/lib/python2.7/dist-packages/ubuntuone-control-panel', '/usr/lib/python2.7/dist-packages/ubuntuone-couch', '/usr/lib/python2.7/dist-packages/ubuntuone-installer', '/usr/lib/python2.7/dist-packages/ubuntuone-storage-protocol']

Please do help identify the problem.

---

