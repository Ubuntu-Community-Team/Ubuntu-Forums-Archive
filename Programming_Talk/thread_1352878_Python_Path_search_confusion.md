---
title: "Python Path search confusion"
date: 2009-12-12
forum: Programming Talk
---

### Post by kakila on 2009-12-12
Hi,
I have problems running a python script as standalone.
Here is the symptom

```

$ pwd
<my folders>/src
$ tree
.
|-- Apps
|   |-- DragAndDrop.py
|   |-- FlockDebug.py
|   |-- FlockTestApp.py
|   |-- OffsetTest.py
|   |-- PursuitTest.py
|   |-- ShootTheFliesApp.py
|   `--__init__.py
|-- Controller
|   |-- Cameras.py
|   |-- Controller.py
|   |-- Crosshair.py
|   |-- KeyboardController.py
|   |-- Labelers.py
|   |-- MiscControllers.py
|   |-- MouseController.py
|   |-- Posture
|   |   |-- LookAt.py
|   |   |-- PostureController.py
|   |   `-- __init__.py
|   |-- Steering
|   |   |-- SteerController.py
|   |   |-- SteerForAlign.py
|   |   |-- SteerForArrive.py
|   |   |-- SteerForCohesion.py
|   |   |-- SteerForEvasion.py
|   |   |-- SteerForFlee.py
|   |   |-- SteerForFlock.py
|   |   |-- SteerForOffset.py
|   |   |-- SteerForPursuit.py
|   |   |-- SteerForSeek.py
|   |   |-- SteerForSeparation.py
|   |   `-- __init__.py
|   `-- __init__.py
|-- Mediator
|   |-- EventManager.py
|   `-- __init__.py
|-- Model
|   |-- Model.py
|   `-- __init__.py
|-- Test
|   |-- __init__.py
|   |-- testNew_abs.py
|   `-- testNew.py
|-- Tools
|   |-- LinAlgebra_extra.py
|   |-- WeakRefSet.py
|   |-- __init__.py
|   |-- orderedset.py
|   `-- real2pix.py
|-- View
|   |-- Font
|   |-- Images
|   |-- View.py
|   |-- __init__.py
|   |-- colormap.py
|   |-- config.py
|   `-- misc.py
`-- __init__.py

$ cd Test
$ pwd
<my folders>/src/Test
$ pychecker testNew.py
Processing module testNew (testNew.py)...

Warnings...

None
$ python testNew.py
Traceback (most recent call last):
  File "testNew.py", line 138, in <module>
    from ..View.View import PygameViewer
ValueError: Attempted relative import in non-package
$ python testNew_abs.py
Traceback (most recent call last):
  File "testNew_abs.py", line 138, in <module>
    from View.View import PygameViewer
ImportError: No module named View.View
```

I searched the web and python.org but cannot find an explanation to the problem.
The issue is partially covered in the documentation of modules but no references when running as standalone...

Any ideas?

Thanks

---

### Post by ssam on 2009-12-12
can you just run the test from the source dir?
```

cd <my folders>/src
python Test/testNew_abs.py

```

otherwise you can make <my folders>/src part of the python path.

```

export PYTHONPATH=<my folders>/src:$PYTHONPATH

```

if you want to see the current search paths run
```

python -c "import sys; print sys.path"
```

---

### Post by kakila on 2009-12-12
[QUOTE=ssam;8484607]can you just run the test from the source dir?
```

cd <my folders>/src
python Test/testNew_abs.py

```
Still doesn't work

```

export PYTHONPATH=<my folders>/src:$PYTHONPATH

```
This worked. Thanks!
Can I add this somehow in the __init__.py on the src folder?

---

### Post by nvteighen on 2009-12-12
> **kakila said:**
> [QUOTE=ssam;8484607]can you just run the test from the source dir?
```

cd <my folders>/src
python Test/testNew_abs.py

```
Still doesn't work

```

export PYTHONPATH=<my folders>/src:$PYTHONPATH

```
This worked. Thanks!
Can I add this somehow in the __init__.py on the src folder?

Do it this way:
```

import sys
sys.path.append(folders + "/src") 
# folders should be a string with the rest of your path.

```

---

### Post by kakila on 2009-12-12
Thanks a lot!

--- Later....

It still doesn't work, even when those lines are added to the __init__.py on the /src folder.

:(

Ayn suggestion?

---

### Post by kakila on 2009-12-29
Doing this on the test makes it work. Also is independent of the tree structure

```

import sys,os
filepath, filename = os.path.split(os.path.abspath(os.path.dirname(__file__)) )
sys.path.append(filepath)

```

But I do not find a way of doing this automatically...I have to write this lines in each Test I write...there must be a cleverer solution...

---

